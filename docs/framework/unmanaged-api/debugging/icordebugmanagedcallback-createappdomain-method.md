---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: CreateAppDomain'
title: Метод ICorDebugManagedCallback::CreateAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 5f4aa49ce90e8ec1343794db71ae3aa911c9e09f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791079"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="cb5e9-103">Метод ICorDebugManagedCallback::CreateAppDomain</span><span class="sxs-lookup"><span data-stu-id="cb5e9-103">ICorDebugManagedCallback::CreateAppDomain Method</span></span>

<span data-ttu-id="cb5e9-104">Уведомляет отладчик о создании домена приложения.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-104">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5e9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb5e9-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb5e9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cb5e9-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="cb5e9-107">окне Указатель на объект ICorDebugProcess, представляющий процесс, в котором был создан домен приложения.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-107">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="cb5e9-108">окне Указатель на объект ICorDebugAppDomain, представляющий созданный домен приложения.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-108">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5e9-109">Требования</span><span class="sxs-lookup"><span data-stu-id="cb5e9-109">Requirements</span></span>  

 <span data-ttu-id="cb5e9-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb5e9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5e9-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb5e9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb5e9-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb5e9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb5e9-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5e9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5e9-114">См. также</span><span class="sxs-lookup"><span data-stu-id="cb5e9-114">See also</span></span>

- [<span data-ttu-id="cb5e9-115">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="cb5e9-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
