---
description: 'Дополнительные сведения о: <requiredRuntime> element'
title: <requiredRuntime> - элемент
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: e9d0a88a65f72ec03f3b2b124920d8265b8bf0c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639852"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="00af5-103">Элемент \<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="00af5-103">\<requiredRuntime> element</span></span>

<span data-ttu-id="00af5-104">Указывает, что приложение поддерживает только версию 1.0 среды CLR.</span><span class="sxs-lookup"><span data-stu-id="00af5-104">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="00af5-105">Этот элемент является устаревшим и больше не должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="00af5-105">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="00af5-106">[`supportedRuntime`](supportedruntime-element.md)Вместо этого следует использовать элемент.</span><span class="sxs-lookup"><span data-stu-id="00af5-106">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="00af5-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="00af5-107">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00af5-108">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="00af5-108">Attributes and elements</span></span>

<span data-ttu-id="00af5-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="00af5-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="00af5-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="00af5-110">Attributes</span></span>

|<span data-ttu-id="00af5-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="00af5-111">Attribute</span></span>|<span data-ttu-id="00af5-112">Описание</span><span class="sxs-lookup"><span data-stu-id="00af5-112">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="00af5-113">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="00af5-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="00af5-114">Строковое значение, указывающее версию платформа .NET Framework, которую поддерживает это приложение.</span><span class="sxs-lookup"><span data-stu-id="00af5-114">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="00af5-115">Строковое значение должно соответствовать имени каталога, обнаруженному в корне установки платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00af5-115">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="00af5-116">Содержимое строкового значения не анализируется.</span><span class="sxs-lookup"><span data-stu-id="00af5-116">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="00af5-117">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="00af5-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="00af5-118">Указывает, будет ли код запуска среды выполнения выполнять поиск в реестре для определения версии среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="00af5-118">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="00af5-119">атрибут безопасный режим</span><span class="sxs-lookup"><span data-stu-id="00af5-119">safemode attribute</span></span>

|<span data-ttu-id="00af5-120">Значение</span><span class="sxs-lookup"><span data-stu-id="00af5-120">Value</span></span>|<span data-ttu-id="00af5-121">Описание</span><span class="sxs-lookup"><span data-stu-id="00af5-121">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="00af5-122">Код запуска среды выполнения выполняет поиск в реестре.</span><span class="sxs-lookup"><span data-stu-id="00af5-122">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="00af5-123">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="00af5-123">This is the default value.</span></span>|
|`true`|<span data-ttu-id="00af5-124">Код запуска среды выполнения не выполняет поиск в реестре.</span><span class="sxs-lookup"><span data-stu-id="00af5-124">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="00af5-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="00af5-125">Child elements</span></span>

<span data-ttu-id="00af5-126">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="00af5-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="00af5-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="00af5-127">Parent elements</span></span>

|<span data-ttu-id="00af5-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="00af5-128">Element</span></span>|<span data-ttu-id="00af5-129">Описание</span><span class="sxs-lookup"><span data-stu-id="00af5-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="00af5-130">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00af5-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="00af5-131">Содержит `<requiredRuntime>` элемент.</span><span class="sxs-lookup"><span data-stu-id="00af5-131">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00af5-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="00af5-132">Remarks</span></span>

 <span data-ttu-id="00af5-133">Приложения, созданные для поддержки только версии 1,0 среды выполнения, должны использовать `<requiredRuntime>` элемент.</span><span class="sxs-lookup"><span data-stu-id="00af5-133">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="00af5-134">Приложения, созданные с помощью версии 1,1 или более поздней версии среды выполнения, должны использовать `<supportedRuntime>` элемент.</span><span class="sxs-lookup"><span data-stu-id="00af5-134">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="00af5-135">При использовании функции [корбиндторунтимебикфг](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) для указания файла конфигурации необходимо использовать `<requiredRuntime>` элемент для всех версий среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="00af5-135">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="00af5-136">`<supportedRuntime>`При использовании [корбиндторунтимебикфг](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)элемент игнорируется.</span><span class="sxs-lookup"><span data-stu-id="00af5-136">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="00af5-137">`version`Строка атрибута должна соответствовать имени папки установки для указанной версии платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00af5-137">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="00af5-138">Эта строка не интерпретируется.</span><span class="sxs-lookup"><span data-stu-id="00af5-138">This string is not interpreted.</span></span> <span data-ttu-id="00af5-139">Если код запуска среды выполнения не находит совпадающую папку, среда выполнения не загружается; код запуска отображает сообщение об ошибке и завершает работу.</span><span class="sxs-lookup"><span data-stu-id="00af5-139">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="00af5-140">Код запуска для приложения, размещенного в Microsoft Internet Explorer, игнорирует `<requiredRuntime>` элемент.</span><span class="sxs-lookup"><span data-stu-id="00af5-140">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="00af5-141">Пример</span><span class="sxs-lookup"><span data-stu-id="00af5-141">Example</span></span>

<span data-ttu-id="00af5-142">В следующем примере показано, как указать версию среды выполнения в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="00af5-142">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="00af5-143">См. также</span><span class="sxs-lookup"><span data-stu-id="00af5-143">See also</span></span>

- [<span data-ttu-id="00af5-144">Схема параметров запуска</span><span class="sxs-lookup"><span data-stu-id="00af5-144">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="00af5-145">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="00af5-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="00af5-146">Практическое руководство. Настройка приложения для включения поддержки .NET Framework версии 4 и выше</span><span class="sxs-lookup"><span data-stu-id="00af5-146">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
