---
description: 'Дополнительные сведения: настраиваемое время существования'
title: Настраиваемое время существования
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 24845aaa20e60f92e2add568c81ab3d6502ebedf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732479"
---
# <a name="custom-lifetime"></a><span data-ttu-id="423c2-103">Настраиваемое время существования</span><span class="sxs-lookup"><span data-stu-id="423c2-103">Custom lifetime</span></span>

<span data-ttu-id="423c2-104">В этом примере демонстрируется написание расширения Windows Communication Foundation (WCF) для предоставления служб времени жизни для общих экземпляров службы WCF.</span><span class="sxs-lookup"><span data-stu-id="423c2-104">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="423c2-105">Процедура настройки и инструкции по построению для данного примера приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="423c2-105">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="423c2-106">Общий создание экземпляров</span><span class="sxs-lookup"><span data-stu-id="423c2-106">Shared instancing</span></span>

<span data-ttu-id="423c2-107">WCF предлагает несколько режимов создания экземпляров для экземпляров службы.</span><span class="sxs-lookup"><span data-stu-id="423c2-107">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="423c2-108">Режим совместного создания экземпляров, описанный в этой статье, предоставляет способ совместного использования экземпляра службы несколькими каналами.</span><span class="sxs-lookup"><span data-stu-id="423c2-108">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="423c2-109">Клиенты могут обратиться к методу фабрики в службе и создать новый канал для запуска обмена данными.</span><span class="sxs-lookup"><span data-stu-id="423c2-109">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="423c2-110">В следующем фрагменте кода показано, как клиентское приложение создает новый канал для существующего экземпляра службы:</span><span class="sxs-lookup"><span data-stu-id="423c2-110">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="423c2-111">В отличие от других режимов создания экземпляров, режим создания общих экземпляров располагает уникальным способом освобождения экземпляров служб.</span><span class="sxs-lookup"><span data-stu-id="423c2-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="423c2-112">По умолчанию, когда все каналы закрыты для <xref:System.ServiceModel.InstanceContext> , среда выполнения службы WCF проверяет <xref:System.ServiceModel.InstanceContextMode> , настроена ли служба для <xref:System.ServiceModel.InstanceContextMode.PerCall> или <xref:System.ServiceModel.InstanceContextMode.PerSession> , и, если это так, освобождает экземпляр и заявляет ресурсы.</span><span class="sxs-lookup"><span data-stu-id="423c2-112">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="423c2-113">Если используется настраиваемый объект <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> , WCF вызывает <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> метод реализации поставщика перед освобождением экземпляра.</span><span class="sxs-lookup"><span data-stu-id="423c2-113">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="423c2-114"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `true` Значение, если метод возвращает экземпляр, в противном случае <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Реализация отвечает за уведомление о `Dispatcher` состоянии простоя с помощью метода обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="423c2-114">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="423c2-115">Это делается путем вызова <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> метода поставщика.</span><span class="sxs-lookup"><span data-stu-id="423c2-115">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="423c2-116">В этом образце показано, как можно отложить освобождение <xref:System.ServiceModel.InstanceContext> с временем ожидания простоя 20 секунд.</span><span class="sxs-lookup"><span data-stu-id="423c2-116">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="423c2-117">Расширение InstanceContext</span><span class="sxs-lookup"><span data-stu-id="423c2-117">Extending the InstanceContext</span></span>

