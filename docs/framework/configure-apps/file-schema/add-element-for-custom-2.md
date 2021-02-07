---
description: 'Дополнительные сведения о: <add> Element для NameValueSectionHandler и DictionarySectionHandler'
title: <add> элемент для NameValueSectionHandler и DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 5a8cf22b21370e60086408f792f8137386d07aa3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713056"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="0bf59-103">\<add> элемент для NameValueSectionHandler и DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="0bf59-103">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="0bf59-104">Добавляет настраиваемые параметры приложения.</span><span class="sxs-lookup"><span data-stu-id="0bf59-104">Adds custom application settings.</span></span> <span data-ttu-id="0bf59-105">Каждый **\<add>** тег содержит пару "ключ-значение".</span><span class="sxs-lookup"><span data-stu-id="0bf59-105">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="0bf59-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0bf59-106">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="0bf59-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0bf59-107">Attributes</span></span>

| <span data-ttu-id="0bf59-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0bf59-108">Attribute</span></span> | <span data-ttu-id="0bf59-109">Описание</span><span class="sxs-lookup"><span data-stu-id="0bf59-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="0bf59-110">**key**</span><span class="sxs-lookup"><span data-stu-id="0bf59-110">**key**</span></span>   | <span data-ttu-id="0bf59-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0bf59-111">Required attribute.</span></span><br><br><span data-ttu-id="0bf59-112">Задает имя параметра.</span><span class="sxs-lookup"><span data-stu-id="0bf59-112">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="0bf59-113">**value**</span><span class="sxs-lookup"><span data-stu-id="0bf59-113">**value**</span></span> | <span data-ttu-id="0bf59-114">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="0bf59-114">Required attribute.</span></span><br><br><span data-ttu-id="0bf59-115">Задает значение параметра.</span><span class="sxs-lookup"><span data-stu-id="0bf59-115">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="0bf59-116">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="0bf59-116">Parent element</span></span>

| <span data-ttu-id="0bf59-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="0bf59-117">Element</span></span> | <span data-ttu-id="0bf59-118">Описание</span><span class="sxs-lookup"><span data-stu-id="0bf59-118">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="0bf59-119">**\<sectionName>** Элемент</span><span class="sxs-lookup"><span data-stu-id="0bf59-119">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="0bf59-120">Определяет параметры для пользовательских разделов конфигурации, использующих <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> классы и.</span><span class="sxs-lookup"><span data-stu-id="0bf59-120">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0bf59-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0bf59-121">Child elements</span></span>

<span data-ttu-id="0bf59-122">None</span><span class="sxs-lookup"><span data-stu-id="0bf59-122">None</span></span>

## <a name="example"></a><span data-ttu-id="0bf59-123">Пример</span><span class="sxs-lookup"><span data-stu-id="0bf59-123">Example</span></span>

<span data-ttu-id="0bf59-124">В следующем примере показано, как определить пользовательский раздел конфигурации и использовать **\<add>** элемент для помещения параметров в раздел:</span><span class="sxs-lookup"><span data-stu-id="0bf59-124">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="0bf59-125">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="0bf59-125">Configuration file</span></span>

<span data-ttu-id="0bf59-126">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="0bf59-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bf59-127">См. также</span><span class="sxs-lookup"><span data-stu-id="0bf59-127">See also</span></span>

- [<span data-ttu-id="0bf59-128">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0bf59-128">Configuration file schema for the .NET Framework</span></span>](index.md)
