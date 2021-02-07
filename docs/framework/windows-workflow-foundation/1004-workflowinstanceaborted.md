---
description: 'Дополнительные сведения: 1004-Воркфловинстанцеабортед'
title: 1004 ― WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: 4aaa0899da9b0b8510684a13537a8cb8f9117ee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755626"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="96b28-103">1004 ― WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="96b28-103">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="96b28-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="96b28-104">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="96b28-105">ID</span><span class="sxs-lookup"><span data-stu-id="96b28-105">ID</span></span>|<span data-ttu-id="96b28-106">1004</span><span class="sxs-lookup"><span data-stu-id="96b28-106">1004</span></span>|
|<span data-ttu-id="96b28-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="96b28-107">Keywords</span></span>|<span data-ttu-id="96b28-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="96b28-108">WFRuntime</span></span>|
|<span data-ttu-id="96b28-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="96b28-109">Level</span></span>|<span data-ttu-id="96b28-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="96b28-110">Information</span></span>|
|<span data-ttu-id="96b28-111">Канал</span><span class="sxs-lookup"><span data-stu-id="96b28-111">Channel</span></span>|<span data-ttu-id="96b28-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="96b28-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="96b28-113">Описание</span><span class="sxs-lookup"><span data-stu-id="96b28-113">Description</span></span>

<span data-ttu-id="96b28-114">Указывает, что экземпляр рабочего процесса прерван с исключением.</span><span class="sxs-lookup"><span data-stu-id="96b28-114">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="96b28-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="96b28-115">Message</span></span>

<span data-ttu-id="96b28-116">Выполнение элемента WorkflowInstance с идентификатором «%1» было прервано в результате исключения.</span><span class="sxs-lookup"><span data-stu-id="96b28-116">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="96b28-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="96b28-117">Details</span></span>

|<span data-ttu-id="96b28-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="96b28-118">Data Item Name</span></span>|<span data-ttu-id="96b28-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="96b28-119">Data Item Type</span></span>|<span data-ttu-id="96b28-120">Описание</span><span class="sxs-lookup"><span data-stu-id="96b28-120">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="96b28-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="96b28-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="96b28-122">Идентификатор экземпляра для рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="96b28-122">The instance id for the workflow</span></span>|
|<span data-ttu-id="96b28-123">Исключение</span><span class="sxs-lookup"><span data-stu-id="96b28-123">Exception</span></span>|`xs:string`|<span data-ttu-id="96b28-124">Сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="96b28-124">The exception details for the exception</span></span>|
|<span data-ttu-id="96b28-125">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="96b28-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="96b28-126">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="96b28-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
