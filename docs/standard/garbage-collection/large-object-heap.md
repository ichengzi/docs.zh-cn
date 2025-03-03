---
title: Windows 系统上的大型对象堆
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 618db9faff137e6ff0f878c928e3a889cff37838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120939"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Windows 系统上的大型对象堆

.NET 垃圾回收器 (GC) 将对象分为小型和大型对象。 如果是大型对象，它的某些特性将比对象较小时显得更为重要。 例如，压缩大型对象（也就是在内存中将其复制到堆上的其他地方）的费用相当高。 因此，.NET 垃圾回收器将大型对象放置在大型对象堆 (LOH) 上。 在本主题中，我们将深度探讨大型对象堆。 我们将讨论符合什么条件的对象才能称之为大型对象，如何回收这些大型对象，以及大型对象具备哪些性能意义。

> [!IMPORTANT]
> 本主题仅讨论 .NET Framework 中的大型对象堆和 Windows 系统上运行的 .NET Core。 不包括在其他平台上的 .NET 实现上运行的 LOH。

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>对象如何在大型对象堆上结束以及 GC 如何处理它们

如果对象大于或等于 85,000 字节，将被视为大型对象。 此数字根据性能优化确定。 对象分配请求为 85,000 字节或更大时，运行时会将其分配到大型对象堆。

若要了解其意义，可查看 .NET GC 的部分相关基础知识。

.NET 垃圾回收器是分代回收器。 它包含三代：第 0 代、第 1 代和第 2 代。 包含 3 代的原因是，在优化良好的应用中，大部分对象都在第 0 代就清除了。 例如，在服务器应用中，与每个请求相关的分配应在请求完成后清除。 仍存在的分配请求将转到第 1 代，并在那里进行清除。 从本质上讲，第 1 代是新对象区域与生存期较长的对象区域之间的缓冲区。

小型对象始终在第 0 代中进行分配，或者根据它们的生存期，可能会提升为第 1 代或第 2 代。 大型对象始终在第 2 代中进行分配。

大型对象属于第 2 代，因为只有在第 2 代回收期间才能回收它们。 回收一代时，同时也会回收它前面的所有代。 例如，执行第 1 代 GC 时，将同时回收第 1 代和第 0 代。 执行第 2 代 GC 时，将回收整个堆。 因此，第 2 代 GC 还可称为“完整 GC”  。 本文引用第 2 代 GC 而不是完整 GC，但这两个术语是可以互换的。

代可提供 GC 堆的逻辑视图。 实际上，对象存在于托管堆段中。 托管堆段是 GC 通过调用 [VirtualAlloc 功能](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)代表托管代码在操作系统上保留的内存块  。 加载 CLR 时，GC 分配两个初始堆段：一个用于小型对象（小型对象堆或 SOH），一个用于大型对象（大型对象堆）。

然后，通过将托管对象置于这些托管堆段上来满足分配请求。 如果该对象小于 85,000 字节，则将它置于 SOH 的段上，否则，将它置于 LOH 段。 随着分配到各段上的对象越来越多，会以较小块的形式提交这些段。
对于 SOH，GC 未处理的对象将提升为下一代。 第 0 代回收未处理的对象现在视为第 1 代对象，以此类推。 但是，最后一代回收未处理的对象仍会被视为最后一代中的对象。 也就是说，第 2 代垃圾回收未处理的对象仍是第 2 代对象；LOH 未处理的对象仍是 LOH 对象（由第 2 代回收）。

用户代码只能在第 0 代（小型对象）或 LOH（大型对象）中分配。 只有 GC 可以在第 1 代（通过提升第 0 代回收未处理的对象）和第 2 代（通过提升第 1 代和第 2 代回收未处理的对象）中“分配”对象。

触发垃圾回收后，GC 将寻找存在的对象并将它们压缩。 但是由于压缩费用很高，GC 会扫过 LOH，列出没有被清除的对象列表以供以后重新使用，从而满足大型对象的分配请求  。 相邻的被清除对象将组成一个自由对象。

