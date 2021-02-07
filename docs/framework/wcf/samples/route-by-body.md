---
description: 'Дополнительные сведения: Маршрутизация по телу'
title: Маршрутизация по телу сообщения
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 1c9505484c4af34c5e1f2f98524c01fb378c005f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703787"
---
# <a name="route-by-body"></a><span data-ttu-id="c8b48-103">Маршрутизация по телу сообщения</span><span class="sxs-lookup"><span data-stu-id="c8b48-103">Route by Body</span></span>

<span data-ttu-id="c8b48-104">В этом образце показано, как реализовать службу, которая принимает объекты сообщений с действием SOAP.</span><span class="sxs-lookup"><span data-stu-id="c8b48-104">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="c8b48-105">Этот образец основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="c8b48-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="c8b48-106">Служба реализует одну операцию `Calculate`, которая принимает параметр запроса <xref:System.ServiceModel.Channels.Message> и возвращает ответ <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="c8b48-106">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="c8b48-107">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="c8b48-107">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8b48-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="c8b48-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c8b48-109">Этот образец демонстрирует диспетчеризацию сообщений на основе содержимого тела сообщения.</span><span class="sxs-lookup"><span data-stu-id="c8b48-109">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="c8b48-110">Встроенный механизм диспетчеризации сообщений модели служб Windows Communication Foundation (WCF) основан на действиях с сообщениями.</span><span class="sxs-lookup"><span data-stu-id="c8b48-110">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="c8b48-111">Однако есть много существующих веб-служб, которые для всех своих операций определяют параметр Action="".</span><span class="sxs-lookup"><span data-stu-id="c8b48-111">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="c8b48-112">Невозможно построить службу на основе кода WSDL, когда диспетчеризация сообщений запросов осуществляется на основе параметра Action.</span><span class="sxs-lookup"><span data-stu-id="c8b48-112">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="c8b48-113">В этом образце показан контракт службы, основанный на коде WSDL (код WSDL содержится в файле Service.wsdl, который входит в этот образец).</span><span class="sxs-lookup"><span data-stu-id="c8b48-113">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="c8b48-114">Контракт службы — это калькулятор, аналогичный тому, который используется в [Начало работы](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c8b48-114">The service contract is Calculator, similar to the one used in [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="c8b48-115">Однако контракт `[OperationContract]` задает для всех операций `Action=""`.</span><span class="sxs-lookup"><span data-stu-id="c8b48-115">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="c8b48-116">Чтобы при таком контракте можно было распределять сообщения между операциями, службе требуется пользовательское поведение диспетчеризации `DispatchByBodyBehavior`.</span><span class="sxs-lookup"><span data-stu-id="c8b48-116">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="c8b48-117">Это поведение диспетчеризации инициализирует `DispatchByBodyElementOperationSelector` селектор настраиваемых операций с таблицей имен операций, ключом которых является QName соответствующих элементов оболочки.</span><span class="sxs-lookup"><span data-stu-id="c8b48-117">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="c8b48-118">Операция `DispatchByBodyElementOperationSelector` проверяет начальный тег первого дочернего элемента Body и выбирает операцию, используя упомянутую ранее таблицу.</span><span class="sxs-lookup"><span data-stu-id="c8b48-118">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="c8b48-119">Клиент использует автоматически созданный прокси-сервер из WSDL-документа, экспортированного службой с помощью [средства служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c8b48-119">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="c8b48-120">Тот факт, что параметры Action всех операций пусты, не влияет на клиентский код, не считая параметров Action автоматически созданного прокси.</span><span class="sxs-lookup"><span data-stu-id="c8b48-120">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="c8b48-121">Клиентский код выполняет несколько вычислений.</span><span class="sxs-lookup"><span data-stu-id="c8b48-121">The client code performs several calculations.</span></span> <span data-ttu-id="c8b48-122">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="c8b48-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c8b48-123">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="c8b48-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c8b48-124">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="c8b48-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c8b48-125">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8b48-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c8b48-126">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8b48-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c8b48-127">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8b48-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c8b48-128">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c8b48-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8b48-129">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="c8b48-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c8b48-130">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="c8b48-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8b48-131">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="c8b48-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
