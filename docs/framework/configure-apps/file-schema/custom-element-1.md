---
description: 'Дополнительные сведения о: настраиваемый элемент для Синглетагсектионхандлер'
title: Настраиваемый элемент для Синглетагсектионхандлер
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 83022a1ebf295b89d5f868589e3d9a77c78e3fab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729983"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="634f4-103">Настраиваемый элемент для Синглетагсектионхандлер</span><span class="sxs-lookup"><span data-stu-id="634f4-103">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="634f4-104">Определяет параметры в пользовательском разделе конфигурации, определяемом \<section> элементом, и использует <xref:System.Configuration.SingleTagSectionHandler> класс.</span><span class="sxs-lookup"><span data-stu-id="634f4-104">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="634f4-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="634f4-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="634f4-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="634f4-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="634f4-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="634f4-107">Attributes</span></span>

<span data-ttu-id="634f4-108">Атрибуты и значения атрибутов определяются пользователем.</span><span class="sxs-lookup"><span data-stu-id="634f4-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="634f4-109">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="634f4-109">Parent element</span></span>

|     | <span data-ttu-id="634f4-110">Описание</span><span class="sxs-lookup"><span data-stu-id="634f4-110">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="634f4-111">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="634f4-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="634f4-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="634f4-112">Child elements</span></span>

<span data-ttu-id="634f4-113">None</span><span class="sxs-lookup"><span data-stu-id="634f4-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="634f4-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="634f4-114">Remarks</span></span>

<span data-ttu-id="634f4-115">**\<sectionName>** Элемент является пользовательским элементом, определяемым [**\<section>**](section-element.md) тегом в [**\<configSections>**](configsections-element-for-configuration.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="634f4-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="634f4-116">Система конфигурации возвращает <xref:System.Collections.IDictionary> объект при вызове метода <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="634f4-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="634f4-117">Пример</span><span class="sxs-lookup"><span data-stu-id="634f4-117">Example</span></span>

<span data-ttu-id="634f4-118">В следующем примере объявляется пользовательский элемент с именем **\<sampleSection>** , который содержит параметры, считанные <xref:System.Configuration.SingleTagSectionHandler> классом:</span><span class="sxs-lookup"><span data-stu-id="634f4-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="634f4-119">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="634f4-119">Configuration file</span></span>

<span data-ttu-id="634f4-120">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="634f4-120">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="634f4-121">См. также</span><span class="sxs-lookup"><span data-stu-id="634f4-121">See also</span></span>

- [<span data-ttu-id="634f4-122">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="634f4-122">Configuration file schema for the .NET Framework</span></span>](index.md)
