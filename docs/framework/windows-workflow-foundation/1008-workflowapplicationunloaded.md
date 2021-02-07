---
description: 'Дополнительные сведения: 1008-Воркфловаппликатионунлоадед'
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 5e906c0daae525accc3b8b13c907479d18f2fc8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755568"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="3578f-103">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="3578f-103">1008 - WorkflowApplicationUnloaded</span></span>

## <a name="properties"></a><span data-ttu-id="3578f-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="3578f-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3578f-105">ID</span><span class="sxs-lookup"><span data-stu-id="3578f-105">ID</span></span>|<span data-ttu-id="3578f-106">1008</span><span class="sxs-lookup"><span data-stu-id="3578f-106">1008</span></span>|  
|<span data-ttu-id="3578f-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="3578f-107">Keywords</span></span>|<span data-ttu-id="3578f-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3578f-108">WFRuntime</span></span>|  
|<span data-ttu-id="3578f-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="3578f-109">Level</span></span>|<span data-ttu-id="3578f-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="3578f-110">Information</span></span>|  
|<span data-ttu-id="3578f-111">Канал</span><span class="sxs-lookup"><span data-stu-id="3578f-111">Channel</span></span>|<span data-ttu-id="3578f-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3578f-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3578f-113">Описание</span><span class="sxs-lookup"><span data-stu-id="3578f-113">Description</span></span>  

 <span data-ttu-id="3578f-114">Указывает, что приложение рабочего процесса выгружено.</span><span class="sxs-lookup"><span data-stu-id="3578f-114">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3578f-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="3578f-115">Message</span></span>  

 <span data-ttu-id="3578f-116">Элемент WorkflowInstance с идентификатором «%1» выгружен из памяти.</span><span class="sxs-lookup"><span data-stu-id="3578f-116">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3578f-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="3578f-117">Details</span></span>  
  
|<span data-ttu-id="3578f-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="3578f-118">Data Item Name</span></span>|<span data-ttu-id="3578f-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="3578f-119">Data Item Type</span></span>|<span data-ttu-id="3578f-120">Описание</span><span class="sxs-lookup"><span data-stu-id="3578f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3578f-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3578f-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="3578f-122">Идентификатор экземпляра для рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="3578f-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="3578f-123">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="3578f-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3578f-124">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3578f-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