.NET Core 和 .NET Framework（从 .NET Framework 4.5.1 开始）包括 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> 属性，该属性可让用户指定在下一完整阻止 GC 期间压缩 LOH。 并且在以后，.NET 可能会自动决定压缩 LOH。 这就意味着，如果分配了大型对象并希望确保它们不被移动，则应将其固定起来。

图 1 说明了一种情况，在第一次第 0 代 GC 后 GC 形成了第 1 代，其中 `Obj1` 和 `Obj3` 被清除；在第一次第 1 代 GC 后形成了第 2 代，其中 `Obj2` 和 `Obj5` 被清除。 请注意此图和下图仅用于说明，它们只包含能更好展示堆上的情况的极少几个对象。 实际上，GC 中通常包含更多的对象。

![图 1：第 0 代 GC 和第 1 代 GC](media/loh/loh-figure-1.jpg)\
图 1：第 0 代和第 1 代 GC。

图 2 显示了第 2 代 GC 发现 `Obj1` 和 `Obj2` 被清除后，GC 在内存中形成了相邻的可用空间，由 `Obj1` 和 `Obj2` 占用，然后用于满足 `Obj4` 的分配要求。 从最后一个对象 `Obj3` 到此段末尾的空间仍可用于满足分配请求。

![图 2：第 2 代 GC 后](media/loh/loh-figure-2.jpg)\
图 2：第 2 代 GC 后

如果没有足够的可用空间来容纳大型对象分配请求，GC 首先尝试从操作系统获取更多段。 如果失败了，它将触发第 2 代 GC，试图释放部分空间。

在第 1 代或第 2 代 GC 期间，垃圾回收器会通过调用 [VirtualFree 功能](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)将不包含活动对象的段释放回操作系统。 将退回最后一个活动对象到段末尾的空间（第 0 代/第 1 代存在的短暂段上的空间除外，垃圾回收器会在该段上会保存部分提交内容，因为应用程序将在其中立即分配）。 而且，尽管已重置可用空间，但仍会提交它们，这意味着操作系统无需将其中的数据重新写入磁盘。

由于 LOH 仅在第 2 代 GC 期间进行回收，所以 LOH 段仅在此类 GC 期间可用。 图 3 说明了一种情况，在此情况下，垃圾回收器将某段（段 2）释放回操作系统并且退回剩余段上更多的空间。 如果需要使用该段末尾的已退回空间来满足大型对象分配请求，它会再次提交该内存。 （有关提交/退回的解释说明，请参阅 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 的文档）。

![图 3：第 2 代 GC 后的 LOH](media/loh/loh-figure-3.jpg)\
图 3：第 2 代 GC 后的 LOH

## <a name="when-is-a-large-object-collected"></a>何时收集大型对象？

通常情况下，出现以下三种情形中的任一情况，都会执行 GC：

- 分配超出第 0 代或大型对象阈值。

  阈值是某代的属性。 垃圾回收器在其中分配对象时，会为代设置阈值。 超出阈值后，会在该代上触发 GC。 因此，分配小型或大型对象时，需要分别使用第 0 代和 LOH 的阈值。 当垃圾回收器分配到第 1 代和第 2 代中时，将使用它们的阈值。 运行此程序时，会动态调整这些阈值。

  这是典型情况，大部分 GC 执行都因为托管堆上的分配。

- 调用 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法。

  如果调用无参数 <xref:System.GC.Collect?displayProperty=nameWithType> 方法，或另一个重载作为参数传递到 <xref:System.GC.MaxGeneration?displayProperty=nameWithType>，将会一起收集 LOH 和剩余的托管堆。

- 系统处于内存不足的状况。

  垃圾回收器收到来自操作系统 的高内存通知时，会发生以上情况。 如果垃圾回收器认为执行第 2 代 GC 会有效率，它将触发第 2 代。

## <a name="loh-performance-implications"></a>LOH 性能意义

大型对象堆上的分配通过以下几种方式影响性能。

