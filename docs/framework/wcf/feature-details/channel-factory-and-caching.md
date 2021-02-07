---
description: 'Дополнительные сведения: фабрика каналов и кэширование'
title: Производство каналов и кэширование
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 6922191c2b99dea516d0e85aac9ed7bc12a67b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705204"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="c3a68-103">Производство каналов и кэширование</span><span class="sxs-lookup"><span data-stu-id="c3a68-103">Channel Factory and Caching</span></span>

<span data-ttu-id="c3a68-104">Клиентские приложения WCF используют класс <xref:System.ServiceModel.ChannelFactory%601> для создания коммуникационного канала со службой WCF.</span><span class="sxs-lookup"><span data-stu-id="c3a68-104">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="c3a68-105">Создание экземпляров класса <xref:System.ServiceModel.ChannelFactory%601> оказывает определенное влияние на производительность, поскольку выполняются следующие операции:</span><span class="sxs-lookup"><span data-stu-id="c3a68-105">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>

- <span data-ttu-id="c3a68-106">Построение дерева <xref:System.ServiceModel.Description.ContractDescription></span><span class="sxs-lookup"><span data-stu-id="c3a68-106">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>

- <span data-ttu-id="c3a68-107">Отображение всех необходимых типов CLR</span><span class="sxs-lookup"><span data-stu-id="c3a68-107">Reflecting all of the required CLR types</span></span>

- <span data-ttu-id="c3a68-108">Построение стека каналов</span><span class="sxs-lookup"><span data-stu-id="c3a68-108">Constructing the channel stack</span></span>

- <span data-ttu-id="c3a68-109">Освобождение ресурсов</span><span class="sxs-lookup"><span data-stu-id="c3a68-109">Disposing of resources</span></span>

<span data-ttu-id="c3a68-110">Чтобы уменьшить дополнительные расходы ресурсов, WCF может кэшировать фабрики каналов при использовании прокси клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="c3a68-110">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>

> [!TIP]
> <span data-ttu-id="c3a68-111">Вы непосредственно управляете созданием фабрики каналов, когда класс <xref:System.ServiceModel.ChannelFactory%601> используется напрямую.</span><span class="sxs-lookup"><span data-stu-id="c3a68-111">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>

