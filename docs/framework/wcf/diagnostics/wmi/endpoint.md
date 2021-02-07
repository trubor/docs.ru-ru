---
description: 'Дополнительные сведения: Endpoint'
title: Конечная точка
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 1c28be37d1b1abfe1813e6da8903809affd309e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757466"
---
# <a name="endpoint"></a><span data-ttu-id="5cf54-103">Конечная точка</span><span class="sxs-lookup"><span data-stu-id="5cf54-103">Endpoint</span></span>

<span data-ttu-id="5cf54-104">Конечная точка</span><span class="sxs-lookup"><span data-stu-id="5cf54-104">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf54-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5cf54-105">Syntax</span></span>  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5cf54-106">Методы</span><span class="sxs-lookup"><span data-stu-id="5cf54-106">Methods</span></span>  

 <span data-ttu-id="5cf54-107">Класс Endpoint определяет следующий метод.</span><span class="sxs-lookup"><span data-stu-id="5cf54-107">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="5cf54-108">Метод</span><span class="sxs-lookup"><span data-stu-id="5cf54-108">Method</span></span>|<span data-ttu-id="5cf54-109">Описание</span><span class="sxs-lookup"><span data-stu-id="5cf54-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5cf54-110">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="5cf54-110">GetOperationCounterInstanceName</span></span>](getoperationcounterinstancename.md)|<span data-ttu-id="5cf54-111">Извлекает имя экземпляра счетчика производительности операций</span><span class="sxs-lookup"><span data-stu-id="5cf54-111">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="5cf54-112">Свойства</span><span class="sxs-lookup"><span data-stu-id="5cf54-112">Properties</span></span>  

 <span data-ttu-id="5cf54-113">Класс Endpoint имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="5cf54-113">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="5cf54-114">Адрес</span><span class="sxs-lookup"><span data-stu-id="5cf54-114">Address</span></span>  

 <span data-ttu-id="5cf54-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="5cf54-115">Data type: string</span></span>  
  
 <span data-ttu-id="5cf54-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-117">Универсальный код ресурса (URI), содержащий адрес конечной точки.</span><span class="sxs-lookup"><span data-stu-id="5cf54-117">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="5cf54-118">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="5cf54-118">AddressHeaders</span></span>  

 <span data-ttu-id="5cf54-119">Тип данных: массив строк</span><span class="sxs-lookup"><span data-stu-id="5cf54-119">Data type: string array</span></span>  
  
 <span data-ttu-id="5cf54-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-121">Коллекция заголовков адреса, прикрепленных к этой конечной точке.</span><span class="sxs-lookup"><span data-stu-id="5cf54-121">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="5cf54-122">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="5cf54-122">AddressIdentity</span></span>  

 <span data-ttu-id="5cf54-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="5cf54-123">Data type: string</span></span>  
  
 <span data-ttu-id="5cf54-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-125">Удостоверение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="5cf54-125">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="5cf54-126">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="5cf54-126">AppDomainId</span></span>  

 <span data-ttu-id="5cf54-127">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="5cf54-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="5cf54-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-129">Идентификатор домена приложения, который размещает конечную точку.</span><span class="sxs-lookup"><span data-stu-id="5cf54-129">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="5cf54-130">Расширения функциональности</span><span class="sxs-lookup"><span data-stu-id="5cf54-130">Behaviors</span></span>  

 <span data-ttu-id="5cf54-131">Тип данных: массив Behavior</span><span class="sxs-lookup"><span data-stu-id="5cf54-131">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="5cf54-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-133">Коллекция поведений, реализуемых этой конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="5cf54-133">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="5cf54-134">Привязка</span><span class="sxs-lookup"><span data-stu-id="5cf54-134">Binding</span></span>  

 <span data-ttu-id="5cf54-135">Тип данных: Binding</span><span class="sxs-lookup"><span data-stu-id="5cf54-135">Data type: Binding</span></span>  
  
 <span data-ttu-id="5cf54-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-137">Привязка, используемая этой конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="5cf54-137">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="5cf54-138">ContractName</span><span class="sxs-lookup"><span data-stu-id="5cf54-138">ContractName</span></span>  

 <span data-ttu-id="5cf54-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="5cf54-139">Data type: string</span></span>  
  
 <span data-ttu-id="5cf54-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-141">Строка, в которой указывается, какой контракт предоставляется этой конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="5cf54-141">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="5cf54-142">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="5cf54-142">CounterInstanceName</span></span>  

 <span data-ttu-id="5cf54-143">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="5cf54-143">Data type: string</span></span>  
  
 <span data-ttu-id="5cf54-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-145">Имя экземпляра счетчиков производительности конечной точки.</span><span class="sxs-lookup"><span data-stu-id="5cf54-145">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="5cf54-146">ListenUri</span><span class="sxs-lookup"><span data-stu-id="5cf54-146">ListenUri</span></span>  

 <span data-ttu-id="5cf54-147">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="5cf54-147">Data type: string</span></span>  
  
 <span data-ttu-id="5cf54-148">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-149">Универсальный код ресурса (URI), от которого данная конечная точка ожидает передачи данных.</span><span class="sxs-lookup"><span data-stu-id="5cf54-149">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="5cf54-150">Имя</span><span class="sxs-lookup"><span data-stu-id="5cf54-150">Name</span></span>  

 <span data-ttu-id="5cf54-151">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="5cf54-151">Data type: string</span></span>  
  
 <span data-ttu-id="5cf54-152">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-153">Уникальное имя конечной точки.</span><span class="sxs-lookup"><span data-stu-id="5cf54-153">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="5cf54-154">ProcessId</span><span class="sxs-lookup"><span data-stu-id="5cf54-154">ProcessId</span></span>  

 <span data-ttu-id="5cf54-155">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="5cf54-155">Data type: sint32</span></span>  
  
 <span data-ttu-id="5cf54-156">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-157">Возвращает идентификатор процесса, который размещает конечную точку.</span><span class="sxs-lookup"><span data-stu-id="5cf54-157">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="5cf54-158">ref</span><span class="sxs-lookup"><span data-stu-id="5cf54-158">ref</span></span>  

 <span data-ttu-id="5cf54-159">Тип данных: Contract</span><span class="sxs-lookup"><span data-stu-id="5cf54-159">Data type: Contract</span></span>  
  
 <span data-ttu-id="5cf54-160">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5cf54-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5cf54-161">Контракт, предоставляемый этой конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="5cf54-161">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cf54-162">Требования</span><span class="sxs-lookup"><span data-stu-id="5cf54-162">Requirements</span></span>  
  
|<span data-ttu-id="5cf54-163">MOF</span><span class="sxs-lookup"><span data-stu-id="5cf54-163">MOF</span></span>|<span data-ttu-id="5cf54-164">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5cf54-164">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5cf54-165">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="5cf54-165">Namespace</span></span>|<span data-ttu-id="5cf54-166">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="5cf54-166">Defined in root\ServiceModel</span></span>|
