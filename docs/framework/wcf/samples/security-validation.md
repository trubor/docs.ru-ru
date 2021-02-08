---
description: Дополнительные сведения см. в статье Проверка безопасности.
title: Проверка безопасности
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: abca0dce154c82e3834b5ec577da9e53a3697338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793159"
---
# <a name="security-validation"></a><span data-ttu-id="45b2f-103">Проверка безопасности</span><span class="sxs-lookup"><span data-stu-id="45b2f-103">Security validation</span></span>

<span data-ttu-id="45b2f-104">Этот образец показывает, как с помощью пользовательского поведения проверять службы на компьютере на соответствие определенным условиям.</span><span class="sxs-lookup"><span data-stu-id="45b2f-104">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="45b2f-105">В этом образце службы проверяются с помощью пользовательского поведения путем сканирования каждой конечной точки службы и проверки, содержат ли они безопасные элементы привязки.</span><span class="sxs-lookup"><span data-stu-id="45b2f-105">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="45b2f-106">Этот образец основан на [Начало работы](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="45b2f-106">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45b2f-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="45b2f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="45b2f-108">Пользовательское поведение проверки конечной точки</span><span class="sxs-lookup"><span data-stu-id="45b2f-108">Endpoint Validation Custom Behavior</span></span>  

 <span data-ttu-id="45b2f-109">Добавив код пользователя в метод `Validate`, содержащийся в интерфейсе <xref:System.ServiceModel.Description.IServiceBehavior>, для службы или конечной точки можно создать пользовательское поведение, позволяющее выполнять определенные пользователем действия.</span><span class="sxs-lookup"><span data-stu-id="45b2f-109">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="45b2f-110">Следующий код служит для перебора в цикле всех конечных точек, содержащихся в службе, и поиска безопасных привязок в коллекциях привязок конечных точек.</span><span class="sxs-lookup"><span data-stu-id="45b2f-110">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="45b2f-111">При добавлении приведенного ниже кода в файл Web.config добавляется расширение поведения `serviceValidate` для распознавания службой.</span><span class="sxs-lookup"><span data-stu-id="45b2f-111">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>
    ...
</system.serviceModel>
```  
  
 <span data-ttu-id="45b2f-112">После того как расширение поведения добавлено в службу, можно добавить поведение `endpointValidate` в список поведений в файле Web.config и, таким образом, в службу.</span><span class="sxs-lookup"><span data-stu-id="45b2f-112">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="45b2f-113">Поведения и их расширения, добавленные в файл Web.config, применяют поведение к отдельным службам, а при добавлении в файл Machine.config поведение применяется ко всем службам, работающим на компьютере.</span><span class="sxs-lookup"><span data-stu-id="45b2f-113">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45b2f-114">При добавлении поведения во все службы предлагается перед внесением каких-либо изменений в файл Machine.config создать резервную копию этого файла.</span><span class="sxs-lookup"><span data-stu-id="45b2f-114">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="45b2f-115">Теперь запустите клиент, содержащийся в каталоге client\bin данного образца.</span><span class="sxs-lookup"><span data-stu-id="45b2f-115">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="45b2f-116">Создается исключение со следующим сообщением: "запрошенная служба http://localhost/servicemodelsamples/service.svc не может быть активирована".</span><span class="sxs-lookup"><span data-stu-id="45b2f-116">An exception is thrown with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="45b2f-117">Это ожидаемая ситуация, так как поведение проверки конечной точки считает конечную точку небезопасной и запрещает запуск службы.</span><span class="sxs-lookup"><span data-stu-id="45b2f-117">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="45b2f-118">Поведение также создает внутреннее исключение, которое описывает, какая конечная точка является небезопасной, и записывает сообщение в системную программу Просмотр событий, в раздел источника "System.ServiceModel 4.0.0.0", категория "WebHost".</span><span class="sxs-lookup"><span data-stu-id="45b2f-118">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="45b2f-119">В данном образце можно также включить трассировку в службе.</span><span class="sxs-lookup"><span data-stu-id="45b2f-119">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="45b2f-120">Это позволит конечному пользователю просматривать исключения, созданные поведением проверки конечных точек, открыв трассировки службы с помощью программы Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="45b2f-120">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
### <a name="view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="45b2f-121">Просмотр сообщений об исключениях при проверке конечной точки в Просмотр событий</span><span class="sxs-lookup"><span data-stu-id="45b2f-121">View failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="45b2f-122">Щелкните меню **Пуск** и выберите **выполнить...**.</span><span class="sxs-lookup"><span data-stu-id="45b2f-122">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="45b2f-123">Введите `eventvwr` и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="45b2f-123">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="45b2f-124">В окне Просмотр событий щелкните **приложение**.</span><span class="sxs-lookup"><span data-stu-id="45b2f-124">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="45b2f-125">Дважды щелкните недавно добавленное событие System. ServiceModel 4.0.0.0 в категории "WebHost" в окне **приложения** , чтобы просмотреть небезопасные сообщения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="45b2f-125">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="45b2f-126">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="45b2f-126">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="45b2f-127">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45b2f-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="45b2f-128">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45b2f-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="45b2f-129">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45b2f-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45b2f-130">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="45b2f-130">The samples may already be installed on your computer.</span></span> <span data-ttu-id="45b2f-131">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="45b2f-131">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="45b2f-132">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="45b2f-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45b2f-133">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="45b2f-133">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="45b2f-134">См. также</span><span class="sxs-lookup"><span data-stu-id="45b2f-134">See also</span></span>

- <span data-ttu-id="45b2f-135">[Образцы наблюдения за AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="45b2f-135">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
