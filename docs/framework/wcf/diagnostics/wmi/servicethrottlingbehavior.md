---
description: 'Дополнительные сведения о: Сервицесроттлингбехавиор'
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: c4cf354c96340b910807bf7904e63a08dc01764b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715448"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="cef42-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="cef42-103">ServiceThrottlingBehavior</span></span>

<span data-ttu-id="cef42-104">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="cef42-104">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cef42-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cef42-105">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cef42-106">Методы</span><span class="sxs-lookup"><span data-stu-id="cef42-106">Methods</span></span>  

 <span data-ttu-id="cef42-107">Класс ServiceThrottlingBehavior не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="cef42-107">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cef42-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="cef42-108">Properties</span></span>  

 <span data-ttu-id="cef42-109">Класс ServiceThrottlingBehavior имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="cef42-109">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="cef42-110">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="cef42-110">MaxConcurrentCalls</span></span>  

 <span data-ttu-id="cef42-111">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="cef42-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="cef42-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cef42-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cef42-113">Максимальное количество сообщений, которые могут одновременно обрабатываться во всех объектах диспетчера в узле ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="cef42-113">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="cef42-114">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="cef42-114">MaxConcurrentInstances</span></span>  

 <span data-ttu-id="cef42-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="cef42-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="cef42-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cef42-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cef42-117">Максимальное число объектов службы, которые могут выполняться одновременно.</span><span class="sxs-lookup"><span data-stu-id="cef42-117">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="cef42-118">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="cef42-118">MaxConcurrentSessions</span></span>  

 <span data-ttu-id="cef42-119">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="cef42-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="cef42-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cef42-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cef42-121">Максимальное число сеансов, одновременно принимаемых узлом.</span><span class="sxs-lookup"><span data-stu-id="cef42-121">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cef42-122">Требования</span><span class="sxs-lookup"><span data-stu-id="cef42-122">Requirements</span></span>  
  
|<span data-ttu-id="cef42-123">MOF</span><span class="sxs-lookup"><span data-stu-id="cef42-123">MOF</span></span>|<span data-ttu-id="cef42-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cef42-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cef42-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="cef42-125">Namespace</span></span>|<span data-ttu-id="cef42-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="cef42-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cef42-127">См. также</span><span class="sxs-lookup"><span data-stu-id="cef42-127">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
