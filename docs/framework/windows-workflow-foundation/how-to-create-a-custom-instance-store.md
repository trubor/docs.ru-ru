---
description: Дополнительные сведения см. в статье Создание пользовательского хранилища экземпляров.
title: Практическое руководство. Создание настраиваемого хранилища экземпляров
ms.date: 03/30/2017
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
ms.openlocfilehash: 3a1a511e6a97dffe510c839aceec8c9d91a77ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742138"
---
# <a name="how-to-create-a-custom-instance-store"></a><span data-ttu-id="7bede-103">Практическое руководство. Создание настраиваемого хранилища экземпляров</span><span class="sxs-lookup"><span data-stu-id="7bede-103">How to: Create a Custom Instance Store</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="7bede-104">содержит <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> - хранилище экземпляров SQL Server, которое используется для сохранения данных рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="7bede-104">contains <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, an instance store that uses SQL Server to persist workflow data.</span></span> <span data-ttu-id="7bede-105">Если приложению необходимо сохранить данные рабочего процесса в другой среде передачи, например базе данных или файловой системе, вы можете создать настраиваемое хранилище экземпляров.</span><span class="sxs-lookup"><span data-stu-id="7bede-105">If your application is required to persist workflow data to another medium, such as a different database or a file system, you can implement a custom instance store.</span></span> <span data-ttu-id="7bede-106">Пользовательское хранилище экземпляров создается путем расширения абстрактного класса <xref:System.Runtime.DurableInstancing.InstanceStore> и реализации методов, которые необходимы для реализации.</span><span class="sxs-lookup"><span data-stu-id="7bede-106">A custom instance store is created by extending the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class and implementing the methods that are required for the implementation.</span></span> <span data-ttu-id="7bede-107">Полную реализацию хранилища пользовательских экземпляров см. в примере [корпоративного процесса покупки](./samples/corporate-purchase-process.md) .</span><span class="sxs-lookup"><span data-stu-id="7bede-107">For a complete implementation of a custom instance store, see the [Corporate Purchase Process](./samples/corporate-purchase-process.md) sample.</span></span>

## <a name="implementing-the-begintrycommand-method"></a><span data-ttu-id="7bede-108">Реализация метода BeginTryCommand</span><span class="sxs-lookup"><span data-stu-id="7bede-108">Implementing the BeginTryCommand method</span></span>

<span data-ttu-id="7bede-109"><xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> отправляется в хранилище экземпляров подсистемой сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="7bede-109">The <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> is sent to the instance store by the persistence engine.</span></span> <span data-ttu-id="7bede-110">Тип параметра `command` указывает, какая команда выполняется. Этот параметр может быть следующих типов:</span><span class="sxs-lookup"><span data-stu-id="7bede-110">The type of the `command` parameter indicates which command is being executed; this parameter can be of the following types:</span></span>

- <span data-ttu-id="7bede-111"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>. Подсистема сохраняемости отправляет эту команду в хранилище экземпляров, когда рабочий процесс должен были сохранен в среде хранения.</span><span class="sxs-lookup"><span data-stu-id="7bede-111"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be persisted to the storage medium.</span></span> <span data-ttu-id="7bede-112">Сведения о сохраняемости рабочего процесса передаются методу в участнике <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> параметра `command`.</span><span class="sxs-lookup"><span data-stu-id="7bede-112">The workflow persistence data is provided to the method in the <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> member of the `command` parameter.</span></span>

- <span data-ttu-id="7bede-113"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>. Механизм сохраняемости отправляет эту команду в хранилище экземпляров при вызове рабочего процесса из среды хранения.</span><span class="sxs-lookup"><span data-stu-id="7bede-113"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be loaded from the storage medium.</span></span> <span data-ttu-id="7bede-114">Идентификатор экземпляра рабочего процесса, который требуется загрузить, предоставляется методу в параметре `instanceId` свойства <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> параметра `context`.</span><span class="sxs-lookup"><span data-stu-id="7bede-114">The instance ID of the workflow to be loaded is provided to the method in the `instanceId` parameter of the <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> property of the `context` parameter.</span></span>

