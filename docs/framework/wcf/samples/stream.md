---
description: 'Дополнительные сведения: Stream'
title: Поток
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: ea0759f9eca2a974f77e8a6b059160b9a45bd94e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668855"
---
# <a name="stream"></a><span data-ttu-id="8f7f5-103">Поток</span><span class="sxs-lookup"><span data-stu-id="8f7f5-103">Stream</span></span>

<span data-ttu-id="8f7f5-104">Образец потока демонстрирует использование взаимодействия в режиме потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-104">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="8f7f5-105">Служба предоставляет несколько операций, которые отправляют и принимают потоки.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-105">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="8f7f5-106">Этот образец размещается резидентно.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-106">This sample is self-hosted.</span></span> <span data-ttu-id="8f7f5-107">Как клиент, так и служба являются консольными программами.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-107">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f7f5-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8f7f5-109">Windows Communication Foundation (WCF) может взаимодействовать в двух режимах передачи — с буферизацией или потоковой передачей.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-109">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="8f7f5-110">По умолчанию используется режим буферизованной передачи, в случае которого сообщение должно быть доставлено полностью, прежде чем получатель сможет его прочитать.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-110">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="8f7f5-111">При использовании режима потоковой передачи получатель может начать обработку сообщения до того, как оно будет доставлено полностью.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-111">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="8f7f5-112">Режим потоковой передачи полезно использовать при большой длине передаваемых данных, которые могут обрабатываться последовательно.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-112">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="8f7f5-113">Режим потоковой передачи также может быть полезен, когда размер сообщения слишком велик для выполнения полной буферизации.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-113">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="8f7f5-114">Потоковая передача и контракты службы</span><span class="sxs-lookup"><span data-stu-id="8f7f5-114">Streaming and Service Contracts</span></span>  

 <span data-ttu-id="8f7f5-115">При разработке контракта службы следует рассмотреть возможность потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-115">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="8f7f5-116">Если операция принимает или возвращает большой объем данных, необходимо рассмотреть возможность потоковой передачи этих данных во избежание выделения большого объема памяти для буферизации входных и выходных сообщений.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-116">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="8f7f5-117">Для потоковой передачи данных параметр, в котором содержатся эти данные, должен быть единственным параметром в сообщении.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-117">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="8f7f5-118">Например, если требуется выполнить потоковую передачу входного сообщения, операция должна иметь точно один входной параметр.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-118">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="8f7f5-119">Аналогично, если требуется выполнить потоковую передачу выходного сообщения, операция должна иметь точно один выходной параметр или возвращать значение.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-119">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="8f7f5-120">В обоих случаях параметр или тип возвращаемого значения должны являться объектами `Stream`, `Message` или `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-120">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="8f7f5-121">Ниже приведен контракт службы, использованный в данном образце потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-121">The following is the service contract used in this streaming sample.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="8f7f5-122">Операция `GetStream` получает некоторые буферизуемые входные данные в качестве строки и возвращает объект `Stream`, который является потоковым.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-122">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="8f7f5-123">И наоборот, `UploadStream` принимает объект `Stream` (потоковый) и возвращает объект `bool` (буферизованный).</span><span class="sxs-lookup"><span data-stu-id="8f7f5-123">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="8f7f5-124">`EchoStream` принимает и возвращает объект `Stream` и является примером операции, в которой как входное, так и выходное сообщения являются потоковыми.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-124">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="8f7f5-125">Наконец, `GetReversedStream` не принимает никакие данные и возвращает объект `Stream` (потоковый).</span><span class="sxs-lookup"><span data-stu-id="8f7f5-125">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="8f7f5-126">Включение потоковой передачи</span><span class="sxs-lookup"><span data-stu-id="8f7f5-126">Enabling Streamed Transfers</span></span>  

 <span data-ttu-id="8f7f5-127">Такое определение контрактов операций, какое описано выше, обеспечивает потоковую передачу на уровне модели программирования.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-127">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="8f7f5-128">Если этим ограничиться, транспорт все равно выполняет буферизацию всего содержимого сообщения.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-128">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="8f7f5-129">Чтобы обеспечить потоковую передачу на уровне транспорта, выберите режим передачи в элементе привязки транспорта.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-129">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="8f7f5-130">Свойству `TransferMode` элемента привязки можно присвоить значение `Buffered`, `Streamed`, `StreamedRequest` или `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-130">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="8f7f5-131">Если режиму передачи присвоено значение `Streamed`, потоковая передача будет выполняться в обоих направлениях.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-131">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="8f7f5-132">Если режиму передачи присвоено значение `StreamedRequest` или `StreamedResponse`, потоковая передача будет выполняться только в направлении запроса или ответа, соответственно.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-132">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="8f7f5-133">Привязка `basicHttpBinding` предоставляет свойство `TransferMode` в привязке, как и привязки `NetTcpBinding` и `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-133">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="8f7f5-134">Для других транспортов необходимо создать пользовательскую привязку для задания режима передачи.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-134">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="8f7f5-135">В следующем коде конфигурации из образца показано задание для свойства `TransferMode` значения потоковой передачи в привязке `basicHttpBinding` и пользовательской привязке HTTP:</span><span class="sxs-lookup"><span data-stu-id="8f7f5-135">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="8f7f5-136">Помимо задания для свойства `transferMode` значения `Streamed`, предыдущий код конфигурации задает для свойства `maxReceivedMessageSize` значение 64 МБ.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-136">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="8f7f5-137">В качестве защитного механизма свойство `maxReceivedMessageSize` определяет допустимый максимальный размер принимаемых сообщений.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-137">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="8f7f5-138">По умолчанию для свойства `maxReceivedMessageSize` задано значение 64 КБ, которое обычно слишком мало для сценариев потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-138">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="8f7f5-139">Обработка данных во время потоковой передачи</span><span class="sxs-lookup"><span data-stu-id="8f7f5-139">Processing Data As It Is Streamed</span></span>  

 <span data-ttu-id="8f7f5-140">Операции `GetStream`, `UploadStream` и `EchoStream` выполняют передачу данных непосредственно из файла или сохранение полученных данных непосредственно в файл.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-140">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="8f7f5-141">Однако в некоторых случаях требуется отправлять или принимать большие объемы данных и выполнять обработку этих данных по частям во время передачи или приема.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-141">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="8f7f5-142">Одним из способов решения этой задачи является создание пользовательского потока (класса, наследующего от класса <xref:System.IO.Stream>), обрабатывающего данные по мере их чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-142">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="8f7f5-143">Операция `GetReversedStream` и класс `ReverseStream` являются примерами такого подхода.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-143">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="8f7f5-144">Метод `GetReversedStream` создает и возвращает новый экземпляр класса `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-144">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="8f7f5-145">Фактическая обработка происходит, когда система считывает данные из объекта `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-145">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="8f7f5-146">Реализация метода `ReverseStream.Read` считывает фрагмент байтов из исходного файла, обращает их, а затем возвращает обращенные байты.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-146">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="8f7f5-147">Этот метод не обращает все содержимое файла; он обращает один фрагмент байтов за раз.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-147">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="8f7f5-148">В этом примере показано, как можно выполнить потоковую обработку во время чтения или записи содержимого потока.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-148">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="8f7f5-149">Запуск примера</span><span class="sxs-lookup"><span data-stu-id="8f7f5-149">Running the Sample</span></span>  

 <span data-ttu-id="8f7f5-150">Для выполнении этого образца сначала постройте службу и клиент в соответствии с указаниями, приведенными в конце данного документа.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-150">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="8f7f5-151">Затем запустите службу и клиент в двух разных окнах консоли.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-151">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="8f7f5-152">После запуска клиента он ожидает, когда при готовности службы будет нажата клавиша ВВОД.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-152">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="8f7f5-153">Затем клиент вызывает методы `GetStream()`, `UploadStream()` и `GetReversedStream()` сначала по HTTP, а затем по TCP.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-153">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="8f7f5-154">Ниже приведен пример вывода службы, а затем пример вывода клиента:</span><span class="sxs-lookup"><span data-stu-id="8f7f5-154">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="8f7f5-155">Вывод службы:</span><span class="sxs-lookup"><span data-stu-id="8f7f5-155">Service Output:</span></span>  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="8f7f5-156">Вывод клиента:</span><span class="sxs-lookup"><span data-stu-id="8f7f5-156">Client Output:</span></span>  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8f7f5-157">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="8f7f5-157">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8f7f5-158">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8f7f5-158">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8f7f5-159">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8f7f5-159">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8f7f5-160">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8f7f5-160">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f7f5-161">Если для восстановления конфигурации этого образца используется программа Svcutil.exe, измените имя конечной точки в конфигурации клиента, чтобы оно соответствовало клиентскому коду.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-161">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8f7f5-162">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-162">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8f7f5-163">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="8f7f5-163">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8f7f5-164">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-164">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8f7f5-165">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="8f7f5-165">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
