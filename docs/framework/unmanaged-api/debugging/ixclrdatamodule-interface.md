---
description: 'Дополнительные сведения о: интерфейс Иксклрдатамодуле'
title: Интерфейс IXCLRDataModule
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 403d4dd3db64f2855347562da7217a3562985c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800751"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="66a87-103">Интерфейс IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="66a87-103">IXCLRDataModule Interface</span></span>

<span data-ttu-id="66a87-104">Предоставляет методы для запроса сведений о загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="66a87-104">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="66a87-105">Методы</span><span class="sxs-lookup"><span data-stu-id="66a87-105">Methods</span></span>

| <span data-ttu-id="66a87-106">Метод</span><span class="sxs-lookup"><span data-stu-id="66a87-106">Method</span></span>                                                                                                                                | <span data-ttu-id="66a87-107">Описание</span><span class="sxs-lookup"><span data-stu-id="66a87-107">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="66a87-108">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="66a87-108">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="66a87-109">Возвращает определение метода, соответствующее заданному маркеру метаданных.</span><span class="sxs-lookup"><span data-stu-id="66a87-109">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="66a87-110">Запрос</span><span class="sxs-lookup"><span data-stu-id="66a87-110">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="66a87-111">Запросы на заполнение буфера данными модуля.</span><span class="sxs-lookup"><span data-stu-id="66a87-111">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="66a87-112">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="66a87-112">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="66a87-113">Возвращает идентификатор версии модуля.</span><span class="sxs-lookup"><span data-stu-id="66a87-113">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="66a87-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="66a87-114">Remarks</span></span>

<span data-ttu-id="66a87-115">Этот интерфейс находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="66a87-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="66a87-116">Однако это COM-интерфейс, производный от `IUnknown` GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` , который можно получить с помощью стандартных механизмов com.</span><span class="sxs-lookup"><span data-stu-id="66a87-116">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="66a87-117">Требования</span><span class="sxs-lookup"><span data-stu-id="66a87-117">Requirements</span></span>

<span data-ttu-id="66a87-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a87-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="66a87-119">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="66a87-119">**Header:** None</span></span>  
<span data-ttu-id="66a87-120">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="66a87-120">**Library:** None</span></span>  
<span data-ttu-id="66a87-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66a87-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="66a87-122">См. также</span><span class="sxs-lookup"><span data-stu-id="66a87-122">See also</span></span>

- [<span data-ttu-id="66a87-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="66a87-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="66a87-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="66a87-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
