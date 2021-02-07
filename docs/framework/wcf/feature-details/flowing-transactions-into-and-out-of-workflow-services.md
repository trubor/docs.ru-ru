---
description: 'Дополнительные сведения: перетекание транзакций в службы рабочих процессов и из них'
title: Направление транзакций в службы рабочего процесса и из них
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: f39740c45dd70fbc06963b8e842f9a01a0393f7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704970"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="3ece2-103">Направление транзакций в службы рабочего процесса и из них</span><span class="sxs-lookup"><span data-stu-id="3ece2-103">Flowing Transactions into and out of Workflow Services</span></span>

<span data-ttu-id="3ece2-104">Службы и клиенты рабочих процессов могут использоваться в транзакциях.</span><span class="sxs-lookup"><span data-stu-id="3ece2-104">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="3ece2-105">Чтобы сделать операцию службы частью внешней транзакции, поместите действие <xref:System.ServiceModel.Activities.Receive> в действие <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-105">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="3ece2-106">Все вызовы, выполненные действием <xref:System.ServiceModel.Activities.Send> или <xref:System.ServiceModel.Activities.SendReply> в области <xref:System.ServiceModel.Activities.TransactedReceiveScope>, также будут выполнены во внешней транзакции.</span><span class="sxs-lookup"><span data-stu-id="3ece2-106">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="3ece2-107">Клиентское приложение рабочего процесса может создавать внешнюю транзакцию с помощью действия <xref:System.Activities.Statements.TransactionScope> и вызывать операции службы с помощью внешних транзакций.</span><span class="sxs-lookup"><span data-stu-id="3ece2-107">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="3ece2-108">В данном разделе описывается создание службы рабочего процесса и клиента рабочего процесса, которые участвуют в транзакции.</span><span class="sxs-lookup"><span data-stu-id="3ece2-108">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="3ece2-109">Если экземпляр службы рабочего процесса загружен в рамках транзакции, а рабочий процесс содержит <xref:System.Activities.Statements.Persist> действие, экземпляр рабочего процесса будет заблокирован до истечения времени ожидания транзакции.</span><span class="sxs-lookup"><span data-stu-id="3ece2-109">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3ece2-110">При использовании области <xref:System.ServiceModel.Activities.TransactedReceiveScope> рекомендуется размещать все операции получения в рабочем процессе в действиях, связанных с областью <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-110">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3ece2-111">Если используется область <xref:System.ServiceModel.Activities.TransactedReceiveScope>, а сообщения поступают в неверном порядке, рабочий процесс будет прерван при попытке доставки первого сообщения, пришедшего в неправильном порядке.</span><span class="sxs-lookup"><span data-stu-id="3ece2-111">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="3ece2-112">Убедитесь, что рабочий процесс всегда находится в согласованном состоянии при освобождении рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="3ece2-112">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="3ece2-113">Это позволит перезапустить рабочий процесс с прежней сохраненной точки в случае, если он был прерван.</span><span class="sxs-lookup"><span data-stu-id="3ece2-113">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="3ece2-114">Создание общей библиотеки</span><span class="sxs-lookup"><span data-stu-id="3ece2-114">Create a shared library</span></span>  
  
