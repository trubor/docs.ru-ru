---
description: 'Дополнительные сведения о: <startup> element'
title: <startup> - элемент
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 82ece56aaa05376237922b3bd54b6f15967adf8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639826"
---
# <a name="startup-element"></a><span data-ttu-id="f02ae-103">Элемент \<startup></span><span class="sxs-lookup"><span data-stu-id="f02ae-103">\<startup> element</span></span>

<span data-ttu-id="f02ae-104">Задает сведения о запуске среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f02ae-104">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="f02ae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f02ae-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f02ae-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="f02ae-106">Attributes and elements</span></span>

 <span data-ttu-id="f02ae-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f02ae-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f02ae-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f02ae-108">Attributes</span></span>

|<span data-ttu-id="f02ae-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f02ae-109">Attribute</span></span>|<span data-ttu-id="f02ae-110">Описание</span><span class="sxs-lookup"><span data-stu-id="f02ae-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="f02ae-111">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="f02ae-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f02ae-112">Указывает, следует ли включить политику активации среды выполнения платформа .NET Framework 2,0 или использовать политику активации платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f02ae-112">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="f02ae-113">атрибут useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="f02ae-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="f02ae-114">Значение</span><span class="sxs-lookup"><span data-stu-id="f02ae-114">Value</span></span>|<span data-ttu-id="f02ae-115">Описание</span><span class="sxs-lookup"><span data-stu-id="f02ae-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="f02ae-116">Включите политику активации среды выполнения платформа .NET Framework 2,0 для выбранной среды выполнения, чтобы привязать устаревшие методы активации среды выполнения (например, [функцию CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) к среде выполнения, выбранной из файла конфигурации, вместо того, чтобы заключать их в CLR версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="f02ae-116">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="f02ae-117">Таким же, если в файле конфигурации выбрана среда CLR версии 4 или более поздней, сборки в смешанном режиме, созданные в более ранних версиях платформа .NET Framework, загружаются с выбранной версией среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f02ae-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="f02ae-118">Установка этого значения предотвращает загрузку среды CLR версии 1,1 или CLR версии 2,0 в один и тот же процесс, фактически отключив внутрипроцессный параллельный компонент.</span><span class="sxs-lookup"><span data-stu-id="f02ae-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="f02ae-119">Используйте политику активации по умолчанию для платформа .NET Framework 4 и более поздних версий, которая позволяет использовать устаревшие методы активации среды выполнения для загрузки среды CLR версии 1,1 или 2,0 в процесс.</span><span class="sxs-lookup"><span data-stu-id="f02ae-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="f02ae-120">Установка этого значения предотвращает загрузку сборок в смешанном режиме в платформа .NET Framework 4 или более поздней версии, если они не были созданы с помощью платформа .NET Framework 4 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f02ae-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="f02ae-121">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f02ae-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f02ae-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f02ae-122">Child elements</span></span>

|<span data-ttu-id="f02ae-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="f02ae-123">Element</span></span>|<span data-ttu-id="f02ae-124">Описание</span><span class="sxs-lookup"><span data-stu-id="f02ae-124">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="f02ae-125">Указывает, что приложение поддерживает только версию 1.0 среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f02ae-125">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f02ae-126">В приложениях, созданных с помощью среды выполнения версии 1,1 или более поздней, должен использоваться **\<supportedRuntime>** элемент.</span><span class="sxs-lookup"><span data-stu-id="f02ae-126">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="f02ae-127">Указывает, какие версии среды CLR поддерживает приложение.</span><span class="sxs-lookup"><span data-stu-id="f02ae-127">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f02ae-128">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f02ae-128">Parent elements</span></span>

|<span data-ttu-id="f02ae-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="f02ae-129">Element</span></span>|<span data-ttu-id="f02ae-130">Описание</span><span class="sxs-lookup"><span data-stu-id="f02ae-130">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="f02ae-131">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f02ae-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f02ae-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="f02ae-132">Remarks</span></span>

 <span data-ttu-id="f02ae-133">**\<supportedRuntime>** Элемент должен использоваться всеми приложениями, созданными с помощью среды выполнения версии 1,1 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="f02ae-133">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="f02ae-134">Приложения, созданные для поддержки только версии 1,0 среды выполнения, должны использовать **\<requiredRuntime>** элемент.</span><span class="sxs-lookup"><span data-stu-id="f02ae-134">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="f02ae-135">Код запуска для приложения, размещенного в Microsoft Internet Explorer, игнорирует **\<startup>** элемент и его дочерние элементы.</span><span class="sxs-lookup"><span data-stu-id="f02ae-135">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="f02ae-136">Атрибут useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="f02ae-136">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="f02ae-137">Этот атрибут полезен, если ваше приложение использует пути активации прежних версий, например [функцию CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), и вы хотите, чтобы эти пути активировали версию 4 среды CLR вместо более ранней версии или если приложение создано с платформа .NET Framework 4, но зависит от сборки в смешанном режиме, построенной с использованием более ранней версии платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f02ae-137">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="f02ae-138">В этих сценариях задайте для атрибута значение `true` .</span><span class="sxs-lookup"><span data-stu-id="f02ae-138">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="f02ae-139">Установка атрибута `true` предотвращает загрузку среды CLR версии 1,1 или CLR версии 2,0 в один и тот же процесс, фактически отключив внутрипроцессный параллельный компонент (см. раздел [параллельное выполнение для COM-взаимодействия](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="f02ae-139">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="f02ae-140">Пример</span><span class="sxs-lookup"><span data-stu-id="f02ae-140">Example</span></span>

 <span data-ttu-id="f02ae-141">В следующем примере показано, как указать версию среды выполнения в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f02ae-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f02ae-142">См. также</span><span class="sxs-lookup"><span data-stu-id="f02ae-142">See also</span></span>

- [<span data-ttu-id="f02ae-143">Схема параметров запуска</span><span class="sxs-lookup"><span data-stu-id="f02ae-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f02ae-144">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="f02ae-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f02ae-145">Практическое руководство. Настройка приложения для включения поддержки .NET Framework версии 4 и выше</span><span class="sxs-lookup"><span data-stu-id="f02ae-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="f02ae-146">[Параллельное выполнение для COM- взаимодействия](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f02ae-146">[Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="f02ae-147">Внутрипроцессное параллельное выполнение</span><span class="sxs-lookup"><span data-stu-id="f02ae-147">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
