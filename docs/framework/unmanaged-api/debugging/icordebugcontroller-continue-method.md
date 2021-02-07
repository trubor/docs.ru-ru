---
description: 'Дополнительные сведения о методе: ICorDebugController:: Continue'
title: Метод ICorDebugController::Continue
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: e5858a8c287e8dd5a493a85c9f427ad8acd9ecc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710807"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="1a7d1-103">Метод ICorDebugController::Continue</span><span class="sxs-lookup"><span data-stu-id="1a7d1-103">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="1a7d1-104">Возобновляет выполнение управляемых потоков после вызова [метода остановкой](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="1a7d1-104">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="1a7d1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1a7d1-105">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="1a7d1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1a7d1-106">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="1a7d1-107">окне Задайте значение `true` , если продолжение события вне диапазона. в противном случае задайте для значение `false` .</span><span class="sxs-lookup"><span data-stu-id="1a7d1-107">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a7d1-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="1a7d1-108">Remarks</span></span>

<span data-ttu-id="1a7d1-109">`Continue` продолжит процесс после вызова `ICorDebugController::Stop` метода.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-109">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="1a7d1-110">При отладке в смешанном режиме не вызывайте метод `Continue` в потоке событий Win32, если вы не продолжите работу по внешнему событию.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-110">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="1a7d1-111">*Событие с чередованием* — это управляемое событие или нормальное неуправляемое событие, в течение которого отладчик поддерживает взаимодействие с управляемым состоянием процесса.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-111">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="1a7d1-112">В этом случае отладчик получает обратный вызов [икордебугунманажедкаллбакк::D ебужевент](icordebugunmanagedcallback-debugevent-method.md) с `fOutOfBand` параметром, имеющим значение `false` .</span><span class="sxs-lookup"><span data-stu-id="1a7d1-112">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="1a7d1-113">*Событие внешнего вида* — это неуправляемое событие, в течение которого взаимодействие с управляемым состоянием процесса невозможно, пока процесс остановлен из-за события.</span><span class="sxs-lookup"><span data-stu-id="1a7d1-113">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="1a7d1-114">В этом случае отладчик получает `ICorDebugUnmanagedCallback::DebugEvent` обратный вызов с `fOutOfBand` параметром, для которого задано значение `true` .</span><span class="sxs-lookup"><span data-stu-id="1a7d1-114">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="1a7d1-115">Требования</span><span class="sxs-lookup"><span data-stu-id="1a7d1-115">Requirements</span></span>

<span data-ttu-id="1a7d1-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a7d1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1a7d1-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a7d1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="1a7d1-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a7d1-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1a7d1-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a7d1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
