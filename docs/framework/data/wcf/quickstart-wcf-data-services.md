---
description: 'Дополнительные сведения: Краткое руководство (службы данных WCF)'
title: Краткое руководство (службы данных WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 92a1b8882f6a7db2ed33f032ad434efd06400421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794953"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="ee26c-103">Краткое руководство (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="ee26c-103">Quickstart (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="ee26c-104">Это краткое руководство поможет вам ознакомиться с службы данных WCF и Open Data Protocol (OData) с помощью серии задач, которые поддерживают разделы в [Начало работы](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ee26c-104">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="ee26c-105">Что вы узнаете</span><span class="sxs-lookup"><span data-stu-id="ee26c-105">What you'll learn</span></span>

<span data-ttu-id="ee26c-106">В первой задаче этого краткого руководства показано, как создать службу данных для предоставления веб-канала OData из образца базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="ee26c-106">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="ee26c-107">В последующих разделах вы получите доступ к каналу OData с помощью веб-браузера, а также создаете клиентское приложение Windows Presentation Foundation (WPF), которое использует канал OData с помощью клиентских библиотек.</span><span class="sxs-lookup"><span data-stu-id="ee26c-107">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ee26c-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="ee26c-108">Prerequisites</span></span>

<span data-ttu-id="ee26c-109">Для выполнения этого краткого руководства установите следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="ee26c-109">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="ee26c-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ee26c-110">Visual Studio</span></span>

- <span data-ttu-id="ee26c-111">Экземпляр SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ee26c-111">An instance of SQL Server.</span></span> <span data-ttu-id="ee26c-112">К ним относятся SQL Server Express, включенные в установку Visual Studio 2015 по умолчанию или как часть рабочей нагрузки **хранения и обработки данных** в visual Studio 2017 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ee26c-112">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="ee26c-113">Наличие учебной базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="ee26c-113">The Northwind sample database.</span></span> <span data-ttu-id="ee26c-114">Чтобы установить базу данных, выполните скрипт Transact-SQL из [баз данных Northwind и Pubs для Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span><span class="sxs-lookup"><span data-stu-id="ee26c-114">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="ee26c-115">Краткие задачи служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="ee26c-115">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="ee26c-116">Создание службы данных</span><span class="sxs-lookup"><span data-stu-id="ee26c-116">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="ee26c-117">Определите приложение ASP.NET, определите модель данных, создайте службу данных и включите доступ к ресурсам.</span><span class="sxs-lookup"><span data-stu-id="ee26c-117">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="ee26c-118">Доступ к службе из веб-браузера</span><span class="sxs-lookup"><span data-stu-id="ee26c-118">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="ee26c-119">Запустите службу из среды Visual Studio и обратитесь к ней с помощью запросов HTTP GET через веб-браузер для получения доступа к предоставляемым каналам.</span><span class="sxs-lookup"><span data-stu-id="ee26c-119">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="ee26c-120">Создание клиентского приложения платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ee26c-120">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="ee26c-121">Создание приложения WPF для использования веб-канала OData, привязки данных к элементам управления Windows, изменения данных в связанных элементах управления и последующей отправки изменений обратно в службу данных.</span><span class="sxs-lookup"><span data-stu-id="ee26c-121">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="ee26c-122">Файлы проекта из готовой версии краткого руководства можно скачать с сайта [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span><span class="sxs-lookup"><span data-stu-id="ee26c-122">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ee26c-123">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="ee26c-123">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee26c-124">Запуск краткого руководства</span><span class="sxs-lookup"><span data-stu-id="ee26c-124">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="ee26c-125">См. также</span><span class="sxs-lookup"><span data-stu-id="ee26c-125">See also</span></span>

- [<span data-ttu-id="ee26c-126">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ee26c-126">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
