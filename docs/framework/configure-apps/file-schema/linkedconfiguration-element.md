---
description: 'Дополнительные сведения о: <linkedConfiguration> element'
title: <linkedConfiguration> - элемент
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: e4312cf788784241efc35304b632dfe1fdef1bc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698665"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="c8c0b-103">Элемент \<linkedConfiguration></span><span class="sxs-lookup"><span data-stu-id="c8c0b-103">\<linkedConfiguration> element</span></span>

<span data-ttu-id="c8c0b-104">Указание файла конфигурации, который следует включить.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-104">Specifies a configuration file to include.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a><span data-ttu-id="c8c0b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c8c0b-105">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="c8c0b-106">attribute</span><span class="sxs-lookup"><span data-stu-id="c8c0b-106">Attribute</span></span>

|           | <span data-ttu-id="c8c0b-107">Описание</span><span class="sxs-lookup"><span data-stu-id="c8c0b-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c8c0b-108">**href**</span><span class="sxs-lookup"><span data-stu-id="c8c0b-108">**href**</span></span>  | <span data-ttu-id="c8c0b-109">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-109">Required attribute.</span></span><br><br><span data-ttu-id="c8c0b-110">URL-адрес файла конфигурации, который необходимо включить.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-110">The URL of the configuration file to include.</span></span> <span data-ttu-id="c8c0b-111">Единственным форматом, поддерживаемым для атрибута **href** , является `file://` .</span><span class="sxs-lookup"><span data-stu-id="c8c0b-111">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="c8c0b-112">Поддерживаются локальные файлы и файлы в формате UNC.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-112">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c8c0b-113">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="c8c0b-113">Parent element</span></span>

|     | <span data-ttu-id="c8c0b-114">Описание</span><span class="sxs-lookup"><span data-stu-id="c8c0b-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c8c0b-115">**\<assemblyBinding>** Элемент</span><span class="sxs-lookup"><span data-stu-id="c8c0b-115">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="c8c0b-116">Определяет политику привязки сборок на уровне конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-116">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c8c0b-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c8c0b-117">Child elements</span></span>

<span data-ttu-id="c8c0b-118">None</span><span class="sxs-lookup"><span data-stu-id="c8c0b-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="c8c0b-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="c8c0b-119">Remarks</span></span>

<span data-ttu-id="c8c0b-120">**\<linkedConfiguration>** Элемент упрощает обслуживание сборок компонентов.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-120">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="c8c0b-121">Если одно или несколько приложений используют сборку с файлом конфигурации, находящимся в хорошо известном расположении, файлы конфигурации приложений, использующих эту сборку, могут использовать этот **\<linkedConfiguration>** элемент для включения файла конфигурации сборки, вместо того чтобы включать сведения о конфигурации напрямую.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-121">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="c8c0b-122">При обслуживании сборки компонента обновление общего файла конфигурации предоставляет обновленные сведения о конфигурации всем приложениям, которые используют сборку.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-122">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="c8c0b-123">**\<linkedConfiguration>** Элемент не поддерживается для приложений с параллельными манифестами Windows.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="c8c0b-124">Следующие правила управляют использованием связанных файлов конфигурации:</span><span class="sxs-lookup"><span data-stu-id="c8c0b-124">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="c8c0b-125">Параметры в включаемых файлах конфигурации влияют только на политику привязки загрузчика и используются только загрузчиком.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-125">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="c8c0b-126">Включаемые файлы конфигурации могут иметь параметры, отличные от политик привязки, но эти параметры не оказывают никакого влияния.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-126">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="c8c0b-127">Единственным форматом, поддерживаемым для `href` атрибута, является `file://` .</span><span class="sxs-lookup"><span data-stu-id="c8c0b-127">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="c8c0b-128">Поддерживаются локальные файлы и файлы в формате UNC.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-128">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="c8c0b-129">Ограничений на количество связанных конфигураций для каждого файла конфигурации не существует.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-129">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="c8c0b-130">Все связанные файлы конфигурации объединяются в один файл, аналогично поведению `#include` директивы в C/C++.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-130">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="c8c0b-131">**\<linkedConfiguration>** Элемент разрешен только в файлах конфигурации приложения. он игнорируется в *Machine.config*.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-131">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="c8c0b-132">Обнаружены и завершаются циклические ссылки.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-132">Circular references are detected and terminated.</span></span> <span data-ttu-id="c8c0b-133">То есть, если **\<linkedConfiguration>** элементы последовательности файлов конфигурации образуют цикл, цикл определяется и останавливается.</span><span class="sxs-lookup"><span data-stu-id="c8c0b-133">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="c8c0b-134">Пример</span><span class="sxs-lookup"><span data-stu-id="c8c0b-134">Example</span></span>

<span data-ttu-id="c8c0b-135">В следующем примере показано, как включить файл конфигурации с локального жесткого диска:</span><span class="sxs-lookup"><span data-stu-id="c8c0b-135">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c8c0b-136">См. также</span><span class="sxs-lookup"><span data-stu-id="c8c0b-136">See also</span></span>

- [<span data-ttu-id="c8c0b-137">**\<assemblyBinding>** Элемент</span><span class="sxs-lookup"><span data-stu-id="c8c0b-137">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="c8c0b-138">Схема файла конфигурации для платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c8c0b-138">Configuration file schema for the .NET Framework</span></span>](index.md)
