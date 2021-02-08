---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback::D Ебугжереррор'
title: Метод ICorDebugManagedCallback::DebuggerError
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: 2f73e07711f7d2ce865aab8f90862563e767fd16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791010"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="f9c0d-103">Метод ICorDebugManagedCallback::DebuggerError</span><span class="sxs-lookup"><span data-stu-id="f9c0d-103">ICorDebugManagedCallback::DebuggerError Method</span></span>

<span data-ttu-id="f9c0d-104">Уведомляет отладчик о том, что произошла ошибка при попытке выполнить обработку события из среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f9c0d-104">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c0d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f9c0d-105">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9c0d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f9c0d-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="f9c0d-107">окне Указатель на объект "ICorDebugProcess", представляющий процесс, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="f9c0d-107">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="f9c0d-108">окне Значение HRESULT, возвращенное обработчиком событий.</span><span class="sxs-lookup"><span data-stu-id="f9c0d-108">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="f9c0d-109">окне Целое число, указывающее ошибку CLR.</span><span class="sxs-lookup"><span data-stu-id="f9c0d-109">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9c0d-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="f9c0d-110">Remarks</span></span>  

 <span data-ttu-id="f9c0d-111">Процесс может быть помещен в сквозной режим в зависимости от характера ошибки.</span><span class="sxs-lookup"><span data-stu-id="f9c0d-111">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="f9c0d-112">`DebugError`Обратный вызов указывает, что службы отладки были отключены из-за ошибки, поэтому Отладчики должны сделать сообщение об ошибке доступным для пользователя.</span><span class="sxs-lookup"><span data-stu-id="f9c0d-112">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="f9c0d-113">[ICorDebugProcess:: GetID](icordebugprocess-getid-method.md) будет использоваться в качестве безопасного вызова, но все остальные методы, включая [ICorDebug:: Terminate](icordebug-terminate-method.md), не должны вызываться.</span><span class="sxs-lookup"><span data-stu-id="f9c0d-113">[ICorDebugProcess::GetID](icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="f9c0d-114">Отладчик должен использовать средства операционной системы для завершения процессов.</span><span class="sxs-lookup"><span data-stu-id="f9c0d-114">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c0d-115">Требования</span><span class="sxs-lookup"><span data-stu-id="f9c0d-115">Requirements</span></span>  

 <span data-ttu-id="f9c0d-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9c0d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9c0d-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9c0d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9c0d-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9c0d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9c0d-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9c0d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c0d-120">См. также</span><span class="sxs-lookup"><span data-stu-id="f9c0d-120">See also</span></span>

- [<span data-ttu-id="f9c0d-121">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="f9c0d-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
