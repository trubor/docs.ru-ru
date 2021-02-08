---
description: 'Дополнительные сведения о методе: ICorDebugILFrame2:: RemapFunction'
title: Метод ICorDebugILFrame2::RemapFunction
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
ms.openlocfilehash: d8a6c7f966488e7b74a9661e3a18b5248df7400b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791298"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="7df48-103">Метод ICorDebugILFrame2::RemapFunction</span><span class="sxs-lookup"><span data-stu-id="7df48-103">ICorDebugILFrame2::RemapFunction Method</span></span>

<span data-ttu-id="7df48-104">Повторно сопоставляет отредактированную функцию, указывая новое смещение MSIL</span><span class="sxs-lookup"><span data-stu-id="7df48-104">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df48-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7df48-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7df48-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7df48-106">Parameters</span></span>  

 `newILOffset`  
 <span data-ttu-id="7df48-107">окне Новое смещение MSIL кадра стека, в которое следует поместить указатель инструкции.</span><span class="sxs-lookup"><span data-stu-id="7df48-107">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="7df48-108">Это значение должно быть точкой последовательности.</span><span class="sxs-lookup"><span data-stu-id="7df48-108">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="7df48-109">Для обеспечения допустимости этого значения отвечает вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="7df48-109">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="7df48-110">Например, смещение MSIL недопустимо, если оно находится вне границ функции.</span><span class="sxs-lookup"><span data-stu-id="7df48-110">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7df48-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="7df48-111">Remarks</span></span>  

 <span data-ttu-id="7df48-112">Когда функция фрейма была изменена, отладчик может вызвать `RemapFunction` метод для замены последней версии функции кадра, чтобы ее можно было выполнить.</span><span class="sxs-lookup"><span data-stu-id="7df48-112">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="7df48-113">Выполнение кода начнется с заданного смещения MSIL.</span><span class="sxs-lookup"><span data-stu-id="7df48-113">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7df48-114">Вызов метода `RemapFunction` , как и вызов [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md), немедленно сделает недействительными все интерфейсы отладки, связанные с формированием трассировки стека для потока.</span><span class="sxs-lookup"><span data-stu-id="7df48-114">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="7df48-115">К этим интерфейсам относятся [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame и ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="7df48-115">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="7df48-116">`RemapFunction`Метод может быть вызван только в контексте текущего кадра и только в одном из следующих случаев:</span><span class="sxs-lookup"><span data-stu-id="7df48-116">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="7df48-117">После получения обратного вызова [ICorDebugManagedCallback2:: FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) , который еще не был продолжен.</span><span class="sxs-lookup"><span data-stu-id="7df48-117">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="7df48-118">Пока выполнение кода остановлено из-за события [ICorDebugManagedCallback:: EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) для этого кадра.</span><span class="sxs-lookup"><span data-stu-id="7df48-118">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7df48-119">Требования</span><span class="sxs-lookup"><span data-stu-id="7df48-119">Requirements</span></span>  

 <span data-ttu-id="7df48-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7df48-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7df48-121">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7df48-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7df48-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7df48-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7df48-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7df48-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
