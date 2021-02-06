---
description: 'Дополнительные сведения: 3507-Сервицеендпоинтаддед'
title: 3507 - ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: 7de51cb8908d3bf4b450c545c1a4c0f2bdc6a453
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631480"
---
# <a name="3507---serviceendpointadded"></a><span data-ttu-id="26ab6-103">3507 - ServiceEndpointAdded</span><span class="sxs-lookup"><span data-stu-id="26ab6-103">3507 - ServiceEndpointAdded</span></span>

## <a name="properties"></a><span data-ttu-id="26ab6-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="26ab6-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26ab6-105">ID</span><span class="sxs-lookup"><span data-stu-id="26ab6-105">ID</span></span>|<span data-ttu-id="26ab6-106">3507</span><span class="sxs-lookup"><span data-stu-id="26ab6-106">3507</span></span>|  
|<span data-ttu-id="26ab6-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="26ab6-107">Keywords</span></span>|<span data-ttu-id="26ab6-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="26ab6-108">WFServices</span></span>|  
|<span data-ttu-id="26ab6-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="26ab6-109">Level</span></span>|<span data-ttu-id="26ab6-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="26ab6-110">Information</span></span>|  
|<span data-ttu-id="26ab6-111">Канал</span><span class="sxs-lookup"><span data-stu-id="26ab6-111">Channel</span></span>|<span data-ttu-id="26ab6-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="26ab6-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="26ab6-113">Описание</span><span class="sxs-lookup"><span data-stu-id="26ab6-113">Description</span></span>  

 <span data-ttu-id="26ab6-114">Указывает, что конечная точка службы была добавлена.</span><span class="sxs-lookup"><span data-stu-id="26ab6-114">Indicates a service endpoint has been added.</span></span>  
  
## <a name="message"></a><span data-ttu-id="26ab6-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="26ab6-115">Message</span></span>  

 <span data-ttu-id="26ab6-116">Конечная точка службы была добавлена для адреса «%1», привязки «%2» и контракта «%3».</span><span class="sxs-lookup"><span data-stu-id="26ab6-116">A service endpoint has been added for address '%1', binding '%2', and contract '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="26ab6-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="26ab6-117">Details</span></span>  
  
|<span data-ttu-id="26ab6-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="26ab6-118">Data Item Name</span></span>|<span data-ttu-id="26ab6-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="26ab6-119">Data Item Type</span></span>|<span data-ttu-id="26ab6-120">Описание</span><span class="sxs-lookup"><span data-stu-id="26ab6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="26ab6-121">Адрес</span><span class="sxs-lookup"><span data-stu-id="26ab6-121">Address</span></span>|<span data-ttu-id="26ab6-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="26ab6-122">xs:string</span></span>|<span data-ttu-id="26ab6-123">Адрес конечной точки.</span><span class="sxs-lookup"><span data-stu-id="26ab6-123">The address of the endpoint.</span></span>|  
|<span data-ttu-id="26ab6-124">Привязка</span><span class="sxs-lookup"><span data-stu-id="26ab6-124">Binding</span></span>|<span data-ttu-id="26ab6-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="26ab6-125">xs:string</span></span>|<span data-ttu-id="26ab6-126">Привязка конечной точки.</span><span class="sxs-lookup"><span data-stu-id="26ab6-126">The binding of the endpoint.</span></span>|  
|<span data-ttu-id="26ab6-127">Контракт</span><span class="sxs-lookup"><span data-stu-id="26ab6-127">Contract</span></span>|<span data-ttu-id="26ab6-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="26ab6-128">xs:string</span></span>|<span data-ttu-id="26ab6-129">Контракт конечной точки.</span><span class="sxs-lookup"><span data-stu-id="26ab6-129">The contract of the endpoint.</span></span>|  
|<span data-ttu-id="26ab6-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="26ab6-130">AppDomain</span></span>|<span data-ttu-id="26ab6-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="26ab6-131">xs:string</span></span>|<span data-ttu-id="26ab6-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="26ab6-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
