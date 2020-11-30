---
title: XmlSchemaSet для компиляции схемы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 4501f3dde8d402bd318332dfe9b2209b3febea71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723367"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="986d3-102">XmlSchemaSet для компиляции схемы</span><span class="sxs-lookup"><span data-stu-id="986d3-102">XmlSchemaSet for Schema Compilation</span></span>

<span data-ttu-id="986d3-103">Описывает класс <xref:System.Xml.Schema.XmlSchemaSet>, который представляет собой кэш, в котором можно хранить и проверять схемы XSD.</span><span class="sxs-lookup"><span data-stu-id="986d3-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="986d3-104">Класс XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="986d3-104">The XmlSchemaSet Class</span></span>  

 <span data-ttu-id="986d3-105">Класс <xref:System.Xml.Schema.XmlSchemaSet> - это кэш, в котором можно хранить и проверять схемы XSD.</span><span class="sxs-lookup"><span data-stu-id="986d3-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="986d3-106">В <xref:System.Xml?displayProperty=nameWithType> версии 1.0 схемы XML загружались в класс <xref:System.Xml.Schema.XmlSchemaCollection> как в библиотеку схем.</span><span class="sxs-lookup"><span data-stu-id="986d3-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="986d3-107">В <xref:System.Xml?displayProperty=nameWithType> версии 2.0 классы <xref:System.Xml.XmlValidatingReader> и <xref:System.Xml.Schema.XmlSchemaCollection> устарели и были заменены методами <xref:System.Xml.XmlReader.Create%2A> и классом <xref:System.Xml.Schema.XmlSchemaSet>, соответственно.</span><span class="sxs-lookup"><span data-stu-id="986d3-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="986d3-108">Класс <xref:System.Xml.Schema.XmlSchemaSet> был введен, чтобы устранить ряд проблем, в том числе совместимости со стандартами, производительности и устаревшего формата схемы Microsoft XDR.</span><span class="sxs-lookup"><span data-stu-id="986d3-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="986d3-109">Ниже дано сравнение класса <xref:System.Xml.Schema.XmlSchemaCollection> с классом <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="986d3-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="986d3-110">XmlSchemaCollection</span></span>|<span data-ttu-id="986d3-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="986d3-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="986d3-112">Поддерживает схемы Microsoft XDR и W3C XML.</span><span class="sxs-lookup"><span data-stu-id="986d3-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="986d3-113">Поддерживает только схемы W3C XML.</span><span class="sxs-lookup"><span data-stu-id="986d3-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="986d3-114">Схемы компилируются при вызове метода <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="986d3-115">Схемы не компилируются при вызове метода <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="986d3-116">В результате повышается производительность при создании библиотеки схем.</span><span class="sxs-lookup"><span data-stu-id="986d3-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="986d3-117">Каждая схема формирует отдельную скомпилированную версию, что может привести к созданию «островов схем», т. е. изолированных групп схем.</span><span class="sxs-lookup"><span data-stu-id="986d3-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="986d3-118">В результате все включения и импорты ограничиваются только этой схемой.</span><span class="sxs-lookup"><span data-stu-id="986d3-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="986d3-119">Скомпилированные схемы формируют единую логическую схему, «набор» схем.</span><span class="sxs-lookup"><span data-stu-id="986d3-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="986d3-120">Любые импортированные схемы внутри схемы, добавленные в набор, сами напрямую добавляются в набор.</span><span class="sxs-lookup"><span data-stu-id="986d3-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="986d3-121">Это означает, что все типы доступны всем схемам.</span><span class="sxs-lookup"><span data-stu-id="986d3-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="986d3-122">Для определенного целевого пространства имен в коллекции может существовать только одна схема.</span><span class="sxs-lookup"><span data-stu-id="986d3-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="986d3-123">Для одного целевого пространства имен может быть добавлено несколько схем, если не возникает конфликтов типов.</span><span class="sxs-lookup"><span data-stu-id="986d3-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="986d3-124">Переход на класс XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="986d3-124">Migrating to the XmlSchemaSet</span></span>  

 <span data-ttu-id="986d3-125">В следующем примере кода даны инструкции по переходу на новый класс <xref:System.Xml.Schema.XmlSchemaSet> с устаревшего класса <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="986d3-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="986d3-126">В примере кода показаны следующие важные различия между двумя классами.</span><span class="sxs-lookup"><span data-stu-id="986d3-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="986d3-127">В отличие от метода <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> класса <xref:System.Xml.Schema.XmlSchemaCollection>, при вызове метода <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> класса <xref:System.Xml.Schema.XmlSchemaSet> схемы не компилируются.</span><span class="sxs-lookup"><span data-stu-id="986d3-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-128">В примере кода явно вызывается метод <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> класса <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="986d3-129">Для итераций по классу <xref:System.Xml.Schema.XmlSchemaSet> необходимо использовать свойство <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> класса <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="986d3-130">Пример устаревшего кода с классом <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="986d3-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="986d3-131">Пример эквивалентного кода с классом <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="986d3-132">Добавление и получение схем</span><span class="sxs-lookup"><span data-stu-id="986d3-132">Adding and Retrieving Schemas</span></span>  

 <span data-ttu-id="986d3-133">Схемы добавляются к классу <xref:System.Xml.Schema.XmlSchemaSet> с помощью метода <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> класса <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-134">Когда схема добавляется в класс <xref:System.Xml.Schema.XmlSchemaSet>, она связывается с URI-кодом целевого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="986d3-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="986d3-135">URI-код целевого пространства имен указывается как параметр метода <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>, или, если целевое пространство имен не задано, класс <xref:System.Xml.Schema.XmlSchemaSet> использует целевое пространство имен, определенное в схеме.</span><span class="sxs-lookup"><span data-stu-id="986d3-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="986d3-136">Схемы получаются из класса <xref:System.Xml.Schema.XmlSchemaSet> с помощью свойства <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> класса <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-137">Свойство <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> класса <xref:System.Xml.Schema.XmlSchemaSet> позволяет выполнить итерацию по объектам <xref:System.Xml.Schema.XmlSchema>, содержащимся в классе <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-138">Свойство <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> возвращает все объекты <xref:System.Xml.Schema.XmlSchema>, содержащиеся в классе <xref:System.Xml.Schema.XmlSchemaSet>, или, при указании параметра целевого пространства имен, возвращает все объекты <xref:System.Xml.Schema.XmlSchema>, которые принадлежат целевому пространству имен.</span><span class="sxs-lookup"><span data-stu-id="986d3-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="986d3-139">Если в качестве параметра целевого пространства имен указано `null`, свойство <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> возвращает все схемы без пространства имен.</span><span class="sxs-lookup"><span data-stu-id="986d3-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="986d3-140">В следующем примере схема `books.xsd` из пространства имен `http://www.contoso.com/books` добавляется в класс <xref:System.Xml.Schema.XmlSchemaSet>, затем из класса `http://www.contoso.com/books` получаются все схемы, принадлежащие к пространству имен <xref:System.Xml.Schema.XmlSchemaSet>, и записываются в объект <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="986d3-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="986d3-141">Дополнительные сведения о добавлении и извлечении схем из класса <xref:System.Xml.Schema.XmlSchemaSet> см. в справочной документации по методу <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> и свойству <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="986d3-142">Компиляция схем</span><span class="sxs-lookup"><span data-stu-id="986d3-142">Compiling Schemas</span></span>  

 <span data-ttu-id="986d3-143">Схемы в классе <xref:System.Xml.Schema.XmlSchemaSet> компилируются в одну логическую схему с помощью метода <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> класса <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="986d3-144">В отличие от устаревшего класса <xref:System.Xml.Schema.XmlSchemaCollection>, при вызове метода <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> схемы не компилируются.</span><span class="sxs-lookup"><span data-stu-id="986d3-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="986d3-145">Если метод <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> выполняется успешно, свойство <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> класса <xref:System.Xml.Schema.XmlSchemaSet> имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="986d3-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="986d3-146">Свойство <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> не изменяется, если изменяются схемы в классе <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-147">Обновления отдельных схем в классе <xref:System.Xml.Schema.XmlSchemaSet> не отслеживаются.</span><span class="sxs-lookup"><span data-stu-id="986d3-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="986d3-148">В результате свойство <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> может иметь значение `true`, даже если одна из схем в классе <xref:System.Xml.Schema.XmlSchemaSet> была изменена, но схемы не добавлялись и не удалялись из класса <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="986d3-149">В следующем примере файл `books.xsd` добавляется в класс <xref:System.Xml.Schema.XmlSchemaSet>, а затем вызывается метод <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="986d3-150">Дополнительные сведения о компиляции схем в объекте <xref:System.Xml.Schema.XmlSchemaSet> см. в справочной документации по методу <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="986d3-151">Повторная обработка схем</span><span class="sxs-lookup"><span data-stu-id="986d3-151">Reprocessing Schemas</span></span>  

 <span data-ttu-id="986d3-152">При повторной обработке схемы в классе <xref:System.Xml.Schema.XmlSchemaSet> выполняются все шаги предварительной обработки, выполняемые при вызове метода <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> класса <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="986d3-153">Если метод <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> выполнен успешно, свойство <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> класса <xref:System.Xml.Schema.XmlSchemaSet> имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="986d3-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="986d3-154">Метод <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> должен использоваться, когда схема в классе <xref:System.Xml.Schema.XmlSchemaSet> была изменена после выполнения компиляции классом <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="986d3-155">В следующем примере показана повторная обработка схемы, добавленной в класс <xref:System.Xml.Schema.XmlSchemaSet> с использованием метода <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="986d3-156">После того, как класс <xref:System.Xml.Schema.XmlSchemaSet> скомпилирован с использованием метода <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>, и схема, добавленная в <xref:System.Xml.Schema.XmlSchemaSet>, изменена, свойство <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> имеет значение `true`, даже если схема в классе <xref:System.Xml.Schema.XmlSchemaSet> была изменена.</span><span class="sxs-lookup"><span data-stu-id="986d3-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="986d3-157">При вызове метода <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> выполняется вся предварительная обработка с использованием метода <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>, и свойство <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> устанавливается в значение `false`.</span><span class="sxs-lookup"><span data-stu-id="986d3-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="986d3-158">Дополнительные сведения о повторной обработке схем в классе <xref:System.Xml.Schema.XmlSchemaSet> см. в справочной документации по методу <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="986d3-159">Проверка наличия схемы</span><span class="sxs-lookup"><span data-stu-id="986d3-159">Checking for a Schema</span></span>  

 <span data-ttu-id="986d3-160">Метод <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> класса <xref:System.Xml.Schema.XmlSchemaSet> можно использовать для проверки, что схема содержится в классе <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-161">Метод <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> принимает целевое пространство имен или объект <xref:System.Xml.Schema.XmlSchema> для проверки.</span><span class="sxs-lookup"><span data-stu-id="986d3-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="986d3-162">Метод <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> возвращает значение `true` если схема содержится в классе <xref:System.Xml.Schema.XmlSchemaSet>; в противном случае возвращается значение `false`.</span><span class="sxs-lookup"><span data-stu-id="986d3-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="986d3-163">Дополнительные сведения о проверке наличия схемы см. в справочной документации по методу <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="986d3-164">Удаление схем</span><span class="sxs-lookup"><span data-stu-id="986d3-164">Removing Schemas</span></span>  

 <span data-ttu-id="986d3-165">Схемы удаляются из класса <xref:System.Xml.Schema.XmlSchemaSet> с помощью методов <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> и <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> класса <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-166">Метод <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> удаляет указанную схему из класса <xref:System.Xml.Schema.XmlSchemaSet>, а метод <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> удаляет из класса <xref:System.Xml.Schema.XmlSchemaSet> указанную схему и все схемы, импортированные ей.</span><span class="sxs-lookup"><span data-stu-id="986d3-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="986d3-167">В следующем примере продемонстрировано добавление нескольких схем в класс <xref:System.Xml.Schema.XmlSchemaSet> с последующим использованием метода <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> для удаления одной из схем и всех импортированных ей схем.</span><span class="sxs-lookup"><span data-stu-id="986d3-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="986d3-168">Дополнительные сведения об удалении схем из класса <xref:System.Xml.Schema.XmlSchemaSet> см. в справочной документации по методам <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> и <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>.</span><span class="sxs-lookup"><span data-stu-id="986d3-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="986d3-169">Разрешение схем и xs:import</span><span class="sxs-lookup"><span data-stu-id="986d3-169">Schema Resolution and xs:import</span></span>  

 <span data-ttu-id="986d3-170">В следующих примерах описано поведение класса <xref:System.Xml.Schema.XmlSchemaSet> при импорте схем и существовании в классе <xref:System.Xml.Schema.XmlSchemaSet> нескольких схем для данного пространства имен.</span><span class="sxs-lookup"><span data-stu-id="986d3-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="986d3-171">Например, рассмотрим класс <xref:System.Xml.Schema.XmlSchemaSet>, содержащий несколько схем пространства имен `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="986d3-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="986d3-172">Схема со следующей директивой `xs:import` добавлена в класс <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="986d3-173">Класс <xref:System.Xml.Schema.XmlSchemaSet> пытается импортировать схему пространства имен `http://www.contoso.com`, загрузив ее по URL-адресу `http://www.contoso.com/schema.xsd`.</span><span class="sxs-lookup"><span data-stu-id="986d3-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="986d3-174">В импортируемой схеме доступны только декларация схемы и типы, объявленные в документе схемы, даже если другие документы схемы из пространства имен `http://www.contoso.com` существуют в классе <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-175">Если файл `schema.xsd` не может быть обнаружен по URL-адресу `http://www.contoso.com/schema.xsd`, схема для пространства имен `http://www.contoso.com` не импортируется в импортируемую схему.</span><span class="sxs-lookup"><span data-stu-id="986d3-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="986d3-176">Проверка XML-документов</span><span class="sxs-lookup"><span data-stu-id="986d3-176">Validating XML Documents</span></span>  

 <span data-ttu-id="986d3-177">XML-документы могут быть проверены путем сопоставления со схемами в классе <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="986d3-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="986d3-178">Для проверки XML-документа нужно добавить схему в свойство <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> объекта <xref:System.Xml.XmlReaderSettings>, или добавить класс <xref:System.Xml.Schema.XmlSchemaSet> к свойству <xref:System.Xml.XmlReaderSettings.Schemas%2A> объекта <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="986d3-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="986d3-179">Затем объект <xref:System.Xml.XmlReaderSettings> используется методом <xref:System.Xml.XmlReader.Create%2A> класса <xref:System.Xml.XmlReader>, чтобы создать объект <xref:System.Xml.XmlReader> и проверить XML-документ.</span><span class="sxs-lookup"><span data-stu-id="986d3-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="986d3-180">Дополнительные сведения о проверке XML-документов с использованием класса <xref:System.Xml.Schema.XmlSchemaSet> см. в руководстве по [проверке схем XML (XSD) с помощью XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="986d3-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986d3-181">См. также</span><span class="sxs-lookup"><span data-stu-id="986d3-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="986d3-182">Использование XmlSchemaSet как кэша схемы</span><span class="sxs-lookup"><span data-stu-id="986d3-182">XmlSchemaSet as a Schema Cache</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="986d3-183">Проверка по XML-схеме (XSD) с помощью XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="986d3-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](xml-schema-xsd-validation-with-xmlschemaset.md)
