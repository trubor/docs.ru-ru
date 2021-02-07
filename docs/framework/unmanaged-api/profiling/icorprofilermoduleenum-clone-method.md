---
description: 'Дополнительные сведения о методе: ICorProfilerModuleEnum:: Clone'
title: Метод ICorProfilerModuleEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: 0d2a235def6d3b16d661e51979742426ebe1942f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736943"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="4081e-103">Метод ICorProfilerModuleEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="4081e-103">ICorProfilerModuleEnum::Clone Method</span></span>

<span data-ttu-id="4081e-104">Получает указатель интерфейса на копию этого интерфейса [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4081e-104">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4081e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4081e-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4081e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4081e-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="4081e-107">заполняет Указатель на указатель интерфейса, который, в свою очередь, указывает на копию этого интерфейса [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4081e-107">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="4081e-108">Копия перечислителя поддерживает собственное состояние перечисления отдельно от этого перечислителя.</span><span class="sxs-lookup"><span data-stu-id="4081e-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="4081e-109">Однако начальная позиции курсора копии совпадает с текущей позицией курсора этого перечислителя.</span><span class="sxs-lookup"><span data-stu-id="4081e-109">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4081e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="4081e-110">Requirements</span></span>  

 <span data-ttu-id="4081e-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4081e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4081e-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4081e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4081e-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4081e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4081e-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4081e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4081e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="4081e-115">See also</span></span>

- [<span data-ttu-id="4081e-116">Интерфейс ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="4081e-116">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="4081e-117">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="4081e-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
