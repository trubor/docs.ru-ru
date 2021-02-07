---
description: 'Дополнительные сведения о: Сервицеаппдомаин'
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 1ac32b1fbd88518ffb260be9dd3ed2adb88d211c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715643"
---
# <a name="serviceappdomain"></a><span data-ttu-id="d9199-103">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="d9199-103">ServiceAppDomain</span></span>

<span data-ttu-id="d9199-104">Сопоставляет службу с доменом приложения.</span><span class="sxs-lookup"><span data-stu-id="d9199-104">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9199-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9199-105">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d9199-106">Методы</span><span class="sxs-lookup"><span data-stu-id="d9199-106">Methods</span></span>  

 <span data-ttu-id="d9199-107">Класс ServiceAppDomain не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="d9199-107">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d9199-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="d9199-108">Properties</span></span>  

 <span data-ttu-id="d9199-109">Класс ServiceAppDomain имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="d9199-109">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="d9199-110">ref</span><span class="sxs-lookup"><span data-stu-id="d9199-110">ref</span></span>  

 <span data-ttu-id="d9199-111">Тип данных: Service</span><span class="sxs-lookup"><span data-stu-id="d9199-111">Data type: Service</span></span>  
<span data-ttu-id="d9199-112">Квалификаторы: ключ</span><span class="sxs-lookup"><span data-stu-id="d9199-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="d9199-113">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d9199-113">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9199-114">Служба этого домена приложения.</span><span class="sxs-lookup"><span data-stu-id="d9199-114">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="d9199-115">ref</span><span class="sxs-lookup"><span data-stu-id="d9199-115">ref</span></span>  

 <span data-ttu-id="d9199-116">Тип данных: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="d9199-116">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="d9199-117">Квалификаторы: ключ</span><span class="sxs-lookup"><span data-stu-id="d9199-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="d9199-118">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="d9199-118">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9199-119">Содержит свойства домена приложения.</span><span class="sxs-lookup"><span data-stu-id="d9199-119">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9199-120">Требования</span><span class="sxs-lookup"><span data-stu-id="d9199-120">Requirements</span></span>  
  
|<span data-ttu-id="d9199-121">MOF</span><span class="sxs-lookup"><span data-stu-id="d9199-121">MOF</span></span>|<span data-ttu-id="d9199-122">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d9199-122">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d9199-123">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="d9199-123">Namespace</span></span>|<span data-ttu-id="d9199-124">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="d9199-124">Defined in root\ServiceModel</span></span>|
