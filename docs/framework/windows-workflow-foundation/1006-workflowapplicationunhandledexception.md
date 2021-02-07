---
description: 'Дополнительные сведения: 1006-Воркфловаппликатионунхандледексцептион'
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: bfccd0d12c5dac4caad1e84e95f1cd096a551aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755594"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="b7830-103">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="b7830-103">1006 - WorkflowApplicationUnhandledException</span></span>

## <a name="properties"></a><span data-ttu-id="b7830-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="b7830-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7830-105">ID</span><span class="sxs-lookup"><span data-stu-id="b7830-105">ID</span></span>|<span data-ttu-id="b7830-106">1006</span><span class="sxs-lookup"><span data-stu-id="b7830-106">1006</span></span>|  
|<span data-ttu-id="b7830-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="b7830-107">Keywords</span></span>|<span data-ttu-id="b7830-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b7830-108">WFRuntime</span></span>|  
|<span data-ttu-id="b7830-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="b7830-109">Level</span></span>|<span data-ttu-id="b7830-110">Ошибка</span><span class="sxs-lookup"><span data-stu-id="b7830-110">Error</span></span>|  
|<span data-ttu-id="b7830-111">Канал</span><span class="sxs-lookup"><span data-stu-id="b7830-111">Channel</span></span>|<span data-ttu-id="b7830-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b7830-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7830-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b7830-113">Description</span></span>  

 <span data-ttu-id="b7830-114">Указывает, что приложение рабочего процесса обнаружило необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="b7830-114">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7830-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="b7830-115">Message</span></span>  

 <span data-ttu-id="b7830-116">Элемент WorkflowInstance с идентификатором "%1" обнаружил необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="b7830-116">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="b7830-117">Исключение произошло из действия "%2", DisplayName: "%3".</span><span class="sxs-lookup"><span data-stu-id="b7830-117">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="b7830-118">Будет выполнено следующее действие: %4.</span><span class="sxs-lookup"><span data-stu-id="b7830-118">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7830-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="b7830-119">Details</span></span>  
  
|<span data-ttu-id="b7830-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="b7830-120">Data Item Name</span></span>|<span data-ttu-id="b7830-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="b7830-121">Data Item Type</span></span>|<span data-ttu-id="b7830-122">Описание</span><span class="sxs-lookup"><span data-stu-id="b7830-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7830-123">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="b7830-123">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="b7830-124">Идентификатор экземпляра для рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="b7830-124">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b7830-125">Исключение</span><span class="sxs-lookup"><span data-stu-id="b7830-125">Exception</span></span>|`xs:string`|<span data-ttu-id="b7830-126">Сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="b7830-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="b7830-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="b7830-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b7830-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b7830-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
