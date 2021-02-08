---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback2:: FunctionRemapOpportunity'
title: Метод ICorDebugManagedCallback2::FunctionRemapOpportunity
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
ms.openlocfilehash: 901a9432ddf17efabd96153581b816f653ff501d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790871"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="dcaa6-103">Метод ICorDebugManagedCallback2::FunctionRemapOpportunity</span><span class="sxs-lookup"><span data-stu-id="dcaa6-103">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>

<span data-ttu-id="dcaa6-104">Уведомляет отладчик о том, что выполнение кода достигло точки последовательности в более ранней версии измененной функции.</span><span class="sxs-lookup"><span data-stu-id="dcaa6-104">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcaa6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dcaa6-105">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcaa6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcaa6-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="dcaa6-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий измененную функцию.</span><span class="sxs-lookup"><span data-stu-id="dcaa6-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="dcaa6-108">окне Указатель на объект ICorDebugThread, представляющий поток, в котором была обнаружена точка останова сопоставления.</span><span class="sxs-lookup"><span data-stu-id="dcaa6-108">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="dcaa6-109">окне Указатель на объект ICorDebugFunction, представляющий версию функции, которая в данный момент выполняется в потоке.</span><span class="sxs-lookup"><span data-stu-id="dcaa6-109">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="dcaa6-110">окне Указатель на объект ICorDebugFunction, представляющий последнюю версию функции.</span><span class="sxs-lookup"><span data-stu-id="dcaa6-110">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="dcaa6-111">окне Смещение указателя инструкции в старой версии функции на языке MSIL.</span><span class="sxs-lookup"><span data-stu-id="dcaa6-111">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcaa6-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="dcaa6-112">Remarks</span></span>  

 <span data-ttu-id="dcaa6-113">Этот обратный вызов дает отладчику возможность перенаправить указатель инструкции в соответствующую позицию в новой версии указанной функции, вызвав метод [ICorDebugILFrame2:: RemapFunction](icordebugilframe2-remapfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dcaa6-113">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="dcaa6-114">Если отладчик не вызывает `RemapFunction` метод [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , среда выполнения продолжит выполнение старого кода и запустит другой `FunctionRemapOpportunity` обратный вызов в следующей точке последовательности.</span><span class="sxs-lookup"><span data-stu-id="dcaa6-114">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="dcaa6-115">Этот обратный вызов будет вызываться для каждого кадра, который выполняет более старую версию данной функции до тех пор, пока отладчик не возвратит S_OK.</span><span class="sxs-lookup"><span data-stu-id="dcaa6-115">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcaa6-116">Требования</span><span class="sxs-lookup"><span data-stu-id="dcaa6-116">Requirements</span></span>  

 <span data-ttu-id="dcaa6-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcaa6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcaa6-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcaa6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcaa6-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcaa6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcaa6-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcaa6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcaa6-121">См. также</span><span class="sxs-lookup"><span data-stu-id="dcaa6-121">See also</span></span>

- [<span data-ttu-id="dcaa6-122">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="dcaa6-122">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="dcaa6-123">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="dcaa6-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
