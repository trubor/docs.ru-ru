---
title: Динамическое обновление
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: cb4b63a67aa6e9033b227198e2ecc2b1b80db927
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190160"
---
# <a name="dynamic-update"></a><span data-ttu-id="455de-102">Динамическое обновление</span><span class="sxs-lookup"><span data-stu-id="455de-102">Dynamic Update</span></span>

<span data-ttu-id="455de-103">Динамическое обновление предоставляет разработчикам приложений рабочих процессов механизм обновления определения рабочего процесса для сохраненного экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="455de-104">Это позволяет реализовать исправление ошибки, внедрить новые требования и внести непредвиденные изменения.</span><span class="sxs-lookup"><span data-stu-id="455de-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="455de-105">В этом разделе приводятся общие сведения о функции динамического обновления, представленной в .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="455de-105">This topic provides an overview of the dynamic update functionality introduced in .NET Framework 4.5.</span></span>

## <a name="dynamic-update"></a><span data-ttu-id="455de-106">Динамическое обновление</span><span class="sxs-lookup"><span data-stu-id="455de-106">Dynamic Update</span></span>

<span data-ttu-id="455de-107">Для применения динамического обновления к сохраненному экземпляру рабочего процесса создается схема <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, которая содержит инструкции времени выполнения, описывающие, как следует изменить сохраненный экземпляр рабочего процесса, чтобы он отражал требуемые изменения.</span><span class="sxs-lookup"><span data-stu-id="455de-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="455de-108">После создания схема обновления применяется к выбранным экземплярам рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="455de-109">Сразу после применения динамического обновления экземпляр рабочего процесса может быть возобновлен уже с новыми, обновленными определениями рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="455de-110">Создание и применение схемы обновления происходит в четыре этапа.</span><span class="sxs-lookup"><span data-stu-id="455de-110">There are four steps required to create and apply an update map.</span></span>

