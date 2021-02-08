---
description: 'Дополнительные сведения: нематериализованные экземпляры рабочих процессов'
title: Экземпляры нематериализованного рабочего процесса
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 0ee5968426a6bb800b9e70ac592c6da191c22511
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787907"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="5c8f7-103">Экземпляры нематериализованного рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="5c8f7-103">Non-Persisted Workflow Instances</span></span>

<span data-ttu-id="5c8f7-104">При создании нового экземпляра рабочего процесса, состояние которого сохраняется в <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, узел службы создает запись для этой службы в хранилище экземпляров.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-104">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="5c8f7-105">Затем при первом сохранении экземпляра рабочего процесса <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> сохраняет текущее состояние экземпляра.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-105">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="5c8f7-106">Если рабочий процесс размещен в службе активации Windows, данные развертывания службы также записываются в хранилище экземпляров при первом сохранении экземпляра.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-106">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>

<span data-ttu-id="5c8f7-107">Пока экземпляр рабочего процесса не сохранен, он находится в **непостоянном** состоянии.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-107">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="5c8f7-108">Если экземпляр рабочего процесса находится в этом состоянии, его нельзя восстановить после очистки домена приложения, ошибки узла или сбоя в работе компьютера.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-108">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>

## <a name="the-non-persisted-state"></a><span data-ttu-id="5c8f7-109">Несохраняемое состояние</span><span class="sxs-lookup"><span data-stu-id="5c8f7-109">The Non-Persisted State</span></span>

<span data-ttu-id="5c8f7-110">Несохраненные устойчивые экземпляры рабочего процесса остаются в несохраняемом состоянии в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-110">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>

- <span data-ttu-id="5c8f7-111">Сбой узла службы происходит до первого сохранения экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-111">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="5c8f7-112">Экземпляр рабочего процесса остается в хранилище экземпляров. Не выполняется восстановление этого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-112">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="5c8f7-113">Если поступает связанное сообщение, экземпляр рабочего процесса вновь становится активным.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-113">If a correlated message arrives, the workflow instance becomes active again.</span></span>

- <span data-ttu-id="5c8f7-114">Экземпляр рабочего процесса формирует исключение до его первого сохранения.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-114">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="5c8f7-115">В зависимости от возвращаемого <xref:System.Activities.UnhandledExceptionAction> выполняется следующий сценарий:</span><span class="sxs-lookup"><span data-stu-id="5c8f7-115">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>

  - <span data-ttu-id="5c8f7-116">Для <xref:System.Activities.UnhandledExceptionAction> задается <xref:System.Activities.UnhandledExceptionAction.Abort>: при формировании исключения данные развертывания службы записываются в хранилище экземпляров и экземпляр рабочего процесса выгружается из памяти.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-116"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="5c8f7-117">Экземпляр рабочего процесса остается в несохраняемом состоянии и не может быть выгружен.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-117">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>

  - <span data-ttu-id="5c8f7-118">Для <xref:System.Activities.UnhandledExceptionAction> задается <xref:System.Activities.UnhandledExceptionAction.Cancel> или <xref:System.Activities.UnhandledExceptionAction.Terminate>: при формировании исключения данные развертывания службы записываются в хранилище экземпляров и для экземпляра действия задается состояние <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-118"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>

<span data-ttu-id="5c8f7-119">Чтобы свести к минимуму риск возникновения невыгруженных несохраняемых экземпляров рабочих процессов, рекомендуется сохранять рабочие процессы на ранних этапах жизненного цикла.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-119">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>

## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="5c8f7-120">Обнаружение и удаление несохраняемых экземпляров</span><span class="sxs-lookup"><span data-stu-id="5c8f7-120">Detection and Removal of Non-Persisted Instances</span></span>

<span data-ttu-id="5c8f7-121"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> не удаляет из хранилища экземпляров несохраняемые экземпляры рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-121">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="5c8f7-122">Также не удаляются владельцы блокировок, срок действия которых истек и с которыми связаны несохраняемые экземпляры рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-122">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>

<span data-ttu-id="5c8f7-123">Администратору рекомендуется выполнять регулярную проверку хранилища экземпляров на наличие несохраняемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-123">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="5c8f7-124">Администраторы могут удалять эти экземпляры из хранилища экземпляров, если известно, что этот рабочий процесс не будет получать связанные сообщения.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-124">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="5c8f7-125">Например, если экземпляр находился в базе данных в течение нескольких месяцев и известно, что стандартное время существования жизненного цикла рабочего процесса составляет несколько дней, можно с уверенностью предположить, что это инициализированный экземпляр, в котором произошел сбой.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-125">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>

<span data-ttu-id="5c8f7-126">При поиске несохраняемых экземпляров в хранилище экземпляров рабочих процессов SQL можно использовать следующие SQL-запросы:</span><span class="sxs-lookup"><span data-stu-id="5c8f7-126">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>

- <span data-ttu-id="5c8f7-127">Этот запрос найдет все сохраненные экземпляры и вернет для них идентификаторы и время создания (сохраняется во времени в формате UTC).</span><span class="sxs-lookup"><span data-stu-id="5c8f7-127">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- <span data-ttu-id="5c8f7-128">Этот запрос найдет все несохраненные и незагруженные экземпляры и вернет для них идентификаторы и время создания (сохраняется во времени в формате UTC).</span><span class="sxs-lookup"><span data-stu-id="5c8f7-128">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- <span data-ttu-id="5c8f7-129">Этот запрос найдет все приостановленные и несохраненные экземпляры и вернет для них идентификаторы, время создания (сохраняется во времени в формате UTC), причину приостановления и имя исключения.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-129">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

<span data-ttu-id="5c8f7-130">При удалении несохраненных экземпляров будьте крайне внимательны.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-130">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="5c8f7-131">Как правило, несохраненные экземпляры, созданные <xref:System.ServiceModel.Activities.WorkflowServiceHost>, которые были отложены или не загружены, можно удалять без осложнений.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-131">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="5c8f7-132">Эти конкретные экземпляры можно удалить из хранилища путем их удаления из представления `[System.Activities.DurableInstancing].[Instances]` с помощью следующей команды SQL, указав правильный идентификатор экземпляра.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-132">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> <span data-ttu-id="5c8f7-133">Не рекомендуется удалять все несохраненные экземпляры, поскольку к ним относятся экземпляры, которые были недавно созданы и которые еще не были сохранены.</span><span class="sxs-lookup"><span data-stu-id="5c8f7-133">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
