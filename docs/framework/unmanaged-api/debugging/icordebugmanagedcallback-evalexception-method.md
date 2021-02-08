---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: Евалексцептион'
title: Метод ICorDebugManagedCallback::EvalException
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
ms.openlocfilehash: 0938276a854020efa897499af8c0fd69c0541124
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790988"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="b1ffc-103">Метод ICorDebugManagedCallback::EvalException</span><span class="sxs-lookup"><span data-stu-id="b1ffc-103">ICorDebugManagedCallback::EvalException Method</span></span>

<span data-ttu-id="b1ffc-104">Уведомляет отладчик о том, что вычисление завершено с необработанным исключением.</span><span class="sxs-lookup"><span data-stu-id="b1ffc-104">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ffc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b1ffc-105">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1ffc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b1ffc-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="b1ffc-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в котором завершается вычисление.</span><span class="sxs-lookup"><span data-stu-id="b1ffc-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b1ffc-108">окне Указатель на объект ICorDebugThread, представляющий поток, в котором завершено вычисление.</span><span class="sxs-lookup"><span data-stu-id="b1ffc-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="b1ffc-109">окне Указатель на объект ICorDebugEval, представляющий код, который выполнил вычисление.</span><span class="sxs-lookup"><span data-stu-id="b1ffc-109">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1ffc-110">Требования</span><span class="sxs-lookup"><span data-stu-id="b1ffc-110">Requirements</span></span>  

 <span data-ttu-id="b1ffc-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1ffc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1ffc-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1ffc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1ffc-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1ffc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1ffc-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1ffc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ffc-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b1ffc-115">See also</span></span>

- [<span data-ttu-id="b1ffc-116">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b1ffc-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
