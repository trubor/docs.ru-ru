---
title: Параллельное управление версиями в WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 1505582e5ac7303a2df20539fdcf67435746b9d3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190498"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="c753d-102">Параллельное управление версиями в WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c753d-102">Side by Side Versioning in WorkflowServiceHost</span></span>

<span data-ttu-id="c753d-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost>Параллельное управление версиями, представленное в .NET Framework 4,5, предоставляет возможность размещения нескольких версий службы рабочего процесса на одной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="c753d-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="c753d-104">Предоставляемая функциональность параллельной работы позволяет настроить службу Workflow Service таким образом, чтобы новые экземпляры службы Workflow Service создавались с использованием нового определения рабочего процесса, а запущенные экземпляры завершались с использованием существующего определения.</span><span class="sxs-lookup"><span data-stu-id="c753d-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="c753d-105">Данный раздел содержит общие сведения о параллельном выполнении служб Workflow Services с использованием <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c753d-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="c753d-106">Размещение нескольких версий в службе Workflow Service</span><span class="sxs-lookup"><span data-stu-id="c753d-106">Hosting Multiple Versions in a Workflow Service</span></span>  

 <span data-ttu-id="c753d-107"><xref:System.ServiceModel.Activities.WorkflowServiceHost> содержит два свойства, которые можно настроить для разрешения параллельного выполнения нескольких версий рабочего процесса: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> и <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="c753d-107"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="c753d-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> содержит поддерживаемые версии службы Workflow Service, а <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> используется для уникальной идентификации каждой службы Workflow Service.</span><span class="sxs-lookup"><span data-stu-id="c753d-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="c753d-109">Для этого нужно связать <xref:System.Activities.WorkflowIdentity> со службой Workflow Service.</span><span class="sxs-lookup"><span data-stu-id="c753d-109">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="c753d-110">В <xref:System.Activities.WorkflowIdentity> содержится три элемента информации для идентификации.</span><span class="sxs-lookup"><span data-stu-id="c753d-110">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="c753d-111"><xref:System.Activities.WorkflowIdentity.Name%2A> и <xref:System.Activities.WorkflowIdentity.Version%2A> содержат имя и <xref:System.Version> и являются обязательными, а <xref:System.Activities.WorkflowIdentity.Package%2A> является необязательным и может использоваться для указания дополнительной строки с информацией (например, именем сборки или другими полезными сведениями).</span><span class="sxs-lookup"><span data-stu-id="c753d-111"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="c753d-112">Каждая служба Workflow Service, содержащаяся в коллекции <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>, должна иметь уникальный <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="c753d-112">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="c753d-113"><xref:System.Activities.WorkflowIdentity> уникален, если какое-либо из его трех свойств отличается от другого <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="c753d-113">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="c753d-114">Является допустимым `null` <xref:System.Activities.WorkflowIdentity> значением для <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , но только у одной предыдущей версии службы рабочего процесса может быть `null` <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="c753d-114">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c753d-115">Экземпляр <xref:System.Activities.WorkflowIdentity> не должен содержать персональные данные (PII).</span><span class="sxs-lookup"><span data-stu-id="c753d-115">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="c753d-116"><xref:System.Activities.WorkflowIdentity> состоит из 3 частей: <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) и <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="c753d-116"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="c753d-117">Сведения об объекте <xref:System.Activities.WorkflowIdentity>, используемом для создания экземпляра, передаются средой выполнения всем настроенным службам отслеживания на различных этапах жизненного цикла действия.</span><span class="sxs-lookup"><span data-stu-id="c753d-117">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="c753d-118">Отслеживание WF не имеет механизмов, позволяющих скрывать персональные данные (конфиденциальные пользовательские данные).</span><span class="sxs-lookup"><span data-stu-id="c753d-118">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="c753d-119">Поэтому экземпляр <xref:System.Activities.WorkflowIdentity> не должен содержать никаких персональных данных, так как они будут передаваться средой выполнения в записях отслеживания и могут отображаться любому пользователю с доступом к записям отслеживания.</span><span class="sxs-lookup"><span data-stu-id="c753d-119">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="c753d-120">Правила размещения нескольких версий службы Workflow Service</span><span class="sxs-lookup"><span data-stu-id="c753d-120">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  

 <span data-ttu-id="c753d-121">При добавлении пользователем дополнительной версии на <xref:System.ServiceModel.Activities.WorkflowServiceHost> существует несколько условий, которые необходимо выполнить для размещения службы Workflow Service с одним и тем же описанием и набором конечных точек.</span><span class="sxs-lookup"><span data-stu-id="c753d-121">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="c753d-122">Если одна из дополнительных версий не выполняет эти условия, <xref:System.ServiceModel.Activities.WorkflowServiceHost> возвращает исключение при вызове `Open`.</span><span class="sxs-lookup"><span data-stu-id="c753d-122">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="c753d-123">Каждое определение рабочего процесса, предоставленное узлу в качестве дополнительной версии, должно выполнять следующие требования (где основной версией является определение службы Workflow Service, предоставленное конструктору узла).</span><span class="sxs-lookup"><span data-stu-id="c753d-123">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="c753d-124">Дополнительная версия рабочего процесса должна:</span><span class="sxs-lookup"><span data-stu-id="c753d-124">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="c753d-125">иметь одинаковый <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> с основной версией службы Workflow Service.</span><span class="sxs-lookup"><span data-stu-id="c753d-125">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="c753d-126">Не должна содержать действий <xref:System.ServiceModel.Activities.Receive> или <xref:System.ServiceModel.Activities.SendReply> в своем <xref:System.ServiceModel.Activities.WorkflowService.Body%2A>, которых нет в основной версии, и они должны соответствовать контракту операции.</span><span class="sxs-lookup"><span data-stu-id="c753d-126">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="c753d-127">Иметь уникальный <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="c753d-127">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="c753d-128">Только одно определение рабочего процесса может содержать `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="c753d-128">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="c753d-129">Некоторые изменения разрешены.</span><span class="sxs-lookup"><span data-stu-id="c753d-129">Some changes are permitted.</span></span> <span data-ttu-id="c753d-130">Следующие элементы могут различаться между версиями:</span><span class="sxs-lookup"><span data-stu-id="c753d-130">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="c753d-131"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> может иметь Name и Package, отличные от основной версии.</span><span class="sxs-lookup"><span data-stu-id="c753d-131">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="c753d-132">Значение <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> может отличаться от основной версии.</span><span class="sxs-lookup"><span data-stu-id="c753d-132">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="c753d-133"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> может отличаться от основной версии.</span><span class="sxs-lookup"><span data-stu-id="c753d-133">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="c753d-134"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> может отличаться от основной версии.</span><span class="sxs-lookup"><span data-stu-id="c753d-134">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="c753d-135">Настройка DefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="c753d-135">Configuring the DefinitionIdentity</span></span>  

 <span data-ttu-id="c753d-136">При создании службы рабочего процесса с помощью конструктора рабочих процессов параметр <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> задается с помощью окна **свойства** .</span><span class="sxs-lookup"><span data-stu-id="c753d-136">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="c753d-137">Щелкните за пределами корневого действия службы в конструкторе, чтобы выбрать службу рабочего процесса, и выберите в меню **вид** пункт **окно свойств** .</span><span class="sxs-lookup"><span data-stu-id="c753d-137">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="c753d-138">Выберите **WorkflowIdentity** из раскрывающегося списка рядом со свойством **дефинитионидентити** , а затем разверните и укажите нужные <xref:System.Activities.WorkflowIdentity> Свойства.</span><span class="sxs-lookup"><span data-stu-id="c753d-138">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="c753d-139">В следующем примере <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> выполняется настройка с параметром <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` и <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="c753d-139">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="c753d-140"><xref:System.Activities.WorkflowIdentity.Package%2A> является необязательным и в данном примере равняется `null`.</span><span class="sxs-lookup"><span data-stu-id="c753d-140"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![Снимок экрана, на котором показано свойство Дефинитионидентити.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="c753d-142">Если служба Workflow Service размещается резидентно, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> настраивается при построении службы Workflow Service.</span><span class="sxs-lookup"><span data-stu-id="c753d-142">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="c753d-143">В следующем примере для заданы те <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> же значения, что и в предыдущем примере, с и с <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="c753d-143">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 <span data-ttu-id="c753d-144"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>Не требуется, хотя только одна версия службы рабочего процесса может иметь **значение NULL** <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> .</span><span class="sxs-lookup"><span data-stu-id="c753d-144">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c753d-145">Это полезно, если служба изначально была развернута без настроенного <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, а после этого создается обновленная версия.</span><span class="sxs-lookup"><span data-stu-id="c753d-145">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="c753d-146">Добавление новой версии к службе Workflow Service, размещенной на веб-сервере</span><span class="sxs-lookup"><span data-stu-id="c753d-146">Adding a New Version to a Web-hosted Workflow Service</span></span>  

 <span data-ttu-id="c753d-147">Первым шагом в настройке новой версии службы Workflow Service в службе, размещенной на веб-сервере, является создание новой папки в папке `App_Code`, которая имеет то же имя, что и файл службы.</span><span class="sxs-lookup"><span data-stu-id="c753d-147">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="c753d-148">Если файл `xamlx` службы имеет имя `MortgageWorkflow.xamlx`, необходимо присвоить папке имя `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="c753d-148">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="c753d-149">Поместите копию файла `xamlx` изначальной службы в эту папку и присвойте ему другое имя, например `MortgageWorkflowV1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="c753d-149">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="c753d-150">Внесите желаемые изменения в основную службу, обновите ее <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, затем разверните службу.</span><span class="sxs-lookup"><span data-stu-id="c753d-150">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="c753d-151">В следующем примере <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> был обновлен с помощью <xref:System.Activities.WorkflowIdentity.Name%2A>, равного `MortgageWorkflow`, и с <xref:System.Activities.WorkflowIdentity.Version%2A>, равной `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="c753d-151">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![Снимок экрана, на котором показано Дефинитионидентити WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="c753d-153">При повторном запуске службы предыдущая версия автоматически добавится в коллекцию <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>, так как она находится в указанной подпапке `App_Code`.</span><span class="sxs-lookup"><span data-stu-id="c753d-153">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="c753d-154">Обратите внимание, что если в основной версии службы рабочего процесса есть `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> предыдущие версии, они не будут добавлены.</span><span class="sxs-lookup"><span data-stu-id="c753d-154">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="c753d-155">В одной версии `null` может быть равен <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, но, если имеется несколько таких версий, основная версия не должна быть с `null`, равным <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, в противном случае предыдущие версии не будут добавлены в коллекцию <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>.</span><span class="sxs-lookup"><span data-stu-id="c753d-155">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="c753d-156">Добавление новой версии к службе Workflow Service, размещенной резидентно</span><span class="sxs-lookup"><span data-stu-id="c753d-156">Adding a New Version to a Self-hosted Workflow Service</span></span>  

 <span data-ttu-id="c753d-157">При добавлении новой версии в резидентную службу Workflow Service <xref:System.ServiceModel.Activities.WorkflowServiceHost> настраивается с основной версией службы Workflow Service, а предыдущие версии должны быть явным образом добавлены в коллекцию <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>.</span><span class="sxs-lookup"><span data-stu-id="c753d-157">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="c753d-158">В следующем примере <xref:System.ServiceModel.Activities.WorkflowServiceHost> настраивается с основной службой Workflow Service, которая использует определение рабочего процесса `MortgageWorkflowV2`, и в коллекцию `MortgageWorkflowV1` добавляется служба Workflow Service, настроенная с определением рабочего процесса <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>.</span><span class="sxs-lookup"><span data-stu-id="c753d-158">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="c753d-159">Каждая служба Workflow Service настраивается с уникальным <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, отражающим версию определения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="c753d-159">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```
