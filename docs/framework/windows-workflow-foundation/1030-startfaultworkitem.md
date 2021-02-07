---
description: 'Дополнительные сведения: 1030-Стартфаултворкитем'
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 2d148277b2d593cfcf75e17662626f1f486e7c1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668101"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="24865-103">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="24865-103">1030 - StartFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="24865-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="24865-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24865-105">ID</span><span class="sxs-lookup"><span data-stu-id="24865-105">ID</span></span>|<span data-ttu-id="24865-106">1030</span><span class="sxs-lookup"><span data-stu-id="24865-106">1030</span></span>|  
|<span data-ttu-id="24865-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="24865-107">Keywords</span></span>|<span data-ttu-id="24865-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="24865-108">WFRuntime</span></span>|  
|<span data-ttu-id="24865-109">Level</span><span class="sxs-lookup"><span data-stu-id="24865-109">Level</span></span>|<span data-ttu-id="24865-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="24865-110">Verbose</span></span>|  
|<span data-ttu-id="24865-111">Канал</span><span class="sxs-lookup"><span data-stu-id="24865-111">Channel</span></span>|<span data-ttu-id="24865-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="24865-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="24865-113">Описание</span><span class="sxs-lookup"><span data-stu-id="24865-113">Description</span></span>  

 <span data-ttu-id="24865-114">Указывает на начало выполнения FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="24865-114">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="24865-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="24865-115">Message</span></span>  

 <span data-ttu-id="24865-116">Запуск выполнения Фаултворкитем для действия "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="24865-116">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="24865-117">Исключение распространено из действия «%4», DisplayName «%5», InstanceId «%6».</span><span class="sxs-lookup"><span data-stu-id="24865-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="24865-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="24865-118">Details</span></span>  
  
|<span data-ttu-id="24865-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="24865-119">Data Item Name</span></span>|<span data-ttu-id="24865-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="24865-120">Data Item Type</span></span>|<span data-ttu-id="24865-121">Описание</span><span class="sxs-lookup"><span data-stu-id="24865-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="24865-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="24865-122">FaultActivity</span></span>|<span data-ttu-id="24865-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="24865-123">xs:string</span></span>|<span data-ttu-id="24865-124">Имя типа действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="24865-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="24865-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="24865-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="24865-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="24865-126">xs:string</span></span>|<span data-ttu-id="24865-127">Отображаемое имя действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="24865-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="24865-128">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="24865-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="24865-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="24865-129">xs:string</span></span>|<span data-ttu-id="24865-130">Идентификатор экземпляра действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="24865-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="24865-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="24865-131">ExceptionActivity</span></span>|<span data-ttu-id="24865-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="24865-132">xs:string</span></span>|<span data-ttu-id="24865-133">Имя типа действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="24865-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="24865-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="24865-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="24865-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="24865-135">xs:string</span></span>|<span data-ttu-id="24865-136">Отображаемое имя действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="24865-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="24865-137">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="24865-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="24865-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="24865-138">xs:string</span></span>|<span data-ttu-id="24865-139">Идентификатор экземпляра действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="24865-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="24865-140">Исключение</span><span class="sxs-lookup"><span data-stu-id="24865-140">Exception</span></span>|<span data-ttu-id="24865-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="24865-141">xs:string</span></span>|<span data-ttu-id="24865-142">Сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="24865-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="24865-143">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="24865-143">AppDomain</span></span>|<span data-ttu-id="24865-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="24865-144">xs:string</span></span>|<span data-ttu-id="24865-145">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="24865-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
