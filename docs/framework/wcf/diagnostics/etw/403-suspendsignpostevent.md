---
description: 'Дополнительные сведения: 403-Суспендсигнпостевент'
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 4e601920c94ed99c25a1c969508798f65f5348bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99656427"
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="f717d-103">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="f717d-103">403 - SuspendSignpostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="f717d-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="f717d-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f717d-105">ID</span><span class="sxs-lookup"><span data-stu-id="f717d-105">ID</span></span>|<span data-ttu-id="f717d-106">403</span><span class="sxs-lookup"><span data-stu-id="f717d-106">403</span></span>|  
|<span data-ttu-id="f717d-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f717d-107">Keywords</span></span>|<span data-ttu-id="f717d-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="f717d-108">Troubleshooting</span></span>|  
|<span data-ttu-id="f717d-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="f717d-109">Level</span></span>|<span data-ttu-id="f717d-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="f717d-110">Information</span></span>|  
|<span data-ttu-id="f717d-111">Канал</span><span class="sxs-lookup"><span data-stu-id="f717d-111">Channel</span></span>|<span data-ttu-id="f717d-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f717d-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f717d-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f717d-113">Description</span></span>  

 <span data-ttu-id="f717d-114">Это событие сигнализирует о приостановке сквозного действия.</span><span class="sxs-lookup"><span data-stu-id="f717d-114">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="f717d-115">В ней содержится имя действия.</span><span class="sxs-lookup"><span data-stu-id="f717d-115">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f717d-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="f717d-116">Message</span></span>  

 <span data-ttu-id="f717d-117">Граница действия.</span><span class="sxs-lookup"><span data-stu-id="f717d-117">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f717d-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="f717d-118">Details</span></span>  
  
|<span data-ttu-id="f717d-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="f717d-119">Data Item Name</span></span>|<span data-ttu-id="f717d-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="f717d-120">Data Item Type</span></span>|<span data-ttu-id="f717d-121">Описание</span><span class="sxs-lookup"><span data-stu-id="f717d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f717d-122">Расширенные данные</span><span class="sxs-lookup"><span data-stu-id="f717d-122">Extended Data</span></span>|`xs:string`|<span data-ttu-id="f717d-123">Имя действия.</span><span class="sxs-lookup"><span data-stu-id="f717d-123">The name of the activity.</span></span>|  
|<span data-ttu-id="f717d-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="f717d-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f717d-125">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f717d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
