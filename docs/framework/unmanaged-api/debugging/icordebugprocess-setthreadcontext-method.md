---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: SetThreadContext'
title: Метод ICorDebugProcess::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 3576c3bf3159e3960e7d2d4601ac2fb67d7218f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753982"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="1a052-103">Метод ICorDebugProcess::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="1a052-103">ICorDebugProcess::SetThreadContext Method</span></span>

<span data-ttu-id="1a052-104">Задает контекст для данного потока в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="1a052-104">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a052-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1a052-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a052-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1a052-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="1a052-107">окне Идентификатор потока, для которого задается контекст.</span><span class="sxs-lookup"><span data-stu-id="1a052-107">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="1a052-108">[in] Размер массива `context`.</span><span class="sxs-lookup"><span data-stu-id="1a052-108">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="1a052-109">окне Массив байтов, описывающих контекст потока.</span><span class="sxs-lookup"><span data-stu-id="1a052-109">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="1a052-110">Контекст указывает архитектуру процессора, на котором работает поток.</span><span class="sxs-lookup"><span data-stu-id="1a052-110">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a052-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="1a052-111">Remarks</span></span>  

 <span data-ttu-id="1a052-112">Отладчик должен вызывать этот метод, а не `SetThreadContext` функцию Win32, так как поток может находиться в состоянии "перехвачено", в котором его контекст был временно изменен.</span><span class="sxs-lookup"><span data-stu-id="1a052-112">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="1a052-113">Этот метод следует использовать только в том случае, если поток находится в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="1a052-113">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="1a052-114">Используйте [ICorDebugRegisterSet](icordebugregisterset-interface.md) для потоков в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="1a052-114">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="1a052-115">Никогда не нужно изменять контекст потока во время события нестандартного управления (OOB).</span><span class="sxs-lookup"><span data-stu-id="1a052-115">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="1a052-116">Передаваемые данные должны быть структурой контекста для текущей платформы.</span><span class="sxs-lookup"><span data-stu-id="1a052-116">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="1a052-117">Этот метод может повредить среду выполнения при неправильном использовании.</span><span class="sxs-lookup"><span data-stu-id="1a052-117">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a052-118">Требования</span><span class="sxs-lookup"><span data-stu-id="1a052-118">Requirements</span></span>  

 <span data-ttu-id="1a052-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a052-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a052-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a052-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a052-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a052-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a052-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a052-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
