---
description: 'Дополнительные сведения: 1131-Инвокемесодусеасинкпаттерн'
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 59d8e5e1fe7c5b038df6fce3211fd01977abc4f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667321"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="7aa59-103">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="7aa59-103">1131 - InvokeMethodUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="7aa59-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="7aa59-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7aa59-105">ID</span><span class="sxs-lookup"><span data-stu-id="7aa59-105">ID</span></span>|<span data-ttu-id="7aa59-106">1131</span><span class="sxs-lookup"><span data-stu-id="7aa59-106">1131</span></span>|  
|<span data-ttu-id="7aa59-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="7aa59-107">Keywords</span></span>|<span data-ttu-id="7aa59-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7aa59-108">WFRuntime</span></span>|  
|<span data-ttu-id="7aa59-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="7aa59-109">Level</span></span>|<span data-ttu-id="7aa59-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="7aa59-110">Information</span></span>|  
|<span data-ttu-id="7aa59-111">Канал</span><span class="sxs-lookup"><span data-stu-id="7aa59-111">Channel</span></span>|<span data-ttu-id="7aa59-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7aa59-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7aa59-113">Описание</span><span class="sxs-lookup"><span data-stu-id="7aa59-113">Description</span></span>  

 <span data-ttu-id="7aa59-114">На шаге CacheMetadata действие InvokeMethod указывает на использование асинхронного шаблона при вызове метода.</span><span class="sxs-lookup"><span data-stu-id="7aa59-114">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7aa59-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="7aa59-115">Message</span></span>  

 <span data-ttu-id="7aa59-116">Метод InvokeMethod «%1»: в методе используется асинхронная модель «%2» и «%3».</span><span class="sxs-lookup"><span data-stu-id="7aa59-116">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7aa59-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="7aa59-117">Details</span></span>  
  
|<span data-ttu-id="7aa59-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="7aa59-118">Data Item Name</span></span>|<span data-ttu-id="7aa59-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="7aa59-119">Data Item Type</span></span>|<span data-ttu-id="7aa59-120">Описание</span><span class="sxs-lookup"><span data-stu-id="7aa59-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7aa59-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="7aa59-121">InvokeMethod</span></span>|<span data-ttu-id="7aa59-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="7aa59-122">xs:string</span></span>|<span data-ttu-id="7aa59-123">Отображаемое имя действия InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="7aa59-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="7aa59-124">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="7aa59-124">BeginMethod</span></span>|<span data-ttu-id="7aa59-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="7aa59-125">xs:string</span></span>|<span data-ttu-id="7aa59-126">Имя метода Begin.</span><span class="sxs-lookup"><span data-stu-id="7aa59-126">The name of the begin method.</span></span>|  
|<span data-ttu-id="7aa59-127">EndMethod</span><span class="sxs-lookup"><span data-stu-id="7aa59-127">EndMethod</span></span>|<span data-ttu-id="7aa59-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="7aa59-128">xs:string</span></span>|<span data-ttu-id="7aa59-129">Имя метода End.</span><span class="sxs-lookup"><span data-stu-id="7aa59-129">The name of the end method.</span></span>|  
|<span data-ttu-id="7aa59-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="7aa59-130">AppDomain</span></span>|<span data-ttu-id="7aa59-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="7aa59-131">xs:string</span></span>|<span data-ttu-id="7aa59-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7aa59-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
