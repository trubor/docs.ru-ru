---
description: 'Дополнительные сведения: 2577-Трикатчексцептиондурингканцелатион'
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: e02e7722dadfe38b9fc1fbb92e809ae8f80cbd2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778104"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="a1b11-103">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="a1b11-103">2577 - TryCatchExceptionDuringCancelation</span></span>

## <a name="properties"></a><span data-ttu-id="a1b11-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="a1b11-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1b11-105">ID</span><span class="sxs-lookup"><span data-stu-id="a1b11-105">ID</span></span>|<span data-ttu-id="a1b11-106">2577</span><span class="sxs-lookup"><span data-stu-id="a1b11-106">2577</span></span>|  
|<span data-ttu-id="a1b11-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="a1b11-107">Keywords</span></span>|<span data-ttu-id="a1b11-108">WFActivities</span><span class="sxs-lookup"><span data-stu-id="a1b11-108">WFActivities</span></span>|  
|<span data-ttu-id="a1b11-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="a1b11-109">Level</span></span>|<span data-ttu-id="a1b11-110">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="a1b11-110">Warning</span></span>|  
|<span data-ttu-id="a1b11-111">Канал</span><span class="sxs-lookup"><span data-stu-id="a1b11-111">Channel</span></span>|<span data-ttu-id="a1b11-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a1b11-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a1b11-113">Описание</span><span class="sxs-lookup"><span data-stu-id="a1b11-113">Description</span></span>  

 <span data-ttu-id="a1b11-114">Указывает, что дочернее действие для действия TryCatch вызвало исключение во время отмены.</span><span class="sxs-lookup"><span data-stu-id="a1b11-114">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a1b11-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="a1b11-115">Message</span></span>  

 <span data-ttu-id="a1b11-116">При отмене дочернего действия для действия TryCatch «%1» произошло исключение.</span><span class="sxs-lookup"><span data-stu-id="a1b11-116">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a1b11-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="a1b11-117">Details</span></span>  
  
|<span data-ttu-id="a1b11-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="a1b11-118">Data Item Name</span></span>|<span data-ttu-id="a1b11-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="a1b11-119">Data Item Type</span></span>|<span data-ttu-id="a1b11-120">Описание</span><span class="sxs-lookup"><span data-stu-id="a1b11-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a1b11-121">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a1b11-121">DisplayName</span></span>|<span data-ttu-id="a1b11-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1b11-122">xs:string</span></span>|<span data-ttu-id="a1b11-123">Отображаемое имя действия.</span><span class="sxs-lookup"><span data-stu-id="a1b11-123">The display name of the activity.</span></span>|  
|<span data-ttu-id="a1b11-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="a1b11-124">AppDomain</span></span>|<span data-ttu-id="a1b11-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1b11-125">xs:string</span></span>|<span data-ttu-id="a1b11-126">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a1b11-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
