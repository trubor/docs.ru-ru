---
description: 'Дополнительные сведения о методе: ICorDebugILFrame:: SetIP'
title: Метод ICorDebugILFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 75d2530a3d9151c64980316757074141776a78d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791326"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="9a70a-103">Метод ICorDebugILFrame::SetIP</span><span class="sxs-lookup"><span data-stu-id="9a70a-103">ICorDebugILFrame::SetIP Method</span></span>

<span data-ttu-id="9a70a-104">Задает указатель инструкции в указанном расположении смещения в коде промежуточного языка Майкрософт (MSIL).</span><span class="sxs-lookup"><span data-stu-id="9a70a-104">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a70a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a70a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a70a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9a70a-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="9a70a-107">Положение смещения в коде MSIL.</span><span class="sxs-lookup"><span data-stu-id="9a70a-107">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a70a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="9a70a-108">Remarks</span></span>  

 <span data-ttu-id="9a70a-109">Вызывает метод, чтобы `SetIP` немедленно сделать недействительными все кадры и цепочки для текущего потока.</span><span class="sxs-lookup"><span data-stu-id="9a70a-109">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="9a70a-110">Если отладчику требуются сведения о кадре после вызова `SetIP` , он должен выполнить новую трассировку стека.</span><span class="sxs-lookup"><span data-stu-id="9a70a-110">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="9a70a-111">[ICorDebug](icordebug-interface.md) попытается удержать кадр стека в допустимом состоянии.</span><span class="sxs-lookup"><span data-stu-id="9a70a-111">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="9a70a-112">Тем не менее, даже если кадр находится в допустимом состоянии, могут возникнуть проблемы, например неинициализированные локальные переменные.</span><span class="sxs-lookup"><span data-stu-id="9a70a-112">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="9a70a-113">Вызывающий объект отвечает за обеспечение согласованности выполняющейся программы.</span><span class="sxs-lookup"><span data-stu-id="9a70a-113">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="9a70a-114">На 64-разрядных платформах указатель инструкции не может быть перемещен из `catch` блока или `finally` .</span><span class="sxs-lookup"><span data-stu-id="9a70a-114">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="9a70a-115">Если `SetIP` вызывается метод для перемещения на 64-разрядной платформе, он возвращает значение HRESULT, указывающее на сбой.</span><span class="sxs-lookup"><span data-stu-id="9a70a-115">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a70a-116">Требования</span><span class="sxs-lookup"><span data-stu-id="9a70a-116">Requirements</span></span>  

 <span data-ttu-id="9a70a-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a70a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a70a-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a70a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a70a-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a70a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a70a-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a70a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
