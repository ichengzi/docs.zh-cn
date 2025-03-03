---
title: 适用于 WCF 开发人员的 Docker gRPC
description: 为 ASP.NET Core gRPC 应用程序创建 Docker 映像
ms.date: 09/02/2019
ms.openlocfilehash: a5aceb4b5270cb828965e990a62db4147012adff
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967842"
---
# <a name="docker"></a>Docker

本部分将介绍如何创建用于 ASP.NET Core gRPC 应用程序的 Docker 映像，并准备在 Docker、Kubernetes 或其他容器环境中运行。 在 GitHub 上的[dotnet/gRPC/](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample)存储库中提供了使用的示例应用程序，其中包含 ASP.NET Core MVC web 应用和 gRPC 服务。

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>用于 ASP.NET Core 应用程序的 Microsoft 基础映像

Microsoft 提供了一系列用于构建和运行 .NET Core 应用程序的基本映像。 若要创建 ASP.NET Core 3.0 图像，请使用两个基本映像：用于生成和发布应用程序的 SDK 映像，以及用于部署的运行时映像。

| 映像 | 说明 |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | 用于生成具有 `docker build`的应用程序。 不能在生产中使用。 |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | 包含运行时和 ASP.NET Core 依赖项。 用于生产。 |

对于每个映像，都有四个基于不同 Linux 分发的变量，由标记来区分。

| 图像标记 | Linux | 注意 |
| --------- | ----- | ----- |
| 3.0-buster、3。0 | Debian 10 | 如果未指定操作系统变体，则为默认映像。 |
| 3.0-alpine | Alpine 3。9 | Alpine 基本映像比 Debian 或 Ubuntu 映像小得多。 |
| 3.0-disco | Ubuntu 19.04 | |
| 3.0-bionic | Ubuntu 18.04 | |

相比200于 Debian 和 Ubuntu 映像，Alpine 基本映像约 100 MB，但在 Alpine 的包管理中，某些软件包或库可能不可用。 如果你不确定要使用哪个图像，则最好坚持使用默认的 Debian，除非你有说服力需要使用不同的发行版。

> [!IMPORTANT]
> 请确保为生成和运行时使用相同的 Linux 变体。 在一个变体上构建和发布的应用程序可能无法在另一个上运行。

## <a name="create-a-docker-image"></a>创建 Docker 映像

Docker 映像是由*Dockerfile*定义的，它包含生成应用程序所需的所有命令，并安装生成或运行应用程序所需的任何依赖项。 下面的示例演示 ASP.NET Core 3.0 应用程序的最简单的 Dockerfile：

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Dockerfile 有两部分：第一个使用 `sdk` 基本映像来生成和发布应用程序;第二个基于 `aspnet` 创建运行时映像。 这是因为，对于运行时映像，`sdk` 图像大约为 900 MB （约 200 MB），并且在运行时不需要其大部分内容。

### <a name="the-build-steps"></a>生成步骤

| 步骤 | 说明 |
| ---- | ----------- |
| `FROM ...` | 声明基映像并分配 `builder` 别名（有关说明，请参阅下一部分）。 |
| `WORKDIR /src` | 创建 `/src` 目录，并将其设置为当前工作目录。 |
| `COPY . .` | 将主机上当前目录下的所有内容复制到映像上的当前目录。 |
| `RUN dotnet restore` | 还原任何外部包（ASP.NET Core 3.0 framework 已与 SDK 一起预安装）。 |
| `RUN dotnet publish ...` | 生成并发布发布版本。 请注意，不需要 `--runtime` 标志。 |

### <a name="the-runtime-image-steps"></a>运行时映像步骤

| 步骤 | 说明 |
| ---- | ----------- |
| `FROM ...` | 声明新的基本映像。 |
| `WORKDIR /app` | 创建 `/app` 目录，并将其设置为当前工作目录。 |
| `COPY --from=builder ...` | 使用第一个 `FROM` 行中的 `builder` 别名从上一个映像复制已发布的应用程序。 |
| `ENTRYPOINT [ ... ]` | 设置要在容器启动时运行的命令。 运行时映像中的 `dotnet` 命令只能运行 DLL 文件。 |

### <a name="https-in-docker"></a>Docker 中的 HTTPS

用于 Docker 的 Microsoft 基础映像将 `ASPNETCORE_URLS` 环境变量设置为 `http://+:80`，这意味着 Kestrel 将在该端口上不带 HTTPS 运行。 如果你使用的是带有自定义证书的 HTTPS （如[前一部分](self-hosted.md)中所述），则应通过**在 Dockerfile 的运行时映像创建部分**设置环境变量来替代此设置。

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>.Dockerignore 文件

与从源代码管理中排除某些文件和目录 `.gitignore` 文件非常相似，`.dockerignore` 文件可用于在生成过程中排除文件和目录被复制到映像。 这不仅节省了时间复制，还可以避免由于将 `obj` 目录从 PC 复制到映像中而导致的一些混乱的错误。 应将 `bin` 和 `obj` 的条目至少添加到 `.dockerignore` 文件中。

```console
bin/
obj/
```

## <a name="build-the-image"></a>生成映像

对于具有单个应用程序的解决方案，因此，如果是单个 Dockerfile，则最简单的方法是将 Dockerfile 放在基目录中;这就是与 `.sln` 文件相同的目录。 在这种情况下，若要生成映像，请在包含 Dockerfile 的目录中使用以下 `docker build` 命令。

```console
docker build --tag stockdata .
```

名为 `--tag` 标志的令困惑（可将其缩短为 `-t`）指定图像的整个名称，*包括*实际标记（如果指定）。 末尾处的 `.` 指定将在其中运行生成的*上下文*;Dockerfile 中 `COPY` 命令的当前工作目录。

如果一个解决方案中有多个应用程序，则可以将每个应用程序的 Dockerfile 保存在其自己的文件夹中的 `.csproj` 文件旁边，但你仍应该从基本目录运行 `docker build` 命令，以确保将解决方案和所有项目都复制到该映像。 可以使用 `--file` （或 `-f`）标志在当前目录下指定 Dockerfile。

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>在计算机上的容器中运行映像

若要在本地 Docker 实例中运行映像，请使用 `docker run` 命令。

```console
docker run -ti -p 5000:80 stockdata
```

`-ti` 标志将当前终端连接到容器的终端并在交互模式下运行。 `-p 5000:80` 将容器上的端口80发布（链接）到 localhost 网络接口上的端口80。

## <a name="push-the-image-to-a-registry"></a>将映像推送到注册表

验证映像是否正常工作后，需要将其推送到 Docker 注册表，使其在其他系统上可用。 内部网络将需要预配 Docker 注册表。 这就像运行[Docker 自己的 `registry` 映像](https://docs.docker.com/registry/deploying/)一样简单（即 docker 注册表在 docker 容器中运行），但有多种更全面的解决方案可用。 对于外部共享和云使用，有多种可用的托管注册表，如[Azure 容器注册表](https://docs.microsoft.com/azure/container-registry/)或[Docker Hub](https://docs.docker.com/docker-hub/repos/)。

若要推送到 Docker 中心，请在映像名称后加上用户或组织名称。

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

若要推送到专用注册表，请使用注册表主机名和组织名称作为映像名称的前缀。

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

映像进入注册表后，可将其部署到各个 Docker 主机或容器业务流程引擎（如 Kubernetes）。

>[!div class="step-by-step"]
>[上一页](self-hosted.md)
>[下一页](kubernetes.md)
