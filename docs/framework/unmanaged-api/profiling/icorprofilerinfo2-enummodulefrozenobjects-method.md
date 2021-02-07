---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: EnumModuleFrozenObjects'
title: Метод ICorProfilerInfo2::EnumModuleFrozenObjects
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: b68571544c00c8c234a73404a95433e91f0cfdcf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753215"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="71837-103">Метод ICorProfilerInfo2::EnumModuleFrozenObjects</span><span class="sxs-lookup"><span data-stu-id="71837-103">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>

<span data-ttu-id="71837-104">Возвращает перечислитель, позволяющий выполнять итерацию зафиксированных объектов в указанном модуле. Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="71837-104">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71837-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="71837-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71837-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="71837-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="71837-107">окне Идентификатор модуля, содержащего зафиксированные объекты для перечисления.</span><span class="sxs-lookup"><span data-stu-id="71837-107">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="71837-108">заполняет Указатель на адрес интерфейса [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) , который перечисляет зафиксированные объекты.</span><span class="sxs-lookup"><span data-stu-id="71837-108">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71837-109">Требования</span><span class="sxs-lookup"><span data-stu-id="71837-109">Requirements</span></span>  

 <span data-ttu-id="71837-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71837-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71837-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71837-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71837-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71837-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71837-113">**Платформа .NET Framework версии:** 3,5, 3,0 sp1, 3,0, 2,0 SP1, 2,0</span><span class="sxs-lookup"><span data-stu-id="71837-113">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71837-114">См. также</span><span class="sxs-lookup"><span data-stu-id="71837-114">See also</span></span>

- [<span data-ttu-id="71837-115">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="71837-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="71837-116">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="71837-116">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
