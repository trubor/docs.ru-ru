---
description: Дополнительные сведения о развертывании служб
title: Развертывание служб
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 6a0b1d88410b865f57cd1eb16f070842a75ddb07
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646001"
---
# <a name="deploying-services"></a><span data-ttu-id="e4b06-103">Развертывание служб</span><span class="sxs-lookup"><span data-stu-id="e4b06-103">Deploying Services</span></span>

<span data-ttu-id="e4b06-104">В этом разделе описывается, как можно развернуть приложение Windows Communication Foundation (WCF) в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="e4b06-104">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="e4b06-105">Выбор среды размещения для приложения</span><span class="sxs-lookup"><span data-stu-id="e4b06-105">Choosing the Hosting Environment for Your Application</span></span>  

 <span data-ttu-id="e4b06-106">Службы WCF предназначены для работы в любом процессе Windows, который поддерживает управляемый код.</span><span class="sxs-lookup"><span data-stu-id="e4b06-106">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="e4b06-107">Для активации службы ее необходимо разместить в среде выполнения, которая создает эту службу и управляет ее контекстом и временем существования.</span><span class="sxs-lookup"><span data-stu-id="e4b06-107">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="e4b06-108">Варианты размещения могут быть самыми различными - от выполнения внутри простейшего консольного приложения до работы в серверных средах (таких как службы Windows, службы IIS) или внутри рабочего процесса, управляемого службой активации Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="e4b06-108">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="e4b06-109">Чтобы просмотреть различные варианты размещения для приложения WCF, см. раздел [службы хостинга](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="e4b06-109">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b06-110">См. также</span><span class="sxs-lookup"><span data-stu-id="e4b06-110">See also</span></span>

- [<span data-ttu-id="e4b06-111">Размещение</span><span class="sxs-lookup"><span data-stu-id="e4b06-111">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="e4b06-112">Размещение служб</span><span class="sxs-lookup"><span data-stu-id="e4b06-112">Hosting Services</span></span>](../hosting-services.md)
