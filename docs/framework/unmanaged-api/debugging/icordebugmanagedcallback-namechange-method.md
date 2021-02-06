---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: NameChange'
title: Метод ICorDebugManagedCallback::NameChange
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 5f337f5e05b80c97e8b8e48f8b7bc76b3232b2c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660418"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="717db-103">Метод ICorDebugManagedCallback::NameChange</span><span class="sxs-lookup"><span data-stu-id="717db-103">ICorDebugManagedCallback::NameChange Method</span></span>

<span data-ttu-id="717db-104">Уведомляет отладчик о том, что имя домена приложения или потока изменилось.</span><span class="sxs-lookup"><span data-stu-id="717db-104">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="717db-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="717db-105">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="717db-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="717db-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="717db-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в котором либо было изменено имя, либо содержащий поток, в котором было изменено имя.</span><span class="sxs-lookup"><span data-stu-id="717db-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="717db-108">окне Указатель на объект ICorDebugThread, представляющий поток, для которого было изменено имя.</span><span class="sxs-lookup"><span data-stu-id="717db-108">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="717db-109">Требования</span><span class="sxs-lookup"><span data-stu-id="717db-109">Requirements</span></span>  

 <span data-ttu-id="717db-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="717db-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="717db-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="717db-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="717db-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="717db-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="717db-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="717db-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="717db-114">См. также</span><span class="sxs-lookup"><span data-stu-id="717db-114">See also</span></span>

- [<span data-ttu-id="717db-115">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="717db-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
