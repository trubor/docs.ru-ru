---
description: 'Дополнительные сведения: 402-Стартсигнпостевент'
title: 402 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: e77cac50be2a2e96fabe1301aaeab7ff74142e5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99656687"
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="b49cd-103">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="b49cd-103">402 - StartSignpostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="b49cd-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="b49cd-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b49cd-105">ID</span><span class="sxs-lookup"><span data-stu-id="b49cd-105">ID</span></span>|<span data-ttu-id="b49cd-106">402</span><span class="sxs-lookup"><span data-stu-id="b49cd-106">402</span></span>|  
|<span data-ttu-id="b49cd-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="b49cd-107">Keywords</span></span>|<span data-ttu-id="b49cd-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="b49cd-108">Troubleshooting</span></span>|  
|<span data-ttu-id="b49cd-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="b49cd-109">Level</span></span>|<span data-ttu-id="b49cd-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="b49cd-110">Information</span></span>|  
|<span data-ttu-id="b49cd-111">Канал</span><span class="sxs-lookup"><span data-stu-id="b49cd-111">Channel</span></span>|<span data-ttu-id="b49cd-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b49cd-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b49cd-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b49cd-113">Description</span></span>  

 <span data-ttu-id="b49cd-114">Это событие отмечает начало сквозного действия.</span><span class="sxs-lookup"><span data-stu-id="b49cd-114">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="b49cd-115">В ней содержится имя действия.</span><span class="sxs-lookup"><span data-stu-id="b49cd-115">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b49cd-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="b49cd-116">Message</span></span>  

 <span data-ttu-id="b49cd-117">Граница действия.</span><span class="sxs-lookup"><span data-stu-id="b49cd-117">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b49cd-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="b49cd-118">Details</span></span>  
  
|<span data-ttu-id="b49cd-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="b49cd-119">Data Item Name</span></span>|<span data-ttu-id="b49cd-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="b49cd-120">Data Item Type</span></span>|<span data-ttu-id="b49cd-121">Описание</span><span class="sxs-lookup"><span data-stu-id="b49cd-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b49cd-122">Расширенные данные</span><span class="sxs-lookup"><span data-stu-id="b49cd-122">Extended Data</span></span>|`xs:string`|<span data-ttu-id="b49cd-123">Имя действия.</span><span class="sxs-lookup"><span data-stu-id="b49cd-123">The name of the activity.</span></span>|  
|<span data-ttu-id="b49cd-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="b49cd-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b49cd-125">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b49cd-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
