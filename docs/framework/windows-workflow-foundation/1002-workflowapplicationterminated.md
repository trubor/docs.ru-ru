---
description: 'Дополнительные сведения: 1002-Воркфловаппликатионтерминатед'
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 8ceef41515231833767fc7e2095ab3850bf80e41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755632"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="69829-103">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="69829-103">1002 - WorkflowApplicationTerminated</span></span>

## <a name="properties"></a><span data-ttu-id="69829-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="69829-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69829-105">ID</span><span class="sxs-lookup"><span data-stu-id="69829-105">ID</span></span>|<span data-ttu-id="69829-106">1002</span><span class="sxs-lookup"><span data-stu-id="69829-106">1002</span></span>|  
|<span data-ttu-id="69829-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="69829-107">Keywords</span></span>|<span data-ttu-id="69829-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="69829-108">WFRuntime</span></span>|  
|<span data-ttu-id="69829-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="69829-109">Level</span></span>|<span data-ttu-id="69829-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="69829-110">Information</span></span>|  
|<span data-ttu-id="69829-111">Канал</span><span class="sxs-lookup"><span data-stu-id="69829-111">Channel</span></span>|<span data-ttu-id="69829-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="69829-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="69829-113">Описание</span><span class="sxs-lookup"><span data-stu-id="69829-113">Description</span></span>  

 <span data-ttu-id="69829-114">Указывает, что приложение рабочего процесса было остановлено в состоянии Faulted с исключением.</span><span class="sxs-lookup"><span data-stu-id="69829-114">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="69829-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="69829-115">Message</span></span>  

 <span data-ttu-id="69829-116">WorkflowApplication с идентификатором «%1» остановлено.</span><span class="sxs-lookup"><span data-stu-id="69829-116">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="69829-117">Был прерван в состоянии сбоя с исключением.</span><span class="sxs-lookup"><span data-stu-id="69829-117">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="69829-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="69829-118">Details</span></span>  
  
|<span data-ttu-id="69829-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="69829-119">Data Item Name</span></span>|<span data-ttu-id="69829-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="69829-120">Data Item Type</span></span>|<span data-ttu-id="69829-121">Описание</span><span class="sxs-lookup"><span data-stu-id="69829-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="69829-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="69829-122">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="69829-123">Идентификатор приложения рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="69829-123">The workflow application id</span></span>|  
|<span data-ttu-id="69829-124">Исключение</span><span class="sxs-lookup"><span data-stu-id="69829-124">Exception</span></span>|`xs:string`|<span data-ttu-id="69829-125">Сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="69829-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="69829-126">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="69829-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="69829-127">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="69829-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
