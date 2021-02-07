---
description: 'Дополнительные сведения о: <clear> Element для NameValueSectionHandler и DictionarySectionHandler'
title: <clear> элемент для NameValueSectionHandler и DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: 896aa7e8f0e3b41574538fcd9e4be9d6155da889
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699237"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="32d7d-103">\<clear> элемент для NameValueSectionHandler и DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="32d7d-103">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="32d7d-104">Удаляет все ранее определенные параметры в разделе.</span><span class="sxs-lookup"><span data-stu-id="32d7d-104">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="32d7d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="32d7d-105">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="32d7d-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="32d7d-106">Attributes</span></span>

<span data-ttu-id="32d7d-107">None</span><span class="sxs-lookup"><span data-stu-id="32d7d-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="32d7d-108">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="32d7d-108">Parent element</span></span>

|     | <span data-ttu-id="32d7d-109">Описание</span><span class="sxs-lookup"><span data-stu-id="32d7d-109">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="32d7d-110">**\<sectionName>** Элемент</span><span class="sxs-lookup"><span data-stu-id="32d7d-110">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="32d7d-111">Определяет параметры для пользовательских разделов конфигурации, использующих <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> классы и.</span><span class="sxs-lookup"><span data-stu-id="32d7d-111">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="32d7d-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="32d7d-112">Child elements</span></span>

<span data-ttu-id="32d7d-113">None</span><span class="sxs-lookup"><span data-stu-id="32d7d-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="32d7d-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="32d7d-114">Remarks</span></span>

<span data-ttu-id="32d7d-115">С помощью элемента можно **\<clear>** удалить из приложения все параметры, которые были определены на более высоком уровне в иерархии файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="32d7d-115">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="32d7d-116">Пример</span><span class="sxs-lookup"><span data-stu-id="32d7d-116">Example</span></span>

<span data-ttu-id="32d7d-117">В этом примере определяется файл конфигурации компьютера и файл конфигурации приложения, а также демонстрируется использование **\<clear>** элемента в файле конфигурации приложения для очистки разделов, ранее определенных в файле конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="32d7d-117">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="32d7d-118">Следующий код файла конфигурации компьютера объявляет раздел **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="32d7d-118">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="32d7d-119">Следующий код файла конфигурации приложения удаляет все параметры из **\<mySection>** .</span><span class="sxs-lookup"><span data-stu-id="32d7d-119">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="32d7d-120">Приложение не может получить параметры, которые были объявлены в в **\<mySection>** разделе файла конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="32d7d-120">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="32d7d-121">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="32d7d-121">Configuration file</span></span>

<span data-ttu-id="32d7d-122">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="32d7d-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="32d7d-123">См. также</span><span class="sxs-lookup"><span data-stu-id="32d7d-123">See also</span></span>

- [<span data-ttu-id="32d7d-124">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32d7d-124">Configuration file schema for the .NET Framework</span></span>](index.md)
