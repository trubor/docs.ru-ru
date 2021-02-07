---
description: 'Дополнительные сведения: 1036-Рунтиметрансактионкомплетионрекуестед'
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: e07400902d5c3e08732385ab30e1be0d72d3e997
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667893"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="3a2a8-103">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="3a2a8-103">1036 - RuntimeTransactionCompletionRequested</span></span>

## <a name="properties"></a><span data-ttu-id="3a2a8-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="3a2a8-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a2a8-105">ID</span><span class="sxs-lookup"><span data-stu-id="3a2a8-105">ID</span></span>|<span data-ttu-id="3a2a8-106">1036</span><span class="sxs-lookup"><span data-stu-id="3a2a8-106">1036</span></span>|  
|<span data-ttu-id="3a2a8-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="3a2a8-107">Keywords</span></span>|<span data-ttu-id="3a2a8-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3a2a8-108">WFRuntime</span></span>|  
|<span data-ttu-id="3a2a8-109">Level</span><span class="sxs-lookup"><span data-stu-id="3a2a8-109">Level</span></span>|<span data-ttu-id="3a2a8-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="3a2a8-110">Verbose</span></span>|  
|<span data-ttu-id="3a2a8-111">Канал</span><span class="sxs-lookup"><span data-stu-id="3a2a8-111">Channel</span></span>|<span data-ttu-id="3a2a8-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3a2a8-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3a2a8-113">Описание</span><span class="sxs-lookup"><span data-stu-id="3a2a8-113">Description</span></span>  

 <span data-ttu-id="3a2a8-114">Указывает, что действие запланировало завершение транзакции среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-114">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3a2a8-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="3a2a8-115">Message</span></span>  

 <span data-ttu-id="3a2a8-116">Действие «%1», DisplayName «%2», InstanceId «%3» запланировало завершение транзакции времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-116">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3a2a8-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="3a2a8-117">Details</span></span>  
  
|<span data-ttu-id="3a2a8-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="3a2a8-118">Data Item Name</span></span>|<span data-ttu-id="3a2a8-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="3a2a8-119">Data Item Type</span></span>|<span data-ttu-id="3a2a8-120">Описание</span><span class="sxs-lookup"><span data-stu-id="3a2a8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3a2a8-121">Действие</span><span class="sxs-lookup"><span data-stu-id="3a2a8-121">Activity</span></span>|<span data-ttu-id="3a2a8-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a2a8-122">xs:string</span></span>|<span data-ttu-id="3a2a8-123">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="3a2a8-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3a2a8-124">DisplayName</span></span>|<span data-ttu-id="3a2a8-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a2a8-125">xs:string</span></span>|<span data-ttu-id="3a2a8-126">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="3a2a8-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="3a2a8-127">InstanceId</span></span>|<span data-ttu-id="3a2a8-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a2a8-128">xs:string</span></span>|<span data-ttu-id="3a2a8-129">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3a2a8-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="3a2a8-130">AppDomain</span></span>|<span data-ttu-id="3a2a8-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a2a8-131">xs:string</span></span>|<span data-ttu-id="3a2a8-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3a2a8-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
