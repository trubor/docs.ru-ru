---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: UnloadModule'
title: Метод ICorDebugManagedCallback::UnloadModule
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: d8d37b28d7a7d11000c259f1bcde3138634b2498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754060"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="a38a2-103">Метод ICorDebugManagedCallback::UnloadModule</span><span class="sxs-lookup"><span data-stu-id="a38a2-103">ICorDebugManagedCallback::UnloadModule Method</span></span>

<span data-ttu-id="a38a2-104">Уведомляет отладчик о выгрузке модуля общеязыковой среды выполнения (DLL).</span><span class="sxs-lookup"><span data-stu-id="a38a2-104">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a38a2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a38a2-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a38a2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a38a2-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="a38a2-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в котором содержится модуль.</span><span class="sxs-lookup"><span data-stu-id="a38a2-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="a38a2-108">окне Указатель на объект ICorDebugModule, представляющий модуль.</span><span class="sxs-lookup"><span data-stu-id="a38a2-108">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a38a2-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="a38a2-109">Remarks</span></span>  

 <span data-ttu-id="a38a2-110">Модуль не должен использоваться после этого вызова.</span><span class="sxs-lookup"><span data-stu-id="a38a2-110">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a38a2-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a38a2-111">Requirements</span></span>  

 <span data-ttu-id="a38a2-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a38a2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a38a2-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a38a2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a38a2-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a38a2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a38a2-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a38a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a38a2-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a38a2-116">See also</span></span>

- [<span data-ttu-id="a38a2-117">Метод LoadModule</span><span class="sxs-lookup"><span data-stu-id="a38a2-117">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="a38a2-118">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a38a2-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
