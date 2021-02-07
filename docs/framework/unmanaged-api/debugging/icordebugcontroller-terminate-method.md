---
description: 'Дополнительные сведения о методе: ICorDebugController:: Terminate'
title: Метод ICorDebugController::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: 15cc832205ebfe86e521d4a45124808e0f3fe128
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710716"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="8d84f-103">Метод ICorDebugController::Terminate</span><span class="sxs-lookup"><span data-stu-id="8d84f-103">ICorDebugController::Terminate Method</span></span>

<span data-ttu-id="8d84f-104">Завершает процесс с указанным кодом выхода.</span><span class="sxs-lookup"><span data-stu-id="8d84f-104">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d84f-105">Этот метод является оболочкой для функции Win32 `TerminateProcess` .</span><span class="sxs-lookup"><span data-stu-id="8d84f-105">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="8d84f-106">Таким образом, `Terminate` использует код выхода точно так же, как функция Win32 `TerminateProcess` использует ее.</span><span class="sxs-lookup"><span data-stu-id="8d84f-106">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d84f-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d84f-107">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d84f-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="8d84f-108">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="8d84f-109">окне Числовое значение, которое является кодом выхода.</span><span class="sxs-lookup"><span data-stu-id="8d84f-109">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="8d84f-110">Допустимые числовые значения определяются в Винбасе. h.</span><span class="sxs-lookup"><span data-stu-id="8d84f-110">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d84f-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="8d84f-111">Remarks</span></span>  

 <span data-ttu-id="8d84f-112">Если процесс останавливается при `Terminate` вызове, процесс должен быть продолжен с помощью метода [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , чтобы отладчик получал подтверждение завершения, используя обратный вызов [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) или [ICorDebugManagedCallback:: ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8d84f-112">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d84f-113">Этот метод не реализуется доменом приложения.</span><span class="sxs-lookup"><span data-stu-id="8d84f-113">This method is not implemented by an application domain.</span></span> <span data-ttu-id="8d84f-114">Это значит, что он не реализован на <xref:System.AppDomain> уровне.</span><span class="sxs-lookup"><span data-stu-id="8d84f-114">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d84f-115">Требования</span><span class="sxs-lookup"><span data-stu-id="8d84f-115">Requirements</span></span>  

 <span data-ttu-id="8d84f-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d84f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d84f-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d84f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d84f-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d84f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d84f-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d84f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d84f-120">См. также</span><span class="sxs-lookup"><span data-stu-id="8d84f-120">See also</span></span>
