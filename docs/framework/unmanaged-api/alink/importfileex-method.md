---
description: Дополнительные сведения о методе Импортфиликс
title: Метод ImportFileEx
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
ms.openlocfilehash: a8a7e5a142091bf7cc93f50a4ae20c59d800f3ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718022"
---
# <a name="importfileex-method"></a><span data-ttu-id="3991b-103">Метод ImportFileEx</span><span class="sxs-lookup"><span data-stu-id="3991b-103">ImportFileEx Method</span></span>

<span data-ttu-id="3991b-104">Импортирует указанную сборку или непривязанный модуль.</span><span class="sxs-lookup"><span data-stu-id="3991b-104">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3991b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3991b-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3991b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3991b-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="3991b-107">Полное имя файла, из которого необходимо выполнить импорт.</span><span class="sxs-lookup"><span data-stu-id="3991b-107">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="3991b-108">Необязательное имя целевого файла.</span><span class="sxs-lookup"><span data-stu-id="3991b-108">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="3991b-109">Если значение равно TRUE, используется ImportTypes, в противном случае импорт должен выполняться вручную.</span><span class="sxs-lookup"><span data-stu-id="3991b-109">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="3991b-110">Флаги, передаваемые в [метод OpenScope](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="3991b-110">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="3991b-111">Получает идентификатор импортируемого файла.</span><span class="sxs-lookup"><span data-stu-id="3991b-111">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="3991b-112">Получает интерфейс [интерфейса IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) для области импорта сборки.</span><span class="sxs-lookup"><span data-stu-id="3991b-112">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="3991b-113">Имеет значение NULL, если файл не является сборкой.</span><span class="sxs-lookup"><span data-stu-id="3991b-113">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="3991b-114">Получает число импортированных файлов и (или) областей.</span><span class="sxs-lookup"><span data-stu-id="3991b-114">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3991b-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3991b-115">Return Value</span></span>  

 <span data-ttu-id="3991b-116">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3991b-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3991b-117">Требования</span><span class="sxs-lookup"><span data-stu-id="3991b-117">Requirements</span></span>  

 <span data-ttu-id="3991b-118">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="3991b-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3991b-119">См. также</span><span class="sxs-lookup"><span data-stu-id="3991b-119">See also</span></span>

- [<span data-ttu-id="3991b-120">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="3991b-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3991b-121">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="3991b-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3991b-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="3991b-122">ALink API</span></span>](index.md)
