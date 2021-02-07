---
description: 'Дополнительные сведения: службы WCF и трассировка событий для Windows'
title: Службы WCF и средство отслеживания событий для Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ba2d323322a2d3481f1414ac58fbf0b44508bb03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755685"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="f61f2-103">Службы WCF и средство отслеживания событий для Windows</span><span class="sxs-lookup"><span data-stu-id="f61f2-103">WCF Services and Event Tracing for Windows</span></span>

<span data-ttu-id="f61f2-104">В этом примере показано, как использовать аналитическую трассировку в Windows Communication Foundation (WCF) для создания событий в трассировке событий Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="f61f2-104">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="f61f2-105">Аналитические трассировки — это события, генерируемые в ключевых точках стека WCF, которые позволяют устранять неполадки служб WCF в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="f61f2-105">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="f61f2-106">Аналитическая трассировка в службах WCF — это трассировка, которую можно включить в рабочей среде с минимальным влиянием на производительность.</span><span class="sxs-lookup"><span data-stu-id="f61f2-106">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="f61f2-107">Отслеживаемые события передаются в сеанс трассировки событий Windows.</span><span class="sxs-lookup"><span data-stu-id="f61f2-107">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="f61f2-108">Этот пример включает базовую службу WCF, в которой события выдаются из службы в журнал событий, который можно просмотреть с помощью Просмотр событий.</span><span class="sxs-lookup"><span data-stu-id="f61f2-108">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="f61f2-109">Также можно запустить выделенный сеанс ETW, который прослушивает события из службы WCF.</span><span class="sxs-lookup"><span data-stu-id="f61f2-109">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="f61f2-110">Данный образец включает скрипт для создания выделенного сеанса трассировки событий Windows, хранящего события в двоичном файле, который можно прочесть с помощью средства просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="f61f2-110">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="f61f2-111">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="f61f2-111">To use this sample</span></span>

1. <span data-ttu-id="f61f2-112">С помощью Visual Studio 2012 откройте файл решения Етваналитиктрацесампле. sln.</span><span class="sxs-lookup"><span data-stu-id="f61f2-112">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="f61f2-113">Для построения решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="f61f2-113">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="f61f2-114">Чтобы запустить решение, нажмите клавиши CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="f61f2-114">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="f61f2-115">В веб-браузере щелкните **Калькулятор. svc**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-115">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="f61f2-116">В браузере должен появиться URI WSDL-документа для службы.</span><span class="sxs-lookup"><span data-stu-id="f61f2-116">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="f61f2-117">Скопируйте этот URI.</span><span class="sxs-lookup"><span data-stu-id="f61f2-117">Copy that URI.</span></span>

     <span data-ttu-id="f61f2-118">По умолчанию служба запускает прослушивание запросов через порт 1378 `http://localhost:1378/Calculator.svc` .</span><span class="sxs-lookup"><span data-stu-id="f61f2-118">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="f61f2-119">Запустите тестовый клиент WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="f61f2-119">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="f61f2-120">Тестовый клиент WCF (WcfTestClient.exe) находится в папке `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe` .</span><span class="sxs-lookup"><span data-stu-id="f61f2-120">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="f61f2-121">Каталог установки Visual Studio 2012 по умолчанию — `C:\Program Files\Microsoft Visual Studio 10.0` .</span><span class="sxs-lookup"><span data-stu-id="f61f2-121">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="f61f2-122">В тестовом клиенте WCF добавьте службу, выбрав **файл**, а затем **Добавить службу**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-122">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="f61f2-123">Добавьте адрес конечной точки в поле ввода.</span><span class="sxs-lookup"><span data-stu-id="f61f2-123">Add the endpoint address in the input box.</span></span> <span data-ttu-id="f61f2-124">Значение по умолчанию — `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="f61f2-124">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="f61f2-125">Откройте приложение просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="f61f2-125">Open the Event Viewer application.</span></span>

     <span data-ttu-id="f61f2-126">Перед вызовом службы запустите Просмотр событий и убедитесь, что журнал событий прослушивает события отслеживания, созданные из службы WCF.</span><span class="sxs-lookup"><span data-stu-id="f61f2-126">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="f61f2-127">В меню **Пуск** выберите **Администрирование**, а затем **Просмотр событий**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-127">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="f61f2-128">Включите журналы **аналитики** и **отладки** .</span><span class="sxs-lookup"><span data-stu-id="f61f2-128">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="f61f2-129">В древовидном представлении в Просмотр событий перейдите к **Просмотр событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, а затем **сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-129">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="f61f2-130">Щелкните правой кнопкой мыши **сервер приложений — приложения**, выберите **вид**, а затем **Показать журналы аналитики и отладки**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-130">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="f61f2-131">Убедитесь, что установлен флажок **отображать журналы аналитики и отладки** .</span><span class="sxs-lookup"><span data-stu-id="f61f2-131">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="f61f2-132">Включите **аналитический** журнал.</span><span class="sxs-lookup"><span data-stu-id="f61f2-132">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="f61f2-133">В древовидном представлении в Просмотр событий перейдите к **Просмотр событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, а затем **сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-133">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="f61f2-134">Щелкните правой кнопкой мыши **аналитика** и выберите **Включить журнал**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-134">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="f61f2-135">Проверка службы</span><span class="sxs-lookup"><span data-stu-id="f61f2-135">To test the service</span></span>

