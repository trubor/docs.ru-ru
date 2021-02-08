---
description: 'Дополнительные сведения: <NetFx45_CultureAwareComparerGetHashCode_LongStrings элемент>'
title: Элемент <NetFx45_CultureAwareComparerGetHashCode_LongStrings>
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: ca4099d3bf812cb25e6a611b9b51b3752b1ad361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782290"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="bf3b6-103">Элемент \<NetFx45_CultureAwareComparerGetHashCode_LongStrings></span><span class="sxs-lookup"><span data-stu-id="bf3b6-103">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="bf3b6-104">Определяет, использует ли среда выполнения постоянный объем памяти для вычисления хэш-кодов методом <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bf3b6-104">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="bf3b6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bf3b6-105">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf3b6-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="bf3b6-106">Attributes and Elements</span></span>

<span data-ttu-id="bf3b6-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf3b6-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="bf3b6-108">Attributes</span></span>

|<span data-ttu-id="bf3b6-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="bf3b6-109">Attribute</span></span>|<span data-ttu-id="bf3b6-110">Описание</span><span class="sxs-lookup"><span data-stu-id="bf3b6-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="bf3b6-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="bf3b6-112">Определяет, выделяет ли среда CLR постоянный объем памяти при вычислении хэш-кодов.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-112">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="bf3b6-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="bf3b6-113">enabled Attribute</span></span>

|<span data-ttu-id="bf3b6-114">Значение</span><span class="sxs-lookup"><span data-stu-id="bf3b6-114">Value</span></span>|<span data-ttu-id="bf3b6-115">Описание</span><span class="sxs-lookup"><span data-stu-id="bf3b6-115">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="bf3b6-116">0</span><span class="sxs-lookup"><span data-stu-id="bf3b6-116">0</span></span>|<span data-ttu-id="bf3b6-117">Среда CLR выделяет переменный объем памяти методу <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> для вычисления хэш-кодов.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-117">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="bf3b6-118">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-118">This is the default.</span></span>|
|<span data-ttu-id="bf3b6-119">1</span><span class="sxs-lookup"><span data-stu-id="bf3b6-119">1</span></span>|<span data-ttu-id="bf3b6-120">Среда CLR выделяет постоянный объем памяти методу <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> для вычисления хэш-кодов.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-120">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bf3b6-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="bf3b6-121">Child Elements</span></span>

<span data-ttu-id="bf3b6-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bf3b6-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="bf3b6-123">Parent Elements</span></span>

|<span data-ttu-id="bf3b6-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="bf3b6-124">Element</span></span>|<span data-ttu-id="bf3b6-125">Описание</span><span class="sxs-lookup"><span data-stu-id="bf3b6-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="bf3b6-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="bf3b6-127">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bf3b6-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="bf3b6-128">Remarks</span></span>

<span data-ttu-id="bf3b6-129">По умолчанию среда CLR выделяет переменный объем памяти для метода <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> и при попытке вычисления этим методом хэш-кодов очень больших строк (длиной свыше нескольких миллионов символов) может быть создано исключение <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="bf3b6-129">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="bf3b6-130">Добавив этот элемент в файл конфигурации приложения и присвоив его атрибуту `enabled` значение "1", можно определить, что метод <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> использует другой алгоритм, который выделяет для вычисления хэш-кодов постоянный объем памяти.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-130">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf3b6-131">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Элемент не используется в Windows 8 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="bf3b6-131">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf3b6-132">См. также</span><span class="sxs-lookup"><span data-stu-id="bf3b6-132">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bf3b6-133">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="bf3b6-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf3b6-134">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="bf3b6-134">Configuration File Schema</span></span>](../index.md)
