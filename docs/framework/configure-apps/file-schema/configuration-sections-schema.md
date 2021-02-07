---
description: См. Дополнительные сведения о схеме разделов конфигурации.
title: Схема разделов конфигурации
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: f16ca16417da0b3ee7a7d0a5ebdd1a446ec0714a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698964"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="c94ef-103">Схема разделов конфигурации</span><span class="sxs-lookup"><span data-stu-id="c94ef-103">Configuration sections schema</span></span>

<span data-ttu-id="c94ef-104">Схема разделов конфигурации содержит элементы, определяющие пользовательские параметры в файлах конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c94ef-104">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="c94ef-105">Общие сведения о файлах конфигурации и схемах см. [в разделе Схема файла конфигурации для платформа .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="c94ef-105">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="c94ef-106">Описание</span><span class="sxs-lookup"><span data-stu-id="c94ef-106">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="c94ef-107">Содержит раздел конфигурации и объявления пространств имен.</span><span class="sxs-lookup"><span data-stu-id="c94ef-107">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="c94ef-108">**\<section>** для **\<configSections>** и **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="c94ef-108">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="c94ef-109">Содержит объявление раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c94ef-109">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="c94ef-110">**\<sectionGroup>** предмет **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="c94ef-110">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c94ef-111">Определяет пространство имен для разделов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c94ef-111">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="c94ef-112">Нереализованные элементы</span><span class="sxs-lookup"><span data-stu-id="c94ef-112">Unimplemented elements</span></span>

<span data-ttu-id="c94ef-113">Следующие элементы не влияют на использование и не должны использоваться:</span><span class="sxs-lookup"><span data-stu-id="c94ef-113">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
