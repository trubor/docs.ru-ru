---
description: 'Дополнительные сведения о: объединение в пул'
title: Pooling
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: cb770b60a3011f95df5a2fdecea6cdc66b64710f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703852"
---
# <a name="pooling"></a><span data-ttu-id="5564d-103">Pooling</span><span class="sxs-lookup"><span data-stu-id="5564d-103">Pooling</span></span>

<span data-ttu-id="5564d-104">В этом примере показано, как расширить Windows Communication Foundation (WCF) для поддержки пула объектов.</span><span class="sxs-lookup"><span data-stu-id="5564d-104">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="5564d-105">Этот образец демонстрирует, как создать атрибут, синтаксически и семантически аналогичный функциям атрибута `ObjectPoolingAttribute` служб Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="5564d-105">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="5564d-106">Использование пулов объектов может значительно повысить производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="5564d-106">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="5564d-107">Однако при неправильном использовании эффект может быть противоположным.</span><span class="sxs-lookup"><span data-stu-id="5564d-107">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="5564d-108">Использование пулов объектов позволяет снизить накладные расходы на повторное создание часто используемых объектов, требующих большого объема инициализации.</span><span class="sxs-lookup"><span data-stu-id="5564d-108">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="5564d-109">Однако если завершение вызова метода для объекта из пула занимает много времени, сразу после достижения максимального размера пула функция пулов объектов ставит дополнительные запросы в очередь.</span><span class="sxs-lookup"><span data-stu-id="5564d-109">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="5564d-110">В результате возможен сбой обслуживания запросов создания некоторых объектов из-за возникновения исключения времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="5564d-110">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5564d-111">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="5564d-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5564d-112">Первым шагом в создании расширения WCF является выбор точки расширения для использования.</span><span class="sxs-lookup"><span data-stu-id="5564d-112">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="5564d-113">В WCF термин *Dispatcher* относится к компоненту времени выполнения, который отвечает за преобразование входящих сообщений в вызовы методов в службе пользователя и преобразование возвращаемых значений из этого метода в исходящее сообщение.</span><span class="sxs-lookup"><span data-stu-id="5564d-113">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="5564d-114">Служба WCF создает диспетчер для каждой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="5564d-114">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="5564d-115">Клиент WCF должен использовать Dispatcher, если контракт, связанный с этим клиентом, является дуплексным контрактом.</span><span class="sxs-lookup"><span data-stu-id="5564d-115">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="5564d-116">Диспетчеры каналов и конечных точек обеспечивают расширяемость на уровне канала и контракта, предоставляя различные свойства, которые управляют поведением диспетчера.</span><span class="sxs-lookup"><span data-stu-id="5564d-116">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="5564d-117">Свойство <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> также позволяет контролировать, изменять или настраивать диспетчерский процесс.</span><span class="sxs-lookup"><span data-stu-id="5564d-117">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="5564d-118">В этом образце рассматривается свойство <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, которое указывает на объект, предоставляющий экземпляры класса службы.</span><span class="sxs-lookup"><span data-stu-id="5564d-118">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="5564d-119">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="5564d-119">The IInstanceProvider</span></span>  

 <span data-ttu-id="5564d-120">В WCF диспетчер создает экземпляры класса службы с помощью <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> , который реализует <xref:System.ServiceModel.Dispatcher.IInstanceProvider> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="5564d-120">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="5564d-121">У этого интерфейса есть три метода.</span><span class="sxs-lookup"><span data-stu-id="5564d-121">This interface has three methods:</span></span>  
  
