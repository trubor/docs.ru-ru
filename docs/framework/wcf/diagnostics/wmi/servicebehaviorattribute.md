---
description: 'Дополнительные сведения о: ServiceBehaviorAttribute'
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 57ffa9103523618db752b3be6d43bb16603d1728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715578"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="c4703-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="c4703-103">ServiceBehaviorAttribute</span></span>

<span data-ttu-id="c4703-104">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="c4703-104">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4703-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4703-105">Syntax</span></span>  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c4703-106">Методы</span><span class="sxs-lookup"><span data-stu-id="c4703-106">Methods</span></span>  

 <span data-ttu-id="c4703-107">Класс ServiceBehaviorAttribute не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="c4703-107">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c4703-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="c4703-108">Properties</span></span>  

 <span data-ttu-id="c4703-109">Класс ServiceBehaviorAttribute имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="c4703-109">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="c4703-110">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="c4703-110">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="c4703-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="c4703-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4703-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-113">Указывает, следует ли автоматически закрывать сеанс, когда клиент закрывает выходной сеанс.</span><span class="sxs-lookup"><span data-stu-id="c4703-113">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="c4703-114">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="c4703-114">ConcurrencyMode</span></span>  

 <span data-ttu-id="c4703-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c4703-115">Data type: string</span></span>  
<span data-ttu-id="c4703-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-117">Указывает, поддерживает служба один поток, несколько потоков или повторные входящие вызовы.</span><span class="sxs-lookup"><span data-stu-id="c4703-117">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="c4703-118">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="c4703-118">ConfigurationName</span></span>  

 <span data-ttu-id="c4703-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c4703-119">Data type: string</span></span>  
  
 <span data-ttu-id="c4703-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-121">Имя конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="c4703-121">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="c4703-122">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="c4703-122">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="c4703-123">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="c4703-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4703-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-125">Указывает, требуется ли передать неизвестные данные сериализации по сети.</span><span class="sxs-lookup"><span data-stu-id="c4703-125">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="c4703-126">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="c4703-126">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="c4703-127">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="c4703-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4703-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-129">Указывает, включать ли информацию об управляемых исключениях в сведения об ошибках SOAP, возвращаемые клиентам для отладки.</span><span class="sxs-lookup"><span data-stu-id="c4703-129">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="c4703-130">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="c4703-130">InstanceContextMode</span></span>  

 <span data-ttu-id="c4703-131">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c4703-131">Data type: string</span></span>  
  
 <span data-ttu-id="c4703-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-133">Указывает, когда создается новый объект службы.</span><span class="sxs-lookup"><span data-stu-id="c4703-133">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="c4703-134">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="c4703-134">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="c4703-135">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="c4703-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="c4703-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-137">Максимальное количество элементов, допустимое в сериализованном объекте.</span><span class="sxs-lookup"><span data-stu-id="c4703-137">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="c4703-138">Имя</span><span class="sxs-lookup"><span data-stu-id="c4703-138">Name</span></span>  

 <span data-ttu-id="c4703-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c4703-139">Data type: string</span></span>  
  
 <span data-ttu-id="c4703-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-141">Имя атрибута службы в WSDL.</span><span class="sxs-lookup"><span data-stu-id="c4703-141">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="c4703-142">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="c4703-142">Namespace</span></span>  

 <span data-ttu-id="c4703-143">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c4703-143">Data type: string</span></span>  
  
 <span data-ttu-id="c4703-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-145">Целевое пространство имен службы в WSDL.</span><span class="sxs-lookup"><span data-stu-id="c4703-145">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="c4703-146">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="c4703-146">ReleaseServiceInstanceOnTransactionComplete</span></span>  

 <span data-ttu-id="c4703-147">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="c4703-147">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4703-148">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-149">Указывает, производится ли повторное использование объекта службы после завершения текущей транзакции.</span><span class="sxs-lookup"><span data-stu-id="c4703-149">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="c4703-150">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="c4703-150">TransactionAutoCompleteOnSessionClose</span></span>  

 <span data-ttu-id="c4703-151">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="c4703-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4703-152">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-153">Указывает, завершаются ли ожидающие транзакции при закрытии текущего сеанса.</span><span class="sxs-lookup"><span data-stu-id="c4703-153">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="c4703-154">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="c4703-154">TransactionIsolationLevel</span></span>  

 <span data-ttu-id="c4703-155">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="c4703-155">Data type: string</span></span>  
  
 <span data-ttu-id="c4703-156">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-157">Указывает уровень изоляции транзакции.</span><span class="sxs-lookup"><span data-stu-id="c4703-157">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="c4703-158">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="c4703-158">TransactionTimeout</span></span>  

 <span data-ttu-id="c4703-159">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="c4703-159">Data type: datetime</span></span>  
  
 <span data-ttu-id="c4703-160">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-161">Период времени, в течение которого транзакция должна быть завершена.</span><span class="sxs-lookup"><span data-stu-id="c4703-161">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="c4703-162">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="c4703-162">UseSynchronizationContext</span></span>  

 <span data-ttu-id="c4703-163">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="c4703-163">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4703-164">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-164">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-165">Указывает, использовать ли текущий контекст синхронизации для выбора потока выполнения.</span><span class="sxs-lookup"><span data-stu-id="c4703-165">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="c4703-166">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="c4703-166">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="c4703-167">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="c4703-167">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4703-168">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c4703-168">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4703-169">Указывает, кем выполняется принудительная обработка заголовка SOAP MustUnderstand: системой или приложением.</span><span class="sxs-lookup"><span data-stu-id="c4703-169">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4703-170">Требования</span><span class="sxs-lookup"><span data-stu-id="c4703-170">Requirements</span></span>  
  
|<span data-ttu-id="c4703-171">MOF</span><span class="sxs-lookup"><span data-stu-id="c4703-171">MOF</span></span>|<span data-ttu-id="c4703-172">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c4703-172">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c4703-173">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="c4703-173">Namespace</span></span>|<span data-ttu-id="c4703-174">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="c4703-174">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4703-175">См. также</span><span class="sxs-lookup"><span data-stu-id="c4703-175">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
