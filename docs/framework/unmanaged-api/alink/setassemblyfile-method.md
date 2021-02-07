---
description: Дополнительные сведения о методе Сетассемблифиле
title: Метод SetAssemblyFile
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 943e0600b9781aeaf45cc26e39bd8a8b33a783c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662498"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="fcec0-103">Метод SetAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="fcec0-103">SetAssemblyFile Method</span></span>

<span data-ttu-id="fcec0-104">Присваивает имя сборки, которая должна быть построена.</span><span class="sxs-lookup"><span data-stu-id="fcec0-104">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="fcec0-105">Не предназначен для использования при создании непривязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="fcec0-105">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcec0-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fcec0-106">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcec0-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="fcec0-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="fcec0-108">Полное имя файла манифеста.</span><span class="sxs-lookup"><span data-stu-id="fcec0-108">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="fcec0-109">Указатель на интерфейс [интерфейса IMetaDataEmit](../metadata/imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fcec0-109">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="fcec0-110">Флаги, определенные в [перечислении AssemblyFlags](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="fcec0-110">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="fcec0-111">Указатель на идентификатор результирующей сборки.</span><span class="sxs-lookup"><span data-stu-id="fcec0-111">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcec0-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fcec0-112">Return Value</span></span>  

 <span data-ttu-id="fcec0-113">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="fcec0-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcec0-114">Требования</span><span class="sxs-lookup"><span data-stu-id="fcec0-114">Requirements</span></span>  

 <span data-ttu-id="fcec0-115">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="fcec0-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcec0-116">См. также</span><span class="sxs-lookup"><span data-stu-id="fcec0-116">See also</span></span>

- [<span data-ttu-id="fcec0-117">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="fcec0-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="fcec0-118">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="fcec0-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="fcec0-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="fcec0-119">ALink API</span></span>](index.md)