- <span data-ttu-id="7bede-115"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>. Механизм сохраняемости отправляет эту команду в хранилище экземпляров, когда <xref:System.ServiceModel.Activities.WorkflowServiceHost> следует зарегистрировать в качестве владельца блокировки.</span><span class="sxs-lookup"><span data-stu-id="7bede-115"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when a <xref:System.ServiceModel.Activities.WorkflowServiceHost> must be registered as a lock owner.</span></span> <span data-ttu-id="7bede-116">Идентификатор экземпляра текущего рабочего процесса должен быть передан в хранилище экземпляров с помощью метода <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> в параметре `context`.</span><span class="sxs-lookup"><span data-stu-id="7bede-116">The instance ID of the current workflow should be provided to the instance store using <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> method of the `context` parameter.</span></span>

     <span data-ttu-id="7bede-117">В следующем фрагменте кода показано, как реализовать команду CreateWorkflowOwner, чтобы назначить явного владельца блокировки.</span><span class="sxs-lookup"><span data-stu-id="7bede-117">The following code snippet demonstrates how to implement the CreateWorkflowOwner command to assign an explicit lock owner.</span></span>

    ```csharp
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");
    ...
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()
    {
        InstanceOwnerMetadata =
        {
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },
        }
    };
    InstanceHandle ownerHandle = store.CreateInstanceHandle();
    store.DefaultInstanceOwner = store.Execute(
                                   ownerHandle,
                                   createCommand,
                                   TimeSpan.FromSeconds(30)).InstanceOwner;
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });
    ```

- <span data-ttu-id="7bede-118"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>. Механизм сохраняемости отправляет эту команду в хранилище экземпляров, если идентификатор экземпляра владельца блокировки может быть удален из хранилища экземпляров.</span><span class="sxs-lookup"><span data-stu-id="7bede-118"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when the instance ID of a lock owner can be removed from the instance store.</span></span> <span data-ttu-id="7bede-119">Как и в случае с <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, идентификатор владельца блокировки должен быть предоставлен приложением.</span><span class="sxs-lookup"><span data-stu-id="7bede-119">As with <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, the ID of the lock owner should be provided by the application.</span></span>

     <span data-ttu-id="7bede-120">В следующем фрагменте кода показано, как с помощью <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand> освободить блокировку.</span><span class="sxs-lookup"><span data-stu-id="7bede-120">The following code snippet demonstrates how to release a lock using <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span></span>

    ```csharp
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)
    {
        handle.Free();
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);
        try
        {
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.
            Thread.Sleep(10000);
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));
        }
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }
        catch (Exception ex) { Log.Inform(ex.Message); }
        finally
        {
            handle.Free();
            store.DefaultInstanceOwner = null;
        }
    }
    ```

     <span data-ttu-id="7bede-121">Приведенный выше метод должен быть вызван в блоке try/catch при запуске экземпляра дочернего действия.</span><span class="sxs-lookup"><span data-stu-id="7bede-121">The above method should be called in a Try/Catch block when a child instance is run.</span></span>

    ```csharp
    try
    {
        childInstance.Run();
    }
    catch (Exception)
    {
        throw ;
    }
    finally
    {
        FreeHandleAndDeleteOwner(store, ownerHandle);
    }
    ```

- <span data-ttu-id="7bede-122"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>. Механизм сохраняемости отправляет эту команду в хранилище экземпляров, когда экземпляр рабочего процесса необходимо загрузить с помощью ключа экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="7bede-122"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: The persistence engine sends this command to the instance store when a workflow instance is to be loaded using the workflow’s instance key.</span></span> <span data-ttu-id="7bede-123">Идентификатор ключа экземпляра может быть указан с помощью параметра <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> команды.</span><span class="sxs-lookup"><span data-stu-id="7bede-123">The ID of the instance key can be determined by using the <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parameter of the command.</span></span>

- <span data-ttu-id="7bede-124"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>. Механизм сохраняемости отправляет эту команду в хранилище экземпляров для извлечения параметров активации сохраненных рабочих процессов для создания узла рабочего процесса, который затем может загружать рабочие процессы.</span><span class="sxs-lookup"><span data-stu-id="7bede-124"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: The persistence engine sends this command to the instance store to retrieve activation parameters for persisted workflows in order to create a workflow host that can then load workflows.</span></span> <span data-ttu-id="7bede-125">Эта команда отправляется подсистемой в ответ на вызов хранилищем экземпляров <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> для узла, когда она выполняет поиск экземпляра, который можно активировать.</span><span class="sxs-lookup"><span data-stu-id="7bede-125">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> to the host when it locates an instance that can be activated.</span></span> <span data-ttu-id="7bede-126">Хранилище экземпляров должно быть опрошено, чтобы определить, есть ли рабочие процессы, которые можно активировать.</span><span class="sxs-lookup"><span data-stu-id="7bede-126">The instance store should be polled to determine if there are workflows that can be activated.</span></span>

