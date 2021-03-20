---
description: 'Дополнительные сведения о методе: ICorProfilerCallback8::D Инамикмесоджиткомпилатионфинишед'
title: 'ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионфинишед'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d610024af9959790b37a724c2bdbf4dabc89dd20
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759824"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="9c403-103">ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионфинишед</span><span class="sxs-lookup"><span data-stu-id="9c403-103">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>

<span data-ttu-id="9c403-104">[Поддерживается в платформа .NET Framework 4,7 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="9c403-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="9c403-105">Уведомляет профилировщик о завершении JIT-компиляции динамического метода.</span><span class="sxs-lookup"><span data-stu-id="9c403-105">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c403-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9c403-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c403-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9c403-107">Parameters</span></span>  

`functionId`  
<span data-ttu-id="9c403-108">окне Идентификатор функции в памяти, для которой запускается JIT-компиляция.</span><span class="sxs-lookup"><span data-stu-id="9c403-108">[in] The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="9c403-109">`hrStatus` окне Значение, указывающее, была ли JIT-компиляция успешной.</span><span class="sxs-lookup"><span data-stu-id="9c403-109">`hrStatus` [in] A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="9c403-110">`fIsSafeToBlock` [входные] `true` чтобы указать, что блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова. `false` чтобы указать, что блокировка не повлияет на работу среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="9c403-110">`fIsSafeToBlock` [in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="9c403-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="9c403-111">Remarks</span></span>  

<span data-ttu-id="9c403-112">Этот обратный вызов активируется каждый раз, когда JIT-компиляция динамического метода завершается.</span><span class="sxs-lookup"><span data-stu-id="9c403-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="9c403-113">Сюда входят различные суррогаты IL и методы LCG.</span><span class="sxs-lookup"><span data-stu-id="9c403-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="9c403-114">Его цель — предоставить средствам записи профилировщика достаточно информации для распознавания скомпилированного метода для пользователей.</span><span class="sxs-lookup"><span data-stu-id="9c403-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="9c403-115">`functionId` нельзя использовать значения для разрешения их маркеров метаданных, так как динамические методы не имеют метаданных.</span><span class="sxs-lookup"><span data-stu-id="9c403-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="9c403-116">Требования</span><span class="sxs-lookup"><span data-stu-id="9c403-116">Requirements</span></span>  

 <span data-ttu-id="9c403-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c403-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c403-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c403-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c403-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c403-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c403-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9c403-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c403-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9c403-121">See also</span></span>

- [<span data-ttu-id="9c403-122">Метод DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="9c403-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="9c403-123">Интерфейс ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="9c403-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
