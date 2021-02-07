---
description: 'Дополнительные сведения: Настройка службы IIS 7,0 для Windows Communication Foundation'
title: Настройка IIS 7.0 для Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: e76918d70a922cb32c9bbacd5779aa4f8e991b2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743269"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="19497-103">Настройка IIS 7.0 для Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="19497-103">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="19497-104">Службы IIS 7.0 имеют модульную архитектуру, что позволяет выборочно устанавливать необходимые компоненты.</span><span class="sxs-lookup"><span data-stu-id="19497-104">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="19497-105">Эта схема основана на новой технологии, управляемой манифестом, которая появилась в Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="19497-105">This design is based on the new manifest-driven componentization technology introduced in Windows Vista.</span></span> <span data-ttu-id="19497-106">Существует более 40 отдельных компонентов служб IIS 7,0, которые могут быть установлены независимо.</span><span class="sxs-lookup"><span data-stu-id="19497-106">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="19497-107">Это позволяет ИТ-специалистам легко настраивать службы в соответствии с конкретными требованиями.</span><span class="sxs-lookup"><span data-stu-id="19497-107">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="19497-108">В этом разделе описано, как настроить IIS 7,0 для использования с Windows Communication Foundation (WCF) и определить, какие компоненты требуются.</span><span class="sxs-lookup"><span data-stu-id="19497-108">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="19497-109">Минимальная установка: установка службы WAS</span><span class="sxs-lookup"><span data-stu-id="19497-109">Minimal Installation: Installing WAS</span></span>

 <span data-ttu-id="19497-110">Минимальная установка всего пакета IIS 7,0 заключается в установке службы активации процессов Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="19497-110">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="19497-111">WAS — это автономная функция, которая является единственной функцией IIS 7,0, доступной для всех операционных систем Windows Vista (Домашняя базовая, Домашняя расширенная, Business, максимальная и корпоративная).</span><span class="sxs-lookup"><span data-stu-id="19497-111">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all Windows Vista operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="19497-112">На панели управления щелкните **программы** , а затем — **Включение или отключение компонентов Windows** , которые перечислены в разделе **программы и компоненты**, компонент WAS показан в списке, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="19497-112">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="19497-113">![Диалоговое окно включения и отключения функций](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="19497-113">![Turn Features On or Off Dialog](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="19497-114">Этот компонент включает следующие подкомпоненты:</span><span class="sxs-lookup"><span data-stu-id="19497-114">This feature has the following sub-components:</span></span>

- <span data-ttu-id="19497-115">Среда .NET</span><span class="sxs-lookup"><span data-stu-id="19497-115">.NET Environment</span></span>

- <span data-ttu-id="19497-116">API-интерфейсы конфигурации</span><span class="sxs-lookup"><span data-stu-id="19497-116">Configuration APIs</span></span>

- <span data-ttu-id="19497-117">Модель процесса</span><span class="sxs-lookup"><span data-stu-id="19497-117">Process Model</span></span>

 <span data-ttu-id="19497-118">Если выбран корневой узел WAS, по умолчанию проверяется только вложенный узел **модели процесса** .</span><span class="sxs-lookup"><span data-stu-id="19497-118">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="19497-119">Обратите внимание, что при такой установке устанавливается только служба WAS, поскольку поддержка веб-сервера отсутствует.</span><span class="sxs-lookup"><span data-stu-id="19497-119">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="19497-120">Чтобы сделать WCF или любое приложение ASP.NET работать, установите флажок **среда .NET** .</span><span class="sxs-lookup"><span data-stu-id="19497-120">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="19497-121">Это означает, что все компоненты WAS необходимы для того, чтобы обеспечить хорошую работу WCF и ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="19497-121">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="19497-122">Они автоматически выбираются при установке какого либо из этих компонентов.</span><span class="sxs-lookup"><span data-stu-id="19497-122">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="19497-123">Службы IIS 7.0: установка по умолчанию</span><span class="sxs-lookup"><span data-stu-id="19497-123">IIS 7.0: Default Installation</span></span>

 <span data-ttu-id="19497-124">После проверки функции **службы IIS** некоторые из подузлов автоматически проверяются, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="19497-124">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="19497-125">![Параметры по умолчанию для функций IIS 7.0](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="19497-125">![Default settings for IIS 7.0 features](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="19497-126">Это установка IIS 7,0 по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="19497-126">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="19497-127">С помощью этой установки можно использовать IIS 7,0 для обслуживания статического содержимого (например, HTML-страниц и другого содержимого).</span><span class="sxs-lookup"><span data-stu-id="19497-127">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="19497-128">Однако вы не можете запускать приложения ASP.NET или CGI или размещать службы WCF.</span><span class="sxs-lookup"><span data-stu-id="19497-128">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="19497-129">IIS 7.0: установка с поддержкой ASP.NET</span><span class="sxs-lookup"><span data-stu-id="19497-129">IIS 7.0: Installation with ASP.NET Support</span></span>

 <span data-ttu-id="19497-130">Необходимо установить ASP.NET, чтобы сделать ASP.NET работу с IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="19497-130">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="19497-131">После проверки **ASP.NET** экран должен выглядеть, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="19497-131">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="19497-132">![Обязательные параметры Asp.NET](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="19497-132">![Asp.NET required settings](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="19497-133">Это минимальная среда для приложений WCF и ASP.NET для работы в IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="19497-133">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="19497-134">IIS 7.0: установка с компонентами совместимости с IIS 6.0</span><span class="sxs-lookup"><span data-stu-id="19497-134">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>

 <span data-ttu-id="19497-135">При установке IIS 7,0 в системе с помощью Visual Studio 2005 или некоторых других сценариев или средств автоматизации (таких как Adsutil.vbs), которые настраивают виртуальные приложения, использующие API метабазы IIS 6,0, убедитесь, что вы установили **средства создания скриптов** для служб IIS 6,0.</span><span class="sxs-lookup"><span data-stu-id="19497-135">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="19497-136">Это автоматически проверяет другие подузлы **совместимости управления** IIS 6,0.</span><span class="sxs-lookup"><span data-stu-id="19497-136">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="19497-137">На следующем рисунке показан экран после выполнения этой задачи:</span><span class="sxs-lookup"><span data-stu-id="19497-137">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="19497-138">![Параметры совместимости управления IIS 6.0](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="19497-138">![IIS 6.0 Management Compatibility Settings](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="19497-139">В этой установке все, что необходимо для использования функций и примеров IIS 7,0, ASP.NET и WCF, доступны в Интернете.</span><span class="sxs-lookup"><span data-stu-id="19497-139">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="19497-140">Ограничения запросов</span><span class="sxs-lookup"><span data-stu-id="19497-140">Request Limits</span></span>

 <span data-ttu-id="19497-141">В Windows Vista с IIS 7 значения `maxUri` параметров и по умолчанию `maxQueryStringSize` изменены.</span><span class="sxs-lookup"><span data-stu-id="19497-141">On Windows Vista with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="19497-142">По умолчанию фильтрация запросов в IIS 7.0 допускает использование URL-адресов длиной 4096 знаков и строк запросов длиной 2048 знаков.</span><span class="sxs-lookup"><span data-stu-id="19497-142">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="19497-143">Чтобы изменить эти значения по умолчанию, добавьте в файл App.config следующий XML-код.</span><span class="sxs-lookup"><span data-stu-id="19497-143">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="19497-144">См. также</span><span class="sxs-lookup"><span data-stu-id="19497-144">See also</span></span>

- [<span data-ttu-id="19497-145">Архитектура активации WAS</span><span class="sxs-lookup"><span data-stu-id="19497-145">WAS Activation Architecture</span></span>](was-activation-architecture.md)
- [<span data-ttu-id="19497-146">Настройка WAS для использования с WCF</span><span class="sxs-lookup"><span data-stu-id="19497-146">Configuring WAS for Use with WCF</span></span>](configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="19497-147">Практическое руководство. Установка и настройка компонентов активации WCF</span><span class="sxs-lookup"><span data-stu-id="19497-147">How to: Install and Configure WCF Activation Components</span></span>](how-to-install-and-configure-wcf-activation-components.md)
- <span data-ttu-id="19497-148">[Функции размещения Windows Server App Fabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="19497-148">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
