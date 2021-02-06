---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: Жетаппдомаинсконтаинингмодуле'
title: Метод ICorProfilerInfo3::GetAppDomainsContainingModule
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
ms.openlocfilehash: 0f0fea5b01b80b110d7ab041574dc195162cb508
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646846"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="a9574-103">Метод ICorProfilerInfo3::GetAppDomainsContainingModule</span><span class="sxs-lookup"><span data-stu-id="a9574-103">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>

<span data-ttu-id="a9574-104">Возвращает идентификаторы доменов приложений, в которые был загружен указанный модуль.</span><span class="sxs-lookup"><span data-stu-id="a9574-104">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9574-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a9574-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9574-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a9574-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="a9574-107">[in] Идентификатор загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="a9574-107">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="a9574-108">[in] Размер массива `appDomainIds`.</span><span class="sxs-lookup"><span data-stu-id="a9574-108">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="a9574-109">[out] Указатель на общее число возвращенных элементов.</span><span class="sxs-lookup"><span data-stu-id="a9574-109">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="a9574-110">[out] Массив значений идентификаторов доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="a9574-110">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9574-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a9574-111">Remarks</span></span>  

 <span data-ttu-id="a9574-112">Этот метод использует буферы, выделенные вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="a9574-112">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9574-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a9574-113">Requirements</span></span>  

 <span data-ttu-id="a9574-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9574-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9574-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9574-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9574-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9574-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9574-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9574-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9574-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a9574-118">See also</span></span>

- [<span data-ttu-id="a9574-119">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="a9574-119">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="a9574-120">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="a9574-120">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a9574-121">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="a9574-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a9574-122">Профилирование</span><span class="sxs-lookup"><span data-stu-id="a9574-122">Profiling</span></span>](index.md)
