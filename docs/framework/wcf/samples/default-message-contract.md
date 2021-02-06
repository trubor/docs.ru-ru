---
description: 'Дополнительные сведения: контракт сообщения по умолчанию'
title: Контракт сообщения по умолчанию
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 3587f6ce81e085a4915af8162f8d76aed30bf8df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632091"
---
# <a name="default-message-contract"></a><span data-ttu-id="bea7d-103">Контракт сообщения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="bea7d-103">Default Message Contract</span></span>

<span data-ttu-id="bea7d-104">Образец контракта сообщения по умолчанию демонстрирует службу, в которой пользовательское сообщение, определенное пользователем, передается в операции службы и из операций службы.</span><span class="sxs-lookup"><span data-stu-id="bea7d-104">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="bea7d-105">Этот пример основан на [Начало работы](getting-started-sample.md) , который реализует интерфейс калькулятора как типизированную службу.</span><span class="sxs-lookup"><span data-stu-id="bea7d-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="bea7d-106">Вместо отдельных операций службы для сложения, вычитания, умножения и деления, используемого в [Начало работы](getting-started-sample.md), этот пример передает пользовательское сообщение, которое содержит операнды и оператор, и возвращает результат арифметического вычисления.</span><span class="sxs-lookup"><span data-stu-id="bea7d-106">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="bea7d-107">Клиентом является консольное приложение (EXE), а библиотека службы (DLL) размещается в службах Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="bea7d-107">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="bea7d-108">Действия клиента отображаются в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="bea7d-108">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bea7d-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="bea7d-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bea7d-110">В этой службе определена единственная операция службы, которая принимает и возвращает пользовательские сообщения типа `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="bea7d-110">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="bea7d-111">Хотя в этом образце сообщения запроса и ответа имеют одинаковый тип, при необходимости они, конечно, могут быть различными контрактами сообщений.</span><span class="sxs-lookup"><span data-stu-id="bea7d-111">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="bea7d-112">Пользовательское сообщение `MyMessage` определено в классе, аннотированном атрибутами <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> и <xref:System.ServiceModel.MessageBodyMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bea7d-112">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="bea7d-113">В этом образце используется только третий конструктор.</span><span class="sxs-lookup"><span data-stu-id="bea7d-113">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="bea7d-114">Использование контрактов сообщений обеспечивает полное управление сообщением SOAP.</span><span class="sxs-lookup"><span data-stu-id="bea7d-114">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="bea7d-115">В этом образце атрибут <xref:System.ServiceModel.MessageHeaderAttribute> используется для помещения параметра `Operation` в заголовок SOAP.</span><span class="sxs-lookup"><span data-stu-id="bea7d-115">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="bea7d-116">Операнды `N1`, `N2` и `Result` помещаются в тело сообщения SOAP, так как к ним применен атрибут <xref:System.ServiceModel.MessageBodyMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bea7d-116">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="bea7d-117">Класс реализации содержит код для операции службы `Calculate`.</span><span class="sxs-lookup"><span data-stu-id="bea7d-117">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="bea7d-118">Класс `CalculateService` получает операнды и оператор из сообщения запроса и создает ответное сообщение, содержащее результаты запрошенного вычисления, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="bea7d-118">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="bea7d-119">Созданный клиентский код для клиента был создан с помощью средства [служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="bea7d-119">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="bea7d-120">При необходимости это средство автоматически создает типы контрактов сообщений в создаваемом коде клиента.</span><span class="sxs-lookup"><span data-stu-id="bea7d-120">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="bea7d-121">Можно указать параметр команды `/messageContract`, чтобы принудительно создавать контракты сообщений.</span><span class="sxs-lookup"><span data-stu-id="bea7d-121">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="bea7d-122">В следующем образце кода показан клиент, использующий сообщение `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="bea7d-122">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage()
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="bea7d-123">При выполнении образца ход вычислений отображается в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="bea7d-123">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="bea7d-124">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="bea7d-124">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="bea7d-125">На этом этапе пользовательские сообщения, определенные пользователем, передаются между клиентом и операцией службы.</span><span class="sxs-lookup"><span data-stu-id="bea7d-125">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="bea7d-126">Контракт сообщений определяет, что операнды и результаты находятся в теле сообщения, а оператор - в заголовке сообщения.</span><span class="sxs-lookup"><span data-stu-id="bea7d-126">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="bea7d-127">Для наблюдения за этой структурой сообщений можно настроить ведение журнала сообщений.</span><span class="sxs-lookup"><span data-stu-id="bea7d-127">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bea7d-128">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="bea7d-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bea7d-129">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bea7d-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bea7d-130">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bea7d-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="bea7d-131">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bea7d-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bea7d-132">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="bea7d-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bea7d-133">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="bea7d-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bea7d-134">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="bea7d-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bea7d-135">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="bea7d-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
