---
description: 'Дополнительные сведения: шаблоны проектирования: List-Based Publish-Subscribe'
title: 'Шаблоны разработки: публикация-подписка на основе списка'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: b615da2afa4e6452b62eacae2cc6b61e4c4363dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726745"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="7cb05-103">Шаблоны разработки: публикация-подписка на основе списка</span><span class="sxs-lookup"><span data-stu-id="7cb05-103">Design Patterns: List-Based Publish-Subscribe</span></span>

<span data-ttu-id="7cb05-104">В этом примере показан шаблон Publish-Subscribe на основе списка, реализованный как программа Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7cb05-104">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cb05-105">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="7cb05-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7cb05-106">Шаблон Publish-Subscribe, основанный на списке, описан в статье публикация методик &, [Шаблоны интеграции](/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7cb05-106">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="7cb05-107">Шаблон публикации-подписки передает информацию коллекции получателей, подписавшихся на информационный раздел.</span><span class="sxs-lookup"><span data-stu-id="7cb05-107">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="7cb05-108">Шаблон публикации-подписки на основе списка поддерживает список подписчиков.</span><span class="sxs-lookup"><span data-stu-id="7cb05-108">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="7cb05-109">Если имеется информация для обмена, копия отправляется каждому подписчику в списке.</span><span class="sxs-lookup"><span data-stu-id="7cb05-109">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="7cb05-110">В этом образце демонстрируется динамический шаблон публикации-подписки на основе списка, в котором клиенты могут подписываться или отказываться от подписки так часто, как требуется.</span><span class="sxs-lookup"><span data-stu-id="7cb05-110">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="7cb05-111">Образец шаблона публикации-подписки на основе списка состоит из клиента, службы и программы источника данных.</span><span class="sxs-lookup"><span data-stu-id="7cb05-111">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="7cb05-112">Одновременно могут выполняться несколько клиентов и несколько программ источника данных.</span><span class="sxs-lookup"><span data-stu-id="7cb05-112">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="7cb05-113">Клиенты подписываются на службу, получают уведомления и отказываются от подписки.</span><span class="sxs-lookup"><span data-stu-id="7cb05-113">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="7cb05-114">Программы источника данных отправляют информацию службе для обмена со всеми текущими подписчиками.</span><span class="sxs-lookup"><span data-stu-id="7cb05-114">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="7cb05-115">В этом образце клиент и источник данных являются консольными программами (файлы EXE), а служба - библиотекой (.dll), размещенной в IIS.</span><span class="sxs-lookup"><span data-stu-id="7cb05-115">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="7cb05-116">Деятельность клиента и источника данных отображается на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="7cb05-116">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="7cb05-117">Служба использует дуплексную связь.</span><span class="sxs-lookup"><span data-stu-id="7cb05-117">The service uses duplex communication.</span></span> <span data-ttu-id="7cb05-118">Контракт службы `ISampleContract` объединен с контрактом обратного вызова `ISampleClientCallback`.</span><span class="sxs-lookup"><span data-stu-id="7cb05-118">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="7cb05-119">Служба реализует операции службы подписки и отказа от подписки, которые используются клиентами для присоединения к списку подписчиков и выхода из него.</span><span class="sxs-lookup"><span data-stu-id="7cb05-119">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="7cb05-120">Служба также реализует операцию службы `PublishPriceChange`, которую программа источника данных вызывает для предоставления службе новой информации.</span><span class="sxs-lookup"><span data-stu-id="7cb05-120">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="7cb05-121">Программа клиента реализует операцию службы `PriceChange`, вызываемую службой, чтобы уведомить всех подписчиков об изменении цены.</span><span class="sxs-lookup"><span data-stu-id="7cb05-121">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```csharp  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="7cb05-122">Служба использует событие среды .NET Framework в качестве механизма информирования всех подписчиков о поступлении новых сведений.</span><span class="sxs-lookup"><span data-stu-id="7cb05-122">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="7cb05-123">Когда клиент присоединяется к службе, вызывая метод Subscribe, он предоставляет обработчик событий.</span><span class="sxs-lookup"><span data-stu-id="7cb05-123">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="7cb05-124">Когда клиент покидает службу, он отказывается от подписки на событие для своего обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="7cb05-124">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="7cb05-125">Если источник данных вызывает службу, чтобы сообщить об изменении цены, служба создает событие.</span><span class="sxs-lookup"><span data-stu-id="7cb05-125">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="7cb05-126">При этом вызывается каждый экземпляр службы (по одному для каждого подписавшегося клиента), и в результате выполняются их обработчики событий.</span><span class="sxs-lookup"><span data-stu-id="7cb05-126">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="7cb05-127">Каждый обработчик событий передает информацию своему клиенту с помощью функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="7cb05-127">Each event handler passes the information to its client through its callback function.</span></span>  
  
```csharp
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="7cb05-128">При выполнении образца необходимо запускать несколько клиентов.</span><span class="sxs-lookup"><span data-stu-id="7cb05-128">When you run the sample, launch several clients.</span></span> <span data-ttu-id="7cb05-129">Клиенты подписываются на службу.</span><span class="sxs-lookup"><span data-stu-id="7cb05-129">The clients subscribe to the service.</span></span> <span data-ttu-id="7cb05-130">Затем необходимо выполнить программу источника данных, которая отправляет информацию службе.</span><span class="sxs-lookup"><span data-stu-id="7cb05-130">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="7cb05-131">Служба передает информацию всем подписчикам.</span><span class="sxs-lookup"><span data-stu-id="7cb05-131">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="7cb05-132">На консоли каждого клиента можно видеть выполняемые действия, подтверждающие, что информация была получена.</span><span class="sxs-lookup"><span data-stu-id="7cb05-132">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="7cb05-133">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="7cb05-133">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="7cb05-134">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="7cb05-134">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="7cb05-135">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7cb05-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7cb05-136">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7cb05-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="7cb05-137">Запуск образца на том же компьютере</span><span class="sxs-lookup"><span data-stu-id="7cb05-137">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="7cb05-138">Проверьте, что доступ к службе можно получить с помощью браузера, введя следующий адрес: `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="7cb05-138">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="7cb05-139">Должна отобразиться страница подтверждения.</span><span class="sxs-lookup"><span data-stu-id="7cb05-139">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="7cb05-140">Запустите Client.exe из \client\bin\ в \\ папке для конкретного языка.</span><span class="sxs-lookup"><span data-stu-id="7cb05-140">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="7cb05-141">Действия клиента отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="7cb05-141">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="7cb05-142">Запустите несколько клиентов.</span><span class="sxs-lookup"><span data-stu-id="7cb05-142">Launch several clients.</span></span>  
  
3. <span data-ttu-id="7cb05-143">Запустите Datasource.exe из \датасаурце\бин в \\ папке для конкретного языка.</span><span class="sxs-lookup"><span data-stu-id="7cb05-143">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="7cb05-144">Действия источника данных отображаются в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="7cb05-144">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="7cb05-145">После того, как источник данных отправляет информацию службе, она должна быть передана каждому клиенту.</span><span class="sxs-lookup"><span data-stu-id="7cb05-145">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="7cb05-146">Если клиент, источник данных и служебные программы не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7cb05-146">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="7cb05-147">Выполнение примера на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="7cb05-147">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="7cb05-148">Настройка компьютера службы.</span><span class="sxs-lookup"><span data-stu-id="7cb05-148">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="7cb05-149">На компьютере службы создайте виртуальный каталог с именем ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="7cb05-149">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="7cb05-150">Пакетный файл Setupvroot.bat из [процедуры однократной настройки для примеров Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md) можно использовать для создания каталога диска и виртуального каталога.</span><span class="sxs-lookup"><span data-stu-id="7cb05-150">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="7cb05-151">Скопируйте файлы программы службы из каталога %SystemDrive%\Inetpub\wwwroot\servicemodelsamples в виртуальный каталог ServiceModelSamples на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="7cb05-151">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="7cb05-152">Не забудьте включить файлы в каталог \bin.</span><span class="sxs-lookup"><span data-stu-id="7cb05-152">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="7cb05-153">Убедитесь, что доступ к службе с клиентского компьютера можно получить из браузера.</span><span class="sxs-lookup"><span data-stu-id="7cb05-153">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="7cb05-154">Настройка клиентских компьютеров.</span><span class="sxs-lookup"><span data-stu-id="7cb05-154">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="7cb05-155">Скопируйте на клиентские компьютеры файлы из папки \client\bin\ в языковой папке.</span><span class="sxs-lookup"><span data-stu-id="7cb05-155">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="7cb05-156">В каждом файле конфигурации клиента измените значение адреса определения конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="7cb05-156">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="7cb05-157">Замените любые ссылки на "localhost" в адресе полным именем домена.</span><span class="sxs-lookup"><span data-stu-id="7cb05-157">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="7cb05-158">Настройка компьютера источника данных.</span><span class="sxs-lookup"><span data-stu-id="7cb05-158">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="7cb05-159">Скопируйте на компьютер источника данных файлы программы источника данных из папки \datasource\bin\ в языковой папке.</span><span class="sxs-lookup"><span data-stu-id="7cb05-159">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="7cb05-160">В файле конфигурации источника данных измените значение адреса определения конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="7cb05-160">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="7cb05-161">Замените любые ссылки на "localhost" в адресе полным именем домена.</span><span class="sxs-lookup"><span data-stu-id="7cb05-161">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="7cb05-162">На клиентских компьютерах запустите из командной строки программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="7cb05-162">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="7cb05-163">На компьютере источника данных запустите из окна командной строки программу Datasource.exe.</span><span class="sxs-lookup"><span data-stu-id="7cb05-163">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7cb05-164">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="7cb05-164">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7cb05-165">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="7cb05-165">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7cb05-166">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="7cb05-166">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7cb05-167">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="7cb05-167">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`
