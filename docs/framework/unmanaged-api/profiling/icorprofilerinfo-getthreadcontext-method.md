---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetThreadContext'
title: Метод ICorProfilerInfo::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: b2970da90250819cc68eee55b70188d4830113a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687277"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="d720b-103">Метод ICorProfilerInfo::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="d720b-103">ICorProfilerInfo::GetThreadContext Method</span></span>

<span data-ttu-id="d720b-104">Возвращает удостоверение контекста, которое в настоящее время связано с указанным потоком.</span><span class="sxs-lookup"><span data-stu-id="d720b-104">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d720b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d720b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d720b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d720b-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="d720b-107">окне Идентификатор потока.</span><span class="sxs-lookup"><span data-stu-id="d720b-107">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="d720b-108">заполняет Указатель на идентификатор контекста, который в настоящее время связан с указанным потоком.</span><span class="sxs-lookup"><span data-stu-id="d720b-108">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="d720b-109">Если с потоком не связан ни один контекст, эта функция возвратит CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="d720b-109">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d720b-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d720b-110">Requirements</span></span>  

 <span data-ttu-id="d720b-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d720b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d720b-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d720b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d720b-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d720b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d720b-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d720b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d720b-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d720b-115">See also</span></span>

- [<span data-ttu-id="d720b-116">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d720b-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
