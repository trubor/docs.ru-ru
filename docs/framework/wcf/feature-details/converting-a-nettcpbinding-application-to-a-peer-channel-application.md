---
description: Дополнительные сведения о преобразовании приложения NetTcpBinding в приложение однорангового канала
title: Преобразование приложения NetTcpBinding в приложение одноранговых каналов
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 828ffce38fb05acff851c9fe5a6fbb38fffad6aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780418"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="77522-103">Преобразование приложения NetTcpBinding в приложение одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="77522-103">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>

<span data-ttu-id="77522-104">Можно создавать соединения между клиентами с помощью WinFX, используя привязки, описывающие параметры соединения.</span><span class="sxs-lookup"><span data-stu-id="77522-104">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="77522-105">Для преобразования платформа .NET Framework приложения для использования одноранговых подключений требуется привязка, поддерживающая эту технологию при подключении клиентов.</span><span class="sxs-lookup"><span data-stu-id="77522-105">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="77522-106">Одноранговый канал предоставляет привязку, называемую <xref:System.ServiceModel.NetPeerTcpBinding>, которую можно использовать аналогично привязке <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="77522-106">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="77522-107">Основное отличие в том, как задается служба распознавателя и определяются параметры безопасности.</span><span class="sxs-lookup"><span data-stu-id="77522-107">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="77522-108">Если приложение использует распознаватель и параметры безопасности по умолчанию, преобразование обычного клиентско-серверного приложения для использования однорангового канала предполагает изменение имени привязки с "NetTcpBinding" на "NetPeerTcpBinding" в файле конфигурации приложения, при этом не требуется изменять базу кода приложения.</span><span class="sxs-lookup"><span data-stu-id="77522-108">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77522-109">См. также</span><span class="sxs-lookup"><span data-stu-id="77522-109">See also</span></span>

- [<span data-ttu-id="77522-110">Создание приложения одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="77522-110">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
- [<span data-ttu-id="77522-111">Привязки, предоставляемые системой</span><span class="sxs-lookup"><span data-stu-id="77522-111">System-Provided Bindings</span></span>](../system-provided-bindings.md)
