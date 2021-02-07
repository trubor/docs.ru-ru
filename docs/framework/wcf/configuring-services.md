---
description: 'Дополнительные сведения: Настройка служб WCF'
title: Настройка служб WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 1c0df8c7d9b4e2b1a032f02e74db2de4a8de020c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720843"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="943a8-103">Настройка служб WCF</span><span class="sxs-lookup"><span data-stu-id="943a8-103">Configuring WCF services</span></span>

<span data-ttu-id="943a8-104">После разработки и реализации контракта службы можно переходить к настройке службы.</span><span class="sxs-lookup"><span data-stu-id="943a8-104">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="943a8-105">В ходе этого определяется и настраивается способ представления службы клиентам, включая задание адреса, по которому ее можно найти, транспорт и кодирование сообщений, используемые для отправки и получения сообщений, а также требуемый тип безопасности.</span><span class="sxs-lookup"><span data-stu-id="943a8-105">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="943a8-106">В используемой конфигурации предусматриваются все способы (принудительно в коде или с помощью файла конфигурации) определения и настройки различных аспектов службы, таких как задание адресов конечных точек, используемых транспортов и схем безопасности.</span><span class="sxs-lookup"><span data-stu-id="943a8-106">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="943a8-107">На практике написание конфигурации является основной частью программирования приложений WCF.</span><span class="sxs-lookup"><span data-stu-id="943a8-107">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="943a8-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="943a8-108">In This Section</span></span>  

 [<span data-ttu-id="943a8-109">Упрощенная конфигурация</span><span class="sxs-lookup"><span data-stu-id="943a8-109">Simplified Configuration</span></span>](simplified-configuration.md)  
 <span data-ttu-id="943a8-110">Начиная с платформа .NET Framework 4, WCF поставляется с новой моделью конфигурации по умолчанию, которая упрощает требования к конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="943a8-110">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="943a8-111">Если не указать конфигурацию WCF для конкретной службы, среда выполнения автоматически настроит службу с конечными точками по умолчанию, привязками и поведением.</span><span class="sxs-lookup"><span data-stu-id="943a8-111">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="943a8-112">Настройка служб с использованием файлов конфигурации</span><span class="sxs-lookup"><span data-stu-id="943a8-112">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
 <span data-ttu-id="943a8-113">Служба Windows Communication Foundation (WCF) настраивается с помощью технологии конфигурации платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="943a8-113">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="943a8-114">Чаще всего XML-элементы добавляются в файл Web.config для сайта службы IIS (IIS), на котором размещена служба WCF.</span><span class="sxs-lookup"><span data-stu-id="943a8-114">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="943a8-115">Эти элементы позволяют изменять данные, такие как адреса конечных точек (фактические адреса, используемые для взаимодействия со службой), по схеме компьютер-компьютер.</span><span class="sxs-lookup"><span data-stu-id="943a8-115">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="943a8-116">Привязки</span><span class="sxs-lookup"><span data-stu-id="943a8-116">Bindings</span></span>](bindings.md)  
 <span data-ttu-id="943a8-117">Кроме того, в состав WCF входит несколько общих конфигураций, предоставляемых системой, в виде привязок, которые позволяют быстро выбрать основные возможности взаимодействия клиента и службы, такие как транспорты, безопасность и используемые кодировки сообщений.</span><span class="sxs-lookup"><span data-stu-id="943a8-117">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="943a8-118">Конечные точки</span><span class="sxs-lookup"><span data-stu-id="943a8-118">Endpoints</span></span>](endpoints.md)  
 <span data-ttu-id="943a8-119">Все взаимодействие со службой WCF осуществляется через *конечные точки* службы.</span><span class="sxs-lookup"><span data-stu-id="943a8-119">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="943a8-120">Конечные точки содержат контракт, сведения о конфигурации, указанные в привязках, и адреса, указывающие, где расположена служба и где получить информацию о ней.</span><span class="sxs-lookup"><span data-stu-id="943a8-120">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="943a8-121">Защита служб</span><span class="sxs-lookup"><span data-stu-id="943a8-121">Securing Services</span></span>](securing-services.md)  
 <span data-ttu-id="943a8-122">С помощью WCF и существующих механизмов безопасности можно реализовать конфиденциальность, целостность, проверку подлинности и авторизацию в любой службе.</span><span class="sxs-lookup"><span data-stu-id="943a8-122">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="943a8-123">Также можно выполнить аудит на предмет успешных и неудачных попыток выполнения службы.</span><span class="sxs-lookup"><span data-stu-id="943a8-123">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="943a8-124">Создание служб, поддерживающих взаимодействие с базовым профилем WS-I 1.1</span><span class="sxs-lookup"><span data-stu-id="943a8-124">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="943a8-125">Требования к развертыванию службы с возможностью взаимодействия со службами и клиентами, размещенными на другой платформе или в другой операционной системе, указаны в спецификации WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="943a8-125">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="943a8-126">Справочник</span><span class="sxs-lookup"><span data-stu-id="943a8-126">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="943a8-127">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="943a8-127">Related Sections</span></span>  

 [<span data-ttu-id="943a8-128">Базовый жизненный цикл программирования</span><span class="sxs-lookup"><span data-stu-id="943a8-128">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="943a8-129">Проектирование и реализация служб</span><span class="sxs-lookup"><span data-stu-id="943a8-129">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
 [<span data-ttu-id="943a8-130">Размещение служб</span><span class="sxs-lookup"><span data-stu-id="943a8-130">Hosting Services</span></span>](hosting-services.md)  
  
 [<span data-ttu-id="943a8-131">Создание клиентов</span><span class="sxs-lookup"><span data-stu-id="943a8-131">Building Clients</span></span>](building-clients.md)  
  
 [<span data-ttu-id="943a8-132">Введение в расширяемость</span><span class="sxs-lookup"><span data-stu-id="943a8-132">Introduction to Extensibility</span></span>](introduction-to-extensibility.md)  
  
 [<span data-ttu-id="943a8-133">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="943a8-133">Administration and Diagnostics</span></span>](./diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="943a8-134">См. также</span><span class="sxs-lookup"><span data-stu-id="943a8-134">See also</span></span>

- [<span data-ttu-id="943a8-135">Базовое программирование для WCF</span><span class="sxs-lookup"><span data-stu-id="943a8-135">Basic WCF Programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="943a8-136">Общие сведения об основных понятиях</span><span class="sxs-lookup"><span data-stu-id="943a8-136">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="943a8-137">Сведения о функции WCF</span><span class="sxs-lookup"><span data-stu-id="943a8-137">WCF Feature Details</span></span>](./feature-details/index.md)
