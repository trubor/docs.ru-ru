---
description: 'Дополнительные сведения о: Сервицетимеаутсбехавиор'
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 147d249af0e87bc41da93a4a31355da7053caaf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715422"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="a69f7-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="a69f7-103">ServiceTimeoutsBehavior</span></span>

<span data-ttu-id="a69f7-104">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="a69f7-104">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a69f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a69f7-105">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a69f7-106">Методы</span><span class="sxs-lookup"><span data-stu-id="a69f7-106">Methods</span></span>  

 <span data-ttu-id="a69f7-107">Класс ServiceTimeoutsBehavior не определяет никакие методы.</span><span class="sxs-lookup"><span data-stu-id="a69f7-107">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a69f7-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="a69f7-108">Properties</span></span>  

 <span data-ttu-id="a69f7-109">Класс ServiceTimeoutsBehavior имеет следующее свойство.</span><span class="sxs-lookup"><span data-stu-id="a69f7-109">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="a69f7-110">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="a69f7-110">TransactionTimeout</span></span>  

 <span data-ttu-id="a69f7-111">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="a69f7-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="a69f7-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="a69f7-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a69f7-113">Период времени, в течение которого транзакция должна быть завершена.</span><span class="sxs-lookup"><span data-stu-id="a69f7-113">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a69f7-114">Требования</span><span class="sxs-lookup"><span data-stu-id="a69f7-114">Requirements</span></span>  
  
|<span data-ttu-id="a69f7-115">MOF</span><span class="sxs-lookup"><span data-stu-id="a69f7-115">MOF</span></span>|<span data-ttu-id="a69f7-116">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a69f7-116">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a69f7-117">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="a69f7-117">Namespace</span></span>|<span data-ttu-id="a69f7-118">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="a69f7-118">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a69f7-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a69f7-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
