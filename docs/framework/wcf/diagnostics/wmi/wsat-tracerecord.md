---
description: 'Дополнительные сведения: WSAT_TraceRecord'
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 67202c5d2910783c40b934d2da6108e6b514a728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756881"
---
# <a name="wsat_tracerecord"></a><span data-ttu-id="90c38-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="90c38-103">WSAT_TraceRecord</span></span>

<span data-ttu-id="90c38-104">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="90c38-104">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c38-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="90c38-105">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="90c38-106">Методы</span><span class="sxs-lookup"><span data-stu-id="90c38-106">Methods</span></span>  

 <span data-ttu-id="90c38-107">Класс WSAT_TraceRecord не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="90c38-107">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="90c38-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="90c38-108">Properties</span></span>  

 <span data-ttu-id="90c38-109">Класс WSAT_TraceRecord имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="90c38-109">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="90c38-110">Идентификатор действия</span><span class="sxs-lookup"><span data-stu-id="90c38-110">ActivityID</span></span>  

 <span data-ttu-id="90c38-111">Тип данных: объект</span><span class="sxs-lookup"><span data-stu-id="90c38-111">Data type: object</span></span>  
<span data-ttu-id="90c38-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="90c38-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="90c38-113">ИД активности записи трассировки.</span><span class="sxs-lookup"><span data-stu-id="90c38-113">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="90c38-114">EventID</span><span class="sxs-lookup"><span data-stu-id="90c38-114">EventID</span></span>  

 <span data-ttu-id="90c38-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="90c38-115">Data type: sint32</span></span>  
<span data-ttu-id="90c38-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="90c38-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="90c38-117">ИД события записи трассировки.</span><span class="sxs-lookup"><span data-stu-id="90c38-117">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="90c38-118">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="90c38-118">TraceRecord</span></span>  

 <span data-ttu-id="90c38-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="90c38-119">Data type: string</span></span>  
<span data-ttu-id="90c38-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="90c38-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="90c38-121">Запись трассировки</span><span class="sxs-lookup"><span data-stu-id="90c38-121">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90c38-122">Требования</span><span class="sxs-lookup"><span data-stu-id="90c38-122">Requirements</span></span>  
  
|<span data-ttu-id="90c38-123">MOF</span><span class="sxs-lookup"><span data-stu-id="90c38-123">MOF</span></span>|<span data-ttu-id="90c38-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="90c38-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="90c38-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="90c38-125">Namespace</span></span>|<span data-ttu-id="90c38-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="90c38-126">Defined in root\ServiceModel</span></span>|
