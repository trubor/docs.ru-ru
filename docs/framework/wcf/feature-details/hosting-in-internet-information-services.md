---
description: 'Дополнительные сведения о: размещение в службы IIS'
title: Размещение в службах IIS
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 23c81bcfccba316500d333d277907d66e5d457c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743139"
---
# <a name="host-in-internet-information-services"></a><span data-ttu-id="e2e39-103">Размещение в службы IIS</span><span class="sxs-lookup"><span data-stu-id="e2e39-103">Host in Internet Information Services</span></span>

<span data-ttu-id="e2e39-104">Один из вариантов размещения служб Windows Communication Foundation (WCF) находится внутри приложения службы IIS (IIS).</span><span class="sxs-lookup"><span data-stu-id="e2e39-104">One option for hosting Windows Communication Foundation (WCF) services is inside of an Internet Information Services (IIS) application.</span></span> <span data-ttu-id="e2e39-105">Эта модель размещения похожа на модель, используемую веб-службами ASP.NET и ASP.NET Web Services (ASMX).</span><span class="sxs-lookup"><span data-stu-id="e2e39-105">This hosting model is similar to the model used by ASP.NET and ASP.NET Web services (ASMX) Web Services.</span></span>

## <a name="versions-of-iis"></a><span data-ttu-id="e2e39-106">Версии IIS</span><span class="sxs-lookup"><span data-stu-id="e2e39-106">Versions of IIS</span></span>

<span data-ttu-id="e2e39-107">WCF может размещаться на следующих версиях служб IIS в следующих операционных системах:</span><span class="sxs-lookup"><span data-stu-id="e2e39-107">WCF can be hosted on the following versions of IIS on the following operating systems:</span></span>

- <span data-ttu-id="e2e39-108">IIS 5,1 в Windows XP с пакетом обновления 2 (SP2).</span><span class="sxs-lookup"><span data-stu-id="e2e39-108">IIS 5.1 on Windows XP SP2.</span></span> <span data-ttu-id="e2e39-109">Эта среда полезна при проектировании и разработке приложений, размещенных в IIS, которые позже развертываются в серверной операционной системе, такой как Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="e2e39-109">This environment is useful for the design and development of IIS-hosted applications that are later deployed on a server operating system such as Windows Server 2003.</span></span>

- <span data-ttu-id="e2e39-110">IIS 6,0 на Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="e2e39-110">IIS 6.0 on Windows Server 2003.</span></span> <span data-ttu-id="e2e39-111">IIS 6,0 предоставляет расширенную модель процессов, обеспечивающую улучшенную масштабируемость, надежность и изоляцию приложений.</span><span class="sxs-lookup"><span data-stu-id="e2e39-111">IIS 6.0 provides an advanced process model that offers improved scalability, reliability, and application isolation.</span></span> <span data-ttu-id="e2e39-112">Эта среда подходит для рабочего развертывания служб WCF, использующих исключительно обмен данными по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2e39-112">This environment is suitable for production deployment of WCF services that use HTTP communication exclusively.</span></span>

- <span data-ttu-id="e2e39-113">IIS 7,0 в Windows Vista и Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="e2e39-113">IIS 7.0 on Windows Vista and Windows Server 2008.</span></span> <span data-ttu-id="e2e39-114">IIS 7,0 предоставляет ту же модель расширенных процессов, что и IIS 6,0, но использует службу активации процессов Windows (WAS), чтобы обеспечить активацию и сетевую связь по протоколам, отличным от HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2e39-114">IIS 7.0 provides the same advanced process model as IIS 6.0, but uses the Windows Process Activation Service (WAS) to allow activation and network communication over protocols other than HTTP.</span></span> <span data-ttu-id="e2e39-115">Эта среда подходит для разработки служб WCF, взаимодействующих по любому сетевому протоколу, поддерживаемому WCF (включая HTTP, net. TCP, net. pipe и net. MSMQ).</span><span class="sxs-lookup"><span data-stu-id="e2e39-115">This environment is suitable for the development of WCF services that communicate over any network protocol supported by WCF (including HTTP, net.tcp, net.pipe, and net.msmq).</span></span> <span data-ttu-id="e2e39-116">Дополнительные сведения о WAS см. [в разделе Размещение в службе активации Windows](hosting-in-windows-process-activation-service.md).</span><span class="sxs-lookup"><span data-stu-id="e2e39-116">For more information about WAS, see [Hosting in Windows Process Activation Service](hosting-in-windows-process-activation-service.md).</span></span>

