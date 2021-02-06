---
description: 'Дополнительные сведения о: интерфейс ICorDebugProcess4'
title: Интерфейс ICorDebugProcess4
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 16c7f3fbd1a79b1406fe0c19a9d922964667a2a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650005"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="1378f-103">Интерфейс ICorDebugProcess4</span><span class="sxs-lookup"><span data-stu-id="1378f-103">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="1378f-104">Обеспечивает поддержку управления выполнением в процессе.</span><span class="sxs-lookup"><span data-stu-id="1378f-104">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="1378f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="1378f-105">Methods</span></span>

| <span data-ttu-id="1378f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="1378f-106">Method</span></span>                                                                 | <span data-ttu-id="1378f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="1378f-107">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="1378f-108">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="1378f-108">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="1378f-109">Уведомляет конвейер ICorDebug о том, что отладчик out-Process продолжает выполнение отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="1378f-109">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1378f-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1378f-110">Remarks</span></span>

<span data-ttu-id="1378f-111">Этот интерфейс находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="1378f-111">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="1378f-112">Однако это COM-интерфейс, производный от `IUnknown` GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , который можно получить с помощью стандартных механизмов com.</span><span class="sxs-lookup"><span data-stu-id="1378f-112">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="1378f-113">Требования</span><span class="sxs-lookup"><span data-stu-id="1378f-113">Requirements</span></span>

<span data-ttu-id="1378f-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1378f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1378f-115">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="1378f-115">**Header:** None</span></span>

<span data-ttu-id="1378f-116">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="1378f-116">**Library:** None</span></span>

<span data-ttu-id="1378f-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1378f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1378f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="1378f-118">See also</span></span>

- [<span data-ttu-id="1378f-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1378f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1378f-120">Отладка</span><span class="sxs-lookup"><span data-stu-id="1378f-120">Debugging</span></span>](index.md)
