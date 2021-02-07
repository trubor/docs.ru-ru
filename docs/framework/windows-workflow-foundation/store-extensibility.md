---
description: Дополнительные сведения о сохранении расширяемости хранилища
title: Расширяемость хранилища
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: f04c466224aacd1c8f755e7aa60b18846d0c7180
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755230"
---
# <a name="store-extensibility"></a><span data-ttu-id="fc90e-103">Расширяемость хранилища</span><span class="sxs-lookup"><span data-stu-id="fc90e-103">Store Extensibility</span></span>

<span data-ttu-id="fc90e-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> позволяет пользователям повышать уровень относящихся к приложению пользовательских свойств, которые могут использоваться для создания запросов к экземплярам в базе данных сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="fc90e-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="fc90e-105">Благодаря действию по повышению уровня свойства значение становится доступным в специальном представлении в базе данных.</span><span class="sxs-lookup"><span data-stu-id="fc90e-105">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="fc90e-106">Свойства с повышенным уровнем (т.е. свойства, которые могут использоваться в пользовательских запросах), могут относиться к простым типам, например к Int64, Guid, String, DateTime или к сериализованному двоичному типу (byte[]).</span><span class="sxs-lookup"><span data-stu-id="fc90e-106">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>

<span data-ttu-id="fc90e-107">Класс <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> содержит метод <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A>, который может использоваться для повышения уровня свойства, чтобы его можно было использовать в запросах.</span><span class="sxs-lookup"><span data-stu-id="fc90e-107">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="fc90e-108">Ниже приведен подробный пошаговый пример расширения хранилища.</span><span class="sxs-lookup"><span data-stu-id="fc90e-108">The following example is an end-to-end example of store extensibility.</span></span>

1. <span data-ttu-id="fc90e-109">В данном образце сценария приложение обработки документов содержит рабочие процессы, в каждом из которых для обработки документов применяются пользовательские действия.</span><span class="sxs-lookup"><span data-stu-id="fc90e-109">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="fc90e-110">Эти рабочие процессы содержат набор переменных состояния, которые необходимо сделать доступными для конечных пользователей.</span><span class="sxs-lookup"><span data-stu-id="fc90e-110">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="fc90e-111">Для этого приложение обработки документов предоставляет расширение экземпляра типа <xref:System.Activities.Persistence.PersistenceParticipant>, используемое действиями для предоставления переменных состояния.</span><span class="sxs-lookup"><span data-stu-id="fc90e-111">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. <span data-ttu-id="fc90e-112">Затем к узлу добавляется новое расширение.</span><span class="sxs-lookup"><span data-stu-id="fc90e-112">The new extension is then added to the host.</span></span>

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     <span data-ttu-id="fc90e-113">Дополнительные сведения о добавлении настраиваемого участника сохраняемости см. в образце [участников сохраняемости](persistence-participants.md) .</span><span class="sxs-lookup"><span data-stu-id="fc90e-113">For more details about adding a custom persistence participant, see the [Persistence Participants](persistence-participants.md) sample.</span></span>

3. <span data-ttu-id="fc90e-114">Пользовательские действия в приложении DP заполняют различные поля состояния в методе **EXECUTE** .</span><span class="sxs-lookup"><span data-stu-id="fc90e-114">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>

    ```csharp
    public override void Execute(CodeActivityContext context)
    {
        // ...
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();
        // ...
    }
    ```

4. <span data-ttu-id="fc90e-115">Когда экземпляр рабочего процесса достигает точки сохраняемости, метод **CollectValues** участника сохраняемости **документстатусекстенсион** сохраняет эти свойства в коллекции данных сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="fc90e-115">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");

        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)
        {
            readWriteValues = new Dictionary<XName, object>();
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);

            writeOnlyValues = null;
        }
        // ...
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="fc90e-116">Все эти свойства передаются в **SqlWorkflowInstanceStore** средой сохраняемости с помощью коллекции **савеворкфловкомманд. инстанцедата** .</span><span class="sxs-lookup"><span data-stu-id="fc90e-116">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>

