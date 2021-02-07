---
description: 'Дополнительные сведения о методе: ICorProfilerFunctionEnum:: Clone'
title: Метод ICorProfilerFunctionEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: 6cadadd98f64a27de0cd4e7d264fe797d22c33a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737679"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="11d70-103">Метод ICorProfilerFunctionEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="11d70-103">ICorProfilerFunctionEnum::Clone Method</span></span>

<span data-ttu-id="11d70-104">Получает указатель интерфейса на копию этого интерфейса [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="11d70-104">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d70-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="11d70-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11d70-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="11d70-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="11d70-107">заполняет Указатель на указатель интерфейса, который, в свою очередь, указывает на копию этого интерфейса [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="11d70-107">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="11d70-108">Копия перечислителя поддерживает собственное состояние перечисления отдельно от этого перечислителя.</span><span class="sxs-lookup"><span data-stu-id="11d70-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="11d70-109">Однако начальная позиции курсора копии совпадает с текущей позицией курсора этого перечислителя.</span><span class="sxs-lookup"><span data-stu-id="11d70-109">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d70-110">Требования</span><span class="sxs-lookup"><span data-stu-id="11d70-110">Requirements</span></span>  

 <span data-ttu-id="11d70-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11d70-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11d70-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11d70-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11d70-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11d70-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11d70-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11d70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d70-115">См. также</span><span class="sxs-lookup"><span data-stu-id="11d70-115">See also</span></span>

- [<span data-ttu-id="11d70-116">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="11d70-116">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="11d70-117">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="11d70-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
