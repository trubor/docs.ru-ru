---
description: 'Узнайте подробнее о: XML-документы и данные'
title: XML-документы и данные
ms.date: 03/30/2017
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: c2f64c218f2f6051f27087a98616b17e57583f75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713667"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="857d5-103">XML-документы и данные</span><span class="sxs-lookup"><span data-stu-id="857d5-103">XML Documents and Data</span></span>

<span data-ttu-id="857d5-104">Платформа .NET Framework имеет всеобъемлющий и интегрированный набор классов, с помощью которых можно легко создавать приложения, использующие XML.</span><span class="sxs-lookup"><span data-stu-id="857d5-104">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="857d5-105">Классы из следующих пространств имен поддерживают синтаксический анализ и запись XML-кода, изменение XML-данных в памяти, проверку данных и преобразование XSLT.</span><span class="sxs-lookup"><span data-stu-id="857d5-105">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

<span data-ttu-id="857d5-106">Чтобы получить полный список, выполните поиск System.Xml в [браузере API .NET](../../../../api/index.md?term=system.xml).</span><span class="sxs-lookup"><span data-stu-id="857d5-106">For a full list, search for "System.Xml" on the [.NET API browser](../../../../api/index.md?term=system.xml).</span></span>

<span data-ttu-id="857d5-107">Классы из этих пространств имен поддерживают рекомендации W3C.</span><span class="sxs-lookup"><span data-stu-id="857d5-107">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="857d5-108">Пример:</span><span class="sxs-lookup"><span data-stu-id="857d5-108">For example:</span></span>

