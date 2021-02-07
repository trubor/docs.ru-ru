---
description: 'Дополнительные сведения: пример общего доступа к портам Net. TCP'
title: Пример совместного использования портов Net.TCP
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: 30b5e8896cfdd5b4174067fa37a047029bdb4502
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752162"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="1f2b6-103">Пример совместного использования портов Net.TCP</span><span class="sxs-lookup"><span data-stu-id="1f2b6-103">Net.TCP Port Sharing Sample</span></span>

<span data-ttu-id="1f2b6-104">Протокол TCP/IP использует 16-разрядное число, называемое номером порта, чтобы различать подключения к разным сетевым приложениям, выполняющимся на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-104">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="1f2b6-105">Если приложение ожидает передачи данных через порт, то весь трафик TCP через этот порт перенаправляется данному приложению.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-105">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="1f2b6-106">Другие приложения не могут одновременно ожидать передачи данных через тот же порт.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-106">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1f2b6-107">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1f2b6-108">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="1f2b6-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1f2b6-109">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1f2b6-110">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="1f2b6-111">У многих протоколов имеется номер порта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-111">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="1f2b6-112">Например, для протокола HTTP обычно используется порт TCP 80.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-112">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="1f2b6-113">У служб IIS имеется прослушиватель для совместного использования одного порта несколькими приложениями HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-113">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="1f2b6-114">Службы IIS ожидают передачи данных непосредственно через этот порт и перенаправляют сообщения соответствующим приложениям в зависимости от информации внутри сообщения.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-114">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="1f2b6-115">Это позволяет нескольким приложениям HTTP использовать один и тот же номер порта, не конкурируя за порт для получения сообщений.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-115">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="1f2b6-116">Совместное использование портов NetTcp — это функция Windows Communication Foundation (WCF), которая аналогично позволяет нескольким сетевым приложениям совместно использовать один порт.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-116">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="1f2b6-117">Служба общего доступа к портам NetTcp принимает подключения с помощью протокола net.tcp и перенаправляет сообщения в зависимости от их адреса назначения.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-117">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="1f2b6-118">По умолчанию служба общего доступа к портам NetTcp отключена.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-118">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="1f2b6-119">Перед запуском этого образца необходимо вручную включить эту службу.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-119">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="1f2b6-120">Дополнительные сведения см. [в разделе инструкции. Включение службы совместного использования портов net. TCP](../feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="1f2b6-120">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="1f2b6-121">Если служба отключена, при запуске серверного приложения создается исключение.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-121">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="1f2b6-122">Общий доступ к портам включается на сервере путем задания свойства <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> привязки <xref:System.ServiceModel.NetTcpBinding> или элемента привязки <xref:System.ServiceModel.Channels.TcpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-122">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="1f2b6-123">Чтобы использовать на сервере общий доступ к портам, клиенту не требуются сведения о его конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-123">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="1f2b6-124">Включение общего доступа к портам</span><span class="sxs-lookup"><span data-stu-id="1f2b6-124">Enabling Port Sharing</span></span>  

 <span data-ttu-id="1f2b6-125">В следующем примере кода показано, как включить на сервере общий доступ к портам.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-125">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="1f2b6-126">Он запускает экземпляр службы `ICalculator` на фиксированном порту со случайным путем универсального кода ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="1f2b6-126">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="1f2b6-127">Хотя две службы могут использовать один и тот же порт, их адреса конечных точек должны быть уникальными, чтобы служба общего доступа к портам NetTcp могла перенаправлять сообщения нужным приложениям.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-127">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 <span data-ttu-id="1f2b6-128">Если общий доступ к портам включен, службу можно запускать несколько раз без конфликта по поводу номера порта.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-128">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="1f2b6-129">Если изменить код и отключить общий доступ к портам, то в случае запуска двух экземпляров службы при запуске второго экземпляра будет создано исключение <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-129">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="1f2b6-130">Запуск примера</span><span class="sxs-lookup"><span data-stu-id="1f2b6-130">Running the Sample</span></span>  

 <span data-ttu-id="1f2b6-131">Чтобы проверить, что сообщения правильно направляются службам, которые совместно используют порт, можно воспользоваться тестовым клиентом.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-131">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 <span data-ttu-id="1f2b6-132">Каждый экземпляр службы выводит собственный уникальный номер и адрес.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-132">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="1f2b6-133">Например, при запуске файла service.exe можно увидеть следующий текст.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-133">For instance, you may see the following text when you run service.exe.</span></span>  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="1f2b6-134">При запуске файла client.exe введите показанный номер службы.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-134">Enter the service number you see here when you run client.exe.</span></span>  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="1f2b6-135">Этот образец можно выполнять на нескольких компьютерах, если изменить созданный адрес, используемый клиентом.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-135">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="1f2b6-136">В файле Client.cs измените строку формата адреса конечной точки, чтобы она соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-136">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="1f2b6-137">Замените вхождения localhost на IP-адрес серверного компьютера.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-137">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="1f2b6-138">После внесения этого изменения необходимо перекомпилировать пример.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-138">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1f2b6-139">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="1f2b6-139">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1f2b6-140">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-140">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="1f2b6-141">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1f2b6-141">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="1f2b6-142">Включите службу общего доступа к портам NetTcp, как описано в начале раздела.</span><span class="sxs-lookup"><span data-stu-id="1f2b6-142">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4. <span data-ttu-id="1f2b6-143">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1f2b6-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="1f2b6-144">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1f2b6-144">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="1f2b6-145">Конкретные сведения о выполнении этого образца описаны в разделе "Выполнение образца".</span><span class="sxs-lookup"><span data-stu-id="1f2b6-145">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