<span data-ttu-id="423c2-118">В WCF <xref:System.ServiceModel.InstanceContext> — это связь между экземпляром службы и `Dispatcher` .</span><span class="sxs-lookup"><span data-stu-id="423c2-118">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="423c2-119">WCF позволяет расширить этот компонент среды выполнения, добавив новое состояние или поведение, используя его расширяемый шаблон объектов.</span><span class="sxs-lookup"><span data-stu-id="423c2-119">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="423c2-120">Шаблон расширяемого объекта используется в WCF для расширения существующих классов среды выполнения с новыми функциональными возможностями или для добавления новых функций состояния в объект.</span><span class="sxs-lookup"><span data-stu-id="423c2-120">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="423c2-121">Предусмотрено три интерфейса в шаблоне расширяемого объекта: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601> и <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="423c2-121">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="423c2-122"><xref:System.ServiceModel.IExtensibleObject%601>Интерфейс реализуется объектами, чтобы разрешить расширения, которые настраивают их функциональность.</span><span class="sxs-lookup"><span data-stu-id="423c2-122">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="423c2-123">Интерфейс <xref:System.ServiceModel.IExtension%601> реализуется объектами, которые могут быть расширениями классов типа `T`.</span><span class="sxs-lookup"><span data-stu-id="423c2-123">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="423c2-124">И, наконец, <xref:System.ServiceModel.IExtensionCollection%601> интерфейс представляет собой коллекцию <xref:System.ServiceModel.IExtension%601> реализаций, которые позволяют получить реализацию <xref:System.ServiceModel.IExtension%601> по типу.</span><span class="sxs-lookup"><span data-stu-id="423c2-124">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="423c2-125">Таким образом, для расширения необходимо <xref:System.ServiceModel.InstanceContext> реализовать <xref:System.ServiceModel.IExtension%601> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="423c2-125">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="423c2-126">В этом примере проекта `CustomLeaseExtension` класс содержит эту реализацию.</span><span class="sxs-lookup"><span data-stu-id="423c2-126">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="423c2-127">У интерфейса <xref:System.ServiceModel.IExtension%601> имеется два метода: <xref:System.ServiceModel.IExtension%601.Attach%2A> и <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="423c2-127">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="423c2-128">Как видно по их именам, два этих метода вызываются, когда среда выполнения присоединяет и отсоединяет расширение экземпляра класса <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="423c2-128">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="423c2-129">В этом образце метод `Attach` используется для отслеживания объекта <xref:System.ServiceModel.InstanceContext>, который принадлежит текущему экземпляру расширения.</span><span class="sxs-lookup"><span data-stu-id="423c2-129">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="423c2-130">Кроме того, в расширение необходимо добавить требуемую реализацию, чтобы обеспечить поддержку продленного времени существования.</span><span class="sxs-lookup"><span data-stu-id="423c2-130">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="423c2-131">Поэтому `ICustomLease` интерфейс объявляется с нужными методами и реализуется в `CustomLeaseExtension` классе.</span><span class="sxs-lookup"><span data-stu-id="423c2-131">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="423c2-132">Когда WCF вызывает <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> метод в <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> реализации, этот вызов направляется к <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> методу класса `CustomLeaseExtension` .</span><span class="sxs-lookup"><span data-stu-id="423c2-132">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="423c2-133">Затем `CustomLeaseExtension` проверяется его закрытое состояние, чтобы узнать, <xref:System.ServiceModel.InstanceContext> не простаивает ли.</span><span class="sxs-lookup"><span data-stu-id="423c2-133">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="423c2-134">Если он бездействует, возвращается значение `true` .</span><span class="sxs-lookup"><span data-stu-id="423c2-134">If it is idle, it returns `true`.</span></span> <span data-ttu-id="423c2-135">В противном случае запускается таймер на указанное продленное время существования.</span><span class="sxs-lookup"><span data-stu-id="423c2-135">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

