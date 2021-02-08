---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: Жеселперсреадид'
title: Метод ICorDebugProcess::GetHelperThreadID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: ee7bd2106a37c5c67df48a54ff9ab7fa49a03f80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801024"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="873fe-103">Метод ICorDebugProcess::GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="873fe-103">ICorDebugProcess::GetHelperThreadID Method</span></span>

<span data-ttu-id="873fe-104">Получает идентификатор потока операционной системы (ОС) внутреннего вспомогательного потока отладчика.</span><span class="sxs-lookup"><span data-stu-id="873fe-104">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="873fe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="873fe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="873fe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="873fe-106">Parameters</span></span>  

 `pThreadID`  
 <span data-ttu-id="873fe-107">заполняет Указатель на идентификатор потока операционной системы внутреннего вспомогательного потока отладчика.</span><span class="sxs-lookup"><span data-stu-id="873fe-107">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="873fe-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="873fe-108">Remarks</span></span>  

 <span data-ttu-id="873fe-109">Во время управляемой и неуправляемой отладки следует следить за тем, чтобы поток с указанным ИДЕНТИФИКАТОРом оставался в работоспособном режиме, если он достигнет точки останова, размещенной отладчиком.</span><span class="sxs-lookup"><span data-stu-id="873fe-109">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="873fe-110">Отладчику также может потребоваться скрыть этот поток от пользователя.</span><span class="sxs-lookup"><span data-stu-id="873fe-110">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="873fe-111">Если в процессе еще не существует вспомогательного потока, `GetHelperThreadID` метод возвращает ноль в \* `pThreadID` .</span><span class="sxs-lookup"><span data-stu-id="873fe-111">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="873fe-112">Невозможно кэшировать идентификатор потока вспомогательного потока, так как он может измениться со временем.</span><span class="sxs-lookup"><span data-stu-id="873fe-112">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="873fe-113">Необходимо повторно запросить идентификатор потока при каждом событии остановки.</span><span class="sxs-lookup"><span data-stu-id="873fe-113">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="873fe-114">Идентификатор потока вспомогательного потока отладчика будет правильным для каждого неуправляемого события [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) , что позволяет отладчику определить идентификатор потока вспомогательного потока и скрыть его от пользователя.</span><span class="sxs-lookup"><span data-stu-id="873fe-114">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="873fe-115">Поток, идентифицированный в виде вспомогательного потока во время неуправляемого `ICorDebugManagedCallback::CreateThread` события, никогда не будет запускать управляемый пользовательский код.</span><span class="sxs-lookup"><span data-stu-id="873fe-115">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="873fe-116">Требования</span><span class="sxs-lookup"><span data-stu-id="873fe-116">Requirements</span></span>  

 <span data-ttu-id="873fe-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="873fe-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="873fe-118">**Заголовок:** CorDebug. idl.</span><span class="sxs-lookup"><span data-stu-id="873fe-118">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="873fe-119">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="873fe-119">CorDebug.h</span></span>  
  
 <span data-ttu-id="873fe-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="873fe-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="873fe-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="873fe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
