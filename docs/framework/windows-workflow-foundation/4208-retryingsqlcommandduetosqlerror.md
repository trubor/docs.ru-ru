---
description: 'Дополнительные сведения: 4208-Ретрингсклкомманддуетосклеррор'
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 11ea2260f6a2ceffc1ffdbfce2cb3e3ce784076d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755308"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="9a97b-103">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="9a97b-103">4208 - RetryingSqlCommandDueToSqlError</span></span>

## <a name="properties"></a><span data-ttu-id="9a97b-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="9a97b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a97b-105">ID</span><span class="sxs-lookup"><span data-stu-id="9a97b-105">ID</span></span>|<span data-ttu-id="9a97b-106">4208</span><span class="sxs-lookup"><span data-stu-id="9a97b-106">4208</span></span>|  
|<span data-ttu-id="9a97b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9a97b-107">Keywords</span></span>|<span data-ttu-id="9a97b-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="9a97b-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="9a97b-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="9a97b-109">Level</span></span>|<span data-ttu-id="9a97b-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="9a97b-110">Information</span></span>|  
|<span data-ttu-id="9a97b-111">Канал</span><span class="sxs-lookup"><span data-stu-id="9a97b-111">Channel</span></span>|<span data-ttu-id="9a97b-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9a97b-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a97b-113">Описание</span><span class="sxs-lookup"><span data-stu-id="9a97b-113">Description</span></span>  

 <span data-ttu-id="9a97b-114">Указывает, что поставщик SQL повторяет команду SQL из-за ошибки SQL.</span><span class="sxs-lookup"><span data-stu-id="9a97b-114">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a97b-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="9a97b-115">Message</span></span>  

 <span data-ttu-id="9a97b-116">Выполняется повтор команды SQL из-за ошибки SQL с номером %1.</span><span class="sxs-lookup"><span data-stu-id="9a97b-116">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a97b-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="9a97b-117">Details</span></span>  
  
|<span data-ttu-id="9a97b-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="9a97b-118">Data Item Name</span></span>|<span data-ttu-id="9a97b-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="9a97b-119">Data Item Type</span></span>|<span data-ttu-id="9a97b-120">Описание</span><span class="sxs-lookup"><span data-stu-id="9a97b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a97b-121">Номер ошибки</span><span class="sxs-lookup"><span data-stu-id="9a97b-121">ErrorNumber</span></span>|<span data-ttu-id="9a97b-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a97b-122">xs:string</span></span>|<span data-ttu-id="9a97b-123">Номер ошибки SQL.</span><span class="sxs-lookup"><span data-stu-id="9a97b-123">The SQL error number.</span></span>|  
|<span data-ttu-id="9a97b-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="9a97b-124">AppDomain</span></span>|<span data-ttu-id="9a97b-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a97b-125">xs:string</span></span>|<span data-ttu-id="9a97b-126">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9a97b-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
