---
description: 'Дополнительные сведения: 4812-Дисковеримессажевиснуллреплито'
title: 4812 - DiscoveryMessageWithNullReplyTo
ms.date: 03/30/2017
ms.assetid: a40e6b7e-c2a6-4186-b1d6-c9560f24a959
ms.openlocfilehash: cbc085e727aed85df184e27b6ae835d1bfcd7021
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760242"
---
# <a name="4812---discoverymessagewithnullreplyto"></a><span data-ttu-id="60396-103">4812 - DiscoveryMessageWithNullReplyTo</span><span class="sxs-lookup"><span data-stu-id="60396-103">4812 - DiscoveryMessageWithNullReplyTo</span></span>

## <a name="properties"></a><span data-ttu-id="60396-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="60396-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60396-105">ID</span><span class="sxs-lookup"><span data-stu-id="60396-105">ID</span></span>|<span data-ttu-id="60396-106">4812</span><span class="sxs-lookup"><span data-stu-id="60396-106">4812</span></span>|  
|<span data-ttu-id="60396-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="60396-107">Keywords</span></span>|<span data-ttu-id="60396-108">Обнаружение</span><span class="sxs-lookup"><span data-stu-id="60396-108">Discovery</span></span>|  
|<span data-ttu-id="60396-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="60396-109">Level</span></span>|<span data-ttu-id="60396-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="60396-110">Warning</span></span>|  
|<span data-ttu-id="60396-111">Канал</span><span class="sxs-lookup"><span data-stu-id="60396-111">Channel</span></span>|<span data-ttu-id="60396-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="60396-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="60396-113">Описание</span><span class="sxs-lookup"><span data-stu-id="60396-113">Description</span></span>  

 <span data-ttu-id="60396-114">Это событие создается при удалении клиентом DiscoveryClient сообщения запроса обнаружения из-за отсутствия в нем адреса ReplyTo.</span><span class="sxs-lookup"><span data-stu-id="60396-114">This event is emitted when the discovery message was dropped by the DiscoveryClient because it did not have a ReplyTo address.</span></span>  
  
## <a name="message"></a><span data-ttu-id="60396-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="60396-115">Message</span></span>  

 <span data-ttu-id="60396-116">Сообщение запроса обнаружения с messageId="%1" удалено, поскольку отсутствует адрес ReplyTo.</span><span class="sxs-lookup"><span data-stu-id="60396-116">A discovery request message with messageId='%1' was dropped because it did not have a ReplyTo address.</span></span>  
  
## <a name="details"></a><span data-ttu-id="60396-117">Подробнее</span><span class="sxs-lookup"><span data-stu-id="60396-117">Details</span></span>
