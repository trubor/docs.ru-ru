---
description: 'Дополнительные сведения о: интерфейс Иклрдомаинманажер'
title: Интерфейс ICLRDomainManager
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: d719e89d81e8c7abb1f238ce50b4e236de17ac72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790013"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="f5cff-103">Интерфейс ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="f5cff-103">ICLRDomainManager Interface</span></span>

<span data-ttu-id="f5cff-104">Позволяет узлу указать Диспетчер домена приложения, который будет использоваться для инициализации домена приложения по умолчанию, а также для указания свойств инициализации.</span><span class="sxs-lookup"><span data-stu-id="f5cff-104">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5cff-105">Методы</span><span class="sxs-lookup"><span data-stu-id="f5cff-105">Methods</span></span>  
  
|<span data-ttu-id="f5cff-106">Метод</span><span class="sxs-lookup"><span data-stu-id="f5cff-106">Method</span></span>|<span data-ttu-id="f5cff-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f5cff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5cff-108">Метод SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="f5cff-108">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="f5cff-109">Задает тип, производный от <xref:System.AppDomainManager?displayProperty=nameWithType> класса диспетчера домена приложения, который будет использоваться для инициализации домена приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f5cff-109">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="f5cff-110">Метод SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="f5cff-110">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="f5cff-111">Задает свойства, которые будут использоваться для инициализации домена приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f5cff-111">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5cff-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="f5cff-112">Remarks</span></span>  

 <span data-ttu-id="f5cff-113">Чтобы получить экземпляр этого интерфейса, вызовите метод [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) с типом менеджера IID `IID_ICLRDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="f5cff-113">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5cff-114">Требования</span><span class="sxs-lookup"><span data-stu-id="f5cff-114">Requirements</span></span>  

 <span data-ttu-id="f5cff-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5cff-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5cff-116">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="f5cff-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f5cff-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5cff-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5cff-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5cff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cff-119">См. также</span><span class="sxs-lookup"><span data-stu-id="f5cff-119">See also</span></span>

- [<span data-ttu-id="f5cff-120">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="f5cff-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f5cff-121">Размещение</span><span class="sxs-lookup"><span data-stu-id="f5cff-121">Hosting</span></span>](index.md)
