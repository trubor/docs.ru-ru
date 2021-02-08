---
description: 'Дополнительные сведения: 4209-Тимеаутопенингсклконнектион'
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9c7540e328530fdc01b9f065dfb75b92c467bd43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787998"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="a9969-103">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="a9969-103">4209 - TimeoutOpeningSqlConnection</span></span>

## <a name="properties"></a><span data-ttu-id="a9969-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="a9969-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a9969-105">ID</span><span class="sxs-lookup"><span data-stu-id="a9969-105">ID</span></span>|<span data-ttu-id="a9969-106">4209</span><span class="sxs-lookup"><span data-stu-id="a9969-106">4209</span></span>|  
|<span data-ttu-id="a9969-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="a9969-107">Keywords</span></span>|<span data-ttu-id="a9969-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="a9969-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="a9969-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="a9969-109">Level</span></span>|<span data-ttu-id="a9969-110">Ошибка</span><span class="sxs-lookup"><span data-stu-id="a9969-110">Error</span></span>|  
|<span data-ttu-id="a9969-111">Канал</span><span class="sxs-lookup"><span data-stu-id="a9969-111">Channel</span></span>|<span data-ttu-id="a9969-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a9969-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a9969-113">Описание</span><span class="sxs-lookup"><span data-stu-id="a9969-113">Description</span></span>  

 <span data-ttu-id="a9969-114">Указывает, что при попытке открыть соединение SQL превышено время ожидания.</span><span class="sxs-lookup"><span data-stu-id="a9969-114">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a9969-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="a9969-115">Message</span></span>  

 <span data-ttu-id="a9969-116">Истекло время ожидания при открытии соединения SQL.</span><span class="sxs-lookup"><span data-stu-id="a9969-116">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="a9969-117">Не удалось выполнить операцию за выделенное время ожидания %1.</span><span class="sxs-lookup"><span data-stu-id="a9969-117">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="a9969-118">Возможно, выделенное для этой операции время было частью более длительного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="a9969-118">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a9969-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="a9969-119">Details</span></span>  
  
|<span data-ttu-id="a9969-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="a9969-120">Data Item Name</span></span>|<span data-ttu-id="a9969-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="a9969-121">Data Item Type</span></span>|<span data-ttu-id="a9969-122">Описание</span><span class="sxs-lookup"><span data-stu-id="a9969-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a9969-123">Время ожидания</span><span class="sxs-lookup"><span data-stu-id="a9969-123">Timeout</span></span>|<span data-ttu-id="a9969-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a9969-124">xs:string</span></span>|<span data-ttu-id="a9969-125">Значение времени ожидания для открытия соединения SQL.</span><span class="sxs-lookup"><span data-stu-id="a9969-125">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="a9969-126">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="a9969-126">AppDomain</span></span>|<span data-ttu-id="a9969-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a9969-127">xs:string</span></span>|<span data-ttu-id="a9969-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a9969-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
