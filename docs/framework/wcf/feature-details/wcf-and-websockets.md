---
description: 'Дополнительные сведения: WCF и WebSockets'
title: WCF и WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: 6b0d8c33000a65bf3bbf834f66119d65768b3cb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755984"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="661cb-103">WCF и WebSockets</span><span class="sxs-lookup"><span data-stu-id="661cb-103">WCF and WebSockets</span></span>

<span data-ttu-id="661cb-104">В .NET Framework версии 4.5 добавлена поддержка WebSockets в службах Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="661cb-104">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="661cb-105">WebSockets - это эффективная, основанная на стандартах технология, обеспечивающая двусторонний обмен сообщениями через стандартные HTTP-порты 80 и 443.</span><span class="sxs-lookup"><span data-stu-id="661cb-105">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="661cb-106">Использование стандартных HTTP-портов позволяет WebSockets устанавливать связь по сети через посредников.</span><span class="sxs-lookup"><span data-stu-id="661cb-106">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="661cb-107">Были добавлены две стандартные привязки для поддержки обмена данными через транспорт WebSocket.</span><span class="sxs-lookup"><span data-stu-id="661cb-107">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="661cb-108"><xref:System.ServiceModel.NetHttpBinding> и <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="661cb-108"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="661cb-109">Параметры, относящиеся к WebSocket, можно настроить в <xref:System.ServiceModel.Channels.HttpTransportBindingElement> с помощью <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> Свойства.</span><span class="sxs-lookup"><span data-stu-id="661cb-109">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="661cb-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="661cb-110">In This Section</span></span>  

 [<span data-ttu-id="661cb-111">Использование NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="661cb-111">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)  
 <span data-ttu-id="661cb-112">Описывает <xref:System.ServiceModel.NetHttpBinding> и его настройку.</span><span class="sxs-lookup"><span data-stu-id="661cb-112">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="661cb-113">Практическое руководство. Создание службы WCF, обменивающейся данными через WebSockets</span><span class="sxs-lookup"><span data-stu-id="661cb-113">How to: Create a WCF Service that Communicates over WebSockets</span></span>](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="661cb-114">Описывает процесс создания службы WCF, обменивающейся данными через Websockets.</span><span class="sxs-lookup"><span data-stu-id="661cb-114">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="661cb-115">Справочник</span><span class="sxs-lookup"><span data-stu-id="661cb-115">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="661cb-116">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="661cb-116">Related Sections</span></span>
