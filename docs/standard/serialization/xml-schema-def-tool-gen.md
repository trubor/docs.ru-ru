---
title: Практическое руководство. Использование инструмента определения схемы XML для создания классов и документов схемы XML
description: Узнайте, как использовать средство определения схемы XML для создания схемы XML, которая описывает класс, или для создания класса, определенного схемой XML.
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 9d94ed7c2558b1d60efb8b3cdbaac1ea1f0087b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676664"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="3100e-103">Практическое руководство. Использование инструмента определения схемы XML для создания классов и документов схемы XML</span><span class="sxs-lookup"><span data-stu-id="3100e-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>

<span data-ttu-id="3100e-104">С помощью инструмента определения схемы XML (Xsd.exe) можно создать схему XML, которая описывает класс, или создать класс, определенный схемой XML.</span><span class="sxs-lookup"><span data-stu-id="3100e-104">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="3100e-105">В процедурах ниже показана методика выполнения таких операций.</span><span class="sxs-lookup"><span data-stu-id="3100e-105">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="3100e-106">Инструмент определения схемы XML (Xsd.exe) обычно можно найти по следующему пути:</span><span class="sxs-lookup"><span data-stu-id="3100e-106">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="3100e-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{версия}\\bin\\NETFX {версия} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="3100e-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="3100e-108">Создание классов, соответствующих определенной схеме</span><span class="sxs-lookup"><span data-stu-id="3100e-108">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="3100e-109">Откройте окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="3100e-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="3100e-110">Передайте схему XML как аргумент в инструмент определения схемы XML, который создаст набор классов, точно соответствующих схеме XML, например:</span><span class="sxs-lookup"><span data-stu-id="3100e-110">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="3100e-111">Средство может обрабатывать только схемы, которые ссылаются на спецификацию XML консорциума W3C от 16 марта 2001 г.</span><span class="sxs-lookup"><span data-stu-id="3100e-111">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="3100e-112">Иными словами, пространство имен схемы XML должно иметь вид "http://www.w3.org/2001/XMLSchema", как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3100e-112">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="3100e-113">При необходимости измените классы с методами, свойствами или полями.</span><span class="sxs-lookup"><span data-stu-id="3100e-113">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="3100e-114">Дополнительные сведения об изменении класса с помощью атрибутов см. в разделах [Управление сериализацией XML с использованием атрибутов](controlling-xml-serialization-using-attributes.md) и [Атрибуты управления сериализацией с кодировкой SOAP](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="3100e-114">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="3100e-115">Часто бывает полезным изучить схему потока XML, которая генерируется при сериализации экземпляров класса (или классов).</span><span class="sxs-lookup"><span data-stu-id="3100e-115">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="3100e-116">Например, можно опубликовать схему для совместного использования или сравнить ее со схемой, в которой предпринимается попытка обеспечения соответствия.</span><span class="sxs-lookup"><span data-stu-id="3100e-116">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="3100e-117">Создание документа схемы XML из набора классов</span><span class="sxs-lookup"><span data-stu-id="3100e-117">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="3100e-118">Скомпилируйте класс или классы в библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="3100e-118">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="3100e-119">Откройте окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="3100e-119">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="3100e-120">Передайте библиотеку DLL как аргумент в Xsd.exe, например:</span><span class="sxs-lookup"><span data-stu-id="3100e-120">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="3100e-121">В результате записывается схема (или схемы), которая начинается с имени "schema0.xsd".</span><span class="sxs-lookup"><span data-stu-id="3100e-121">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3100e-122">См. также</span><span class="sxs-lookup"><span data-stu-id="3100e-122">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="3100e-123">Инструмент определения схемы XML и сериализация XML</span><span class="sxs-lookup"><span data-stu-id="3100e-123">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="3100e-124">Введение в сериализацию XML</span><span class="sxs-lookup"><span data-stu-id="3100e-124">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="3100e-125">Инструмент определения схемы XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="3100e-125">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="3100e-126">Практическое руководство. Сериализация объекта</span><span class="sxs-lookup"><span data-stu-id="3100e-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="3100e-127">Практическое руководство. Десериализация объекта</span><span class="sxs-lookup"><span data-stu-id="3100e-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
