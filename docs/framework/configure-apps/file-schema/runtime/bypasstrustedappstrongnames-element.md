---
description: 'Дополнительные сведения о: <bypassTrustedAppStrongNames> element'
title: Элемент <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: d23b9efa19481027480f2a1c7dab22bc97a05e13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719166"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="ef9d5-103">Элемент \<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="ef9d5-103">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="ef9d5-104">Указывает, следует ли обходить проверку строгих имен в сборках с полным доверием, загружаемых в полное доверие <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ef9d5-104">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="ef9d5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ef9d5-105">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef9d5-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ef9d5-106">Attributes and Elements</span></span>

<span data-ttu-id="ef9d5-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef9d5-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ef9d5-108">Attributes</span></span>

|<span data-ttu-id="ef9d5-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ef9d5-109">Attribute</span></span>|<span data-ttu-id="ef9d5-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ef9d5-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ef9d5-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef9d5-112">Указывает, включена ли функция обхода, которая не позволяет проверять строгие имена для сборок с полным доверием.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-112">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="ef9d5-113">Если эта функция включена, строгие имена не проверяются на правильность при загрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-113">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="ef9d5-114">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-114">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ef9d5-115">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="ef9d5-115">enabled Attribute</span></span>

|<span data-ttu-id="ef9d5-116">Значение</span><span class="sxs-lookup"><span data-stu-id="ef9d5-116">Value</span></span>|<span data-ttu-id="ef9d5-117">Описание</span><span class="sxs-lookup"><span data-stu-id="ef9d5-117">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="ef9d5-118">Подписи строгого имени в сборках с полным доверием не проверяются при загрузке сборок в режиме полного доверия <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ef9d5-118">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="ef9d5-119">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-119">This is the default.</span></span>|
|`false`|<span data-ttu-id="ef9d5-120">Подписи строгого имени в сборках с полным доверием проверяются при загрузке сборок в режиме полного доверия <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ef9d5-120">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="ef9d5-121">Подпись строгого имени проверяется только на правильность сигнатуры; оно не сравнивается с другим строгим именем для соответствия.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-121">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ef9d5-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ef9d5-122">Child Elements</span></span>

<span data-ttu-id="ef9d5-123">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef9d5-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ef9d5-124">Parent Elements</span></span>

|<span data-ttu-id="ef9d5-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="ef9d5-125">Element</span></span>|<span data-ttu-id="ef9d5-126">Описание</span><span class="sxs-lookup"><span data-stu-id="ef9d5-126">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ef9d5-127">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ef9d5-128">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-128">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef9d5-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="ef9d5-129">Remarks</span></span>

<span data-ttu-id="ef9d5-130">Функция пропуска строгих имен позволяет избежать дополнительных затрат на проверку подписи строгого имени сборок с полным доверием.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-130">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="ef9d5-131">Функция обхода применима к любой сборке, подписанной со строгим именем и имеющей следующие характеристики.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-131">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="ef9d5-132">Полное доверие без <xref:System.Security.Policy.StrongName> свидетельства (например, наличие `MyComputer` свидетельства зоны).</span><span class="sxs-lookup"><span data-stu-id="ef9d5-132">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="ef9d5-133">Загрузка в домен <xref:System.AppDomain> с полным доверием.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-133">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="ef9d5-134">Загрузка из расположения со свойством <xref:System.AppDomainSetup.ApplicationBase%2A> домена <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-134">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="ef9d5-135">Подпись осуществлена без задержки.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-135">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="ef9d5-136">Если функция обхода отключена для всех приложений на компьютере с помощью раздела реестра, этот параметр файла конфигурации не действует.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-136">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="ef9d5-137">Дополнительные сведения см. в разделе [как отключить функцию обхода Strong-Name](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="ef9d5-137">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="ef9d5-138">Пример</span><span class="sxs-lookup"><span data-stu-id="ef9d5-138">Example</span></span>

<span data-ttu-id="ef9d5-139">В следующем примере показано, как задать поведение, которое проверяет подпись строгого имени в сборках с полным доверием.</span><span class="sxs-lookup"><span data-stu-id="ef9d5-139">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ef9d5-140">См. также</span><span class="sxs-lookup"><span data-stu-id="ef9d5-140">See also</span></span>

- [<span data-ttu-id="ef9d5-141">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="ef9d5-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ef9d5-142">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="ef9d5-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ef9d5-143">Практическое руководство. Отключение функции пропуска строгих имен</span><span class="sxs-lookup"><span data-stu-id="ef9d5-143">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
