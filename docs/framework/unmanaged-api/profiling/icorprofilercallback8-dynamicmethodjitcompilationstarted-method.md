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
ms.openlocfilehash: c03251ab3120fd93cbb8e6c2f1bb62a4527a92bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759928"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="2053f-103">ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионстартед</span><span class="sxs-lookup"><span data-stu-id="2053f-103">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>

<span data-ttu-id="2053f-104">[Поддерживается в платформа .NET Framework 4,7 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="2053f-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="2053f-105">Уведомляет профилировщик каждый раз, когда запускается JIT-компиляция динамического метода.</span><span class="sxs-lookup"><span data-stu-id="2053f-105">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2053f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2053f-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2053f-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="2053f-107">Parameters</span></span>  

`functionId`  
<span data-ttu-id="2053f-108">окне Идентификатор функции в памяти, для которой запускается JIT-компиляция.</span><span class="sxs-lookup"><span data-stu-id="2053f-108">[in] The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="2053f-109">`fIsSafeToBlock` [входные] `true` чтобы указать, что блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова. `false` чтобы указать, что блокировка не повлияет на работу среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2053f-109">`fIsSafeToBlock` [in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="2053f-110">`pILHeader` окне Указатель на первый байт заголовка IL метода.</span><span class="sxs-lookup"><span data-stu-id="2053f-110">`pILHeader` [in] A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="2053f-111">`cbILHeader` окне Число байтов в заголовке IL.</span><span class="sxs-lookup"><span data-stu-id="2053f-111">`cbILHeader` [in] The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="2053f-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="2053f-112">Remarks</span></span>  

<span data-ttu-id="2053f-113">Этот обратный вызов активируется всякий раз, когда динамический метод компилируется JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="2053f-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="2053f-114">Сюда входят различные суррогаты IL и методы LCG.</span><span class="sxs-lookup"><span data-stu-id="2053f-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="2053f-115">Его цель — предоставить средствам записи профилировщика достаточно информации для распознавания скомпилированного метода для пользователей.</span><span class="sxs-lookup"><span data-stu-id="2053f-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="2053f-116">`functionId` нельзя использовать значения для разрешения их маркеров метаданных, так как динамические методы не имеют метаданных.</span><span class="sxs-lookup"><span data-stu-id="2053f-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="2053f-117">`pILHeader`Указатель допустим только во время обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="2053f-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="2053f-118">Требования</span><span class="sxs-lookup"><span data-stu-id="2053f-118">Requirements</span></span>  

 <span data-ttu-id="2053f-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2053f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2053f-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2053f-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2053f-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2053f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2053f-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2053f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2053f-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2053f-123">See also</span></span>

- [<span data-ttu-id="2053f-124">Метод DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="2053f-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="2053f-125">Интерфейс ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="2053f-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
