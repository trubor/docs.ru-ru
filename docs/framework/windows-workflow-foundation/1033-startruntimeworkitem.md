---
description: 'Дополнительные сведения: 1033-Стартрунтимеворкитем'
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: 31e664070b7592d3350a2f6f84f0493cc8f11ea1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668010"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="69f66-103">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="69f66-103">1033 - StartRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="69f66-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="69f66-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69f66-105">ID</span><span class="sxs-lookup"><span data-stu-id="69f66-105">ID</span></span>|<span data-ttu-id="69f66-106">1033</span><span class="sxs-lookup"><span data-stu-id="69f66-106">1033</span></span>|  
|<span data-ttu-id="69f66-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="69f66-107">Keywords</span></span>|<span data-ttu-id="69f66-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="69f66-108">WFRuntime</span></span>|  
|<span data-ttu-id="69f66-109">Level</span><span class="sxs-lookup"><span data-stu-id="69f66-109">Level</span></span>|<span data-ttu-id="69f66-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="69f66-110">Verbose</span></span>|  
|<span data-ttu-id="69f66-111">Канал</span><span class="sxs-lookup"><span data-stu-id="69f66-111">Channel</span></span>|<span data-ttu-id="69f66-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="69f66-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="69f66-113">Описание</span><span class="sxs-lookup"><span data-stu-id="69f66-113">Description</span></span>  

 <span data-ttu-id="69f66-114">Указывает, что начинается выполнение RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="69f66-114">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="69f66-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="69f66-115">Message</span></span>  

 <span data-ttu-id="69f66-116">Начато выполнение рабочего элемента среды выполнения для действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="69f66-116">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="69f66-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="69f66-117">Details</span></span>  
  
|<span data-ttu-id="69f66-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="69f66-118">Data Item Name</span></span>|<span data-ttu-id="69f66-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="69f66-119">Data Item Type</span></span>|<span data-ttu-id="69f66-120">Описание</span><span class="sxs-lookup"><span data-stu-id="69f66-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="69f66-121">Действие</span><span class="sxs-lookup"><span data-stu-id="69f66-121">Activity</span></span>|<span data-ttu-id="69f66-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="69f66-122">xs:string</span></span>|<span data-ttu-id="69f66-123">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="69f66-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="69f66-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="69f66-124">DisplayName</span></span>|<span data-ttu-id="69f66-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="69f66-125">xs:string</span></span>|<span data-ttu-id="69f66-126">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="69f66-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="69f66-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="69f66-127">InstanceId</span></span>|<span data-ttu-id="69f66-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="69f66-128">xs:string</span></span>|<span data-ttu-id="69f66-129">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="69f66-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="69f66-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="69f66-130">AppDomain</span></span>|<span data-ttu-id="69f66-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="69f66-131">xs:string</span></span>|<span data-ttu-id="69f66-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="69f66-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
