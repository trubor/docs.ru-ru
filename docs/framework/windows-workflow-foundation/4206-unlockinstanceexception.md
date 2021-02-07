---
description: 'Дополнительные сведения: 4206-Унлоккинстанцеексцептион'
title: 4206 - UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 7c281b7471869fc2361b1c7fb158559e4c9fae65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676278"
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="48610-103">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="48610-103">4206 - UnlockInstanceException</span></span>

## <a name="properties"></a><span data-ttu-id="48610-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="48610-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48610-105">ID</span><span class="sxs-lookup"><span data-stu-id="48610-105">ID</span></span>|<span data-ttu-id="48610-106">4206</span><span class="sxs-lookup"><span data-stu-id="48610-106">4206</span></span>|  
|<span data-ttu-id="48610-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="48610-107">Keywords</span></span>|<span data-ttu-id="48610-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="48610-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="48610-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="48610-109">Level</span></span>|<span data-ttu-id="48610-110">Ошибка</span><span class="sxs-lookup"><span data-stu-id="48610-110">Error</span></span>|  
|<span data-ttu-id="48610-111">Канал</span><span class="sxs-lookup"><span data-stu-id="48610-111">Channel</span></span>|<span data-ttu-id="48610-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="48610-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="48610-113">Описание</span><span class="sxs-lookup"><span data-stu-id="48610-113">Description</span></span>  

 <span data-ttu-id="48610-114">Указывает, что при попытке разблокировать экземпляр возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="48610-114">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="48610-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="48610-115">Message</span></span>  

 <span data-ttu-id="48610-116">При попытке разблокировать экземпляр обнаружено исключение «%1».</span><span class="sxs-lookup"><span data-stu-id="48610-116">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="48610-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="48610-117">Details</span></span>  
  
|<span data-ttu-id="48610-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="48610-118">Data Item Name</span></span>|<span data-ttu-id="48610-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="48610-119">Data Item Type</span></span>|<span data-ttu-id="48610-120">Описание</span><span class="sxs-lookup"><span data-stu-id="48610-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="48610-121">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="48610-121">ExceptionMessage</span></span>|<span data-ttu-id="48610-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="48610-122">xs:string</span></span>|<span data-ttu-id="48610-123">Текст сообщения из исключения SQL.</span><span class="sxs-lookup"><span data-stu-id="48610-123">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="48610-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="48610-124">AppDomain</span></span>|<span data-ttu-id="48610-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="48610-125">xs:string</span></span>|<span data-ttu-id="48610-126">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="48610-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
