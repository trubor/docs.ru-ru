---
description: 'Дополнительные сведения о: настраиваемый элемент для NameValueSectionHandler и DictionarySectionHandler'
title: Настраиваемый элемент для NameValueSectionHandler и DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: c1bb5b2fb321e2cc9235e02be2158c0875d42032
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698730"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="e928e-103">Настраиваемый элемент для NameValueSectionHandler и DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="e928e-103">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="e928e-104">Определяет параметры для пользовательских разделов конфигурации, использующих <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> классы и.</span><span class="sxs-lookup"><span data-stu-id="e928e-104">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a><span data-ttu-id="e928e-105">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e928e-105">Attributes</span></span>

<span data-ttu-id="e928e-106">None</span><span class="sxs-lookup"><span data-stu-id="e928e-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="e928e-107">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="e928e-107">Parent element</span></span>

|     | <span data-ttu-id="e928e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e928e-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="e928e-109">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e928e-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e928e-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e928e-110">Child elements</span></span>

|     | <span data-ttu-id="e928e-111">Описание</span><span class="sxs-lookup"><span data-stu-id="e928e-111">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="e928e-112">[**\<add>**](add-element-for-custom-2.md) для <xref:System.Configuration.NameValueSectionHandler> и <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="e928e-112">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="e928e-113">Добавляет настраиваемые параметры приложения.</span><span class="sxs-lookup"><span data-stu-id="e928e-113">Adds custom application settings.</span></span> |
| <span data-ttu-id="e928e-114">[**\<remove>**](remove-element-for-custom-2.md) для <xref:System.Configuration.NameValueSectionHandler> и <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="e928e-114">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="e928e-115">Удаляет ранее определенный параметр.</span><span class="sxs-lookup"><span data-stu-id="e928e-115">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="e928e-116">[**\<clear>**](clear-element-for-custom-2.md) для <xref:System.Configuration.NameValueSectionHandler> и <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="e928e-116">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="e928e-117">Удаляет все ранее определенные параметры в разделе.</span><span class="sxs-lookup"><span data-stu-id="e928e-117">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e928e-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="e928e-118">Remarks</span></span>

<span data-ttu-id="e928e-119">**\<sectionName>** Элемент является пользовательским элементом, определяемым **\<section>** тегом в **\<configSections>** элементе.</span><span class="sxs-lookup"><span data-stu-id="e928e-119">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="e928e-120">В следующей таблице показан тип объекта, возвращаемого методом ConfigurationSettings. config для каждого обработчика раздела конфигурации:</span><span class="sxs-lookup"><span data-stu-id="e928e-120">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="e928e-121">Обработчик раздела конфигурации</span><span class="sxs-lookup"><span data-stu-id="e928e-121">Configuration section handler</span></span>                        | <span data-ttu-id="e928e-122">Возвращаемый тип</span><span class="sxs-lookup"><span data-stu-id="e928e-122">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="e928e-123">Пример</span><span class="sxs-lookup"><span data-stu-id="e928e-123">Example</span></span>

<span data-ttu-id="e928e-124">В следующем примере показано, как объявить разделы, в которых используются <xref:System.Configuration.DictionarySectionHandler> <xref:System.Configuration.NameValueSectionHandler> классы и.</span><span class="sxs-lookup"><span data-stu-id="e928e-124">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="e928e-125">Первый настраиваемый элемент — **\<dictionarySample>** , который содержит параметры, считанные <xref:System.Configuration.DictionarySectionHandler> классом в `System.dll` сборке.</span><span class="sxs-lookup"><span data-stu-id="e928e-125">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="e928e-126">Второй настраиваемый элемент — **\<mySection>** , который содержит параметры, считанные <xref:System.Configuration.NameValueSectionHandler> классом в `System.dll` сборке.</span><span class="sxs-lookup"><span data-stu-id="e928e-126">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="e928e-127">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="e928e-127">Configuration file</span></span>

<span data-ttu-id="e928e-128">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="e928e-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e928e-129">См. также</span><span class="sxs-lookup"><span data-stu-id="e928e-129">See also</span></span>

- [<span data-ttu-id="e928e-130">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e928e-130">Configuration file schema for the .NET Framework</span></span>](index.md)
