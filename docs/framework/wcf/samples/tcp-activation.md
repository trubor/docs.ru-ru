---
description: 'Дополнительные сведения: Активация по TCP'
title: Активация TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: bfa98eff1bcab31df3e28d46e77d90456020507c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685638"
---
# <a name="tcp-activation"></a><span data-ttu-id="8c8af-103">Активация TCP</span><span class="sxs-lookup"><span data-stu-id="8c8af-103">TCP Activation</span></span>

<span data-ttu-id="8c8af-104">Этот образец демонстрирует размещение службы, использующей службу активации Windows (WAS) для активации службы, которая осуществляет взаимодействие по протоколу net.tcp.</span><span class="sxs-lookup"><span data-stu-id="8c8af-104">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="8c8af-105">Этот образец основан на [Начало работы](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8c8af-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8c8af-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="8c8af-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c8af-107">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8c8af-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8c8af-108">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="8c8af-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8c8af-109">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="8c8af-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8c8af-110">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="8c8af-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="8c8af-111">Пример содержит консольную программу клиента (EXE) и библиотеку службы (DLL), размещаемую в рабочем процессе, активируемом службой WAS.</span><span class="sxs-lookup"><span data-stu-id="8c8af-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="8c8af-112">Действия клиента отображаются в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="8c8af-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="8c8af-113">Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="8c8af-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8c8af-114">Контракт определяется интерфейсом `ICalculator`, который предоставляет математические операции (сложение, вычитание, умножение и деление), как показано ниже в образце кода:</span><span class="sxs-lookup"><span data-stu-id="8c8af-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

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

<span data-ttu-id="8c8af-115">Реализация службы выполняет вычисления и возвращает соответствующий результат:</span><span class="sxs-lookup"><span data-stu-id="8c8af-115">The service implementation calculates and returns the appropriate result:</span></span>

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

<span data-ttu-id="8c8af-116">В этом образце используется вариант привязки net.tcp с включенным совместным использованием порта TCP и отключенным механизмом безопасности.</span><span class="sxs-lookup"><span data-stu-id="8c8af-116">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="8c8af-117">Если требуется использовать безопасную привязку TCP, измените режим безопасности сервера на требуемое значение и снова запустите svcutil.exe на клиенте, чтобы получить обновленный файл конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="8c8af-117">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="8c8af-118">В следующем образце показана конфигурация для службы:</span><span class="sxs-lookup"><span data-stu-id="8c8af-118">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
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

<span data-ttu-id="8c8af-119">Конечная точка клиента настраивается так, как показано в следующем образце кода:</span><span class="sxs-lookup"><span data-stu-id="8c8af-119">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="8c8af-120">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="8c8af-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8c8af-121">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="8c8af-121">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8c8af-122">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="8c8af-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8c8af-123">Убедитесь, что установлен сервер IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="8c8af-123">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="8c8af-124">Для активации WAS требуется IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="8c8af-124">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="8c8af-125">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c8af-125">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="8c8af-126">Кроме того, необходимо установить компоненты активации WCF, отличные от HTTP:</span><span class="sxs-lookup"><span data-stu-id="8c8af-126">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="8c8af-127">В меню **Пуск** выберите **Панель управления**.</span><span class="sxs-lookup"><span data-stu-id="8c8af-127">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="8c8af-128">Выберите **программы и компоненты**.</span><span class="sxs-lookup"><span data-stu-id="8c8af-128">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="8c8af-129">Щелкните **Включение или отключение компонентов Windows**.</span><span class="sxs-lookup"><span data-stu-id="8c8af-129">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="8c8af-130">Разверните узел **Microsoft .NET Framework 3,0** и установите флажок **Windows Communication Foundation активации, отличной от HTTP** .</span><span class="sxs-lookup"><span data-stu-id="8c8af-130">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="8c8af-131">Настройте службу WAS на поддержку активации по протоколу TCP.</span><span class="sxs-lookup"><span data-stu-id="8c8af-131">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="8c8af-132">Для удобства два нижеописанных действия выполняются в пакетом файле AddNetTcpSiteBinding.cmd, расположенном в каталоге с образцами.</span><span class="sxs-lookup"><span data-stu-id="8c8af-132">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="8c8af-133">Для поддержки активации по net.tcp веб-узел по умолчанию необходимо сначала привязать к порту net.tcp.</span><span class="sxs-lookup"><span data-stu-id="8c8af-133">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="8c8af-134">Сделать это позволяет программа Appcmd.exe, которая устанавливается с набором инструментов управления IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="8c8af-134">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="8c8af-135">В командной строке с правами администратора выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8c8af-135">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="8c8af-136">Эта команда представляет собой одну строку текста.</span><span class="sxs-lookup"><span data-stu-id="8c8af-136">This command is a single line of text.</span></span> <span data-ttu-id="8c8af-137">Она добавляет привязку сайта к протоколу net.tcp в веб-сайт по умолчанию, ожидающий передачи данных по протоколу TCP на порту 808 с любым именем узла.</span><span class="sxs-lookup"><span data-stu-id="8c8af-137">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="8c8af-138">Несмотря на то что все приложения в узле имеют общую привязку к протоколу net.tcp, включать поддержку net.tcp можно для каждого приложения отдельно.</span><span class="sxs-lookup"><span data-stu-id="8c8af-138">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="8c8af-139">Для включения протокола net.tcp для приложения /servicemodelsample необходимо выполнить следующую команду из командной строки с правами администратора:</span><span class="sxs-lookup"><span data-stu-id="8c8af-139">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="8c8af-140">Эта команда представляет собой одну строку текста.</span><span class="sxs-lookup"><span data-stu-id="8c8af-140">This command is a single line of text.</span></span> <span data-ttu-id="8c8af-141">Эта команда позволяет получить доступ к приложению/сервицемоделсамплес с помощью `http://localhost/servicemodelsamples` и `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="8c8af-141">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="8c8af-142">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c8af-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="8c8af-143">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c8af-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    <span data-ttu-id="8c8af-144">Удалите привязку сайта к протоколу net.tcp, добавленную ранее для данного образца.</span><span class="sxs-lookup"><span data-stu-id="8c8af-144">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="8c8af-145">Для удобства два нижеописанных действия выполняются в пакетом файле RemoveNetTcpSiteBinding.cmd, расположенном в каталоге с образцами.</span><span class="sxs-lookup"><span data-stu-id="8c8af-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="8c8af-146">Удалите протокол net.tcp из списка разрешенных протоколов, выполнив следующую команду в окне командной строки с правами администратора:</span><span class="sxs-lookup"><span data-stu-id="8c8af-146">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="8c8af-147">Эта команда вводится как одна строка текста.</span><span class="sxs-lookup"><span data-stu-id="8c8af-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="8c8af-148">Удалите привязку узла к протоколу net.tcp, выполнив следующую команду в окне командной строки с правами администратора:</span><span class="sxs-lookup"><span data-stu-id="8c8af-148">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="8c8af-149">Эта команда должна вводиться как одна строка текста.</span><span class="sxs-lookup"><span data-stu-id="8c8af-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c8af-150">См. также</span><span class="sxs-lookup"><span data-stu-id="8c8af-150">See also</span></span>

- <span data-ttu-id="8c8af-151">[Образцы размещения и сохраняемости AppFabric](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8c8af-151">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
