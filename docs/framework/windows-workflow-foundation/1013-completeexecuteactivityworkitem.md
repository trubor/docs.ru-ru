---
description: 'Дополнительные сведения: 1013-Комплетиксекутеактивитиворкитем'
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: 815f859c40a02e8c06e44603a80ab964dc4e64bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792951"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="d4506-103">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="d4506-103">1013 - CompleteExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="d4506-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="d4506-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d4506-105">ID</span><span class="sxs-lookup"><span data-stu-id="d4506-105">ID</span></span>|<span data-ttu-id="d4506-106">1013</span><span class="sxs-lookup"><span data-stu-id="d4506-106">1013</span></span>|  
|<span data-ttu-id="d4506-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="d4506-107">Keywords</span></span>|<span data-ttu-id="d4506-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d4506-108">WFRuntime</span></span>|  
|<span data-ttu-id="d4506-109">Level</span><span class="sxs-lookup"><span data-stu-id="d4506-109">Level</span></span>|<span data-ttu-id="d4506-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="d4506-110">Verbose</span></span>|  
|<span data-ttu-id="d4506-111">Канал</span><span class="sxs-lookup"><span data-stu-id="d4506-111">Channel</span></span>|<span data-ttu-id="d4506-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d4506-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d4506-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d4506-113">Description</span></span>  

 <span data-ttu-id="d4506-114">Указывает, что ExecuteActivityWorkItem завершено</span><span class="sxs-lookup"><span data-stu-id="d4506-114">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="d4506-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="d4506-115">Message</span></span>  

 <span data-ttu-id="d4506-116">Завершено выполнение ExecuteActivityWorkItem для действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="d4506-116">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d4506-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="d4506-117">Details</span></span>  
  
|<span data-ttu-id="d4506-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="d4506-118">Data Item Name</span></span>|<span data-ttu-id="d4506-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="d4506-119">Data Item Type</span></span>|<span data-ttu-id="d4506-120">Описание</span><span class="sxs-lookup"><span data-stu-id="d4506-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d4506-121">Действие</span><span class="sxs-lookup"><span data-stu-id="d4506-121">Activity</span></span>|<span data-ttu-id="d4506-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="d4506-122">xs:string</span></span>|<span data-ttu-id="d4506-123">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="d4506-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="d4506-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d4506-124">DisplayName</span></span>|<span data-ttu-id="d4506-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="d4506-125">xs:string</span></span>|<span data-ttu-id="d4506-126">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="d4506-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="d4506-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="d4506-127">InstanceId</span></span>|<span data-ttu-id="d4506-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="d4506-128">xs:string</span></span>|<span data-ttu-id="d4506-129">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="d4506-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d4506-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="d4506-130">AppDomain</span></span>|<span data-ttu-id="d4506-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="d4506-131">xs:string</span></span>|<span data-ttu-id="d4506-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d4506-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
