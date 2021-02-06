---
description: Дополнительные сведения о методе ExportType
title: Метод ExportType
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
ms.openlocfilehash: 6dc047cac3b80e6fe7a6f2cd980061b34bb7f286
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638071"
---
# <a name="exporttype-method"></a><span data-ttu-id="3f7eb-103">Метод ExportType</span><span class="sxs-lookup"><span data-stu-id="3f7eb-103">ExportType Method</span></span>

<span data-ttu-id="3f7eb-104">Указывает, что тип является экспортируемым.</span><span class="sxs-lookup"><span data-stu-id="3f7eb-104">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7eb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3f7eb-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f7eb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3f7eb-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="3f7eb-107">Идентификатор сборки, из которой необходимо выполнить экспорт.</span><span class="sxs-lookup"><span data-stu-id="3f7eb-107">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3f7eb-108">Маркер файла или идентификатор сборки файла, который определяет экспортируемый тип.</span><span class="sxs-lookup"><span data-stu-id="3f7eb-108">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="3f7eb-109">Токен типа, который должен быть сделан экспортируемым.</span><span class="sxs-lookup"><span data-stu-id="3f7eb-109">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="3f7eb-110">Полное имя типа, которое необходимо сделать экспортируемым.</span><span class="sxs-lookup"><span data-stu-id="3f7eb-110">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3f7eb-111">`ComType` Флаги, такие как `tdPublic` или `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="3f7eb-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="3f7eb-112">Этот параметр может быть передан [методу дефиникспортедтипе](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3f7eb-112">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="3f7eb-113">Получает токен для экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="3f7eb-113">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f7eb-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3f7eb-114">Return Value</span></span>  

 <span data-ttu-id="3f7eb-115">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3f7eb-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7eb-116">Требования</span><span class="sxs-lookup"><span data-stu-id="3f7eb-116">Requirements</span></span>  

 <span data-ttu-id="3f7eb-117">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="3f7eb-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7eb-118">См. также</span><span class="sxs-lookup"><span data-stu-id="3f7eb-118">See also</span></span>

- [<span data-ttu-id="3f7eb-119">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="3f7eb-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3f7eb-120">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="3f7eb-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3f7eb-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="3f7eb-121">ALink API</span></span>](index.md)