5. <span data-ttu-id="fc90e-117">Приложение DP инициализирует хранилище экземпляров рабочих процессов SQL и вызывает метод **Promote** для продвижения этих данных.</span><span class="sxs-lookup"><span data-stu-id="fc90e-117">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);

    List<XName> variantProperties = new List<XName>()
    {
        xNS.GetName("UserName"),
        xNS.GetName("ApprovalStatus"),
        xNS.GetName("DocumentId"),
        xNS.GetName("LastModifiedTime")
    };

    store.Promote("DocumentStatus", variantProperties, null);
    ```

    <span data-ttu-id="fc90e-118">На основе этих сведений об акциях **SqlWorkflowInstanceStore** размещает свойства данных в столбцах представления [инстанцепромотедпропертиес](#InstancePromotedProperties) .</span><span class="sxs-lookup"><span data-stu-id="fc90e-118">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>

6. <span data-ttu-id="fc90e-119">Чтобы создать запрос к подмножеству данных из таблицы повышения уровня, приложение обработки данных добавляет пользовательское представление к представлению повышения уровня.</span><span class="sxs-lookup"><span data-stu-id="fc90e-119">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>

    ```sql
    create view [dbo].[DocumentStatus] with schemabinding
    as
        select  P.[InstanceId] as [InstanceId],
            P.Value1 as [UserName],
            P.Value2 as [ApprovalStatus],
            P.Value3 as [DocumentId],
            P.Value4 as [LastUpdatedTime]
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P
    where P.PromotionName = N'DocumentStatus'
    go
    ```

## <a name="systemactivitiesdurableinstancinginstancepromotedproperties-view"></a><a name="InstancePromotedProperties"></a> <span data-ttu-id="fc90e-120">[System. Activity. DurableInstancing. Инстанцепромотедпропертиес] представление</span><span class="sxs-lookup"><span data-stu-id="fc90e-120">[System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>

|<span data-ttu-id="fc90e-121">Имя столбца</span><span class="sxs-lookup"><span data-stu-id="fc90e-121">Column Name</span></span>|<span data-ttu-id="fc90e-122">Тип столбца</span><span class="sxs-lookup"><span data-stu-id="fc90e-122">Column Type</span></span>|<span data-ttu-id="fc90e-123">Описание</span><span class="sxs-lookup"><span data-stu-id="fc90e-123">Description</span></span>|
|-----------------|-----------------|-----------------|
|<span data-ttu-id="fc90e-124">InstanceId</span><span class="sxs-lookup"><span data-stu-id="fc90e-124">InstanceId</span></span>|<span data-ttu-id="fc90e-125">Идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="fc90e-125">GUID</span></span>|<span data-ttu-id="fc90e-126">Экземпляр рабочего процесса, которому принадлежит это повышение уровня.</span><span class="sxs-lookup"><span data-stu-id="fc90e-126">The workflow instance that this promotion belongs to.</span></span>|
|<span data-ttu-id="fc90e-127">PromotionName</span><span class="sxs-lookup"><span data-stu-id="fc90e-127">PromotionName</span></span>|<span data-ttu-id="fc90e-128">nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="fc90e-128">nvarchar(400)</span></span>|<span data-ttu-id="fc90e-129">Имя самого продвижения.</span><span class="sxs-lookup"><span data-stu-id="fc90e-129">The name of the promotion itself.</span></span>|
|<span data-ttu-id="fc90e-130">Value1, Value2, Value3,..,Value32</span><span class="sxs-lookup"><span data-stu-id="fc90e-130">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="fc90e-131">sql_variant</span><span class="sxs-lookup"><span data-stu-id="fc90e-131">sql_variant</span></span>|<span data-ttu-id="fc90e-132">Значение самого свойства, уровень которого повышен.</span><span class="sxs-lookup"><span data-stu-id="fc90e-132">The value of the promoted property itself.</span></span> <span data-ttu-id="fc90e-133">Большинство примитивных типов данных SQL, за исключением больших двоичных объектов BLOB и строк длиной более 8000 байт, помещается в sql_variant.</span><span class="sxs-lookup"><span data-stu-id="fc90e-133">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|
|<span data-ttu-id="fc90e-134">Value33, Value34, Value35, …, Value64</span><span class="sxs-lookup"><span data-stu-id="fc90e-134">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="fc90e-135">varbinary(max)</span><span class="sxs-lookup"><span data-stu-id="fc90e-135">varbinary(max)</span></span>|<span data-ttu-id="fc90e-136">Значение свойств повышаемого уровня, явно объявленных, как varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="fc90e-136">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
