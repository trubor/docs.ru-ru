---
description: 'Дополнительные сведения о: <clear> Element для <appSettings>'
title: Элемент <clear> для <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 88c6a02441c038619cb74947c024de7712189915
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699341"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="07d67-103">Элемент \<clear> для \<appSettings></span><span class="sxs-lookup"><span data-stu-id="07d67-103">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="07d67-104">Удаляет пользовательские параметры приложения.</span><span class="sxs-lookup"><span data-stu-id="07d67-104">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="07d67-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07d67-105">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="07d67-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="07d67-106">Attributes</span></span>

<span data-ttu-id="07d67-107">None</span><span class="sxs-lookup"><span data-stu-id="07d67-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="07d67-108">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="07d67-108">Parent element</span></span>

|     | <span data-ttu-id="07d67-109">Описание</span><span class="sxs-lookup"><span data-stu-id="07d67-109">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="07d67-110">Содержит пользовательские параметры приложения, такие как пути к файлам, URL-адреса XML или другие сведения о конфигурации пользовательских приложений.</span><span class="sxs-lookup"><span data-stu-id="07d67-110">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="07d67-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="07d67-111">Child elements</span></span>

<span data-ttu-id="07d67-112">None</span><span class="sxs-lookup"><span data-stu-id="07d67-112">None</span></span>

## <a name="example"></a><span data-ttu-id="07d67-113">Пример</span><span class="sxs-lookup"><span data-stu-id="07d67-113">Example</span></span>

<span data-ttu-id="07d67-114">В следующем примере показано, как удалить настраиваемые параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="07d67-114">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="07d67-115">См. также</span><span class="sxs-lookup"><span data-stu-id="07d67-115">See also</span></span>

- [<span data-ttu-id="07d67-116">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07d67-116">Configuration file schema for the .NET Framework</span></span>](../index.md)
