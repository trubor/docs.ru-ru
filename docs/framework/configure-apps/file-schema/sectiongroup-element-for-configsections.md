---
description: 'Дополнительные сведения о: <sectionGroup> Element для <configSections>'
title: Элемент <sectionGroup> для <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: 0d822b98acbc041b9d6e146e9cd15848a73d2f88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639891"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="24e93-103">Элемент \<sectionGroup> для \<configSections></span><span class="sxs-lookup"><span data-stu-id="24e93-103">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="24e93-104">Определяет пространство имен для разделов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="24e93-104">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="24e93-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="24e93-105">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="24e93-106">attribute</span><span class="sxs-lookup"><span data-stu-id="24e93-106">Attribute</span></span>

|           | <span data-ttu-id="24e93-107">Описание</span><span class="sxs-lookup"><span data-stu-id="24e93-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="24e93-108">**name**</span><span class="sxs-lookup"><span data-stu-id="24e93-108">**name**</span></span>  | <span data-ttu-id="24e93-109">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="24e93-109">Required attribute.</span></span><br><br><span data-ttu-id="24e93-110">Указывает имя определяемой группы разделов.</span><span class="sxs-lookup"><span data-stu-id="24e93-110">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="24e93-111">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="24e93-111">Parent element</span></span>

|     | <span data-ttu-id="24e93-112">Описание</span><span class="sxs-lookup"><span data-stu-id="24e93-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="24e93-113">**\<configSections>** Элемент</span><span class="sxs-lookup"><span data-stu-id="24e93-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="24e93-114">Содержит раздел конфигурации и объявления пространств имен.</span><span class="sxs-lookup"><span data-stu-id="24e93-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="24e93-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="24e93-115">Child elements</span></span>

|     | <span data-ttu-id="24e93-116">Описание</span><span class="sxs-lookup"><span data-stu-id="24e93-116">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="24e93-117">Содержит объявление раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="24e93-117">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="24e93-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="24e93-118">Remarks</span></span>

<span data-ttu-id="24e93-119">Объявление группы разделов создает тег контейнера для разделов конфигурации и гарантирует отсутствие конфликтов имен с разделами конфигурации, определенными другими пользователями.</span><span class="sxs-lookup"><span data-stu-id="24e93-119">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="24e93-120">Элементы можно вкладывать **\<sectionGroup>** друг в друга.</span><span class="sxs-lookup"><span data-stu-id="24e93-120">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="24e93-121">Пример</span><span class="sxs-lookup"><span data-stu-id="24e93-121">Example</span></span>

<span data-ttu-id="24e93-122">В следующем примере показано, как объявить группу разделов и объявить разделы в группе разделов:</span><span class="sxs-lookup"><span data-stu-id="24e93-122">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="24e93-123">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="24e93-123">Configuration file</span></span>

<span data-ttu-id="24e93-124">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="24e93-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="24e93-125">См. также</span><span class="sxs-lookup"><span data-stu-id="24e93-125">See also</span></span>

- [<span data-ttu-id="24e93-126">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="24e93-126">Configuration file schema for the .NET Framework</span></span>](index.md)
