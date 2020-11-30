---
title: Элемент <dateTimeSerialization>
description: В этой статье описывается элемент <dateTimeSerialization>, который определяет режим сериализации объектов DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 1623517e66955c14b7e738c860ec16086fe30429
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678978"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="44892-103">Элемент \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="44892-103">\<dateTimeSerialization> Element</span></span>

<span data-ttu-id="44892-104">Определяет режим сериализации объектов <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="44892-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="44892-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44892-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44892-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="44892-106">Attributes and Elements</span></span>  

 <span data-ttu-id="44892-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="44892-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44892-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="44892-108">Attributes</span></span>  
  
|<span data-ttu-id="44892-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="44892-109">Attributes</span></span>|<span data-ttu-id="44892-110">Описание</span><span class="sxs-lookup"><span data-stu-id="44892-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="44892-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="44892-111">Optional.</span></span> <span data-ttu-id="44892-112">Задает режим сериализации.</span><span class="sxs-lookup"><span data-stu-id="44892-112">Specifies the serialization mode.</span></span> <span data-ttu-id="44892-113">Задайте одно из значений <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="44892-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="44892-114">Значение по умолчанию: **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="44892-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44892-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="44892-115">Child Elements</span></span>  

 <span data-ttu-id="44892-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="44892-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44892-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="44892-117">Parent Elements</span></span>  
  
|<span data-ttu-id="44892-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="44892-118">Element</span></span>|<span data-ttu-id="44892-119">Описание</span><span class="sxs-lookup"><span data-stu-id="44892-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44892-120">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="44892-120">system.xml.serialization</span></span>|<span data-ttu-id="44892-121">Элемент верхнего уровня для управления XML-сериализацией.</span><span class="sxs-lookup"><span data-stu-id="44892-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44892-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="44892-122">Remarks</span></span>  

<span data-ttu-id="44892-123">Если этому свойству присвоить значение **Local**, объекты <xref:System.DateTime> будут всегда иметь формат местного времени.</span><span class="sxs-lookup"><span data-stu-id="44892-123">When this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="44892-124">Это значит, что в сериализованные данные всегда включается информация о местном часовом поясе.</span><span class="sxs-lookup"><span data-stu-id="44892-124">That is, local time zone information is always included with the serialized data.</span></span>
  
<span data-ttu-id="44892-125">Если для этого свойства задано значение **Roundtrip**, объекты <xref:System.DateTime> анализируются с целью выяснить, указан ли в них местный часовой пояс, время UTC или часовой пояс не указан.</span><span class="sxs-lookup"><span data-stu-id="44892-125">When this property is set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="44892-126">После этого объекты <xref:System.DateTime> сериализуются способом, обеспечивающим сохранение этой информации.</span><span class="sxs-lookup"><span data-stu-id="44892-126">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="44892-127">Это является поведением по умолчанию, рекомендуемым для всех новых приложений, не взаимодействующих со старыми версиями платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44892-127">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44892-128">См. также</span><span class="sxs-lookup"><span data-stu-id="44892-128">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="44892-129">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="44892-129">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="44892-130">\<schemaImporterExtensions> Элемент</span><span class="sxs-lookup"><span data-stu-id="44892-130">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="44892-131">Элемент \<add> для \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="44892-131">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="44892-132">\<system.xml.serialization> Элемент</span><span class="sxs-lookup"><span data-stu-id="44892-132">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
