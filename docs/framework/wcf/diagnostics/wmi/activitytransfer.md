---
description: 'Дополнительные сведения о: Активититрансфер'
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 28f7d1c0d1056327313e7aa6be293eb325d8f265
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758012"
---
# <a name="activitytransfer"></a><span data-ttu-id="a28c1-103">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="a28c1-103">ActivityTransfer</span></span>

<span data-ttu-id="a28c1-104">Событие перенаправления действия</span><span class="sxs-lookup"><span data-stu-id="a28c1-104">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a28c1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a28c1-105">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a28c1-106">Методы</span><span class="sxs-lookup"><span data-stu-id="a28c1-106">Methods</span></span>  

 <span data-ttu-id="a28c1-107">Класс ActivityTransfer не определяет никакие методы.</span><span class="sxs-lookup"><span data-stu-id="a28c1-107">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a28c1-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="a28c1-108">Properties</span></span>  

 <span data-ttu-id="a28c1-109">Класс ActivityTransfer имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="a28c1-109">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="a28c1-110">Идентификатор действия</span><span class="sxs-lookup"><span data-stu-id="a28c1-110">ActivityID</span></span>  
  
- <span data-ttu-id="a28c1-111">Тип данных: объект</span><span class="sxs-lookup"><span data-stu-id="a28c1-111">Data type: object</span></span>  
    <span data-ttu-id="a28c1-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="a28c1-112">Access type: Read-only</span></span>  
  
- <span data-ttu-id="a28c1-113">Идентификатор действия</span><span class="sxs-lookup"><span data-stu-id="a28c1-113">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="a28c1-114">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="a28c1-114">RelatedActivityID</span></span>  
  
- <span data-ttu-id="a28c1-115">Тип данных: объект</span><span class="sxs-lookup"><span data-stu-id="a28c1-115">Data type: object</span></span>  
    <span data-ttu-id="a28c1-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="a28c1-116">Access type: Read-only</span></span>  
  
- <span data-ttu-id="a28c1-117">Связанный идентификатор действия</span><span class="sxs-lookup"><span data-stu-id="a28c1-117">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a28c1-118">Требования</span><span class="sxs-lookup"><span data-stu-id="a28c1-118">Requirements</span></span>  
  
|<span data-ttu-id="a28c1-119">MOF</span><span class="sxs-lookup"><span data-stu-id="a28c1-119">MOF</span></span>|<span data-ttu-id="a28c1-120">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a28c1-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a28c1-121">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="a28c1-121">Namespace</span></span>|<span data-ttu-id="a28c1-122">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="a28c1-122">Defined in root\ServiceModel.</span></span>|
