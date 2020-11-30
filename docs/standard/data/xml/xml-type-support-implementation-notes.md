---
title: Примечания по реализации поддержки типов XML
ms.date: 03/30/2017
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 29535efcbc7ecaaef0c5d1620ac05464a9a6a69a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731921"
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="11921-102">Примечания по реализации поддержки типов XML</span><span class="sxs-lookup"><span data-stu-id="11921-102">XML Type Support Implementation Notes</span></span>

<span data-ttu-id="11921-103">В этом разделе описываются определенные детали реализации, которые следует знать.</span><span class="sxs-lookup"><span data-stu-id="11921-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="11921-104">Сопоставление списков</span><span class="sxs-lookup"><span data-stu-id="11921-104">List Mappings</span></span>  

 <span data-ttu-id="11921-105">Типы <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]** и <xref:System.String> используются для представления типов списков языка XSD.</span><span class="sxs-lookup"><span data-stu-id="11921-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="11921-106">Сопоставление объединений</span><span class="sxs-lookup"><span data-stu-id="11921-106">Union Mappings</span></span>  

 <span data-ttu-id="11921-107">Типы объединений представляются с помощью типов <xref:System.Xml.Schema.XmlAtomicValue> или <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11921-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="11921-108">Следовательно, исходный тип или тип назначения всегда должны принадлежать либо к типу <xref:System.String>, либо к типу <xref:System.Xml.Schema.XmlAtomicValue>.</span><span class="sxs-lookup"><span data-stu-id="11921-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="11921-109">Если объект <xref:System.Xml.Schema.XmlSchemaDatatype> представляет тип списка, этот объект преобразует входное строковое значение в список, состоящий из одного или нескольких объектов.</span><span class="sxs-lookup"><span data-stu-id="11921-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="11921-110">Если объект <xref:System.Xml.Schema.XmlSchemaDatatype> представляет тип объединения, тогда предпринимается попытка проанализировать входное значение как тип элемента объединения.</span><span class="sxs-lookup"><span data-stu-id="11921-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="11921-111">В случае сбоя попытки синтаксического анализа предпринимается попытка преобразования следующего элемента объединения и т. д. - до тех пор, пока преобразование не будет успешным или пока не останется других типов элементов. В последнем случае возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="11921-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="11921-112">Различия между типами данных CLR и XML</span><span class="sxs-lookup"><span data-stu-id="11921-112">Differences Between CLR and XML Data Types</span></span>  

 <span data-ttu-id="11921-113">Ниже описывается ряд несоответствий, которые могут возникать между типами данных CLR и XML, и о том, как они преодолеваются.</span><span class="sxs-lookup"><span data-stu-id="11921-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11921-114">Префикс `xs` сопоставляется с <https://www.w3.org/2001/XMLSchema> и URI пространства имен.</span><span class="sxs-lookup"><span data-stu-id="11921-114">The `xs` prefix is mapped to the <https://www.w3.org/2001/XMLSchema> and namespace URI.</span></span>
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="11921-115">System.TimeSpan и xs:duration</span><span class="sxs-lookup"><span data-stu-id="11921-115">System.TimeSpan and xs:duration</span></span>  

 <span data-ttu-id="11921-116">Тип `xs:duration` частично упорядочен в том смысле, что в нем представлены некоторые значения длительности, отличные друг от друга, но эквивалентные.</span><span class="sxs-lookup"><span data-stu-id="11921-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="11921-117">Это означает, что для типа `xs:duration` значение 1 месяц (P1M) меньше чем 32 дня (P32D), больше чем 27 дней (P27D) и эквивалентно 28, 29 или 30 дням.</span><span class="sxs-lookup"><span data-stu-id="11921-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="11921-118">Класс <xref:System.TimeSpan> не поддерживает такое частичное упорядочение.</span><span class="sxs-lookup"><span data-stu-id="11921-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="11921-119">Он предполагает использование определенного числа дней для 1 года и для 1 месяца: 365 дней и 30 дней соответственно.</span><span class="sxs-lookup"><span data-stu-id="11921-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="11921-120">Дополнительные сведения о типе `xs:duration` см. в документе W3C [Схема XML. Часть 2. Рекомендация по типам данных](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="11921-120">For more information on the `xs:duration` type, see the W3C [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="11921-121">Типы данных xs:time, григорианского календаря и System.DateTime</span><span class="sxs-lookup"><span data-stu-id="11921-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  

 <span data-ttu-id="11921-122">Когда значение `xs:time` сопоставляется с объектом <xref:System.DateTime>, поле <xref:System.DateTime.MinValue> используется для инициализации свойств даты объекта <xref:System.DateTime> (таких как <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A> и <xref:System.DateTime.Day%2A>) наименьшим из возможных значений <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="11921-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="11921-123">Подобным же образом экземпляры типов `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` и `xs:gMonthDay` сопоставляются с объектом <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="11921-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="11921-124">Неиспользованные свойства объекта <xref:System.DateTime> получают значения поля <xref:System.DateTime.MinValue>.</span><span class="sxs-lookup"><span data-stu-id="11921-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11921-125">Не следует полагаться на значение свойства <xref:System.DateTime.Year%2A?displayProperty=nameWithType>, когда содержимое типизируется как `xs:gMonthDay`.</span><span class="sxs-lookup"><span data-stu-id="11921-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="11921-126">Значение свойства <xref:System.DateTime.Year%2A?displayProperty=nameWithType> в этом случае всегда устанавливается равным 1904.</span><span class="sxs-lookup"><span data-stu-id="11921-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="11921-127">Типы данных xs:anyURI и System.Uri</span><span class="sxs-lookup"><span data-stu-id="11921-127">xs:anyURI and System.Uri</span></span>  

 <span data-ttu-id="11921-128">Когда экземпляр `xs:anyURI`, представляющий относительный идентификатор URI, сопоставляется с объектом <xref:System.Uri>, объект <xref:System.Uri> не имеет базового идентификатора URI.</span><span class="sxs-lookup"><span data-stu-id="11921-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11921-129">См. также</span><span class="sxs-lookup"><span data-stu-id="11921-129">See also</span></span>

- [<span data-ttu-id="11921-130">Поддержка типов в классах System.Xml</span><span class="sxs-lookup"><span data-stu-id="11921-130">Type Support in the System.Xml Classes</span></span>](type-support-in-the-system-xml-classes.md)
