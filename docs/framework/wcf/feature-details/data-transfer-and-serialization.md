---
description: 'Дополнительные сведения: Передача данных и сериализация'
title: Передача данных и сериализация
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 50e5068efc10d706fb9ce2634998408e48037ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756569"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="24ae1-103">Передача данных и сериализация</span><span class="sxs-lookup"><span data-stu-id="24ae1-103">Data Transfer and Serialization</span></span>

<span data-ttu-id="24ae1-104">В распределенных системах для выполнения каких-либо задач клиенты и службы обмениваются данными.</span><span class="sxs-lookup"><span data-stu-id="24ae1-104">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="24ae1-105">Разработчику службы или клиента необходимо также понимать, как Windows Communication Foundation (WCF) обрабатывает данные и сериализацию данных для создания эффективных и удобных в обслуживании приложений.</span><span class="sxs-lookup"><span data-stu-id="24ae1-105">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24ae1-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="24ae1-106">In This Section</span></span>  

 [<span data-ttu-id="24ae1-107">Задание передачи данных в контрактах служб</span><span class="sxs-lookup"><span data-stu-id="24ae1-107">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="24ae1-108">Базовые принципы передачи данных в службах.</span><span class="sxs-lookup"><span data-stu-id="24ae1-108">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="24ae1-109">Использование контрактов данных</span><span class="sxs-lookup"><span data-stu-id="24ae1-109">Using Data Contracts</span></span>](using-data-contracts.md)  
 <span data-ttu-id="24ae1-110">Понятие контрактов данных и процедур их создания и использования.</span><span class="sxs-lookup"><span data-stu-id="24ae1-110">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="24ae1-111">Сериализатор контракта данных</span><span class="sxs-lookup"><span data-stu-id="24ae1-111">Data Contract Serializer</span></span>](data-contract-serializer.md)  
 <span data-ttu-id="24ae1-112">Сериализация данных с помощью класса <xref:System.Runtime.Serialization.DataContractSerializer> и каких-либо расширений класса <xref:System.Runtime.Serialization.XmlObjectSerializer>.</span><span class="sxs-lookup"><span data-stu-id="24ae1-112">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="24ae1-113">Использование класса XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="24ae1-113">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)  
 <span data-ttu-id="24ae1-114">Способы и причины использования класса <xref:System.Xml.Serialization.XmlSerializer> в качестве альтернативы классу <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="24ae1-114">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="24ae1-115">Использование контрактов сообщений</span><span class="sxs-lookup"><span data-stu-id="24ae1-115">Using Message Contracts</span></span>](using-message-contracts.md)  
 <span data-ttu-id="24ae1-116">Точное управление сообщениями SOAP с помощью контрактов сообщений.</span><span class="sxs-lookup"><span data-stu-id="24ae1-116">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="24ae1-117">Использование класса сообщений</span><span class="sxs-lookup"><span data-stu-id="24ae1-117">Using the Message Class</span></span>](using-the-message-class.md)  
 <span data-ttu-id="24ae1-118">Использование возможностей класса Message.</span><span class="sxs-lookup"><span data-stu-id="24ae1-118">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="24ae1-119">Фильтрация</span><span class="sxs-lookup"><span data-stu-id="24ae1-119">Filtering</span></span>](filtering.md)  
 <span data-ttu-id="24ae1-120">Фильтрация, позволяющая выполнять предварительную обработку сообщений на основе различных критериев.</span><span class="sxs-lookup"><span data-stu-id="24ae1-120">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="24ae1-121">Большие наборы данных и потоковая передача</span><span class="sxs-lookup"><span data-stu-id="24ae1-121">Large Data and Streaming</span></span>](large-data-and-streaming.md)  
 <span data-ttu-id="24ae1-122">Отправка больших фрагментов данных, например двоичных файлов.</span><span class="sxs-lookup"><span data-stu-id="24ae1-122">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="24ae1-123">Вопросы безопасности для данных</span><span class="sxs-lookup"><span data-stu-id="24ae1-123">Security Considerations for Data</span></span>](security-considerations-for-data.md)  
 <span data-ttu-id="24ae1-124">Вопросы, которые необходимо учитывать при решении задач сериализации и передачи данных.</span><span class="sxs-lookup"><span data-stu-id="24ae1-124">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="24ae1-125">Общие сведения об архитектуре передачи данных</span><span class="sxs-lookup"><span data-stu-id="24ae1-125">Data Transfer Architectural Overview</span></span>](data-transfer-architectural-overview.md)  
 <span data-ttu-id="24ae1-126">Описывает общие сведения о структуре обмена данными в WCF.</span><span class="sxs-lookup"><span data-stu-id="24ae1-126">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="24ae1-127">Справочник</span><span class="sxs-lookup"><span data-stu-id="24ae1-127">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="24ae1-128">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="24ae1-128">Related Sections</span></span>  

 [<span data-ttu-id="24ae1-129">Расширение кодировщиков и сериализаторов</span><span class="sxs-lookup"><span data-stu-id="24ae1-129">Extending Encoders and Serializers</span></span>](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="24ae1-130">См. также</span><span class="sxs-lookup"><span data-stu-id="24ae1-130">See also</span></span>

- [<span data-ttu-id="24ae1-131">Рекомендации. Управление версиями контракта данных</span><span class="sxs-lookup"><span data-stu-id="24ae1-131">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="24ae1-132">Управление версиями службы</span><span class="sxs-lookup"><span data-stu-id="24ae1-132">Service Versioning</span></span>](../service-versioning.md)
