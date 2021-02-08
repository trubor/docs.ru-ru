---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: ExitAppDomain'
title: Метод ICorDebugManagedCallback::ExitAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: a08f29c6c4c8196b968118433c31afb715935aec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803624"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="ab6b3-103">Метод ICorDebugManagedCallback::ExitAppDomain</span><span class="sxs-lookup"><span data-stu-id="ab6b3-103">ICorDebugManagedCallback::ExitAppDomain Method</span></span>

<span data-ttu-id="ab6b3-104">Уведомляет отладчик о завершении работы домена приложения.</span><span class="sxs-lookup"><span data-stu-id="ab6b3-104">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab6b3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab6b3-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab6b3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ab6b3-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="ab6b3-107">окне Указатель на объект ICorDebugProcess, представляющий процесс, который содержит заданный домен приложения.</span><span class="sxs-lookup"><span data-stu-id="ab6b3-107">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="ab6b3-108">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, который завершил работу.</span><span class="sxs-lookup"><span data-stu-id="ab6b3-108">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab6b3-109">Требования</span><span class="sxs-lookup"><span data-stu-id="ab6b3-109">Requirements</span></span>  

 <span data-ttu-id="ab6b3-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab6b3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab6b3-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab6b3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab6b3-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab6b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab6b3-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab6b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6b3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="ab6b3-114">See also</span></span>

- [<span data-ttu-id="ab6b3-115">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="ab6b3-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
