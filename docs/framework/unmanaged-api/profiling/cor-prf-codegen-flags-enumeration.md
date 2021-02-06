---
description: 'Дополнительные сведения: перечисление COR_PRF_CODEGEN_FLAGS'
title: Перечисление COR_PRF_CODEGEN_FLAGS
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 40ddaa77047e0b1daa743b512f21ba7643127230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649180"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="12363-103">Перечисление COR_PRF_CODEGEN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="12363-103">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>

<span data-ttu-id="12363-104">Определяет флаги создания кода, которые можно задать с помощью метода [икорпрофилерфунктионконтрол:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="12363-104">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12363-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="12363-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="12363-106">Члены</span><span class="sxs-lookup"><span data-stu-id="12363-106">Members</span></span>  
  
|<span data-ttu-id="12363-107">Член</span><span class="sxs-lookup"><span data-stu-id="12363-107">Member</span></span>|<span data-ttu-id="12363-108">Описание</span><span class="sxs-lookup"><span data-stu-id="12363-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="12363-109">Никакие функции не будут встроены в текст этой функции.</span><span class="sxs-lookup"><span data-stu-id="12363-109">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="12363-110">Однако сама функция может быть встроена в ее вызывающие объекты.</span><span class="sxs-lookup"><span data-stu-id="12363-110">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="12363-111">Для текста этой функции будут отключены все оптимизации.</span><span class="sxs-lookup"><span data-stu-id="12363-111">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="12363-112">Однако сама функция по-прежнему может быть встроена в ее вызывающие объекты.</span><span class="sxs-lookup"><span data-stu-id="12363-112">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12363-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="12363-113">Remarks</span></span>  

 <span data-ttu-id="12363-114">`COR_PRF_CODEGEN_FLAGS`Перечисление используется методом [икорпрофилерфунктионконтрол:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) , чтобы позволить профилировщику управлять созданием кода для JIT-перекомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="12363-114">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12363-115">Требования</span><span class="sxs-lookup"><span data-stu-id="12363-115">Requirements</span></span>  

 <span data-ttu-id="12363-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12363-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12363-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12363-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12363-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12363-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12363-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12363-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12363-120">См. также</span><span class="sxs-lookup"><span data-stu-id="12363-120">See also</span></span>

- [<span data-ttu-id="12363-121">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="12363-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
