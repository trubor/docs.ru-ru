---
description: 'Дополнительные сведения: <NetFx40_LegacySecurityPolicy элемент>'
title: Элемент <NetFx40_LegacySecurityPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: 6be520d4cfd4f9ec05f4aceec82e4fef5440f55d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782316"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="674e1-103">Элемент \<NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="674e1-103">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="674e1-104">Указывает, использует ли среда выполнения устаревшую политику разграничения доступа кода.</span><span class="sxs-lookup"><span data-stu-id="674e1-104">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

## <a name="syntax"></a><span data-ttu-id="674e1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="674e1-105">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="674e1-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="674e1-106">Attributes and Elements</span></span>

<span data-ttu-id="674e1-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="674e1-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="674e1-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="674e1-108">Attributes</span></span>

|<span data-ttu-id="674e1-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="674e1-109">Attribute</span></span>|<span data-ttu-id="674e1-110">Описание</span><span class="sxs-lookup"><span data-stu-id="674e1-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="674e1-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="674e1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="674e1-112">Указывает, использует ли среда выполнения устаревшую политику разграничения доступа кода.</span><span class="sxs-lookup"><span data-stu-id="674e1-112">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="674e1-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="674e1-113">enabled Attribute</span></span>

|<span data-ttu-id="674e1-114">Значение</span><span class="sxs-lookup"><span data-stu-id="674e1-114">Value</span></span>|<span data-ttu-id="674e1-115">Описание</span><span class="sxs-lookup"><span data-stu-id="674e1-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="674e1-116">Среда выполнения не использует устаревшую политику разграничения доступа кода.</span><span class="sxs-lookup"><span data-stu-id="674e1-116">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="674e1-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="674e1-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="674e1-118">Среда выполнения использует устаревшую политику разграничения доступа кода.</span><span class="sxs-lookup"><span data-stu-id="674e1-118">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="674e1-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="674e1-119">Child Elements</span></span>

<span data-ttu-id="674e1-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="674e1-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="674e1-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="674e1-121">Parent Elements</span></span>

|<span data-ttu-id="674e1-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="674e1-122">Element</span></span>|<span data-ttu-id="674e1-123">Описание</span><span class="sxs-lookup"><span data-stu-id="674e1-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="674e1-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="674e1-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="674e1-125">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="674e1-125">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="674e1-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="674e1-126">Remarks</span></span>

<span data-ttu-id="674e1-127">В платформа .NET Framework версии 3,5 и более ранних версиях политика CAS действует всегда.</span><span class="sxs-lookup"><span data-stu-id="674e1-127">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="674e1-128">В платформа .NET Framework 4 политика CAS должна быть включена.</span><span class="sxs-lookup"><span data-stu-id="674e1-128">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="674e1-129">Политика CAS зависит от версии.</span><span class="sxs-lookup"><span data-stu-id="674e1-129">CAS policy is version-specific.</span></span> <span data-ttu-id="674e1-130">Пользовательские политики CAS, существующие в более ранних версиях платформа .NET Framework, должны быть указаны в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="674e1-130">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="674e1-131">Применение `<NetFx40_LegacySecurityPolicy>` элемента к сборке платформа .NET Framework 4 не влияет на прозрачный для [безопасности код](../../../misc/security-transparent-code.md); правила прозрачности по-прежнему применяются.</span><span class="sxs-lookup"><span data-stu-id="674e1-131">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="674e1-132">Применение `<NetFx40_LegacySecurityPolicy>` элемента может привести к значительному снижению производительности для сборок образов в машинном кодах, созданных [генератором образов в машинном кодах (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) , которые не установлены в [глобальном кэше сборок](../../../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="674e1-132">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="674e1-133">Снижение производительности вызвано невозможностью загрузки средой выполнения сборок в качестве образов в машинном код при применении атрибута, что приводит к их загрузке как JIT-сборки.</span><span class="sxs-lookup"><span data-stu-id="674e1-133">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="674e1-134">Если указать целевую версию платформа .NET Framework более раннюю, чем платформа .NET Framework 4 в параметрах проекта для проекта Visual Studio, будет включена политика CAS, включая любые пользовательские политики CAS, указанные для этой версии.</span><span class="sxs-lookup"><span data-stu-id="674e1-134">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="674e1-135">Однако вы не сможете использовать новые типы и члены платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="674e1-135">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="674e1-136">Можно также указать более раннюю версию платформа .NET Framework с помощью [ \<supportedRuntime> элемента](../startup/supportedruntime-element.md) в схеме параметров запуска в [файле конфигурации приложения](../../index.md).</span><span class="sxs-lookup"><span data-stu-id="674e1-136">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="674e1-137">В синтаксисе файла конфигурации учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="674e1-137">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="674e1-138">Следует использовать синтаксис, указанный в разделах синтаксис и пример.</span><span class="sxs-lookup"><span data-stu-id="674e1-138">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="674e1-139">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="674e1-139">Configuration File</span></span>

<span data-ttu-id="674e1-140">Этот элемент может использоваться только в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="674e1-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="674e1-141">Пример</span><span class="sxs-lookup"><span data-stu-id="674e1-141">Example</span></span>

<span data-ttu-id="674e1-142">В следующем примере показано, как включить устаревшую политику CAS для приложения.</span><span class="sxs-lookup"><span data-stu-id="674e1-142">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="674e1-143">См. также</span><span class="sxs-lookup"><span data-stu-id="674e1-143">See also</span></span>

- [<span data-ttu-id="674e1-144">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="674e1-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="674e1-145">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="674e1-145">Configuration File Schema</span></span>](../index.md)
