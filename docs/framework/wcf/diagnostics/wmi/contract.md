---
description: 'Дополнительные сведения: контракт'
title: Контракт
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 3443a7d2eed1a34f07495bd3ceb98c1ba997fabf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757557"
---
# <a name="contract"></a><span data-ttu-id="ce79d-103">Контракт</span><span class="sxs-lookup"><span data-stu-id="ce79d-103">Contract</span></span>

<span data-ttu-id="ce79d-104">Контракт</span><span class="sxs-lookup"><span data-stu-id="ce79d-104">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce79d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ce79d-105">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ce79d-106">Методы</span><span class="sxs-lookup"><span data-stu-id="ce79d-106">Methods</span></span>  

 <span data-ttu-id="ce79d-107">Класс контракта не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="ce79d-107">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ce79d-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="ce79d-108">Properties</span></span>  

 <span data-ttu-id="ce79d-109">Класс контракта имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="ce79d-109">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="ce79d-110">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="ce79d-110">AppDomainId</span></span>  

 <span data-ttu-id="ce79d-111">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="ce79d-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="ce79d-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-113">Идентификатор домена приложения, который размещает контракт.</span><span class="sxs-lookup"><span data-stu-id="ce79d-113">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="ce79d-114">Расширения функциональности</span><span class="sxs-lookup"><span data-stu-id="ce79d-114">Behaviors</span></span>  

 <span data-ttu-id="ce79d-115">Тип данных: массив Behavior</span><span class="sxs-lookup"><span data-stu-id="ce79d-115">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="ce79d-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-117">Поведения, связанные с этим контрактом.</span><span class="sxs-lookup"><span data-stu-id="ce79d-117">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ce79d-118">Имя</span><span class="sxs-lookup"><span data-stu-id="ce79d-118">Name</span></span>  

 <span data-ttu-id="ce79d-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="ce79d-119">Data type: string</span></span>  
  
 <span data-ttu-id="ce79d-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-121">Имя контракта в WSDL.</span><span class="sxs-lookup"><span data-stu-id="ce79d-121">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="ce79d-122">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="ce79d-122">Namespace</span></span>  

 <span data-ttu-id="ce79d-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="ce79d-123">Data type: string</span></span>  
  
 <span data-ttu-id="ce79d-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-125">Пространство имен элемента `portType` в WSDL.</span><span class="sxs-lookup"><span data-stu-id="ce79d-125">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="ce79d-126">Операции</span><span class="sxs-lookup"><span data-stu-id="ce79d-126">Operations</span></span>  

 <span data-ttu-id="ce79d-127">Тип данных: массив Operation</span><span class="sxs-lookup"><span data-stu-id="ce79d-127">Data type: Operation array</span></span>  
  
 <span data-ttu-id="ce79d-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-129">Операции данного контракта.</span><span class="sxs-lookup"><span data-stu-id="ce79d-129">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="ce79d-130">ProcessId</span><span class="sxs-lookup"><span data-stu-id="ce79d-130">ProcessId</span></span>  

 <span data-ttu-id="ce79d-131">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="ce79d-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="ce79d-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-133">Идентификатор процесса, который размещает контракт.</span><span class="sxs-lookup"><span data-stu-id="ce79d-133">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="ce79d-134">ref</span><span class="sxs-lookup"><span data-stu-id="ce79d-134">ref</span></span>  

 <span data-ttu-id="ce79d-135">Тип данных: Contract</span><span class="sxs-lookup"><span data-stu-id="ce79d-135">Data type: Contract</span></span>  
  
 <span data-ttu-id="ce79d-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-137">Тип обратного вызова, когда контракт является дуплексным.</span><span class="sxs-lookup"><span data-stu-id="ce79d-137">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="ce79d-138">SessionMode</span><span class="sxs-lookup"><span data-stu-id="ce79d-138">SessionMode</span></span>  

 <span data-ttu-id="ce79d-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="ce79d-139">Data type: string</span></span>  
  
 <span data-ttu-id="ce79d-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-141">Указывает, требуется ли для контракта, чтобы связанная с ним привязка использовала сеансы канала.</span><span class="sxs-lookup"><span data-stu-id="ce79d-141">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="ce79d-142">Тип</span><span class="sxs-lookup"><span data-stu-id="ce79d-142">Type</span></span>  

 <span data-ttu-id="ce79d-143">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="ce79d-143">Data type: string</span></span>  
  
 <span data-ttu-id="ce79d-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="ce79d-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce79d-145">Тип контракта.</span><span class="sxs-lookup"><span data-stu-id="ce79d-145">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce79d-146">Требования</span><span class="sxs-lookup"><span data-stu-id="ce79d-146">Requirements</span></span>  
  
|<span data-ttu-id="ce79d-147">MOF</span><span class="sxs-lookup"><span data-stu-id="ce79d-147">MOF</span></span>|<span data-ttu-id="ce79d-148">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ce79d-148">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ce79d-149">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="ce79d-149">Namespace</span></span>|<span data-ttu-id="ce79d-150">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="ce79d-150">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce79d-151">См. также</span><span class="sxs-lookup"><span data-stu-id="ce79d-151">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
