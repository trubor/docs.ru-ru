---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: GetThreadContext'
title: Метод ICorDebugProcess::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 4cb926183522548e924013580f207d1d0677a0d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746871"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="a35ab-103">Метод ICorDebugProcess::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="a35ab-103">ICorDebugProcess::GetThreadContext Method</span></span>

<span data-ttu-id="a35ab-104">Возвращает контекст для данного потока в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="a35ab-104">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35ab-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a35ab-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a35ab-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a35ab-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="a35ab-107">окне Идентификатор потока, для которого извлекается контекст.</span><span class="sxs-lookup"><span data-stu-id="a35ab-107">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a35ab-108">[in] Размер массива `context`.</span><span class="sxs-lookup"><span data-stu-id="a35ab-108">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="a35ab-109">[вход, выход] Массив байтов, описывающих контекст потока.</span><span class="sxs-lookup"><span data-stu-id="a35ab-109">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="a35ab-110">Контекст указывает архитектуру процессора, на котором работает поток.</span><span class="sxs-lookup"><span data-stu-id="a35ab-110">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a35ab-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a35ab-111">Remarks</span></span>  

 <span data-ttu-id="a35ab-112">Отладчик должен вызывать этот метод вместо `GetThreadContext` метода Win32, так как поток может находиться в состоянии "перехвачено", в котором его контекст временно изменен.</span><span class="sxs-lookup"><span data-stu-id="a35ab-112">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="a35ab-113">Этот метод следует использовать только в том случае, если поток находится в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="a35ab-113">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="a35ab-114">Используйте [ICorDebugRegisterSet](icordebugregisterset-interface.md) для потоков в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="a35ab-114">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="a35ab-115">Возвращаемые данные — это структура контекста для текущей платформы.</span><span class="sxs-lookup"><span data-stu-id="a35ab-115">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="a35ab-116">Как и в случае с `GetThreadContext` методом Win32, вызывающий объект должен инициализировать `context` параметр перед вызовом этого метода.</span><span class="sxs-lookup"><span data-stu-id="a35ab-116">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35ab-117">Требования</span><span class="sxs-lookup"><span data-stu-id="a35ab-117">Requirements</span></span>  

 <span data-ttu-id="a35ab-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a35ab-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a35ab-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a35ab-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a35ab-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a35ab-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a35ab-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a35ab-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
