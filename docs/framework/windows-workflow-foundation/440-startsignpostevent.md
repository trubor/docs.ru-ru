---
description: 'Дополнительные сведения: 440-StartSignpostEvent1'
title: 440 - StartSignpostEvent1
ms.date: 03/30/2017
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
ms.openlocfilehash: 462ad54c9dd8230632d76d88f2b779eaea3b43ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720375"
---
# <a name="440---startsignpostevent1"></a><span data-ttu-id="67277-103">440 - StartSignpostEvent1</span><span class="sxs-lookup"><span data-stu-id="67277-103">440 - StartSignpostEvent1</span></span>

## <a name="properties"></a><span data-ttu-id="67277-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="67277-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67277-105">ID</span><span class="sxs-lookup"><span data-stu-id="67277-105">ID</span></span>|<span data-ttu-id="67277-106">440</span><span class="sxs-lookup"><span data-stu-id="67277-106">440</span></span>|  
|<span data-ttu-id="67277-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="67277-107">Keywords</span></span>|<span data-ttu-id="67277-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="67277-108">Troubleshooting</span></span>|  
|<span data-ttu-id="67277-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="67277-109">Level</span></span>|<span data-ttu-id="67277-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="67277-110">Information</span></span>|  
|<span data-ttu-id="67277-111">Канал</span><span class="sxs-lookup"><span data-stu-id="67277-111">Channel</span></span>|<span data-ttu-id="67277-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="67277-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="67277-113">Описание</span><span class="sxs-lookup"><span data-stu-id="67277-113">Description</span></span>  

 <span data-ttu-id="67277-114">В трассировке действий указывает на то, что сообщение начало пересекать границу действия при отправке или приеме.</span><span class="sxs-lookup"><span data-stu-id="67277-114">In activity tracing, indicates a message has started crossing an activity boundary in send or receive.</span></span>  
  
## <a name="message"></a><span data-ttu-id="67277-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="67277-115">Message</span></span>  

 <span data-ttu-id="67277-116">Граница действия.</span><span class="sxs-lookup"><span data-stu-id="67277-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="67277-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="67277-117">Details</span></span>  
  
|<span data-ttu-id="67277-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="67277-118">Data Item Name</span></span>|<span data-ttu-id="67277-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="67277-119">Data Item Type</span></span>|<span data-ttu-id="67277-120">Описание</span><span class="sxs-lookup"><span data-stu-id="67277-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="67277-121">ExtendedData</span><span class="sxs-lookup"><span data-stu-id="67277-121">ExtendedData</span></span>|`xs:string`|<span data-ttu-id="67277-122">Имя действия.</span><span class="sxs-lookup"><span data-stu-id="67277-122">The name of the activity.</span></span>|  
|<span data-ttu-id="67277-123">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="67277-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="67277-124">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="67277-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
