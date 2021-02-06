---
description: Дополнительные сведения о методе AddFile2
title: Метод AddFile2
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: d53527ecf7e8b3a99a11ea99512fbc812125de3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638617"
---
# <a name="addfile2-method"></a><span data-ttu-id="c8b6d-103">Метод AddFile2</span><span class="sxs-lookup"><span data-stu-id="c8b6d-103">AddFile2 Method</span></span>

<span data-ttu-id="c8b6d-104">Добавляет файлы в сборку.</span><span class="sxs-lookup"><span data-stu-id="c8b6d-104">Adds files to the assembly.</span></span> <span data-ttu-id="c8b6d-105">Также можно использовать для создания непривязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="c8b6d-105">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b6d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c8b6d-106">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8b6d-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="c8b6d-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c8b6d-108">Идентификатор сборки, в которую добавляется файл.</span><span class="sxs-lookup"><span data-stu-id="c8b6d-108">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="c8b6d-109">Имя добавляемого файла.</span><span class="sxs-lookup"><span data-stu-id="c8b6d-109">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c8b6d-110">`FileDef`Флаги com+, такие как `ffContainsNoMetaData` и `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="c8b6d-110">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="c8b6d-111">`dwFlags` передается [методу дефинефиле](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c8b6d-111">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c8b6d-112">Интерфейс для интерфейса интерфейса [IMetaDataEmit2](../metadata/imetadataemit2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c8b6d-112">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="c8b6d-113">Получает идентификатор добавляемого файла.</span><span class="sxs-lookup"><span data-stu-id="c8b6d-113">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8b6d-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c8b6d-114">Return Value</span></span>  

 <span data-ttu-id="c8b6d-115">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="c8b6d-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b6d-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c8b6d-116">Requirements</span></span>  

 <span data-ttu-id="c8b6d-117">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c8b6d-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b6d-118">См. также</span><span class="sxs-lookup"><span data-stu-id="c8b6d-118">See also</span></span>

- [<span data-ttu-id="c8b6d-119">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="c8b6d-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c8b6d-120">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="c8b6d-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c8b6d-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="c8b6d-121">ALink API</span></span>](index.md)
