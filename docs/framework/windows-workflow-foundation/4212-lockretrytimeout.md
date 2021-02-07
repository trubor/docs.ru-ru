---
description: 'Дополнительные сведения: 4212-Локкретритимеаут'
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: a2299d0d9643fb60ff420519fb43199e3f747c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667087"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="e1a44-103">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="e1a44-103">4212 - LockRetryTimeout</span></span>

## <a name="properties"></a><span data-ttu-id="e1a44-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="e1a44-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1a44-105">ID</span><span class="sxs-lookup"><span data-stu-id="e1a44-105">ID</span></span>|<span data-ttu-id="e1a44-106">4212</span><span class="sxs-lookup"><span data-stu-id="e1a44-106">4212</span></span>|  
|<span data-ttu-id="e1a44-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="e1a44-107">Keywords</span></span>|<span data-ttu-id="e1a44-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="e1a44-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="e1a44-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="e1a44-109">Level</span></span>|<span data-ttu-id="e1a44-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="e1a44-110">Warning</span></span>|  
|<span data-ttu-id="e1a44-111">Канал</span><span class="sxs-lookup"><span data-stu-id="e1a44-111">Channel</span></span>|<span data-ttu-id="e1a44-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e1a44-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1a44-113">Описание</span><span class="sxs-lookup"><span data-stu-id="e1a44-113">Description</span></span>  

 <span data-ttu-id="e1a44-114">При попытке поставщика SQL получить блокировку для экземпляра истекло время ожидания.</span><span class="sxs-lookup"><span data-stu-id="e1a44-114">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1a44-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="e1a44-115">Message</span></span>  

 <span data-ttu-id="e1a44-116">Истекло время ожидания при попытке получить блокировку экземпляра.</span><span class="sxs-lookup"><span data-stu-id="e1a44-116">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="e1a44-117">Не удалось выполнить операцию за выделенное время ожидания %1.</span><span class="sxs-lookup"><span data-stu-id="e1a44-117">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="e1a44-118">Возможно, выделенное для этой операции время было частью более длительного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="e1a44-118">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1a44-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="e1a44-119">Details</span></span>  
  
|<span data-ttu-id="e1a44-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="e1a44-120">Data Item Name</span></span>|<span data-ttu-id="e1a44-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="e1a44-121">Data Item Type</span></span>|<span data-ttu-id="e1a44-122">Описание</span><span class="sxs-lookup"><span data-stu-id="e1a44-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1a44-123">Задержка</span><span class="sxs-lookup"><span data-stu-id="e1a44-123">Delay</span></span>|<span data-ttu-id="e1a44-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1a44-124">xs:string</span></span>|<span data-ttu-id="e1a44-125">Задержка между повторными попытками.</span><span class="sxs-lookup"><span data-stu-id="e1a44-125">The delay between retries.</span></span>|  
|<span data-ttu-id="e1a44-126">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="e1a44-126">AppDomain</span></span>|<span data-ttu-id="e1a44-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1a44-127">xs:string</span></span>|<span data-ttu-id="e1a44-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e1a44-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
