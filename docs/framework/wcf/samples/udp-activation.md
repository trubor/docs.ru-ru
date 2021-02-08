---
description: 'Дополнительные сведения: Активация по протоколу UDP'
title: Активация UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 8ee5e6363265ddc74d27884ef40354108da17581
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798229"
---
# <a name="udp-activation"></a><span data-ttu-id="5d3bc-103">Активация UDP</span><span class="sxs-lookup"><span data-stu-id="5d3bc-103">UDP Activation</span></span>

<span data-ttu-id="5d3bc-104">Этот пример основан на образце [Transport: UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="5d3bc-104">This sample is based on the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="5d3bc-105">Он расширяет пример [Transport: UDP](transport-udp.md) для поддержки активации процессов с помощью службы активации процессов Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="5d3bc-105">It extends the [Transport: UDP](transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="5d3bc-106">Образец состоит из трех основных частей:</span><span class="sxs-lookup"><span data-stu-id="5d3bc-106">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="5d3bc-107">Активатор протокола UDP - автономный процесс, получающий сообщения UDP от лица приложений, подлежащих активации.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-107">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="5d3bc-108">Клиент, использующий пользовательский транспорт UDP для отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-108">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="5d3bc-109">Служба (размещенная в рабочем процессе, активированном службой WAS), получающая сообщения по пользовательскому транспорту UDP.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-109">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="5d3bc-110">Активатор протокола UDP</span><span class="sxs-lookup"><span data-stu-id="5d3bc-110">UDP Protocol Activator</span></span>  

 <span data-ttu-id="5d3bc-111">Активатор протокола UDP — это мост между клиентом WCF и службой WCF.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-111">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="5d3bc-112">Он обеспечивает передачу данных через протокол UDP на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-112">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="5d3bc-113">У него две основные функции.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-113">It has two major functions:</span></span>  
  
- <span data-ttu-id="5d3bc-114">Адаптер прослушивателя WAS (LA), работающий совместно со службой WAS для активирования процессов в ответ на входящие сообщения.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-114">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="5d3bc-115">Прослушиватель протокола UDP, который принимает сообщения UDP от лица приложений, подлежащих активации.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-115">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="5d3bc-116">Активатор должен работать как автономная программа на компьютере сервера.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-116">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="5d3bc-117">Обычно адаптеры прослушивателя WAS (такие как NetTcpActivator и NetPipeActivator) реализуются в долговременных службах Windows.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-117">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="5d3bc-118">Однако для простоты и ясности в данном образце активатор протокола реализован как автономное приложение.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-118">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="5d3bc-119">Адаптер прослушивателя WAS</span><span class="sxs-lookup"><span data-stu-id="5d3bc-119">WAS Listener Adapter</span></span>  

 <span data-ttu-id="5d3bc-120">Адаптер прослушивателя WAS для протокола UDP реализован в классе `UdpListenerAdapter`.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-120">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="5d3bc-121">Именно этот модуль во взаимодействии со службой WAS выполняет активацию приложения для протокола UDP.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-121">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="5d3bc-122">Это производится путем вызова следующих интерфейсов Webhost API:</span><span class="sxs-lookup"><span data-stu-id="5d3bc-122">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="5d3bc-123">После исходного вызова `WebhostRegisterProtocol` адаптер прослушивателя получает обратный вызов `ApplicationCreated` от службы WAS для всех приложений, зарегистрированных в applicationHost.config (расположен в %windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="5d3bc-123">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="5d3bc-124">В этом образце обрабатываются только приложения с включенным протоколом UDP (с ИД протокола "net.udp").</span><span class="sxs-lookup"><span data-stu-id="5d3bc-124">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="5d3bc-125">Другие реализации могут выполнять эту обработку по-другому, если такие реализацию реагируют на динамические изменения конфигурации приложения (например, переход приложения из отключенного состояния во включенное).</span><span class="sxs-lookup"><span data-stu-id="5d3bc-125">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="5d3bc-126">Получение обратного вызова `ConfigManagerInitializationCompleted` показывает, что служба WAS завершила все уведомления для инициализации протокола.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-126">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="5d3bc-127">На этом этапе прослушиватель готов к обработке запросов активации.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-127">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="5d3bc-128">При поступлении нового запроса, который является первым для приложения, адаптер прослушивателя вызывает `WebhostOpenListenerChannelInstance` в WAS, запуская рабочий процесс, если он еще не запущен.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-128">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="5d3bc-129">Затем загружаются обработчики протокола, и можно начинать обмен данными между адаптером прослушивателя и виртуальным приложением.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-129">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="5d3bc-130">Адаптер прослушивателя регистрируется в папке% SystemRoot% \System32\inetsrv\ApplicationHost.config в разделе <`listenerAdapters`> следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5d3bc-130">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="5d3bc-131">Прослушиватель протокола</span><span class="sxs-lookup"><span data-stu-id="5d3bc-131">Protocol Listener</span></span>  

 <span data-ttu-id="5d3bc-132">Прослушиватель протокола UDP представляет собой модуль внутри активатора протокола, который ожидает передачи данных на конечной точке UDP от лица виртуального приложения.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-132">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="5d3bc-133">Он реализован в классе `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-133">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="5d3bc-134">Конечная точка представлена как `IPEndpoint`, номер порта для которой извлекается из привязки протокола для сайта.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-134">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="5d3bc-135">Служба управления</span><span class="sxs-lookup"><span data-stu-id="5d3bc-135">Control Service</span></span>  

 <span data-ttu-id="5d3bc-136">В этом примере мы используем WCF для обмена данными между активатором и рабочим процессом WAS.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-136">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="5d3bc-137">Служба, находящаяся в активаторе, называется службой управления.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-137">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="5d3bc-138">Обработчики протоколов</span><span class="sxs-lookup"><span data-stu-id="5d3bc-138">Protocol Handlers</span></span>  

 <span data-ttu-id="5d3bc-139">После того как адаптер прослушивателя вызывает `WebhostOpenListenerChannelInstance`, диспетчер процесса WAS запускает рабочий процесс, если он еще не запущен.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-139">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="5d3bc-140">Затем диспетчер приложения внутри рабочего процесса загружает обработчик протокола процесса (PPH) UDP с запросом этого `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-140">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="5d3bc-141">PPH в включает вызовы `IAdphManager` .`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="5d3bc-141">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="5d3bc-142">запуск обработчика протокола домена приложения UDP (АДФ).</span><span class="sxs-lookup"><span data-stu-id="5d3bc-142">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="5d3bc-143">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d3bc-143">HostedUDPTransportConfiguration</span></span>  

 <span data-ttu-id="5d3bc-144">Информация регистрируется в файле Web.config следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5d3bc-144">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="5d3bc-145">Специальная настройка для этого примера</span><span class="sxs-lookup"><span data-stu-id="5d3bc-145">Special Setup for This Sample</span></span>  

 <span data-ttu-id="5d3bc-146">Этот образец может быть построен и запущен только в ОС Windows Vista, Windows Server 2008 или Windows 7.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-146">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="5d3bc-147">Для запуска этого примера необходимо сначала правильно установить все компоненты.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-147">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="5d3bc-148">Установите образец в соответствии с приведенными ниже шагами.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-148">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="5d3bc-149">Настройка этого образца</span><span class="sxs-lookup"><span data-stu-id="5d3bc-149">To set up this sample</span></span>  
  
1. <span data-ttu-id="5d3bc-150">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-150">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="5d3bc-151">Постройте проект в ОС Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-151">Build the project on Windows Vista.</span></span> <span data-ttu-id="5d3bc-152">После компиляции на этапе за построением также выполняются следующие операции.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-152">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="5d3bc-153">Устанавливается привязка UDP на сайт "Веб-узел по умолчанию".</span><span class="sxs-lookup"><span data-stu-id="5d3bc-153">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="5d3bc-154">Создается виртуальное приложение "ServiceModelSamples", указывающее по физическому пути: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="5d3bc-154">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="5d3bc-155">Также включается протокол "net.udp" для данного виртуального приложения.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-155">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="5d3bc-156">Запустите приложение пользовательского интерфейса "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="5d3bc-156">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="5d3bc-157">Перейдите на вкладку **Настройка** , установите следующие флажки и нажмите кнопку **установить** , чтобы установить их:</span><span class="sxs-lookup"><span data-stu-id="5d3bc-157">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="5d3bc-158">Адаптер прослушивателя UDP</span><span class="sxs-lookup"><span data-stu-id="5d3bc-158">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="5d3bc-159">Обработчики протокола UDP</span><span class="sxs-lookup"><span data-stu-id="5d3bc-159">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="5d3bc-160">Перейдите на вкладку **Активация** приложения пользовательского интерфейса "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="5d3bc-160">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="5d3bc-161">Нажмите кнопку " **Пуск** ", чтобы запустить Адаптер прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-161">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="5d3bc-162">Теперь все готово для запуска программы.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-162">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5d3bc-163">Завершив работу с этим примером, необходимо запустить файл Cleanup.bat, чтобы удалить привязку net.udp с сайта "Веб-узел по умолчанию".</span><span class="sxs-lookup"><span data-stu-id="5d3bc-163">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="5d3bc-164">Пример использования</span><span class="sxs-lookup"><span data-stu-id="5d3bc-164">Sample Usage</span></span>  

 <span data-ttu-id="5d3bc-165">После компиляции создаются четыре различных двоичных файла.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-165">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="5d3bc-166">Client.exe: код клиента.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-166">Client.exe: The client code.</span></span> <span data-ttu-id="5d3bc-167">Файл App.config компилируется в файл конфигурации клиента Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-167">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="5d3bc-168">UDPActivation.dll: библиотека, содержащая все основные реализации UDP.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-168">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="5d3bc-169">Service.dll: код службы.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-169">Service.dll: The service code.</span></span> <span data-ttu-id="5d3bc-170">Он копируется в каталог \bin виртуального приложения ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-170">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="5d3bc-171">Файл службы называется Service.svc, а файл конфигурации — Web.config. После компиляции они копируются в следующее расположение: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-171">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="5d3bc-172">WasNetActivator: программа активатора UDP.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-172">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="5d3bc-173">Убедитесь, что все обязательные элементы правильно установлены.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-173">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="5d3bc-174">Следующие шаги показывают, как запустить образец:</span><span class="sxs-lookup"><span data-stu-id="5d3bc-174">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="5d3bc-175">Убедитесь, что запущены следующие службы Windows:</span><span class="sxs-lookup"><span data-stu-id="5d3bc-175">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="5d3bc-176">Служба активации Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="5d3bc-176">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="5d3bc-177">Службы IIS: W3SVC.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-177">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="5d3bc-178">Затем запустите активатор WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-178">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="5d3bc-179">На вкладке **Активация** в раскрывающемся списке выбран единственный протокол **UDP**.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-179">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="5d3bc-180">Нажмите кнопку " **Пуск** ", чтобы запустить активатор.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-180">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="5d3bc-181">После запуска активатора можно запустить код клиента, запустив файл Client.exe в командном окне.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-181">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="5d3bc-182">Далее приводится образец вывода:</span><span class="sxs-lookup"><span data-stu-id="5d3bc-182">The following is the sample output:</span></span>  
  
    ```console  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="5d3bc-183">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5d3bc-184">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5d3bc-184">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5d3bc-185">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5d3bc-186">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5d3bc-186">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