<span data-ttu-id="423c2-136">В `Elapsed` событии таймера функция обратного вызова в Dispatcher вызывается для запуска другого цикла очистки.</span><span class="sxs-lookup"><span data-stu-id="423c2-136">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="423c2-137">Невозможно продлить выполняющийся таймер, когда поступит новое сообщение для перемещения экземпляра в состояние простоя.</span><span class="sxs-lookup"><span data-stu-id="423c2-137">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="423c2-138">Для перехвата вызовов метода <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> и их перенаправления расширению <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> образец реализует `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="423c2-138">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="423c2-139">Реализация <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> содержится в классе `CustomLifetimeLease`.</span><span class="sxs-lookup"><span data-stu-id="423c2-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="423c2-140"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>Метод вызывается, когда WCF собирается освободить экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="423c2-140">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="423c2-141">Однако в коллекции `ISharedSessionInstance` ServiceBehavior имеется только один экземпляр конкретной реализации <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>.</span><span class="sxs-lookup"><span data-stu-id="423c2-141">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="423c2-142">Это означает, что не существует способа узнать, закрыт ли объект <xref:System.ServiceModel.InstanceContext> во время проверки метода в WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="423c2-142">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="423c2-143">Поэтому в этом образце для сериализации запросов к методу используется блокировка потока <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="423c2-143">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="423c2-144">Использовать блокировку потока не рекомендуется, поскольку сериализация может значительно снизить производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="423c2-144">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="423c2-145">Поле закрытого члена используется в `CustomLifetimeLease` классе для отслеживания состояния простоя и возврата <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> методом.</span><span class="sxs-lookup"><span data-stu-id="423c2-145">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="423c2-146">При каждом <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> вызове метода `isIdle` поле возвращается и сбрасывается в `false` .</span><span class="sxs-lookup"><span data-stu-id="423c2-146">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="423c2-147">Важно задать этому параметру значение `false` с тем, чтобы гарантировать вызов диспетчером метода <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="423c2-147">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="423c2-148">Если <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> метод возвращает значение `false` , диспетчер регистрирует функцию обратного вызова с помощью <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="423c2-148">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="423c2-149">Этот метод получает ссылку на освобождаемый контекст <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="423c2-149">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="423c2-150">Поэтому пример кода может запросить `ICustomLease` расширение типа и проверить `ICustomLease.IsIdle` свойство в расширенном состоянии.</span><span class="sxs-lookup"><span data-stu-id="423c2-150">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

<span data-ttu-id="423c2-151">Перед установкой `ICustomLease.IsIdle` свойства необходимо установить свойство обратного вызова, так как это важно для `CustomLeaseExtension` уведомления диспетчера о состоянии простоя.</span><span class="sxs-lookup"><span data-stu-id="423c2-151">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="423c2-152">Если `ICustomLease.IsIdle` возвращает значение `true`, то закрытому элементу `isIdle` в `CustomLifetimeLease` просто устанавливается значение `true` и вызывается метод обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="423c2-152">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="423c2-153">Так как код удерживает блокировку, другие потоки не могут изменить значение этого закрытого члена.</span><span class="sxs-lookup"><span data-stu-id="423c2-153">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="423c2-154">И при следующем вызове диспетчера вызывается метод <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> , который возвращает `true` и позволяет диспетчеру освободить экземпляр.</span><span class="sxs-lookup"><span data-stu-id="423c2-154">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="423c2-155">Завершив подготовительную работу для пользовательского расширения, его необходимо подключить к модели службы.</span><span class="sxs-lookup"><span data-stu-id="423c2-155">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="423c2-156">Чтобы подключить `CustomLeaseExtension` реализацию к <xref:System.ServiceModel.InstanceContext> , WCF предоставляет <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> интерфейс для выполнения начальной загрузки <xref:System.ServiceModel.InstanceContext> .</span><span class="sxs-lookup"><span data-stu-id="423c2-156">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="423c2-157">В этом образце класс `CustomLeaseInitializer` реализует этот интерфейс и добавляет экземпляр `CustomLeaseExtension` в коллекцию <xref:System.ServiceModel.InstanceContext.Extensions%2A> из единственной инициализации метода.</span><span class="sxs-lookup"><span data-stu-id="423c2-157">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="423c2-158">Этот метод вызывается диспетчером при инициализации <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="423c2-158">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="423c2-159">Наконец, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Реализация присоединяется к модели службы с помощью <xref:System.ServiceModel.Description.IServiceBehavior> реализации.</span><span class="sxs-lookup"><span data-stu-id="423c2-159">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="423c2-160">Эта реализация помещается в класс `CustomLeaseTimeAttribute`, кроме того, она является производной от базового класса <xref:System.Attribute> для предоставления этого поведения в виде атрибута.</span><span class="sxs-lookup"><span data-stu-id="423c2-160">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="423c2-161">Это поведение можно добавить в класс образца службы, сопроводив его заметкой в вида атрибута `CustomLeaseTime`.</span><span class="sxs-lookup"><span data-stu-id="423c2-161">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="423c2-162">При запуске данного примера запросы и ответы операций отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="423c2-162">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="423c2-163">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="423c2-163">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="423c2-164">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="423c2-164">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="423c2-165">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="423c2-165">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="423c2-166">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="423c2-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="423c2-167">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="423c2-167">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="423c2-168">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="423c2-168">The samples may already be installed on your machine.</span></span> <span data-ttu-id="423c2-169">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="423c2-169">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="423c2-170">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="423c2-170">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="423c2-171">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="423c2-171">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
