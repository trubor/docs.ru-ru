---
description: 'Дополнительные сведения о: помощью канала NamedPipe Activation'
title: Активация NamedPipe
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 4955511f24d831f4aa9e3aa67fdb3f6a218d7af0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752227"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="a4e93-103">Активация NamedPipe</span><span class="sxs-lookup"><span data-stu-id="a4e93-103">NamedPipe Activation</span></span>

<span data-ttu-id="a4e93-104">Этот пример демонстрирует размещение службы, которая использует службу активации Windows (WAS), чтобы активировать службу, которая взаимодействует через именованные каналы.</span><span class="sxs-lookup"><span data-stu-id="a4e93-104">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="a4e93-105">Этот пример основан на [Начало работы](getting-started-sample.md) и требует запуска Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="a4e93-105">This sample is based on the [Getting Started](getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="a4e93-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="a4e93-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4e93-107">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="a4e93-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a4e93-108">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="a4e93-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a4e93-109">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="a4e93-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a4e93-110">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="a4e93-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="a4e93-111">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="a4e93-111">Sample Details</span></span>

<span data-ttu-id="a4e93-112">Пример содержит консольную программу клиента (EXE) и библиотеку службы (DLL), размещаемую в рабочем процессе, активируемом службой активации процесса Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="a4e93-112">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="a4e93-113">Действия клиента отображаются в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="a4e93-113">Client activity is visible in the console window.</span></span>

<span data-ttu-id="a4e93-114">Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="a4e93-114">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="a4e93-115">Контракт определяется интерфейсом `ICalculator`, который предоставляет математические операции (сложить, вычесть, умножить и разделить), как это показано ниже в образце кода.</span><span class="sxs-lookup"><span data-stu-id="a4e93-115">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
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
}
```

<span data-ttu-id="a4e93-116">Клиент осуществляет синхронные вызовы заданной математической операции, а реализация службы вычисляет и возвращает соответствующий результат.</span><span class="sxs-lookup"><span data-stu-id="a4e93-116">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="a4e93-117">Образец использует изменяемую привязку `netNamedPipeBinding` без использования безопасности.</span><span class="sxs-lookup"><span data-stu-id="a4e93-117">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="a4e93-118">Привязка задается в файлах конфигурации для клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="a4e93-118">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="a4e93-119">Тип привязки для службы задается в атрибуте `binding` элемента конечной точки, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a4e93-119">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="a4e93-120">Если требуется использовать безопасную привязку именованного канала, измените настройку режима безопасности для требуемого параметра безопасности и снова запустите svcutil.exe на клиенте, чтобы получить обновленный файл конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="a4e93-120">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
        </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="a4e93-121">Информация конечной точки клиента настраивается, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="a4e93-121">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="a4e93-122">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="a4e93-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a4e93-123">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="a4e93-123">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a4e93-124">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="a4e93-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a4e93-125">Убедитесь, что установлен сервер IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="a4e93-125">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="a4e93-126">Для активации WAS требуется IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="a4e93-126">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="a4e93-127">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4e93-127">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="a4e93-128">Кроме того, необходимо установить компоненты активации WCF, отличные от HTTP:</span><span class="sxs-lookup"><span data-stu-id="a4e93-128">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="a4e93-129">В меню **Пуск** выберите **Панель управления**.</span><span class="sxs-lookup"><span data-stu-id="a4e93-129">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="a4e93-130">Выберите **программы и компоненты**.</span><span class="sxs-lookup"><span data-stu-id="a4e93-130">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="a4e93-131">Щелкните **Включение или отключение компонентов Windows**.</span><span class="sxs-lookup"><span data-stu-id="a4e93-131">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="a4e93-132">Разверните узел **Microsoft .NET Framework 3,0** и установите флажок **Windows Communication Foundation активации, отличной от HTTP** .</span><span class="sxs-lookup"><span data-stu-id="a4e93-132">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="a4e93-133">Настройка службы активации Windows (WAS) для поддержки активации именованных каналов.</span><span class="sxs-lookup"><span data-stu-id="a4e93-133">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="a4e93-134">Для удобства два нижеописанных действия выполняются в пакетном файле AddNetPipeSiteBinding.cmd, расположенном в каталоге с примерами.</span><span class="sxs-lookup"><span data-stu-id="a4e93-134">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="a4e93-135">Чтобы поддерживать активацию по net.pipe, веб-узел по умолчанию должен прежде быть привязан к протоколу net.pipe.</span><span class="sxs-lookup"><span data-stu-id="a4e93-135">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="a4e93-136">Сделать это позволяет файл Appcmd.exe, который устанавливается с помощью набора инструментов управления IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="a4e93-136">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="a4e93-137">В командной строке с повышенными привилегиями (с правами администратора) выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="a4e93-137">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="a4e93-138">Эта команда представляет собой одну строку текста.</span><span class="sxs-lookup"><span data-stu-id="a4e93-138">This command is a single line of text.</span></span>

        <span data-ttu-id="a4e93-139">Эта команда добавит для веб-сайта по умолчанию привязку сайта к протоколу net.pipe.</span><span class="sxs-lookup"><span data-stu-id="a4e93-139">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="a4e93-140">Несмотря на то что все приложения в узле имеют общую привязку к протоколу net.pipe, включать поддержку net.pipe можно для каждого приложения отдельно.</span><span class="sxs-lookup"><span data-stu-id="a4e93-140">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="a4e93-141">Чтобы включить протокол net.pipe для приложения /servicemodelsamples, необходимо выполнить следующую команду из командной строки с повышенными привилегиями.</span><span class="sxs-lookup"><span data-stu-id="a4e93-141">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="a4e93-142">Эта команда представляет собой одну строку текста.</span><span class="sxs-lookup"><span data-stu-id="a4e93-142">This command is a single line of text.</span></span>

        <span data-ttu-id="a4e93-143">Эта команда позволяет получить доступ к приложению/сервицемоделсамплес с помощью `http://localhost/servicemodelsamples` и `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="a4e93-143">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="a4e93-144">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4e93-144">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="a4e93-145">Удалите привязку узла к протоколу net.pipe, добавленную ранее для этого образца.</span><span class="sxs-lookup"><span data-stu-id="a4e93-145">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="a4e93-146">Для удобства выполняются два следующих действия в пакетном файле RemoveNetPipeSiteBinding.cmd, расположенном в каталоге с образцами.</span><span class="sxs-lookup"><span data-stu-id="a4e93-146">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="a4e93-147">Удалите протокол net.tcp из списка включенных протоколов, выполнив следующую команду из командной строки с повышенными привилегиями.</span><span class="sxs-lookup"><span data-stu-id="a4e93-147">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="a4e93-148">Эта команда вводится как одна строка текста.</span><span class="sxs-lookup"><span data-stu-id="a4e93-148">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="a4e93-149">Удалите привязку узла к протоколу net.tcp, выполнив следующую команду из командной строки с повышенными привилегиями.</span><span class="sxs-lookup"><span data-stu-id="a4e93-149">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="a4e93-150">Эта команда должна вводиться как одна строка текста.</span><span class="sxs-lookup"><span data-stu-id="a4e93-150">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4e93-151">См. также</span><span class="sxs-lookup"><span data-stu-id="a4e93-151">See also</span></span>

- <span data-ttu-id="a4e93-152">[Образцы размещения и сохраняемости AppFabric](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a4e93-152">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