1. <span data-ttu-id="3ece2-115">Создайте новое пустое решение Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ece2-115">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="3ece2-116">Добавьте новый проект библиотеки классов с именем `Common`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-116">Add a new class library project called `Common`.</span></span> <span data-ttu-id="3ece2-117">Добавьте ссылки на следующие сборки:</span><span class="sxs-lookup"><span data-stu-id="3ece2-117">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="3ece2-118">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="3ece2-118">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="3ece2-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="3ece2-119">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="3ece2-120">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="3ece2-120">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="3ece2-121">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="3ece2-121">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="3ece2-122">Добавьте новый класс с именем `PrintTransactionInfo` к проекту `Common`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-122">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="3ece2-123">Класс является производным от <xref:System.Activities.NativeActivity> и перегружает метод <xref:System.Activities.NativeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-123">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     <span data-ttu-id="3ece2-124">Это собственное действие, при выполнении которого отображаются данные о внешней транзакции, и оно используется в службе и клиенте рабочих процессов, описываемых в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="3ece2-124">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="3ece2-125">Выполните сборку решения, чтобы сделать это действие доступным в разделе " **Общие** " области **элементов**.</span><span class="sxs-lookup"><span data-stu-id="3ece2-125">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="3ece2-126">Реализация службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="3ece2-126">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="3ece2-127">Добавьте новую службу рабочего процесса WCF, которая вызывается `WorkflowService` в `Common` проект.</span><span class="sxs-lookup"><span data-stu-id="3ece2-127">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="3ece2-128">Для этого щелкните проект правой кнопкой мыши `Common` , выберите **Добавить**, **новый элемент...**, выберите **Рабочий процесс** в разделе **Установленные шаблоны** и выберите **Служба рабочего процесса WCF**.</span><span class="sxs-lookup"><span data-stu-id="3ece2-128">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Добавление службы рабочего процесса](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="3ece2-130">Удалите заданные по умолчанию действия `ReceiveRequest` и `SendResponse`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-130">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="3ece2-131">Перетащите действие с именем <xref:System.Activities.Statements.WriteLine> в `Sequential Service`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-131">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="3ece2-132">Задайте значение для свойства текста `"Workflow Service starting ..."`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3ece2-132">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="3ece2-133">! [Добавление действия WriteLine к действию последовательной службы (./медиа/фловинг-трансактионс-Инто-Анд-аут-оф-воркфлов-сервицес/add-writeline-sequential-service.jpg)</span><span class="sxs-lookup"><span data-stu-id="3ece2-133">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="3ece2-134">Перетащите действие <xref:System.ServiceModel.Activities.TransactedReceiveScope> и поместите его после действия <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-134">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="3ece2-135">Это <xref:System.ServiceModel.Activities.TransactedReceiveScope> действие можно найти в разделе « **Обмен сообщениями** » **панели элементов**.</span><span class="sxs-lookup"><span data-stu-id="3ece2-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="3ece2-136"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Действие состоит из двух разделов: **запрос** и **текст**.</span><span class="sxs-lookup"><span data-stu-id="3ece2-136">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="3ece2-137">Раздел **запроса** содержит <xref:System.ServiceModel.Activities.Receive> действие.</span><span class="sxs-lookup"><span data-stu-id="3ece2-137">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="3ece2-138">Раздел **Body** содержит действия, выполняемые в рамках транзакции после получения сообщения.</span><span class="sxs-lookup"><span data-stu-id="3ece2-138">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![Добавление действия TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="3ece2-140">Выберите <xref:System.ServiceModel.Activities.TransactedReceiveScope> действие и нажмите кнопку **переменные** .</span><span class="sxs-lookup"><span data-stu-id="3ece2-140">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="3ece2-141">Добавьте следующие переменные.</span><span class="sxs-lookup"><span data-stu-id="3ece2-141">Add the following variables.</span></span>  
  
     ![Добавление переменных в TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="3ece2-143">Можно удалить переменную данных, заданную по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3ece2-143">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="3ece2-144">Также можно использовать существующую переменную обработки.</span><span class="sxs-lookup"><span data-stu-id="3ece2-144">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="3ece2-145">Перетащите <xref:System.ServiceModel.Activities.Receive> действие в раздел **запроса** <xref:System.ServiceModel.Activities.TransactedReceiveScope> действия.</span><span class="sxs-lookup"><span data-stu-id="3ece2-145">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="3ece2-146">Задайте следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="3ece2-146">Set the following properties:</span></span>  
  
    |<span data-ttu-id="3ece2-147">Свойство</span><span class="sxs-lookup"><span data-stu-id="3ece2-147">Property</span></span>|<span data-ttu-id="3ece2-148">Значение</span><span class="sxs-lookup"><span data-stu-id="3ece2-148">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="3ece2-149">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="3ece2-149">CanCreateInstance</span></span>|<span data-ttu-id="3ece2-150">True (установите флажок)</span><span class="sxs-lookup"><span data-stu-id="3ece2-150">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="3ece2-151">OperationName</span><span class="sxs-lookup"><span data-stu-id="3ece2-151">OperationName</span></span>|<span data-ttu-id="3ece2-152">StartSample</span><span class="sxs-lookup"><span data-stu-id="3ece2-152">StartSample</span></span>|  
    |<span data-ttu-id="3ece2-153">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="3ece2-153">ServiceContractName</span></span>|<span data-ttu-id="3ece2-154">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="3ece2-154">ITransactionSample</span></span>|  
  
     <span data-ttu-id="3ece2-155">Рабочий процесс должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="3ece2-155">The workflow should look like this:</span></span>  
  
     ![Добавление действия Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="3ece2-157">Щелкните ссылку **define...** в <xref:System.ServiceModel.Activities.Receive> действии и задайте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="3ece2-157">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Настройка параметров сообщений для действия Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="3ece2-159">Перетащите действие <xref:System.Activities.Statements.Sequence> в разделе «Текст» <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-159">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="3ece2-160">В действии <xref:System.Activities.Statements.Sequence> перетащите два действия <xref:System.Activities.Statements.WriteLine> и настройте свойства <xref:System.Activities.Statements.WriteLine.Text%2A>, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="3ece2-160">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="3ece2-161">Действие</span><span class="sxs-lookup"><span data-stu-id="3ece2-161">Activity</span></span>|<span data-ttu-id="3ece2-162">Значение</span><span class="sxs-lookup"><span data-stu-id="3ece2-162">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="3ece2-163">Первое действие WriteLine</span><span class="sxs-lookup"><span data-stu-id="3ece2-163">1st WriteLine</span></span>|<span data-ttu-id="3ece2-164">"Служба: получение завершено"</span><span class="sxs-lookup"><span data-stu-id="3ece2-164">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="3ece2-165">Второе действие WriteLine</span><span class="sxs-lookup"><span data-stu-id="3ece2-165">2nd WriteLine</span></span>|<span data-ttu-id="3ece2-166">"Service: Received = " + requestMessage</span><span class="sxs-lookup"><span data-stu-id="3ece2-166">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="3ece2-167">После этого рабочий процесс должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="3ece2-167">The workflow should now look like this:</span></span>  
  
     ![Последовательность после добавления действий WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="3ece2-169">Перетащите `PrintTransactionInfo` действие после второго <xref:System.Activities.Statements.WriteLine> действия в **текст** <xref:System.ServiceModel.Activities.TransactedReceiveScope> действия.</span><span class="sxs-lookup"><span data-stu-id="3ece2-169">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![Последовательность после добавления Принттрансактионинфо](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="3ece2-171">Перетащите действие <xref:System.Activities.Statements.Assign>, поместите его после действия `PrintTransactionInfo` и задайте свойства в соответствии со следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="3ece2-171">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="3ece2-172">Свойство</span><span class="sxs-lookup"><span data-stu-id="3ece2-172">Property</span></span>|<span data-ttu-id="3ece2-173">Значение</span><span class="sxs-lookup"><span data-stu-id="3ece2-173">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="3ece2-174">Кому</span><span class="sxs-lookup"><span data-stu-id="3ece2-174">To</span></span>|<span data-ttu-id="3ece2-175">replyMessage</span><span class="sxs-lookup"><span data-stu-id="3ece2-175">replyMessage</span></span>|  
    |<span data-ttu-id="3ece2-176">Значение</span><span class="sxs-lookup"><span data-stu-id="3ece2-176">Value</span></span>|<span data-ttu-id="3ece2-177">"Service: Sending reply."</span><span class="sxs-lookup"><span data-stu-id="3ece2-177">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="3ece2-178">Перетащите действие <xref:System.Activities.Statements.WriteLine>, поместите его после действия <xref:System.Activities.Statements.Assign> и задайте для свойства <xref:System.Activities.Statements.WriteLine.Text%2A> значение "Service: Begin reply".</span><span class="sxs-lookup"><span data-stu-id="3ece2-178">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="3ece2-179">После этого рабочий процесс должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="3ece2-179">The workflow should now look like this:</span></span>  
  
     ![После добавления Assign и WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="3ece2-181">Щелкните действие правой кнопкой мыши <xref:System.ServiceModel.Activities.Receive> и выберите **Создать SendReply** и вставьте его после последнего <xref:System.Activities.Statements.WriteLine> действия.</span><span class="sxs-lookup"><span data-stu-id="3ece2-181">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="3ece2-182">Щелкните ссылку **define...** в `SendReplyToReceive` действии и задайте следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="3ece2-182">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Параметры ответного сообщения](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="3ece2-184">Перетащите <xref:System.Activities.Statements.WriteLine> действие после `SendReplyToReceive` действия и задайте <xref:System.Activities.Statements.WriteLine.Text%2A> для его свойства значение "служба: ответ отправлен".</span><span class="sxs-lookup"><span data-stu-id="3ece2-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="3ece2-185">Перетащите действие <xref:System.Activities.Statements.WriteLine> в нижнюю область рабочего процесса и задайте для свойства <xref:System.Activities.Statements.WriteLine.Text%2A> значение "Service: Workflow ends, press ENTER to exit".</span><span class="sxs-lookup"><span data-stu-id="3ece2-185">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="3ece2-186">Завершенный рабочий процесс службы должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3ece2-186">The completed service workflow should look like this:</span></span>  
  
     ![Полный рабочий процесс службы](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="3ece2-188">Реализуйте клиент рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="3ece2-188">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="3ece2-189">Добавьте новое приложение WCF Workflow с именем `WorkflowClient` к проекту `Common`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-189">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="3ece2-190">Для этого щелкните проект правой кнопкой мыши `Common` , выберите **Добавить**, **новый элемент...**, выберите **Рабочий процесс** в разделе **Установленные шаблоны** и выберите **действие**.</span><span class="sxs-lookup"><span data-stu-id="3ece2-190">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Добавление проекта действия](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="3ece2-192">Перетащите действие <xref:System.Activities.Statements.Sequence> в область конструктора.</span><span class="sxs-lookup"><span data-stu-id="3ece2-192">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="3ece2-193">В действии <xref:System.Activities.Statements.Sequence> перетащите действие <xref:System.Activities.Statements.WriteLine> и задайте для его свойства <xref:System.Activities.Statements.WriteLine.Text%2A> значение `"Client: Workflow starting"`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-193">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="3ece2-194">После этого рабочий процесс должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="3ece2-194">The workflow should now look like this:</span></span>  
  
     ![Добавление действия WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="3ece2-196">Перетащите действие <xref:System.Activities.Statements.TransactionScope> и поместите его после действия <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-196">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="3ece2-197">Выберите действие <xref:System.Activities.Statements.TransactionScope>, нажмите кнопку «Переменные» и добавьте следующие переменные.</span><span class="sxs-lookup"><span data-stu-id="3ece2-197">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![Добавление переменных в TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="3ece2-199">Перетащите действие <xref:System.Activities.Statements.Sequence> в текст действия <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-199">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="3ece2-200">Перетащите действие `PrintTransactionInfo` в <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-200">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="3ece2-201">Перетащите <xref:System.Activities.Statements.WriteLine> действие после `PrintTransactionInfo` действия и задайте <xref:System.Activities.Statements.WriteLine.Text%2A> для его свойства значение "Клиент: Начало отправки".</span><span class="sxs-lookup"><span data-stu-id="3ece2-201">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="3ece2-202">После этого рабочий процесс должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="3ece2-202">The workflow should now look like this:</span></span>  
  
     ![Добавление клиента: Начало отправки действий](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="3ece2-204">Перетащите действие <xref:System.ServiceModel.Activities.Send>, поместите его после действия <xref:System.Activities.Statements.Assign> и задайте следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="3ece2-204">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="3ece2-205">Свойство</span><span class="sxs-lookup"><span data-stu-id="3ece2-205">Property</span></span>|<span data-ttu-id="3ece2-206">Значение</span><span class="sxs-lookup"><span data-stu-id="3ece2-206">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="3ece2-207">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="3ece2-207">EndpointConfigurationName</span></span>|<span data-ttu-id="3ece2-208">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="3ece2-208">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="3ece2-209">OperationName</span><span class="sxs-lookup"><span data-stu-id="3ece2-209">OperationName</span></span>|<span data-ttu-id="3ece2-210">StartSample</span><span class="sxs-lookup"><span data-stu-id="3ece2-210">StartSample</span></span>|  
    |<span data-ttu-id="3ece2-211">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="3ece2-211">ServiceContractName</span></span>|<span data-ttu-id="3ece2-212">ITransactionSample</span><span class="sxs-lookup"><span data-stu-id="3ece2-212">ITransactionSample</span></span>|  
  
     <span data-ttu-id="3ece2-213">После этого рабочий процесс должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="3ece2-213">The workflow should now look like this:</span></span>  
  
     ![Задание свойств действия Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="3ece2-215">Щелкните ссылку **define...** и задайте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="3ece2-215">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Параметры сообщения действия Send](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="3ece2-217">Щелкните действие правой кнопкой мыши <xref:System.ServiceModel.Activities.Send> и выберите **создать ReceiveReply**.</span><span class="sxs-lookup"><span data-stu-id="3ece2-217">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="3ece2-218">Действие <xref:System.ServiceModel.Activities.ReceiveReply> будет автоматически помещено после действия <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-218">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="3ece2-219">Щелкните ссылку «Определить...» в действии ReceiveReplyForSend и задайте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="3ece2-219">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![Задание параметров сообщения ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="3ece2-221">Перетащите действие <xref:System.Activities.Statements.WriteLine>, поместите его между действиями <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply>, а также задайте для свойства <xref:System.Activities.Statements.WriteLine.Text%2A> значение "Client: Send complete".</span><span class="sxs-lookup"><span data-stu-id="3ece2-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="3ece2-222">Перетащите действие <xref:System.Activities.Statements.WriteLine>, поместите его после действия <xref:System.ServiceModel.Activities.ReceiveReply> и задайте для свойства <xref:System.Activities.Statements.WriteLine.Text%2A> значение "Client side: Reply received = " + replyMessage.</span><span class="sxs-lookup"><span data-stu-id="3ece2-222">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="3ece2-223">Перетащите действие `PrintTransactionInfo` и поместите его после действия <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="3ece2-223">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="3ece2-224">Перетащите действие <xref:System.Activities.Statements.WriteLine> в конец рабочего процесса и задайте для свойства <xref:System.Activities.Statements.WriteLine.Text%2A> значение "Client workflow ends".</span><span class="sxs-lookup"><span data-stu-id="3ece2-224">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="3ece2-225">Завершенный рабочий процесс клиента должен выглядеть следующим образом на приведенной ниже схеме.</span><span class="sxs-lookup"><span data-stu-id="3ece2-225">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Завершенный рабочий процесс клиента](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="3ece2-227">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="3ece2-227">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="3ece2-228">Создание приложения службы</span><span class="sxs-lookup"><span data-stu-id="3ece2-228">Create the Service application</span></span>  
  
1. <span data-ttu-id="3ece2-229">Добавьте в решение новый проект консольного приложения с именем `Service`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-229">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="3ece2-230">Добавьте ссылки на следующие сборки:</span><span class="sxs-lookup"><span data-stu-id="3ece2-230">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="3ece2-231">System.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="3ece2-231">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="3ece2-232">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="3ece2-232">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="3ece2-233">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="3ece2-233">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="3ece2-234">Откройте созданный файл Program.cs и следующий код:</span><span class="sxs-lookup"><span data-stu-id="3ece2-234">Open the generated Program.cs file and the following code:</span></span>  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };
          }  
    ```  
  
3. <span data-ttu-id="3ece2-235">Добавьте к проекту следующий файл app.config.</span><span class="sxs-lookup"><span data-stu-id="3ece2-235">Add the following app.config file to the project.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a><span data-ttu-id="3ece2-236">Создание клиентского приложения</span><span class="sxs-lookup"><span data-stu-id="3ece2-236">Create the client application</span></span>  
  
1. <span data-ttu-id="3ece2-237">Добавьте в решение новый проект консольного приложения с именем `Client`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-237">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="3ece2-238">Добавьте ссылку на библиотеку System.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="3ece2-238">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="3ece2-239">Откройте файл program.cs и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="3ece2-239">Open the program.cs file and add the following code.</span></span>  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3ece2-240">См. также</span><span class="sxs-lookup"><span data-stu-id="3ece2-240">See also</span></span>

- [<span data-ttu-id="3ece2-241">Службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="3ece2-241">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="3ece2-242">Общие сведения о транзакциях Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3ece2-242">Windows Communication Foundation Transactions Overview</span></span>](transactions-overview.md)
