---
description: 'Дополнительные сведения: схема параметров приложения'
title: Схема параметров приложения
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: a98a60b0470e0fa2c03313f25de9b310f5fce785
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699354"
---
# <a name="app-settings-schema"></a><span data-ttu-id="88022-103">Схема параметров приложения</span><span class="sxs-lookup"><span data-stu-id="88022-103">App Settings schema</span></span>

<span data-ttu-id="88022-104">Содержит пользовательские параметры приложения, такие как пути к файлам, URL-адреса XML-веб-служб и другие сведения о пользовательской конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="88022-104">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="88022-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="88022-105">Element</span></span> | <span data-ttu-id="88022-106">Описание</span><span class="sxs-lookup"><span data-stu-id="88022-106">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="88022-107">Содержит **\<add>** **\<clear>** теги, и **\<remove>** для управления параметрами приложения.</span><span class="sxs-lookup"><span data-stu-id="88022-107">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="88022-108">Имеет необязательный атрибут **file**.</span><span class="sxs-lookup"><span data-stu-id="88022-108">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="88022-109">Определяет параметр.</span><span class="sxs-lookup"><span data-stu-id="88022-109">Defines a setting.</span></span> <span data-ttu-id="88022-110">Дочерний элемент **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="88022-110">Child of **\<appSettings>**.</span></span> <span data-ttu-id="88022-111">Обязательные атрибуты — **key** и **value**.</span><span class="sxs-lookup"><span data-stu-id="88022-111">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="88022-112">Удаляет все параметры.</span><span class="sxs-lookup"><span data-stu-id="88022-112">Clears all settings.</span></span> <span data-ttu-id="88022-113">Дочерний элемент **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="88022-113">Child of **\<appSettings>**.</span></span> <span data-ttu-id="88022-114">Не имеет атрибутов.</span><span class="sxs-lookup"><span data-stu-id="88022-114">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="88022-115">Удаляет параметр.</span><span class="sxs-lookup"><span data-stu-id="88022-115">Removes a setting.</span></span> <span data-ttu-id="88022-116">Дочерний элемент **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="88022-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="88022-117">Требуется атрибут **key**.</span><span class="sxs-lookup"><span data-stu-id="88022-117">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="88022-118">Элемент \<appSettings></span><span class="sxs-lookup"><span data-stu-id="88022-118">\<appSettings> element</span></span>

<span data-ttu-id="88022-119">Этот элемент содержит **\<add>** **\<clear>** теги, и **\<remove>** для управления параметрами приложения.</span><span class="sxs-lookup"><span data-stu-id="88022-119">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="88022-120">Определяет необязательный атрибут для **file**.</span><span class="sxs-lookup"><span data-stu-id="88022-120">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="88022-121">Элемент \<add></span><span class="sxs-lookup"><span data-stu-id="88022-121">\<add> element</span></span>

<span data-ttu-id="88022-122">Добавляет пользовательский параметр приложения в виде пары "имя-значение" в коллекцию параметров приложения.</span><span class="sxs-lookup"><span data-stu-id="88022-122">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="88022-123">Определяет атрибуты для **key** и **value**.</span><span class="sxs-lookup"><span data-stu-id="88022-123">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="88022-124">Элемент \<clear></span><span class="sxs-lookup"><span data-stu-id="88022-124">\<clear> element</span></span>

<span data-ttu-id="88022-125">Удаляет все ссылки на унаследованные пользовательские параметры приложения и разрешает только ссылки, добавленные **\<add>** элементами после **\<clear>** элемента.</span><span class="sxs-lookup"><span data-stu-id="88022-125">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="88022-126">Атрибуты не определяются.</span><span class="sxs-lookup"><span data-stu-id="88022-126">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="88022-127">Элемент \<remove></span><span class="sxs-lookup"><span data-stu-id="88022-127">\<remove> element</span></span>

<span data-ttu-id="88022-128">Удаляет ссылку на унаследованный пользовательский параметр приложения из коллекции параметров приложения.</span><span class="sxs-lookup"><span data-stu-id="88022-128">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="88022-129">Определяет атрибут для **key**.</span><span class="sxs-lookup"><span data-stu-id="88022-129">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="88022-130">Пример</span><span class="sxs-lookup"><span data-stu-id="88022-130">Example</span></span>

<span data-ttu-id="88022-131">В приведенном ниже примере показан внешний файл параметров приложения (*custom.config*), в котором определен пользовательский параметр приложения.</span><span class="sxs-lookup"><span data-stu-id="88022-131">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="88022-132">В приведенном ниже примере показан файл конфигурации приложения, в котором используется параметр из внешнего файла параметров и задается собственный параметр приложения.</span><span class="sxs-lookup"><span data-stu-id="88022-132">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="88022-133">См. также</span><span class="sxs-lookup"><span data-stu-id="88022-133">See also</span></span>

- [<span data-ttu-id="88022-134">Общие сведения о параметрах приложений</span><span class="sxs-lookup"><span data-stu-id="88022-134">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="88022-135">Архитектура параметров приложения</span><span class="sxs-lookup"><span data-stu-id="88022-135">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
