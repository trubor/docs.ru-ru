---
description: 'Дополнительные сведения: 3550-Буффераутофордермессаженоинстанце'
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: cb51f9fa32de1b56560f9593dae2ec82c100dc65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631454"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="5f4d5-103">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="5f4d5-103">3550 - BufferOutOfOrderMessageNoInstance</span></span>

## <a name="properties"></a><span data-ttu-id="5f4d5-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="5f4d5-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f4d5-105">ID</span><span class="sxs-lookup"><span data-stu-id="5f4d5-105">ID</span></span>|<span data-ttu-id="5f4d5-106">3550</span><span class="sxs-lookup"><span data-stu-id="5f4d5-106">3550</span></span>|  
|<span data-ttu-id="5f4d5-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="5f4d5-107">Keywords</span></span>|<span data-ttu-id="5f4d5-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="5f4d5-108">WFServices</span></span>|  
|<span data-ttu-id="5f4d5-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="5f4d5-109">Level</span></span>|<span data-ttu-id="5f4d5-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="5f4d5-110">Information</span></span>|  
|<span data-ttu-id="5f4d5-111">Канал</span><span class="sxs-lookup"><span data-stu-id="5f4d5-111">Channel</span></span>|<span data-ttu-id="5f4d5-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5f4d5-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5f4d5-113">Описание</span><span class="sxs-lookup"><span data-stu-id="5f4d5-113">Description</span></span>  

 <span data-ttu-id="5f4d5-114">Указывает, что получение через буфер не удалось.</span><span class="sxs-lookup"><span data-stu-id="5f4d5-114">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="5f4d5-115">Следующая попытка выполнить операцию будет предпринята, когда экземпляр службы будет готов к обработке именно этой операции.</span><span class="sxs-lookup"><span data-stu-id="5f4d5-115">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5f4d5-116">Сообщение</span><span class="sxs-lookup"><span data-stu-id="5f4d5-116">Message</span></span>  

 <span data-ttu-id="5f4d5-117">Операция «%1» сейчас не может быть выполнена.</span><span class="sxs-lookup"><span data-stu-id="5f4d5-117">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="5f4d5-118">Следующая попытка будет предпринята, когда экземпляр службы будет готов к обработке именно этой операции.</span><span class="sxs-lookup"><span data-stu-id="5f4d5-118">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5f4d5-119">Сведения</span><span class="sxs-lookup"><span data-stu-id="5f4d5-119">Details</span></span>  
  
|<span data-ttu-id="5f4d5-120">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="5f4d5-120">Data Item Name</span></span>|<span data-ttu-id="5f4d5-121">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="5f4d5-121">Data Item Type</span></span>|<span data-ttu-id="5f4d5-122">Описание</span><span class="sxs-lookup"><span data-stu-id="5f4d5-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5f4d5-123">OperationName</span><span class="sxs-lookup"><span data-stu-id="5f4d5-123">OperationName</span></span>|<span data-ttu-id="5f4d5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f4d5-124">xs:string</span></span>|<span data-ttu-id="5f4d5-125">Имя операции.</span><span class="sxs-lookup"><span data-stu-id="5f4d5-125">The name of the operation.</span></span>|  
|<span data-ttu-id="5f4d5-126">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="5f4d5-126">AppDomain</span></span>|<span data-ttu-id="5f4d5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f4d5-127">xs:string</span></span>|<span data-ttu-id="5f4d5-128">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5f4d5-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