<span data-ttu-id="c3a68-112">Прокси-серверы клиента WCF, созданные с помощью [средства служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , являются производными от <xref:System.ServiceModel.ClientBase%601> .</span><span class="sxs-lookup"><span data-stu-id="c3a68-112">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="c3a68-113"><xref:System.ServiceModel.ClientBase%601> определяет статическое свойство <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A>, которое определяет режим кэширования фабрики каналов.</span><span class="sxs-lookup"><span data-stu-id="c3a68-113"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="c3a68-114">Параметры кэша задаются для определенного типа.</span><span class="sxs-lookup"><span data-stu-id="c3a68-114">Cache settings are made for a specific type.</span></span> <span data-ttu-id="c3a68-115">Например, задание  `ClientBase<ITest>.CacheSettings` одного из значений, определенных ниже, влияет только на прокси-объект или объект ClientBase типа `ITest` .</span><span class="sxs-lookup"><span data-stu-id="c3a68-115">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="c3a68-116">Параметры кэша для конкретного <xref:System.ServiceModel.ClientBase%601> являются неизменяемыми после создания первого экземпляра класса-посредника или ClientBase.</span><span class="sxs-lookup"><span data-stu-id="c3a68-116">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>

## <a name="specifying-caching-behavior"></a><span data-ttu-id="c3a68-117">Установка режима кэширования</span><span class="sxs-lookup"><span data-stu-id="c3a68-117">Specifying Caching Behavior</span></span>

<span data-ttu-id="c3a68-118">Режим кэширования задается установкой свойства <xref:System.ServiceModel.ClientBase%601.CacheSetting> в одно из следующих значений.</span><span class="sxs-lookup"><span data-stu-id="c3a68-118">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>

|<span data-ttu-id="c3a68-119">Значение параметра кэша</span><span class="sxs-lookup"><span data-stu-id="c3a68-119">Cache Setting Value</span></span>|<span data-ttu-id="c3a68-120">Описание</span><span class="sxs-lookup"><span data-stu-id="c3a68-120">Description</span></span>|
|-------------------------|-----------------|
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="c3a68-121">Все экземпляры <xref:System.ServiceModel.ClientBase%601> в пределах домена приложения могут участвовать в кэшировании.</span><span class="sxs-lookup"><span data-stu-id="c3a68-121">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="c3a68-122">Разработчик определил, что при кэшировании не будет неблагоприятных последствий для безопасности.</span><span class="sxs-lookup"><span data-stu-id="c3a68-122">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="c3a68-123">Кэширование не будет отключено даже при доступе к свойствам с учетом безопасности <xref:System.ServiceModel.ClientBase%601> .</span><span class="sxs-lookup"><span data-stu-id="c3a68-123">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="c3a68-124">Свойства, учитывающие безопасность <xref:System.ServiceModel.ClientBase%601> , — это <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> , <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> и <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A> .</span><span class="sxs-lookup"><span data-stu-id="c3a68-124">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="c3a68-125">Только экземпляры <xref:System.ServiceModel.ClientBase%601>, созданные на основе конечных точек, определенных в файлах конфигурации, участвуют в кэшировании внутри домена приложения.</span><span class="sxs-lookup"><span data-stu-id="c3a68-125">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="c3a68-126">Ни один экземпляр <xref:System.ServiceModel.ClientBase%601>, созданный программно внутри домена приложения, не будет участвовать в кэшировании.</span><span class="sxs-lookup"><span data-stu-id="c3a68-126">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="c3a68-127">Кроме того, кэширование будет отключено для экземпляра <xref:System.ServiceModel.ClientBase%601> после обращения к любому из свойств «с учетом безопасности».</span><span class="sxs-lookup"><span data-stu-id="c3a68-127">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="c3a68-128">Кэширование отключается для всех экземпляров <xref:System.ServiceModel.ClientBase%601> определенного типа в пределах домена приложений.</span><span class="sxs-lookup"><span data-stu-id="c3a68-128">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|

<span data-ttu-id="c3a68-129">Следующие фрагменты кода показывают использование свойства <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3a68-129">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))
         {
            // ...
            proxy.Test(msg);
            // ...
         }
      }
   }
}
// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }
```

<span data-ttu-id="c3a68-130">В приведенном выше коде все экземпляры `TestClient` будут использовать одну и ту же фабрику каналов.</span><span class="sxs-lookup"><span data-stu-id="c3a68-130">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.Default;
      int i = 1;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            if (i == 4)
            {
               ServiceEndpoint endpoint = proxy.Endpoint;
               ... // use endpoint in some way
            }
            proxy.Test(msg);
         }
         i++;
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

<span data-ttu-id="c3a68-131">В приведенном выше примере все экземпляры `TestClient` будут использовать одну и ту же фабрику каналов, за исключением экземпляра № 4.</span><span class="sxs-lookup"><span data-stu-id="c3a68-131">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="c3a68-132">Экземпляр № 4 будет использовать фабрику каналов, созданную специально для этой цели.</span><span class="sxs-lookup"><span data-stu-id="c3a68-132">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="c3a68-133">Этот параметр не работает в сценариях, где определенной конечной точке необходимы различные параметры безопасности из других конечных точек того же типа фабрики каналов (в данном случае `ITest`).</span><span class="sxs-lookup"><span data-stu-id="c3a68-133">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            proxy.Test(msg);
         }
      }
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

<span data-ttu-id="c3a68-134">В приведенном выше примере все экземпляры `TestClient` будут использовать различные фабрики каналов.</span><span class="sxs-lookup"><span data-stu-id="c3a68-134">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="c3a68-135">Это полезно в случае, если каждая конечная точка имеет различные требования к безопасности и нет смысла выполнять кэширование.</span><span class="sxs-lookup"><span data-stu-id="c3a68-135">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3a68-136">См. также</span><span class="sxs-lookup"><span data-stu-id="c3a68-136">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="c3a68-137">Создание клиентов</span><span class="sxs-lookup"><span data-stu-id="c3a68-137">Building Clients</span></span>](../building-clients.md)
- [<span data-ttu-id="c3a68-138">Клиенты</span><span class="sxs-lookup"><span data-stu-id="c3a68-138">Clients</span></span>](clients.md)
- [<span data-ttu-id="c3a68-139">Обращение к службам с использованием клиента WCF</span><span class="sxs-lookup"><span data-stu-id="c3a68-139">Accessing Services Using a WCF Client</span></span>](../accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="c3a68-140">Практическое руководство. Использование ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="c3a68-140">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
