---
description: 'Дополнительные сведения о: <forcePerformanceCounterUniqueSharedMemoryReads> element'
title: Элемент <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 63fe695cc993faa851a9ea3196294397d2992c45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787036"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="72631-103">Элемент \<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="72631-103">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>

<span data-ttu-id="72631-104">Указывает, использует ли файл PerfCounter.dll параметр реестра CategoryOptions в приложении .NET Framework версии 1.1, чтобы определить, следует ли загружать данные счетчиков производительности из общей памяти конкретной категории или глобальной памяти.</span><span class="sxs-lookup"><span data-stu-id="72631-104">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="72631-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="72631-105">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72631-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="72631-106">Attributes and Elements</span></span>  

 <span data-ttu-id="72631-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="72631-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72631-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="72631-108">Attributes</span></span>  
  
|<span data-ttu-id="72631-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="72631-109">Attribute</span></span>|<span data-ttu-id="72631-110">Описание</span><span class="sxs-lookup"><span data-stu-id="72631-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="72631-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="72631-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="72631-112">Указывает, использует ли PerfCounter.dll параметр реестра Категорйоптионс, чтобы определить, следует ли загружать данные счетчиков производительности из общей памяти конкретной категории или глобальной памяти.</span><span class="sxs-lookup"><span data-stu-id="72631-112">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="72631-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="72631-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="72631-114">Значение</span><span class="sxs-lookup"><span data-stu-id="72631-114">Value</span></span>|<span data-ttu-id="72631-115">Описание</span><span class="sxs-lookup"><span data-stu-id="72631-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="72631-116">PerfCounter.dll не использует параметр реестра Категорйоптионс, это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="72631-116">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="72631-117">PerfCounter.dll использует параметр реестра Категорйоптионс.</span><span class="sxs-lookup"><span data-stu-id="72631-117">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72631-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="72631-118">Child Elements</span></span>  

 <span data-ttu-id="72631-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="72631-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72631-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="72631-120">Parent Elements</span></span>  
  
|<span data-ttu-id="72631-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="72631-121">Element</span></span>|<span data-ttu-id="72631-122">Описание</span><span class="sxs-lookup"><span data-stu-id="72631-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="72631-123">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="72631-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="72631-124">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="72631-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72631-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="72631-125">Remarks</span></span>  

 <span data-ttu-id="72631-126">В версиях платформа .NET Framework до платформа .NET Framework 4 версия PerfCounter.dll, которая была загружена, соответствует среде выполнения, загруженной в процессе.</span><span class="sxs-lookup"><span data-stu-id="72631-126">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="72631-127">Если на компьютере установлены как платформа .NET Framework версии 1,1, так и платформа .NET Framework 2,0, то приложение платформа .NET Framework 1,1 загрузит платформа .NET Framework 1,1 версии PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="72631-127">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="72631-128">Начиная с платформа .NET Framework 4, загружается последняя установленная версия PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="72631-128">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="72631-129">Это означает, что приложение платформа .NET Framework 1,1 будет загружать версию PerfCounter.dll платформа .NET Framework 4, если на компьютере установлен платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="72631-129">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="72631-130">Начиная с платформа .NET Framework 4 при использовании счетчиков производительности PerfCounter.dll проверяет запись реестра Категорйоптионс для каждого поставщика, чтобы определить, должен ли он выполнять чтение из общей памяти конкретной категории или глобальной общей памяти.</span><span class="sxs-lookup"><span data-stu-id="72631-130">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="72631-131">Платформа .NET Framework 1,1 PerfCounter.dll не считывает эту запись реестра, так как она не поддерживает общую память, относящуюся к категории. Он всегда считывает данные из глобальной общей памяти.</span><span class="sxs-lookup"><span data-stu-id="72631-131">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="72631-132">Для обеспечения обратной совместимости платформа .NET Framework 4 PerfCounter.dll не проверяет запись реестра Категорйоптионс при запуске в приложении платформа .NET Framework 1,1.</span><span class="sxs-lookup"><span data-stu-id="72631-132">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="72631-133">Он просто использует глобальную общую память так же, как PerfCounter.dll платформа .NET Framework 1,1.</span><span class="sxs-lookup"><span data-stu-id="72631-133">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="72631-134">Однако можно указать платформа .NET Framework 4 PerfCounter.dll, чтобы проверить параметр реестра, включив `<forcePerformanceCounterUniqueSharedMemoryReads>` элемент.</span><span class="sxs-lookup"><span data-stu-id="72631-134">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72631-135">Включение `<forcePerformanceCounterUniqueSharedMemoryReads>` элемента не гарантирует, что будет использоваться общая память, относящаяся к категории.</span><span class="sxs-lookup"><span data-stu-id="72631-135">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="72631-136">Включение параметра включает `true` только PerfCounter.dll для ссылки на параметр реестра категорйоптионс.</span><span class="sxs-lookup"><span data-stu-id="72631-136">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="72631-137">Значение по умолчанию для Категорйоптионс — использовать общую память, относящуюся к категории; Однако можно изменить Категорйоптионс, чтобы указать, что следует использовать глобальную общую память.</span><span class="sxs-lookup"><span data-stu-id="72631-137">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="72631-138">Раздел реестра, содержащий параметр Категорйоптионс, — HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<CategoryName \> \перформанце.</span><span class="sxs-lookup"><span data-stu-id="72631-138">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="72631-139">По умолчанию Категорйоптионс имеет значение 3, что указывает PerfCounter.dll использовать общую память конкретной категории.</span><span class="sxs-lookup"><span data-stu-id="72631-139">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="72631-140">Если Категорйоптионс имеет значение 0, PerfCounter.dll использует глобальную общую память.</span><span class="sxs-lookup"><span data-stu-id="72631-140">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="72631-141">Данные экземпляра будут использоваться повторно только в том случае, если имя создаваемого экземпляра идентично повторно используемому экземпляру.</span><span class="sxs-lookup"><span data-stu-id="72631-141">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="72631-142">Все версии будут иметь возможность записи в категорию.</span><span class="sxs-lookup"><span data-stu-id="72631-142">All versions will be able to write to the category.</span></span> <span data-ttu-id="72631-143">Если для Категорйоптионс задано значение 1, используется глобальная общая память, но данные экземпляра могут использоваться повторно, если длина имени категории совпадает с длиной повторно используемого категории.</span><span class="sxs-lookup"><span data-stu-id="72631-143">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="72631-144">Параметры 0 и 1 могут привести к утечке памяти и заполнению памяти счетчика производительности.</span><span class="sxs-lookup"><span data-stu-id="72631-144">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72631-145">Пример</span><span class="sxs-lookup"><span data-stu-id="72631-145">Example</span></span>  

 <span data-ttu-id="72631-146">В следующем примере показано, как указать, что PerfCounter.dll должен ссылаться на запись реестра Категорйоптионс, чтобы определить, должна ли она использовать общую память, относящуюся к определенной категории.</span><span class="sxs-lookup"><span data-stu-id="72631-146">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72631-147">См. также</span><span class="sxs-lookup"><span data-stu-id="72631-147">See also</span></span>

- [<span data-ttu-id="72631-148">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="72631-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="72631-149">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="72631-149">Configuration File Schema</span></span>](../index.md)
