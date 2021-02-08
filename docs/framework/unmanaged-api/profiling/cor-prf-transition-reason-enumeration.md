---
description: 'Дополнительные сведения: перечисление COR_PRF_TRANSITION_REASON'
title: Перечисление COR_PRF_TRANSITION_REASON
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 8d0b7852f80f80a47f910e9f1240a5315772cd23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788999"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="eab36-103">Перечисление COR_PRF_TRANSITION_REASON</span><span class="sxs-lookup"><span data-stu-id="eab36-103">COR_PRF_TRANSITION_REASON Enumeration</span></span>

<span data-ttu-id="eab36-104">Указывает причину перехода из управляемого в неуправляемый код или наоборот.</span><span class="sxs-lookup"><span data-stu-id="eab36-104">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab36-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eab36-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="eab36-106">Члены</span><span class="sxs-lookup"><span data-stu-id="eab36-106">Members</span></span>  
  
|<span data-ttu-id="eab36-107">Член</span><span class="sxs-lookup"><span data-stu-id="eab36-107">Member</span></span>|<span data-ttu-id="eab36-108">Описание</span><span class="sxs-lookup"><span data-stu-id="eab36-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="eab36-109">Переход происходит из-за вызова функции.</span><span class="sxs-lookup"><span data-stu-id="eab36-109">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="eab36-110">Переход происходит из-за возврата из функции.</span><span class="sxs-lookup"><span data-stu-id="eab36-110">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eab36-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="eab36-111">Remarks</span></span>  

 <span data-ttu-id="eab36-112">Когда происходит переход, профилировщик получает обратный вызов [ICorProfilerCallback:: манажедтаунманажедтранситион](icorprofilercallback-managedtounmanagedtransition-method.md) или [ICorProfilerCallback:: унманажедтоманажедтранситион](icorprofilercallback-unmanagedtomanagedtransition-method.md) , который предоставляет значение `COR_PRF_TRANSITION_REASON` перечисления для указания причины перехода.</span><span class="sxs-lookup"><span data-stu-id="eab36-112">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab36-113">Требования</span><span class="sxs-lookup"><span data-stu-id="eab36-113">Requirements</span></span>  

 <span data-ttu-id="eab36-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab36-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab36-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eab36-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eab36-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eab36-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eab36-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab36-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
