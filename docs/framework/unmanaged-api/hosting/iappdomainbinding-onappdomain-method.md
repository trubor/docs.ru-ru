---
description: 'Дополнительные сведения о методе: Иаппдомаинбиндинг:: onappdomain'
title: Метод IAppDomainBinding::OnAppDomain
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
ms.openlocfilehash: de7f37152261a6fe829026607cf135f3ea0b4a84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760606"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="27414-103">Метод IAppDomainBinding::OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="27414-103">IAppDomainBinding::OnAppDomain Method</span></span>

<span data-ttu-id="27414-104">Вызывается средой CLR для уведомления узла о создании домена приложения.</span><span class="sxs-lookup"><span data-stu-id="27414-104">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27414-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="27414-105">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27414-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="27414-106">Parameters</span></span>  

 `pAppdomain`  
 <span data-ttu-id="27414-107">окне Указатель на объект интерфейса [IUnknown](/cpp/atl/iunknown) , представляющий новый домен приложения.</span><span class="sxs-lookup"><span data-stu-id="27414-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27414-108">Требования</span><span class="sxs-lookup"><span data-stu-id="27414-108">Requirements</span></span>  

 <span data-ttu-id="27414-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27414-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27414-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="27414-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27414-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27414-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27414-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27414-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27414-113">См. также</span><span class="sxs-lookup"><span data-stu-id="27414-113">See also</span></span>

- [<span data-ttu-id="27414-114">Интерфейс IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="27414-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
