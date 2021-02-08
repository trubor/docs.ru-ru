---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback2:: Ексцептионунвинд'
title: Метод ICorDebugManagedCallback2::ExceptionUnwind
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 2d98fb21cdbb0db25a11761ac9b00e99e1526cc0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790854"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="d7a5c-103">Метод ICorDebugManagedCallback2::ExceptionUnwind</span><span class="sxs-lookup"><span data-stu-id="d7a5c-103">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>

<span data-ttu-id="d7a5c-104">Предоставляет уведомление о состоянии во время процесса очистки исключения.</span><span class="sxs-lookup"><span data-stu-id="d7a5c-104">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7a5c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d7a5c-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7a5c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7a5c-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d7a5c-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий поток, в котором было создано исключение.</span><span class="sxs-lookup"><span data-stu-id="d7a5c-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d7a5c-108">окне Указатель на объект ICorDebugThread, представляющий поток, в котором было создано исключение.</span><span class="sxs-lookup"><span data-stu-id="d7a5c-108">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="d7a5c-109">окне Значение перечисления Кордебужексцептионунвиндкаллбакктипе, указывающее событие, сигнальное функцией обратного вызова на этапе очистки.</span><span class="sxs-lookup"><span data-stu-id="d7a5c-109">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d7a5c-110">окне Значение перечисления [кордебужексцептионфлагс](cordebugexceptionflags-enumeration.md) , которое указывает дополнительные сведения об исключении.</span><span class="sxs-lookup"><span data-stu-id="d7a5c-110">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7a5c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="d7a5c-111">Remarks</span></span>  

 <span data-ttu-id="d7a5c-112">`ExceptionUnwind` вызывается в различных точках на этапе очистки процесса обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="d7a5c-112">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="d7a5c-113">`ExceptionUnwind` может вызываться более одного раза при очистке одного исключения.</span><span class="sxs-lookup"><span data-stu-id="d7a5c-113">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="d7a5c-114">Если `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, указатель инструкции будет находиться в конечном кадре потока в точке следования до (это может быть несколько инструкций до) инструкции, вызвавшей исключение.</span><span class="sxs-lookup"><span data-stu-id="d7a5c-114">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7a5c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="d7a5c-115">Requirements</span></span>  

 <span data-ttu-id="d7a5c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7a5c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7a5c-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7a5c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7a5c-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7a5c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7a5c-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7a5c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a5c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="d7a5c-120">See also</span></span>

- [<span data-ttu-id="d7a5c-121">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="d7a5c-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d7a5c-122">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="d7a5c-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
