---
description: Дополнительные сведения о методе ImportTypes
title: Метод ImportTypes
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 9a30c735ca2c9ad0f945628c3de1eb1bb56efe2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662628"
---
# <a name="importtypes-method"></a><span data-ttu-id="8e17d-103">Метод ImportTypes</span><span class="sxs-lookup"><span data-stu-id="8e17d-103">ImportTypes Method</span></span>

<span data-ttu-id="8e17d-104">Инициирует импорт типов из каждой области, импортированной с помощью [метода ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="8e17d-104">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e17d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8e17d-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e17d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8e17d-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="8e17d-107">Идентификатор сборки, в которую необходимо выполнить импорт.</span><span class="sxs-lookup"><span data-stu-id="8e17d-107">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8e17d-108">Идентификатор файла, из которого необходимо выполнить импорт.</span><span class="sxs-lookup"><span data-stu-id="8e17d-108">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="8e17d-109">Отсчитываемая от нуля область для импорта.</span><span class="sxs-lookup"><span data-stu-id="8e17d-109">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="8e17d-110">Получает обработчики перечислителя для типов в этой области.</span><span class="sxs-lookup"><span data-stu-id="8e17d-110">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="8e17d-111">При необходимости получает интерфейс [интерфейса IMetaDataImport](../metadata/imetadataimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8e17d-111">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="8e17d-112">При необходимости получает число типов в указанной области.</span><span class="sxs-lookup"><span data-stu-id="8e17d-112">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e17d-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8e17d-113">Return Value</span></span>  

 <span data-ttu-id="8e17d-114">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="8e17d-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e17d-115">Требования</span><span class="sxs-lookup"><span data-stu-id="8e17d-115">Requirements</span></span>  

 <span data-ttu-id="8e17d-116">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="8e17d-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e17d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="8e17d-117">See also</span></span>

- [<span data-ttu-id="8e17d-118">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="8e17d-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8e17d-119">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="8e17d-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8e17d-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="8e17d-120">ALink API</span></span>](index.md)
