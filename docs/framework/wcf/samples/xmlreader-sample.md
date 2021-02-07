---
description: Дополнительные сведения см. в примере XmlReader
title: Пример XmlReader
ms.date: 03/30/2017
helpviewer_keywords:
- XML Reader
ms.assetid: 60e5848d-7d9c-4ea5-bed9-22758c9ac16c
ms.openlocfilehash: 07e54c6f8ccfe36bc378bd8c839cd7dd7f6ecb42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668270"
---
# <a name="xmlreader-sample"></a><span data-ttu-id="cb12e-103">Пример XmlReader</span><span class="sxs-lookup"><span data-stu-id="cb12e-103">XmlReader Sample</span></span>

<span data-ttu-id="cb12e-104">Образец XmlReader демонстрирует обработку тела сообщения с помощью <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="cb12e-104">The XmlReader sample demonstrates the processing of a message body using an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="cb12e-105">Образец основан на [Начало работы](getting-started-sample.md), который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="cb12e-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="cb12e-106">Добавлена дополнительная операция службы `Sum`, которая принимает сообщение, содержащее массив складываемых значений.</span><span class="sxs-lookup"><span data-stu-id="cb12e-106">An additional service operation, `Sum`, has been added that accepts a message that contains an array of values to add together.</span></span> <span data-ttu-id="cb12e-107">Служба считывает сообщение с использованием <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="cb12e-107">The service reads the message using an <xref:System.Xml.XmlReader>.</span></span>

> [!NOTE]
> <span data-ttu-id="cb12e-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="cb12e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="cb12e-109">Интерфейс калькулятора включает в себя операцию службы с именем `Sum`, которая принимает параметр <xref:System.ServiceModel.Channels.Message>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="cb12e-109">The calculator interface includes a service operation named `Sum` that accepts a <xref:System.ServiceModel.Channels.Message> parameter, as shown in the following sample code.</span></span>

```csharp
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
    [OperationContract]
    Message Sum(Message message);
}
```

<span data-ttu-id="cb12e-110">Для обращения к операции `Sum` клиент сначала создает массив целых чисел, потом создает из этого массива сообщение, а затем вызывает метод `Sum` с использованием созданного сообщения, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="cb12e-110">The client accesses `Sum` by first creating an array of integer values, then creating a message from the array, and then calling the `Sum` method using the created message, as shown in the following sample code.</span></span>

```csharp
CalculatorClient client = new CalculatorClient();
//...

// Call the Sum service operation.
int[] values = { 1, 2, 3, 4, 5 };
using (new OperationContextScope(client.InnerChannel))
{
    Message request = Message.CreateMessage(OperationContext.Current.OutgoingMessageHeaders.MessageVersion, "http://Microsoft.ServiceModel.Samples/ICalculator/Sum", values);
    Message reply = client.Sum(request);
    int sum = reply.GetBody<int>();

    Console.WriteLine("Sum(1,2,3,4,5) = {0}", sum);
}
```

<span data-ttu-id="cb12e-111">В службе реализация операции службы `Sum` получает доступ к телу сообщения с помощью объекта <xref:System.Xml.XmlReader> для итерационной обработки суммируемых значений.</span><span class="sxs-lookup"><span data-stu-id="cb12e-111">In the service, the implementation of the service operation `Sum` accesses the message body using an <xref:System.Xml.XmlReader> object to iterate through the values to sum.</span></span> <span data-ttu-id="cb12e-112">Метод <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> вызывается для доступа к телу сообщения, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="cb12e-112">The <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> method is called to access the message body, as shown in the following sample code.</span></span>

```csharp
public int Sum(Message message)
{
    int sum = 0;
    string text = "";

    //The body of the message contains a list of numbers that are read
    //directly using an XmlReader.
    XmlReader body = message.GetReaderAtBodyContents ();
    while (body.Read())
    {
        text = body.ReadString().Trim();
        if (text.Length>0)
        {
            sum += Convert.ToInt32(text);
        }
    }
    body.Close();
    Message response = Message.CreateMessage(
       "http://Microsoft.ServiceModel.Samples/ICalculator/SumResponse",
       sum);
    return response;
}
```

<span data-ttu-id="cb12e-113">При выполнении образца запросы и отклики операции отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="cb12e-113">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="cb12e-114">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="cb12e-114">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Sum(1,2,3,4,5) = 15

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb12e-115">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="cb12e-115">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="cb12e-116">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb12e-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="cb12e-117">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb12e-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="cb12e-118">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb12e-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb12e-119">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="cb12e-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb12e-120">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="cb12e-120">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cb12e-121">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="cb12e-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb12e-122">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="cb12e-122">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\XmlReader`
