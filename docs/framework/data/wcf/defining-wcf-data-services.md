---
description: 'Дополнительные сведения: определение службы данных WCF'
title: Определение служб данных WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: 43a4887226b03e80c4a966a118f210fe8a28000d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766092"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="855bc-103">Определение служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="855bc-103">Defining WCF Data Services</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="855bc-104">В этом разделе описывается создание и Настройка службы данных WCF для предоставления данных в виде веб-канала Open Data Protocol (OData).</span><span class="sxs-lookup"><span data-stu-id="855bc-104">This section describes how to create and configure WCF Data Services to expose data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="855bc-105">Дополнительные сведения о базовых шагах, необходимых для создания службы данных, см. в разделе [предоставление данных в виде службы](exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="855bc-105">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="855bc-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="855bc-106">In This Section</span></span>

 [<span data-ttu-id="855bc-107">Настройка службы данных</span><span class="sxs-lookup"><span data-stu-id="855bc-107">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="855bc-108">Описывает параметры конфигурации службы данных, предоставляемые службы данных WCF.</span><span class="sxs-lookup"><span data-stu-id="855bc-108">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="855bc-109">Поставщики служб данных</span><span class="sxs-lookup"><span data-stu-id="855bc-109">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

 <span data-ttu-id="855bc-110">Описывает модели поставщиков для предоставления данных в виде службы данных.</span><span class="sxs-lookup"><span data-stu-id="855bc-110">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="855bc-111">Операции служб</span><span class="sxs-lookup"><span data-stu-id="855bc-111">Service Operations</span></span>](service-operations-wcf-data-services.md)

 <span data-ttu-id="855bc-112">Описывает определение операций службы, которые предоставляют доступ к методам на сервере.</span><span class="sxs-lookup"><span data-stu-id="855bc-112">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="855bc-113">Настройка канала</span><span class="sxs-lookup"><span data-stu-id="855bc-113">Feed Customization</span></span>](feed-customization-wcf-data-services.md)

 <span data-ttu-id="855bc-114">Описывает создание сопоставлений между сущностями модели данных, определенной поставщиком службы данных, и элементами канала данных.</span><span class="sxs-lookup"><span data-stu-id="855bc-114">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="855bc-115">Перехватчики</span><span class="sxs-lookup"><span data-stu-id="855bc-115">Interceptors</span></span>](interceptors-wcf-data-services.md)

 <span data-ttu-id="855bc-116">Описывает определение методов перехватчиков для применения к запросам к службе данных пользовательской бизнес-логики.</span><span class="sxs-lookup"><span data-stu-id="855bc-116">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="855bc-117">Разработка и развертывание службы данных WCF</span><span class="sxs-lookup"><span data-stu-id="855bc-117">Developing and Deploying WCF Data Services</span></span>](developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="855bc-118">Описывает разработку и развертывание службы данных с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="855bc-118">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="855bc-119">Защита служб WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="855bc-119">Securing WCF Data Services</span></span>](securing-wcf-data-services.md)

 <span data-ttu-id="855bc-120">Содержит описание проверки подлинности и авторизации для службы данных и другие рекомендации по безопасности.</span><span class="sxs-lookup"><span data-stu-id="855bc-120">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="855bc-121">Размещение службы данных</span><span class="sxs-lookup"><span data-stu-id="855bc-121">Hosting the Data Service</span></span>](hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="855bc-122">Описывает метод выбора размещения для службы данных.</span><span class="sxs-lookup"><span data-stu-id="855bc-122">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="855bc-123">Управление версиями служб данных</span><span class="sxs-lookup"><span data-stu-id="855bc-123">Data Service Versioning</span></span>](data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="855bc-124">Описывает работу с различными версиями OData.</span><span class="sxs-lookup"><span data-stu-id="855bc-124">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="855bc-125">Сведения о реализации протокола служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="855bc-125">WCF Data Services Protocol Implementation Details</span></span>](wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="855bc-126">Описывает необязательные функции протокола OData, которые в настоящее время не реализованы службы данных WCF.</span><span class="sxs-lookup"><span data-stu-id="855bc-126">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="855bc-127">См. также</span><span class="sxs-lookup"><span data-stu-id="855bc-127">See also</span></span>

- [<span data-ttu-id="855bc-128">Библиотека клиентов служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="855bc-128">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="855bc-129">Доступ к ресурсам служб данных</span><span class="sxs-lookup"><span data-stu-id="855bc-129">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="855bc-130">Начало работы</span><span class="sxs-lookup"><span data-stu-id="855bc-130">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
