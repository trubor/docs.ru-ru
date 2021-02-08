---
description: 'Дополнительные сведения: 3503-Дупликатекоррелатионкуери'
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: a8e1e41aad3aa1b273d8f8a5d7b0768fabe4e658
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778078"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="151b2-103">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="151b2-103">3503 - DuplicateCorrelationQuery</span></span>

## <a name="properties"></a><span data-ttu-id="151b2-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="151b2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="151b2-105">ID</span><span class="sxs-lookup"><span data-stu-id="151b2-105">ID</span></span>|<span data-ttu-id="151b2-106">3503</span><span class="sxs-lookup"><span data-stu-id="151b2-106">3503</span></span>|  
|<span data-ttu-id="151b2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="151b2-107">Keywords</span></span>|<span data-ttu-id="151b2-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="151b2-108">WFServices</span></span>|  
|<span data-ttu-id="151b2-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="151b2-109">Level</span></span>|<span data-ttu-id="151b2-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="151b2-110">Warning</span></span>|  
|<span data-ttu-id="151b2-111">Канал</span><span class="sxs-lookup"><span data-stu-id="151b2-111">Channel</span></span>|<span data-ttu-id="151b2-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="151b2-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="151b2-113">Описание</span><span class="sxs-lookup"><span data-stu-id="151b2-113">Description</span></span>  

 <span data-ttu-id="151b2-114">Указывает, что обнаружен повторяющийся запрос CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="151b2-114">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="151b2-115">Повторяющийся запрос не будет использоваться при расчете корреляции.</span><span class="sxs-lookup"><span data-stu-id="151b2-115">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="151b2-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="151b2-116">Message</span></span>  

 <span data-ttu-id="151b2-117">Обнаружен повторяющийся запрос CorrelationQuery с параметром Where=«%1».</span><span class="sxs-lookup"><span data-stu-id="151b2-117">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="151b2-118">Это дубликат не будет использоваться при расчете корреляции.</span><span class="sxs-lookup"><span data-stu-id="151b2-118">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="151b2-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="151b2-119">Details</span></span>  
  
|<span data-ttu-id="151b2-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="151b2-120">Data Item Name</span></span>|<span data-ttu-id="151b2-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="151b2-121">Data Item Type</span></span>|<span data-ttu-id="151b2-122">Описание</span><span class="sxs-lookup"><span data-stu-id="151b2-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="151b2-123">Where</span><span class="sxs-lookup"><span data-stu-id="151b2-123">Where</span></span>|<span data-ttu-id="151b2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="151b2-124">xs:string</span></span>|<span data-ttu-id="151b2-125">Часть Where в запросе корреляции.</span><span class="sxs-lookup"><span data-stu-id="151b2-125">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="151b2-126">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="151b2-126">AppDomain</span></span>|<span data-ttu-id="151b2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="151b2-127">xs:string</span></span>|<span data-ttu-id="151b2-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="151b2-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
