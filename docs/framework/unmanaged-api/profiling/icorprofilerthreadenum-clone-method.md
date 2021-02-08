---
description: 'Дополнительные сведения о методе: Икорпрофилерсреаденум:: Clone'
title: Метод ICorProfilerThreadEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: 00920484ed6f089f40281ea2590e6d9c27cd3268
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783798"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="0382f-103">Метод ICorProfilerThreadEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="0382f-103">ICorProfilerThreadEnum::Clone Method</span></span>

<span data-ttu-id="0382f-104">Получает указатель интерфейса на копию этого интерфейса [икорпрофилерсреаденум](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0382f-104">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0382f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0382f-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0382f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0382f-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="0382f-107">заполняет Указатель на указатель интерфейса, который, в свою очередь, указывает на копию этого интерфейса [икорпрофилерсреаденум](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0382f-107">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="0382f-108">Копия перечислителя поддерживает собственное состояние перечисления отдельно от этого перечислителя.</span><span class="sxs-lookup"><span data-stu-id="0382f-108">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="0382f-109">Однако начальная координата курсора копирования совпадает с текущей позицией курсора в перечислителе.</span><span class="sxs-lookup"><span data-stu-id="0382f-109">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0382f-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0382f-110">Requirements</span></span>  

 <span data-ttu-id="0382f-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0382f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0382f-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0382f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0382f-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0382f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0382f-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0382f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0382f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="0382f-115">See also</span></span>

- [<span data-ttu-id="0382f-116">икорпрофилерсреаденум</span><span class="sxs-lookup"><span data-stu-id="0382f-116">ICorProfilerThreadEnum</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="0382f-117">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="0382f-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
