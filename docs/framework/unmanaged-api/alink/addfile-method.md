---
description: Дополнительные сведения о методе AddFile
title: Метод AddFile
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
ms.openlocfilehash: 5e1253587298b2c1559c72dced43ec70dc169090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638630"
---
# <a name="addfile-method"></a><span data-ttu-id="37a6b-103">Метод AddFile</span><span class="sxs-lookup"><span data-stu-id="37a6b-103">AddFile Method</span></span>

<span data-ttu-id="37a6b-104">Добавляет файлы в сборку.</span><span class="sxs-lookup"><span data-stu-id="37a6b-104">Adds files to the assembly.</span></span> <span data-ttu-id="37a6b-105">Также можно использовать для создания непривязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="37a6b-105">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37a6b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37a6b-106">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="37a6b-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="37a6b-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="37a6b-108">Уникальный идентификатор сборки, подлежащая дополну.</span><span class="sxs-lookup"><span data-stu-id="37a6b-108">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="37a6b-109">Полное имя добавляемого файла.</span><span class="sxs-lookup"><span data-stu-id="37a6b-109">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="37a6b-110">COM+ Филедеф флаги, такие как `ffContainsNoMetaData` и `ffWriteable` .</span><span class="sxs-lookup"><span data-stu-id="37a6b-110">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="37a6b-111">`dwFlags` передается [методу дефинефиле](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="37a6b-111">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="37a6b-112">Интерфейс [IMetaDataEmit](../metadata/imetadataemit-interface.md) , используемый для выдачи метаданных при необходимости.</span><span class="sxs-lookup"><span data-stu-id="37a6b-112">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="37a6b-113">Указатель на место, где будет храниться уникальный идентификатор добавленного файла.</span><span class="sxs-lookup"><span data-stu-id="37a6b-113">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37a6b-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="37a6b-114">Return Value</span></span>  

 <span data-ttu-id="37a6b-115">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="37a6b-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37a6b-116">Требования</span><span class="sxs-lookup"><span data-stu-id="37a6b-116">Requirements</span></span>  

 <span data-ttu-id="37a6b-117">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="37a6b-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a6b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="37a6b-118">See also</span></span>

- [<span data-ttu-id="37a6b-119">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="37a6b-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="37a6b-120">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="37a6b-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="37a6b-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="37a6b-121">ALink API</span></span>](index.md)
