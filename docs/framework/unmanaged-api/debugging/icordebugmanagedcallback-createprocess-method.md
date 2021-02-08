---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: CreateProcess'
title: Метод ICorDebugManagedCallback::CreateProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
ms.openlocfilehash: 564c9862dd90431f0626204fdfe49e59b85a124d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791053"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="10620-103">Метод ICorDebugManagedCallback::CreateProcess</span><span class="sxs-lookup"><span data-stu-id="10620-103">ICorDebugManagedCallback::CreateProcess Method</span></span>

<span data-ttu-id="10620-104">Уведомляет отладчик о том, что процесс был присоединен или запущен в первый раз.</span><span class="sxs-lookup"><span data-stu-id="10620-104">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10620-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="10620-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10620-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="10620-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="10620-107">окне Указатель на объект ICorDebugProcess, представляющий процесс, который был присоединен или запущен.</span><span class="sxs-lookup"><span data-stu-id="10620-107">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10620-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="10620-108">Remarks</span></span>  

 <span data-ttu-id="10620-109">Этот метод не вызывается до тех пор, пока не будет инициализирована среда CLR.</span><span class="sxs-lookup"><span data-stu-id="10620-109">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="10620-110">Большая часть методов [ICorDebug](icordebug-interface.md) возвратит CORDBG_E_NOTREADY перед `CreateProcess` обратным вызовом.</span><span class="sxs-lookup"><span data-stu-id="10620-110">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10620-111">Требования</span><span class="sxs-lookup"><span data-stu-id="10620-111">Requirements</span></span>  

 <span data-ttu-id="10620-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10620-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10620-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10620-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10620-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10620-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10620-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10620-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10620-116">См. также</span><span class="sxs-lookup"><span data-stu-id="10620-116">See also</span></span>

- [<span data-ttu-id="10620-117">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="10620-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
