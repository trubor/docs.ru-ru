---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: точка останова'
title: Метод ICorDebugManagedCallback::Breakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Breakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type:
- apiref
ms.openlocfilehash: dd4339294d8c4061c89bbb0ba7023b313e06102f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660602"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="d35c6-103">Метод ICorDebugManagedCallback::Breakpoint</span><span class="sxs-lookup"><span data-stu-id="d35c6-103">ICorDebugManagedCallback::Breakpoint Method</span></span>

<span data-ttu-id="d35c6-104">Уведомляет отладчик об обнаружении точки останова.</span><span class="sxs-lookup"><span data-stu-id="d35c6-104">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35c6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d35c6-105">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d35c6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d35c6-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d35c6-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий точку останова.</span><span class="sxs-lookup"><span data-stu-id="d35c6-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d35c6-108">окне Указатель на объект ICorDebugThread, представляющий поток, содержащий точку останова.</span><span class="sxs-lookup"><span data-stu-id="d35c6-108">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="d35c6-109">окне Указатель на объект Икордебугбреакпоинт, представляющий точку останова.</span><span class="sxs-lookup"><span data-stu-id="d35c6-109">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d35c6-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d35c6-110">Requirements</span></span>  

 <span data-ttu-id="d35c6-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d35c6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d35c6-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d35c6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d35c6-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d35c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d35c6-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d35c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35c6-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d35c6-115">See also</span></span>

- [<span data-ttu-id="d35c6-116">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="d35c6-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
