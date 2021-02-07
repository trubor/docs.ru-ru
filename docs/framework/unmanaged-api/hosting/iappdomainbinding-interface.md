---
description: 'Дополнительные сведения о: интерфейс Иаппдомаинбиндинг'
title: Интерфейс IAppDomainBinding
ms.date: 03/30/2017
api_name:
- IAppDomainBinding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainBinding
helpviewer_keywords:
- IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type:
- apiref
ms.openlocfilehash: 3de559af023311f705f9f7dc6eb9785788216a83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760619"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="60a9f-103">Интерфейс IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="60a9f-103">IAppDomainBinding Interface</span></span>

<span data-ttu-id="60a9f-104">Предоставляет метод, вызываемый средой CLR для уведомления ведущего приложения о создании домена приложения.</span><span class="sxs-lookup"><span data-stu-id="60a9f-104">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60a9f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="60a9f-105">Methods</span></span>  
  
|<span data-ttu-id="60a9f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="60a9f-106">Method</span></span>|<span data-ttu-id="60a9f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="60a9f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60a9f-108">Метод OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="60a9f-108">OnAppDomain Method</span></span>](iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="60a9f-109">Вызывается средой CLR для уведомления узла о создании домена приложения.</span><span class="sxs-lookup"><span data-stu-id="60a9f-109">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60a9f-110">Требования</span><span class="sxs-lookup"><span data-stu-id="60a9f-110">Requirements</span></span>  

 <span data-ttu-id="60a9f-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a9f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a9f-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="60a9f-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60a9f-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60a9f-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60a9f-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a9f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a9f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="60a9f-115">See also</span></span>

- [<span data-ttu-id="60a9f-116">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="60a9f-116">Hosting Interfaces</span></span>](hosting-interfaces.md)
