---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: CreateThread'
title: Метод ICorDebugManagedCallback::CreateThread
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 20d5ce9da34e7082502252eeece2ab34b1f2e902
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791037"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="4c5fa-103">Метод ICorDebugManagedCallback::CreateThread</span><span class="sxs-lookup"><span data-stu-id="4c5fa-103">ICorDebugManagedCallback::CreateThread Method</span></span>

<span data-ttu-id="4c5fa-104">Уведомляет отладчик о том, что поток начал выполнение управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="4c5fa-104">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c5fa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c5fa-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c5fa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4c5fa-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="4c5fa-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий поток.</span><span class="sxs-lookup"><span data-stu-id="4c5fa-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="4c5fa-108">окне Указатель на объект ICorDebugThread, представляющий поток.</span><span class="sxs-lookup"><span data-stu-id="4c5fa-108">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c5fa-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c5fa-109">Remarks</span></span>  

 <span data-ttu-id="4c5fa-110">Поток будет размещен в первой выполняемой инструкции управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="4c5fa-110">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c5fa-111">Требования</span><span class="sxs-lookup"><span data-stu-id="4c5fa-111">Requirements</span></span>  

 <span data-ttu-id="4c5fa-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c5fa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c5fa-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c5fa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c5fa-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c5fa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c5fa-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c5fa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5fa-116">См. также</span><span class="sxs-lookup"><span data-stu-id="4c5fa-116">See also</span></span>

- [<span data-ttu-id="4c5fa-117">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="4c5fa-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