- <span data-ttu-id="7bede-127"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>. Механизм сохраняемости отправляет эту команду в хранилище экземпляров для загрузки запускаемых экземпляров рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="7bede-127"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: The persistence engine sends this command to the instance store to load runnable workflow instances.</span></span> <span data-ttu-id="7bede-128">Эта команда отправляется подсистемой в ответ на вызов хранилищем экземпляров <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> для узла, когда она выполняет поиск экземпляра, который можно выполнить.</span><span class="sxs-lookup"><span data-stu-id="7bede-128">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> to the host when it locates an instance that can be run.</span></span> <span data-ttu-id="7bede-129">Хранилище экземпляров должно сделать запрос рабочих процессов, которые можно выполнить.</span><span class="sxs-lookup"><span data-stu-id="7bede-129">The instance store should poll for workflows that can be run.</span></span> <span data-ttu-id="7bede-130">Следующий фрагмент кода демонстрирует опрос в хранилище экземпляров рабочих процессов, которые можно выполнить или активировать.</span><span class="sxs-lookup"><span data-stu-id="7bede-130">The following code snippet demonstrates polling an instance store for workflows that can be run or activated.</span></span>

    ```csharp
    public void PollForEvents()
    {
        InstanceOwner[] storeOwners = this.GetInstanceOwners();

        foreach (InstanceOwner owner in storeOwners)
        {
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))
            {
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))
                {
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivatable);
                    if (hasRunnable)
                    {
                        this.SignalEvent(ppEvent, owner);
                    }
                    else
                    {
                        this.ResetEvent(ppEvent, owner);
                    }
                }
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))
                {
                   bool hasActivatable = GetActivatableEvents(this.StoreId, owner.InstanceOwnerId);
                   if (hasActivatable)
                    {
                        this.SignalEvent(ppEvent, owner);
                    }
                    else
                    {
                        this.ResetEvent(ppEvent, owner);
                    }
                }
            }
        }
    }
    ```

     <span data-ttu-id="7bede-131">В предыдущем фрагменте кода хранилище экземпляров запрашивает доступные события и проверяет каждое из них, определяя, является ли оно событием <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>.</span><span class="sxs-lookup"><span data-stu-id="7bede-131">In the above code snippet, the instance store queries the events available and examines each one to determine if it is a <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> event.</span></span> <span data-ttu-id="7bede-132">Если событие обнаружено, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> вызывается для подачи сигнала узлу для отправки команды в хранилище экземпляров.</span><span class="sxs-lookup"><span data-stu-id="7bede-132">If one is found, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> is called to signal the host to send a command to the instance store.</span></span> <span data-ttu-id="7bede-133">Следующий фрагмент кода демонстрирует реализацию обработчика события для этой команды.</span><span class="sxs-lookup"><span data-stu-id="7bede-133">The following code snippet demonstrates an implementation of a handler for this command.</span></span>

    ```csharp
    If (command is TryLoadRunnableWorkflowCommand)
    {
        Owner owner;
        CheckOwner(context, command.Name, out owner);
        // Checking instance.Owner is like an InstanceLockQueryResult.
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));

        XName ownerService = null;
        InstanceValue value;
        Instance runnableInstance = default(Instance);
        bool foundRunnableInstance = false;

        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);
        if (value != null && value.Value is XName)
        {
            ownerService = (XName)value.Value;
        }

        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)
        {
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)
            {
                continue;
            }

            if (ownerService != null)
            {
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);
                if (value == null || ((XName)value.Value) != ownerService)
                {
                    continue;
                }
            }

            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);
            if (value != null && value.Value != null && value.Value is string)
            {
                continue;
            }

            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")
            {
                runnableInstance = instance.Value;
                foundRunnableInstance = true;
            }

            if (!foundRunnableInstance)
            {
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)
                {
                    runnableInstance = instance.Value;
                    foundRunnableInstance = true;
                }
            }

            if (foundRunnableInstance)
            {
                runnableInstance.LockVersion++;
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;
                MemoryStore.instances[instance.Key] = runnableInstance;
                context.BindInstance(instance.Key);
                context.BindAcquiredLock(runnableInstance.LockVersion);

                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)
                {
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)
                {
                    if (keyEntry.Value.Completed)
                    {
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));
                    }
                    else
                    {
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));
                    }
                }
            }

            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);
            break;
        }
    }
    ```

    <span data-ttu-id="7bede-134">В предыдущем фрагменте кода хранилище экземпляров выполняет поиск запускаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="7bede-134">In the above code snippet, the instance store searches for runnable instances.</span></span> <span data-ttu-id="7bede-135">Если экземпляр найден, он связывается с контекстом выполнения и загружается.</span><span class="sxs-lookup"><span data-stu-id="7bede-135">If an instance is found, it is bound to the execution context and loaded.</span></span>

## <a name="using-a-custom-instance-store"></a><span data-ttu-id="7bede-136">Использование пользовательского хранилища экземпляров</span><span class="sxs-lookup"><span data-stu-id="7bede-136">Using a custom instance store</span></span>

