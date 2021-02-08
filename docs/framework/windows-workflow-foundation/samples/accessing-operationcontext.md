---
description: 'Дополнительные сведения: доступ к OperationContext'
title: Доступ к контексту OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 768475f115f653630aaedeee976d0c96bc9e4dd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792626"
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="3ab7e-103">Доступ к контексту OperationContext</span><span class="sxs-lookup"><span data-stu-id="3ab7e-103">Accessing OperationContext</span></span>

<span data-ttu-id="3ab7e-104">В этом примере показано, как действия обмена сообщениями ( <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.Send> ) могут использоваться с действием пользовательской области для доступа к <xref:System.ServiceModel.OperationContext.Current%2A> настраиваемому заголовку сообщения и его получения в исходящем или входящем сообщении.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-104">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3ab7e-105">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="3ab7e-105">Demonstrates</span></span>  

 <span data-ttu-id="3ab7e-106">Действия обмена сообщениями, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-106">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3ab7e-107">Разговор</span><span class="sxs-lookup"><span data-stu-id="3ab7e-107">Discussion</span></span>  

 <span data-ttu-id="3ab7e-108">В этом образце показано, как использовать точки расширяемости (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) в действиях обмена сообщения для доступа к <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-108">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="3ab7e-109">Обратные вызовы регистрируются в среде выполнения рабочего процесса в качестве реализации свойства <xref:System.Activities.IExecutionProperty>, которое выбирается действиями обмена сообщениями после выполнения.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-109">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="3ab7e-110">Затрагиваются все действия обмена сообщениями в той же области, что и реализация <xref:System.Activities.IExecutionProperty>.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-110">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="3ab7e-111">В частности, в этом образце используется действие пользовательской области для принудительного задания поведения обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-111">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="3ab7e-112"><xref:System.ServiceModel.Activities.ISendMessageCallback> используется в клиентском рабочем процессе, чтобы включить состояние <xref:System.Activities.WorkflowApplication.Id%2A> рабочего процесса в качестве заголовка <xref:System.ServiceModel.Channels.MessageHeader> исходящего сообщения.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-112">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="3ab7e-113">Затем этот заголовок выбирается в службе с помощью <xref:System.ServiceModel.Activities.IReceiveMessageCallback>, и значение заголовка выводится на консоли.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-113">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3ab7e-114">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="3ab7e-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3ab7e-115">В этом образце доступ к службе рабочего процесса предоставляется через конечные точки HTTP.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-115">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="3ab7e-116">Чтобы выполнить этот пример, необходимо добавить соответствующие списки ACL URL-адресов (см. Дополнительные сведения о [настройке HTTP и HTTPS](../../wcf/feature-details/configuring-http-and-https.md) ), запустив Visual Studio от имени администратора или выполнив следующую команду в командной строке с повышенными привилегиями, чтобы добавить соответствующие списки ACL.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-116">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="3ab7e-117">Убедитесь, что подставлены нужный домен и имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-117">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="3ab7e-118">После добавления списков управления доступом по URL-адресу выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-118">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="3ab7e-119">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-119">Build the solution.</span></span>  
  
    2. <span data-ttu-id="3ab7e-120">Задайте несколько проектов запуска, щелкнув решение правой кнопкой мыши и выбрав пункт **задать запускаемые проекты**.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-120">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3. <span data-ttu-id="3ab7e-121">Добавьте **службу** и **клиент** (в этом порядке) в качестве нескольких запускаемых проектов.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-121">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4. <span data-ttu-id="3ab7e-122">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-122">Run the application.</span></span> <span data-ttu-id="3ab7e-123">На консоли клиента показан дважды выполняемый рабочий процесс, а в окне службы показаны идентификаторы экземпляров этих рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-123">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3ab7e-124">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3ab7e-125">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="3ab7e-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3ab7e-126">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3ab7e-127">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3ab7e-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
