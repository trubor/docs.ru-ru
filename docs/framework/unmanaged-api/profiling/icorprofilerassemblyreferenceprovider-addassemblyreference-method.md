---
description: 'Дополнительные сведения о методе: ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference'
title: Метод ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 343e76dd64329c88bf4b52e24d45a1e7c8b639bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648380"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="eb065-103">Метод ICorProfilerAssemblyReferenceProvider::AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="eb065-103">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>

<span data-ttu-id="eb065-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="eb065-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="eb065-105">Информирует среду CLR о ссылке сборки, которую профилировщик планирует добавить в обратный вызов [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eb065-105">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb065-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eb065-106">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb065-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb065-107">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="eb065-108">Указатель на структуру [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) , которая предоставляет среде CLR сведения о ссылке на сборку, которую следует учитывать при выполнении анализа закрытия ссылок на сборки.</span><span class="sxs-lookup"><span data-stu-id="eb065-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="eb065-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="eb065-109">Remarks</span></span>  

 <span data-ttu-id="eb065-110">Профилировщик вызывает этот метод для каждой целевой сборки, на которую планируется ссылаться из сборки, указанной в `wszAssemblyPath` аргументе обратного вызова [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eb065-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="eb065-111">Объект интерфейса [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) передается обратному вызову [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) профилировщика вместе с путем к сборке и именем в `wszAssemblyPath` аргументе.</span><span class="sxs-lookup"><span data-stu-id="eb065-111">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb065-112">Требования</span><span class="sxs-lookup"><span data-stu-id="eb065-112">Requirements</span></span>  

 <span data-ttu-id="eb065-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb065-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb065-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb065-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb065-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb065-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb065-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb065-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb065-117">См. также</span><span class="sxs-lookup"><span data-stu-id="eb065-117">See also</span></span>

- [<span data-ttu-id="eb065-118">Интерфейс ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="eb065-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="eb065-119">Метод GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="eb065-119">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="eb065-120">Метод ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="eb065-120">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
