---
description: 'Дополнительные сведения: 3557-Трансактедрецеивескопиндкоммитфаилед'
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 7865ae27e7ce5b3f13b3567f3f8aeebd6edf3fd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777987"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="e8601-103">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="e8601-103">3557 - TransactedReceiveScopeEndCommitFailed</span></span>

## <a name="properties"></a><span data-ttu-id="e8601-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="e8601-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e8601-105">ID</span><span class="sxs-lookup"><span data-stu-id="e8601-105">ID</span></span>|<span data-ttu-id="e8601-106">3557</span><span class="sxs-lookup"><span data-stu-id="e8601-106">3557</span></span>|  
|<span data-ttu-id="e8601-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="e8601-107">Keywords</span></span>|<span data-ttu-id="e8601-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="e8601-108">WFServices</span></span>|  
|<span data-ttu-id="e8601-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="e8601-109">Level</span></span>|<span data-ttu-id="e8601-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="e8601-110">Information</span></span>|  
|<span data-ttu-id="e8601-111">Канал</span><span class="sxs-lookup"><span data-stu-id="e8601-111">Channel</span></span>|<span data-ttu-id="e8601-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e8601-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e8601-113">Описание</span><span class="sxs-lookup"><span data-stu-id="e8601-113">Description</span></span>  

 <span data-ttu-id="e8601-114">Указывает, что вызов к EndCommit в CommittableTransaction привел к созданию исключения TransactionException.</span><span class="sxs-lookup"><span data-stu-id="e8601-114">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e8601-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="e8601-115">Message</span></span>  

 <span data-ttu-id="e8601-116">Вызов EndCommit для CommittableTransaction с id = «%1» привел к созданию исключения TransactionException со следующим сообщением: «%2».</span><span class="sxs-lookup"><span data-stu-id="e8601-116">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e8601-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="e8601-117">Details</span></span>  
  
|<span data-ttu-id="e8601-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="e8601-118">Data Item Name</span></span>|<span data-ttu-id="e8601-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="e8601-119">Data Item Type</span></span>|<span data-ttu-id="e8601-120">Описание</span><span class="sxs-lookup"><span data-stu-id="e8601-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e8601-121">TransactionId</span><span class="sxs-lookup"><span data-stu-id="e8601-121">TransactionId</span></span>|<span data-ttu-id="e8601-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8601-122">xs:string</span></span>|<span data-ttu-id="e8601-123">Идентификатор CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="e8601-123">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="e8601-124">Исключение</span><span class="sxs-lookup"><span data-stu-id="e8601-124">Exception</span></span>|<span data-ttu-id="e8601-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8601-125">xs:string</span></span>|<span data-ttu-id="e8601-126">Сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="e8601-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="e8601-127">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="e8601-127">AppDomain</span></span>|<span data-ttu-id="e8601-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e8601-128">xs:string</span></span>|<span data-ttu-id="e8601-129">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e8601-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
