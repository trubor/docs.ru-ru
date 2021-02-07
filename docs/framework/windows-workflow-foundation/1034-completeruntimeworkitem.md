---
description: 'Дополнительные сведения: 1034-Комплетерунтимеворкитем'
title: 1034 - CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: dd8a9fcb2fb692ab3b69df8f07f6a96cf48fc806
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667971"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="67bdc-103">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="67bdc-103">1034 - CompleteRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="67bdc-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="67bdc-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67bdc-105">ID</span><span class="sxs-lookup"><span data-stu-id="67bdc-105">ID</span></span>|<span data-ttu-id="67bdc-106">1034</span><span class="sxs-lookup"><span data-stu-id="67bdc-106">1034</span></span>|  
|<span data-ttu-id="67bdc-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="67bdc-107">Keywords</span></span>|<span data-ttu-id="67bdc-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="67bdc-108">WFRuntime</span></span>|  
|<span data-ttu-id="67bdc-109">Level</span><span class="sxs-lookup"><span data-stu-id="67bdc-109">Level</span></span>|<span data-ttu-id="67bdc-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="67bdc-110">Verbose</span></span>|  
|<span data-ttu-id="67bdc-111">Канал</span><span class="sxs-lookup"><span data-stu-id="67bdc-111">Channel</span></span>|<span data-ttu-id="67bdc-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="67bdc-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="67bdc-113">Описание</span><span class="sxs-lookup"><span data-stu-id="67bdc-113">Description</span></span>  

 <span data-ttu-id="67bdc-114">Указывает на завершение RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="67bdc-114">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="67bdc-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="67bdc-115">Message</span></span>  

 <span data-ttu-id="67bdc-116">Рабочий элемент среды выполнения завершен для действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="67bdc-116">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="67bdc-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="67bdc-117">Details</span></span>  
  
|<span data-ttu-id="67bdc-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="67bdc-118">Data Item Name</span></span>|<span data-ttu-id="67bdc-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="67bdc-119">Data Item Type</span></span>|<span data-ttu-id="67bdc-120">Описание</span><span class="sxs-lookup"><span data-stu-id="67bdc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="67bdc-121">Действие</span><span class="sxs-lookup"><span data-stu-id="67bdc-121">Activity</span></span>|<span data-ttu-id="67bdc-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="67bdc-122">xs:string</span></span>|<span data-ttu-id="67bdc-123">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="67bdc-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="67bdc-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="67bdc-124">DisplayName</span></span>|<span data-ttu-id="67bdc-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="67bdc-125">xs:string</span></span>|<span data-ttu-id="67bdc-126">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="67bdc-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="67bdc-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="67bdc-127">InstanceId</span></span>|<span data-ttu-id="67bdc-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="67bdc-128">xs:string</span></span>|<span data-ttu-id="67bdc-129">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="67bdc-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="67bdc-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="67bdc-130">AppDomain</span></span>|<span data-ttu-id="67bdc-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="67bdc-131">xs:string</span></span>|<span data-ttu-id="67bdc-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="67bdc-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