1. <span data-ttu-id="f61f2-136">Вернитесь в тестовый клиент WCF и дважды щелкните `Divide` и не задерживайте значения по умолчанию, указав знаменатель 0.</span><span class="sxs-lookup"><span data-stu-id="f61f2-136">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="f61f2-137">Если знаменатель равен 0, служба выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="f61f2-137">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="f61f2-138">Просмотрите события, переданные из службы.</span><span class="sxs-lookup"><span data-stu-id="f61f2-138">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="f61f2-139">Вернитесь к Просмотр событий и перейдите в раздел **Просмотр событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, а затем **сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-139">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="f61f2-140">Щелкните правой кнопкой мыши **аналитика** и выберите **Обновить**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-140">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="f61f2-141">События аналитического отслеживания WCF отображаются в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="f61f2-141">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="f61f2-142">Обратите внимание, что для возникшей ошибки в средстве просмотра событий отображается событие аналитического отслеживания.</span><span class="sxs-lookup"><span data-stu-id="f61f2-142">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="f61f2-143">Повторите шаги 1 и 2, используя уже допустимые входные значения.</span><span class="sxs-lookup"><span data-stu-id="f61f2-143">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="f61f2-144">Значением параметра `N2` может быть любое число, отличное от 0.</span><span class="sxs-lookup"><span data-stu-id="f61f2-144">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="f61f2-145">Обновите канал аналитики, чтобы убедиться, что события WCF не включают событий, связанных с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="f61f2-145">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="f61f2-146">Образец иллюстрирует передачу событий аналитического отслеживания из службы WCF.</span><span class="sxs-lookup"><span data-stu-id="f61f2-146">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="f61f2-147">Очистка (необязательно)</span><span class="sxs-lookup"><span data-stu-id="f61f2-147">To cleanup (Optional)</span></span>

1. <span data-ttu-id="f61f2-148">Откройте средство просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="f61f2-148">Open Event Viewer.</span></span>

2. <span data-ttu-id="f61f2-149">Перейдите к **Просмотр событий**, **журналам приложений и служб**, **Microsoft**, **Windows**, а затем **Application-Servers-Applications**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="f61f2-150">Щелкните правой кнопкой мыши **аналитика** и выберите **Отключить журнал**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-150">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="f61f2-151">Перейдите к **Просмотр событий**, **журналам приложений и служб**, **Microsoft**, **Windows**, а затем **Application-Servers-Applications**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-151">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="f61f2-152">Щелкните правой кнопкой мыши **аналитика** и выберите **Очистить журнал**.</span><span class="sxs-lookup"><span data-stu-id="f61f2-152">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="f61f2-153">Выберите параметр **clear (очистить** ), чтобы очистить события.</span><span class="sxs-lookup"><span data-stu-id="f61f2-153">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f61f2-154">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f61f2-154">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f61f2-155">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="f61f2-155">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f61f2-156">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="f61f2-156">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f61f2-157">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="f61f2-157">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="f61f2-158">См. также</span><span class="sxs-lookup"><span data-stu-id="f61f2-158">See also</span></span>

- <span data-ttu-id="f61f2-159">[Образцы наблюдения за AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f61f2-159">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
