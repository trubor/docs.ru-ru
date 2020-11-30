---
title: Элемент <schemaImporterExtensions>
description: Элемент <schemaImporterExtensions> содержит типы, которые XmlSchemaImporter использует для сопоставления типов XSD с типами .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 6b644ed1112b748be4dd301d6fa6f2a6416dc67e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722145"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="c3997-103">Элемент \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="c3997-103">\<schemaImporterExtensions> element</span></span>

<span data-ttu-id="c3997-104">Содержит типы, которые <xref:System.Xml.Serialization.XmlSchemaImporter> использует для сопоставления типов XSD с типами .NET.</span><span class="sxs-lookup"><span data-stu-id="c3997-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span> <span data-ttu-id="c3997-105">Дополнительные сведения о файлах конфигурации см. в разделе [Схема файла конфигурации](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="c3997-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3997-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c3997-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="c3997-107">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c3997-107">Child Elements</span></span>  
  
|<span data-ttu-id="c3997-108">Элемент</span><span class="sxs-lookup"><span data-stu-id="c3997-108">Element</span></span>|<span data-ttu-id="c3997-109">Описание</span><span class="sxs-lookup"><span data-stu-id="c3997-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3997-110">Элемент \<add> для \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="c3997-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="c3997-111">Добавляет типы, используемые <xref:System.Xml.Serialization.XmlSchemaImporter> для создания сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="c3997-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="c3997-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c3997-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c3997-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="c3997-113">Element</span></span>|<span data-ttu-id="c3997-114">Описание</span><span class="sxs-lookup"><span data-stu-id="c3997-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3997-115">\<system.xml.serialization> Элемент</span><span class="sxs-lookup"><span data-stu-id="c3997-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="c3997-116">Элемент верхнего уровня для управления XML-сериализацией.</span><span class="sxs-lookup"><span data-stu-id="c3997-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c3997-117">Пример</span><span class="sxs-lookup"><span data-stu-id="c3997-117">Example</span></span>  

 <span data-ttu-id="c3997-118">В следующем примере кода показано, как добавлять типы, используемые <xref:System.Xml.Serialization.XmlSchemaImporter> при сопоставлении типов XSD с типами .NET.</span><span class="sxs-lookup"><span data-stu-id="c3997-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3997-119">См. также</span><span class="sxs-lookup"><span data-stu-id="c3997-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="c3997-120">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="c3997-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c3997-121">\<dateTimeSerialization> Элемент</span><span class="sxs-lookup"><span data-stu-id="c3997-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="c3997-122">Элемент \<add> для \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="c3997-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="c3997-123">\<system.xml.serialization> Элемент</span><span class="sxs-lookup"><span data-stu-id="c3997-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
