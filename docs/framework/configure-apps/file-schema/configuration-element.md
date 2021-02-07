---
description: 'Дополнительные сведения о: <configuration> element'
title: <configuration> - элемент
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: ee48a45ddb987201e84213a0d7674da004951ab1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699002"
---
# <a name="configuration-element"></a><span data-ttu-id="aa276-103">Элемент \<configuration></span><span class="sxs-lookup"><span data-stu-id="aa276-103">\<configuration> element</span></span>

<span data-ttu-id="aa276-104">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa276-104">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="aa276-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aa276-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="aa276-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="aa276-106">Attributes</span></span>

<span data-ttu-id="aa276-107">None</span><span class="sxs-lookup"><span data-stu-id="aa276-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="aa276-108">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="aa276-108">Parent element</span></span>

<span data-ttu-id="aa276-109">None</span><span class="sxs-lookup"><span data-stu-id="aa276-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="aa276-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="aa276-110">Child elements</span></span>

|     | <span data-ttu-id="aa276-111">Описание</span><span class="sxs-lookup"><span data-stu-id="aa276-111">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="aa276-112">Определяет политику привязки сборок на уровне конфигурации.</span><span class="sxs-lookup"><span data-stu-id="aa276-112">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="aa276-113">**\<startup>** Схема параметров</span><span class="sxs-lookup"><span data-stu-id="aa276-113">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="aa276-114">Все элементы в схеме параметров запуска.</span><span class="sxs-lookup"><span data-stu-id="aa276-114">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="aa276-115">**\<runtime>** Схема параметров</span><span class="sxs-lookup"><span data-stu-id="aa276-115">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="aa276-116">Все элементы в схеме параметров среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="aa276-116">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="aa276-117">[**\<system.runtime.remoting>** Схема параметров](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aa276-117">[**\<system.runtime.remoting>** Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="aa276-118">Все элементы в схеме параметров удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="aa276-118">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="aa276-119">**\<system.Net>** Схема параметров</span><span class="sxs-lookup"><span data-stu-id="aa276-119">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="aa276-120">Все элементы в схеме параметров сети.</span><span class="sxs-lookup"><span data-stu-id="aa276-120">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="aa276-121">**\<cryptographySettings>** Схема параметров</span><span class="sxs-lookup"><span data-stu-id="aa276-121">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="aa276-122">Все элементы в схеме параметров шифрования.</span><span class="sxs-lookup"><span data-stu-id="aa276-122">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="aa276-123">**\<configuration>** Схема разделов</span><span class="sxs-lookup"><span data-stu-id="aa276-123">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="aa276-124">Все элементы в схеме параметров раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="aa276-124">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="aa276-125">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="aa276-125">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="aa276-126">Все элементы в схеме параметров трассировки и отладки.</span><span class="sxs-lookup"><span data-stu-id="aa276-126">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="aa276-127">[Схема параметров конфигурации ASP.NET](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aa276-127">[ASP.NET Configuration Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="aa276-128">Все элементы в схеме конфигурации ASP.NET, включая элементы для настройки веб-сайтов и приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="aa276-128">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="aa276-129">Используется в файлах *Web.config* .</span><span class="sxs-lookup"><span data-stu-id="aa276-129">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="aa276-130">[**\<webServices>** Схема параметров](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aa276-130">[**\<webServices>** Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="aa276-131">Все элементы в схеме параметров веб-служб.</span><span class="sxs-lookup"><span data-stu-id="aa276-131">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="aa276-132">Схема веб-параметров</span><span class="sxs-lookup"><span data-stu-id="aa276-132">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="aa276-133">Все элементы схемы веб-параметров, в том числе элементы настройки способов работы ASP.NET с ведущими приложениями, такими как службы IIS.</span><span class="sxs-lookup"><span data-stu-id="aa276-133">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="aa276-134">Используется в файлах *aspnet.config* .</span><span class="sxs-lookup"><span data-stu-id="aa276-134">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="aa276-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="aa276-135">Remarks</span></span>

<span data-ttu-id="aa276-136">Каждый файл конфигурации должен содержать ровно один **\<configuration>** элемент.</span><span class="sxs-lookup"><span data-stu-id="aa276-136">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa276-137">См. также</span><span class="sxs-lookup"><span data-stu-id="aa276-137">See also</span></span>

- [<span data-ttu-id="aa276-138">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa276-138">Configuration file schema for the .NET Framework</span></span>](index.md)
