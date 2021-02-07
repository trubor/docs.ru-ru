---
description: Дополнительные сведения см. в статье Использование стандартных конечных точек.
title: Использование стандартных конечных точек
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 804fdd84d3f6ff6f961aed81e8bd14cf8c43063c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685417"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="293cd-103">Использование стандартных конечных точек</span><span class="sxs-lookup"><span data-stu-id="293cd-103">Usage of Standard Endpoints</span></span>

<span data-ttu-id="293cd-104">Этот образец демонстрирует использование стандартных конечных точек в файлах конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="293cd-104">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="293cd-105">Стандартная конечная точка позволяет пользователю упростить определения конечных точек за счет использования единого свойства, описывающего комбинацию адреса, привязки и контракта вместе с дополнительными свойствами.</span><span class="sxs-lookup"><span data-stu-id="293cd-105">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="293cd-106">Данный образец демонстрирует определение и реализацию пользовательской стандартной конечной точки, а также определение конкретных свойств в конечной точке.</span><span class="sxs-lookup"><span data-stu-id="293cd-106">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="293cd-107">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="293cd-107">Sample Details</span></span>

<span data-ttu-id="293cd-108">Конечные точки службы могут быть заданы с использованием трех параметров: адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="293cd-108">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="293cd-109">Кроме того, можно задать и другие параметры - конфигурацию поведения, заголовки, URI прослушивания и т. д.</span><span class="sxs-lookup"><span data-stu-id="293cd-109">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="293cd-110">В некоторых случаях значения адресов, привязок или контрактов не могут меняться.</span><span class="sxs-lookup"><span data-stu-id="293cd-110">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="293cd-111">В такой ситуации можно воспользоваться стандартными конечными точками.</span><span class="sxs-lookup"><span data-stu-id="293cd-111">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="293cd-112">Среди примеров таких конечных точек - конечные точки обмена метаданными и конечные точки обнаружения.</span><span class="sxs-lookup"><span data-stu-id="293cd-112">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="293cd-113">Стандартные конечные точки также повышают удобство использования, позволяя конфигурировать конечные точки службы, не предоставляя сведений фиксированного характера и не создавая для них собственных стандартных конечных точек. Это дает возможность, например, повысить удобство использования, предоставляя разумный набор значений по умолчанию и тем самым сокращая количество строк в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="293cd-113">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="293cd-114">Данный образец состоит из двух проектов - службы, которая определяет две стандартных конечных точки, и клиента, который обращается к службе.</span><span class="sxs-lookup"><span data-stu-id="293cd-114">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="293cd-115">Метод определения стандартных конечных точек для этой службы в файле конфигурации показан в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="293cd-115">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="293cd-116">Первая конечная точка, определенная для службы, имеет тип `customEndpoint`, ее определение можно увидеть в разделе `<standardEndpoints>`, в котором свойству `property` задано значение `true`.</span><span class="sxs-lookup"><span data-stu-id="293cd-116">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="293cd-117">Это пример конечной точки, дополненной новым свойством.</span><span class="sxs-lookup"><span data-stu-id="293cd-117">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="293cd-118">Вторая конечная точка соответствует конечной точке метаданных, и значения адреса, привязки и контракта в ней фиксированы.</span><span class="sxs-lookup"><span data-stu-id="293cd-118">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="293cd-119">Для определения элемента стандартной конечной точки необходимо создать класс, производный от класса `StandardEndpointElement`.</span><span class="sxs-lookup"><span data-stu-id="293cd-119">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="293cd-120">В нашем образце класс `CustomEndpointElement` определен, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="293cd-120">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

<span data-ttu-id="293cd-121">В функции `CreateServiceEndpoint` создается объект `CustomEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="293cd-121">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="293cd-122">Его определение показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="293cd-122">Its definition is shown in the following example:</span></span>

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 <span data-ttu-id="293cd-123">Чтобы осуществить сообщение между службой и клиентом, в клиенте, обращающемся к службе, создается ссылка на службу.</span><span class="sxs-lookup"><span data-stu-id="293cd-123">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="293cd-124">Когда образец построен и запущен, запускается и служба, и клиент сообщается с ней.</span><span class="sxs-lookup"><span data-stu-id="293cd-124">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="293cd-125">Обратите внимание, что ссылку на службу следует обновлять при каждом изменении службы.</span><span class="sxs-lookup"><span data-stu-id="293cd-125">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="293cd-126">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="293cd-126">To use this sample</span></span>

1. <span data-ttu-id="293cd-127">С помощью Visual Studio 2012 откройте файл Стандардендпоинтс. sln.</span><span class="sxs-lookup"><span data-stu-id="293cd-127">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="293cd-128">Разрешите запуск нескольких проектов.</span><span class="sxs-lookup"><span data-stu-id="293cd-128">Enable multiple projects to start up.</span></span>

    1. <span data-ttu-id="293cd-129">В **Обозреватель решений** щелкните правой кнопкой мыши решение стандартные конечные точки и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="293cd-129">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2. <span data-ttu-id="293cd-130">В окне **Общие свойства** выберите **запускаемый проект** и щелкните **Несколько запускаемых проектов**.</span><span class="sxs-lookup"><span data-stu-id="293cd-130">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3. <span data-ttu-id="293cd-131">Переместите проект службы в начало списка, указав для параметра **действие** значение **Запуск**.</span><span class="sxs-lookup"><span data-stu-id="293cd-131">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4. <span data-ttu-id="293cd-132">Переместите проект клиента после проекта службы, а также задайте для параметра **действие** значение **Запуск**.</span><span class="sxs-lookup"><span data-stu-id="293cd-132">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="293cd-133">Это указывает, что проект «Client» выполняется после проекта «Service».</span><span class="sxs-lookup"><span data-stu-id="293cd-133">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="293cd-134">Чтобы запустить решение, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="293cd-134">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="293cd-135">Если эти действия не работают, убедитесь, что среда настроена правильно, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="293cd-135">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="293cd-136">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="293cd-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="293cd-137">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="293cd-137">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="293cd-138">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [Запуск примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="293cd-138">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="293cd-139">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="293cd-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="293cd-140">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="293cd-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="293cd-141">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="293cd-141">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="293cd-142">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="293cd-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
