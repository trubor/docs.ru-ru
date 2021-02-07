---
description: 'Дополнительные сведения о: <remove> Element для NameValueSectionHandler и DictionarySectionHandler'
title: <remove> элемент для NameValueSectionHandler и DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: bf1434b257aa014c8f46e34f2d57d109bd510452
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740084"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="f2215-103">\<remove> элемент для NameValueSectionHandler и DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="f2215-103">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="f2215-104">Удаляет ранее определенный параметр.</span><span class="sxs-lookup"><span data-stu-id="f2215-104">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="f2215-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f2215-105">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="f2215-106">attribute</span><span class="sxs-lookup"><span data-stu-id="f2215-106">Attribute</span></span>

|           | <span data-ttu-id="f2215-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f2215-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f2215-108">**key**</span><span class="sxs-lookup"><span data-stu-id="f2215-108">**key**</span></span>   | <span data-ttu-id="f2215-109">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="f2215-109">Required attribute.</span></span><br><br><span data-ttu-id="f2215-110">Задает имя удаляемого параметра.</span><span class="sxs-lookup"><span data-stu-id="f2215-110">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f2215-111">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="f2215-111">Parent element</span></span>

| <span data-ttu-id="f2215-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="f2215-112">Element</span></span> | <span data-ttu-id="f2215-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f2215-113">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="f2215-114">**\<sectionName>** Элемент</span><span class="sxs-lookup"><span data-stu-id="f2215-114">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="f2215-115">Определяет параметры для пользовательских разделов конфигурации, использующих <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> классы и.</span><span class="sxs-lookup"><span data-stu-id="f2215-115">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f2215-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f2215-116">Child elements</span></span>

<span data-ttu-id="f2215-117">None</span><span class="sxs-lookup"><span data-stu-id="f2215-117">None</span></span>

## <a name="remarks"></a><span data-ttu-id="f2215-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="f2215-118">Remarks</span></span>

<span data-ttu-id="f2215-119">С помощью элемента можно **\<remove>** удалить из приложения параметры, которые были определены на более высоком уровне в иерархии файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f2215-119">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="f2215-120">Пример</span><span class="sxs-lookup"><span data-stu-id="f2215-120">Example</span></span>

<span data-ttu-id="f2215-121">В следующем примере показано, как использовать **\<remove>** элемент в файле конфигурации приложения для удаления параметров, ранее определенных в файле конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="f2215-121">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="f2215-122">Следующий код файла конфигурации компьютера объявляет раздел **\<mySection>** и добавляет `key1` `key2` в него два параметра:</span><span class="sxs-lookup"><span data-stu-id="f2215-122">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="f2215-123">Следующий код файла конфигурации приложения удаляет `key2` параметр из **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="f2215-123">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="f2215-124">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="f2215-124">Configuration file</span></span>

<span data-ttu-id="f2215-125">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="f2215-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2215-126">См. также</span><span class="sxs-lookup"><span data-stu-id="f2215-126">See also</span></span>

- [<span data-ttu-id="f2215-127">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f2215-127">Configuration file schema for the .NET Framework</span></span>](index.md)
