---
description: 'Дополнительные сведения: пример интеграции Системвебраутинг'
title: Образец интеграции с SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 84b442dfb7f0e5877f742fb055aea49a5625bb78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668660"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="31cf2-103">Образец интеграции с SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="31cf2-103">SystemWebRouting Integration Sample</span></span>

<span data-ttu-id="31cf2-104">Этот образец показывает интеграцию уровня размещения с классами в пространстве имен <xref:System.Web.Routing>.</span><span class="sxs-lookup"><span data-stu-id="31cf2-104">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="31cf2-105">Классы в пространстве имен <xref:System.Web.Routing> позволяют приложению использовать URL-адреса, которые не соответствуют непосредственно физическому ресурсу.</span><span class="sxs-lookup"><span data-stu-id="31cf2-105">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="31cf2-106">Использование веб-маршрутизации позволяет разработчику создавать виртуальные адреса для протокола HTTP, которые затем сопоставляются с реальными службами WCF.</span><span class="sxs-lookup"><span data-stu-id="31cf2-106">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="31cf2-107">Это может быть полезно, когда службу WCF необходимо разместить без обязательного выделения физического файла или ресурса или к службам необходимо получать доступ по URL-адресам, не содержащим файлов, например HTML или ASPX.</span><span class="sxs-lookup"><span data-stu-id="31cf2-107">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="31cf2-108">Этот образец показывает использование класса <xref:System.Web.Routing.RouteTable> для создания виртуальных URI-адресов, связанных с выполняющимися службами, которые определены в файле global.asax.</span><span class="sxs-lookup"><span data-stu-id="31cf2-108">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="31cf2-109">Классы в пространстве имен <xref:System.Web.Routing> работают только со службами, размещаемыми по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="31cf2-109">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="31cf2-110">В этом примере используется WCF для создания двух RSS-каналов: `movies` канала и `channels` канала.</span><span class="sxs-lookup"><span data-stu-id="31cf2-110">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="31cf2-111">URL-адреса для активации служб не содержат расширения и регистрируются в `Application_Start` методе `Global` класса, производного от <xref:System.Web.HttpApplication> класса.</span><span class="sxs-lookup"><span data-stu-id="31cf2-111">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31cf2-112">Этот пример работает только в службы IIS (IIS) 7,0 и более поздних версиях, так как в IIS 6,0 используется другой метод для поддержки URL-адресов без расширений.</span><span class="sxs-lookup"><span data-stu-id="31cf2-112">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="31cf2-113">Чтобы скачать этот пример</span><span class="sxs-lookup"><span data-stu-id="31cf2-113">To download this sample</span></span>
  
<span data-ttu-id="31cf2-114">Возможно, этот образец уже установлен на компьютере.</span><span class="sxs-lookup"><span data-stu-id="31cf2-114">This sample may already be installed on your computer.</span></span> <span data-ttu-id="31cf2-115">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="31cf2-115">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="31cf2-116">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="31cf2-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31cf2-117">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="31cf2-117">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="31cf2-118">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="31cf2-118">To use this sample</span></span>  
  
1. <span data-ttu-id="31cf2-119">В Visual Studio откройте файл Вебраутингинтегратион. sln.</span><span class="sxs-lookup"><span data-stu-id="31cf2-119">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="31cf2-120">Нажмите клавишу F5, чтобы выполнить решение и запустить веб-сервер разработки.</span><span class="sxs-lookup"><span data-stu-id="31cf2-120">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="31cf2-121">Отобразится список каталогов для образца.</span><span class="sxs-lookup"><span data-stu-id="31cf2-121">A directory listing for the sample appears.</span></span> <span data-ttu-id="31cf2-122">Обратите внимание, что файлы с расширением SVC отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="31cf2-122">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="31cf2-123">В адресной строке добавьте `movies` к URL-адресу, чтобы он был прочитан, `http://localhost:[port]/movies` и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="31cf2-123">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="31cf2-124">В браузере откроется пакет фильмов.</span><span class="sxs-lookup"><span data-stu-id="31cf2-124">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="31cf2-125">В адресной строке добавьте `channels` к URL-адресу, чтобы он был считан, `http://localhost:[port]/channels` и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="31cf2-125">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="31cf2-126">В браузере откроется пакет каналов.</span><span class="sxs-lookup"><span data-stu-id="31cf2-126">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="31cf2-127">Закройте веб-браузер, нажав клавиши ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="31cf2-127">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="31cf2-128">Если сервер разработки не завершил работу, щелкните правой кнопкой мыши значок области уведомлений и выберите пункт **прекратить**.</span><span class="sxs-lookup"><span data-stu-id="31cf2-128">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="31cf2-129">Использование этого образца в случае размещения на IIS</span><span class="sxs-lookup"><span data-stu-id="31cf2-129">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="31cf2-130">В Visual Studio откройте файл Вебраутингинтегратион. sln.</span><span class="sxs-lookup"><span data-stu-id="31cf2-130">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="31cf2-131">Постройте проект, нажав клавиши CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="31cf2-131">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="31cf2-132">Создайте веб-приложение в Диспетчере служб IIS.</span><span class="sxs-lookup"><span data-stu-id="31cf2-132">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="31cf2-133">В диспетчере служб IIS щелкните правой кнопкой мыши **веб-сайт по умолчанию** и выберите **Добавить приложение**.</span><span class="sxs-lookup"><span data-stu-id="31cf2-133">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="31cf2-134">В качестве **псевдонима** введите `WebRoutingIntegration` .</span><span class="sxs-lookup"><span data-stu-id="31cf2-134">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="31cf2-135">Для **физического пути** выберите папку службы внутри проекта.</span><span class="sxs-lookup"><span data-stu-id="31cf2-135">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="31cf2-136">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="31cf2-136">Press **OK**.</span></span>  
  
4. <span data-ttu-id="31cf2-137">Запустите приложение, щелкнув правой кнопкой мыши веб-приложение и выбрав **Управление приложением** , а затем — **Обзор**.</span><span class="sxs-lookup"><span data-stu-id="31cf2-137">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="31cf2-138">В адресной строке добавьте `movies` к URL-адресу, чтобы он был считан, `http://localhost:[port]/movies` и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="31cf2-138">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="31cf2-139">В браузере откроется пакет фильмов.</span><span class="sxs-lookup"><span data-stu-id="31cf2-139">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="31cf2-140">В адресной строке добавьте `channels` к URL-адресу, чтобы он был считан, `http://localhost:[port]/channels` и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="31cf2-140">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="31cf2-141">В браузере откроется пакет каналов.</span><span class="sxs-lookup"><span data-stu-id="31cf2-141">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="31cf2-142">Закройте веб-браузер, нажав клавиши ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="31cf2-142">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="31cf2-143">Этот образец демонстрирует, что уровень размещения может взаимодействовать с классами в пространстве имен <xref:System.Web.Routing> для маршрутизации запросов служб, размещенных через протокол HTTP.</span><span class="sxs-lookup"><span data-stu-id="31cf2-143">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31cf2-144">Необходимо обновить версию пула приложений по умолчанию до платформа .NET Framework 4, если она имеет значение версии 2.</span><span class="sxs-lookup"><span data-stu-id="31cf2-144">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31cf2-145">См. также</span><span class="sxs-lookup"><span data-stu-id="31cf2-145">See also</span></span>

- <span data-ttu-id="31cf2-146">[Образцы размещения и сохраняемости AppFabric](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="31cf2-146">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
