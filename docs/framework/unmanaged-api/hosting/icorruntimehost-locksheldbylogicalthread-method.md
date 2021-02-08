---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Локкшелдбилогикалсреад'
title: Метод ICorRuntimeHost::LocksHeldByLogicalThread
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: bd64151bdc0c6aa0235192f0fc7f4badd8b0bbd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789649"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="9966a-103">Метод ICorRuntimeHost::LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="9966a-103">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>

<span data-ttu-id="9966a-104">Возвращает число блокировок, удерживаемых текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="9966a-104">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="9966a-105">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="9966a-105">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9966a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9966a-106">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9966a-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9966a-107">Parameters</span></span>  

 `pCount`  
 <span data-ttu-id="9966a-108">заполняет Указатель на число блокировок, удерживаемых текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="9966a-108">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9966a-109">Требования</span><span class="sxs-lookup"><span data-stu-id="9966a-109">Requirements</span></span>  

 <span data-ttu-id="9966a-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9966a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9966a-111">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9966a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9966a-112">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9966a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9966a-113">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="9966a-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9966a-114">См. также</span><span class="sxs-lookup"><span data-stu-id="9966a-114">See also</span></span>

- [<span data-ttu-id="9966a-115">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9966a-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
