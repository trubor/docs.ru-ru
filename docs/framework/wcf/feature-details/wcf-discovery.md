---
description: 'Дополнительные сведения: Обнаружение WCF'
title: Обнаружение WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 67fa5800209676b11e9e49171483bf514b6a190a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779638"
---
# <a name="wcf-discovery"></a><span data-ttu-id="08050-103">Обнаружение WCF</span><span class="sxs-lookup"><span data-stu-id="08050-103">WCF Discovery</span></span>

<span data-ttu-id="08050-104">Windows Communication Foundation (WCF) предоставляет поддержку для обеспечения возможности обнаружения служб во время выполнения с помощью протокола WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="08050-104">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="08050-105">Службы WCF могут объявлять о доступности в сети с помощью многоадресного сообщения или прокси-сервера обнаружения.</span><span class="sxs-lookup"><span data-stu-id="08050-105">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="08050-106">Клиентские приложения могут осуществлять поиск служб, отвечающих набору указанных критериев, в сети или на прокси-сервере обнаружения.</span><span class="sxs-lookup"><span data-stu-id="08050-106">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="08050-107">В подразделах этого раздела представлены общие сведения и описание модели программирования данной функции.</span><span class="sxs-lookup"><span data-stu-id="08050-107">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08050-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="08050-108">In This Section</span></span>  

 [<span data-ttu-id="08050-109">Общие сведения об обнаружении WCF</span><span class="sxs-lookup"><span data-stu-id="08050-109">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="08050-110">Содержит общие сведения о поддержке WS-Discovery, предоставляемой WCF.</span><span class="sxs-lookup"><span data-stu-id="08050-110">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="08050-111">Модель объектов обнаружения WCF</span><span class="sxs-lookup"><span data-stu-id="08050-111">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="08050-112">Содержит описание классов объектной модели и расширяемости поддержки WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="08050-112">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="08050-113">Практическое руководство. Как программно добавить возможность обнаружения к службе и клиенту WCF</span><span class="sxs-lookup"><span data-stu-id="08050-113">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="08050-114">Показывает, как сделать службу Windows Communication Foundation (WCF) обнаруживаемой.</span><span class="sxs-lookup"><span data-stu-id="08050-114">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="08050-115">Реализация прокси-сервера обнаружения</span><span class="sxs-lookup"><span data-stu-id="08050-115">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="08050-116">Содержит описание шагов, необходимых для реализации прокси-сервера обнаружения, службы, доступной для обнаружения, которая регистрируется на прокси-сервере обнаружения, и клиента, использующего прокси-сервер обнаружения для поиска этой службы.</span><span class="sxs-lookup"><span data-stu-id="08050-116">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="08050-117">Управление версиями обнаружения</span><span class="sxs-lookup"><span data-stu-id="08050-117">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="08050-118">Содержит общие сведения о реализации прототипа некоторых новых функций обнаружения.</span><span class="sxs-lookup"><span data-stu-id="08050-118">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="08050-119">Также приводятся общие сведения о выборе версии обнаружения.</span><span class="sxs-lookup"><span data-stu-id="08050-119">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="08050-120">Настройка обнаружения в файле конфигурации</span><span class="sxs-lookup"><span data-stu-id="08050-120">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="08050-121">Настройка обнаружения в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="08050-121">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="08050-122">Использование клиентского канала обнаружения</span><span class="sxs-lookup"><span data-stu-id="08050-122">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="08050-123">Показывает, как использовать клиентский канал обнаружения при записи клиентского приложения WCF.</span><span class="sxs-lookup"><span data-stu-id="08050-123">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
