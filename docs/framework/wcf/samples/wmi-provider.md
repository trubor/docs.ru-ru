---
description: 'Дополнительные сведения: поставщик WMI'
title: Поставщик WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 23d673f55781204fb4ce54d7d8ee0dab7933484f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715097"
---
# <a name="wmi-provider"></a><span data-ttu-id="25ef4-103">Поставщик WMI</span><span class="sxs-lookup"><span data-stu-id="25ef4-103">WMI Provider</span></span>

<span data-ttu-id="25ef4-104">В этом примере показано, как собирать данные из служб Windows Communication Foundation (WCF) во время выполнения с помощью поставщика инструментарий управления Windows (WMI) (WMI), встроенного в WCF.</span><span class="sxs-lookup"><span data-stu-id="25ef4-104">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="25ef4-105">Кроме того, в образце показано, как добавлять в службу пользовательский объект инструментария WMI.</span><span class="sxs-lookup"><span data-stu-id="25ef4-105">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="25ef4-106">В примере активируется поставщик WMI для [Начало работы](getting-started-sample.md) и демонстрируется сбор данных из `ICalculator` службы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="25ef4-106">The sample activates the WMI provider for the [Getting Started](getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="25ef4-107">Инструментарий WMI - это реализованный корпорацией Майкрософт стандарт управления предприятием через Интернет (WBEM).</span><span class="sxs-lookup"><span data-stu-id="25ef4-107">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="25ef4-108">Дополнительные сведения о пакете SDK для инструментария WMI см. в разделе [инструментарий управления Windows (WMI)](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="25ef4-108">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="25ef4-109">WBEM является отраслевым стандартом предоставления приложениями инструментария управления для внешних средств управления.</span><span class="sxs-lookup"><span data-stu-id="25ef4-109">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="25ef4-110">WCF реализует поставщик WMI, компонент, который предоставляет инструментирование во время выполнения через интерфейс, совместимый с WBEM.</span><span class="sxs-lookup"><span data-stu-id="25ef4-110">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="25ef4-111">Средства управления могут подключаться к службам через интерфейс во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="25ef4-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="25ef4-112">WCF предоставляет атрибуты служб, такие как адреса, привязки, поведения и прослушиватели.</span><span class="sxs-lookup"><span data-stu-id="25ef4-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="25ef4-113">Встроенный поставщик инструментария WMI активируется в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="25ef4-113">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="25ef4-114">Это делается с помощью `wmiProviderEnabled` атрибута [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) в [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) разделе, как показано в следующем образце конфигурации:</span><span class="sxs-lookup"><span data-stu-id="25ef4-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="25ef4-115">Эта запись конфигурации предоставляет интерфейс инструментария WMI.</span><span class="sxs-lookup"><span data-stu-id="25ef4-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="25ef4-116">Теперь приложения управления могут подключаться через этот интерфейс и обращаться к инструментарию управления приложения.</span><span class="sxs-lookup"><span data-stu-id="25ef4-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="25ef4-117">Пользовательский объект WMI</span><span class="sxs-lookup"><span data-stu-id="25ef4-117">Custom WMI Object</span></span>  

 <span data-ttu-id="25ef4-118">Добавление в службу объектов WMI позволяет предоставлять доступ к пользовательским сведениям, а также к сведениям встроенного поставщика WMI.</span><span class="sxs-lookup"><span data-stu-id="25ef4-118">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="25ef4-119">Для этого необходимо опубликовать схему службы в инструментарии WMI с помощью приложения Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="25ef4-119">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="25ef4-120">Соответствующие инструкции, а также более подробные сведения, см в инструкция по установке в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="25ef4-120">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="25ef4-121">Доступ к сведениям WMI</span><span class="sxs-lookup"><span data-stu-id="25ef4-121">Accessing WMI Information</span></span>  

<span data-ttu-id="25ef4-122">Доступ к данным инструментария WMI может осуществляться несколькими различными способами.</span><span class="sxs-lookup"><span data-stu-id="25ef4-122">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="25ef4-123">Корпорация Майкрософт предоставляет API-интерфейсы WMI для сценариев, Visual Basic приложений, приложений C++ и платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25ef4-123">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="25ef4-124">Дополнительные сведения см. [в разделе Использование WMI](/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="25ef4-124">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="25ef4-125">В этом образце используется два скрипта Java: один - для перечисления выполняющихся на компьютере служб и некоторых их свойств, а второй - для просмотра пользовательских данных инструментария WMI.</span><span class="sxs-lookup"><span data-stu-id="25ef4-125">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="25ef4-126">Скрипт открывает подключение к поставщику инструментария WMI, анализирует данные и отображает собранные данные.</span><span class="sxs-lookup"><span data-stu-id="25ef4-126">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="25ef4-127">Запустите пример, чтобы создать запущенный экземпляр службы WCF.</span><span class="sxs-lookup"><span data-stu-id="25ef4-127">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="25ef4-128">Во время работы службы выполните каждый из скриптов Java с помощью следующей команды командной строки:</span><span class="sxs-lookup"><span data-stu-id="25ef4-128">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="25ef4-129">Этот скрипт обращается к хранящемуся в службе инструментированию и создает следующий результат:</span><span class="sxs-lookup"><span data-stu-id="25ef4-129">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```console  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 <span data-ttu-id="25ef4-130">Затем выполните второй скрипт Java, чтобы отобразить пользовательские данные WMI:</span><span class="sxs-lookup"><span data-stu-id="25ef4-130">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="25ef4-131">Этот скрипт обращается к хранящемуся в службах пользовательскому инструментированию и создает следующий результат:</span><span class="sxs-lookup"><span data-stu-id="25ef4-131">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="25ef4-132">Сценарий показывает, что на компьютере запущена одна служба.</span><span class="sxs-lookup"><span data-stu-id="25ef4-132">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="25ef4-133">Служба предоставляет одну конечную точку, реализующую контракт `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="25ef4-133">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="25ef4-134">Параметры поведения и привязки, реализуемых конечной точкой, задаются в виде отдельных элементов стека обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="25ef4-134">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="25ef4-135">Инструментарий WMI не ограничивается предоставлением инструментария управления инфраструктуры WCF.</span><span class="sxs-lookup"><span data-stu-id="25ef4-135">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="25ef4-136">Приложение может предоставлять собственные относящиеся к домену элементы данных, используя для этого такой же механизм.</span><span class="sxs-lookup"><span data-stu-id="25ef4-136">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="25ef4-137">Инструментарий WMI представляет собой единый механизм для контроля веб-службы и управления ею.</span><span class="sxs-lookup"><span data-stu-id="25ef4-137">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="25ef4-138">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="25ef4-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="25ef4-139">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25ef4-139">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="25ef4-140">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25ef4-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="25ef4-141">Опубликуйте схему служб в WMI, запустив программу InstallUtil.exe (по умолчанию файл InstallUtil.exe расположен в папке «%WINDIR%\Microsoft.NET\Framework\v4.0.30319») для файла service.dll в каталоге размещения.</span><span class="sxs-lookup"><span data-stu-id="25ef4-141">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="25ef4-142">Эту операцию нужно выполнять только в том случае, если в файл service.dll были внесены изменения.</span><span class="sxs-lookup"><span data-stu-id="25ef4-142">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="25ef4-143">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25ef4-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="25ef4-144">Если вы установили WCF после установки ASP.NET, может потребоваться выполнить команду "% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe "-r-x предоставить учетной записи ASPNET разрешение на публикацию объектов WMI.</span><span class="sxs-lookup"><span data-stu-id="25ef4-144">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="25ef4-145">Для просмотра данных из образцов, доступных через WMI, следует воспользоваться командами: `cscript EnumerateServices.js` или `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="25ef4-145">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="25ef4-146">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="25ef4-146">The samples may already be installed on your computer.</span></span> <span data-ttu-id="25ef4-147">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="25ef4-147">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="25ef4-148">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="25ef4-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="25ef4-149">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="25ef4-149">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="25ef4-150">См. также</span><span class="sxs-lookup"><span data-stu-id="25ef4-150">See also</span></span>

- <span data-ttu-id="25ef4-151">[Образцы наблюдения за AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="25ef4-151">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
