---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback2::D Естройконнектион'
title: Метод ICorDebugManagedCallback2::DestroyConnection
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: f17def5599dc02ed6b7b49d7f8ed4db02eb40181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790897"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="abb54-103">Метод ICorDebugManagedCallback2::DestroyConnection</span><span class="sxs-lookup"><span data-stu-id="abb54-103">ICorDebugManagedCallback2::DestroyConnection Method</span></span>

<span data-ttu-id="abb54-104">Уведомляет отладчик о завершении указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="abb54-104">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb54-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="abb54-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abb54-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="abb54-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="abb54-107">окне Указатель на объект ICorDebugProcess, представляющий процесс, содержащий удаленное соединение.</span><span class="sxs-lookup"><span data-stu-id="abb54-107">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="abb54-108">окне Идентификатор уничтоженного соединения.</span><span class="sxs-lookup"><span data-stu-id="abb54-108">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abb54-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="abb54-109">Remarks</span></span>  

 <span data-ttu-id="abb54-110">`DestroyConnection`Обратный вызов будет срабатывать, когда узел вызывает [ICLRDebugManager:: ЕНДКОННЕКТИОН](../hosting/iclrdebugmanager-endconnection-method.md) в [API размещения](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="abb54-110">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb54-111">Требования</span><span class="sxs-lookup"><span data-stu-id="abb54-111">Requirements</span></span>  

 <span data-ttu-id="abb54-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abb54-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abb54-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abb54-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abb54-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abb54-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abb54-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abb54-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb54-116">См. также</span><span class="sxs-lookup"><span data-stu-id="abb54-116">See also</span></span>

- [<span data-ttu-id="abb54-117">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="abb54-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="abb54-118">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="abb54-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
