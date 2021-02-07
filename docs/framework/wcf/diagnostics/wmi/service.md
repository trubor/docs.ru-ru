---
description: 'Дополнительные сведения: служба'
title: Служба
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: e66f9a23f8c182327899904c26ff6a6368b9bdc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715630"
---
# <a name="service"></a><span data-ttu-id="39d35-103">Служба</span><span class="sxs-lookup"><span data-stu-id="39d35-103">Service</span></span>

<span data-ttu-id="39d35-104">Служба</span><span class="sxs-lookup"><span data-stu-id="39d35-104">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d35-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39d35-105">Syntax</span></span>  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="39d35-106">Методы</span><span class="sxs-lookup"><span data-stu-id="39d35-106">Methods</span></span>  

 <span data-ttu-id="39d35-107">Класс Service не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="39d35-107">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="39d35-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="39d35-108">Properties</span></span>  

 <span data-ttu-id="39d35-109">Класс Service имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="39d35-109">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="39d35-110">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="39d35-110">BaseAddresses</span></span>  

 <span data-ttu-id="39d35-111">Тип данных: массив строк</span><span class="sxs-lookup"><span data-stu-id="39d35-111">Data type: string array</span></span>  
  
 <span data-ttu-id="39d35-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-113">Базовые адреса, используемые службой.</span><span class="sxs-lookup"><span data-stu-id="39d35-113">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="39d35-114">Расширения функциональности</span><span class="sxs-lookup"><span data-stu-id="39d35-114">Behaviors</span></span>  

 <span data-ttu-id="39d35-115">Тип данных: массив Behavior</span><span class="sxs-lookup"><span data-stu-id="39d35-115">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="39d35-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-117">Поведения, связанные с этой службой.</span><span class="sxs-lookup"><span data-stu-id="39d35-117">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="39d35-118">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="39d35-118">ConfigurationName</span></span>  

 <span data-ttu-id="39d35-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="39d35-119">Data type: string</span></span>  
  
 <span data-ttu-id="39d35-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-121">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="39d35-121">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="39d35-122">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="39d35-122">CounterInstanceName</span></span>  

 <span data-ttu-id="39d35-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="39d35-123">Data type: string</span></span>  
  
 <span data-ttu-id="39d35-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-125">Имя экземпляра счетчиков производительности службы.</span><span class="sxs-lookup"><span data-stu-id="39d35-125">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="39d35-126">Различающееся имя.</span><span class="sxs-lookup"><span data-stu-id="39d35-126">DistinguishedName</span></span>  

 <span data-ttu-id="39d35-127">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="39d35-127">Data type: string</span></span>  
  
 <span data-ttu-id="39d35-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-129">Имя службы по адресу.</span><span class="sxs-lookup"><span data-stu-id="39d35-129">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="39d35-130">Расширения</span><span class="sxs-lookup"><span data-stu-id="39d35-130">Extensions</span></span>  

 <span data-ttu-id="39d35-131">Тип данных: массив строк</span><span class="sxs-lookup"><span data-stu-id="39d35-131">Data type: string array</span></span>  
  
 <span data-ttu-id="39d35-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-133">Контексты экземпляра для расширений экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="39d35-133">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="39d35-134">Метаданные</span><span class="sxs-lookup"><span data-stu-id="39d35-134">Metadata</span></span>  

 <span data-ttu-id="39d35-135">Тип данных: массив строк</span><span class="sxs-lookup"><span data-stu-id="39d35-135">Data type: string array</span></span>  
  
 <span data-ttu-id="39d35-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-137">Параметры метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="39d35-137">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="39d35-138">Имя</span><span class="sxs-lookup"><span data-stu-id="39d35-138">Name</span></span>  

 <span data-ttu-id="39d35-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="39d35-139">Data type: string</span></span>  
  
 <span data-ttu-id="39d35-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-141">Уникальное имя службы.</span><span class="sxs-lookup"><span data-stu-id="39d35-141">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="39d35-142">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="39d35-142">Namespace</span></span>  

 <span data-ttu-id="39d35-143">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="39d35-143">Data type: string</span></span>  
  
 <span data-ttu-id="39d35-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-145">Пространство имен службы.</span><span class="sxs-lookup"><span data-stu-id="39d35-145">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="39d35-146">Opened (Открыто)</span><span class="sxs-lookup"><span data-stu-id="39d35-146">Opened</span></span>  

 <span data-ttu-id="39d35-147">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="39d35-147">Data type: datetime</span></span>  
  
 <span data-ttu-id="39d35-148">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-149">Время открытия службы.</span><span class="sxs-lookup"><span data-stu-id="39d35-149">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="39d35-150">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="39d35-150">OutgoingChannels</span></span>  

 <span data-ttu-id="39d35-151">Тип данных: массив Channel</span><span class="sxs-lookup"><span data-stu-id="39d35-151">Data type: Channel array</span></span>  
  
 <span data-ttu-id="39d35-152">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-153">Каналы, исходящие из экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="39d35-153">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="39d35-154">ProcessId</span><span class="sxs-lookup"><span data-stu-id="39d35-154">ProcessId</span></span>  

 <span data-ttu-id="39d35-155">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="39d35-155">Data type: sint32</span></span>  
  
 <span data-ttu-id="39d35-156">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="39d35-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39d35-157">Возвращает ИД процесса, который размещает службу.</span><span class="sxs-lookup"><span data-stu-id="39d35-157">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39d35-158">Требования</span><span class="sxs-lookup"><span data-stu-id="39d35-158">Requirements</span></span>  
  
|<span data-ttu-id="39d35-159">MOF</span><span class="sxs-lookup"><span data-stu-id="39d35-159">MOF</span></span>|<span data-ttu-id="39d35-160">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="39d35-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="39d35-161">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="39d35-161">Namespace</span></span>|<span data-ttu-id="39d35-162">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="39d35-162">Defined in root\ServiceModel</span></span>|
