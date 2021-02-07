---
description: 'Дополнительные сведения о: <assemblyBinding> Element для <configuration>'
title: Элемент <assemblyBinding> для <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 5cc3fc7cccd4b9dc7b62815734ff76e32e2243d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730113"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="48b21-103">Элемент \<assemblyBinding> для \<configuration></span><span class="sxs-lookup"><span data-stu-id="48b21-103">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="48b21-104">Определяет политику привязки сборок на уровне конфигурации.</span><span class="sxs-lookup"><span data-stu-id="48b21-104">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="48b21-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="48b21-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="48b21-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="48b21-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="48b21-107">attribute</span><span class="sxs-lookup"><span data-stu-id="48b21-107">Attribute</span></span>

|           | <span data-ttu-id="48b21-108">Описание</span><span class="sxs-lookup"><span data-stu-id="48b21-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="48b21-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="48b21-109">**xmlns**</span></span> | <span data-ttu-id="48b21-110">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="48b21-110">Required attribute.</span></span><br><br><span data-ttu-id="48b21-111">Задает пространство имен XML, необходимое для привязки сборок.</span><span class="sxs-lookup"><span data-stu-id="48b21-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="48b21-112">Используйте строку urn:schemas-microsoft-com:asm.v1 в качестве значения.</span><span class="sxs-lookup"><span data-stu-id="48b21-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="48b21-113">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="48b21-113">Parent element</span></span>

|     | <span data-ttu-id="48b21-114">Описание</span><span class="sxs-lookup"><span data-stu-id="48b21-114">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="48b21-115">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48b21-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="48b21-116">Дочерний элемент</span><span class="sxs-lookup"><span data-stu-id="48b21-116">Child element</span></span>

|     | <span data-ttu-id="48b21-117">Описание</span><span class="sxs-lookup"><span data-stu-id="48b21-117">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="48b21-118">Указание файла конфигурации, который следует включить.</span><span class="sxs-lookup"><span data-stu-id="48b21-118">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="48b21-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="48b21-119">Remarks</span></span>

<span data-ttu-id="48b21-120">[**\<linkedConfiguration>**](linkedconfiguration-element.md)Элемент упрощает управление сборками компонентов, позволяя файлам конфигурации приложения включать файлы конфигурации сборки в хорошо известные расположения, а не дублировать параметры конфигурации сборки.</span><span class="sxs-lookup"><span data-stu-id="48b21-120">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="48b21-121">**\<linkedConfiguration>** Элемент не поддерживается для приложений с параллельными манифестами Windows.</span><span class="sxs-lookup"><span data-stu-id="48b21-121">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="48b21-122">Пример</span><span class="sxs-lookup"><span data-stu-id="48b21-122">Example</span></span>

<span data-ttu-id="48b21-123">В следующем примере показано, как включить файл конфигурации на локальный жесткий диск:</span><span class="sxs-lookup"><span data-stu-id="48b21-123">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="48b21-124">См. также</span><span class="sxs-lookup"><span data-stu-id="48b21-124">See also</span></span>

- [<span data-ttu-id="48b21-125">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48b21-125">Configuration file schema for the .NET Framework</span></span>](index.md)
