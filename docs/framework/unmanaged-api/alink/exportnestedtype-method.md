---
description: Дополнительные сведения о методе Експортнестедтипе
title: Метод ExportNestedType
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: 66cf4c3572857a0e7e99efa966cdb0b9ae2be673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638148"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="56ebb-103">Метод ExportNestedType</span><span class="sxs-lookup"><span data-stu-id="56ebb-103">ExportNestedType Method</span></span>

<span data-ttu-id="56ebb-104">Указывает вложенные типы как экспортируемые.</span><span class="sxs-lookup"><span data-stu-id="56ebb-104">Specifies nested types as exportable.</span></span> <span data-ttu-id="56ebb-105">[Метод ExportType](exporttype-method.md) также может экспортировать вложенные типы, но этот метод выполняется быстрее.</span><span class="sxs-lookup"><span data-stu-id="56ebb-105">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ebb-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="56ebb-106">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="56ebb-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="56ebb-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="56ebb-108">Идентификатор сборки, из которой производится экспорт.</span><span class="sxs-lookup"><span data-stu-id="56ebb-108">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="56ebb-109">Маркер файла или сборка файла, определяющая тип, который должен быть сделан экспортируемым.</span><span class="sxs-lookup"><span data-stu-id="56ebb-109">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="56ebb-110">Токен типа, который должен быть доступен для экспорта.</span><span class="sxs-lookup"><span data-stu-id="56ebb-110">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="56ebb-111">Токен родительского типа.</span><span class="sxs-lookup"><span data-stu-id="56ebb-111">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="56ebb-112">Полное имя типа для экспорта.</span><span class="sxs-lookup"><span data-stu-id="56ebb-112">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="56ebb-113">`ComType` Флаги, такие как `tdPublic` или `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="56ebb-113">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="56ebb-114">Это значение может быть передано [методу дефиникспортедтипе](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="56ebb-114">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="56ebb-115">Получает токен для экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="56ebb-115">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56ebb-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="56ebb-116">Return Value</span></span>  

 <span data-ttu-id="56ebb-117">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="56ebb-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56ebb-118">Требования</span><span class="sxs-lookup"><span data-stu-id="56ebb-118">Requirements</span></span>  

 <span data-ttu-id="56ebb-119">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="56ebb-119">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ebb-120">См. также</span><span class="sxs-lookup"><span data-stu-id="56ebb-120">See also</span></span>

- [<span data-ttu-id="56ebb-121">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="56ebb-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="56ebb-122">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="56ebb-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="56ebb-123">API ALink</span><span class="sxs-lookup"><span data-stu-id="56ebb-123">ALink API</span></span>](index.md)
