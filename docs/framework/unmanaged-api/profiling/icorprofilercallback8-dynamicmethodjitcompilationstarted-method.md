---
description: 'Дополнительные сведения о методе: ICorProfilerCallback8::D Инамикмесоджиткомпилатионстартед'
title: 'ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионстартед'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 186b41564e0aabb069b06356b8eccbe90296ec4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781705"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="6c26f-103">ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионстартед</span><span class="sxs-lookup"><span data-stu-id="6c26f-103">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>

<span data-ttu-id="6c26f-104">[Поддерживается в платформа .NET Framework 4,7 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="6c26f-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="6c26f-105">Уведомляет профилировщик каждый раз, когда запускается JIT-компиляция динамического метода.</span><span class="sxs-lookup"><span data-stu-id="6c26f-105">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c26f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6c26f-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c26f-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="6c26f-107">Parameters</span></span>  

<span data-ttu-id="6c26f-108">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="6c26f-108">[in] `functionId`</span></span>  
<span data-ttu-id="6c26f-109">Идентификатор функции в памяти, для которой запускается JIT-компиляция.</span><span class="sxs-lookup"><span data-stu-id="6c26f-109">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="6c26f-110">[входные] `fIsSafeToBlock` 
 `true` чтобы указать, что блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова. `false`чтобы указать, что блокировка не повлияет на работу среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6c26f-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="6c26f-111">[входные] `pILHeader` Указатель на первый байт заголовка IL метода.</span><span class="sxs-lookup"><span data-stu-id="6c26f-111">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="6c26f-112">[входные] `cbILHeader` Число байтов в заголовке IL.</span><span class="sxs-lookup"><span data-stu-id="6c26f-112">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c26f-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="6c26f-113">Remarks</span></span>  

<span data-ttu-id="6c26f-114">Этот обратный вызов активируется всякий раз, когда динамический метод компилируется JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="6c26f-114">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="6c26f-115">Сюда входят различные суррогаты IL и методы LCG.</span><span class="sxs-lookup"><span data-stu-id="6c26f-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="6c26f-116">Его цель — предоставить средствам записи профилировщика достаточно информации для распознавания скомпилированного метода для пользователей.</span><span class="sxs-lookup"><span data-stu-id="6c26f-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="6c26f-117">`functionId` нельзя использовать значения для разрешения их маркеров метаданных, так как динамические методы не имеют метаданных.</span><span class="sxs-lookup"><span data-stu-id="6c26f-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="6c26f-118">`pILHeader`Указатель допустим только во время обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="6c26f-118">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="6c26f-119">Требования</span><span class="sxs-lookup"><span data-stu-id="6c26f-119">Requirements</span></span>  

 <span data-ttu-id="6c26f-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c26f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c26f-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c26f-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c26f-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c26f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c26f-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6c26f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c26f-124">См. также</span><span class="sxs-lookup"><span data-stu-id="6c26f-124">See also</span></span>

- [<span data-ttu-id="6c26f-125">Метод DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="6c26f-125">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="6c26f-126">Интерфейс ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="6c26f-126">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
