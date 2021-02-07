---
description: 'Дополнительные сведения: 1132-Инвокемесоддоеснотусеасинкпаттерн'
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 05bbd1f6047ab4c6451d71a4f6007f3112f9630f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667282"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="33c0d-103">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="33c0d-103">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="33c0d-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="33c0d-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33c0d-105">ID</span><span class="sxs-lookup"><span data-stu-id="33c0d-105">ID</span></span>|<span data-ttu-id="33c0d-106">1132</span><span class="sxs-lookup"><span data-stu-id="33c0d-106">1132</span></span>|  
|<span data-ttu-id="33c0d-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="33c0d-107">Keywords</span></span>|<span data-ttu-id="33c0d-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="33c0d-108">WFRuntime</span></span>|  
|<span data-ttu-id="33c0d-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="33c0d-109">Level</span></span>|<span data-ttu-id="33c0d-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="33c0d-110">Information</span></span>|  
|<span data-ttu-id="33c0d-111">Канал</span><span class="sxs-lookup"><span data-stu-id="33c0d-111">Channel</span></span>|<span data-ttu-id="33c0d-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="33c0d-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="33c0d-113">Описание</span><span class="sxs-lookup"><span data-stu-id="33c0d-113">Description</span></span>  

 <span data-ttu-id="33c0d-114">На шаге CacheMetadata действие InvokeMethod указывает, что при вызове метода не используется асинхронный шаблон.</span><span class="sxs-lookup"><span data-stu-id="33c0d-114">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="33c0d-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="33c0d-115">Message</span></span>  

 <span data-ttu-id="33c0d-116">Метод InvokeMethod «%1»: в методе не используется асинхронная модель.</span><span class="sxs-lookup"><span data-stu-id="33c0d-116">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="33c0d-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="33c0d-117">Details</span></span>  
  
|<span data-ttu-id="33c0d-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="33c0d-118">Data Item Name</span></span>|<span data-ttu-id="33c0d-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="33c0d-119">Data Item Type</span></span>|<span data-ttu-id="33c0d-120">Описание</span><span class="sxs-lookup"><span data-stu-id="33c0d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="33c0d-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="33c0d-121">InvokeMethod</span></span>|<span data-ttu-id="33c0d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="33c0d-122">xs:string</span></span>|<span data-ttu-id="33c0d-123">Отображаемое имя действия InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="33c0d-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="33c0d-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="33c0d-124">AppDomain</span></span>|<span data-ttu-id="33c0d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="33c0d-125">xs:string</span></span>|<span data-ttu-id="33c0d-126">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="33c0d-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
