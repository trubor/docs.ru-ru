---
description: 'Подробнее: заголовки адресов'
title: Заголовки адресов
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: a0b421776e1b6b792fa237e0cd65f9686198194e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779196"
---
# <a name="address-headers"></a><span data-ttu-id="c8138-103">Заголовки адресов</span><span class="sxs-lookup"><span data-stu-id="c8138-103">Address Headers</span></span>

<span data-ttu-id="c8138-104">В образце заголовков адреса показано, как клиенты могут передавать ссылочные параметры службе с помощью Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c8138-104">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="c8138-105">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="c8138-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="c8138-106">Спецификация WS-Addressing определяет понятие ссылки на конечную точку как способа обращения к определенной конечной точке веб-службы.</span><span class="sxs-lookup"><span data-stu-id="c8138-106">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="c8138-107">В WCF ссылки на конечные точки моделируются с помощью `EndpointAddress` класса класс — `EndpointAddress` это тип поля адреса `ServiceEndpoint` класса.</span><span class="sxs-lookup"><span data-stu-id="c8138-107">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="c8138-108">Особенностью модели ссылки на конечную точку является то, что каждая ссылка может содержать несколько ссылочных параметров, которые добавляют дополнительные идентификационные сведения.</span><span class="sxs-lookup"><span data-stu-id="c8138-108">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="c8138-109">В WCF эти ссылочные параметры моделируются как экземпляры `AddressHeader` класса.</span><span class="sxs-lookup"><span data-stu-id="c8138-109">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="c8138-110">В этом образце клиент добавляет ссылочный параметр в `EndpointAddress` конечной точки клиента.</span><span class="sxs-lookup"><span data-stu-id="c8138-110">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="c8138-111">Служба ищет этот ссылочный параметр и использует его значение в логике операции службы "Привет".</span><span class="sxs-lookup"><span data-stu-id="c8138-111">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="c8138-112">Клиент</span><span class="sxs-lookup"><span data-stu-id="c8138-112">Client</span></span>

<span data-ttu-id="c8138-113">Чтобы клиент мог отправить ссылочный параметр, он должен добавить заголовок `AddressHeader` в адрес `EndpointAddress` конечной точки `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="c8138-113">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="c8138-114">Поскольку класс `EndpointAddress` является неизменным, изменение адреса конечной точки необходимо выполнить с помощью класса `EndpointAddressBuilder`.</span><span class="sxs-lookup"><span data-stu-id="c8138-114">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="c8138-115">В следующем коде клиент инициализируется для отправки ссылочного параметра как часть сообщения.</span><span class="sxs-lookup"><span data-stu-id="c8138-115">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="c8138-116">Код создает `EndpointAddressBuilder` с использованием исходного `EndpointAddress` в качестве первоначального значения.</span><span class="sxs-lookup"><span data-stu-id="c8138-116">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="c8138-117">Затем он добавляет только что созданный заголовок адреса. вызов метода `CreateAddressHeader` создает заголовок с определенным именем, пространством имен и значением.</span><span class="sxs-lookup"><span data-stu-id="c8138-117">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="c8138-118">В этом случае значением является "John".</span><span class="sxs-lookup"><span data-stu-id="c8138-118">Here the value is "John".</span></span> <span data-ttu-id="c8138-119">После добавления заголовка в конструктор метод `ToEndpointAddress()` преобразовывает (изменяемый) конструктор назад в (неизменяемый) адрес конечной точки, который снова присваивается полю адреса конечной точки клиента.</span><span class="sxs-lookup"><span data-stu-id="c8138-119">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="c8138-120">Теперь при вызове `Console.WriteLine(client.Hello());` клиентом служба может получить значение этого параметра адреса, как показано в результирующих выходных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="c8138-120">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="c8138-121">Сервер</span><span class="sxs-lookup"><span data-stu-id="c8138-121">Server</span></span>

<span data-ttu-id="c8138-122">Реализация операции службы `Hello()` использует текущий `OperationContext` для проверки значений заголовков входящего сообщения.</span><span class="sxs-lookup"><span data-stu-id="c8138-122">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

```csharp
string id = null;
// look at headers on incoming message
for (int i = 0;
     i < OperationContext.Current.IncomingMessageHeaders.Count;
     ++i)
{
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];
    // for any reference parameters with the correct name & namespace
    if (h.IsReferenceParameter &&
        h.Name == IDName &&
        h.Namespace == IDNamespace)
    {
        // read the value of that header
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);
        id = xr.ReadElementContentAsString();
    }
}
return "Hello, " + id;
```

<span data-ttu-id="c8138-123">Код выполняет итерацию всех заголовков входящего сообщения, выполняя поиск заголовок, которые являются ссылочными параметрами с определенным именем.</span><span class="sxs-lookup"><span data-stu-id="c8138-123">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="c8138-124">При нахождении параметра он считывает значение параметра и сохраняет его в переменной "id".</span><span class="sxs-lookup"><span data-stu-id="c8138-124">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c8138-125">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="c8138-125">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c8138-126">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8138-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c8138-127">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8138-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="c8138-128">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8138-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8138-129">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c8138-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8138-130">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="c8138-130">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c8138-131">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="c8138-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8138-132">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="c8138-132">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
