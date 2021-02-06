---
description: Дополнительные сведения о методе AddImport
title: Метод AddImport
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 9dca26501e66313b0932caf1288db7c909154e1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638604"
---
# <a name="addimport-method"></a><span data-ttu-id="503a2-103">Метод AddImport</span><span class="sxs-lookup"><span data-stu-id="503a2-103">AddImport Method</span></span>

<span data-ttu-id="503a2-104">Добавляет в сборку импорты.</span><span class="sxs-lookup"><span data-stu-id="503a2-104">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503a2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="503a2-105">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="503a2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="503a2-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="503a2-107">Уникальный идентификатор сборки для дополнения.</span><span class="sxs-lookup"><span data-stu-id="503a2-107">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="503a2-108">Уникальный идентификатор, полученный из [метода ImportFile](importfile-method.md)импортируемого файла.</span><span class="sxs-lookup"><span data-stu-id="503a2-108">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="503a2-109">COM+ Филедеф флаги, такие как `ffContainsNoMetaData` и `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="503a2-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="503a2-110">`dwFlags` передается [методу дефинефиле](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="503a2-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="503a2-111">Указатель на токен, который получает идентификатор для результирующего файла.</span><span class="sxs-lookup"><span data-stu-id="503a2-111">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="503a2-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="503a2-112">Return Value</span></span>  

 <span data-ttu-id="503a2-113">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="503a2-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="503a2-114">Требования</span><span class="sxs-lookup"><span data-stu-id="503a2-114">Requirements</span></span>  

 <span data-ttu-id="503a2-115">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="503a2-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503a2-116">См. также</span><span class="sxs-lookup"><span data-stu-id="503a2-116">See also</span></span>

- [<span data-ttu-id="503a2-117">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="503a2-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="503a2-118">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="503a2-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="503a2-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="503a2-119">ALink API</span></span>](index.md)
