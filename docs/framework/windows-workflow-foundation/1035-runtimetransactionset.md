---
description: 'Дополнительные сведения: 1035-Рунтиметрансактионсет'
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 513ba49962a8f02ab47b8e5b762949cd09154a3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667906"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="7906f-103">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="7906f-103">1035 - RuntimeTransactionSet</span></span>

## <a name="properties"></a><span data-ttu-id="7906f-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="7906f-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7906f-105">ID</span><span class="sxs-lookup"><span data-stu-id="7906f-105">ID</span></span>|<span data-ttu-id="7906f-106">1035</span><span class="sxs-lookup"><span data-stu-id="7906f-106">1035</span></span>|  
|<span data-ttu-id="7906f-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="7906f-107">Keywords</span></span>|<span data-ttu-id="7906f-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7906f-108">WFRuntime</span></span>|  
|<span data-ttu-id="7906f-109">Level</span><span class="sxs-lookup"><span data-stu-id="7906f-109">Level</span></span>|<span data-ttu-id="7906f-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="7906f-110">Verbose</span></span>|  
|<span data-ttu-id="7906f-111">Канал</span><span class="sxs-lookup"><span data-stu-id="7906f-111">Channel</span></span>|<span data-ttu-id="7906f-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7906f-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7906f-113">Описание</span><span class="sxs-lookup"><span data-stu-id="7906f-113">Description</span></span>  

 <span data-ttu-id="7906f-114">Указывает, что действие задало транзакцию среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="7906f-114">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7906f-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="7906f-115">Message</span></span>  

 <span data-ttu-id="7906f-116">Транзакция среды выполнения была задана действием "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="7906f-116">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="7906f-117">Выполнение изолировано с действием "%4", DisplayName: "%5", InstanceId: "%6".</span><span class="sxs-lookup"><span data-stu-id="7906f-117">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7906f-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="7906f-118">Details</span></span>  
  
|<span data-ttu-id="7906f-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="7906f-119">Data Item Name</span></span>|<span data-ttu-id="7906f-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="7906f-120">Data Item Type</span></span>|<span data-ttu-id="7906f-121">Описание</span><span class="sxs-lookup"><span data-stu-id="7906f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7906f-122">Действие</span><span class="sxs-lookup"><span data-stu-id="7906f-122">Activity</span></span>|<span data-ttu-id="7906f-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="7906f-123">xs:string</span></span>|<span data-ttu-id="7906f-124">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="7906f-124">The type name of the activity.</span></span>|  
|<span data-ttu-id="7906f-125">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7906f-125">DisplayName</span></span>|<span data-ttu-id="7906f-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="7906f-126">xs:string</span></span>|<span data-ttu-id="7906f-127">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="7906f-127">The display name of the activity.</span></span>|  
|<span data-ttu-id="7906f-128">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7906f-128">InstanceId</span></span>|<span data-ttu-id="7906f-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="7906f-129">xs:string</span></span>|<span data-ttu-id="7906f-130">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="7906f-130">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7906f-131">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="7906f-131">IsolatedActivity</span></span>|<span data-ttu-id="7906f-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="7906f-132">xs:string</span></span>|<span data-ttu-id="7906f-133">Имя типа для действия, в котором изолирована транзакция.</span><span class="sxs-lookup"><span data-stu-id="7906f-133">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="7906f-134">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="7906f-134">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="7906f-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="7906f-135">xs:string</span></span>|<span data-ttu-id="7906f-136">Имя отображаемого имени действия, в котором изолирована транзакция.</span><span class="sxs-lookup"><span data-stu-id="7906f-136">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="7906f-137">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="7906f-137">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="7906f-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="7906f-138">xs:string</span></span>|<span data-ttu-id="7906f-139">Идентификатор экземпляра действия, в котором изолирована транзакция.</span><span class="sxs-lookup"><span data-stu-id="7906f-139">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="7906f-140">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="7906f-140">AppDomain</span></span>|<span data-ttu-id="7906f-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="7906f-141">xs:string</span></span>|<span data-ttu-id="7906f-142">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7906f-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