- <span data-ttu-id="857d5-109">Класс <xref:System.Xml.XmlDocument?displayProperty=nameWithType> реализует рекомендации модели W3C [DOM базового уровня 1](https://www.w3.org/TR/REC-DOM-Level-1/) и [DOM базового уровня 2](https://www.w3.org/TR/DOM-Level-2-Core/).</span><span class="sxs-lookup"><span data-stu-id="857d5-109">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>

- <span data-ttu-id="857d5-110">Классы <xref:System.Xml.XmlReader?displayProperty=nameWithType> и <xref:System.Xml.XmlWriter?displayProperty=nameWithType> поддерживают рекомендации [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) и [Пространства имен в XML](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="857d5-110">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>

- <span data-ttu-id="857d5-111">Схемы в классе <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> поддерживают рекомендации в разделах [Схема XML W3C, часть 1. Структуры](https://www.w3.org/TR/xmlschema-1/) и [Схема XML, часть 2. Типы данных](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="857d5-111">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>

- <span data-ttu-id="857d5-112">Классы в пространстве имен <xref:System.Xml.Xsl?displayProperty=nameWithType> поддерживают преобразования XSLT, соответствующие рекомендациям [W3C XSLT 1.0](https://www.w3.org/TR/xslt).</span><span class="sxs-lookup"><span data-stu-id="857d5-112">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>

<span data-ttu-id="857d5-113">Классы XML в платформе .NET Framework предоставляют следующие преимущества.</span><span class="sxs-lookup"><span data-stu-id="857d5-113">The XML classes in the .NET Framework provide these benefits:</span></span>

- <span data-ttu-id="857d5-114">**Производительность**</span><span class="sxs-lookup"><span data-stu-id="857d5-114">**Productivity.**</span></span> <span data-ttu-id="857d5-115">[LINQ to XML (C#)](../../linq/linq-xml-overview.md) и [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) упрощает программирование с использованием XML и обеспечивает работу с запросами, похожую на работу в SQL.</span><span class="sxs-lookup"><span data-stu-id="857d5-115">[LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>

- <span data-ttu-id="857d5-116">**Расширяемость**</span><span class="sxs-lookup"><span data-stu-id="857d5-116">**Extensibility.**</span></span> <span data-ttu-id="857d5-117">XML-классы в .NET Framework являются расширяемыми, что было достигнуто за счет использования абстрактных базовых классов и виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="857d5-117">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="857d5-118">Например, можно создать класс, производный от класса <xref:System.Xml.XmlUrlResolver>, который будет сохранять поток кэширования на локальном диске.</span><span class="sxs-lookup"><span data-stu-id="857d5-118">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>

- <span data-ttu-id="857d5-119">**Модульная архитектура**</span><span class="sxs-lookup"><span data-stu-id="857d5-119">**Pluggable architecture.**</span></span> <span data-ttu-id="857d5-120">Платформа .NET Framework обеспечивает архитектуру, в которой компоненты могут использовать друг друга, а данные можно передавать в потоках между компонентами.</span><span class="sxs-lookup"><span data-stu-id="857d5-120">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="857d5-121">Например, хранилище данных, такое как объект <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument>, можно преобразовать с помощью класса <xref:System.Xml.Xsl.XslCompiledTransform>, а выходные данные затем могут быть переданы в виде потока в другое хранилище или возвращены в виде потока из веб-службы XML.</span><span class="sxs-lookup"><span data-stu-id="857d5-121">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>

- <span data-ttu-id="857d5-122">**Производительность.**</span><span class="sxs-lookup"><span data-stu-id="857d5-122">**Performance.**</span></span> <span data-ttu-id="857d5-123">С целью повышения быстродействия приложений некоторые XML-классы в .NET Framework поддерживают модель на основе потоковой передачи со следующими характеристиками.</span><span class="sxs-lookup"><span data-stu-id="857d5-123">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>

  - <span data-ttu-id="857d5-124">Минимальное кэширование для анализа по запросу в однопроходном режиме (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="857d5-124">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="857d5-125">Проверка в однопроходном режиме (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="857d5-125">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="857d5-126">Навигация, аналогичная курсорам, которая сводит создание узлов к минимуму (до одного виртуального узла) и обеспечивает произвольный доступ к документу (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="857d5-126">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>

  <span data-ttu-id="857d5-127">В случае если требуется обработка XSLT, для повышения производительности можно использовать класс <xref:System.Xml.XPath.XPathDocument>, который является оптимизированным хранилищем «только для чтения» для запросов XPath, обеспечивающих эффективное взаимодействие с классом <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="857d5-127">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

- <span data-ttu-id="857d5-128">**Интеграция с ADO.NET**</span><span class="sxs-lookup"><span data-stu-id="857d5-128">**Integration with ADO.NET.**</span></span> <span data-ttu-id="857d5-129">Классы XML и [ADO.NET](../../../framework/data/adonet/index.md) тесно интегрированы для сведения воедино реляционных данных и XML.</span><span class="sxs-lookup"><span data-stu-id="857d5-129">The XML classes and [ADO.NET](../../../framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="857d5-130">Класс <xref:System.Data.DataSet> представляет собой кэш «в памяти» для данных, полученных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="857d5-130">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="857d5-131">Класс <xref:System.Data.DataSet> позволяет считывать и записывать код XML с помощью классов <xref:System.Xml.XmlReader> и <xref:System.Xml.XmlWriter>, сохранять внутреннюю реляционную структуру в виде схем XML (XSD) и логически выводить структуру схем XML-документов.</span><span class="sxs-lookup"><span data-stu-id="857d5-131">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="857d5-132">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="857d5-132">In This Section</span></span>

<span data-ttu-id="857d5-133">[Варианты обработки XML-данных](xml-processing-options.md) Обсуждаются параметры обработки XML-данных.</span><span class="sxs-lookup"><span data-stu-id="857d5-133">[XML Processing Options](xml-processing-options.md) Discusses options for processing XML data.</span></span>

<span data-ttu-id="857d5-134">[Обработка XML-данных в памяти](processing-xml-data-in-memory.md) Содержит обсуждение трех моделей обработки XML-данных в памяти: [LINQ to XML (C#)](../../linq/linq-xml-overview.md) и [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md), класс <xref:System.Xml.XmlDocument> (основанный на модели W3C DOM) и класс <xref:System.Xml.XPath.XPathDocument> (основанный на модели данных XPath).</span><span class="sxs-lookup"><span data-stu-id="857d5-134">[Processing XML Data In-Memory](processing-xml-data-in-memory.md) Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>

<span data-ttu-id="857d5-135">[Преобразования XSLT](xslt-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="857d5-135">[XSLT Transformations](xslt-transformations.md)</span></span>\
<span data-ttu-id="857d5-136">Описывается, как использовать обработчик XSLT.</span><span class="sxs-lookup"><span data-stu-id="857d5-136">Describes how to use the XSLT processor.</span></span>

<span data-ttu-id="857d5-137">[Модель объектов схемы XML (SOM)](xml-schema-object-model-som.md)</span><span class="sxs-lookup"><span data-stu-id="857d5-137">[XML Schema Object Model (SOM)](xml-schema-object-model-som.md)</span></span>\
<span data-ttu-id="857d5-138">Описываются классы, используемые для построения схем XML (XSD-файлов) и работы с ними, используя класс <xref:System.Xml.Schema.XmlSchema> для загрузки и изменения схемы.</span><span class="sxs-lookup"><span data-stu-id="857d5-138">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>

<span data-ttu-id="857d5-139">[Интеграция XML с реляционными данными и ADO.NET](xml-integration-with-relational-data-and-adonet.md)</span><span class="sxs-lookup"><span data-stu-id="857d5-139">[XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md)</span></span>\
<span data-ttu-id="857d5-140">Описывается, как платформа .NET Framework реализует синхронный доступ в режиме реального времени к данным в реляционном и иерархическом представлении с помощью объектов <xref:System.Data.DataSet> и <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="857d5-140">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>

<span data-ttu-id="857d5-141">[Управление пространствами имен в XML-документе](managing-namespaces-in-an-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="857d5-141">[Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md)</span></span>\
<span data-ttu-id="857d5-142">Описывает использование класса <xref:System.Xml.XmlNamespaceManager> для хранения и ведения информации о пространствах имен.</span><span class="sxs-lookup"><span data-stu-id="857d5-142">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>

<span data-ttu-id="857d5-143">[Поддержка типов в классах System.Xml](type-support-in-the-system-xml-classes.md)</span><span class="sxs-lookup"><span data-stu-id="857d5-143">[Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md)</span></span>\
<span data-ttu-id="857d5-144">Описывает сопоставление типов данных XML с типами CLR, преобразование типов данных XML и другие возможности по работе с типами, которые есть в классах <xref:System.Xml>.</span><span class="sxs-lookup"><span data-stu-id="857d5-144">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>

## <a name="related-sections"></a><span data-ttu-id="857d5-145">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="857d5-145">Related Sections</span></span>

<span data-ttu-id="857d5-146">[ADO.NET](../../../framework/data/adonet/index.md)</span><span class="sxs-lookup"><span data-stu-id="857d5-146">[ADO.NET](../../../framework/data/adonet/index.md)</span></span>\
<span data-ttu-id="857d5-147">Приводятся сведения о доступе к данным с помощью ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="857d5-147">Provides information on how to access data using ADO.NET.</span></span>

<span data-ttu-id="857d5-148">[Безопасность](../../security/index.md)</span><span class="sxs-lookup"><span data-stu-id="857d5-148">[Security](../../security/index.md)</span></span>\
<span data-ttu-id="857d5-149">Приводятся общие сведения о системе безопасности в платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="857d5-149">Provides an overview of the .NET Framework security system.</span></span>
