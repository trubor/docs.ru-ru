---
description: 'Дополнительные сведения: компенсация'
title: Компенсация
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: d2c57a248939d0485075a5cbf57d91789f58d01a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792795"
---
# <a name="compensation"></a><span data-ttu-id="70e48-103">Компенсация</span><span class="sxs-lookup"><span data-stu-id="70e48-103">Compensation</span></span>

<span data-ttu-id="70e48-104">Компенсация в Windows Workflow Foundation (WF) — это механизм, с помощью которого ранее завершенная работа может быть отменена или компенсироваться (после логики, определенной приложением) при последующем возникновении сбоя.</span><span class="sxs-lookup"><span data-stu-id="70e48-104">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="70e48-105">В данном разделе описывается применение компенсации в рабочих процессах.</span><span class="sxs-lookup"><span data-stu-id="70e48-105">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="70e48-106">Сравнение компенсации и транзакций</span><span class="sxs-lookup"><span data-stu-id="70e48-106">Compensation vs. Transactions</span></span>  

 <span data-ttu-id="70e48-107">Транзакция позволяет объединить несколько операций в одну единицу работы.</span><span class="sxs-lookup"><span data-stu-id="70e48-107">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="70e48-108">Использование транзакции дает приложению возможность прерывать (откатывать) все изменения, выполненные в транзакции, если во время выполнения какой-либо части обработки транзакции возникнет ошибка.</span><span class="sxs-lookup"><span data-stu-id="70e48-108">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="70e48-109">Однако использование транзакций может быть неприемлемо, если работа является долговременной.</span><span class="sxs-lookup"><span data-stu-id="70e48-109">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="70e48-110">Пусть, например, приложение планирования путешествия реализовано как рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="70e48-110">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="70e48-111">Шагами рабочего процесса могут быть заказ авиабилетов, ожидание подтверждения диспетчера и, наконец, оплата билета.</span><span class="sxs-lookup"><span data-stu-id="70e48-111">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="70e48-112">Этот процесс может занять несколько дней, и включение шагов заказа и оплаты авиабилетов в одну транзакцию непрактично.</span><span class="sxs-lookup"><span data-stu-id="70e48-112">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="70e48-113">Если позднее в процессе произойдет ошибка, в таком сценарии можно воспользоваться компенсацией для отмены шага заказа в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="70e48-113">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70e48-114">В этом разделе описывается компенсация в рабочих процессах.</span><span class="sxs-lookup"><span data-stu-id="70e48-114">This topic covers compensation in workflows.</span></span> <span data-ttu-id="70e48-115">Дополнительные сведения о транзакциях в рабочих процессах см. в разделе [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="70e48-115">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="70e48-116">Дополнительные сведения о транзакциях см. в статьях <xref:System.Transactions?displayProperty=nameWithType> и <xref:System.Transactions.Transaction?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="70e48-116">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="70e48-117">Использование действия CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="70e48-117">Using CompensableActivity</span></span>  

 <span data-ttu-id="70e48-118"><xref:System.Activities.Statements.CompensableActivity> - это базовое действие компенсации в [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70e48-118"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="70e48-119">Все выполняющие работу действия, для которых может понадобиться выполнить компенсацию, помещаются в элемент <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="70e48-119">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="70e48-120">В данном примере шаг бронирования при покупке авиабилета размещен в элементе <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity>, а отмена бронирования помещается в обработчик <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="70e48-120">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="70e48-121">Сразу за действием <xref:System.Activities.Statements.CompensableActivity> в рабочем процессе идут два действия, ожидающие одобрения от диспетчера и выполняющие шаг приобретения билета.</span><span class="sxs-lookup"><span data-stu-id="70e48-121">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="70e48-122">Если состояние ошибки вызывает отмену рабочего процесса после успешного завершения работы действия <xref:System.Activities.Statements.CompensableActivity>, то действия в обработчике <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> планируются к выполнению, а полет отменяется.</span><span class="sxs-lookup"><span data-stu-id="70e48-122">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="70e48-123">Далее показан пример рабочего процесса в XAML.</span><span class="sxs-lookup"><span data-stu-id="70e48-123">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="70e48-124">При вызове рабочего процесса на консоль выводятся следующие данные.</span><span class="sxs-lookup"><span data-stu-id="70e48-124">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="70e48-125">**Ресервефлигхт: билет зарезервирован.**</span><span class="sxs-lookup"><span data-stu-id="70e48-125">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="70e48-126">**ManagerApproval: получено утверждение от диспетчера.** 
 **Пурчасефлигхт: билет приобретен.** 
 **Рабочий процесс успешно завершен с состоянием: закрыто.**</span><span class="sxs-lookup"><span data-stu-id="70e48-126">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="70e48-127">В образцах действий этого раздела, таких как `ReserveFlight`, на консоли отображается их название и назначение для иллюстрации порядка, в котором действия выполняются при возникновении компенсации.</span><span class="sxs-lookup"><span data-stu-id="70e48-127">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="70e48-128">Компенсация рабочего процесса по умолчанию</span><span class="sxs-lookup"><span data-stu-id="70e48-128">Default Workflow Compensation</span></span>  

 <span data-ttu-id="70e48-129">По умолчанию, если рабочий процесс отменяется, то логика компенсации выполняется для всех подлежащих компенсации действий, которые уже успешно выполнены, но еще не были подтверждены или компенсированы.</span><span class="sxs-lookup"><span data-stu-id="70e48-129">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70e48-130">Если <xref:System.Activities.Statements.CompensableActivity> *подтверждено*, компенсация за действие больше не может быть вызвана.</span><span class="sxs-lookup"><span data-stu-id="70e48-130">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="70e48-131">Процесс подтверждения описывается далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="70e48-131">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="70e48-132">В данном примере исключение выдается после бронирования авиабилета, но до шага подтверждения диспетчера.</span><span class="sxs-lookup"><span data-stu-id="70e48-132">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="70e48-133">Этот пример является рабочим процессом в XAML.</span><span class="sxs-lookup"><span data-stu-id="70e48-133">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="70e48-134">Если вызывается рабочий процесс, исключение смоделированного условия ошибки обрабатывается ведущим приложением в <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, рабочий процесс отменяется, и вызывается логика компенсации.</span><span class="sxs-lookup"><span data-stu-id="70e48-134">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="70e48-135">**Ресервефлигхт: билет зарезервирован.**</span><span class="sxs-lookup"><span data-stu-id="70e48-135">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="70e48-136">**Симулатедерроркондитион: создание ApplicationException.** 
 **Необработанное исключение рабочего процесса:** 
 **System. ApplicationException: смоделированное условие ошибки в рабочем процессе.** 
 **Канцелфлигхт: билет отменен.** 
 **Рабочий процесс успешно завершен с состоянием "отменено".**</span><span class="sxs-lookup"><span data-stu-id="70e48-136">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>

### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="70e48-137">Отмена и CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="70e48-137">Cancellation and CompensableActivity</span></span>  

 <span data-ttu-id="70e48-138">Если действия в теле <xref:System.Activities.Statements.CompensableActivity.Body%2A> объекта <xref:System.Activities.Statements.CompensableActivity> не завершены, и действие отменено, выполняются действия в обработчике <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="70e48-138">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70e48-139">Обработчик <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> вызывается, только если действия в теле <xref:System.Activities.Statements.CompensableActivity.Body%2A> объекта <xref:System.Activities.Statements.CompensableActivity> не завершены, и действие отменено.</span><span class="sxs-lookup"><span data-stu-id="70e48-139">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="70e48-140">Обработчик <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> выполняется, только если действия в теле <xref:System.Activities.Statements.CompensableActivity.Body%2A> объекта <xref:System.Activities.Statements.CompensableActivity> успешно завершены, после чего на действии вызвана компенсация.</span><span class="sxs-lookup"><span data-stu-id="70e48-140">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="70e48-141">Обработчик <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> предоставляет разработчикам рабочего процесса возможность предоставить соответствующую логику отмены.</span><span class="sxs-lookup"><span data-stu-id="70e48-141">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="70e48-142">В следующем примере во время выполнения <xref:System.Activities.Statements.CompensableActivity.Body%2A> создается исключение, а затем вызывается обработчик <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="70e48-142">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="70e48-143">Этот пример является рабочим процессом в XAML.</span><span class="sxs-lookup"><span data-stu-id="70e48-143">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="70e48-144">Если вызывается рабочий процесс, исключение смоделированного условия ошибки обрабатывается ведущим приложением в <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, рабочий процесс отменяется, и вызывается логика отмены объекта <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="70e48-144">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="70e48-145">В этом примере логика компенсации и логика отмены имеют различные задачи.</span><span class="sxs-lookup"><span data-stu-id="70e48-145">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="70e48-146">Успешное завершение <xref:System.Activities.Statements.CompensableActivity.Body%2A> означает, что с кредитной карты были списаны средства, а авиабилет заказан, поэтому компенсация должна отменить оба шага.</span><span class="sxs-lookup"><span data-stu-id="70e48-146">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="70e48-147">(В этом примере отмена рейса автоматически отменяет оплату кредитных карт.) Однако если <xref:System.Activities.Statements.CompensableActivity> отменяется, это означает, что <xref:System.Activities.Statements.CompensableActivity.Body%2A> не завершено, и логика <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> должна уметь определить, как лучше обрабатывать отмену.</span><span class="sxs-lookup"><span data-stu-id="70e48-147">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="70e48-148">В этом примере <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> отменяет начисление обязательства на кредитную карту, но, поскольку `ReserveFlight` было последним действием в <xref:System.Activities.Statements.CompensableActivity.Body%2A>, попытка отмены авиабилета не выполняется.</span><span class="sxs-lookup"><span data-stu-id="70e48-148">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="70e48-149">Поскольку `ReserveFlight` было последним действием в <xref:System.Activities.Statements.CompensableActivity.Body%2A>, если оно успешно завершилось, то <xref:System.Activities.Statements.CompensableActivity.Body%2A> также завершилась и отмена невозможна.</span><span class="sxs-lookup"><span data-stu-id="70e48-149">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="70e48-150">**ChargeCreditCard: начисление обязательства на кредитную карту за авиабилет.**</span><span class="sxs-lookup"><span data-stu-id="70e48-150">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="70e48-151">**Симулатедерроркондитион: создание ApplicationException.** 
 **Необработанное исключение рабочего процесса:** 
 **System. ApplicationException: смоделированное условие ошибки в рабочем процессе.** 
 **Канцелкредиткард: Отмена оплаты кредитных карт.** 
 **Рабочий процесс успешно завершен с состоянием "отменено".**</span><span class="sxs-lookup"><span data-stu-id="70e48-151">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="70e48-152">Дополнительные сведения об отмене см. в разделе [Отмена](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="70e48-152">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="70e48-153">Явная компенсация с использованием действия компенсации</span><span class="sxs-lookup"><span data-stu-id="70e48-153">Explicit Compensation Using the Compensate Activity</span></span>  

 <span data-ttu-id="70e48-154">В предыдущем разделе была описана неявная компенсация.</span><span class="sxs-lookup"><span data-stu-id="70e48-154">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="70e48-155">Неявная компенсация может использоваться в простых сценариях, но если требуется более явный контроль над планированием обработки компенсации, можно использовать действие <xref:System.Activities.Statements.Compensate>.</span><span class="sxs-lookup"><span data-stu-id="70e48-155">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="70e48-156">Для инициации процесса компенсации с применением действия <xref:System.Activities.Statements.Compensate> используется маркер <xref:System.Activities.Statements.CompensationToken> действия <xref:System.Activities.Statements.CompensableActivity>, для которого необходимо провести компенсацию.</span><span class="sxs-lookup"><span data-stu-id="70e48-156">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="70e48-157">Действие <xref:System.Activities.Statements.Compensate> может использоваться для запуска компенсации для любого выполненного действия <xref:System.Activities.Statements.CompensableActivity>, которое не было подтверждено или компенсировано.</span><span class="sxs-lookup"><span data-stu-id="70e48-157">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="70e48-158">Например, действие <xref:System.Activities.Statements.Compensate> может использоваться в разделе <xref:System.Activities.Statements.TryCatch.Catches%2A> действия <xref:System.Activities.Statements.TryCatch> или в любой момент после завершения действия <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="70e48-158">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="70e48-159">В данном примере действие <xref:System.Activities.Statements.Compensate> используется в разделе <xref:System.Activities.Statements.TryCatch.Catches%2A> действия <xref:System.Activities.Statements.TryCatch> для обращения действия <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="70e48-159">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="70e48-160">Этот пример является рабочим процессом в XAML.</span><span class="sxs-lookup"><span data-stu-id="70e48-160">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="70e48-161">При вызове рабочего процесса на консоль выводятся следующие данные.</span><span class="sxs-lookup"><span data-stu-id="70e48-161">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="70e48-162">**Ресервефлигхт: билет зарезервирован.**</span><span class="sxs-lookup"><span data-stu-id="70e48-162">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="70e48-163">**Симулатедерроркондитион: создание ApplicationException.** 
 **Канцелфлигхт: билет отменен.** 
 **Рабочий процесс успешно завершен с состоянием: закрыто.**</span><span class="sxs-lookup"><span data-stu-id="70e48-163">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>

### <a name="confirming-compensation"></a><span data-ttu-id="70e48-164">Подтверждение компенсации</span><span class="sxs-lookup"><span data-stu-id="70e48-164">Confirming Compensation</span></span>  

 <span data-ttu-id="70e48-165">По умолчанию подлежащие компенсации действия могут быть компенсированы в любой момент после их завершения.</span><span class="sxs-lookup"><span data-stu-id="70e48-165">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="70e48-166">Но в некоторых ситуациях это может быть невозможно.</span><span class="sxs-lookup"><span data-stu-id="70e48-166">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="70e48-167">В предыдущем примере компенсацией для бронирования авиабилета служит отмена бронирования.</span><span class="sxs-lookup"><span data-stu-id="70e48-167">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="70e48-168">Однако после выполнения перелета такой шаг компенсации уже недопустим.</span><span class="sxs-lookup"><span data-stu-id="70e48-168">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="70e48-169">Подтверждение подлежащего компенсации действия вызывает действие, заданное обработчиком <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="70e48-169">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="70e48-170">Это может использоваться, например, для освобождения любых ресурсов, которые требуются при выполнении компенсации.</span><span class="sxs-lookup"><span data-stu-id="70e48-170">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="70e48-171">После подтверждения действия, которое могло быть компенсировано, его компенсация становится невозможной, и при попытке такой компенсации возникнет исключение <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="70e48-171">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="70e48-172">Если рабочий процесс завершается успешно, все неподтвержденные и некомпенсированные действия, завершенные успешно, подтверждаются в порядке, обратном порядку их завершения.</span><span class="sxs-lookup"><span data-stu-id="70e48-172">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="70e48-173">В данном примере авиабилет бронируется, приобретается и завершается, после чего выполняется подтверждение действия, подлежащего компенсации.</span><span class="sxs-lookup"><span data-stu-id="70e48-173">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="70e48-174">Для подтверждения действия <xref:System.Activities.Statements.CompensableActivity> следует использовать действие <xref:System.Activities.Statements.Confirm> и задать маркер <xref:System.Activities.Statements.CompensationToken> действия <xref:System.Activities.Statements.CompensableActivity>, подлежащего подтверждению.</span><span class="sxs-lookup"><span data-stu-id="70e48-174">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="70e48-175">Этот пример является рабочим процессом в XAML.</span><span class="sxs-lookup"><span data-stu-id="70e48-175">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
<span data-ttu-id="70e48-176">При вызове рабочего процесса на консоль выводятся следующие данные.</span><span class="sxs-lookup"><span data-stu-id="70e48-176">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="70e48-177">**Ресервефлигхт: билет зарезервирован.**</span><span class="sxs-lookup"><span data-stu-id="70e48-177">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="70e48-178">**ManagerApproval: получено утверждение от диспетчера.** 
 **Пурчасефлигхт: билет приобретен.** 
 **Такефлигхт: перелет завершен.** 
 **Конфирмфлигхт: рейс сделан, компенсация невозможна.** 
 **Рабочий процесс успешно завершен с состоянием: закрыто.**</span><span class="sxs-lookup"><span data-stu-id="70e48-178">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="70e48-179">Вложенные действия компенсации</span><span class="sxs-lookup"><span data-stu-id="70e48-179">Nesting Compensation Activities</span></span>  

<span data-ttu-id="70e48-180">Действие <xref:System.Activities.Statements.CompensableActivity> может быть помещено в раздел <xref:System.Activities.Statements.CompensableActivity.Body%2A> другого действия <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="70e48-180">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="70e48-181">Объект <xref:System.Activities.Statements.CompensableActivity> не может быть помещен в обработчик другого <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="70e48-181">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="70e48-182">Родительское действие <xref:System.Activities.Statements.CompensableActivity> обязано убедиться в том, что при отмене, подтверждении или компенсации все дочерние действия, подлежащие компенсации, которые успешно завершились и еще не подтверждены и не компенсированы, должны быть подтверждены или компенсированы перед тем, как родительское действие завершит отмену, подтверждение или компенсацию.</span><span class="sxs-lookup"><span data-stu-id="70e48-182">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="70e48-183">Если это не моделируется явным образом, родительское действие <xref:System.Activities.Statements.CompensableActivity> неявно компенсирует дочерние действия, подлежащие компенсации, если получит сигнал отмены или компенсации.</span><span class="sxs-lookup"><span data-stu-id="70e48-183">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="70e48-184">Если родитель получил сигнал подтверждения, родитель неявно подтвердит дочерние действия, подлежащие компенсации.</span><span class="sxs-lookup"><span data-stu-id="70e48-184">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="70e48-185">Если логика обработки отмены, подтверждения или компенсации явным образом моделируется в обработчике родительского <xref:System.Activities.Statements.CompensableActivity>, то любое явно не обработанное дочернее действие будет неявно подтверждено.</span><span class="sxs-lookup"><span data-stu-id="70e48-185">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e48-186">См. также</span><span class="sxs-lookup"><span data-stu-id="70e48-186">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
