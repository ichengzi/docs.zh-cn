---
title: GetWin32ResBlob 方法
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: ff3103a46390c880a56ff443bfe20744f2ba0bfd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430690"
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob 方法
Retrieves Win32 resource blob. Call this method after setting assembly options.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a>参数  
 `AssemblyID`  
 ID of the assembly.  
  
 `FileToken`  
 File token used to retrieve the filename to be used when constructing the Win32 Version resource  
  
 `fDll`  
 TRUE if file is a DLL, false for an EXE.  
  
 `pszIconFile`  
 Optional icon to insert into the resource blob.  
  
 `ppResBlob`  
 Receives the resource blob.  
  
 `pcbResBlob`  
 Receives the size of the blob.  
  
## <a name="return-value"></a>返回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>要求  
 Requires alink.h  
  
## <a name="see-also"></a>请参阅

- [IALink 接口](ialink-interface.md)
- [IALink2 接口](ialink2-interface.md)
- [ALink API](index.md)
