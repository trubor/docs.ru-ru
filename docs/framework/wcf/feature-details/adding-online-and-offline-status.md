---
description: 'Дополнительные сведения: Добавление состояния в сети и вне сети'
title: Добавление подключенного и отключенного состояния
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 33f7920954ed28ebc2c3d34cc54a2e294f5730c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705243"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="6efde-103">Добавление подключенного и отключенного состояния</span><span class="sxs-lookup"><span data-stu-id="6efde-103">Adding Online and Offline Status</span></span>

<span data-ttu-id="6efde-104">Во многих случаях для приложения важно контролировать конкретные сведения о состоянии подключения по одноранговому каналу.</span><span class="sxs-lookup"><span data-stu-id="6efde-104">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="6efde-105">Эти сведения можно получить, вызвав метод `GetProperty` в реализации интерфейса <xref:System.ServiceModel.IOnlineStatus>.</span><span class="sxs-lookup"><span data-stu-id="6efde-105">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="6efde-106">Объект с реализацией этого интерфейса может контролировать состояние подключения или регистрировать обработчики событий, например `OnOnline` и `OnOffline`, и немедленно реагировать при возникновении изменений в состоянии подключения к сети.</span><span class="sxs-lookup"><span data-stu-id="6efde-106">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="6efde-107">В инфраструктуре одноранговых каналов клиент считается подключенным к сети, если он подключен по крайней мере к одному одноранговому узлу. В противном случае клиент считается автономным.</span><span class="sxs-lookup"><span data-stu-id="6efde-107">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="6efde-108">Это может быть особенно полезно как при отладке разрабатываемых приложений, так и при отображении подробных сведений для конечного пользователя.</span><span class="sxs-lookup"><span data-stu-id="6efde-108">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6efde-109">Перед отправкой любых сообщений обработчик событий подключения к сети должен убедиться, что узел открыт.</span><span class="sxs-lookup"><span data-stu-id="6efde-109">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efde-110">См. также</span><span class="sxs-lookup"><span data-stu-id="6efde-110">See also</span></span>

- [<span data-ttu-id="6efde-111">Создание приложения одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="6efde-111">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
