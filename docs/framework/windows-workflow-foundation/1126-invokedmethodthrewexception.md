---
description: 'Дополнительные сведения: 1126-Инвокедмесодсревексцептион'
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 35c4311a4ab7750cc54a5c9ffb379f34b1cb12aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667360"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="24569-103">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="24569-103">1126 - InvokedMethodThrewException</span></span>

## <a name="properties"></a><span data-ttu-id="24569-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="24569-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24569-105">ID</span><span class="sxs-lookup"><span data-stu-id="24569-105">ID</span></span>|<span data-ttu-id="24569-106">1126</span><span class="sxs-lookup"><span data-stu-id="24569-106">1126</span></span>|  
|<span data-ttu-id="24569-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="24569-107">Keywords</span></span>|<span data-ttu-id="24569-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="24569-108">WFRuntime</span></span>|  
|<span data-ttu-id="24569-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="24569-109">Level</span></span>|<span data-ttu-id="24569-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="24569-110">Information</span></span>|  
|<span data-ttu-id="24569-111">Канал</span><span class="sxs-lookup"><span data-stu-id="24569-111">Channel</span></span>|<span data-ttu-id="24569-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="24569-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="24569-113">Описание</span><span class="sxs-lookup"><span data-stu-id="24569-113">Description</span></span>  

 <span data-ttu-id="24569-114">Означает, что метод, вызванный действием InvokeMethod, привел к созданию исключения.</span><span class="sxs-lookup"><span data-stu-id="24569-114">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="24569-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="24569-115">Message</span></span>  

 <span data-ttu-id="24569-116">Возникло исключение в методе, вызванном операцией «%1».</span><span class="sxs-lookup"><span data-stu-id="24569-116">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="24569-117">%2</span><span class="sxs-lookup"><span data-stu-id="24569-117">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="24569-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="24569-118">Details</span></span>  
  
|<span data-ttu-id="24569-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="24569-119">Data Item Name</span></span>|<span data-ttu-id="24569-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="24569-120">Data Item Type</span></span>|<span data-ttu-id="24569-121">Описание</span><span class="sxs-lookup"><span data-stu-id="24569-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="24569-122">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="24569-122">InvokeMethod</span></span>|<span data-ttu-id="24569-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="24569-123">xs:string</span></span>|<span data-ttu-id="24569-124">Отображаемое имя действия InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="24569-124">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="24569-125">Исключение</span><span class="sxs-lookup"><span data-stu-id="24569-125">Exception</span></span>|<span data-ttu-id="24569-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="24569-126">xs:string</span></span>|<span data-ttu-id="24569-127">Сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="24569-127">The exception details for the exception</span></span>|  
|<span data-ttu-id="24569-128">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="24569-128">AppDomain</span></span>|<span data-ttu-id="24569-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="24569-129">xs:string</span></span>|<span data-ttu-id="24569-130">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="24569-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
