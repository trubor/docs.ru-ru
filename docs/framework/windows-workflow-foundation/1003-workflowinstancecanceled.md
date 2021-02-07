---
description: 'Дополнительные сведения: 1003-Воркфловинстанцеканцелед'
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: ef7b7c6849e96866204fe53deadce8302d18e0d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703371"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="d3bf7-103">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="d3bf7-103">1003 - WorkflowInstanceCanceled</span></span>

## <a name="properties"></a><span data-ttu-id="d3bf7-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="d3bf7-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3bf7-105">ID</span><span class="sxs-lookup"><span data-stu-id="d3bf7-105">ID</span></span>|<span data-ttu-id="d3bf7-106">1003</span><span class="sxs-lookup"><span data-stu-id="d3bf7-106">1003</span></span>|  
|<span data-ttu-id="d3bf7-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="d3bf7-107">Keywords</span></span>|<span data-ttu-id="d3bf7-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d3bf7-108">WFRuntime</span></span>|  
|<span data-ttu-id="d3bf7-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="d3bf7-109">Level</span></span>|<span data-ttu-id="d3bf7-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="d3bf7-110">Information</span></span>|  
|<span data-ttu-id="d3bf7-111">Канал</span><span class="sxs-lookup"><span data-stu-id="d3bf7-111">Channel</span></span>|<span data-ttu-id="d3bf7-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d3bf7-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d3bf7-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d3bf7-113">Description</span></span>  

 <span data-ttu-id="d3bf7-114">Указывает, что экземпляр рабочего процесса завершено в состоянии Canceled.</span><span class="sxs-lookup"><span data-stu-id="d3bf7-114">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d3bf7-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="d3bf7-115">Message</span></span>  

 <span data-ttu-id="d3bf7-116">Элемент WorkflowInstance с идентификатором «%1» завершил работу в состоянии Canceled.</span><span class="sxs-lookup"><span data-stu-id="d3bf7-116">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d3bf7-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="d3bf7-117">Details</span></span>  
  
|<span data-ttu-id="d3bf7-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="d3bf7-118">Data Item Name</span></span>|<span data-ttu-id="d3bf7-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="d3bf7-119">Data Item Type</span></span>|<span data-ttu-id="d3bf7-120">Описание</span><span class="sxs-lookup"><span data-stu-id="d3bf7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d3bf7-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="d3bf7-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="d3bf7-122">Идентификатор экземпляра для рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d3bf7-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="d3bf7-123">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="d3bf7-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d3bf7-124">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d3bf7-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
