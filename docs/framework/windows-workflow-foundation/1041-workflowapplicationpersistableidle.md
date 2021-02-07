---
description: 'Дополнительные сведения: 1041-Воркфловаппликатионперсистаблеидле'
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: eb004077a36ed3e78229df92a73972ed5feda665
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667763"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="3984b-103">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="3984b-103">1041 - WorkflowApplicationPersistableIdle</span></span>

## <a name="properties"></a><span data-ttu-id="3984b-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="3984b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3984b-105">ID</span><span class="sxs-lookup"><span data-stu-id="3984b-105">ID</span></span>|<span data-ttu-id="3984b-106">1041</span><span class="sxs-lookup"><span data-stu-id="3984b-106">1041</span></span>|  
|<span data-ttu-id="3984b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="3984b-107">Keywords</span></span>|<span data-ttu-id="3984b-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3984b-108">WFRuntime</span></span>|  
|<span data-ttu-id="3984b-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="3984b-109">Level</span></span>|<span data-ttu-id="3984b-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="3984b-110">Information</span></span>|  
|<span data-ttu-id="3984b-111">Канал</span><span class="sxs-lookup"><span data-stu-id="3984b-111">Channel</span></span>|<span data-ttu-id="3984b-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3984b-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3984b-113">Описание</span><span class="sxs-lookup"><span data-stu-id="3984b-113">Description</span></span>  

 <span data-ttu-id="3984b-114">Указывает, что приложение рабочего процесса бездействует и является сохраняемым.</span><span class="sxs-lookup"><span data-stu-id="3984b-114">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="3984b-115">Приложение рабочего процесса будет бездействующим или сохраняемым.</span><span class="sxs-lookup"><span data-stu-id="3984b-115">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3984b-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="3984b-116">Message</span></span>  

 <span data-ttu-id="3984b-117">Идентификатор WorkflowApplication: "%1" находится в состоянии бездействия и является сохраняемым.</span><span class="sxs-lookup"><span data-stu-id="3984b-117">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="3984b-118">Будет выполнено следующее действие: %2.</span><span class="sxs-lookup"><span data-stu-id="3984b-118">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3984b-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="3984b-119">Details</span></span>  
  
|<span data-ttu-id="3984b-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="3984b-120">Data Item Name</span></span>|<span data-ttu-id="3984b-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="3984b-121">Data Item Type</span></span>|<span data-ttu-id="3984b-122">Описание</span><span class="sxs-lookup"><span data-stu-id="3984b-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3984b-123">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="3984b-123">WorkflowApplicationId</span></span>|<span data-ttu-id="3984b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3984b-124">xs:string</span></span>|<span data-ttu-id="3984b-125">Идентификатор приложения рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="3984b-125">The workflow application id</span></span>|  
|<span data-ttu-id="3984b-126">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="3984b-126">ActionTaken</span></span>|<span data-ttu-id="3984b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3984b-127">xs:string</span></span>|<span data-ttu-id="3984b-128">Действие, которое будет выполняться в приложении рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="3984b-128">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="3984b-129">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="3984b-129">AppDomain</span></span>|<span data-ttu-id="3984b-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="3984b-130">xs:string</span></span>|<span data-ttu-id="3984b-131">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3984b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
