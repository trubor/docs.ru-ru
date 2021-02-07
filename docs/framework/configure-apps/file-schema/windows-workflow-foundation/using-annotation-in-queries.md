---
description: 'Дополнительные сведения о: использование аннотации в запросах'
title: Использование заметок в запросах
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 97423fe8ea7d90522a5f469adda5f645aa7e4485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698028"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="67587-103">Использование заметок в запросах</span><span class="sxs-lookup"><span data-stu-id="67587-103">Using Annotation in Queries</span></span>

<span data-ttu-id="67587-104">Заметки позволяют произвольно добавлять теги для записей отслеживания со значением, которое можно изменить после построения.</span><span class="sxs-lookup"><span data-stu-id="67587-104">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="67587-105">Например, может потребоваться, чтобы несколько записей отслеживания в нескольких рабочих процессах были помечены как "почтовый сервер" = = "почта Server1".</span><span class="sxs-lookup"><span data-stu-id="67587-105">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="67587-106">Это упростит поиск всех записей с этим тегом при последующем составлении запроса записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="67587-106">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="67587-107">Добавление заметок</span><span class="sxs-lookup"><span data-stu-id="67587-107">Adding Annotations</span></span>  

 <span data-ttu-id="67587-108">В следующем примере показано, как добавить заметку к запросу отслеживания.</span><span class="sxs-lookup"><span data-stu-id="67587-108">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
> <span data-ttu-id="67587-109">Эти элементы запроса могут быть использованы для создания профиля отслеживания.</span><span class="sxs-lookup"><span data-stu-id="67587-109">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="67587-110">Профиль отслеживания можно создать в коде или в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="67587-110">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67587-111">См. также</span><span class="sxs-lookup"><span data-stu-id="67587-111">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [<span data-ttu-id="67587-112">Отслеживание и трассировка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="67587-112">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="67587-113">Профили отслеживания</span><span class="sxs-lookup"><span data-stu-id="67587-113">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