- <span data-ttu-id="5564d-122"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>. Когда прибывает сообщение, объект Dispatcher вызывает метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, чтобы создать экземпляр класса службы для обработки сообщения.</span><span class="sxs-lookup"><span data-stu-id="5564d-122"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="5564d-123">Частота вызовов этого метода определяется свойством <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="5564d-123">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="5564d-124">Например, если свойство <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> имеет значение <xref:System.ServiceModel.InstanceContextMode.PerCall>, для обработки каждого получаемого сообщения создается новый экземпляр класса службы, поэтому метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> вызывается каждый раз, когда приходит сообщение.</span><span class="sxs-lookup"><span data-stu-id="5564d-124">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="5564d-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>. Этот метод идентичен предыдущему методу, за исключением того, что он вызывается при отсутствии аргумента Message.</span><span class="sxs-lookup"><span data-stu-id="5564d-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="5564d-126"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>. Когда истекает время существования службы, Dispatcher вызывает метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="5564d-126"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="5564d-127">Как и в случае метода <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, частота вызовов этого метода определяется свойством <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="5564d-127">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="5564d-128">Пул объектов</span><span class="sxs-lookup"><span data-stu-id="5564d-128">The Object Pool</span></span>  

 <span data-ttu-id="5564d-129">Пользовательская реализация <xref:System.ServiceModel.Dispatcher.IInstanceProvider> обеспечивает необходимую семантику пула объектов для службы.</span><span class="sxs-lookup"><span data-stu-id="5564d-129">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="5564d-130">Поэтому в образце имеется тип `ObjectPoolingInstanceProvider`, который предоставляет пользовательскую реализацию интерфейса <xref:System.ServiceModel.Dispatcher.IInstanceProvider> для создания пула.</span><span class="sxs-lookup"><span data-stu-id="5564d-130">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="5564d-131">Когда `Dispatcher` вызывает метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>, пользовательская реализация вместо создания нового экземпляра ищет существующий объект в находящемся в памяти пуле.</span><span class="sxs-lookup"><span data-stu-id="5564d-131">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="5564d-132">Если такой объект доступен, метод возвращает его.</span><span class="sxs-lookup"><span data-stu-id="5564d-132">If one is available, it is returned.</span></span> <span data-ttu-id="5564d-133">В противном случае создается новый объект.</span><span class="sxs-lookup"><span data-stu-id="5564d-133">Otherwise, a new object is created.</span></span> <span data-ttu-id="5564d-134">Реализация метода `GetInstance` показана в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="5564d-134">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;
}  
```  
  
 <span data-ttu-id="5564d-135">Пользовательская реализация `ReleaseInstance` добавляет освободившийся экземпляр обратно в пул и уменьшает значение `ActiveObjectsCount` на единицу.</span><span class="sxs-lookup"><span data-stu-id="5564d-135">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="5564d-136">`Dispatcher` может вызывать эти методы из различных потоков, поэтому требуется синхронизированный доступ к членам уровня класса в классе `ObjectPoolingInstanceProvider`.</span><span class="sxs-lookup"><span data-stu-id="5564d-136">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();
    }  
}  
```  
  
 <span data-ttu-id="5564d-137">`ReleaseInstance`Метод предоставляет функцию "очистить инициализацию".</span><span class="sxs-lookup"><span data-stu-id="5564d-137">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="5564d-138">Обычно пул поддерживает минимальное число объектов в течение времени существования пула.</span><span class="sxs-lookup"><span data-stu-id="5564d-138">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="5564d-139">Однако возможны периоды интенсивного использования, когда требуется создавать в пуле дополнительные объекты, пока не будет достигнуто заданное в конфигурации максимальное значение.</span><span class="sxs-lookup"><span data-stu-id="5564d-139">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="5564d-140">В конце концов, когда активность пула снизится, эти дополнительные объекты могут стать излишней нагрузкой.</span><span class="sxs-lookup"><span data-stu-id="5564d-140">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="5564d-141">Поэтому когда значение `activeObjectsCount` достигает нуля, запускается таймер бездействия, по истечении времени ожидания которого выполняется цикл очистки.</span><span class="sxs-lookup"><span data-stu-id="5564d-141">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="5564d-142">Добавление поведения</span><span class="sxs-lookup"><span data-stu-id="5564d-142">Adding the Behavior</span></span>  

 <span data-ttu-id="5564d-143">Расширения уровня диспетчера подключаются с помощью следующих поведений.</span><span class="sxs-lookup"><span data-stu-id="5564d-143">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="5564d-144">Поведения служб.</span><span class="sxs-lookup"><span data-stu-id="5564d-144">Service Behaviors.</span></span> <span data-ttu-id="5564d-145">Позволяют настраивать всю среду выполнения службы.</span><span class="sxs-lookup"><span data-stu-id="5564d-145">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="5564d-146">Поведения конечных точек.</span><span class="sxs-lookup"><span data-stu-id="5564d-146">Endpoint Behaviors.</span></span> <span data-ttu-id="5564d-147">Позволяют настраивать конечные точки службы, включая диспетчера каналов и конечных точек.</span><span class="sxs-lookup"><span data-stu-id="5564d-147">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="5564d-148">Поведения контрактов.</span><span class="sxs-lookup"><span data-stu-id="5564d-148">Contract Behaviors.</span></span> <span data-ttu-id="5564d-149">Эти поведения позволяют настраивать классы <xref:System.ServiceModel.Dispatcher.ClientRuntime> и <xref:System.ServiceModel.Dispatcher.DispatchRuntime> в клиенте и службе соответственно.</span><span class="sxs-lookup"><span data-stu-id="5564d-149">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="5564d-150">С целью реализации расширения создания пулов объектов должно быть создано поведение службы.</span><span class="sxs-lookup"><span data-stu-id="5564d-150">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="5564d-151">Поведения служб создаются путем реализации интерфейса <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="5564d-151">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="5564d-152">Имеется несколько способов сообщить модели службы о пользовательских поведениях:</span><span class="sxs-lookup"><span data-stu-id="5564d-152">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="5564d-153">с помощью пользовательского атрибута;</span><span class="sxs-lookup"><span data-stu-id="5564d-153">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="5564d-154">путем ее императивного добавления в коллекцию поведений описания службы;</span><span class="sxs-lookup"><span data-stu-id="5564d-154">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="5564d-155">путем расширения файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5564d-155">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="5564d-156">В этом образце используется пользовательский атрибут.</span><span class="sxs-lookup"><span data-stu-id="5564d-156">This sample uses a custom attribute.</span></span> <span data-ttu-id="5564d-157">При создании <xref:System.ServiceModel.ServiceHost> проверяются атрибуты, используемые в определении типа службы, а в коллекцию поведений описания службы добавляются доступные поведения.</span><span class="sxs-lookup"><span data-stu-id="5564d-157">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="5564d-158">У интерфейса <xref:System.ServiceModel.Description.IServiceBehavior> имеется три метода — <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> и <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="5564d-158">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="5564d-159">Метод <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> используется для обеспечения того, что поведение может быть применено к службе.</span><span class="sxs-lookup"><span data-stu-id="5564d-159">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="5564d-160">В этом образце реализация обеспечивает, что служба не настраивается с <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="5564d-160">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="5564d-161">Метод <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> используется для настройки привязок службы.</span><span class="sxs-lookup"><span data-stu-id="5564d-161">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="5564d-162">Это не требуется в данном сценарии.</span><span class="sxs-lookup"><span data-stu-id="5564d-162">It is not required in this scenario.</span></span> <span data-ttu-id="5564d-163">Метод <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> используется для настройки диспетчеров службы.</span><span class="sxs-lookup"><span data-stu-id="5564d-163">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="5564d-164">Этот метод вызывается WCF при <xref:System.ServiceModel.ServiceHost> инициализации.</span><span class="sxs-lookup"><span data-stu-id="5564d-164">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="5564d-165">Этому методу передаются следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="5564d-165">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="5564d-166">`Description`: этот аргумент содержит описание службы для всей службы.</span><span class="sxs-lookup"><span data-stu-id="5564d-166">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="5564d-167">Его можно использовать для проверки данных описания о конечных точках, контрактах и привязках службы, а также других данных.</span><span class="sxs-lookup"><span data-stu-id="5564d-167">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="5564d-168">`ServiceHostBase`: этот аргумент содержит инициализируемый в данный момент объект <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="5564d-168">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="5564d-169">В пользовательской реализации <xref:System.ServiceModel.Description.IServiceBehavior> создается новый экземпляр `ObjectPoolingInstanceProvider`, который присваивается свойству <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> в каждом объекте <xref:System.ServiceModel.Dispatcher.DispatchRuntime> в ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="5564d-169">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior
    // (this.throttlingBehavior==null), it should have initialized
    // a single ServiceThrottle on all ChannelDispatchers.
    // As we loop through the ChannelDispatchers, we verify that
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all
            // endpoints. If there were others, we could not enforce
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="5564d-170">Помимо реализации интерфейса <xref:System.ServiceModel.Description.IServiceBehavior> у класса <xref:System.EnterpriseServices.ObjectPoolingAttribute> имеется несколько членов для настройки пула объектов с помощью аргументов атрибута.</span><span class="sxs-lookup"><span data-stu-id="5564d-170">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="5564d-171">К этим членам относятся <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> и <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, и они должны соответствовать набору возможностей пула, предоставляемому службами .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="5564d-171">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="5564d-172">Поведение пула объектов теперь можно добавить в службу WCF, заменив в реализации службы только что созданный настраиваемый `ObjectPooling` атрибут.</span><span class="sxs-lookup"><span data-stu-id="5564d-172">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="5564d-173">Запуск примера</span><span class="sxs-lookup"><span data-stu-id="5564d-173">Running the Sample</span></span>  

 <span data-ttu-id="5564d-174">В этом образце демонстрируются преимущества в производительности, которые могут быть получены при использовании пула объектов в различных сценариях.</span><span class="sxs-lookup"><span data-stu-id="5564d-174">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="5564d-175">Приложение службы реализует две службы - `WorkService` и `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="5564d-175">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="5564d-176">Обе службы совместно используют одну реализацию - обеим требуется обширная инициализация, а затем обе предоставляют метод `DoWork()`, требующий относительно малых затрат.</span><span class="sxs-lookup"><span data-stu-id="5564d-176">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="5564d-177">Единственное отличие заключается в том, что в службе `ObjectPooledWorkService` настроено использование пула объектов.</span><span class="sxs-lookup"><span data-stu-id="5564d-177">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }
}  
```  
  
 <span data-ttu-id="5564d-178">При выполнении клиента он измеряет время 5-кратного вызова службы `WorkService`.</span><span class="sxs-lookup"><span data-stu-id="5564d-178">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="5564d-179">Затем измеряется время 5-кратного вызова службы `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="5564d-179">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="5564d-180">Затем отображается разница во времени:</span><span class="sxs-lookup"><span data-stu-id="5564d-180">The difference in time is then displayed:</span></span>  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> <span data-ttu-id="5564d-181">При первом запуске клиента обращение к обеим службам занимает приблизительно одинаковое время.</span><span class="sxs-lookup"><span data-stu-id="5564d-181">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="5564d-182">При повторном запуске образца видно, что служба `ObjectPooledWorkService` возвращает результаты намного быстрее, потому что экземпляр этого объекта уже существует в пуле.</span><span class="sxs-lookup"><span data-stu-id="5564d-182">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5564d-183">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="5564d-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5564d-184">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5564d-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5564d-185">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5564d-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5564d-186">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5564d-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5564d-187">Если для восстановления конфигурации этого образца используется программа Svcutil.exe, измените имя конечной точки в конфигурации клиента, чтобы оно соответствовало клиентскому коду.</span><span class="sxs-lookup"><span data-stu-id="5564d-187">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5564d-188">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5564d-188">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5564d-189">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5564d-189">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5564d-190">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="5564d-190">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5564d-191">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5564d-191">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
