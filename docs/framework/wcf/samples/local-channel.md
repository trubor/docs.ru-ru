---
description: Дополнительные сведения о локальном канале
title: Локальный канал
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: a580abc1e8dcd89c40c9fdc02001deb094eb0b05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631753"
---
# <a name="local-channel"></a><span data-ttu-id="30dd8-103">Локальный канал</span><span class="sxs-lookup"><span data-stu-id="30dd8-103">Local Channel</span></span>

<span data-ttu-id="30dd8-104">Локальный канал — это канал транспорта Windows Communication Foundation (WCF), который используется для обмена данными в пределах одного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="30dd8-104">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="30dd8-105">Это полезно в случаях, когда клиент и служба работают на одном домене приложения и требуется избежать увеличения расхода ресурсов типичного WCF-канала (сериализация и десериализация сообщений).</span><span class="sxs-lookup"><span data-stu-id="30dd8-105">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="30dd8-106">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="30dd8-106">Demonstrates</span></span>  

 <span data-ttu-id="30dd8-107">Локальный канал</span><span class="sxs-lookup"><span data-stu-id="30dd8-107">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="30dd8-108">Разговор</span><span class="sxs-lookup"><span data-stu-id="30dd8-108">Discussion</span></span>  

 <span data-ttu-id="30dd8-109">Образец состоит из двух файлов проектов:</span><span class="sxs-lookup"><span data-stu-id="30dd8-109">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="30dd8-110">**Локалчаннел**: программное представление локального канала в текущем домене приложения.</span><span class="sxs-lookup"><span data-stu-id="30dd8-110">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="30dd8-111">В этом проекте отправляющий модуль размещает сообщение в очереди памяти, а получающий модуль выводит его из очереди, получая сообщение.</span><span class="sxs-lookup"><span data-stu-id="30dd8-111">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="30dd8-112">**Клиентандсервице**: этот проект размещает службу в консольном приложении, а затем запускает клиент для вызова службы из того же домена приложения.</span><span class="sxs-lookup"><span data-stu-id="30dd8-112">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="30dd8-113">Конструктор локального канала пропускает стек каналов и процесс сериализации для увеличения скорости.</span><span class="sxs-lookup"><span data-stu-id="30dd8-113">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="30dd8-114">Локальный канал транспорта реализуется при помощи очереди, которая используется для переноса вызовов службы от клиента к службе и возвращения значения клиенту.</span><span class="sxs-lookup"><span data-stu-id="30dd8-114">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="30dd8-115">Вместо сериализации параметров и возвращения значений образец копирует объекты.</span><span class="sxs-lookup"><span data-stu-id="30dd8-115">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="30dd8-116">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="30dd8-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="30dd8-117">Постройте и запустите решение LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="30dd8-117">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="30dd8-118">Запускается узел службы, клиент вызывает службу при помощи локального канала.</span><span class="sxs-lookup"><span data-stu-id="30dd8-118">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="30dd8-119">Появляется окно консоли, в котором отображаются результаты вызова службы.</span><span class="sxs-lookup"><span data-stu-id="30dd8-119">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="30dd8-120">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="30dd8-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="30dd8-121">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="30dd8-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="30dd8-122">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="30dd8-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="30dd8-123">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="30dd8-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
