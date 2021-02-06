---
description: 'Дополнительные сведения: 3502-Инферредоператиондескриптион'
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 5068a3553484b38242951ef985886190f8027035
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631493"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="54a16-103">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="54a16-103">3502 - InferredOperationDescription</span></span>

## <a name="properties"></a><span data-ttu-id="54a16-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="54a16-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54a16-105">ID</span><span class="sxs-lookup"><span data-stu-id="54a16-105">ID</span></span>|<span data-ttu-id="54a16-106">3502</span><span class="sxs-lookup"><span data-stu-id="54a16-106">3502</span></span>|  
|<span data-ttu-id="54a16-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="54a16-107">Keywords</span></span>|<span data-ttu-id="54a16-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="54a16-108">WFServices</span></span>|  
|<span data-ttu-id="54a16-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="54a16-109">Level</span></span>|<span data-ttu-id="54a16-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="54a16-110">Information</span></span>|  
|<span data-ttu-id="54a16-111">Канал</span><span class="sxs-lookup"><span data-stu-id="54a16-111">Channel</span></span>|<span data-ttu-id="54a16-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="54a16-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="54a16-113">Описание</span><span class="sxs-lookup"><span data-stu-id="54a16-113">Description</span></span>  

 <span data-ttu-id="54a16-114">Указывает, что описание операции OperationDescription выведено из WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="54a16-114">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="54a16-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="54a16-115">Message</span></span>  

 <span data-ttu-id="54a16-116">Описание OperationDescription с параметром Name=«%1» в контракте «%2» было выведено из WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="54a16-116">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="54a16-117">IsOneWay=%3.</span><span class="sxs-lookup"><span data-stu-id="54a16-117">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="54a16-118">Сведения</span><span class="sxs-lookup"><span data-stu-id="54a16-118">Details</span></span>  
  
|<span data-ttu-id="54a16-119">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="54a16-119">Data Item Name</span></span>|<span data-ttu-id="54a16-120">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="54a16-120">Data Item Type</span></span>|<span data-ttu-id="54a16-121">Описание</span><span class="sxs-lookup"><span data-stu-id="54a16-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="54a16-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="54a16-122">OperationName</span></span>|<span data-ttu-id="54a16-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="54a16-123">xs:string</span></span>|<span data-ttu-id="54a16-124">Имя операции.</span><span class="sxs-lookup"><span data-stu-id="54a16-124">The name of the operation.</span></span>|  
|<span data-ttu-id="54a16-125">ContractName</span><span class="sxs-lookup"><span data-stu-id="54a16-125">ContractName</span></span>|<span data-ttu-id="54a16-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="54a16-126">xs:string</span></span>|<span data-ttu-id="54a16-127">Имя контракта.</span><span class="sxs-lookup"><span data-stu-id="54a16-127">The name of the contract.</span></span>|  
|<span data-ttu-id="54a16-128">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="54a16-128">IsOneWay</span></span>|<span data-ttu-id="54a16-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="54a16-129">xs:string</span></span>|<span data-ttu-id="54a16-130">Логическое значение True или False, указывающее, является ли контракт односторонним.</span><span class="sxs-lookup"><span data-stu-id="54a16-130">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="54a16-131">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="54a16-131">AppDomain</span></span>|<span data-ttu-id="54a16-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="54a16-132">xs:string</span></span>|<span data-ttu-id="54a16-133">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="54a16-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
