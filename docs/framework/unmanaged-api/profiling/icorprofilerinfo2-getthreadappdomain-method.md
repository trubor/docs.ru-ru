---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: Жетсреадаппдомаин'
title: Метод ICorProfilerInfo2::GetThreadAppDomain
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: b480388254a6ee84db9f6c3e8d44b7358246502a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647067"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="3b48f-103">Метод ICorProfilerInfo2::GetThreadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3b48f-103">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>

<span data-ttu-id="3b48f-104">Возвращает идентификатор домена приложения, в котором указанный поток в настоящий момент исполняет код.</span><span class="sxs-lookup"><span data-stu-id="3b48f-104">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b48f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3b48f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b48f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3b48f-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="3b48f-107">окне Идентификатор, указывающий поток.</span><span class="sxs-lookup"><span data-stu-id="3b48f-107">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="3b48f-108">заполняет Указатель на идентификатор домена приложения.</span><span class="sxs-lookup"><span data-stu-id="3b48f-108">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b48f-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3b48f-109">Requirements</span></span>  

 <span data-ttu-id="3b48f-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b48f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b48f-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b48f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b48f-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b48f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b48f-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b48f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b48f-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3b48f-114">See also</span></span>

- [<span data-ttu-id="3b48f-115">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="3b48f-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="3b48f-116">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="3b48f-116">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
