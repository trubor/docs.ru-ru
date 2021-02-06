---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetILFunctionBodyAllocator'
title: Метод ICorProfilerInfo::GetILFunctionBodyAllocator
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 25d059d784fe64231d4d2ff3d23b4820443873cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647431"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="2c482-103">Метод ICorProfilerInfo::GetILFunctionBodyAllocator</span><span class="sxs-lookup"><span data-stu-id="2c482-103">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>

<span data-ttu-id="2c482-104">Возвращает интерфейс, предоставляющий метод для выделения памяти, используемой для перекачки тела метода в коде на языке MSIL.</span><span class="sxs-lookup"><span data-stu-id="2c482-104">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c482-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2c482-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c482-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2c482-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="2c482-107">окне Идентификатор модуля, в котором находится метод.</span><span class="sxs-lookup"><span data-stu-id="2c482-107">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="2c482-108">заполняет Указатель на интерфейс [IMethodMalloc](imethodmalloc-interface.md) , предоставляющий метод для выделения памяти.</span><span class="sxs-lookup"><span data-stu-id="2c482-108">[out] A pointer to an [IMethodMalloc](imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c482-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="2c482-109">Remarks</span></span>  

 <span data-ttu-id="2c482-110">Тело метода в коде MSIL должен располагаться как относительный виртуальный адрес (RVA) относительно загруженного модуля. Это означает, что он следует за модулем в пределах 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="2c482-110">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="2c482-111">Чтобы упростить средство для замены тела метода, `GetILFunctionBodyAllocator` метод обеспечивает выделение памяти в пределах этого диапазона.</span><span class="sxs-lookup"><span data-stu-id="2c482-111">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c482-112">Требования</span><span class="sxs-lookup"><span data-stu-id="2c482-112">Requirements</span></span>  

 <span data-ttu-id="2c482-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c482-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c482-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c482-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c482-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c482-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c482-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c482-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c482-117">См. также</span><span class="sxs-lookup"><span data-stu-id="2c482-117">See also</span></span>

- [<span data-ttu-id="2c482-118">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="2c482-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
