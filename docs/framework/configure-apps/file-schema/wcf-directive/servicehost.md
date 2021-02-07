---
description: 'Дополнительные сведения: @ServiceHost'
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: d16fda68bdc753121f02f6332dabedf236fac257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750316"
---
# <a name="servicehost"></a><span data-ttu-id="92d5a-102">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="92d5a-102">\@ServiceHost</span></span>

<span data-ttu-id="92d5a-103">Связывает фабрику, используемую для создания узла службы, с размещаемой службой и другими элементами программирования, необходимыми для доступа или компиляции кода размещения, представленного в SVC-файле.</span><span class="sxs-lookup"><span data-stu-id="92d5a-103">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>

## <a name="syntax"></a><span data-ttu-id="92d5a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92d5a-104">Syntax</span></span>

```aspx-csharp
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a><span data-ttu-id="92d5a-105">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="92d5a-105">Attributes</span></span>

### <a name="service"></a><span data-ttu-id="92d5a-106">Служба</span><span class="sxs-lookup"><span data-stu-id="92d5a-106">Service</span></span>

<span data-ttu-id="92d5a-107">Имя типа CLR размещенной службы.</span><span class="sxs-lookup"><span data-stu-id="92d5a-107">The CLR type name of the service hosted.</span></span> <span data-ttu-id="92d5a-108">Это должно быть полное имя типа, который реализует один или несколько контактов службы.</span><span class="sxs-lookup"><span data-stu-id="92d5a-108">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>

### <a name="factory"></a><span data-ttu-id="92d5a-109">Factory</span><span class="sxs-lookup"><span data-stu-id="92d5a-109">Factory</span></span>

<span data-ttu-id="92d5a-110">Имя типа CLR фабрики узла службы, используемой для создания узла службы.</span><span class="sxs-lookup"><span data-stu-id="92d5a-110">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="92d5a-111">Этот атрибут является необязательным.</span><span class="sxs-lookup"><span data-stu-id="92d5a-111">This attribute is optional.</span></span> <span data-ttu-id="92d5a-112">Если данный атрибут не задан, по умолчанию используется значение <xref:System.ServiceModel.Activation.ServiceHostFactory>, которое возвращает экземпляр <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="92d5a-112">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

### <a name="debug"></a><span data-ttu-id="92d5a-113">Отладка</span><span class="sxs-lookup"><span data-stu-id="92d5a-113">Debug</span></span>

<span data-ttu-id="92d5a-114">Указывает, должна ли служба Windows Communication Foundation (WCF) компилироваться с отладочными символами.</span><span class="sxs-lookup"><span data-stu-id="92d5a-114">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="92d5a-115">`true` значение, если служба WCF должна быть скомпилирована с отладочными символами; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="92d5a-115">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>

### <a name="language"></a><span data-ttu-id="92d5a-116">Язык</span><span class="sxs-lookup"><span data-stu-id="92d5a-116">Language</span></span>

<span data-ttu-id="92d5a-117">Задает язык, используемый при компиляции всего встроенного кода в файле (SVC).</span><span class="sxs-lookup"><span data-stu-id="92d5a-117">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="92d5a-118">Значения могут представлять любые. NET — поддерживаемый язык, включая `C#` , `VB` и `JS` , которые ссылаются на C#, Visual Basic и JScript .NET соответственно.</span><span class="sxs-lookup"><span data-stu-id="92d5a-118">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="92d5a-119">Этот атрибут является необязательным.</span><span class="sxs-lookup"><span data-stu-id="92d5a-119">This attribute is optional.</span></span>

### <a name="codebehind"></a><span data-ttu-id="92d5a-120">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="92d5a-120">CodeBehind</span></span>

<span data-ttu-id="92d5a-121">Указывает исходный файл, который реализует веб-службу XML, если класс, реализующий веб-службу XML, не находится в том же файле и не был скомпилирован в сборку и помещен в каталог *\bin* .</span><span class="sxs-lookup"><span data-stu-id="92d5a-121">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the *\Bin* directory.</span></span>

## <a name="remarks"></a><span data-ttu-id="92d5a-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="92d5a-122">Remarks</span></span>

<span data-ttu-id="92d5a-123">Объект, <xref:System.ServiceModel.ServiceHost> используемый для размещения службы, является точкой расширения в модели программирования Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="92d5a-123">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="92d5a-124">Для создания узла службы <xref:System.ServiceModel.ServiceHost> используется шаблон фабрики, поскольку он, возможно, имеет полиморфный тип, экземпляр которого среда размещения не должна создавать явно.</span><span class="sxs-lookup"><span data-stu-id="92d5a-124">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>

<span data-ttu-id="92d5a-125">В реализации по умолчанию используется фабрика <xref:System.ServiceModel.Activation.ServiceHostFactory> для создания экземпляра узла службы <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="92d5a-125">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="92d5a-126">Но вы можете предоставить собственную фабрику (которая возвращает производный узел), указав имя типа CLR для реализации фабрики в `@ServiceHost` директиве.</span><span class="sxs-lookup"><span data-stu-id="92d5a-126">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the `@ServiceHost` directive.</span></span>

<span data-ttu-id="92d5a-127">Чтобы использовать собственную фабрику узла службы вместо фабрики по умолчанию, просто укажите имя типа в `@ServiceHost` директиве следующим образом.</span><span class="sxs-lookup"><span data-stu-id="92d5a-127">To use you own custom service host factory instead of the default factory, just provide the type name in the `@ServiceHost` directive as follows.</span></span>

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

<span data-ttu-id="92d5a-128">Создавайте реализацию фабрики в наиболее простом виде.</span><span class="sxs-lookup"><span data-stu-id="92d5a-128">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="92d5a-129">Если имеется значительный объем пользовательской логики, то можно увеличить возможность повторного использования кода, если разместить эту логику на узле, а не в фабрике.</span><span class="sxs-lookup"><span data-stu-id="92d5a-129">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>

<span data-ttu-id="92d5a-130">Например, чтобы включить конечную точку с поддержкой AJAX для `MyService` , укажите <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> для значения `Factory` атрибута, а не по умолчанию <xref:System.ServiceModel.Activation.ServiceHostFactory> в `@ServiceHost` директиве, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="92d5a-130">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the `@ServiceHost` directive as shown in the following example:</span></span>

```aspx-csharp
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a><span data-ttu-id="92d5a-131">См. также</span><span class="sxs-lookup"><span data-stu-id="92d5a-131">See also</span></span>

- [<span data-ttu-id="92d5a-132">Пользовательский узел службы</span><span class="sxs-lookup"><span data-stu-id="92d5a-132">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
