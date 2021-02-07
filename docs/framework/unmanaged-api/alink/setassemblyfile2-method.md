---
description: Дополнительные сведения о методе SetAssemblyFile2
title: Метод SetAssemblyFile2
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 890646b718c211b476d013daf021f8889198c1ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662407"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="6fe31-103">Метод SetAssemblyFile2</span><span class="sxs-lookup"><span data-stu-id="6fe31-103">SetAssemblyFile2 Method</span></span>

<span data-ttu-id="6fe31-104">Задает имя параметров и для новой сборки.</span><span class="sxs-lookup"><span data-stu-id="6fe31-104">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="6fe31-105">Не вызывайте этот метод при создании несвязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="6fe31-105">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe31-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6fe31-106">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fe31-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="6fe31-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="6fe31-108">Имя файла манифеста.</span><span class="sxs-lookup"><span data-stu-id="6fe31-108">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="6fe31-109">Интерфейс интерфейса [IMetaDataEmit2](../metadata/imetadataemit2-interface.md) для этого файла.</span><span class="sxs-lookup"><span data-stu-id="6fe31-109">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="6fe31-110">Параметры, представленные [перечислением AssemblyFlags](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6fe31-110">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="6fe31-111">Получает уникальный идентификатор для создаваемой сборки.</span><span class="sxs-lookup"><span data-stu-id="6fe31-111">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fe31-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6fe31-112">Return Value</span></span>  

 <span data-ttu-id="6fe31-113">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="6fe31-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fe31-114">Требования</span><span class="sxs-lookup"><span data-stu-id="6fe31-114">Requirements</span></span>  

 <span data-ttu-id="6fe31-115">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="6fe31-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe31-116">См. также</span><span class="sxs-lookup"><span data-stu-id="6fe31-116">See also</span></span>

- [<span data-ttu-id="6fe31-117">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="6fe31-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6fe31-118">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="6fe31-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6fe31-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="6fe31-119">ALink API</span></span>](index.md)
