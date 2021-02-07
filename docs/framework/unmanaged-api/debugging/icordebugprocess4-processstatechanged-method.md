---
description: 'Дополнительные сведения о методе: ICorDebugProcess4::P Роцессстатечанжед'
title: 'ICorDebugProcess4: метод:P Роцессстатечанжед'
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 35a76b3c6dd9b37d3f06f23bc2ffea82f125a29e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746477"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="6943b-103">ICorDebugProcess4: метод:P Роцессстатечанжед</span><span class="sxs-lookup"><span data-stu-id="6943b-103">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="6943b-104">Уведомляет конвейер ICorDebug о том, что отладчик out-Process продолжает выполнение отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="6943b-104">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="6943b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6943b-105">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="6943b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6943b-106">Parameters</span></span>

 `eChange`\
<span data-ttu-id="6943b-107">окне Член [перечисления кордебугстатечанже](cordebugstatechange-enumeration.md) , описывающий изменение в состоянии выполнения процесса.</span><span class="sxs-lookup"><span data-stu-id="6943b-107">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="6943b-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="6943b-108">Remarks</span></span>

<span data-ttu-id="6943b-109">Предоставленный метод является частью `ICorDebugProcess4` интерфейса и соответствует четвертому слоту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="6943b-109">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="6943b-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6943b-110">Requirements</span></span>

 <span data-ttu-id="6943b-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6943b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="6943b-112">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="6943b-112">**Header:** None</span></span>

 <span data-ttu-id="6943b-113">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="6943b-113">**Library:** None</span></span>

 <span data-ttu-id="6943b-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6943b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6943b-115">См. также</span><span class="sxs-lookup"><span data-stu-id="6943b-115">See also</span></span>

- [<span data-ttu-id="6943b-116">Интерфейс ICorDebugProcess4</span><span class="sxs-lookup"><span data-stu-id="6943b-116">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="6943b-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6943b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6943b-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="6943b-118">Debugging</span></span>](index.md)
