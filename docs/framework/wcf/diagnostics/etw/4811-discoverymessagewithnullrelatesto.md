---
description: 'Дополнительные сведения: 4811-Дисковеримессажевиснуллрелатесто'
title: 4811 - DiscoveryMessageWithNullRelatesTo
ms.date: 03/30/2017
ms.assetid: dab901e8-a2b3-41c1-a76b-bcd8b3c7c29a
ms.openlocfilehash: 40b56c7b114246cf28301603b3c33fbf4434d28b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760268"
---
# <a name="4811---discoverymessagewithnullrelatesto"></a><span data-ttu-id="63a2b-103">4811 - DiscoveryMessageWithNullRelatesTo</span><span class="sxs-lookup"><span data-stu-id="63a2b-103">4811 - DiscoveryMessageWithNullRelatesTo</span></span>

## <a name="properties"></a><span data-ttu-id="63a2b-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="63a2b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63a2b-105">ID</span><span class="sxs-lookup"><span data-stu-id="63a2b-105">ID</span></span>|<span data-ttu-id="63a2b-106">4811</span><span class="sxs-lookup"><span data-stu-id="63a2b-106">4811</span></span>|  
|<span data-ttu-id="63a2b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="63a2b-107">Keywords</span></span>|<span data-ttu-id="63a2b-108">Обнаружение</span><span class="sxs-lookup"><span data-stu-id="63a2b-108">Discovery</span></span>|  
|<span data-ttu-id="63a2b-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="63a2b-109">Level</span></span>|<span data-ttu-id="63a2b-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="63a2b-110">Warning</span></span>|  
|<span data-ttu-id="63a2b-111">Канал</span><span class="sxs-lookup"><span data-stu-id="63a2b-111">Channel</span></span>|<span data-ttu-id="63a2b-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="63a2b-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="63a2b-113">Описание</span><span class="sxs-lookup"><span data-stu-id="63a2b-113">Description</span></span>  

 <span data-ttu-id="63a2b-114">Это событие создается при отбрасывании сообщения обнаружения объектом DiscoveryClient из-за отсутствия в заголовке сообщения обязательного свойства RelatesTo.</span><span class="sxs-lookup"><span data-stu-id="63a2b-114">This event is emitted when the discovery message was dropped by the DiscoveryClient because the message header did not contain the required RelatesTo property.</span></span>  
  
## <a name="message"></a><span data-ttu-id="63a2b-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="63a2b-115">Message</span></span>  

 <span data-ttu-id="63a2b-116">Сообщение %1 с messageId="%2" удалено клиентом DiscoveryClient, поскольку заголовок сообщения не содержит обязательного свойства RelatesTo.</span><span class="sxs-lookup"><span data-stu-id="63a2b-116">A %1 message with messageId='%2' was dropped by the DiscoveryClient because the message header did not contain the required RelatesTo property.</span></span>  
  
## <a name="details"></a><span data-ttu-id="63a2b-117">Подробнее</span><span class="sxs-lookup"><span data-stu-id="63a2b-117">Details</span></span>