- 分配成本。

  CLR 确保清除了它提供的每个新对象的内存。 这意味着大型对象的分配成本完全由清理的内存（除非触发了 GC）决定。 如果需要 2 轮才能清除一个字节，即需要 170,000 轮才能清除最小的大型对象。 清除 2GHz 计算机上 16MB 对象的内存大约需要 16ms。 这些成本相当大。

- 回收成本。

  因为 LOH 和第 2 代一起回收，如果超出了它们之中任何一个的阈值，则触发第 2 代回收。 如果由于 LOH 触发第 2 代回收，第 2 代没有必要在 GC 后变得更小。 如果第 2 代上数据不多，则影响较小。 但是，如果第 2 代很大，则触发多次第 2 代 GC 可能会产生性能问题。 如果很多大型对象都在非常短暂的基础上进行分配，并且拥有大型 SOH，则可能会花费太多时间来执行 GC。 除此之外，如果连续分配并且释放真正的大型对象，那么分配成本可能会增加。

- 具有引用类型的数组元素。

  LOH 上的特大型对象通常是数组（很少会有非常大的实例对象）。 如果数组的元素有丰富的引用，则可能产生成本；如果元素没有丰富的引用，将不会产生此类成本。 如果元素不包含任何引用，则垃圾回收器根本无需处理此数组。 例如，如果使用数组存储二进制树中的节点，一种实现方法是按实际节点引用某个节点的左侧节点和右侧节点：

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  如果 `num_nodes` 非常大，则垃圾回收器需要处理每个元素的至少两个引用。 另一种方法是存储左侧节点和右侧节点的索引：

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  不要将左侧节点的数据引用为 `left.d`，而是将其引用为 `binary_tr[left_index].d`。 而垃圾回收器无需查看左侧节点和右侧节点的任何引用。

在这三种因素中，前两个通常比第三个更重要。 因此，建议分配重复使用的大型对象池，而不是分配临时大型对象。

## <a name="collecting-performance-data-for-the-loh"></a>收集 LOH 的性能数据

收集特定区域的性能数据之前，应完成以下操作：

1. 找到应查看此区域的证据。

2. 排查你知道的其他区域，确保未发现可解释上述性能问题的内容。

参阅博客[尝试找出解决方案之前先了解问题](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/)获取内存和 CPU 的基础知识的详细信息。

可使用以下工具来收集 LOH 性能数据：

