---
description: Дополнительные сведения о функции Стаккснапшоткаллбакк
title: Функция StackSnapshotCallback
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: a49588bc3277956acad612afd0fcab3fa7edffbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736860"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="39ddd-103">Функция StackSnapshotCallback</span><span class="sxs-lookup"><span data-stu-id="39ddd-103">StackSnapshotCallback Function</span></span>

<span data-ttu-id="39ddd-104">Предоставляет профилировщику сведения о каждом управляемом кадре и каждом запуске неуправляемых кадров в стеке во время прохода стека, который инициируется методом [ICorProfilerInfo2::D остаккснапшот](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="39ddd-104">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39ddd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39ddd-105">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39ddd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="39ddd-106">Parameters</span></span>  

 `funcId`  
 <span data-ttu-id="39ddd-107">окне Если это значение равно нулю, этот обратный вызов предназначен для запуска неуправляемых кадров; в противном случае это идентификатор управляемой функции, и этот обратный вызов предназначен для управляемого фрейма.</span><span class="sxs-lookup"><span data-stu-id="39ddd-107">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="39ddd-108">окне Значение указателя инструкций машинного кода в кадре.</span><span class="sxs-lookup"><span data-stu-id="39ddd-108">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="39ddd-109">окне `COR_PRF_FRAME_INFO` Значение, которое ссылается на сведения о кадре стека.</span><span class="sxs-lookup"><span data-stu-id="39ddd-109">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="39ddd-110">Это значение допустимо для использования только во время этого обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="39ddd-110">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="39ddd-111">окне Размер `CONTEXT` структуры, на которую ссылается `context` параметр.</span><span class="sxs-lookup"><span data-stu-id="39ddd-111">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="39ddd-112">окне Указатель на `CONTEXT` структуру Win32, которая представляет состояние ЦП для данного кадра.</span><span class="sxs-lookup"><span data-stu-id="39ddd-112">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="39ddd-113">`context`Параметр допустим только в том случае, если был передан флаг COR_PRF_SNAPSHOT_CONTEXT `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="39ddd-113">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="39ddd-114">окне Указатель на данные клиента, которые передаются непосредственно через `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="39ddd-114">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39ddd-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="39ddd-115">Remarks</span></span>  

 <span data-ttu-id="39ddd-116">`StackSnapshotCallback`Функция реализуется модулем записи профилировщика.</span><span class="sxs-lookup"><span data-stu-id="39ddd-116">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="39ddd-117">Необходимо ограничить сложность работы, выполненной в `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="39ddd-117">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="39ddd-118">Например, при использовании `ICorProfilerInfo2::DoStackSnapshot` в асинхронном режиме целевой поток может удерживать блокировки.</span><span class="sxs-lookup"><span data-stu-id="39ddd-118">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="39ddd-119">Если код внутри `StackSnapshotCallback` требует одних и тех же блокировок, может возникнуть взаимоблокировка.</span><span class="sxs-lookup"><span data-stu-id="39ddd-119">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="39ddd-120">`ICorProfilerInfo2::DoStackSnapshot`Метод вызывает `StackSnapshotCallback` функцию один раз для каждого управляемого кадра или один раз для каждого запуска неуправляемых кадров.</span><span class="sxs-lookup"><span data-stu-id="39ddd-120">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="39ddd-121">Если `StackSnapshotCallback` вызывается для запуска неуправляемых кадров, профилировщик может использовать контекст Register (на который ссылается `context` параметр) для выполнения собственного анализа неуправляемого стека.</span><span class="sxs-lookup"><span data-stu-id="39ddd-121">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="39ddd-122">В этом случае `CONTEXT` Структура Win32 представляет состояние ЦП для последнего отправленного кадра в рамках выполнения неуправляемых кадров.</span><span class="sxs-lookup"><span data-stu-id="39ddd-122">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="39ddd-123">Несмотря на то `CONTEXT` , что структура Win32 включает значения для всех регистров, следует полагаться только на значения регистра указателя стека, регистра указателя кадра, регистра указателя инструкций и неизменяемых (то есть сохраненных) целочисленных регистров.</span><span class="sxs-lookup"><span data-stu-id="39ddd-123">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39ddd-124">Требования</span><span class="sxs-lookup"><span data-stu-id="39ddd-124">Requirements</span></span>  

 <span data-ttu-id="39ddd-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39ddd-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39ddd-126">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="39ddd-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="39ddd-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39ddd-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39ddd-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39ddd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39ddd-129">См. также</span><span class="sxs-lookup"><span data-stu-id="39ddd-129">See also</span></span>

- [<span data-ttu-id="39ddd-130">Метод DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="39ddd-130">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="39ddd-131">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="39ddd-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
