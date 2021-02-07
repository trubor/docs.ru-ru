---
description: 'Дополнительные сведения: Отслеживание переменных и аргументов'
title: Отслеживание переменной и аргумента
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: f2663e585ca280739f9c4ec176c31cf1d7c30657
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754983"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="cb62b-103">Отслеживание переменной и аргумента</span><span class="sxs-lookup"><span data-stu-id="cb62b-103">Variable and Argument Tracking</span></span>

<span data-ttu-id="cb62b-104">При отслеживании выполнения рабочего процесса часто бывает полезно извлекать данные.</span><span class="sxs-lookup"><span data-stu-id="cb62b-104">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="cb62b-105">Это обеспечивает дополнительный контекст при доступе к последующему выполнению записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="cb62b-105">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="cb62b-106">В [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] можно извлекать любую видимую переменную или аргумент, находящиеся в рамках области любого действия в рабочем процессе, при помощи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="cb62b-106">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="cb62b-107">Профили отслеживания упрощают извлечение данных.</span><span class="sxs-lookup"><span data-stu-id="cb62b-107">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="cb62b-108">Переменные и аргументы</span><span class="sxs-lookup"><span data-stu-id="cb62b-108">Variables and Arguments</span></span>  

 <span data-ttu-id="cb62b-109">Переменные и аргументы извлекаются при создании действием записи ActivityStateRecord.</span><span class="sxs-lookup"><span data-stu-id="cb62b-109">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="cb62b-110">Переменная доступна для извлечения, только если она записана в области этого действия.</span><span class="sxs-lookup"><span data-stu-id="cb62b-110">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="cb62b-111">Переменная, извлекаемая в действии, задается следующим образом.</span><span class="sxs-lookup"><span data-stu-id="cb62b-111">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
- <span data-ttu-id="cb62b-112">Если переменная задана именем переменной, отслеживание будет искать переменную в текущем отслеживаемом действии и в родительских действиях.</span><span class="sxs-lookup"><span data-stu-id="cb62b-112">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="cb62b-113">Будет выполнен поиск переменной в области текущего действия и в родительской области.</span><span class="sxs-lookup"><span data-stu-id="cb62b-113">The variable is searched in current activity scope and in parent scope.</span></span>  
  
- <span data-ttu-id="cb62b-114">Если переменные для извлечения указываются с помощью имени = " \* ", то извлекаются все переменные в текущем отслеживаемом действии.</span><span class="sxs-lookup"><span data-stu-id="cb62b-114">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="cb62b-115">В этом случае переменные, находящиеся в области, но не определенные в родительских действиях, извлечены не будут.</span><span class="sxs-lookup"><span data-stu-id="cb62b-115">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="cb62b-116">При извлечении аргументов извлекаемые аргументы зависят от состояния действия.</span><span class="sxs-lookup"><span data-stu-id="cb62b-116">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="cb62b-117">Если состояние действия - «Выполнение», тогда только `InArguments` будут доступны для извлечения.</span><span class="sxs-lookup"><span data-stu-id="cb62b-117">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="cb62b-118">Для любого другого состояния действия («Закрыто», «Ошибка», «Отменено») оба аргумента, InArguments и OutArguments, доступны для извлечения.</span><span class="sxs-lookup"><span data-stu-id="cb62b-118">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="cb62b-119">В следующем примере показан запрос состояния действия, который извлекает переменные и аргументы при создании записи отслеживания действия `Closed`.</span><span class="sxs-lookup"><span data-stu-id="cb62b-119">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="cb62b-120">Переменные и аргументы могут быть извлечены при помощи <xref:System.Activities.Tracking.ActivityStateRecord>, поэтому подписка на них выполняется в рамках профиля отслеживания с использованием запроса <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="cb62b-120">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="cb62b-121">Защита информации, сохраняемой в переменных и аргументах</span><span class="sxs-lookup"><span data-stu-id="cb62b-121">Protecting Information Stored Within Variables and Arguments</span></span>  

 <span data-ttu-id="cb62b-122">Отслеживаемая переменная или аргумент по умолчанию становятся видимыми в среде выполнения WF.</span><span class="sxs-lookup"><span data-stu-id="cb62b-122">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="cb62b-123">Разработчик рабочих процессов может установить защиту против доступа, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="cb62b-123">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1. <span data-ttu-id="cb62b-124">Зашифруйте значение переменной.</span><span class="sxs-lookup"><span data-stu-id="cb62b-124">Encrypt the value of a variable.</span></span>  
  
2. <span data-ttu-id="cb62b-125">Контролируйте создание профиля отслеживания для предотвращения извлечения переменной или аргумента.</span><span class="sxs-lookup"><span data-stu-id="cb62b-125">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3. <span data-ttu-id="cb62b-126">Для пользовательских участников отслеживания убедитесь, что код WF не раскрывает конфиденциальные сведения, сохраняемую в переменных и аргументах.</span><span class="sxs-lookup"><span data-stu-id="cb62b-126">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb62b-127">См. также</span><span class="sxs-lookup"><span data-stu-id="cb62b-127">See also</span></span>

- <span data-ttu-id="cb62b-128">[Мониторинг Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cb62b-128">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="cb62b-129">[Мониторинг приложений с помощью App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cb62b-129">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
