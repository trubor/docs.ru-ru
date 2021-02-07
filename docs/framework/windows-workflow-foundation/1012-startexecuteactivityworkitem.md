---
description: 'Дополнительные сведения: 1012-Стартексекутеактивитиворкитем'
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: 3b57fc6d37a6708a4e22537de87a2566612088e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99714889"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="49298-103">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="49298-103">1012 - StartExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="49298-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="49298-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49298-105">ID</span><span class="sxs-lookup"><span data-stu-id="49298-105">ID</span></span>|<span data-ttu-id="49298-106">1012</span><span class="sxs-lookup"><span data-stu-id="49298-106">1012</span></span>|  
|<span data-ttu-id="49298-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="49298-107">Keywords</span></span>|<span data-ttu-id="49298-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="49298-108">WFRuntime</span></span>|  
|<span data-ttu-id="49298-109">Level</span><span class="sxs-lookup"><span data-stu-id="49298-109">Level</span></span>|<span data-ttu-id="49298-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="49298-110">Verbose</span></span>|  
|<span data-ttu-id="49298-111">Канал</span><span class="sxs-lookup"><span data-stu-id="49298-111">Channel</span></span>|<span data-ttu-id="49298-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="49298-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="49298-113">Описание</span><span class="sxs-lookup"><span data-stu-id="49298-113">Description</span></span>  

 <span data-ttu-id="49298-114">Указывает на начало выполнения элемента ExecuteActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="49298-114">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="49298-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="49298-115">Message</span></span>  

 <span data-ttu-id="49298-116">Начато выполнение ExecuteActivityWorkItem для действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="49298-116">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="49298-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="49298-117">Details</span></span>  
  
|<span data-ttu-id="49298-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="49298-118">Data Item Name</span></span>|<span data-ttu-id="49298-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="49298-119">Data Item Type</span></span>|<span data-ttu-id="49298-120">Описание</span><span class="sxs-lookup"><span data-stu-id="49298-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="49298-121">Действие</span><span class="sxs-lookup"><span data-stu-id="49298-121">Activity</span></span>|<span data-ttu-id="49298-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="49298-122">xs:string</span></span>|<span data-ttu-id="49298-123">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="49298-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="49298-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="49298-124">DisplayName</span></span>|<span data-ttu-id="49298-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="49298-125">xs:string</span></span>|<span data-ttu-id="49298-126">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="49298-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="49298-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="49298-127">InstanceId</span></span>|<span data-ttu-id="49298-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="49298-128">xs:string</span></span>|<span data-ttu-id="49298-129">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="49298-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="49298-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="49298-130">AppDomain</span></span>|<span data-ttu-id="49298-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="49298-131">xs:string</span></span>|<span data-ttu-id="49298-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="49298-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
