---
description: 'Дополнительные сведения о: <CompatSortNLSVersion> element'
title: Элемент <CompatSortNLSVersion>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
ms.openlocfilehash: a064c849e53167c5f7cf16b934dfb377f3d07644
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726186"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="3cb91-103">Элемент \<CompatSortNLSVersion></span><span class="sxs-lookup"><span data-stu-id="3cb91-103">\<CompatSortNLSVersion> Element</span></span>

<span data-ttu-id="3cb91-104">Указывает, что при операциях сравнения строк среда выполнения должна использовать устаревший порядок сортировки.</span><span class="sxs-lookup"><span data-stu-id="3cb91-104">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a><span data-ttu-id="3cb91-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3cb91-105">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cb91-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3cb91-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3cb91-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3cb91-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cb91-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3cb91-108">Attributes</span></span>  
  
|<span data-ttu-id="3cb91-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3cb91-109">Attribute</span></span>|<span data-ttu-id="3cb91-110">Описание</span><span class="sxs-lookup"><span data-stu-id="3cb91-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3cb91-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="3cb91-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="3cb91-112">Указывает код языка, порядок сортировки которого должен использоваться.</span><span class="sxs-lookup"><span data-stu-id="3cb91-112">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3cb91-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="3cb91-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="3cb91-114">Значение</span><span class="sxs-lookup"><span data-stu-id="3cb91-114">Value</span></span>|<span data-ttu-id="3cb91-115">Описание</span><span class="sxs-lookup"><span data-stu-id="3cb91-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3cb91-116">4096</span><span class="sxs-lookup"><span data-stu-id="3cb91-116">4096</span></span>|<span data-ttu-id="3cb91-117">Код языка, представляющий альтернативный порядок сортировки.</span><span class="sxs-lookup"><span data-stu-id="3cb91-117">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="3cb91-118">В этом случае 4096 представляет порядок сортировки платформа .NET Framework 3,5 и более ранних версий.</span><span class="sxs-lookup"><span data-stu-id="3cb91-118">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cb91-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3cb91-119">Child Elements</span></span>  

 <span data-ttu-id="3cb91-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3cb91-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cb91-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3cb91-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3cb91-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="3cb91-122">Element</span></span>|<span data-ttu-id="3cb91-123">Описание</span><span class="sxs-lookup"><span data-stu-id="3cb91-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3cb91-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cb91-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3cb91-125">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="3cb91-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cb91-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="3cb91-126">Remarks</span></span>  

 <span data-ttu-id="3cb91-127">Поскольку операции сравнения строк, сортировки и учета регистра, выполняемые <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> классом в платформа .NET Framework 4, соответствуют стандарту Unicode 5,1, результаты методов сравнения строк, таких как <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> и, <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> могут отличаться от предыдущих версий платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cb91-127">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="3cb91-128">Если приложение зависит от устаревшего поведения, можно восстановить правила сравнения строк и сортировки, используемые в платформа .NET Framework 3,5 и более ранних версиях, включив `<CompatSortNLSVersion>` элемент в файл конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="3cb91-128">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3cb91-129">Для восстановления устаревших правил сравнения и сортировки строк также требуется, чтобы в локальной системе была доступна библиотека динамической компоновки sort00001000.dll.</span><span class="sxs-lookup"><span data-stu-id="3cb91-129">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="3cb91-130">Устаревшие правила сортировки и сравнения строк можно также использовать в конкретном домене приложения, передав при создании этого домена строку "NetFx40_Legacy20SortingBehavior" в метод <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cb91-130">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cb91-131">Пример</span><span class="sxs-lookup"><span data-stu-id="3cb91-131">Example</span></span>  

 <span data-ttu-id="3cb91-132">В следующем примере создаются экземпляры двух объектов <xref:System.String> и вызывается метод <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType>, чтобы сравнить их с использованием соглашений текущих языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="3cb91-132">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="3cb91-133">При запуске примера на платформа .NET Framework 4 отображаются следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="3cb91-133">When you run the example on the .NET Framework 4, it displays the following output:</span></span>
  
```console
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="3cb91-134">Он совершенно отличается от выходных данных, отображаемых при выполнении примера на платформа .NET Framework 3,5:</span><span class="sxs-lookup"><span data-stu-id="3cb91-134">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5:</span></span>
  
```console
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="3cb91-135">Однако если добавить в каталог примера следующий файл конфигурации, а затем запустить пример на платформа .NET Framework 4, то выходные данные идентичны тому, что были созданы в примере при его запуске на платформа .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="3cb91-135">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cb91-136">См. также</span><span class="sxs-lookup"><span data-stu-id="3cb91-136">See also</span></span>

- [<span data-ttu-id="3cb91-137">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="3cb91-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3cb91-138">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="3cb91-138">Configuration File Schema</span></span>](../index.md)
