---
description: 'Дополнительные сведения: Приостановка и возобновление рабочего процесса'
title: Приостановление и восстановление рабочего процесса
ms.date: 03/30/2017
ms.assetid: 11f38339-79c7-4295-b610-24a7223bbf6d
ms.openlocfilehash: 787dc2e2ddac03a059df30798645d561cb57437b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787894"
---
# <a name="pausing-and-resuming-a-workflow"></a><span data-ttu-id="411bb-103">Приостановление и восстановление рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="411bb-103">Pausing and Resuming a Workflow</span></span>

<span data-ttu-id="411bb-104">Выполнение рабочих процессов будет приостанавливаться и возобновляться при выполнении действий с закладками и блокировками, такими как <xref:System.Activities.Statements.Delay>. Кроме того, рабочие потоки можно будет явным образом приостановить, выгрузить и возобновить с использованием механизма сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="411bb-104">Workflows will pause and resume in response to bookmarks and blocking activities such as <xref:System.Activities.Statements.Delay>, but a workflow can also be explicitly paused, unloaded, and resumed by using persistence.</span></span>  
  
## <a name="pausing-a-workflow"></a><span data-ttu-id="411bb-105">Приостановка рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="411bb-105">Pausing a Workflow</span></span>  

 <span data-ttu-id="411bb-106">Чтобы приостановить рабочий процесс, пользуйтесь вызовом <xref:System.Activities.WorkflowApplication.Unload%2A>.</span><span class="sxs-lookup"><span data-stu-id="411bb-106">To pause a workflow, use <xref:System.Activities.WorkflowApplication.Unload%2A>.</span></span>  <span data-ttu-id="411bb-107">Этот метод отправляет запрос на сохранение и выгрузку рабочего процесса. При этом, если рабочий процесс не будет выгружен в течение 30 секунд, будет вызвано исключение <xref:System.TimeoutException>.</span><span class="sxs-lookup"><span data-stu-id="411bb-107">This method requests that the workflow persist and unload, and will throw a <xref:System.TimeoutException> if the workflow does not unload in 30 seconds.</span></span>  
  
```csharp  
try  
{  
    // attempt to unload will fail if the workflow is idle within a NoPersistZone  
    application.Unload(TimeSpan.FromSeconds(5));  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
## <a name="resuming-a-workflow"></a><span data-ttu-id="411bb-108">Возобновление рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="411bb-108">Resuming a Workflow</span></span>  

 <span data-ttu-id="411bb-109">Чтобы возобновить выполнение ранее приостановленного и выгруженного рабочего процесса, пользуйтесь вызовом <xref:System.Activities.WorkflowApplication.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="411bb-109">To resume a previously paused and unloaded workflow, use <xref:System.Activities.WorkflowApplication.Load%2A>.</span></span> <span data-ttu-id="411bb-110">Этот метод загружает рабочий процесс из хранилища сохраняемости в память.</span><span class="sxs-lookup"><span data-stu-id="411bb-110">This method loads a workflow from a persistence store into memory.</span></span>  
  
```csharp  
WorkflowApplication application = new WorkflowApplication(activity);  
application.InstanceStore = instanceStore;  
application.Load(id);  
```  
  
## <a name="example"></a><span data-ttu-id="411bb-111">Пример</span><span class="sxs-lookup"><span data-stu-id="411bb-111">Example</span></span>  

 <span data-ttu-id="411bb-112">В следующем образце кода описывается приостановка и возобновление выполнения рабочего процесса с помощью механизма сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="411bb-112">The following code sample demonstrates how to pause and resume a workflow by using persistence.</span></span>  
  
```csharp  
static string bkName = "bkName";  
static void Main(string[] args)
{  
    StartAndUnloadInstance();  
}  
  
static void StartAndUnloadInstance()
{  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(GetDelayedWF());  
    SqlWorkflowInstanceStore instanceStore = SetupSqlpersistenceStore();  
    wfApp.InstanceStore = instanceStore;  
    wfApp.Extensions.Add(SetupMyFileTrackingParticipant);  
    wfApp.PersistableIdle = (e) => {          ///persists application state and remove it from memory
    return PersistableIdleAction.Unload;  
    };  
    wfApp.Unloaded = (e) => {  
        waitHandler.Set();  
    };  
    Guid id = wfApp.Id;  
    wfApp.Run();  
    waitHandler.WaitOne();  
    LoadAndCompleteInstance(id);  
}  
  
static void LoadAndCompleteInstance(Guid id)
{
    Console.WriteLine("Press <enter> to load the persisted workflow");  
    Console.ReadLine();  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(GetDelayedWF());  
    wfApp.InstanceStore =  
        new SqlWorkflowInstanceStore(ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString());  
    wfApp.Completed = (workflowApplicationCompletedEventArgs) => {  
        Console.WriteLine("\nWorkflowApplication has Completed in the {0} state.",  
            workflowApplicationCompletedEventArgs.CompletionState);  
    };  
    wfApp.Unloaded = (workflowApplicationEventArgs) => {  
        Console.WriteLine("WorkflowApplication has Unloaded\n");  
        waitHandler.Set();  
    };  
    wfApp.Load(id);  
    wfApp.Run();  
    waitHandler.WaitOne();  
}  
  
public static Activity GetDelayedWF()
{  
    return new Sequence {  
        Activities ={  
            new WriteLine{Text="Workflow Started"},  
            new Delay{Duration=TimeSpan.FromSeconds(10)},  
            new WriteLine{Text="Workflow Ended"}  
        }  
    };  
}  
  
private static SqlWorkflowInstanceStore SetupSqlpersistenceStore()
{
     string connectionString = ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString();  
    SqlWorkflowInstanceStore sqlWFInstanceStore = new SqlWorkflowInstanceStore(connectionString);  
    sqlWFInstanceStore.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    InstanceHandle handle = sqlWFInstanceStore.CreateInstanceHandle();  
    InstanceView view = sqlWFInstanceStore.Execute(handle, new CreateWorkflowOwnerCommand(), TimeSpan.FromSeconds(5));  
    handle.Free();  
    sqlWFInstanceStore.DefaultInstanceOwner = view.InstanceOwner;  
    return sqlWFInstanceStore;  
}  
```
