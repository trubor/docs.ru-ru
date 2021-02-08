---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Свитчинлогикалсреадстате'
title: Метод ICorRuntimeHost::SwitchInLogicalThreadState
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
ms.openlocfilehash: 3e375379cc5d6af7c3a8fb8d64a40a389e0f9dcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789571"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="0f741-103">Метод ICorRuntimeHost::SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="0f741-103">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>

<span data-ttu-id="0f741-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="0f741-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f741-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f741-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f741-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f741-106">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="0f741-107">окне Файл cookie, указывающий используемое волокно.</span><span class="sxs-lookup"><span data-stu-id="0f741-107">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f741-108">Требования</span><span class="sxs-lookup"><span data-stu-id="0f741-108">Requirements</span></span>  

 <span data-ttu-id="0f741-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f741-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f741-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f741-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f741-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f741-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f741-112">**Версия платформа .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="0f741-112">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f741-113">См. также</span><span class="sxs-lookup"><span data-stu-id="0f741-113">See also</span></span>

- [<span data-ttu-id="0f741-114">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0f741-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
