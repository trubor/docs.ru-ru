---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: Exception'
title: Метод ICorDebugManagedCallback::Exception
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
ms.openlocfilehash: f738c328e1f6edfeb61a1d5e2ba8f9dd827d05dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790975"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="6f951-103">Метод ICorDebugManagedCallback::Exception</span><span class="sxs-lookup"><span data-stu-id="6f951-103">ICorDebugManagedCallback::Exception Method</span></span>

<span data-ttu-id="6f951-104">Уведомляет отладчик о появлении исключения из управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="6f951-104">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f951-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6f951-105">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f951-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f951-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="6f951-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в котором было создано исключение.</span><span class="sxs-lookup"><span data-stu-id="6f951-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6f951-108">окне Указатель на объект ICorDebugThread, представляющий поток, в котором было создано исключение.</span><span class="sxs-lookup"><span data-stu-id="6f951-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="6f951-109">окне Если это значение равно `false` , исключение еще не было обработано приложением; в противном случае исключение не обрабатывается, и процесс завершится.</span><span class="sxs-lookup"><span data-stu-id="6f951-109">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f951-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="6f951-110">Remarks</span></span>  

 <span data-ttu-id="6f951-111">Конкретное исключение можно получить из объекта потока.</span><span class="sxs-lookup"><span data-stu-id="6f951-111">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f951-112">Требования</span><span class="sxs-lookup"><span data-stu-id="6f951-112">Requirements</span></span>  

 <span data-ttu-id="6f951-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f951-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f951-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f951-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f951-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f951-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f951-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f951-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f951-117">См. также</span><span class="sxs-lookup"><span data-stu-id="6f951-117">See also</span></span>

- [<span data-ttu-id="6f951-118">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="6f951-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
