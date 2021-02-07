---
description: 'Дополнительные сведения: 4810-Дисковеримессажевиснуллмессажесекуенце'
title: 4810 - DiscoveryMessageWithNullMessageSequence
ms.date: 03/30/2017
ms.assetid: aa70573e-8a76-486a-9616-ccca8c7008b6
ms.openlocfilehash: e2c767a0c5a39c75a084c1ebcc114e9d15962cbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760255"
---
# <a name="4810---discoverymessagewithnullmessagesequence"></a><span data-ttu-id="7359f-103">4810 - DiscoveryMessageWithNullMessageSequence</span><span class="sxs-lookup"><span data-stu-id="7359f-103">4810 - DiscoveryMessageWithNullMessageSequence</span></span>

## <a name="properties"></a><span data-ttu-id="7359f-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="7359f-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7359f-105">ID</span><span class="sxs-lookup"><span data-stu-id="7359f-105">ID</span></span>|<span data-ttu-id="7359f-106">4810</span><span class="sxs-lookup"><span data-stu-id="7359f-106">4810</span></span>|  
|<span data-ttu-id="7359f-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="7359f-107">Keywords</span></span>|<span data-ttu-id="7359f-108">Обнаружение</span><span class="sxs-lookup"><span data-stu-id="7359f-108">Discovery</span></span>|  
|<span data-ttu-id="7359f-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="7359f-109">Level</span></span>|<span data-ttu-id="7359f-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="7359f-110">Warning</span></span>|  
|<span data-ttu-id="7359f-111">Канал</span><span class="sxs-lookup"><span data-stu-id="7359f-111">Channel</span></span>|<span data-ttu-id="7359f-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7359f-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7359f-113">Описание</span><span class="sxs-lookup"><span data-stu-id="7359f-113">Description</span></span>  

 <span data-ttu-id="7359f-114">Это событие создается при отбрасывании клиентом DiscoveryClient сообщения запроса обнаружения из-за отсутствия в нем свойства DiscoveryMessageSequence.</span><span class="sxs-lookup"><span data-stu-id="7359f-114">This event is emitted when the discovery message was dropped by the DiscoveryClient because it did not have the DiscoveryMessageSequence property.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7359f-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="7359f-115">Message</span></span>  

 <span data-ttu-id="7359f-116">Сообщение %1 с messageId="%2" удалено клиентом DiscoveryClient, поскольку в нем отсутствует свойство DiscoveryMessageSequence.</span><span class="sxs-lookup"><span data-stu-id="7359f-116">A %1 message with messageId='%2' was dropped by the DiscoveryClient because it did not have the DiscoveryMessageSequence property.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7359f-117">Подробнее</span><span class="sxs-lookup"><span data-stu-id="7359f-117">Details</span></span>
