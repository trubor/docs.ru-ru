---
description: 'Дополнительные сведения о: атрибут DeliveryRequirementsAttribute'
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: ee27ada1c1fb447de3d7a108a4a285ca106e4e8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757505"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="7220d-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="7220d-103">DeliveryRequirementsAttribute</span></span>

<span data-ttu-id="7220d-104">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="7220d-104">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7220d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7220d-105">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7220d-106">Методы</span><span class="sxs-lookup"><span data-stu-id="7220d-106">Methods</span></span>  

 <span data-ttu-id="7220d-107">Класс DeliveryRequirementsAttribute не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="7220d-107">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7220d-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="7220d-108">Properties</span></span>  

 <span data-ttu-id="7220d-109">Класс DeliveryRequirementsAttribute имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="7220d-109">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="7220d-110">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="7220d-110">QueuedDeliveryRequirements</span></span>  

 <span data-ttu-id="7220d-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="7220d-111">Data type: string</span></span>  
  
 <span data-ttu-id="7220d-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="7220d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7220d-113">Указывает, поддерживает ли привязка для службы контракты.</span><span class="sxs-lookup"><span data-stu-id="7220d-113">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="7220d-114">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="7220d-114">RequireOrderedDelivery</span></span>  

 <span data-ttu-id="7220d-115">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="7220d-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="7220d-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="7220d-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7220d-117">Указывает, поддерживает ли привязка упорядоченные сообщения.</span><span class="sxs-lookup"><span data-stu-id="7220d-117">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="7220d-118">TargetContract</span><span class="sxs-lookup"><span data-stu-id="7220d-118">TargetContract</span></span>  

 <span data-ttu-id="7220d-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="7220d-119">Data type: string</span></span>  
  
 <span data-ttu-id="7220d-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="7220d-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7220d-121">Контракт, к которому оно применимо.</span><span class="sxs-lookup"><span data-stu-id="7220d-121">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7220d-122">Требования</span><span class="sxs-lookup"><span data-stu-id="7220d-122">Requirements</span></span>  
  
|<span data-ttu-id="7220d-123">MOF</span><span class="sxs-lookup"><span data-stu-id="7220d-123">MOF</span></span>|<span data-ttu-id="7220d-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7220d-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7220d-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="7220d-125">Namespace</span></span>|<span data-ttu-id="7220d-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="7220d-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7220d-127">См. также</span><span class="sxs-lookup"><span data-stu-id="7220d-127">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
