---
description: Дополнительные сведения о расширении размещения с помощью ServiceHostFactory
title: Расширение размещения с использованием ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: cd7749a153f23586bbf570eaf97f5ae849fc522d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735144"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="25109-103">Расширение размещения с использованием ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="25109-103">Extending Hosting Using ServiceHostFactory</span></span>

<span data-ttu-id="25109-104">Стандартный <xref:System.ServiceModel.ServiceHost> API для размещения служб в Windows Communication Foundation (WCF) является точкой расширения в архитектуре WCF.</span><span class="sxs-lookup"><span data-stu-id="25109-104">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="25109-105">Пользователи могут наследовать свои собственные хост-классы от класса <xref:System.ServiceModel.ServiceHost>, как правило, чтобы переопределить <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> для использования <xref:System.ServiceModel.Description.ServiceDescription> с целью принудительного добавления конечных точек по умолчанию или изменения поведений до открытия службы.</span><span class="sxs-lookup"><span data-stu-id="25109-105">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="25109-106">В резидентной среде нет необходимости создавать пользовательский класс <xref:System.ServiceModel.ServiceHost>, поскольку записывается код, создающий узел, а после его создания в нем вызывается метод <xref:System.ServiceModel.ICommunicationObject.Open>.</span><span class="sxs-lookup"><span data-stu-id="25109-106">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="25109-107">В промежутке между этими двумя операциями можно выполнять любые действия.</span><span class="sxs-lookup"><span data-stu-id="25109-107">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="25109-108">Можно, например, добавить новое поведение <xref:System.ServiceModel.Description.IServiceBehavior>.</span><span class="sxs-lookup"><span data-stu-id="25109-108">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="25109-109">Такой подход нельзя использовать повторно.</span><span class="sxs-lookup"><span data-stu-id="25109-109">This approach is not reusable.</span></span> <span data-ttu-id="25109-110">Код, управляющий описанием, кодируется в программе узла (в данном случае функция Main()), поэтому эту логику трудно повторно использовать в другом контексте.</span><span class="sxs-lookup"><span data-stu-id="25109-110">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="25109-111">Также существуют другие способы добавления поведения <xref:System.ServiceModel.Description.IServiceBehavior>, для которых не требуется принудительный код.</span><span class="sxs-lookup"><span data-stu-id="25109-111">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="25109-112">Можно наследовать атрибут от атрибута <xref:System.ServiceModel.ServiceBehaviorAttribute> и использовать его в типе реализации службы или можно сделать пользовательское поведение настраиваемым и составить его динамически с использованием конфигурации.</span><span class="sxs-lookup"><span data-stu-id="25109-112">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="25109-113">Однако для решения этой проблемы можно также использовать варианты этого примера с незначительными различиями.</span><span class="sxs-lookup"><span data-stu-id="25109-113">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="25109-114">Один подход заключается в перемещении кода, добавляющего ServiceBehavior, из функции `Main()` в метод <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> пользовательского класса, унаследованного от класса <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="25109-114">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 <span data-ttu-id="25109-115">Затем внутри функции `Main()` можно использовать следующее.</span><span class="sxs-lookup"><span data-stu-id="25109-115">Then, inside of `Main()` you can use:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="25109-116">Сейчас пользовательская логика инкапсулирована в пустую абстракцию, которую можно легко использовать повторно во множестве различных исполняемых файлах узла.</span><span class="sxs-lookup"><span data-stu-id="25109-116">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="25109-117">Способ использования пользовательского класса <xref:System.ServiceModel.ServiceHost> в службах IIS или службе активации Windows (WAS) неочевиден.</span><span class="sxs-lookup"><span data-stu-id="25109-117">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="25109-118">Эти среды отличаются от резидентной среды, поскольку среда размещения создает <xref:System.ServiceModel.ServiceHost> от имени приложения.</span><span class="sxs-lookup"><span data-stu-id="25109-118">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="25109-119">Инфраструктура размещения IIS и WAS ничего не знает о пользовательском классе, унаследованном от класса <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="25109-119">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="25109-120">Фабрика <xref:System.ServiceModel.Activation.ServiceHostFactory> разработана для решения проблемы получения доступа к пользовательскому классу <xref:System.ServiceModel.ServiceHost> из IIS или WAS.</span><span class="sxs-lookup"><span data-stu-id="25109-120">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="25109-121">Поскольку пользовательский узел, унаследованный от класса <xref:System.ServiceModel.ServiceHost>, динамически настроен и потенциально принадлежит к различным типам, среда размещения никогда не создает его напрямую.</span><span class="sxs-lookup"><span data-stu-id="25109-121">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="25109-122">Вместо этого в WCF используется шаблон фабрики для обеспечения уровня косвенного обращения между средой размещения и конкретным типом службы.</span><span class="sxs-lookup"><span data-stu-id="25109-122">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="25109-123">Если не задано иное, используется реализация фабрики <xref:System.ServiceModel.Activation.ServiceHostFactory> по умолчанию, возвращающая экземпляр класса <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="25109-123">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="25109-124">Но вы также можете предоставить собственную фабрику, которая возвращает производный узел, указав имя типа CLR для реализации фабрики в @ServiceHost директиве.</span><span class="sxs-lookup"><span data-stu-id="25109-124">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="25109-125">Замысел заключается в том, что в основных случаях реализация собственной фабрики должна иметь простое применение.</span><span class="sxs-lookup"><span data-stu-id="25109-125">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="25109-126">Например, ниже представлена пользовательская фабрика <xref:System.ServiceModel.Activation.ServiceHostFactory>, возвращающая класс, унаследованный от класса <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="25109-126">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="25109-127">Чтобы использовать эту фабрику вместо фабрики по умолчанию, укажите имя типа в @ServiceHost директиве следующим образом:</span><span class="sxs-lookup"><span data-stu-id="25109-127">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <span data-ttu-id="25109-128">Хотя нет технических ограничений на операции с классом <xref:System.ServiceModel.ServiceHost>, возвращаемым методом <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, рекомендуется сохранять реализации фабрики как можно более простыми.</span><span class="sxs-lookup"><span data-stu-id="25109-128">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="25109-129">Если у вас много пользовательских логики, лучше разместить эту логику в своем узле, а не в фабрике, чтобы ее можно было использовать повторно.</span><span class="sxs-lookup"><span data-stu-id="25109-129">If you have lots of custom logic, it is better to put that logic inside of your host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="25109-130">Существует еще один уровень размещения API, о котором следует упомянуть здесь.</span><span class="sxs-lookup"><span data-stu-id="25109-130">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="25109-131">WCF также имеет <xref:System.ServiceModel.ServiceHostBase> и <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> , от которой <xref:System.ServiceModel.ServiceHost> и <xref:System.ServiceModel.Activation.ServiceHostFactory> соответственно является производным.</span><span class="sxs-lookup"><span data-stu-id="25109-131">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="25109-132">Существуют более сложные сценарии, в которых необходимо выгружать большие части системы метаданных с помощью собственных настроенных созданий.</span><span class="sxs-lookup"><span data-stu-id="25109-132">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
