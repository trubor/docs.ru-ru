---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetCurrentThreadID'
title: Метод ICorProfilerInfo::GetCurrentThreadID
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: 562c6cb61f13e9ab568d18c7d179872cbc7cdb06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647647"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="d7ea3-103">Метод ICorProfilerInfo::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="d7ea3-103">ICorProfilerInfo::GetCurrentThreadID Method</span></span>

<span data-ttu-id="d7ea3-104">Возвращает идентификатор текущего потока, если он является управляемым потоком.</span><span class="sxs-lookup"><span data-stu-id="d7ea3-104">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ea3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d7ea3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7ea3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7ea3-106">Parameters</span></span>  

 `pThreadId`  
 <span data-ttu-id="d7ea3-107">заполняет Указатель на возвращенный идентификатор управляемого потока.</span><span class="sxs-lookup"><span data-stu-id="d7ea3-107">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7ea3-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d7ea3-108">Remarks</span></span>  

 <span data-ttu-id="d7ea3-109">Если текущий поток является внутренним потоком среды выполнения или другим неуправляемым потоком, `GetCurrentThreadID` возвращает CORPROF_E_NOT_MANAGED_THREAD как HRESULT, а возвращаемое значение `pThreadId` параметра будет равно null.</span><span class="sxs-lookup"><span data-stu-id="d7ea3-109">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7ea3-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d7ea3-110">Requirements</span></span>  

 <span data-ttu-id="d7ea3-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7ea3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7ea3-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7ea3-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7ea3-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7ea3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7ea3-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7ea3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ea3-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d7ea3-115">See also</span></span>

- [<span data-ttu-id="d7ea3-116">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d7ea3-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
