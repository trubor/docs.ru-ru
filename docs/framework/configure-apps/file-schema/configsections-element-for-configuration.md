---
description: 'Дополнительные сведения о: <configSections> Element для <configuration>'
title: Элемент <configSections> для <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 543ceed8d53fd299e8a0b65594592b64d6b833a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698992"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="36d04-103">Элемент \<configSections> для \<configuration></span><span class="sxs-lookup"><span data-stu-id="36d04-103">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="36d04-104">Содержит раздел конфигурации и объявления пространств имен.</span><span class="sxs-lookup"><span data-stu-id="36d04-104">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="36d04-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="36d04-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="36d04-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="36d04-106">Attributes</span></span>

<span data-ttu-id="36d04-107">None</span><span class="sxs-lookup"><span data-stu-id="36d04-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="36d04-108">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="36d04-108">Parent element</span></span>

|     | <span data-ttu-id="36d04-109">Описание</span><span class="sxs-lookup"><span data-stu-id="36d04-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="36d04-110">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36d04-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="36d04-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="36d04-111">Child elements</span></span>

|     | <span data-ttu-id="36d04-112">Описание</span><span class="sxs-lookup"><span data-stu-id="36d04-112">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="36d04-113">Содержит объявление раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="36d04-113">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="36d04-114">Определяет пространство имен для разделов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="36d04-114">Defines a namespace for configuration sections.</span></span> |

## <a name="remarks"></a><span data-ttu-id="36d04-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="36d04-115">Remarks</span></span>

<span data-ttu-id="36d04-116">Если этот элемент находится в файле конфигурации, он должен быть первым дочерним элементом **\<configuration>** элемента.</span><span class="sxs-lookup"><span data-stu-id="36d04-116">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="36d04-117">Пример</span><span class="sxs-lookup"><span data-stu-id="36d04-117">Example</span></span>

<span data-ttu-id="36d04-118">В следующем примере показано, как определить раздел конфигурации и определить параметры для этого раздела.</span><span class="sxs-lookup"><span data-stu-id="36d04-118">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="36d04-119">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="36d04-119">Configuration file</span></span>

<span data-ttu-id="36d04-120">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="36d04-120">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="36d04-121">См. также</span><span class="sxs-lookup"><span data-stu-id="36d04-121">See also</span></span>

- [<span data-ttu-id="36d04-122">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36d04-122">Configuration file schema for the .NET Framework</span></span>](index.md)
