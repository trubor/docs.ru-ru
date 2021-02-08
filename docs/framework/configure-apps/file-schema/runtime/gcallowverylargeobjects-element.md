---
description: 'Дополнительные сведения о: <gcAllowVeryLargeObjects> element'
title: Элемент gcAllowVeryLargeObjects
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: ff8380a13c4284cc24178e185344207c3b9a39b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787023"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="c9879-103">Элемент \<gcAllowVeryLargeObjects></span><span class="sxs-lookup"><span data-stu-id="c9879-103">\<gcAllowVeryLargeObjects> element</span></span>

<span data-ttu-id="c9879-104">На 64 разрядных платформах позволяет использовать массивы, размер которых превышает 2 гигабайта (ГБ).</span><span class="sxs-lookup"><span data-stu-id="c9879-104">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="c9879-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9879-105">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a><span data-ttu-id="c9879-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c9879-106">Attributes</span></span>
  
|<span data-ttu-id="c9879-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c9879-107">Attribute</span></span>|<span data-ttu-id="c9879-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c9879-108">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c9879-109">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="c9879-109">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9879-110">Указывает, включены ли на 64-разрядных платформах массивы размером более 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="c9879-110">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="c9879-111">Включенный атрибут</span><span class="sxs-lookup"><span data-stu-id="c9879-111">enabled attribute</span></span>  
  
|<span data-ttu-id="c9879-112">Значение</span><span class="sxs-lookup"><span data-stu-id="c9879-112">Value</span></span>|<span data-ttu-id="c9879-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c9879-113">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c9879-114">Массивы объемом более 2 ГБ не включены.</span><span class="sxs-lookup"><span data-stu-id="c9879-114">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="c9879-115">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c9879-115">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c9879-116">Массивы объемом более 2 ГБ включены на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="c9879-116">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="c9879-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c9879-117">Child elements</span></span>  

<span data-ttu-id="c9879-118">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="c9879-118">None.</span></span>  
  
## <a name="parent-elements"></a><span data-ttu-id="c9879-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c9879-119">Parent elements</span></span>
  
|<span data-ttu-id="c9879-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="c9879-120">Element</span></span>|<span data-ttu-id="c9879-121">Описание</span><span class="sxs-lookup"><span data-stu-id="c9879-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c9879-122">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9879-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c9879-123">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="c9879-123">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9879-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9879-124">Remarks</span></span>  

 <span data-ttu-id="c9879-125">Использование этого элемента в файле конфигурации приложения позволяет использовать массивы размером более 2 ГБ, но не изменяет другие ограничения на размер объекта или размер массива:</span><span class="sxs-lookup"><span data-stu-id="c9879-125">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="c9879-126">Максимальное число элементов в массиве — <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c9879-126">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="c9879-127">Максимальный размер в одном измерении — 2 147 483 591 (0x7FFFFFC7) для массивов байтов и массивов однобайтовых структур, а также 2 146 435 071 (0X7FEFFFFF) для массивов, содержащих другие типы.</span><span class="sxs-lookup"><span data-stu-id="c9879-127">The maximum size in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for arrays containing other types.</span></span>  
  
- <span data-ttu-id="c9879-128">Максимальный размер строк и других объектов, не являющихся массивами, не изменяется.</span><span class="sxs-lookup"><span data-stu-id="c9879-128">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c9879-129">Перед включением этой функции убедитесь, что приложение не включает в себя ненадежный код, который предполагает, что размер всех массивов меньше 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="c9879-129">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="c9879-130">Например, ненадежный код, использующий массивы как буферы, может быть уязвим для переполнения буфера, если он написан на основе предположения, что массивы не будут превышать 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="c9879-130">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it's written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9879-131">Пример</span><span class="sxs-lookup"><span data-stu-id="c9879-131">Example</span></span>  

 <span data-ttu-id="c9879-132">В следующем примере показано, как включить эту функцию для приложения.</span><span class="sxs-lookup"><span data-stu-id="c9879-132">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="c9879-133">Поддерживается в</span><span class="sxs-lookup"><span data-stu-id="c9879-133">Supported in</span></span>

<span data-ttu-id="c9879-134">Платформа .NET Framework 4,5 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="c9879-134">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="c9879-135">См. также</span><span class="sxs-lookup"><span data-stu-id="c9879-135">See also</span></span>

- [<span data-ttu-id="c9879-136">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="c9879-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c9879-137">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="c9879-137">Configuration File Schema</span></span>](../index.md)
