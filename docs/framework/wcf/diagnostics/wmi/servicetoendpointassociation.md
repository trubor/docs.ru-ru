---
description: 'Дополнительные сведения о: СервицетоендпоинтассоЦиатион'
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 1ae2ce2bcc0b3494b00fffa750f3ca46d26fe08f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715344"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="3c801-103">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="3c801-103">ServiceToEndpointAssociation</span></span>

<span data-ttu-id="3c801-104">Сопоставляет службу конечной точке.</span><span class="sxs-lookup"><span data-stu-id="3c801-104">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c801-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c801-105">Syntax</span></span>  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3c801-106">Методы</span><span class="sxs-lookup"><span data-stu-id="3c801-106">Methods</span></span>  

 <span data-ttu-id="3c801-107">Класс ServiceToEndpointAssociation не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="3c801-107">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3c801-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="3c801-108">Properties</span></span>  

 <span data-ttu-id="3c801-109">Класс ServiceToEndpointAssociation имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="3c801-109">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="3c801-110">ref</span><span class="sxs-lookup"><span data-stu-id="3c801-110">ref</span></span>  

 <span data-ttu-id="3c801-111">Тип данных: Service</span><span class="sxs-lookup"><span data-stu-id="3c801-111">Data type: Service</span></span>  
  
 <span data-ttu-id="3c801-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="3c801-112">Access type: Read-only</span></span>  
<span data-ttu-id="3c801-113">Квалификаторы: ключ</span><span class="sxs-lookup"><span data-stu-id="3c801-113">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="3c801-114">Служба, связанная с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="3c801-114">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="3c801-115">ref</span><span class="sxs-lookup"><span data-stu-id="3c801-115">ref</span></span>  

 <span data-ttu-id="3c801-116">Тип данных: Endpoint</span><span class="sxs-lookup"><span data-stu-id="3c801-116">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="3c801-117">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="3c801-117">Access type: Read-only</span></span>  
<span data-ttu-id="3c801-118">Квалификаторы: ключ</span><span class="sxs-lookup"><span data-stu-id="3c801-118">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="3c801-119">Конечная точка, связанная со службой.</span><span class="sxs-lookup"><span data-stu-id="3c801-119">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c801-120">Требования</span><span class="sxs-lookup"><span data-stu-id="3c801-120">Requirements</span></span>  
  
|<span data-ttu-id="3c801-121">MOF</span><span class="sxs-lookup"><span data-stu-id="3c801-121">MOF</span></span>|<span data-ttu-id="3c801-122">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3c801-122">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3c801-123">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="3c801-123">Namespace</span></span>|<span data-ttu-id="3c801-124">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="3c801-124">Defined in root\ServiceModel</span></span>|
