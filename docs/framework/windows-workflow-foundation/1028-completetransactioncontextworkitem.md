---
description: 'Дополнительные сведения: 1028-Комплететрансактионконтекстворкитем'
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: ae66072769c24ce8d44f92a88cd4232d20bde5f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755464"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="1e9cc-103">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="1e9cc-103">1028 - CompleteTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="1e9cc-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="1e9cc-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e9cc-105">ID</span><span class="sxs-lookup"><span data-stu-id="1e9cc-105">ID</span></span>|<span data-ttu-id="1e9cc-106">1028</span><span class="sxs-lookup"><span data-stu-id="1e9cc-106">1028</span></span>|  
|<span data-ttu-id="1e9cc-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="1e9cc-107">Keywords</span></span>|<span data-ttu-id="1e9cc-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1e9cc-108">WFRuntime</span></span>|  
|<span data-ttu-id="1e9cc-109">Level</span><span class="sxs-lookup"><span data-stu-id="1e9cc-109">Level</span></span>|<span data-ttu-id="1e9cc-110">Подробный</span><span class="sxs-lookup"><span data-stu-id="1e9cc-110">Verbose</span></span>|  
|<span data-ttu-id="1e9cc-111">Канал</span><span class="sxs-lookup"><span data-stu-id="1e9cc-111">Channel</span></span>|<span data-ttu-id="1e9cc-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1e9cc-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e9cc-113">Описание</span><span class="sxs-lookup"><span data-stu-id="1e9cc-113">Description</span></span>  

 <span data-ttu-id="1e9cc-114">Указывает на завершение TransactionContextWorkItem.</span><span class="sxs-lookup"><span data-stu-id="1e9cc-114">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e9cc-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="1e9cc-115">Message</span></span>  

 <span data-ttu-id="1e9cc-116">TransactionContextWorkItem завершен для действия «%1», DisplayName «%2», InstanceId «%3».</span><span class="sxs-lookup"><span data-stu-id="1e9cc-116">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e9cc-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="1e9cc-117">Details</span></span>  
  
|<span data-ttu-id="1e9cc-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="1e9cc-118">Data Item Name</span></span>|<span data-ttu-id="1e9cc-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="1e9cc-119">Data Item Type</span></span>|<span data-ttu-id="1e9cc-120">Описание</span><span class="sxs-lookup"><span data-stu-id="1e9cc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e9cc-121">Действие</span><span class="sxs-lookup"><span data-stu-id="1e9cc-121">Activity</span></span>|<span data-ttu-id="1e9cc-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e9cc-122">xs:string</span></span>|<span data-ttu-id="1e9cc-123">Имя типа действия.</span><span class="sxs-lookup"><span data-stu-id="1e9cc-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="1e9cc-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1e9cc-124">DisplayName</span></span>|<span data-ttu-id="1e9cc-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e9cc-125">xs:string</span></span>|<span data-ttu-id="1e9cc-126">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="1e9cc-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="1e9cc-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1e9cc-127">InstanceId</span></span>|<span data-ttu-id="1e9cc-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e9cc-128">xs:string</span></span>|<span data-ttu-id="1e9cc-129">Идентификатор экземпляра действия.</span><span class="sxs-lookup"><span data-stu-id="1e9cc-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1e9cc-130">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="1e9cc-130">AppDomain</span></span>|<span data-ttu-id="1e9cc-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e9cc-131">xs:string</span></span>|<span data-ttu-id="1e9cc-132">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1e9cc-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
