---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: EnumModules'
title: Метод ICorProfilerInfo3::EnumModules
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 9cdb76b77f78fa68eafa111e60b31b738173d658
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646859"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="85aa3-103">Метод ICorProfilerInfo3::EnumModules</span><span class="sxs-lookup"><span data-stu-id="85aa3-103">ICorProfilerInfo3::EnumModules Method</span></span>

<span data-ttu-id="85aa3-104">Возвращает перечислитель, предоставляющий методы для последовательного перебора коллекции управляемых модулей, загруженных в приложение.</span><span class="sxs-lookup"><span data-stu-id="85aa3-104">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85aa3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85aa3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85aa3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="85aa3-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="85aa3-107">заполняет Указатель на интерфейс [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="85aa3-107">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85aa3-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="85aa3-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85aa3-109">Требования</span><span class="sxs-lookup"><span data-stu-id="85aa3-109">Requirements</span></span>  

 <span data-ttu-id="85aa3-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85aa3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85aa3-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85aa3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85aa3-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85aa3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85aa3-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85aa3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85aa3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="85aa3-114">See also</span></span>

- [<span data-ttu-id="85aa3-115">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="85aa3-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="85aa3-116">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="85aa3-116">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="85aa3-117">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="85aa3-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="85aa3-118">Профилирование</span><span class="sxs-lookup"><span data-stu-id="85aa3-118">Profiling</span></span>](index.md)
