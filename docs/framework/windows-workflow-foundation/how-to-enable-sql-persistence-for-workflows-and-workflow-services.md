---
description: Дополнительные сведения см. в статье Включение сохраняемости SQL для рабочих процессов и служб рабочих процессов.
title: Практическое руководство. Включение сохраняемости для рабочих процессов и их служб в SQL
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 5c124c4ec1d75d4b3b24468c04a4fb82236aa29a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777727"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="49fb6-103">Практическое руководство. Включение сохраняемости для рабочих процессов и их служб в SQL</span><span class="sxs-lookup"><span data-stu-id="49fb6-103">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="49fb6-104">В данном разделе описано, как настроить возможность хранилища экземпляров рабочих процессов SQL для включения сохраняемости рабочих процессов и служб рабочих процессов программно и с помощью файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="49fb6-104">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="49fb6-105">Windows Server App Fabric упрощает процесс настройки сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="49fb6-105">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="49fb6-106">Дополнительные сведения см. в статье [Конфигурация сохраняемости в App Fabric](/previous-versions/appfabric/ee790848(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="49fb6-106">For more information, see [App Fabric Persistence Configuration](/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="49fb6-107">Перед использованием возможности хранилища экземпляров рабочих процессов SQL необходимо создать базу данных, которая используется возможностью для сохранения экземпляров рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="49fb6-107">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="49fb6-108">Программа установки [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] копирует файлы скрипта SQL, связанные с функцией хранилища экземпляров рабочих процессов SQL, в папку %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN.</span><span class="sxs-lookup"><span data-stu-id="49fb6-108">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="49fb6-109">Выполните эти файлы скрипта в базе данных SQL Server 2005 или SQL Server 2008, которая должна использоваться в хранилище экземпляров рабочих процессов SQL для сохранения экземпляров рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="49fb6-109">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="49fb6-110">Сначала запустите файл SqlWorkflowInstanceStoreSchema.sql, а затем файл SqlWorkflowInstanceStoreLogic.sql.</span><span class="sxs-lookup"><span data-stu-id="49fb6-110">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="49fb6-111">Чтобы очистить базу данных сохраняемости для получения вновь подготовленной базы данных, примените скрипты в каталоге %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN в следующем порядке.</span><span class="sxs-lookup"><span data-stu-id="49fb6-111">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="49fb6-112">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="49fb6-112">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="49fb6-113">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="49fb6-113">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49fb6-114">Если база данных сохраняемости не создана, то при попытке узла сохранить рабочие процессы хранилище экземпляров рабочих процессов SQL вырабатывает исключение, подобное следующему.</span><span class="sxs-lookup"><span data-stu-id="49fb6-114">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="49fb6-115">System.Data.SqlClient.SqlException: не удается найти хранимую процедуру System.Activities.DurableInstancing.CreateLockOwner</span><span class="sxs-lookup"><span data-stu-id="49fb6-115">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="49fb6-116">В следующих разделах описывается включение сохраняемости для рабочих процессов и служб рабочих процессов с использованием хранилища экземпляров рабочих процессов SQL.</span><span class="sxs-lookup"><span data-stu-id="49fb6-116">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="49fb6-117">Дополнительные сведения о свойствах хранилища экземпляров рабочих процессов SQL см. в разделе [Свойства хранилища экземпляров рабочих процессов SQL](properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="49fb6-117">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="49fb6-118">Включение сохраняемости для резидентных рабочих процессов, которые используют WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="49fb6-118">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="49fb6-119">Можно включить сохраняемость для резидентных рабочих процессов, которые программно используют <xref:System.Activities.WorkflowApplication> с помощью объектной модели <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.</span><span class="sxs-lookup"><span data-stu-id="49fb6-119">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="49fb6-120">Шаги, необходимые для выполнения этой задачи, содержатся в следующей процедуре.</span><span class="sxs-lookup"><span data-stu-id="49fb6-120">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="49fb6-121">Включение сохраняемости для резидентных рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="49fb6-121">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="49fb6-122">Добавьте ссылку на System.Activities.DurableInstancing.dll.</span><span class="sxs-lookup"><span data-stu-id="49fb6-122">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="49fb6-123">Добавьте следующий оператор в начало исходного файла после существующих инструкций using.</span><span class="sxs-lookup"><span data-stu-id="49fb6-123">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="49fb6-124">Создайте объект <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> и назначьте его свойству <xref:System.Activities.WorkflowApplication.InstanceStore%2A> приложения <xref:System.Activities.WorkflowApplication>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="49fb6-124">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="49fb6-125">В строке подключения могут указываться различные имена серверов в зависимости от выпуска SQL Server.</span><span class="sxs-lookup"><span data-stu-id="49fb6-125">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="49fb6-126">Вызовите метод <xref:System.Activities.WorkflowApplication.Persist%2A> объекта <xref:System.Activities.WorkflowApplication>, чтобы сохранить рабочий процесс, или метод <xref:System.Activities.WorkflowApplication.Unload%2A>, чтобы сохранить и выгрузить рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="49fb6-126">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="49fb6-127">Можно также обрабатывать событие <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>, вызванное объектом <xref:System.Activities.WorkflowApplication>, и возвращать соответствующий элемент (<xref:System.Activities.PersistableIdleAction.Persist> или <xref:System.Activities.PersistableIdleAction.Unload>) действия <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="49fb6-127">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="49fb6-128">Пошаговые инструкции см. в разделе [инструкции. Создание и выполнение длительно выполняемого рабочего процесса](how-to-create-and-run-a-long-running-workflow.md) [Начало работы учебнике](getting-started-tutorial.md) .</span><span class="sxs-lookup"><span data-stu-id="49fb6-128">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="49fb6-129">Включение сохраняемости для резидентных служб рабочих процессов, которые используют WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="49fb6-129">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="49fb6-130">Можно включить сохраняемость для резидентных служб рабочих процессов, которые программно используют <xref:System.ServiceModel.WorkflowServiceHost> с помощью класса <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> или класса <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="49fb6-130">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="49fb6-131">Использование класса SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="49fb6-131">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="49fb6-132">В следующем списке перечислены этапы использования класса <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> для включения сохраняемости для резидентных служб рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="49fb6-132">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="49fb6-133">Включение сохраняемости с помощью SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="49fb6-133">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="49fb6-134">Добавьте ссылку на System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="49fb6-134">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="49fb6-135">Добавьте следующий оператор в начало исходного файла после существующих инструкций using.</span><span class="sxs-lookup"><span data-stu-id="49fb6-135">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="49fb6-136">Создайте экземпляр `WorkflowServiceHost` и добавьте конечные точки для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="49fb6-136">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="49fb6-137">Создайте объект `SqlWorkflowInstanceStoreBehavior` и задайте свойства объекта поведения.</span><span class="sxs-lookup"><span data-stu-id="49fb6-137">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="49fb6-138">Откройте узел службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="49fb6-138">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="49fb6-139">Использование свойства DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="49fb6-139">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="49fb6-140">После применения поведения `SqlWorkflowInstanceStoreBehavior` хранилищу `DurableInstancingOptions.InstanceStore` на `WorkflowServiceHost` задается значение объекта `SqlWorkflowInstanceStore`, созданного с использованием значений конфигурации.</span><span class="sxs-lookup"><span data-stu-id="49fb6-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="49fb6-141">Эти же действия можно выполнить программно, чтобы задать свойство <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> узла `WorkflowServiceHost` без использования класса `SqlWorkflowInstanceStoreBehavior`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="49fb6-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="49fb6-142">Включение сохраняемости для размещенных на WAS служб рабочих процессов, которые используют WorkflowServiceHost, с помощью файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="49fb6-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="49fb6-143">Можно включить сохраняемость для резидентных или размещенных на WAS служб рабочих процессов с помощью файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="49fb6-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="49fb6-144">Служба рабочих процессов, размещенная на WAS, использует WorkflowServiceHost, так же как это делают резидентные службы рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="49fb6-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="49fb6-145">`SqlWorkflowInstanceStoreBehavior`Поведение службы, которое позволяет удобно изменять свойства [хранилища экземпляра рабочего процесса SQL](sql-workflow-instance-store.md) с помощью конфигурации XML.</span><span class="sxs-lookup"><span data-stu-id="49fb6-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="49fb6-146">Для служб рабочих процессов, размещенных на WAS, используется файл Web.config.</span><span class="sxs-lookup"><span data-stu-id="49fb6-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="49fb6-147">В следующем примере конфигурации показано, как настроить хранилище экземпляров рабочих процессов SQL с помощью элемента поведения `sqlWorkflowInstanceStore` в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="49fb6-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="49fb6-148">Если не заданы значения свойства `connectionString` или `connectionStringName`, хранилище экземпляров рабочих процессов SQL использует строку подключения по умолчанию `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="49fb6-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="49fb6-149">После применения поведения `SqlWorkflowInstanceStoreBehavior` хранилищу `DurableInstancingOptions.InstanceStore` на `WorkflowServiceHost` задается значение объекта `SqlWorkflowInstanceStore`, созданного с использованием значений конфигурации.</span><span class="sxs-lookup"><span data-stu-id="49fb6-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="49fb6-150">Эти же действия можно выполнить программно для использования `SqlWorkflowInstanceStore` с `WorkflowServiceHost` (без использования элемента поведения службы).</span><span class="sxs-lookup"><span data-stu-id="49fb6-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="49fb6-151">В файле Web.config не рекомендуется сохранять конфиденциальные сведения, такие как имена и пароли пользователей.</span><span class="sxs-lookup"><span data-stu-id="49fb6-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="49fb6-152">При сохранении в файле Web.config конфиденциальных сведений необходимо обеспечить защиту доступа к файлу Web.config с помощью списков управления доступом файловой системы.</span><span class="sxs-lookup"><span data-stu-id="49fb6-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="49fb6-153">Кроме того, можно защитить значения конфигурации в файле конфигурации, как упоминалось в этой области, [с помощью защищенной конфигурации](/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="49fb6-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="49fb6-154">Элементы Machine.config, связанные с функцией хранилища экземпляров рабочих процессов SQL</span><span class="sxs-lookup"><span data-stu-id="49fb6-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="49fb6-155">Установка [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] добавляет к файлу Machine.config следующие элементы, связанные с возможностью хранилища экземпляров рабочих процессов SQL:</span><span class="sxs-lookup"><span data-stu-id="49fb6-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="49fb6-156">Добавляет следующий элемент расширения поведения в файл Machine.config, чтобы можно было использовать \<sqlWorkflowInstanceStore> элемент поведения службы в файле конфигурации для настройки сохраняемости для служб.</span><span class="sxs-lookup"><span data-stu-id="49fb6-156">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
