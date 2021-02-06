---
description: Дополнительные сведения о методе ExportTypeForwarder
title: Метод ExportTypeForwarder
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
ms.openlocfilehash: 59fb74c83f6d30dda87d908353795fb218190022
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637993"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="c5c00-103">Метод ExportTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="c5c00-103">ExportTypeForwarder Method</span></span>

<span data-ttu-id="c5c00-104">Добавляет сервер пересылки типа в таблицу типов данной сборки.</span><span class="sxs-lookup"><span data-stu-id="c5c00-104">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c00-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c5c00-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5c00-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c5c00-106">Parameters</span></span>  

 `tkAssemblyRef`  
 <span data-ttu-id="c5c00-107">Ссылка на сборку, к которой относится перенаправитель типа.</span><span class="sxs-lookup"><span data-stu-id="c5c00-107">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="c5c00-108">Полное имя типа для экспорта.</span><span class="sxs-lookup"><span data-stu-id="c5c00-108">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c5c00-109">`ComType` Флаги, такие как `tdPublic` или `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="c5c00-109">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="c5c00-110">Это значение может быть передано [методу дефиникспортедтипе](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="c5c00-110">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="c5c00-111">Получает токен экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="c5c00-111">Receives the token of the exported type.</span></span> <span data-ttu-id="c5c00-112">Это необходимо только для выпуска вложенных типов.</span><span class="sxs-lookup"><span data-stu-id="c5c00-112">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5c00-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c5c00-113">Return Value</span></span>  

 <span data-ttu-id="c5c00-114">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="c5c00-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c00-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c5c00-115">Requirements</span></span>  

 <span data-ttu-id="c5c00-116">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="c5c00-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c00-117">См. также</span><span class="sxs-lookup"><span data-stu-id="c5c00-117">See also</span></span>

- [<span data-ttu-id="c5c00-118">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="c5c00-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c5c00-119">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="c5c00-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c5c00-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="c5c00-120">ALink API</span></span>](index.md)
