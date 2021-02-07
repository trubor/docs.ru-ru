---
description: 'Дополнительные сведения о: Каллбаккбехавиор'
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: fa9e403324afe818e247d1f751cce0ce7d5a6fb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757765"
---
# <a name="callbackbehavior"></a><span data-ttu-id="4c2fa-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="4c2fa-103">CallbackBehavior</span></span>

<span data-ttu-id="4c2fa-104">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="4c2fa-104">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c2fa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c2fa-105">Syntax</span></span>  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4c2fa-106">Методы</span><span class="sxs-lookup"><span data-stu-id="4c2fa-106">Methods</span></span>  

 <span data-ttu-id="4c2fa-107">Класс CallbackBehavior не определяет никакие методы.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-107">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4c2fa-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="4c2fa-108">Properties</span></span>  

 <span data-ttu-id="4c2fa-109">Класс CallbackBehavior имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-109">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="4c2fa-110">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="4c2fa-110">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="4c2fa-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="4c2fa-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="4c2fa-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="4c2fa-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c2fa-113">Если сеанс имеет значение true, он автоматически закрывается при закрытии службой дуплексного сеанса.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-113">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="4c2fa-114">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="4c2fa-114">ConcurrencyMode</span></span>  

 <span data-ttu-id="4c2fa-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="4c2fa-115">Data type: string</span></span>  
<span data-ttu-id="4c2fa-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="4c2fa-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c2fa-117">Указывает, поддерживает служба один поток, несколько потоков или повторные входящие вызовы.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-117">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="4c2fa-118">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="4c2fa-118">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="4c2fa-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="4c2fa-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="4c2fa-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="4c2fa-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c2fa-121">Значение, указывающее, требуется ли передать неизвестные данные сериализации по сети.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-121">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="4c2fa-122">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="4c2fa-122">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="4c2fa-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="4c2fa-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="4c2fa-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="4c2fa-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c2fa-125">Если это свойство включено, подробная информация об исключениях в обратном вызове прикрепляется к ошибкам, возвращаемым в службу.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-125">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="4c2fa-126">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="4c2fa-126">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="4c2fa-127">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="4c2fa-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="4c2fa-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="4c2fa-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c2fa-129">Максимальное количество элементов, допустимое в сериализованном объекте.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-129">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="4c2fa-130">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="4c2fa-130">UseSynchronizationContext</span></span>  

 <span data-ttu-id="4c2fa-131">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="4c2fa-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="4c2fa-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="4c2fa-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c2fa-133">Указывает, использовать ли текущий контекст синхронизации для выбора потока выполнения.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-133">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="4c2fa-134">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="4c2fa-134">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="4c2fa-135">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="4c2fa-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="4c2fa-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="4c2fa-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c2fa-137">Указывает, кем выполняется принудительная обработка заголовка SOAP MustUnderstand: системой или приложением.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-137">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c2fa-138">Требования</span><span class="sxs-lookup"><span data-stu-id="4c2fa-138">Requirements</span></span>  
  
|<span data-ttu-id="4c2fa-139">MOF</span><span class="sxs-lookup"><span data-stu-id="4c2fa-139">MOF</span></span>|<span data-ttu-id="4c2fa-140">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-140">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4c2fa-141">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="4c2fa-141">Namespace</span></span>|<span data-ttu-id="4c2fa-142">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="4c2fa-142">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c2fa-143">См. также</span><span class="sxs-lookup"><span data-stu-id="4c2fa-143">See also</span></span>

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