- <span data-ttu-id="e2e39-117">[Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) работает с IIS 7,0 и службой активации Windows (WAS), чтобы предоставить обширную среду размещения приложений для служб NET4 WCF и WF.</span><span class="sxs-lookup"><span data-stu-id="e2e39-117">[Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) works with IIS 7.0 and Windows Process Activation Service (WAS) to provide a rich application hosting environment for NET4 WCF and WF services.</span></span> <span data-ttu-id="e2e39-118">К ее преимуществам относятся управление жизненным циклом, перезапуск процессов, совместное размещение, быстрая защита от сбоев, обработка потерянных процессов, активация по запросу и наблюдение за работоспособностью.</span><span class="sxs-lookup"><span data-stu-id="e2e39-118">These benefits include process life-cycle management, process recycling, shared hosting, rapid failure protection, process orphaning, on-demand activation, and health monitoring.</span></span> <span data-ttu-id="e2e39-119">Подробные сведения см. в разделе [функции размещения AppFabric](/previous-versions/appfabric/ee677189(v=azure.10)) и [Основные понятия размещения AppFabric](/previous-versions/appfabric/ee677371(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="e2e39-119">For detailed information, see [AppFabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10)) and [AppFabric Hosting Concepts](/previous-versions/appfabric/ee677371(v=azure.10)).</span></span>

## <a name="benefits-of-iis-hosting"></a><span data-ttu-id="e2e39-120">Преимущества размещения служб IIS</span><span class="sxs-lookup"><span data-stu-id="e2e39-120">Benefits of IIS hosting</span></span>

<span data-ttu-id="e2e39-121">Размещение служб WCF в IIS имеет несколько преимуществ:</span><span class="sxs-lookup"><span data-stu-id="e2e39-121">Hosting WCF services in IIS has several benefits:</span></span>

- <span data-ttu-id="e2e39-122">Службы WCF, размещенные в IIS, развертываются и управляются как любые другие типы приложений IIS, включая приложения ASP.NET и ASMX.</span><span class="sxs-lookup"><span data-stu-id="e2e39-122">WCF services hosted in IIS are deployed and managed like any other type of IIS application, including ASP.NET applications and ASMX.</span></span>

- <span data-ttu-id="e2e39-123">службы IIS предоставляют функции активации процессов, управления работоспособностью и перезапуска процессов, что позволяет повысить надежность приложений;</span><span class="sxs-lookup"><span data-stu-id="e2e39-123">IIS provides process activation, health management, and recycling capabilities to increase the reliability of hosted applications.</span></span>

- <span data-ttu-id="e2e39-124">Как и ASP.NET, службы WCF, размещенные в ASP.NET, могут использовать преимущества общей модели размещения ASP.NET, в которой несколько приложений находятся в общем рабочем процессе для повышения плотности и масштабируемости серверов.</span><span class="sxs-lookup"><span data-stu-id="e2e39-124">Like ASP.NET, WCF services hosted in ASP.NET can take advantage of the ASP.NET shared hosting model where multiple applications reside in a common worker process for improved server density and scalability.</span></span>

- <span data-ttu-id="e2e39-125">Службы WCF, размещенные в IIS, используют ту же динамическую модель компиляции, что и ASP.NET 2,0, что упрощает разработку и развертывание размещенных служб.</span><span class="sxs-lookup"><span data-stu-id="e2e39-125">WCF services hosted in IIS use the same dynamic compilation model as ASP.NET 2.0, which simplifies development and deployment of hosted services.</span></span>

<span data-ttu-id="e2e39-126">При принятии решения о размещении служб WCF в IIS важно помнить, что IIS 5,1 и IIS 6,0 ограничены только HTTP-связью.</span><span class="sxs-lookup"><span data-stu-id="e2e39-126">When deciding to host WCF services in IIS, it is important to remember that IIS 5.1 and IIS 6.0 are limited to HTTP communication only.</span></span> <span data-ttu-id="e2e39-127">Дополнительные сведения о выборе среды размещения см. в разделе [службы хостинга](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="e2e39-127">For more information about choosing a hosting environment, see [Hosting Services](../hosting-services.md).</span></span>

## <a name="deploy-an-iis-hosted-wcf-service"></a><span data-ttu-id="e2e39-128">Развертывание размещенной в IIS службы WCF</span><span class="sxs-lookup"><span data-stu-id="e2e39-128">Deploy an IIS-hosted WCF service</span></span>

<span data-ttu-id="e2e39-129">Разработка и развертывание службы WCF, размещенной в IIS, состоит из следующих задач.</span><span class="sxs-lookup"><span data-stu-id="e2e39-129">Developing and deploying an IIS-hosted WCF service consists of the following tasks:</span></span>

- <span data-ttu-id="e2e39-130">Убедитесь, что службы IIS, ASP.NET, WCF и компонент активации HTTP WCF правильно установлены и зарегистрированы.</span><span class="sxs-lookup"><span data-stu-id="e2e39-130">Ensure that IIS, ASP.NET, WCF, and the WCF HTTP activation component are correctly installed and registered.</span></span>

- <span data-ttu-id="e2e39-131">Создайте новое приложение IIS или повторно используйте существующее приложение ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e2e39-131">Create a new IIS application, or reuse an existing ASP.NET application.</span></span>

- <span data-ttu-id="e2e39-132">Создайте SVC-файл для службы WCF.</span><span class="sxs-lookup"><span data-stu-id="e2e39-132">Create a .svc file for the WCF service.</span></span>

- <span data-ttu-id="e2e39-133">Развертывание реализации службы в приложение IIS.</span><span class="sxs-lookup"><span data-stu-id="e2e39-133">Deploy the service implementation to the IIS application.</span></span>

- <span data-ttu-id="e2e39-134">Настройте службу WCF.</span><span class="sxs-lookup"><span data-stu-id="e2e39-134">Configure the WCF service.</span></span>

<span data-ttu-id="e2e39-135">Обсуждение каждой из этих задач см. в разделе [Deploying an Internet Information Services-Hosted WCF Service](deploying-an-internet-information-services-hosted-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="e2e39-135">For a discussion of each of these tasks, see [Deploying an Internet Information Services-Hosted WCF Service](deploying-an-internet-information-services-hosted-wcf-service.md).</span></span>

## <a name="wcf-services-and-aspnet"></a><span data-ttu-id="e2e39-136">Службы WCF и ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e2e39-136">WCF services and ASP.NET</span></span>

<span data-ttu-id="e2e39-137">Службы WCF могут размещаться либо параллельно с ASP.NET, либо в режиме совместимости ASP.NET, в котором службы могут использовать все преимущества функций, предоставляемых платформой веб-приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e2e39-137">WCF services can be hosted either side-by-side with ASP.NET or in ASP.NET Compatibility Mode in which services can take full advantage of features provided by the ASP.NET Web application platform.</span></span> <span data-ttu-id="e2e39-138">Описание этих функций см. в разделе [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="e2e39-138">For a discussion of these features, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2e39-139">См. также</span><span class="sxs-lookup"><span data-stu-id="e2e39-139">See also</span></span>

- [<span data-ttu-id="e2e39-140">Расширение размещения с использованием ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="e2e39-140">Extending Hosting Using ServiceHostFactory</span></span>](../extending/extending-hosting-using-servicehostfactory.md)
- [<span data-ttu-id="e2e39-141">Развертывание службы WCF, размещенной в IIS</span><span class="sxs-lookup"><span data-stu-id="e2e39-141">Deploying an Internet Information Services-Hosted WCF Service</span></span>](deploying-an-internet-information-services-hosted-wcf-service.md)
- [<span data-ttu-id="e2e39-142">Службы WCF и ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e2e39-142">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="e2e39-143">Рекомендации по размещению в службах IIS</span><span class="sxs-lookup"><span data-stu-id="e2e39-143">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="e2e39-144">Настройка IIS 7.0 для Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e2e39-144">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>](configuring-iis-for-wcf.md)
- <span data-ttu-id="e2e39-145">[Функции размещения Windows Server App Fabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e2e39-145">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
