---
description: 'Дополнительные сведения: 4203-Реневлокксистемеррор'
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 0e62c501391fcaec56f2016631707832170775ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792782"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="96458-103">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="96458-103">4203 - RenewLockSystemError</span></span>

## <a name="properties"></a><span data-ttu-id="96458-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="96458-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96458-105">ID</span><span class="sxs-lookup"><span data-stu-id="96458-105">ID</span></span>|<span data-ttu-id="96458-106">4203</span><span class="sxs-lookup"><span data-stu-id="96458-106">4203</span></span>|  
|<span data-ttu-id="96458-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="96458-107">Keywords</span></span>|<span data-ttu-id="96458-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="96458-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="96458-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="96458-109">Level</span></span>|<span data-ttu-id="96458-110">Ошибка</span><span class="sxs-lookup"><span data-stu-id="96458-110">Error</span></span>|  
|<span data-ttu-id="96458-111">Канал</span><span class="sxs-lookup"><span data-stu-id="96458-111">Channel</span></span>|<span data-ttu-id="96458-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="96458-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="96458-113">Описание</span><span class="sxs-lookup"><span data-stu-id="96458-113">Description</span></span>  

 <span data-ttu-id="96458-114">Указывает, что поставщику SQL не удалось продлить срок блокировки либо из-за того, что срок блокировки уже истек, либо из-за того, что владелец блокировки был удален.</span><span class="sxs-lookup"><span data-stu-id="96458-114">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="96458-115">SqlWorkflowInstanceStore будет прервано.</span><span class="sxs-lookup"><span data-stu-id="96458-115">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="96458-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="96458-116">Message</span></span>  

 <span data-ttu-id="96458-117">Не удалось увеличить срок окончания блокировки, срок окончания блокировки уже истек или владелец блокировки удален.</span><span class="sxs-lookup"><span data-stu-id="96458-117">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="96458-118">Прерывание блокировки SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="96458-118">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="96458-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="96458-119">Details</span></span>  
  
|<span data-ttu-id="96458-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="96458-120">Data Item Name</span></span>|<span data-ttu-id="96458-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="96458-121">Data Item Type</span></span>|<span data-ttu-id="96458-122">Описание</span><span class="sxs-lookup"><span data-stu-id="96458-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="96458-123">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="96458-123">AppDomain</span></span>|<span data-ttu-id="96458-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="96458-124">xs:string</span></span>|<span data-ttu-id="96458-125">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="96458-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
