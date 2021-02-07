---
description: 'Дополнительные сведения: служба маршрутизатора обнаружения'
title: Служба обнаружения маршрутизатора
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: f5fa4cd19758bef0b867fafc5af4b9cf6df27028
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726719"
---
# <a name="discovery-router-service"></a><span data-ttu-id="eefef-103">Служба обнаружения маршрутизатора</span><span class="sxs-lookup"><span data-stu-id="eefef-103">Discovery Router Service</span></span>

<span data-ttu-id="eefef-104">В этом образце показаны способы направления сообщений обнаружения другой конечной точке.</span><span class="sxs-lookup"><span data-stu-id="eefef-104">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="eefef-105">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="eefef-105">Demonstrates</span></span>  

 <span data-ttu-id="eefef-106">Маршрутизация обнаружения</span><span class="sxs-lookup"><span data-stu-id="eefef-106">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="eefef-107">Разговор</span><span class="sxs-lookup"><span data-stu-id="eefef-107">Discussion</span></span>  

 <span data-ttu-id="eefef-108">Маршрутизация обнаружения используется в случаях, когда клиент выполняет поиск службы с использованием прокси-сервера и этот прокси-сервер не имеет данных об этой службе, но обладает сведениями о другом прокси-сервере.</span><span class="sxs-lookup"><span data-stu-id="eefef-108">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="eefef-109">Этот прокси-сервер может направлять пакет обнаружения от этого клиента второму прокси-серверу.</span><span class="sxs-lookup"><span data-stu-id="eefef-109">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="eefef-110">Второй прокси-сервер может выполнить поиск службы и вернуть ответы исходному клиенту.</span><span class="sxs-lookup"><span data-stu-id="eefef-110">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="eefef-111">В этом образце клиент отправляет сообщение компоненту маршрутизации обнаружения.</span><span class="sxs-lookup"><span data-stu-id="eefef-111">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="eefef-112">Это сообщение отправляется определенной конечной точке на маршрутизаторе обнаружения.</span><span class="sxs-lookup"><span data-stu-id="eefef-112">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="eefef-113">Затем маршрутизатор перенаправляет сообщение по многоадресной рассылке конечной точке определяемой пользователем процедуре.</span><span class="sxs-lookup"><span data-stu-id="eefef-113">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="eefef-114">Сообщение зонда передается по многоадресной рассылке конечной точке, а служба, прослушивающая адрес многоадресной рассылки определяемой пользователем процедуры, реагирует на маршрутизатор обнаружения.</span><span class="sxs-lookup"><span data-stu-id="eefef-114">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="eefef-115">Маршрутизатор обнаружения выполняет сбор ответов и отправляет их обратно клиенту.</span><span class="sxs-lookup"><span data-stu-id="eefef-115">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eefef-116">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="eefef-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="eefef-117">Выполните сборку примера.</span><span class="sxs-lookup"><span data-stu-id="eefef-117">Build the sample.</span></span>  
  
2. <span data-ttu-id="eefef-118">Запустите исполняемый файл DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="eefef-118">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="eefef-119">Выполните исполняемый файл службы из каталога сборки.</span><span class="sxs-lookup"><span data-stu-id="eefef-119">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="eefef-120">Выполните исполняемый файл клиента.</span><span class="sxs-lookup"><span data-stu-id="eefef-120">Run the client executable.</span></span> <span data-ttu-id="eefef-121">Обратите внимание, что клиент нашел службу.</span><span class="sxs-lookup"><span data-stu-id="eefef-121">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eefef-122">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="eefef-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eefef-123">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="eefef-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="eefef-124">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="eefef-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eefef-125">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="eefef-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
