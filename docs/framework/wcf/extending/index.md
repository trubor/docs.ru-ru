---
description: 'Дополнительные сведения: Расширение WCF'
title: Расширение WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: e243e03a72e6530716959499c311bfe37a39b054
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644155"
---
# <a name="extending-wcf"></a><span data-ttu-id="76753-103">Расширение WCF</span><span class="sxs-lookup"><span data-stu-id="76753-103">Extending WCF</span></span>

<span data-ttu-id="76753-104">Windows Communication Foundation (WCF) позволяет изменять и расширять компоненты времени выполнения для точного управления и расширения приложений на основе служб.</span><span class="sxs-lookup"><span data-stu-id="76753-104">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="76753-105">Статьи данного раздела подробно описывают архитектуру расширяемости.</span><span class="sxs-lookup"><span data-stu-id="76753-105">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="76753-106">Дополнительные сведения о базовом программировании см. в разделе [Basic WCF Programming](../basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="76753-106">For more information about basic programming, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76753-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="76753-107">In This Section</span></span>  

 [<span data-ttu-id="76753-108">Расширение ServiceHost и уровень модели службы</span><span class="sxs-lookup"><span data-stu-id="76753-108">Extending ServiceHost and the Service Model Layer</span></span>](extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="76753-109">Уровень модели службы отвечает за удаление входящих сообщений из базовых каналов, их перевод в вызовы метода в коде приложения и отправку результатов обратно вызывающему коду.</span><span class="sxs-lookup"><span data-stu-id="76753-109">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="76753-110">Расширения модели службы изменяют или реализуют порядок и компоненты выполнения или взаимодействия, в том числе компоненты, включающие возможности диспетчера, пользовательские поведения, перехват сообщений и параметров, а также другие расширяемые возможности.</span><span class="sxs-lookup"><span data-stu-id="76753-110">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="76753-111">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="76753-111">Extending Bindings</span></span>](extending-bindings.md)  
 <span data-ttu-id="76753-112">Привязки - это объекты, которые описывают сведения о связи, требуемые для подключения к конечной точке.</span><span class="sxs-lookup"><span data-stu-id="76753-112">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="76753-113">Расширения привязок и пользовательские привязки реализуют пользовательскую функциональность связи, необходимую для поддержки возможностей приложения.</span><span class="sxs-lookup"><span data-stu-id="76753-113">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="76753-114">Расширение уровня каналов</span><span class="sxs-lookup"><span data-stu-id="76753-114">Extending the Channel Layer</span></span>](extending-the-channel-layer.md)  
 <span data-ttu-id="76753-115">Уровень канала находится в уровне модели службы и отвечает за обмен сообщениями между клиентами и службами.</span><span class="sxs-lookup"><span data-stu-id="76753-115">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="76753-116">Расширения каналов могут реализовывать новые функциональные возможности протокола, такие как безопасность.</span><span class="sxs-lookup"><span data-stu-id="76753-116">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="76753-117">Они также реализуют транспортные функциональные возможности, такие как новый сетевой транспорт для передачи сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="76753-117">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="76753-118">Расширение безопасности</span><span class="sxs-lookup"><span data-stu-id="76753-118">Extending Security</span></span>](extending-security.md)  
 <span data-ttu-id="76753-119">Безопасность в WCF состоит из безопасности передаваемых данных (целостность, конфиденциальность и проверка подлинности), контроля доступа (авторизации) и аудита.</span><span class="sxs-lookup"><span data-stu-id="76753-119">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="76753-120">Классы, найденные в `IdentityModel` пространстве имен, используются WCF для контроля доступа.</span><span class="sxs-lookup"><span data-stu-id="76753-120">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="76753-121">Понимание архитектуры безопасности позволяет создавать пользовательские типы утверждений для использования в системах управления доступом.</span><span class="sxs-lookup"><span data-stu-id="76753-121">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="76753-122">Расширение системы метаданных</span><span class="sxs-lookup"><span data-stu-id="76753-122">Extending the Metadata System</span></span>](extending-the-metadata-system.md)  
 <span data-ttu-id="76753-123">Система метаданных WCF — это группа классов и интерфейсов, представляющих метаданные, необходимые для реализации приложений на основе служб.</span><span class="sxs-lookup"><span data-stu-id="76753-123">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="76753-124">Можно изменять или расширять классы, реализовывать и настраивать интерфейсы для экспорта и импорта пользовательских метаданных, например расширений языка WSDL или пользовательских утверждений WS-PolicyAttachments.</span><span class="sxs-lookup"><span data-stu-id="76753-124">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="76753-125">Расширение кодировщиков и сериализаторов</span><span class="sxs-lookup"><span data-stu-id="76753-125">Extending Encoders and Serializers</span></span>](extending-encoders-and-serializers.md)  
 <span data-ttu-id="76753-126">Кодировщики и сериализаторы преобразовывают данные из одной формы в другую.</span><span class="sxs-lookup"><span data-stu-id="76753-126">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="76753-127">Статьи данного раздела описывают, как расширять переданные классы для удовлетворения конкретных требований.</span><span class="sxs-lookup"><span data-stu-id="76753-127">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="76753-128">Справочник</span><span class="sxs-lookup"><span data-stu-id="76753-128">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="76753-129">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="76753-129">Related Sections</span></span>  

 [<span data-ttu-id="76753-130">Базовое программирование для WCF</span><span class="sxs-lookup"><span data-stu-id="76753-130">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="76753-131">Сведения о функции WCF</span><span class="sxs-lookup"><span data-stu-id="76753-131">WCF Feature Details</span></span>](../feature-details/index.md)  
  
 [<span data-ttu-id="76753-132">Правила и рекомендации</span><span class="sxs-lookup"><span data-stu-id="76753-132">Guidelines and Best Practices</span></span>](../guidelines-and-best-practices.md)
