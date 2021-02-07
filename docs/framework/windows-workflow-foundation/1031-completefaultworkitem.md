---
description: 'Дополнительные сведения: 1031-Комплетефаултворкитем'
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: dc5cb4988df2aab9710fd7ec875d9b4004bfa7af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668075"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="17fd4-103">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="17fd4-103">1031 - CompleteFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="17fd4-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="17fd4-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17fd4-105">ID</span><span class="sxs-lookup"><span data-stu-id="17fd4-105">ID</span></span>|<span data-ttu-id="17fd4-106">1031</span><span class="sxs-lookup"><span data-stu-id="17fd4-106">1031</span></span>|  
|<span data-ttu-id="17fd4-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="17fd4-107">Keywords</span></span>|<span data-ttu-id="17fd4-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="17fd4-108">WFRuntime</span></span>|  
|<span data-ttu-id="17fd4-109">Level</span><span class="sxs-lookup"><span data-stu-id="17fd4-109">Level</span></span>|<span data-ttu-id="17fd4-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="17fd4-110">Verbose</span></span>|  
|<span data-ttu-id="17fd4-111">Канал</span><span class="sxs-lookup"><span data-stu-id="17fd4-111">Channel</span></span>|<span data-ttu-id="17fd4-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="17fd4-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="17fd4-113">Описание</span><span class="sxs-lookup"><span data-stu-id="17fd4-113">Description</span></span>  

 <span data-ttu-id="17fd4-114">Указывает, что FaultWorkItem завершено.</span><span class="sxs-lookup"><span data-stu-id="17fd4-114">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="17fd4-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="17fd4-115">Message</span></span>  

 <span data-ttu-id="17fd4-116">FaultWorkItem завершено для действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="17fd4-116">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="17fd4-117">Исключение распространено из действия «%4», DisplayName «%5», InstanceId «%6».</span><span class="sxs-lookup"><span data-stu-id="17fd4-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="17fd4-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="17fd4-118">Details</span></span>  
  
|<span data-ttu-id="17fd4-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="17fd4-119">Data Item Name</span></span>|<span data-ttu-id="17fd4-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="17fd4-120">Data Item Type</span></span>|<span data-ttu-id="17fd4-121">Описание</span><span class="sxs-lookup"><span data-stu-id="17fd4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="17fd4-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="17fd4-122">FaultActivity</span></span>|<span data-ttu-id="17fd4-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="17fd4-123">xs:string</span></span>|<span data-ttu-id="17fd4-124">Имя типа действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="17fd4-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="17fd4-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="17fd4-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="17fd4-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="17fd4-126">xs:string</span></span>|<span data-ttu-id="17fd4-127">Отображаемое имя действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="17fd4-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="17fd4-128">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="17fd4-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="17fd4-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="17fd4-129">xs:string</span></span>|<span data-ttu-id="17fd4-130">Идентификатор экземпляра действия с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="17fd4-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="17fd4-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="17fd4-131">ExceptionActivity</span></span>|<span data-ttu-id="17fd4-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="17fd4-132">xs:string</span></span>|<span data-ttu-id="17fd4-133">Имя типа действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="17fd4-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="17fd4-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="17fd4-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="17fd4-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="17fd4-135">xs:string</span></span>|<span data-ttu-id="17fd4-136">Отображаемое имя действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="17fd4-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="17fd4-137">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="17fd4-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="17fd4-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="17fd4-138">xs:string</span></span>|<span data-ttu-id="17fd4-139">Идентификатор экземпляра действия, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="17fd4-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="17fd4-140">Исключение</span><span class="sxs-lookup"><span data-stu-id="17fd4-140">Exception</span></span>|<span data-ttu-id="17fd4-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="17fd4-141">xs:string</span></span>|<span data-ttu-id="17fd4-142">Сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="17fd4-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="17fd4-143">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="17fd4-143">AppDomain</span></span>|<span data-ttu-id="17fd4-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="17fd4-144">xs:string</span></span>|<span data-ttu-id="17fd4-145">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="17fd4-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
