---
description: 'Дополнительные сведения о: Hello World со службой маршрутизации'
title: Приветствие средствами служб маршрутизации.
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 1741c7d1f1e474864d66220fd160633997744876
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631974"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="ea0aa-103">Приветствие средствами служб маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-103">Hello World with the Routing Service</span></span>

<span data-ttu-id="ea0aa-104">В этом примере демонстрируется служба маршрутизации Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ea0aa-104">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="ea0aa-105">Служба маршрутизации — это компонент WCF, который позволяет легко включать в приложение маршрутизатор на основе содержимого.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-105">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="ea0aa-106">Этот пример адаптирует стандартный пример калькулятора WCF для обмена данными с помощью службы маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-106">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="ea0aa-107">В этом образце клиент ская часть калькулятора настраивается для отправки сообщений в конечную точку, доступ к которой предоставляется маршрутизатором.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-107">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="ea0aa-108">Служба маршрутизации настроена на прием всех отправляемых ей сообщений и перенаправление их в конечную точку, которая соответствует службе калькулятора.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-108">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="ea0aa-109">Таким образом, сообщения, отправленные клиентом и полученные маршрутизатором, перенаправляются фактической службе калькулятора.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-109">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="ea0aa-110">Сообщения от резервной службы калькулятора отправляются назад маршрутизатору, который, в свою очередь, передает их клиенту калькулятора.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-110">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="ea0aa-111">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="ea0aa-111">To use this sample</span></span>

1. <span data-ttu-id="ea0aa-112">С помощью Visual Studio 2012 откройте Хеллораутингсервице. sln.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-112">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="ea0aa-113">Нажмите клавишу F5 или сочетание клавиш CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-113">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ea0aa-114">При нажатии F5 автоматически запускается клиентская часть калькулятора.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-114">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="ea0aa-115">При нажатии сочетания клавиш CTRL+SHIFT+B (построение) следующие приложения необходимо запустить вручную.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-115">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="ea0aa-116">Клиентская часть калькулятора (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="ea0aa-116">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="ea0aa-117">Служба калькулятора (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="ea0aa-117">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="ea0aa-118">Служба маршрутизации (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="ea0aa-118">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="ea0aa-119">Чтобы запустить клиент, нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-119">Press ENTER to start the client.</span></span>

     <span data-ttu-id="ea0aa-120">Вы должны увидеть следующий результат.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-120">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="ea0aa-121">Настраивается в коде или в файле App.config</span><span class="sxs-lookup"><span data-stu-id="ea0aa-121">Configurable via Code or App.Config</span></span>

 <span data-ttu-id="ea0aa-122">В поставляемой конфигурации образца поведение маршрутизатора определяется в файле App.config.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-122">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="ea0aa-123">Кроме того, можно изменить имя файла App.config на другое, чтобы он не был распознан, и удалить метки комментария с вызова метода ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="ea0aa-123">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="ea0aa-124">Поведение маршрутизатора будет одинаковым для обоих методов.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-124">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="ea0aa-125">Сценарий</span><span class="sxs-lookup"><span data-stu-id="ea0aa-125">Scenario</span></span>

 <span data-ttu-id="ea0aa-126">В этом образце показано, как маршрутизатор пработает в качестве основного средства переноса сообщений.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-126">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="ea0aa-127">Служба маршрутизации действует как прозрачный узел-посредник, настроенный передавать сообщения непосредственно заданному набору конечных точек назначения.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-127">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="ea0aa-128">Реальный сценарий</span><span class="sxs-lookup"><span data-stu-id="ea0aa-128">Real World Scenario</span></span>

 <span data-ttu-id="ea0aa-129">В Contoso необходимо повысить уровень гибкости для именования, адресации, конфигурации и обеспечения безопасности его служб.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-129">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="ea0aa-130">Для этого базовый цикл обработки сообщений помещается перед службами для выполнения роли открытой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-130">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="ea0aa-131">Благодаря этому предоставляется возможность обеспечения дополнительного уровня безопасности для фактических служб и упрощается реализация масштабированных решений и управления версиями служб в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-131">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea0aa-132">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-132">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ea0aa-133">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="ea0aa-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ea0aa-134">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ea0aa-135">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="ea0aa-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="ea0aa-136">См. также</span><span class="sxs-lookup"><span data-stu-id="ea0aa-136">See also</span></span>

- <span data-ttu-id="ea0aa-137">[Образцы размещения и сохраняемости AppFabric](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ea0aa-137">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
