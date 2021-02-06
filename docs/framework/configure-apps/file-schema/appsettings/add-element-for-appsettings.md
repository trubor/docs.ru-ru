---
description: 'Дополнительные сведения о: <add> Element для <appSettings>'
title: Элемент <add> для <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: f10ffe517b3b25543bc7baed0c7d2af13f48ab02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652891"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="4ca0a-103">Элемент \<add> для \<appSettings></span><span class="sxs-lookup"><span data-stu-id="4ca0a-103">\<add> element for \<appSettings></span></span>

<span data-ttu-id="4ca0a-104">Добавляет пользовательский параметр приложения.</span><span class="sxs-lookup"><span data-stu-id="4ca0a-104">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="4ca0a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4ca0a-105">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="4ca0a-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4ca0a-106">Attributes</span></span>

|           | <span data-ttu-id="4ca0a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="4ca0a-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4ca0a-108">**key**</span><span class="sxs-lookup"><span data-stu-id="4ca0a-108">**key**</span></span>   | <span data-ttu-id="4ca0a-109">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4ca0a-109">Required attribute.</span></span><br><br><span data-ttu-id="4ca0a-110">Указывает имя добавляемого ключа.</span><span class="sxs-lookup"><span data-stu-id="4ca0a-110">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="4ca0a-111">**value**</span><span class="sxs-lookup"><span data-stu-id="4ca0a-111">**value**</span></span> | <span data-ttu-id="4ca0a-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4ca0a-112">Required attribute.</span></span><br><br><span data-ttu-id="4ca0a-113">Указывает значение добавляемого ключа.</span><span class="sxs-lookup"><span data-stu-id="4ca0a-113">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4ca0a-114">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="4ca0a-114">Parent element</span></span>

|     | <span data-ttu-id="4ca0a-115">Описание</span><span class="sxs-lookup"><span data-stu-id="4ca0a-115">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="4ca0a-116">Содержит пользовательские параметры приложения, такие как пути к файлам, URL-адреса XML-веб-служб и другие сведения о пользовательской конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="4ca0a-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4ca0a-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4ca0a-117">Child elements</span></span>

<span data-ttu-id="4ca0a-118">None</span><span class="sxs-lookup"><span data-stu-id="4ca0a-118">None</span></span>

## <a name="example"></a><span data-ttu-id="4ca0a-119">Пример</span><span class="sxs-lookup"><span data-stu-id="4ca0a-119">Example</span></span>

<span data-ttu-id="4ca0a-120">В следующем примере показано, как добавить настраиваемый параметр конфигурации для имени приложения:</span><span class="sxs-lookup"><span data-stu-id="4ca0a-120">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="4ca0a-121">В следующем примере элемент используется `<add>` для определения двух параметров совместимости в приложении ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="4ca0a-121">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="4ca0a-122">См. также</span><span class="sxs-lookup"><span data-stu-id="4ca0a-122">See also</span></span>

- [<span data-ttu-id="4ca0a-123">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ca0a-123">Configuration file schema for the .NET Framework</span></span>](../index.md)
