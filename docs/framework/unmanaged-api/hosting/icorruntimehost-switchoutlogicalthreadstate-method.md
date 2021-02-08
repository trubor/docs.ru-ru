---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Свитчаутлогикалсреадстате'
title: Метод ICorRuntimeHost::SwitchOutLogicalThreadState
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
ms.openlocfilehash: b4190ebe6b2c260f85afd8dd17127d0c63dca6c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799451"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="6ce97-103">Метод ICorRuntimeHost::SwitchOutLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="6ce97-103">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>

<span data-ttu-id="6ce97-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="6ce97-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce97-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6ce97-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ce97-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6ce97-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="6ce97-107">заполняет Файл cookie, указывающий на то, что выполняется переключение на волокно.</span><span class="sxs-lookup"><span data-stu-id="6ce97-107">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ce97-108">Требования</span><span class="sxs-lookup"><span data-stu-id="6ce97-108">Requirements</span></span>  

 <span data-ttu-id="6ce97-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ce97-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ce97-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ce97-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ce97-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ce97-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ce97-112">**Версия платформа .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="6ce97-112">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce97-113">См. также</span><span class="sxs-lookup"><span data-stu-id="6ce97-113">See also</span></span>

- [<span data-ttu-id="6ce97-114">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6ce97-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