<span data-ttu-id="7bede-137">Чтобы реализовать пользовательское хранилище экземпляров, присвойте <xref:System.Activities.WorkflowApplication.InstanceStore%2A> экземпляр хранилища экземпляров и реализуйте метод <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="7bede-137">To implement a custom instance store, assign an instance of the instance store to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, and implement the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> method.</span></span> <span data-ttu-id="7bede-138">См. Руководство по [созданию и запуску длительно выполняемого рабочего процесса](how-to-create-and-run-a-long-running-workflow.md) для конкретных действий.</span><span class="sxs-lookup"><span data-stu-id="7bede-138">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) tutorial for specifics.</span></span>

## <a name="a-sample-instance-store"></a><span data-ttu-id="7bede-139">Образец хранилища экземпляров</span><span class="sxs-lookup"><span data-stu-id="7bede-139">A sample instance store</span></span>

<span data-ttu-id="7bede-140">Следующий пример кода представляет собой полную реализацию хранилища экземпляров, взятую из примера [корпоративного процесса покупки](./samples/corporate-purchase-process.md) .</span><span class="sxs-lookup"><span data-stu-id="7bede-140">The following code sample is a complete instance store implementation, taken from the [Corporate Purchase Process](./samples/corporate-purchase-process.md) sample.</span></span> <span data-ttu-id="7bede-141">Это хранилище экземпляров сохраняет данные рабочих процессов в файл с помощью XML.</span><span class="sxs-lookup"><span data-stu-id="7bede-141">This instance store persists workflow data to a file using XML.</span></span>

```csharp
using System;
using System.Activities.DurableInstancing;
using System.Collections.Generic;
using System.IO;
using System.Runtime.DurableInstancing;
using System.Runtime.Serialization;
using System.ServiceModel.Persistence;
using System.Xml;
using System.Xml.Linq;

namespace Microsoft.Samples.WF.PurchaseProcess
{

    public class XmlWorkflowInstanceStore : InstanceStore
    {
        Guid ownerInstanceID;

        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())
        {

        }

        public XmlWorkflowInstanceStore(Guid id)
        {
            ownerInstanceID = id;
        }

        //Synchronous version of the Begin/EndTryCommand functions
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)
        {
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));
        }

        //The persistence engine will send a variety of commands to the configured InstanceStore,
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.
        //This method is where we will handle those commands
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)
        {
            IDictionary<XName, InstanceValue> data = null;

            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle
            if (command is CreateWorkflowOwnerCommand)
            {
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());
            }
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key
            else if (command is SaveWorkflowCommand)
            {
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;
                data = saveCommand.InstanceData;

                Save(data);
            }
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle
            else if (command is LoadWorkflowCommand)
            {
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);

                try
                {
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))
                    {
                        data = LoadInstanceDataFromFile(inputStream);
                        //load the data into the persistence Context
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);
                    }
                }
                catch (Exception exception)
                {
                    throw new PersistenceException(exception.Message);
                }
            }

            return new CompletedAsyncResult<bool>(true, callback, state);
        }

        protected override bool EndTryCommand(IAsyncResult result)
        {
            return CompletedAsyncResult<bool>.End(result);
        }

        //Reads data from xml file and creates a dictionary based off of that.
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)
        {
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();

            NetDataContractSerializer s = new NetDataContractSerializer();

            XmlReader rdr = XmlReader.Create(inputStream);
            XmlDocument doc = new XmlDocument();
            doc.Load(rdr);

            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");
            foreach (XmlElement instanceElement in instances)
            {
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");
                XName key = (XName)DeserializeObject(s, keyElement);

                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");
                object value = DeserializeObject(s, valueElement);
                InstanceValue instVal = new InstanceValue(value);

                data.Add(key, instVal);
            }

            return data;
        }

        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)
        {
            object deserializedObject = null;

            MemoryStream stm = new MemoryStream();
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);
            element.WriteContentTo(wtr);
            wtr.Flush();
            stm.Position = 0;

            deserializedObject = serializer.Deserialize(stm);

            return deserializedObject;
        }

        //Saves the persistence data to an xml file.
        void Save(IDictionary<XName, InstanceValue> instanceData)
        {
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);
            XmlDocument doc = new XmlDocument();
            doc.LoadXml("<InstanceValues/>");

            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)
            {
                XmlElement newInstance = doc.CreateElement("InstanceValue");

                XmlElement newKey = SerializeObject("key", valPair.Key, doc);
                newInstance.AppendChild(newKey);

                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);
                newInstance.AppendChild(newValue);

                doc.DocumentElement.AppendChild(newInstance);
            }
            doc.Save(fileName);
       }

        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)
        {
            NetDataContractSerializer s = new NetDataContractSerializer();
            XmlElement newElement = doc.CreateElement(elementName);
            MemoryStream stm = new MemoryStream();

            s.Serialize(stm, o);
            stm.Position = 0;
            StreamReader rdr = new StreamReader(stm);
            newElement.InnerXml = rdr.ReadToEnd();

            return newElement;
        }
    }
}
```
