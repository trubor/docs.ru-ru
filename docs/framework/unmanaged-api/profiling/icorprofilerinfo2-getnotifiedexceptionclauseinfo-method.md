---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo'
title: Метод ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
ms.openlocfilehash: f297689ccdd1b600fe86db16940434c990e4b084
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716488"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="aa001-103">Метод ICorProfilerInfo2::GetNotifiedExceptionClauseInfo</span><span class="sxs-lookup"><span data-stu-id="aa001-103">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>

<span data-ttu-id="aa001-104">Получает собственный адрес и сведения о кадре для предложения исключения ( `catch` / `finally` / `filter` ), которое будет запущено или только что было запущено.</span><span class="sxs-lookup"><span data-stu-id="aa001-104">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa001-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aa001-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa001-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="aa001-106">Parameters</span></span>  

 `pinfo`  
 <span data-ttu-id="aa001-107">заполняет Указатель на структуру [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) , описывающую экземпляр предложения текущего исключения и связанный с ним кадр.</span><span class="sxs-lookup"><span data-stu-id="aa001-107">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa001-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="aa001-108">Remarks</span></span>  

 <span data-ttu-id="aa001-109">При получении уведомления об исключении `GetNotifiedExceptionClauseInfo` можно использовать для получения собственного адреса и сведений о кадре для предложения исключения ( `catch` / `finally` / `filter` ), которое будет выполнено (в результате выполнения выражения[ICorProfilerCallback:: ексцептионкатчерентер](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: ексцептионунвиндфиналлентер](icorprofilercallback-exceptionunwindfinallyenter-method.md)или [ICorProfilerCallback:: ексцептионсеарчфилтерентер](icorprofilercallback-exceptionsearchfilterenter-method.md) получено профилировщиком) или только что выполнялся (в профилировщике получен обратный вызов ICorProfilerCallback:[: ексцептионкатчерлеаве](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: exceptionunwindfinallyleave-](icorprofilercallback-exceptionunwindfinallyleave-method.md)или [ICorProfilerCallback:: ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="aa001-109">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="aa001-110">Этот вызов можно выполнить в любое время после одного из обратных вызовов при вводе выше, пока не будет получен соответствующий обратный вызов метода Leave или не будет создано вложенное исключение в текущем предложении, в этом случае для этого предложения нет уведомления о выходе.</span><span class="sxs-lookup"><span data-stu-id="aa001-110">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="aa001-111">Обратите внимание, что выдаваемое исключение не может быть экранировано `filter` предложением исключения, поэтому в этом случае всегда отображается уведомление о выходе.</span><span class="sxs-lookup"><span data-stu-id="aa001-111">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa001-112">Требования</span><span class="sxs-lookup"><span data-stu-id="aa001-112">Requirements</span></span>  

 <span data-ttu-id="aa001-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa001-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa001-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aa001-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aa001-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa001-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa001-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa001-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa001-117">См. также</span><span class="sxs-lookup"><span data-stu-id="aa001-117">See also</span></span>

- [<span data-ttu-id="aa001-118">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="aa001-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="aa001-119">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="aa001-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
