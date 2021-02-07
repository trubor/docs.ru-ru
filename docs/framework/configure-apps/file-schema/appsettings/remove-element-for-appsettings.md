---
description: 'Дополнительные сведения о: <remove> Element для <appSettings>'
title: Элемент <remove> для <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: a67003d310377ee4b896843003306201353dae91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699276"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="26424-103">Элемент \<remove> для \<appSettings></span><span class="sxs-lookup"><span data-stu-id="26424-103">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="26424-104">Удаляет пользовательские параметры приложения.</span><span class="sxs-lookup"><span data-stu-id="26424-104">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="26424-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26424-105">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="26424-106">attribute</span><span class="sxs-lookup"><span data-stu-id="26424-106">Attribute</span></span>

|         | <span data-ttu-id="26424-107">Описание</span><span class="sxs-lookup"><span data-stu-id="26424-107">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="26424-108">**key**</span><span class="sxs-lookup"><span data-stu-id="26424-108">**key**</span></span> | <span data-ttu-id="26424-109">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="26424-109">Required attribute.</span></span><br><br><span data-ttu-id="26424-110">Задает имя удаляемого ключа.</span><span class="sxs-lookup"><span data-stu-id="26424-110">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="26424-111">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="26424-111">Parent element</span></span>

|     | <span data-ttu-id="26424-112">Описание</span><span class="sxs-lookup"><span data-stu-id="26424-112">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="26424-113">Содержит пользовательские параметры приложения, такие как пути к файлам, URL-адреса XML-веб-служб и другие сведения о пользовательской конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="26424-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="26424-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="26424-114">Child elements</span></span>

<span data-ttu-id="26424-115">None</span><span class="sxs-lookup"><span data-stu-id="26424-115">None</span></span>

## <a name="example"></a><span data-ttu-id="26424-116">Пример</span><span class="sxs-lookup"><span data-stu-id="26424-116">Example</span></span>

<span data-ttu-id="26424-117">В следующем примере показано, как удалить настраиваемый параметр конфигурации для `ApplicationName` :</span><span class="sxs-lookup"><span data-stu-id="26424-117">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="26424-118">См. также</span><span class="sxs-lookup"><span data-stu-id="26424-118">See also</span></span>

- [<span data-ttu-id="26424-119">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="26424-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
