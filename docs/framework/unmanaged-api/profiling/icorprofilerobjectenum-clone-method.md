---
description: 'Дополнительные сведения о методе: ICorProfilerObjectEnum:: Clone'
title: Метод ICorProfilerObjectEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: 59971f6f6e7edab4b4c4f796ee7bea3c4d8b4e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798957"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="c2e56-103">Метод ICorProfilerObjectEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="c2e56-103">ICorProfilerObjectEnum::Clone Method</span></span>

<span data-ttu-id="c2e56-104">Получает указатель интерфейса на копию этого интерфейса [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c2e56-104">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2e56-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2e56-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2e56-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c2e56-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="c2e56-107">заполняет Указатель на указатель интерфейса, который, в свою очередь, указывает на копию этого `ICorProfilerObjectEnum` интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c2e56-107">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="c2e56-108">Копия хранит собственное состояние перечисления отдельно от этого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c2e56-108">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="c2e56-109">Однако начальная позиции курсора копии будет совпадать с текущей позицией курсора этого перечислителя.</span><span class="sxs-lookup"><span data-stu-id="c2e56-109">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2e56-110">Требования</span><span class="sxs-lookup"><span data-stu-id="c2e56-110">Requirements</span></span>  

 <span data-ttu-id="c2e56-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2e56-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2e56-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2e56-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2e56-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2e56-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2e56-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2e56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e56-115">См. также</span><span class="sxs-lookup"><span data-stu-id="c2e56-115">See also</span></span>

- [<span data-ttu-id="c2e56-116">Интерфейс ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="c2e56-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
