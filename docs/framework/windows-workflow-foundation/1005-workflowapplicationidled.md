---
description: 'Дополнительные сведения: 1005-Воркфловаппликатионидлед'
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: ee8d0b7ff2155333213a718a04c3966024fda89d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755607"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="165dd-103">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="165dd-103">1005 - WorkflowApplicationIdled</span></span>

## <a name="properties"></a><span data-ttu-id="165dd-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="165dd-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="165dd-105">ID</span><span class="sxs-lookup"><span data-stu-id="165dd-105">ID</span></span>|<span data-ttu-id="165dd-106">1005</span><span class="sxs-lookup"><span data-stu-id="165dd-106">1005</span></span>|  
|<span data-ttu-id="165dd-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="165dd-107">Keywords</span></span>|<span data-ttu-id="165dd-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="165dd-108">WFRuntime</span></span>|  
|<span data-ttu-id="165dd-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="165dd-109">Level</span></span>|<span data-ttu-id="165dd-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="165dd-110">Information</span></span>|  
|<span data-ttu-id="165dd-111">Канал</span><span class="sxs-lookup"><span data-stu-id="165dd-111">Channel</span></span>|<span data-ttu-id="165dd-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="165dd-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="165dd-113">Описание</span><span class="sxs-lookup"><span data-stu-id="165dd-113">Description</span></span>  

 <span data-ttu-id="165dd-114">Указывает, что приложение рабочего процесса простаивало.</span><span class="sxs-lookup"><span data-stu-id="165dd-114">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="165dd-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="165dd-115">Message</span></span>  

 <span data-ttu-id="165dd-116">WorkflowApplication с идентификатором «%1» перешло в состояние простоя.</span><span class="sxs-lookup"><span data-stu-id="165dd-116">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="165dd-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="165dd-117">Details</span></span>  
  
|<span data-ttu-id="165dd-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="165dd-118">Data Item Name</span></span>|<span data-ttu-id="165dd-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="165dd-119">Data Item Type</span></span>|<span data-ttu-id="165dd-120">Описание</span><span class="sxs-lookup"><span data-stu-id="165dd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="165dd-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="165dd-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="165dd-122">Идентификатор приложения рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="165dd-122">The workflow application id</span></span>|  
|<span data-ttu-id="165dd-123">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="165dd-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="165dd-124">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="165dd-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
