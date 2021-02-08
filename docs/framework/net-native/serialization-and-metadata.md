---
description: Дополнительные сведения см. в статье сериализация и метаданные.
title: Сериализация и метаданные
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: da7424d683922618abda4b896bc0e7cf2dbc87be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801973"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="41e3f-103">Сериализация и метаданные</span><span class="sxs-lookup"><span data-stu-id="41e3f-103">Serialization and Metadata</span></span>

<span data-ttu-id="41e3f-104">Если ваше приложение сериализует и десериализует объекты, может потребоваться добавить записи в файл директив среды выполнения (. rd.xml) файл, чтобы гарантировать наличие необходимых метаданных во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="41e3f-104">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="41e3f-105">Существует две категории сериализаторов, и каждый требует различной обработки в файла директив среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="41e3f-105">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="41e3f-106">Сериализиторы сторонних поставщиков на основе отражения.</span><span class="sxs-lookup"><span data-stu-id="41e3f-106">Reflection-based third-party serializers.</span></span> <span data-ttu-id="41e3f-107">Они требуют изменений в файле директив среды выполнения и рассматриваются в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="41e3f-107">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="41e3f-108">В библиотеке классов платформа .NET Framework найдены сериализаторы, не основанные на отражении.</span><span class="sxs-lookup"><span data-stu-id="41e3f-108">Non-reflection-based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="41e3f-109">Они могут потребовать внесения изменений в файл директив среды выполнения и обсуждаются в разделе [Сериализаторы Майкрософт](#Microsoft).</span><span class="sxs-lookup"><span data-stu-id="41e3f-109">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>

## <a name="third-party-serializers"></a><span data-ttu-id="41e3f-110">Сериализаторы сторонних поставщиков</span><span class="sxs-lookup"><span data-stu-id="41e3f-110">Third-party serializers</span></span>

 <span data-ttu-id="41e3f-111">Сериализаторы сторонних поставщиков, включая Newtonsoft.JSON, обычно основаны на отражении.</span><span class="sxs-lookup"><span data-stu-id="41e3f-111">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="41e3f-112">Учитывая большой двоичный объект (BLOB) из сериализованных данных, поля данных назначаются конкретному типу путем поиска полей типа целевого объекта по имени.</span><span class="sxs-lookup"><span data-stu-id="41e3f-112">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="41e3f-113">Как минимум, использование этих библиотек приводит к исключениям [MissingMetadataException](missingmetadataexception-class-net-native.md) для каждого объекта <xref:System.Type> при попытке сериализации или десериализации в коллекции `List<Type>`.</span><span class="sxs-lookup"><span data-stu-id="41e3f-113">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="41e3f-114">Самый простой способ решения проблем, вызванных отсутствующими метаданными для этих сериализаторов, состоит в сборе типов, которые будут использоваться при сериализации в одном пространстве имен (например, `App.Models`) и применить к нему директиву метаданных `Serialize`:</span><span class="sxs-lookup"><span data-stu-id="41e3f-114">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="41e3f-115">Сведения о синтаксисе, используемом в примере, см. в разделе [ \<Namespace> element](namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="41e3f-115">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>

## <a name="microsoft-serializers"></a><span data-ttu-id="41e3f-116">Сериализаторы Microsoft</span><span class="sxs-lookup"><span data-stu-id="41e3f-116">Microsoft serializers</span></span>

 <span data-ttu-id="41e3f-117">Несмотря на то, что классы <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> и <xref:System.Xml.Serialization.XmlSerializer> не рассчитывают на отражение, они требуют создания кода на основе объекта для сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="41e3f-117">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="41e3f-118">Перегруженные конструкторы для каждого сериализатора содержа параметр <xref:System.Type>, который задает тип для сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="41e3f-118">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="41e3f-119">Способ указания этого типа в коде определяет действие, которое необходимо выполнить, как описано в следующих двух разделах.</span><span class="sxs-lookup"><span data-stu-id="41e3f-119">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="41e3f-120">TypeOf используется в конструкторе</span><span class="sxs-lookup"><span data-stu-id="41e3f-120">typeof used in the constructor</span></span>

 <span data-ttu-id="41e3f-121">Если вызвать конструктор этих классов сериализации и включить в вызов метода оператор C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) , нет необходимости **выполнять дополнительную работу**.</span><span class="sxs-lookup"><span data-stu-id="41e3f-121">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="41e3f-122">Например, в каждом из следующих вызовов конструктора класса сериализации ключевое слово `typeof`используется как часть выражения, переданного в конструктор.</span><span class="sxs-lookup"><span data-stu-id="41e3f-122">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="41e3f-123">Компилятор .NET Native будет автоматически выполнять этот код.</span><span class="sxs-lookup"><span data-stu-id="41e3f-123">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="41e3f-124">TypeOf, использованный за пределами конструктора</span><span class="sxs-lookup"><span data-stu-id="41e3f-124">typeof used outside the constructor</span></span>

 <span data-ttu-id="41e3f-125">При вызове конструктора этих классов сериализации и использовании оператора C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) за пределами выражения, переданного в параметр конструктора <xref:System.Type> , как показано в следующем коде, компилятору .NET Native не удается разрешить тип:</span><span class="sxs-lookup"><span data-stu-id="41e3f-125">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="41e3f-126">В этом случае необходимо указать тип в файле директив среды выполнения, добавив следующую запись:</span><span class="sxs-lookup"><span data-stu-id="41e3f-126">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="41e3f-127">Аналогичным образом, если вызвать конструктор, например, <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> и предоставить массив дополнительных <xref:System.Type> объектов для сериализации, как показано в следующем коде, компилятор .NET Native не может разрешить эти типы.</span><span class="sxs-lookup"><span data-stu-id="41e3f-127">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
<span data-ttu-id="41e3f-128">Добавьте следующие записи для каждого типа в файл директив среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="41e3f-128">Add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
<span data-ttu-id="41e3f-129">Сведения о синтаксисе, используемом в примере, см. в разделе [ \<Type> element](type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="41e3f-129">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e3f-130">См. также</span><span class="sxs-lookup"><span data-stu-id="41e3f-130">See also</span></span>

- [<span data-ttu-id="41e3f-131">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="41e3f-131">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="41e3f-132">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="41e3f-132">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="41e3f-133">\<Type> Элемент</span><span class="sxs-lookup"><span data-stu-id="41e3f-133">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="41e3f-134">\<Namespace> Элемент</span><span class="sxs-lookup"><span data-stu-id="41e3f-134">\<Namespace> Element</span></span>](namespace-element-net-native.md)
