---
description: 'Дополнительные сведения о методе: ICorProfilerCallback3:: InitializeForAttach'
title: Метод ICorProfilerCallback3::InitializeForAttach
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: b3c5b8701df9e680e4fcbd57f4e08395dfe0b8da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788817"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="e918f-103">Метод ICorProfilerCallback3::InitializeForAttach</span><span class="sxs-lookup"><span data-stu-id="e918f-103">ICorProfilerCallback3::InitializeForAttach Method</span></span>

<span data-ttu-id="e918f-104">Вызывается средой CLR, чтобы предоставить профилировщику возможность инициализировать свое состояние после операции присоединения.</span><span class="sxs-lookup"><span data-stu-id="e918f-104">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e918f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e918f-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e918f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e918f-106">Parameters</span></span>  

 `pCorProfilerInfoUnk`  
 <span data-ttu-id="e918f-107">[in] Указатель интерфейса для интерфейса `ICorProfilerInfo*`.</span><span class="sxs-lookup"><span data-stu-id="e918f-107">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="e918f-108">окне Указатель на данные, передаваемые в метод [иклрпрофилинг:: AttachProfiler](iclrprofiling-attachprofiler-method.md) в своем `pvClientData` параметре.</span><span class="sxs-lookup"><span data-stu-id="e918f-108">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="e918f-109">Если этот параметр имеет значение null, `cbClientData` будет иметь значение 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="e918f-109">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="e918f-110">Среда CLR освобождает эту память при возврате из `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="e918f-110">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="e918f-111">[in] Размер в байтах данных, на которые указывает `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="e918f-111">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e918f-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e918f-112">Remarks</span></span>  

 <span data-ttu-id="e918f-113">Среда CLR вызывает `InitializeForAttach`, чтобы предоставить профилировщику возможность запрашивать обратные вызовы.</span><span class="sxs-lookup"><span data-stu-id="e918f-113">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e918f-114">Требования</span><span class="sxs-lookup"><span data-stu-id="e918f-114">Requirements</span></span>  

 <span data-ttu-id="e918f-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e918f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e918f-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e918f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e918f-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e918f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e918f-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e918f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e918f-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e918f-119">See also</span></span>

- [<span data-ttu-id="e918f-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e918f-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e918f-121">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="e918f-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e918f-122">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e918f-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e918f-123">Профилирование</span><span class="sxs-lookup"><span data-stu-id="e918f-123">Profiling</span></span>](index.md)
