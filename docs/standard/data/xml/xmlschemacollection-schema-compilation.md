---
title: Компиляция схемы XmlSchemaCollection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
ms.openlocfilehash: bb17cd4802f97bb012ae8214b3c4095ed516d367
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721922"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="2727f-102">Компиляция схемы XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="2727f-102">XmlSchemaCollection Schema Compilation</span></span>

<span data-ttu-id="2727f-103">Объект **XmlSchemaCollection** является кэшем или библиотекой, где можно хранить и проверять схемы XDR и XSD.</span><span class="sxs-lookup"><span data-stu-id="2727f-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="2727f-104">Использование **XmlSchemaCollection** повышает производительность, поскольку схемы кэшируются в памяти и их не нужно каждый раз получать из файла или по URL-адресу.</span><span class="sxs-lookup"><span data-stu-id="2727f-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2727f-105">Класс **XmlSchemaCollection** хранит и схемы XDR, и схемы XML, но все методы и свойства, которые принимают или возвращают объект **XmlSchema**, поддерживают только схемы XML.</span><span class="sxs-lookup"><span data-stu-id="2727f-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2727f-106">Класс <xref:System.Xml.Schema.XmlSchemaCollection> устарел и заменен классом <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="2727f-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="2727f-107">Дополнительные сведения о классе <xref:System.Xml.Schema.XmlSchemaSet> см. в руководстве по [использованию XmlSchemaSet для компиляции схемы](xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="2727f-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="2727f-108">Добавление схем в коллекцию</span><span class="sxs-lookup"><span data-stu-id="2727f-108">Add Schemas to the Collection</span></span>  

 <span data-ttu-id="2727f-109">Схемы загружаются в коллекцию с помощью метода **Add** класса **XmlSchemaCollection**, и одновременно с этим схема связывается с URI пространства имен.</span><span class="sxs-lookup"><span data-stu-id="2727f-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="2727f-110">Для схем XML URI-код пространства имен обычно является целевым пространством имен для схемы.</span><span class="sxs-lookup"><span data-stu-id="2727f-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="2727f-111">Для схем XDR URI-код пространства имен будет задаваться во время добавления схемы в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="2727f-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="2727f-112">Проверка наличия схемы в коллекции</span><span class="sxs-lookup"><span data-stu-id="2727f-112">Check for a Schema in the Collection</span></span>  

 <span data-ttu-id="2727f-113">Наличие схемы в коллекции вы можете проверить с помощью метода **Contains**.</span><span class="sxs-lookup"><span data-stu-id="2727f-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="2727f-114">Метод **Contains** принимает объект **XmlSchema** (только для схем XML) или строку, представляющую URI пространства имен, связанного со схемой (для схем XML и XDR).</span><span class="sxs-lookup"><span data-stu-id="2727f-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="2727f-115">Получение схемы из коллекции</span><span class="sxs-lookup"><span data-stu-id="2727f-115">Retrieve a Schema from the Collection</span></span>  

 <span data-ttu-id="2727f-116">Схему из коллекции можно получить с помощью свойства **Item**.</span><span class="sxs-lookup"><span data-stu-id="2727f-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="2727f-117">Свойство **Item** принимает строку, представляющую URI пространства имен, связанного со схемой (обычно это целевое пространство имен), и возвращает объект **XmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="2727f-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="2727f-118">Свойство **Item** применимо только к схемам XML.</span><span class="sxs-lookup"><span data-stu-id="2727f-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="2727f-119">Для схем XDR всегда возвращается ссылка NULL, поскольку для них нет доступной модели объектов.</span><span class="sxs-lookup"><span data-stu-id="2727f-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="2727f-120">Проверка XML-документов с помощью XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="2727f-120">Validate XML Documents Using XmlSchemaCollection</span></span>  

 <span data-ttu-id="2727f-121">Чтобы проверить экземпляр XML-документа с помощью **XmlSchemaCollection**, создайте объект **XmlSchemaCollection**, добавьте в эту коллекцию схемы и задайте свойство **Schemas** для объекта **XmlValidatingReader**, чтобы назначить созданную коллекцию **XmlSchemaCollection** для объекта **XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="2727f-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="2727f-122">Повышенная производительность</span><span class="sxs-lookup"><span data-stu-id="2727f-122">Improved Performance</span></span>  

 <span data-ttu-id="2727f-123">Если вы проверяете несколько документов по одной схеме, мы рекомендуем использовать объект **XmlSchemaCollection**, поскольку его производительность выше благодаря кэшированию схем в памяти.</span><span class="sxs-lookup"><span data-stu-id="2727f-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="2727f-124">Следующий пример кода создает объект **XmlSchemaCollection**, добавляет схемы в коллекцию и задает свойство **Schemas**.</span><span class="sxs-lookup"><span data-stu-id="2727f-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a><span data-ttu-id="2727f-125">См. также</span><span class="sxs-lookup"><span data-stu-id="2727f-125">See also</span></span>

- [<span data-ttu-id="2727f-126">XDR-проверка с помощью XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="2727f-126">XDR Validation with XmlSchemaCollection</span></span>](xdr-validation-with-xmlschemacollection.md)
- [<span data-ttu-id="2727f-127">Проверка по XML-схеме (XSD) с помощью XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="2727f-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](xml-schema-xsd-validation-with-xmlschemacollection.md)
