---
title: Элемент gcAllowVeryLargeObjects
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 1e54b0780ffb5bbe81ab1be2b376ff7a038ee05c
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058133"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="6c13d-102">Элемент \<gcAllowVeryLargeObjects></span><span class="sxs-lookup"><span data-stu-id="6c13d-102">\<gcAllowVeryLargeObjects> element</span></span>

<span data-ttu-id="6c13d-103">На 64 разрядных платформах позволяет использовать массивы, размер которых превышает 2 гигабайта (ГБ).</span><span class="sxs-lookup"><span data-stu-id="6c13d-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="6c13d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6c13d-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a><span data-ttu-id="6c13d-105">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6c13d-105">Attributes</span></span>
  
|<span data-ttu-id="6c13d-106">Атрибут</span><span class="sxs-lookup"><span data-stu-id="6c13d-106">Attribute</span></span>|<span data-ttu-id="6c13d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6c13d-107">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6c13d-108">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="6c13d-108">Required attribute.</span></span><br /><br /> <span data-ttu-id="6c13d-109">Указывает, включены ли на 64-разрядных платформах массивы размером более 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="6c13d-109">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="6c13d-110">Включенный атрибут</span><span class="sxs-lookup"><span data-stu-id="6c13d-110">enabled attribute</span></span>  
  
|<span data-ttu-id="6c13d-111">Значение</span><span class="sxs-lookup"><span data-stu-id="6c13d-111">Value</span></span>|<span data-ttu-id="6c13d-112">Описание</span><span class="sxs-lookup"><span data-stu-id="6c13d-112">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6c13d-113">Массивы объемом более 2 ГБ не включены.</span><span class="sxs-lookup"><span data-stu-id="6c13d-113">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="6c13d-114">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6c13d-114">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6c13d-115">Массивы объемом более 2 ГБ включены на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="6c13d-115">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="6c13d-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6c13d-116">Child elements</span></span>  

<span data-ttu-id="6c13d-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6c13d-117">None.</span></span>  
  
## <a name="parent-elements"></a><span data-ttu-id="6c13d-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6c13d-118">Parent elements</span></span>
  
|<span data-ttu-id="6c13d-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="6c13d-119">Element</span></span>|<span data-ttu-id="6c13d-120">Описание</span><span class="sxs-lookup"><span data-stu-id="6c13d-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6c13d-121">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c13d-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6c13d-122">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6c13d-122">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c13d-123">Комментарии</span><span class="sxs-lookup"><span data-stu-id="6c13d-123">Remarks</span></span>  

 <span data-ttu-id="6c13d-124">Использование этого элемента в файле конфигурации приложения позволяет использовать массивы размером более 2 ГБ, но не изменяет другие ограничения на размер объекта или размер массива:</span><span class="sxs-lookup"><span data-stu-id="6c13d-124">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="6c13d-125">Максимальное число элементов в массиве — <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6c13d-125">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="6c13d-126">Максимальный размер в одном измерении — 2 147 483 591 (0x7FFFFFC7) для массивов байтов и массивов однобайтовых структур, а также 2 146 435 071 (0X7FEFFFFF) для массивов, содержащих другие типы.</span><span class="sxs-lookup"><span data-stu-id="6c13d-126">The maximum size in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for arrays containing other types.</span></span>  
  
- <span data-ttu-id="6c13d-127">Максимальный размер строк и других объектов, не являющихся массивами, не изменяется.</span><span class="sxs-lookup"><span data-stu-id="6c13d-127">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="6c13d-128">Перед включением этой функции убедитесь, что приложение не включает в себя ненадежный код, который предполагает, что размер всех массивов меньше 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="6c13d-128">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="6c13d-129">Например, ненадежный код, использующий массивы как буферы, может быть уязвим для переполнения буфера, если он написан на основе предположения, что массивы не будут превышать 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="6c13d-129">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it's written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c13d-130">Пример</span><span class="sxs-lookup"><span data-stu-id="6c13d-130">Example</span></span>  

 <span data-ttu-id="6c13d-131">В следующем примере показано, как включить эту функцию для приложения.</span><span class="sxs-lookup"><span data-stu-id="6c13d-131">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="6c13d-132">Поддерживается в</span><span class="sxs-lookup"><span data-stu-id="6c13d-132">Supported in</span></span>

<span data-ttu-id="6c13d-133">.NET Framework 4,5 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="6c13d-133">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="6c13d-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6c13d-134">See also</span></span>

- [<span data-ttu-id="6c13d-135">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="6c13d-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6c13d-136">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="6c13d-136">Configuration File Schema</span></span>](../index.md)
