---
description: 'Дополнительные сведения о: OperationContextScope'
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: efe05bdf4071ef8dfd86cf4c393b2abb8d20ad31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793211"
---
# <a name="operationcontextscope"></a><span data-ttu-id="8bec2-103">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="8bec2-103">OperationContextScope</span></span>

<span data-ttu-id="8bec2-104">В примере OperationContextScope показано, как отправить дополнительные сведения о вызове Windows Communication Foundation (WCF) с помощью заголовков.</span><span class="sxs-lookup"><span data-stu-id="8bec2-104">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="8bec2-105">В этом образце сервер и клиент являются консольными приложениями.</span><span class="sxs-lookup"><span data-stu-id="8bec2-105">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bec2-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="8bec2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8bec2-107">В образце показано, как клиент может отправлять дополнительную информацию в виде <xref:System.ServiceModel.Channels.MessageHeader>, используя для этого <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="8bec2-107">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="8bec2-108">Создается объект <xref:System.ServiceModel.OperationContextScope> с областью, соответствующей каналу.</span><span class="sxs-lookup"><span data-stu-id="8bec2-108">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="8bec2-109">В коллекцию <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> можно добавлять заголовки, которые нужно передать удаленной службе.</span><span class="sxs-lookup"><span data-stu-id="8bec2-109">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="8bec2-110">Добавляемые в эту коллекцию заголовки можно извлекать на стороне службы через свойство <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bec2-110">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="8bec2-111">Вызовы осуществляются через различные каналы, но добавляемые к клиенту заголовки применяются только к каналу, с помощью которого был создан объект <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="8bec2-111">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="8bec2-112">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="8bec2-112">MessageHeaderReader</span></span>  

 <span data-ttu-id="8bec2-113">Это образец службы, которая получает сообщения от клиента и пытается найти заголовки в коллекции <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bec2-113">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="8bec2-114">Клиент передает идентификатор GUID, отправленный в заголовке, а служба извлекает пользовательский заголовок и, если имеется, сравнивает его с GUID, переданным клиентом в виде аргумента.</span><span class="sxs-lookup"><span data-stu-id="8bec2-114">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
```csharp
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+
         "Does it match with GUID sent as parameter: {1}",
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a><span data-ttu-id="8bec2-115">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="8bec2-115">MessageHeaderClient</span></span>  

 <span data-ttu-id="8bec2-116">Это реализация клиента, использующая прокси-сервер, созданный с помощью [средства служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) для взаимодействия с удаленной службой.</span><span class="sxs-lookup"><span data-stu-id="8bec2-116">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="8bec2-117">Сначала создается два прокси-объекта `MessageHeaderReaderClient`.</span><span class="sxs-lookup"><span data-stu-id="8bec2-117">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="8bec2-118">Затем клиент создает область OperationContextScope, связанную с `client1`.</span><span class="sxs-lookup"><span data-stu-id="8bec2-118">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="8bec2-119">Он добавляет заголовок <xref:System.ServiceModel.Channels.MessageHeader> в свойство <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> и осуществляет вызов на обоих клиентах.</span><span class="sxs-lookup"><span data-stu-id="8bec2-119">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="8bec2-120">Это гарантирует, что заголовок отправляется только в, `client1` а не в `client2` , путем проверки возвращаемого значения из `RetrieveHeader` вызова.</span><span class="sxs-lookup"><span data-stu-id="8bec2-120">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetrieveHeader on both the proxies. Since the OperationContextScope is tied to
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 <span data-ttu-id="8bec2-121">Этот образец размещается резидентно.</span><span class="sxs-lookup"><span data-stu-id="8bec2-121">This sample is self-hosted.</span></span> <span data-ttu-id="8bec2-122">Ниже показан образец результатов выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="8bec2-122">The following sample output from running the sample is provided:</span></span>  
  
```console  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8bec2-123">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="8bec2-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8bec2-124">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8bec2-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8bec2-125">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8bec2-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8bec2-126">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8bec2-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8bec2-127">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8bec2-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8bec2-128">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="8bec2-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8bec2-129">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="8bec2-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8bec2-130">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="8bec2-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
