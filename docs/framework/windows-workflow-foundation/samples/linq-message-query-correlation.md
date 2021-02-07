---
description: Дополнительные сведения см. в статье корреляция запросов сообщений LINQ.
title: Корреляция запросов сообщений LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 7b979e3bdc2c0ede8f4f9d4595957f90581a0ecc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755282"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="243ac-103">Корреляция запросов сообщений LINQ</span><span class="sxs-lookup"><span data-stu-id="243ac-103">LINQ Message Query Correlation</span></span>

<span data-ttu-id="243ac-104">Этот образец демонстрирует, как выполнять корреляцию на основе содержимого с использованием пользовательской реализации <xref:System.ServiceModel.Dispatcher.MessageQuery> (в отличие от системной реализации <xref:System.ServiceModel.XPathMessageQuery>).</span><span class="sxs-lookup"><span data-stu-id="243ac-104">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="243ac-105">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="243ac-105">Demonstrates</span></span>  

 <span data-ttu-id="243ac-106">Пользовательская корреляция <xref:System.ServiceModel.Dispatcher.MessageQuery> на основе содержимого.</span><span class="sxs-lookup"><span data-stu-id="243ac-106">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="243ac-107">Разговор</span><span class="sxs-lookup"><span data-stu-id="243ac-107">Discussion</span></span>  

 <span data-ttu-id="243ac-108">Этот образец показывает, как выполняется расширение базового класса <xref:System.ServiceModel.Dispatcher.MessageQuery> с целью корреляции.</span><span class="sxs-lookup"><span data-stu-id="243ac-108">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="243ac-109">Пользовательская реализация `LinqMessageQuery` позволяет пользователям выдавать XName для поиска внутри сообщения с использованием XLinq.</span><span class="sxs-lookup"><span data-stu-id="243ac-109">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="243ac-110">Данные, полученные в результате выполнения запроса, используются для формирования ключа корреляции с целью перенаправления сообщений в соответствующий экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="243ac-110">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="243ac-111">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="243ac-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="243ac-112">В этом образце доступ к службе рабочего процесса предоставляется через конечные точки HTTP.</span><span class="sxs-lookup"><span data-stu-id="243ac-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="243ac-113">Чтобы выполнить этот пример, необходимо добавить соответствующие списки ACL URL-адресов (см. Дополнительные сведения о [настройке HTTP и HTTPS](../../wcf/feature-details/configuring-http-and-https.md) ), запустив Visual Studio от имени администратора или выполнив следующую команду в командной строке с повышенными привилегиями, чтобы добавить соответствующие списки ACL.</span><span class="sxs-lookup"><span data-stu-id="243ac-113">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="243ac-114">Убедитесь, что подставлены нужный домен и имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="243ac-114">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="243ac-115">После добавления списков управления доступом по URL-адресу выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="243ac-115">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="243ac-116">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="243ac-116">Build the solution.</span></span>  
  
    2. <span data-ttu-id="243ac-117">Задайте несколько проектов запуска, щелкнув решение правой кнопкой мыши и выбрав пункт **задать запускаемые проекты**.</span><span class="sxs-lookup"><span data-stu-id="243ac-117">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="243ac-118">Добавьте **службу** и **клиент** (в этом порядке) в качестве нескольких запускаемых проектов.</span><span class="sxs-lookup"><span data-stu-id="243ac-118">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="243ac-119">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="243ac-119">Run the application.</span></span> <span data-ttu-id="243ac-120">На консоль клиентского приложения выводится рабочий процесс, вначале отправляющий заказ, затем получающий идентификатор заказа на покупку и, наконец, подтверждающий заказ.</span><span class="sxs-lookup"><span data-stu-id="243ac-120">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="243ac-121">В окне службы будут выведены сведения об обрабатываемых запросах.</span><span class="sxs-lookup"><span data-stu-id="243ac-121">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="243ac-122">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="243ac-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="243ac-123">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="243ac-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="243ac-124">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="243ac-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="243ac-125">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="243ac-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