1. [<span data-ttu-id="455de-111">Подготовка определения рабочего процесса к динамическому обновлению.</span><span class="sxs-lookup"><span data-stu-id="455de-111">Prepare the workflow definition for dynamic update</span></span>](dynamic-update.md#Prepare)

2. [<span data-ttu-id="455de-112">Обновление определения рабочего процесса в соответствии с требуемыми изменениями</span><span class="sxs-lookup"><span data-stu-id="455de-112">Update the workflow definition to reflect the desired changes</span></span>](dynamic-update.md#Update)

3. [<span data-ttu-id="455de-113">Создание схемы обновления</span><span class="sxs-lookup"><span data-stu-id="455de-113">Create the update map</span></span>](dynamic-update.md#Create)

4. [<span data-ttu-id="455de-114">Применение схемы обновления к выбранным экземплярам рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-114">Apply the update map to the desired persisted workflow instances</span></span>](dynamic-update.md#Apply)

> [!NOTE]
> <span data-ttu-id="455de-115">Обратите внимание, что шаги 1–3, которые охватывают создание схемы обновления, могут быть выполнены независимо от применения обновления.</span><span class="sxs-lookup"><span data-stu-id="455de-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="455de-116">Распространенный сценарий, в котором разработчик рабочего процесса создаст схему обновления в автономном режиме, а затем администратор применит обновление позже.</span><span class="sxs-lookup"><span data-stu-id="455de-116">A common scenario that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>

<span data-ttu-id="455de-117">В этом разделе приведены общие сведения о процессе динамического обновления с добавлением нового действия, которое добавляется к сохраненному экземпляру скомпилированного рабочего процесса языка XAML.</span><span class="sxs-lookup"><span data-stu-id="455de-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>

### <a name="prepare-the-workflow-definition-for-dynamic-update"></a><a name="Prepare"></a> <span data-ttu-id="455de-118">Подготовка определения рабочего процесса для динамического обновления</span><span class="sxs-lookup"><span data-stu-id="455de-118">Prepare the workflow definition for dynamic update</span></span>

<span data-ttu-id="455de-119">Первый шаг в процессе динамического обновления - подготовка требуемого определения рабочего процесса к обновлению.</span><span class="sxs-lookup"><span data-stu-id="455de-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="455de-120">Это можно сделать, вызвав метод <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> и передав ему определение изменяемого рабочего процесса .</span><span class="sxs-lookup"><span data-stu-id="455de-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="455de-121">Этот метод проверяет, а затем обходит дерево рабочего процесса для определения всех объектов, таких как открытые переменные и действия, которые необходимо отметить тегами для сравнения в дальнейшем с объектами в измененном определении рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="455de-122">По завершении этой операции дерево рабочего процесса клонируется и присоединяется к исходному определению рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="455de-123">При создании схемы обновленная версия определения рабочего процесса сравнивается с исходным определением рабочего процесса и схема создается на основе различий между ними.</span><span class="sxs-lookup"><span data-stu-id="455de-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>

<span data-ttu-id="455de-124">Чтобы подготовить рабочий процесс языка XAML для динамического обновления, его можно загрузить в <xref:System.Activities.ActivityBuilder>, а затем передать <xref:System.Activities.ActivityBuilder> в <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="455de-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="455de-125">Дополнительные сведения о работе с сериализованными рабочими процессами и <xref:System.Activities.ActivityBuilder> см. [в разделе Сериализация рабочих процессов и действий в XAML и обратно](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="455de-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

<span data-ttu-id="455de-126">В следующем примере определение `MortgageWorkflow` (состоящее из <xref:System.Activities.Statements.Sequence> с несколькими дочерними действиями) загружается в <xref:System.Activities.ActivityBuilder>, а затем подготавливается для динамического обновления.</span><span class="sxs-lookup"><span data-stu-id="455de-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="455de-127">После возврата из метода <xref:System.Activities.ActivityBuilder> содержит исходное определение рабочего процесса и копию.</span><span class="sxs-lookup"><span data-stu-id="455de-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

### <a name="update-the-workflow-definition-to-reflect-the-desired-changes"></a><a name="Update"></a> <span data-ttu-id="455de-128">Обновление определения рабочего процесса в соответствии с требуемыми изменениями</span><span class="sxs-lookup"><span data-stu-id="455de-128">Update the workflow definition to reflect the desired changes</span></span>

<span data-ttu-id="455de-129">После того как определение рабочего процесса будет подготовлено к изменениям, можно внести необходимые желаемые изменения.</span><span class="sxs-lookup"><span data-stu-id="455de-129">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="455de-130">Вы можете добавлять или удалять действия, добавлять, изменять или удалять открытые переменные, добавлять или удалять аргументы и вносить изменения в сигнатуру делегатов действий.</span><span class="sxs-lookup"><span data-stu-id="455de-130">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="455de-131">Нельзя удалить выполняемое действие или изменить сигнатуру выполняемого делегата.</span><span class="sxs-lookup"><span data-stu-id="455de-131">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="455de-132">Эти изменения можно внести из кода или в повторно размещенном конструкторе рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="455de-132">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="455de-133">В следующем примере настраиваемое действие `VerifyAppraisal` добавляется в последовательность, представляющую основу `MortgageWorkflow` из предыдущего примера.</span><span class="sxs-lookup"><span data-stu-id="455de-133">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>

```csharp
// Make desired changes to the definition. In this example, we are
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.
VerifyAppraisal va = new VerifyAppraisal
{
    Result = new VisualBasicReference<bool>("LoanCriteria")
};

// Get the Sequence that makes up the body of the workflow.
Sequence s = ab.Implementation as Sequence;

// Insert the new activity into the Sequence.
s.Activities.Insert(2, va);
```

### <a name="create-the-update-map"></a><a name="Create"></a> <span data-ttu-id="455de-134">Создание схемы обновления</span><span class="sxs-lookup"><span data-stu-id="455de-134">Create the update map</span></span>

<span data-ttu-id="455de-135">После изменения подготовленного к обновлению определения рабочего процесса можно создать схему обновления.</span><span class="sxs-lookup"><span data-stu-id="455de-135">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="455de-136">Для создания схемы динамического обновления вызывается метод <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="455de-136">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="455de-137">Этот метод возвращает <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> - объект, содержащий сведения, необходимые среде выполнения для изменения сохраненного экземпляра рабочего процесса, чтобы тот можно было загрузить и возобновить вместе с новым определением рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-137">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="455de-138">В следующем примере создается динамическая схема для измененного определения `MortgageWorkflow` из предыдущего примера.</span><span class="sxs-lookup"><span data-stu-id="455de-138">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

<span data-ttu-id="455de-139">Эту схему обновления можно сразу же использовать для изменения сохраненных экземпляров рабочего процесса или сохранить ее и применить обновления позже.</span><span class="sxs-lookup"><span data-stu-id="455de-139">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="455de-140">Один из способов сохранить схему обновления - это сериализовать ее в файл, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="455de-140">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<span data-ttu-id="455de-141">Когда <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> возвращает управление, скопированное определение рабочего процесса и другая информация о динамическом обновлении, добавленная при вызове <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>, удаляются, а измененное определение рабочего процесса готово к сохранению, после чего его можно будет использовать при восстановлении обновленных экземпляров рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-141">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="455de-142">В следующем примере определение измененного рабочего процесса сохраняется в `MortgageWorkflow_v1.1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="455de-142">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v1.1.xaml`.</span></span>

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="apply-the-update-map-to-the-desired-persisted-workflow-instances"></a><a name="Apply"></a> <span data-ttu-id="455de-143">Применить карту обновления к желаемым сохраненным экземплярам рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="455de-143">Apply the update map to the desired persisted workflow instances</span></span>

<span data-ttu-id="455de-144">Применение схемы обновления можно выполнить в любое время после ее создания.</span><span class="sxs-lookup"><span data-stu-id="455de-144">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="455de-145">Это можно сделать немедленно с помощью экземпляра <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, который был возвращен методом <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, или позднее с помощью сохраненной копии схемы обновления.</span><span class="sxs-lookup"><span data-stu-id="455de-145">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="455de-146">Для обновления экземпляра рабочего процесса загрузите его в объект <xref:System.Activities.WorkflowApplicationInstance> с помощью метода <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="455de-146">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="455de-147">Далее создайте <xref:System.Activities.WorkflowApplication> с помощью обновленного определения рабочего процесса и нужного метода <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="455de-147">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="455de-148">Этот идентификатор <xref:System.Activities.WorkflowIdentity> может отличаться от того, что был использован для сохранения исходного рабочего процесса, и, как правило, это делается для отражения того, что сохраненный экземпляр был изменен.</span><span class="sxs-lookup"><span data-stu-id="455de-148">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="455de-149">Сразу после создания <xref:System.Activities.WorkflowApplication> загружается с помощью перегрузки <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType>, принимающей <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, затем выгружается посредством вызова <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="455de-149">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="455de-150">При этом будет произведено динамическое обновление и обновленный экземпляр рабочего процесса будет сохранен.</span><span class="sxs-lookup"><span data-stu-id="455de-150">This applies the dynamic update and persists the updated workflow instance.</span></span>

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
{
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
    object updateMap = serializer.ReadObject(fs);
    if (updateMap == null)
    {
        throw new ApplicationException("DynamicUpdateMap is null.");
    }

    map = (DynamicUpdateMap)updateMap;
}

// Retrieve a list of workflow instance ids that corresponds to the
// workflow instances to update. This step is the responsibility of
// the application developer.
List<Guid> ids = GetPersistedWorkflowIds();
foreach (Guid id in ids)
{
    // Get a proxy to the persisted workflow instance.
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);

    // If desired, you can inspect the WorkflowIdentity of the instance
    // using the DefinitionIdentity property to determine whether to apply
    // the update.
    Console.WriteLine(instance.DefinitionIdentity);

    // Create a workflow application. You must specify the updated workflow definition, and
    // you may provide an updated WorkflowIdentity if desired to reflect the update.
    WorkflowIdentity identity = new WorkflowIdentity
    {
        Name = "MortgageWorkflow v1.1",
        Version = new Version(1, 1, 0, 0)
    };

    // Load the persisted workflow instance using the updated workflow definition
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class
    // contains the updated definition.
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

    // Apply the dynamic update on the loaded instance.
    wfApp.Load(instance, map);

    // Unload the updated instance.
    wfApp.Unload();
}
```

### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="455de-151">Возобновление работы обновленного экземпляра рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="455de-151">Resuming an Updated Workflow Instance</span></span>

<span data-ttu-id="455de-152">Сразу после применения динамического обновления можно возобновлять работу экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-152">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="455de-153">Обратите внимание, что следует использовать новое обновленное определение и <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="455de-153">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>

> [!NOTE]
> <span data-ttu-id="455de-154">Дополнительные сведения о работе с <xref:System.Activities.WorkflowApplication> и см <xref:System.Activities.WorkflowIdentity> . в разделе [Использование WorkflowIdentity и управление версиями](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="455de-154">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

<span data-ttu-id="455de-155">В следующем примере рабочий процесс `MortgageWorkflow_v1.1.xaml` из предыдущего примера был скомпилирован, и он загружается и возобновляется с помощью обновленного определения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="455de-155">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>

```csharp
// Load the persisted workflow instance using the updated workflow definition
// and updated WorkflowIdentity.
WorkflowIdentity identity = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1.1",
    Version = new Version(1, 1, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure persistence and desired workflow event handlers.
// (Omitted for brevity.)
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(InstanceId);

// Resume the workflow.
// wfApp.ResumeBookmark(...);
```
