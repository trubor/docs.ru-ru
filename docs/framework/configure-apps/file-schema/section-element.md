---
description: Дополнительные сведения <section> element
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 7756f7ee3be2391a0d068708f3719083640b5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639943"
---
# <a name="section-element"></a><span data-ttu-id="c2d61-104">Элемент \<section></span><span class="sxs-lookup"><span data-stu-id="c2d61-104">\<section> element</span></span>

<span data-ttu-id="c2d61-105">Содержит объявление раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c2d61-105">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="c2d61-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2d61-106">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="c2d61-107">Требуемые атрибуты</span><span class="sxs-lookup"><span data-stu-id="c2d61-107">Required attributes</span></span>

|           | <span data-ttu-id="c2d61-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c2d61-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c2d61-109">**name**</span><span class="sxs-lookup"><span data-stu-id="c2d61-109">**name**</span></span>  | <span data-ttu-id="c2d61-110">Задает имя раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c2d61-110">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="c2d61-111">**type**</span><span class="sxs-lookup"><span data-stu-id="c2d61-111">**type**</span></span>  | <span data-ttu-id="c2d61-112">Указывает имя класса обработчика раздела конфигурации, считывающего раздел из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c2d61-112">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="c2d61-113">Значение типа имеет синтаксис "полное имя-раздела-класса-обработчика", простое-Assembly-Name ".</span><span class="sxs-lookup"><span data-stu-id="c2d61-113">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="c2d61-114">В качестве простого имени сборки используется имя корневого файла без расширения *DLL* .</span><span class="sxs-lookup"><span data-stu-id="c2d61-114">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="c2d61-115">Необязательные атрибуты</span><span class="sxs-lookup"><span data-stu-id="c2d61-115">Optional attributes</span></span>

<span data-ttu-id="c2d61-116">Следующие атрибуты применимы только для приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c2d61-116">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="c2d61-117">Система конфигурации пропускает эти атрибуты для других типов приложений.</span><span class="sxs-lookup"><span data-stu-id="c2d61-117">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="c2d61-118">Описание</span><span class="sxs-lookup"><span data-stu-id="c2d61-118">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="c2d61-119">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="c2d61-119">**allowDefinition**</span></span> | <span data-ttu-id="c2d61-120">Указывает файл конфигурации, в котором может использоваться раздел.</span><span class="sxs-lookup"><span data-stu-id="c2d61-120">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="c2d61-121">Используйте одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="c2d61-121">Use one of the following values:</span></span><br><br><span data-ttu-id="c2d61-122">**Везде**</span><span class="sxs-lookup"><span data-stu-id="c2d61-122">**Everywhere**</span></span><br><span data-ttu-id="c2d61-123">Позволяет использовать раздел в любом файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c2d61-123">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="c2d61-124">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c2d61-124">This is the default.</span></span><br><span data-ttu-id="c2d61-125">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="c2d61-125">**MachineOnly**</span></span><br><span data-ttu-id="c2d61-126">Позволяет использовать раздел только в файле конфигурации компьютера (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="c2d61-126">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="c2d61-127">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="c2d61-127">**MachineToApplication**</span></span><br><span data-ttu-id="c2d61-128">Позволяет использовать раздел в файле конфигурации компьютера или файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="c2d61-128">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="c2d61-129">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="c2d61-129">**allowLocation**</span></span>   | <span data-ttu-id="c2d61-130">Определяет, можно ли использовать раздел в **\<location>** элементе.</span><span class="sxs-lookup"><span data-stu-id="c2d61-130">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="c2d61-131">Используйте одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="c2d61-131">Use one of the following values:</span></span><br><br><span data-ttu-id="c2d61-132">**true**</span><span class="sxs-lookup"><span data-stu-id="c2d61-132">**true**</span></span><br><span data-ttu-id="c2d61-133">Позволяет использовать раздел внутри **\<location>** элемента.</span><span class="sxs-lookup"><span data-stu-id="c2d61-133">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="c2d61-134">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c2d61-134">This is the default.</span></span><br><span data-ttu-id="c2d61-135">**false**</span><span class="sxs-lookup"><span data-stu-id="c2d61-135">**false**</span></span><br><span data-ttu-id="c2d61-136">Не позволяет использовать раздел внутри **\<location>** элемента.</span><span class="sxs-lookup"><span data-stu-id="c2d61-136">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="c2d61-137">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c2d61-137">Parent elements</span></span>

|     | <span data-ttu-id="c2d61-138">Описание</span><span class="sxs-lookup"><span data-stu-id="c2d61-138">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c2d61-139">**\<configSections>** Элемент</span><span class="sxs-lookup"><span data-stu-id="c2d61-139">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="c2d61-140">Содержит раздел конфигурации и объявления пространств имен.</span><span class="sxs-lookup"><span data-stu-id="c2d61-140">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="c2d61-141">**\<sectionGroup>** Дерев</span><span class="sxs-lookup"><span data-stu-id="c2d61-141">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c2d61-142">Определяет пространство имен для разделов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c2d61-142">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="c2d61-143">**\<section>** Элемент — это дочерний элемент либо, либо, **\<configSections>** **\<sectionGroup>** но не оба.</span><span class="sxs-lookup"><span data-stu-id="c2d61-143">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="c2d61-144">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c2d61-144">Child elements</span></span>

<span data-ttu-id="c2d61-145">None</span><span class="sxs-lookup"><span data-stu-id="c2d61-145">None</span></span>

## <a name="remarks"></a><span data-ttu-id="c2d61-146">Remarks</span><span class="sxs-lookup"><span data-stu-id="c2d61-146">Remarks</span></span>

<span data-ttu-id="c2d61-147">Объявление раздела конфигурации фактически определяет новый элемент для файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c2d61-147">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="c2d61-148">Новый элемент содержит параметры, которые обработчик раздела конфигурации (то есть класс, реализующий <xref:System.Configuration.IConfigurationSectionHandler> интерфейс) считывает.</span><span class="sxs-lookup"><span data-stu-id="c2d61-148">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="c2d61-149">Атрибуты и дочерние элементы определяемого раздела зависят от обработчика раздела, используемого для чтения параметров.</span><span class="sxs-lookup"><span data-stu-id="c2d61-149">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="c2d61-150">Объявление обработчика раздела конфигурации в файле *Machine.config* позволяет использовать раздел конфигурации в любом файле конфигурации приложения на этом компьютере, если в атрибуте **allowDefinition** не указано иное.</span><span class="sxs-lookup"><span data-stu-id="c2d61-150">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="c2d61-151">Пример</span><span class="sxs-lookup"><span data-stu-id="c2d61-151">Example</span></span>

<span data-ttu-id="c2d61-152">В следующем примере показано, как определить раздел конфигурации и определить параметры для этого раздела.</span><span class="sxs-lookup"><span data-stu-id="c2d61-152">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c2d61-153">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="c2d61-153">Configuration file</span></span>

<span data-ttu-id="c2d61-154">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="c2d61-154">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2d61-155">См. также</span><span class="sxs-lookup"><span data-stu-id="c2d61-155">See also</span></span>

- [<span data-ttu-id="c2d61-156">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c2d61-156">Configuration file schema for the .NET Framework</span></span>](index.md)
