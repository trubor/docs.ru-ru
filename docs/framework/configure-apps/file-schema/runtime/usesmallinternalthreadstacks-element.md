---
description: 'Дополнительные сведения о: <UseSmallInternalThreadStacks> element'
title: Элемент <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: eeb253025b32f862926c7315004b1854b8eef928
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639969"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="3bc8b-103">Элемент \<UseSmallInternalThreadStacks></span><span class="sxs-lookup"><span data-stu-id="3bc8b-103">\<UseSmallInternalThreadStacks> Element</span></span>

<span data-ttu-id="3bc8b-104">Запрашивает уменьшение использования памяти средой CLR, указывая явные размеры стека при создании определенных потоков, используемых внутренним образом, вместо использования размера стека по умолчанию для этих потоков.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-104">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="3bc8b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3bc8b-105">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bc8b-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3bc8b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3bc8b-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bc8b-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3bc8b-108">Attributes</span></span>  
  
|<span data-ttu-id="3bc8b-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3bc8b-109">Attribute</span></span>|<span data-ttu-id="3bc8b-110">Описание</span><span class="sxs-lookup"><span data-stu-id="3bc8b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bc8b-111">Включено</span><span class="sxs-lookup"><span data-stu-id="3bc8b-111">enabled</span></span>|<span data-ttu-id="3bc8b-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="3bc8b-113">Указывает, следует ли запрашивать, что среда CLR использует явные размеры стека вместо размера стека по умолчанию при создании определенных потоков, используемых внутренним образом.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-113">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="3bc8b-114">Явные размеры стека меньше, чем размер стека по умолчанию (1 МБ).</span><span class="sxs-lookup"><span data-stu-id="3bc8b-114">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3bc8b-115">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="3bc8b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3bc8b-116">Значение</span><span class="sxs-lookup"><span data-stu-id="3bc8b-116">Value</span></span>|<span data-ttu-id="3bc8b-117">Описание</span><span class="sxs-lookup"><span data-stu-id="3bc8b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3bc8b-118">Да</span><span class="sxs-lookup"><span data-stu-id="3bc8b-118">true</span></span>|<span data-ttu-id="3bc8b-119">Запрос явных размеров стека.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-119">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="3bc8b-120">false</span><span class="sxs-lookup"><span data-stu-id="3bc8b-120">false</span></span>|<span data-ttu-id="3bc8b-121">Используйте размер стека по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-121">Use the default stack size.</span></span> <span data-ttu-id="3bc8b-122">Это значение по умолчанию для платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-122">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bc8b-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3bc8b-123">Child Elements</span></span>  

 <span data-ttu-id="3bc8b-124">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bc8b-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3bc8b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3bc8b-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="3bc8b-126">Element</span></span>|<span data-ttu-id="3bc8b-127">Описание</span><span class="sxs-lookup"><span data-stu-id="3bc8b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3bc8b-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3bc8b-129">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bc8b-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="3bc8b-130">Remarks</span></span>  

 <span data-ttu-id="3bc8b-131">Этот элемент конфигурации используется для запроса уменьшенного использования виртуальной памяти в процессе, поскольку явные размеры потоков, используемые средой CLR для внутренних потоков, если запрос обрабатывается, меньше размера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-131">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3bc8b-132">Этот элемент конфигурации является запросом к CLR, а не абсолютному требованию.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-132">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="3bc8b-133">В платформа .NET Framework 4 запрос учитывается только для архитектуры x86.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-133">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="3bc8b-134">Этот элемент может игнорироваться полностью в будущих версиях среды CLR или заменен на явные размеры стека, которые всегда используются для выбранных внутренних потоков.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-134">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="3bc8b-135">Указание этого элемента конфигурации меняет надежность для использования меньшего объема виртуальной памяти, если среда CLR учитывает запрос, так как меньшие размеры стека потенциально могут привести к большей вероятности переполняет стек.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-135">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bc8b-136">Пример</span><span class="sxs-lookup"><span data-stu-id="3bc8b-136">Example</span></span>  

 <span data-ttu-id="3bc8b-137">В следующем примере показано, как запросить, чтобы среда CLR использовала явные размеры стека для определенных потоков, которые он использует для внутренних целей.</span><span class="sxs-lookup"><span data-stu-id="3bc8b-137">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bc8b-138">См. также</span><span class="sxs-lookup"><span data-stu-id="3bc8b-138">See also</span></span>

- [<span data-ttu-id="3bc8b-139">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="3bc8b-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3bc8b-140">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="3bc8b-140">Configuration File Schema</span></span>](../index.md)
