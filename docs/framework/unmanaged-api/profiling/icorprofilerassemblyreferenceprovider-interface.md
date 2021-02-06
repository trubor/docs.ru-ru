---
description: 'Дополнительные сведения о: интерфейс ICorProfilerAssemblyReferenceProvider'
title: Интерфейс ICorProfilerAssemblyReferenceProvider
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: 0f16bad95dba46452ce5cc8ad1bbe6ca1bfeb7c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648354"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="fa4b7-103">Интерфейс ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="fa4b7-103">ICorProfilerAssemblyReferenceProvider Interface</span></span>

<span data-ttu-id="fa4b7-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="fa4b7-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fa4b7-105">Позволяет профилировщику информировать среду CLR о ссылках на сборки, которые профилировщик добавит в обратный вызов [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fa4b7-105">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa4b7-106">Методы</span><span class="sxs-lookup"><span data-stu-id="fa4b7-106">Methods</span></span>  
  
|<span data-ttu-id="fa4b7-107">Метод</span><span class="sxs-lookup"><span data-stu-id="fa4b7-107">Method</span></span>|<span data-ttu-id="fa4b7-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fa4b7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa4b7-109">Метод AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="fa4b7-109">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="fa4b7-110">Сообщает CLR о сборке, которую профилировщик планирует добавить в обратный вызов [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fa4b7-110">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa4b7-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="fa4b7-111">Remarks</span></span>  

 <span data-ttu-id="fa4b7-112">Среда CLR передает профилировщику `ICorProfilerAssemblyReferenceProvider` объект интерфейса в обратном вызове [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fa4b7-112">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="fa4b7-113">Это позволяет профилировщику информировать среду CLR о ссылках на сборки, которые профилировщик планирует добавить позднее в параметре [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="fa4b7-113">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="fa4b7-114">callback.</span><span class="sxs-lookup"><span data-stu-id="fa4b7-114">callback.</span></span> <span data-ttu-id="fa4b7-115">В результате повышается точность обхода замыкания ссылки на сборку среды CLR и его алгоритмов, определяющих возможность совместного доступа к сборкам.</span><span class="sxs-lookup"><span data-stu-id="fa4b7-115">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="fa4b7-116">Этот интерфейс можно использовать только в обратном вызове [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , который передает этот объект интерфейса профилировщику.</span><span class="sxs-lookup"><span data-stu-id="fa4b7-116">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa4b7-117">Требования</span><span class="sxs-lookup"><span data-stu-id="fa4b7-117">Requirements</span></span>  

 <span data-ttu-id="fa4b7-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa4b7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa4b7-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa4b7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa4b7-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa4b7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4b7-121">См. также</span><span class="sxs-lookup"><span data-stu-id="fa4b7-121">See also</span></span>

- [<span data-ttu-id="fa4b7-122">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="fa4b7-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
