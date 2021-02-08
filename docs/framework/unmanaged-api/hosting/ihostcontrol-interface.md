---
description: 'Дополнительные сведения о: интерфейс IHostControl'
title: Интерфейс IHostControl
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: e7a242ed0fdaa734425bec9b48f01fe45cba5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789467"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="1b60c-103">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="1b60c-103">IHostControl Interface</span></span>

<span data-ttu-id="1b60c-104">Предоставляет методы для настройки загрузки сборок и для определения того, какие интерфейсы размещения поддерживает узел.</span><span class="sxs-lookup"><span data-stu-id="1b60c-104">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b60c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="1b60c-105">Methods</span></span>  
  
|<span data-ttu-id="1b60c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="1b60c-106">Method</span></span>|<span data-ttu-id="1b60c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="1b60c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b60c-108">Метод GetHostManager</span><span class="sxs-lookup"><span data-stu-id="1b60c-108">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="1b60c-109">Возвращает указатель интерфейса на реализацию интерфейса узла с указанным `IID` .</span><span class="sxs-lookup"><span data-stu-id="1b60c-109">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="1b60c-110">Метод SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="1b60c-110">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="1b60c-111">Уведомляет узел о том, что домен приложения создан.</span><span class="sxs-lookup"><span data-stu-id="1b60c-111">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b60c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="1b60c-112">Requirements</span></span>  

 <span data-ttu-id="1b60c-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b60c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b60c-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b60c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b60c-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b60c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b60c-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b60c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b60c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1b60c-117">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="1b60c-118">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1b60c-118">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="1b60c-119">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="1b60c-119">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1b60c-120">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="1b60c-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
