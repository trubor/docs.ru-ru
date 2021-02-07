---
description: 'Дополнительные сведения: Инициализация экземпляров'
title: Инициализация создания экземпляров
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 056f867012667abaf046827a7c6295f83d4794f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726524"
---
# <a name="instancing-initialization"></a><span data-ttu-id="d50b1-103">Инициализация создания экземпляров</span><span class="sxs-lookup"><span data-stu-id="d50b1-103">Instancing Initialization</span></span>

<span data-ttu-id="d50b1-104">Этот пример расширяет пример использования [пулов](pooling.md) путем определения интерфейса, `IObjectControl` который настраивает инициализацию объекта путем его активации и деактивации.</span><span class="sxs-lookup"><span data-stu-id="d50b1-104">This sample extends the [Pooling](pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="d50b1-105">Клиент вызывает методы, которые возвращают объект в пул и не возвращают объект в пул.</span><span class="sxs-lookup"><span data-stu-id="d50b1-105">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d50b1-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="d50b1-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="d50b1-107">Точки расширяемости</span><span class="sxs-lookup"><span data-stu-id="d50b1-107">Extensibility Points</span></span>  

 <span data-ttu-id="d50b1-108">Первым шагом в создании расширения Windows Communication Foundation (WCF) является выбор точки расширения для использования.</span><span class="sxs-lookup"><span data-stu-id="d50b1-108">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="d50b1-109">В WCF термин *EndpointDispatcher* относится к компоненту времени выполнения, отвечающему за преобразование входящих сообщений в вызовы методов в службе пользователя и преобразование возвращаемых значений из этого метода в исходящее сообщение.</span><span class="sxs-lookup"><span data-stu-id="d50b1-109">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="d50b1-110">Служба WCF создает EndpointDispatcher для каждой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="d50b1-110">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="d50b1-111">EndpointDispatcher реализует расширяемость области конечной точки (для всех сообщений, получаемых и отправляемых службой) с помощью класса <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-111">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="d50b1-112">Этот класс позволяет настраивать различные свойства, управляющие поведением EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="d50b1-112">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="d50b1-113">В этом образце рассматривается свойство <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, которое указывает на объект, предоставляющий экземпляры класса службы.</span><span class="sxs-lookup"><span data-stu-id="d50b1-113">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="d50b1-114">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="d50b1-114">IInstanceProvider</span></span>  

 <span data-ttu-id="d50b1-115">В WCF EndpointDispatcher создает экземпляры класса службы с помощью поставщика экземпляров, реализующего <xref:System.ServiceModel.Dispatcher.IInstanceProvider> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d50b1-115">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="d50b1-116">У этого интерфейса есть только два метода.</span><span class="sxs-lookup"><span data-stu-id="d50b1-116">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="d50b1-117"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>. Когда прибывает сообщение, объект Dispatcher вызывает метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, чтобы создать экземпляр класса службы для обработки сообщения.</span><span class="sxs-lookup"><span data-stu-id="d50b1-117"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="d50b1-118">Частота вызовов этого метода определяется свойством <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-118">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="d50b1-119">Например, если свойство <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> имеет значение <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, для обработки каждого получаемого сообщения создается новый экземпляр класса службы, поэтому метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> вызывается каждый раз, когда приходит сообщение.</span><span class="sxs-lookup"><span data-stu-id="d50b1-119">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="d50b1-120"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>. Когда экземпляр службы завершает обработку сообщения, EndpointDispatcher вызывает метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-120"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="d50b1-121">Как и в случае метода <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, частота вызовов этого метода определяется свойством <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-121">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="d50b1-122">Пул объектов</span><span class="sxs-lookup"><span data-stu-id="d50b1-122">The Object Pool</span></span>  

 <span data-ttu-id="d50b1-123">Класс `ObjectPoolInstanceProvider` содержит реализацию пула объектов.</span><span class="sxs-lookup"><span data-stu-id="d50b1-123">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="d50b1-124">Этот класс реализует интерфейс <xref:System.ServiceModel.Dispatcher.IInstanceProvider> для взаимодействия с уровнем модели службы.</span><span class="sxs-lookup"><span data-stu-id="d50b1-124">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="d50b1-125">Когда EndpointDispatcher вызывает метод <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>, вместо создания нового экземпляра, пользовательская реализация находит существующий объект в находящемся в памяти пуле.</span><span class="sxs-lookup"><span data-stu-id="d50b1-125">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="d50b1-126">Если такой объект доступен, метод возвращает его.</span><span class="sxs-lookup"><span data-stu-id="d50b1-126">If one is available, it is returned.</span></span> <span data-ttu-id="d50b1-127">В противном случае `ObjectPoolInstanceProvider` проверяет, не достигло ли свойство `ActiveObjectsCount` (количество возвращенных из пула объектов) максимального размера пула.</span><span class="sxs-lookup"><span data-stu-id="d50b1-127">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="d50b1-128">Если нет, то создается и возвращается вызывающей стороне новый экземпляр, а значение `ActiveObjectsCount` увеличивается на единицу.</span><span class="sxs-lookup"><span data-stu-id="d50b1-128">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="d50b1-129">В противном случае запрос на создание объекта помещается в очередь на заданное время.</span><span class="sxs-lookup"><span data-stu-id="d50b1-129">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="d50b1-130">Реализация метода `GetObjectFromThePool` показана в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="d50b1-130">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="d50b1-131">Пользовательская реализация `ReleaseInstance` добавляет освободившийся экземпляр обратно в пул и уменьшает значение `ActiveObjectsCount` на единицу.</span><span class="sxs-lookup"><span data-stu-id="d50b1-131">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="d50b1-132">EndpointDispatcher может вызывать эти методы из различных потоков, поэтому требуется синхронизированный доступ к членам уровня класса в классе `ObjectPoolInstanceProvider`.</span><span class="sxs-lookup"><span data-stu-id="d50b1-132">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="d50b1-133">`ReleaseInstance`Метод предоставляет функцию *инициализации очистки* .</span><span class="sxs-lookup"><span data-stu-id="d50b1-133">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="d50b1-134">Обычно пул поддерживает минимальное число объектов в течение времени существования пула.</span><span class="sxs-lookup"><span data-stu-id="d50b1-134">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="d50b1-135">Однако возможны периоды интенсивного использования, когда требуется создавать в пуле дополнительные объекты, пока не будет достигнуто заданное в конфигурации максимальное значение.</span><span class="sxs-lookup"><span data-stu-id="d50b1-135">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="d50b1-136">В конце концов, когда активность пула снизится, эти дополнительные объекты могут стать излишней нагрузкой.</span><span class="sxs-lookup"><span data-stu-id="d50b1-136">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="d50b1-137">Поэтому когда значение `activeObjectsCount` достигает нуля, запускается таймер бездействия, по истечении времени ожидания которого выполняется цикл очистки.</span><span class="sxs-lookup"><span data-stu-id="d50b1-137">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="d50b1-138">Расширения уровня ServiceModel выполняются с помощью следующих поведений.</span><span class="sxs-lookup"><span data-stu-id="d50b1-138">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="d50b1-139">Поведения служб. Позволяют настраивать всю среду выполнения службы.</span><span class="sxs-lookup"><span data-stu-id="d50b1-139">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="d50b1-140">Поведения конечных точек. Позволяют настраивать отдельные конечные точки, включая EndpointDispatcher.</span><span class="sxs-lookup"><span data-stu-id="d50b1-140">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="d50b1-141">Поведения контрактов. Позволяют настраивать классы <xref:System.ServiceModel.Dispatcher.ClientRuntime> или <xref:System.ServiceModel.Dispatcher.DispatchRuntime> на стороне клиента или службы соответственно.</span><span class="sxs-lookup"><span data-stu-id="d50b1-141">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="d50b1-142">Поведения операций. Позволяют настраивать классы <xref:System.ServiceModel.Dispatcher.ClientOperation> или <xref:System.ServiceModel.Dispatcher.DispatchOperation> на стороне клиента или службы соответственно.</span><span class="sxs-lookup"><span data-stu-id="d50b1-142">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="d50b1-143">С целью реализации расширения создания пулов объектов может быть создано поведение конечной точки или поведение службы.</span><span class="sxs-lookup"><span data-stu-id="d50b1-143">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="d50b1-144">В этом примере используется поведение службы, которое применяет поддержку создания пулов объектов ко всем конечным точкам службы.</span><span class="sxs-lookup"><span data-stu-id="d50b1-144">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="d50b1-145">Поведения служб создаются путем реализации интерфейса <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-145">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="d50b1-146">Имеется несколько способов сообщить ServiceModel о пользовательских поведениях:</span><span class="sxs-lookup"><span data-stu-id="d50b1-146">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="d50b1-147">с помощью пользовательского атрибута;</span><span class="sxs-lookup"><span data-stu-id="d50b1-147">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="d50b1-148">путем ее императивного добавления в коллекцию поведений описания службы;</span><span class="sxs-lookup"><span data-stu-id="d50b1-148">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="d50b1-149">путем расширения файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d50b1-149">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="d50b1-150">В этом образце используется пользовательский атрибут.</span><span class="sxs-lookup"><span data-stu-id="d50b1-150">This sample uses a custom attribute.</span></span> <span data-ttu-id="d50b1-151">При создании <xref:System.ServiceModel.ServiceHost> проверяются атрибуты, используемые в определении типа службы, а в коллекцию поведений описания службы добавляются доступные поведения.</span><span class="sxs-lookup"><span data-stu-id="d50b1-151">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="d50b1-152"><xref:System.ServiceModel.Description.IServiceBehavior>Интерфейс имеет три метода: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` и <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> .</span><span class="sxs-lookup"><span data-stu-id="d50b1-152">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="d50b1-153">Эти методы вызываются WCF при <xref:System.ServiceModel.ServiceHost> инициализации.</span><span class="sxs-lookup"><span data-stu-id="d50b1-153">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="d50b1-154">Сначала вызывается метод <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>, который позволяет проверить согласованность службы.</span><span class="sxs-lookup"><span data-stu-id="d50b1-154"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="d50b1-155">Затем вызывается метод <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>, который используется только в очень сложных сценариях.</span><span class="sxs-lookup"><span data-stu-id="d50b1-155"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="d50b1-156">Метод <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> вызывается в последнюю очередь и отвечает за настройку среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="d50b1-156"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="d50b1-157">Следующие параметры передаются методу <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-157">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="d50b1-158">`Description`: этот параметр содержит описание службы для всей службы.</span><span class="sxs-lookup"><span data-stu-id="d50b1-158">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="d50b1-159">Его можно использовать для проверки данных описания о конечных точках, контрактах и привязках службы, а также других связанных со службой данных.</span><span class="sxs-lookup"><span data-stu-id="d50b1-159">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="d50b1-160">`ServiceHostBase`: этот параметр содержит инициализируемый в данный момент объект <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-160">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="d50b1-161">В пользовательской реализации <xref:System.ServiceModel.Description.IServiceBehavior> создается новый экземпляр `ObjectPoolInstanceProvider`, который присваивается свойству <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> в каждом объекте <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>, прикрепленном к <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-161">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}
```  
  
 <span data-ttu-id="d50b1-162">Помимо реализации интерфейса <xref:System.ServiceModel.Description.IServiceBehavior> у класса `ObjectPoolingAttribute` имеется несколько членов для настройки пула объектов с помощью аргументов атрибута.</span><span class="sxs-lookup"><span data-stu-id="d50b1-162">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="d50b1-163">К этим членам относятся `MaxSize`, `MinSize`, `Enabled` и `CreationTimeout`, и они должны соответствовать набору возможностей пула, предоставляемому службами .NET Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="d50b1-163">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="d50b1-164">Поведение пула объектов теперь можно добавить в службу WCF, заменив в реализации службы только что созданный настраиваемый `ObjectPooling` атрибут.</span><span class="sxs-lookup"><span data-stu-id="d50b1-164">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="d50b1-165">Активация и деактивация связывания</span><span class="sxs-lookup"><span data-stu-id="d50b1-165">Hooking Activation and Deactivation</span></span>  

 <span data-ttu-id="d50b1-166">Основной целью создания пулов объектов является оптимизация использования объектов с небольшим временем существования, чтобы экономить на ресурсоемких процедурах создания и инициализации.</span><span class="sxs-lookup"><span data-stu-id="d50b1-166">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="d50b1-167">Поэтому создание пулов при его правильном использовании позволяет значительно повысить производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="d50b1-167">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="d50b1-168">Поскольку объект возвращается из пула, конструктор вызывается только один раз.</span><span class="sxs-lookup"><span data-stu-id="d50b1-168">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="d50b1-169">Однако некоторым приложениями требуется более высокий уровень контроля, чтобы они могли инициализировать и высвобождать ресурсы в рамках одного контекста.</span><span class="sxs-lookup"><span data-stu-id="d50b1-169">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="d50b1-170">Например, объект, используемый для набора вычислений, может сбрасывать значения своих закрытых полей, прежде чем переходить к следующим вычислениям.</span><span class="sxs-lookup"><span data-stu-id="d50b1-170">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="d50b1-171">Службы Enterprise Services поддерживают такую инициализацию в зависимости от контекста, позволяя разработчику объектов переопределять методы `Activate` и `Deactivate` из базового класса <xref:System.EnterpriseServices.ServicedComponent>.</span><span class="sxs-lookup"><span data-stu-id="d50b1-171">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="d50b1-172">Пул объектов вызывает метод `Activate` непосредственно перед возвращением объекта из пула.</span><span class="sxs-lookup"><span data-stu-id="d50b1-172">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="d50b1-173">Метод `Deactivate` вызывается при возвращении объекта в пул.</span><span class="sxs-lookup"><span data-stu-id="d50b1-173">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="d50b1-174">Кроме того, у базового класса <xref:System.EnterpriseServices.ServicedComponent> имеется свойство типа `boolean` с именем `CanBePooled`, с помощью которого можно уведомить пул о том, можно ли и дальше размещать объект в пуле.</span><span class="sxs-lookup"><span data-stu-id="d50b1-174">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="d50b1-175">Чтобы сымитировать эту функциональность, в этом образце объявляется открытый интерфейс (`IObjectControl`), имеющий указанные выше члены.</span><span class="sxs-lookup"><span data-stu-id="d50b1-175">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="d50b1-176">Затем этот интерфейс реализуется классами службы, предназначенными для инициализации с учетом контекста.</span><span class="sxs-lookup"><span data-stu-id="d50b1-176">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="d50b1-177">Реализацию <xref:System.ServiceModel.Dispatcher.IInstanceProvider> необходимо изменить, чтобы она удовлетворяла этим требованиям.</span><span class="sxs-lookup"><span data-stu-id="d50b1-177">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="d50b1-178">Теперь каждый раз, когда вы получаете объект путем вызова `GetInstance` метода, необходимо проверить, реализует ли объект `IObjectControl.` метод, если он это делает, то необходимо вызвать его `Activate` соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="d50b1-178">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="d50b1-179">При возврате объекта в пул необходимо проверить свойство `CanBePooled`, прежде чем добавлять объект обратно в пул.</span><span class="sxs-lookup"><span data-stu-id="d50b1-179">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="d50b1-180">Поскольку разработчик может решать, можно ли помещать объект в пул, в определенный момент значение счетчика объектов в пуле может оказаться меньше минимального размера пула.</span><span class="sxs-lookup"><span data-stu-id="d50b1-180">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="d50b1-181">Поэтому необходимо сравнивать число объектов с минимальным размером и при необходимости выполнять инициализацию в процедуре очистки.</span><span class="sxs-lookup"><span data-stu-id="d50b1-181">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="d50b1-182">При запуске данного примера запросы и ответы операций отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="d50b1-182">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="d50b1-183">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="d50b1-183">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d50b1-184">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="d50b1-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d50b1-185">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d50b1-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d50b1-186">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d50b1-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d50b1-187">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d50b1-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d50b1-188">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d50b1-188">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d50b1-189">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="d50b1-189">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d50b1-190">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="d50b1-190">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d50b1-191">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="d50b1-191">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