- [.NET CLR 内存性能计数器](#net-clr-memory-performance-counters)

- [ETW 事件](#etw-events)

- [调试器](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>.NET CLR 内存性能计数器

这些性能计数器通常是调查性能问题的第一步（但是推荐使用 [ETW 事件](#etw-events)）。 通过添加所需计数器配置性能监视器，如图 4 所示。 与 LOH 相关的是：

- 第 2 代回收次数 

   显示自进程开始起第 2 代 GC 发生的次数。 此计数器在第 2 代回收结束时递增（也称为完整垃圾回收）。 此计数器显示上次观测的值。

- **大型对象堆大小**

   以字节显示当前大小，包括 LOH 的可用空间。 此计数器在垃圾回收结束时更新，不在每次分配时更新。

查看性能计数器的常用方法是使用性能监视器 (perfmon.exe)。 使用“添加计数器”可为关注的进程添加感兴趣的计数器。 可将性能计数器数据保存在日志文件中，如图 4 所示：

![屏幕截图显示了如何添加性能计数器。](media/large-object-heap/add-performance-counter.png)
图 4：第 2 代 GC 后的 LOH

也可以编程方式查询性能计数器。 大部分人在例行测试过程中都采用此方式进行收集。 如果发现计数器显示的值不正常，则可以使用其他方法获得更多详细信息以帮助调查。

> [!NOTE]
> 建议使用 ETW 事件代替性能计数，因为 ETW 提供更丰富的信息。

### <a name="etw-events"></a>ETW 事件

垃圾回收器提供丰富的 ETW 事件集，帮助了解堆的工作内容和工作原理。 以下博客文章演示了如何使用 ETW 收集和了解 GC 事件：

- [GC ETW 事件 - 1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [GC ETW 事件 - 2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [GC ETW 事件 - 3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [GC ETW 事件 - 4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

若要标识由临时 LOH 分配造成的过多第 2 代 GC 次数，请查看 GC 的“触发原因”列。 有关仅分配临时大型对象的简单测试，可使用以下 [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) 命令行收集 ETW 事件的信息：

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

结果类似于以下类容：

![屏幕截图显示了 PerfView 中的 ETW 事件。](media/large-object-heap/event-tracing-windows-perfview.png)
图 5：使用 PerfView 显示的 ETW 事件

如下所示，所有 GC 都是第 2 代 GC，并且都由 AllocLarge 触发，这表示分配大型对象会触发此 GC。 我们知道这些分配是临时的，因为“LOH 未清理率 %”列显示为 1%  。

可以收集显示分配这些大写对象的人员的其他 ETW 事件。 以下命令行：

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

收集 AllocationTick 事件，大约每 10 万次分配就会触发该事件。 换句话说，每次分配大型对象都会触发事件。 然后可查看某个 GC 堆分配视图，该视图显示分配大型对象的调用堆栈：

![屏幕截图显示了垃圾回收器堆视图。](media/large-object-heap/garbage-collector-heap.png)
图 6：GC 堆分配视图

如图所示，这是从 `Main` 方法分配大型对象的简单测试。

### <a name="a-debugger"></a>调试器

如果只有内存转储，则需要查看 LOH 上实际有哪些对象，你可使用 .NET 提供的 [SoS 调试器扩展](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md)来查看。

> [!NOTE]
> 此部分提到的调试命令适用于 [Windows 调试器](https://www.microsoft.com/whdc/devtools/debugging/default.mspx)。

以下内容显示了分析 LOH 的示例输出：

```console
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

LOH 堆大小为 (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 字节。 在地址 023e1000 和地址 033db630 之间，8,008,736 字节由 <xref:System.Object?displayProperty=nameWithType> 对象的数组占用，6,663,696 字节由 <xref:System.Byte?displayProperty=nameWithType> 对象的数组占用，2,081,792 字节由可用空间占用。

有时，调试器显示 LOH 的总大小少于 85,000 个字节。 这是由于运行时本身使用 LOH 分配某些小于大型对象的对象引起的。

因为不会压缩 LOH，有时会怀疑 LOH 是碎片源。 碎片表示：

- 托管堆的碎片由托管对象之间的可用空间量来表示。 在 SoS 中，`!dumpheap –type Free` 命令显示托管对象之间的可用空间量。

- 虚拟内存 (VM) 地址空间的碎片是标识为 `MEM_FREE` 的内存。 可在 windbg 中使用各种调试器命令来获取碎片。

   以下示例显示 VM 空间中的碎片：

   ```console
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

通常看到的更多是由临时大型对象导致的 VM 碎片，这些对象要求垃圾回收器频繁从操作系统获取新的托管堆段，并将空托管堆段释放回操作系统。

要验证 LOH 是否会生成 VM 碎片，可在 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 和 [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) 上设置一个断点，查看是谁调用了它们。 例如，如果想知道谁曾尝试从操作系统分配大于 8MBB 的虚拟内存块，可按以下方式设置断点：

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

只有在分配大小大于 8MB (0x800000) 的情况下调用 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 时，此命令才会进入调试器并显示调用堆栈。

CLR 2.0 增加了称为“VM 囤积”的功能，用于频繁获取和释放段（包括在大型和小型对象堆上）的情况  。 若要指定 VM 囤积，可通过托管 API 指定称为 `STARTUP_HOARD_GC_VM` 的启动标记。 CLR 退回这些段上的内存并将其添加到备用列表中，而不会将该空段释放回操作系统。 （请注意 CLR 不会针对太大型的段执行此操作。）CLR 稍后将使用这些段来满足新段请求。 下一次应用需要新段时，CLR 将使用此备用列表中的某个足够大的段。

VM 囤积还可用于想要保存已获取的段的应用程序（例如属于系统上运行的主要应用的部分服务器应用），以避免内存不足的异常。

强烈建议你在使用此功能时认真测试应用程序，以确保应用程序的内存使用情况比较稳定。
