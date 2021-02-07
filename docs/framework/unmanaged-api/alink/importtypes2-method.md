---
description: Дополнительные сведения о методе ImportTypes2
title: Метод ImportTypes2
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
ms.openlocfilehash: ca0d174061608f9b4abf524c43023e867e9a9646
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662615"
---
# <a name="importtypes2-method"></a><span data-ttu-id="5d1db-103">Метод ImportTypes2</span><span class="sxs-lookup"><span data-stu-id="5d1db-103">ImportTypes2 Method</span></span>

<span data-ttu-id="5d1db-104">Инициирует импорт типов.</span><span class="sxs-lookup"><span data-stu-id="5d1db-104">Initiates the import of types.</span></span> <span data-ttu-id="5d1db-105">Вызовите этот метод, чтобы начать импорт типов из каждой области, импортированной с помощью [метода ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d1db-105">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d1db-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5d1db-106">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d1db-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="5d1db-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="5d1db-108">Идентификатор сборки, в которую необходимо выполнить импорт.</span><span class="sxs-lookup"><span data-stu-id="5d1db-108">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="5d1db-109">Идентификатор файла для импорта.</span><span class="sxs-lookup"><span data-stu-id="5d1db-109">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="5d1db-110">Отсчитываемая от нуля область, из которой производится импорт.</span><span class="sxs-lookup"><span data-stu-id="5d1db-110">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="5d1db-111">Получает обработчик перечислителя для типов в заданной области.</span><span class="sxs-lookup"><span data-stu-id="5d1db-111">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="5d1db-112">При необходимости получает интерфейс интерфейса [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5d1db-112">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="5d1db-113">При необходимости получает число типов в указанной области.</span><span class="sxs-lookup"><span data-stu-id="5d1db-113">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d1db-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5d1db-114">Return Value</span></span>  

 <span data-ttu-id="5d1db-115">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="5d1db-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d1db-116">Требования</span><span class="sxs-lookup"><span data-stu-id="5d1db-116">Requirements</span></span>  

 <span data-ttu-id="5d1db-117">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="5d1db-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1db-118">См. также</span><span class="sxs-lookup"><span data-stu-id="5d1db-118">See also</span></span>

- [<span data-ttu-id="5d1db-119">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="5d1db-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5d1db-120">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="5d1db-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5d1db-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="5d1db-121">ALink API</span></span>](index.md)
