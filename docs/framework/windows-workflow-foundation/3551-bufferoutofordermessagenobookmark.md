---
description: 'Дополнительные сведения: 3551-Буффераутофордермессаженобукмарк'
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 573056fed1753ac55c51d9a074047e8eea15e229
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778000"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="6dbef-103">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="6dbef-103">3551 - BufferOutOfOrderMessageNoBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="6dbef-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="6dbef-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6dbef-105">ID</span><span class="sxs-lookup"><span data-stu-id="6dbef-105">ID</span></span>|<span data-ttu-id="6dbef-106">3551</span><span class="sxs-lookup"><span data-stu-id="6dbef-106">3551</span></span>|  
|<span data-ttu-id="6dbef-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="6dbef-107">Keywords</span></span>|<span data-ttu-id="6dbef-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="6dbef-108">WFServices</span></span>|  
|<span data-ttu-id="6dbef-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="6dbef-109">Level</span></span>|<span data-ttu-id="6dbef-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="6dbef-110">Information</span></span>|  
|<span data-ttu-id="6dbef-111">Канал</span><span class="sxs-lookup"><span data-stu-id="6dbef-111">Channel</span></span>|<span data-ttu-id="6dbef-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6dbef-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6dbef-113">Описание</span><span class="sxs-lookup"><span data-stu-id="6dbef-113">Description</span></span>  

 <span data-ttu-id="6dbef-114">Указывает на сбой возобновления закладки.</span><span class="sxs-lookup"><span data-stu-id="6dbef-114">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="6dbef-115">Следующая попытка выполнить операцию получения через буфер будет предпринята, когда экземпляр службы будет готов к обработке именно этой операции.</span><span class="sxs-lookup"><span data-stu-id="6dbef-115">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6dbef-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="6dbef-116">Message</span></span>  

 <span data-ttu-id="6dbef-117">Операция «%2» в экземпляре службы «%1» не может быть выполнена в данный момент.</span><span class="sxs-lookup"><span data-stu-id="6dbef-117">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="6dbef-118">Следующая попытка будет предпринята, когда экземпляр службы будет готов к обработке именно этой операции.</span><span class="sxs-lookup"><span data-stu-id="6dbef-118">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6dbef-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="6dbef-119">Details</span></span>  
  
|<span data-ttu-id="6dbef-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="6dbef-120">Data Item Name</span></span>|<span data-ttu-id="6dbef-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="6dbef-121">Data Item Type</span></span>|<span data-ttu-id="6dbef-122">Описание</span><span class="sxs-lookup"><span data-stu-id="6dbef-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6dbef-123">OperationName</span><span class="sxs-lookup"><span data-stu-id="6dbef-123">OperationName</span></span>|<span data-ttu-id="6dbef-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6dbef-124">xs:string</span></span>|<span data-ttu-id="6dbef-125">Имя операции.</span><span class="sxs-lookup"><span data-stu-id="6dbef-125">The name of the operation.</span></span>|  
|<span data-ttu-id="6dbef-126">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="6dbef-126">ServiceInstanceId</span></span>|<span data-ttu-id="6dbef-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6dbef-127">xs:string</span></span>|<span data-ttu-id="6dbef-128">Идентификатор экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="6dbef-128">The id of the service instance.</span></span>|  
|<span data-ttu-id="6dbef-129">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="6dbef-129">AppDomain</span></span>|<span data-ttu-id="6dbef-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="6dbef-130">xs:string</span></span>|<span data-ttu-id="6dbef-131">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6dbef-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
