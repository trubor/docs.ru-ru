---
description: 'Дополнительные сведения: 1125-Инвокемесодиснотстатик'
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: cd63b7b75121a70f7d7bad6a799827971aa4eae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667373"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="93730-103">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="93730-103">1125 - InvokeMethodIsNotStatic</span></span>

## <a name="properties"></a><span data-ttu-id="93730-104">Свойства</span><span class="sxs-lookup"><span data-stu-id="93730-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93730-105">ID</span><span class="sxs-lookup"><span data-stu-id="93730-105">ID</span></span>|<span data-ttu-id="93730-106">1125</span><span class="sxs-lookup"><span data-stu-id="93730-106">1125</span></span>|  
|<span data-ttu-id="93730-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="93730-107">Keywords</span></span>|<span data-ttu-id="93730-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="93730-108">WFRuntime</span></span>|  
|<span data-ttu-id="93730-109">Уровень</span><span class="sxs-lookup"><span data-stu-id="93730-109">Level</span></span>|<span data-ttu-id="93730-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="93730-110">Information</span></span>|  
|<span data-ttu-id="93730-111">Канал</span><span class="sxs-lookup"><span data-stu-id="93730-111">Channel</span></span>|<span data-ttu-id="93730-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="93730-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="93730-113">Описание</span><span class="sxs-lookup"><span data-stu-id="93730-113">Description</span></span>  

 <span data-ttu-id="93730-114">На шаге CacheMetadata действие InvokeMethod означает, что вызываемый метод - не статический.</span><span class="sxs-lookup"><span data-stu-id="93730-114">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="93730-115">Сообщение</span><span class="sxs-lookup"><span data-stu-id="93730-115">Message</span></span>  

 <span data-ttu-id="93730-116">Метод InvokeMethod «%1»: метод не является статическим.</span><span class="sxs-lookup"><span data-stu-id="93730-116">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="93730-117">Сведения</span><span class="sxs-lookup"><span data-stu-id="93730-117">Details</span></span>  
  
|<span data-ttu-id="93730-118">Имя элемента данных</span><span class="sxs-lookup"><span data-stu-id="93730-118">Data Item Name</span></span>|<span data-ttu-id="93730-119">Тип элемента данных</span><span class="sxs-lookup"><span data-stu-id="93730-119">Data Item Type</span></span>|<span data-ttu-id="93730-120">Описание</span><span class="sxs-lookup"><span data-stu-id="93730-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="93730-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="93730-121">InvokeMethod</span></span>|<span data-ttu-id="93730-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="93730-122">xs:string</span></span>|<span data-ttu-id="93730-123">Отображаемое имя действия InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="93730-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="93730-124">Домен приложения</span><span class="sxs-lookup"><span data-stu-id="93730-124">AppDomain</span></span>|<span data-ttu-id="93730-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="93730-125">xs:string</span></span>|<span data-ttu-id="93730-126">Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="93730-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
