---
description: 'Дополнительные сведения о: <disableCachingBindingFailures> element'
title: Элемент <disableCachingBindingFailures>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
ms.openlocfilehash: b1f36f6a8fc7c78a0dc90ecc78ad725b677fdf40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787114"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="07a4c-103">Элемент \<disableCachingBindingFailures></span><span class="sxs-lookup"><span data-stu-id="07a4c-103">\<disableCachingBindingFailures> Element</span></span>

<span data-ttu-id="07a4c-104">Указывает, следует ли отключать кэширование ошибок привязки, возникающих из-за того, что сборка не была найдена проверкой.</span><span class="sxs-lookup"><span data-stu-id="07a4c-104">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="07a4c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07a4c-105">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07a4c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="07a4c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="07a4c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="07a4c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07a4c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="07a4c-108">Attributes</span></span>  
  
|<span data-ttu-id="07a4c-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="07a4c-109">Attribute</span></span>|<span data-ttu-id="07a4c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="07a4c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="07a4c-111">Включено</span><span class="sxs-lookup"><span data-stu-id="07a4c-111">enabled</span></span>|<span data-ttu-id="07a4c-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="07a4c-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="07a4c-113">Указывает, следует ли отключать кэширование ошибок привязки, возникающих из-за того, что сборка не была найдена проверкой.</span><span class="sxs-lookup"><span data-stu-id="07a4c-113">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="07a4c-114">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="07a4c-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="07a4c-115">Значение</span><span class="sxs-lookup"><span data-stu-id="07a4c-115">Value</span></span>|<span data-ttu-id="07a4c-116">Описание</span><span class="sxs-lookup"><span data-stu-id="07a4c-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07a4c-117">0</span><span class="sxs-lookup"><span data-stu-id="07a4c-117">0</span></span>|<span data-ttu-id="07a4c-118">Не отключайте кэширование ошибок привязки, возникающих из-за того, что сборка не была найдена проверкой.</span><span class="sxs-lookup"><span data-stu-id="07a4c-118">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="07a4c-119">Это поведение привязки по умолчанию, начинающееся с платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="07a4c-119">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="07a4c-120">1</span><span class="sxs-lookup"><span data-stu-id="07a4c-120">1</span></span>|<span data-ttu-id="07a4c-121">Отключите кэширование ошибок привязки, возникающих из-за того, что сборка не была найдена проверкой.</span><span class="sxs-lookup"><span data-stu-id="07a4c-121">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="07a4c-122">Этот параметр восстанавливает поведение привязки платформа .NET Framework версии 1,1.</span><span class="sxs-lookup"><span data-stu-id="07a4c-122">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07a4c-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="07a4c-123">Child Elements</span></span>  

 <span data-ttu-id="07a4c-124">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="07a4c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07a4c-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="07a4c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="07a4c-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="07a4c-126">Element</span></span>|<span data-ttu-id="07a4c-127">Описание</span><span class="sxs-lookup"><span data-stu-id="07a4c-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="07a4c-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07a4c-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="07a4c-129">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="07a4c-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07a4c-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="07a4c-130">Remarks</span></span>  

 <span data-ttu-id="07a4c-131">Начиная с версии платформа .NET Framework 2,0, поведением по умолчанию для загрузки сборок является кэширование всех ошибок привязки и загрузки.</span><span class="sxs-lookup"><span data-stu-id="07a4c-131">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="07a4c-132">То есть если попытка загрузить сборку завершается ошибкой, последующие запросы на загрузку одной и той же сборки будут завершаться сбоем немедленно, без каких-либо попыток нахождение сборки.</span><span class="sxs-lookup"><span data-stu-id="07a4c-132">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="07a4c-133">Этот элемент отключает поведение по умолчанию для сбоев привязки, возникающих из-за того, что сборка не найдена в пути поиска.</span><span class="sxs-lookup"><span data-stu-id="07a4c-133">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="07a4c-134">Эти ошибки вызываются <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="07a4c-134">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="07a4c-135">Этот элемент не влияет на некоторые ошибки привязки и загрузки и всегда кэшируется.</span><span class="sxs-lookup"><span data-stu-id="07a4c-135">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="07a4c-136">Эти сбои возникают из-за того, что сборка найдена, но не может быть загружена.</span><span class="sxs-lookup"><span data-stu-id="07a4c-136">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="07a4c-137">Они создают <xref:System.BadImageFormatException> или <xref:System.IO.FileLoadException> .</span><span class="sxs-lookup"><span data-stu-id="07a4c-137">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="07a4c-138">В следующем списке приведены некоторые примеры таких сбоев.</span><span class="sxs-lookup"><span data-stu-id="07a4c-138">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="07a4c-139">Если попытка загрузить файл не является допустимой сборкой, последующие попытки загрузки сборки завершатся ошибкой, даже если поврежденный файл заменяется правильной сборкой.</span><span class="sxs-lookup"><span data-stu-id="07a4c-139">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="07a4c-140">При попытке загрузить сборку, заблокированную файловой системой, последующие попытки загрузки сборки завершатся ошибкой даже после того, как сборка будет освобождена файловой системой.</span><span class="sxs-lookup"><span data-stu-id="07a4c-140">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="07a4c-141">Если одна или несколько версий сборки, которые вы пытаетесь загрузить, находятся в пути поиска, но конкретная Запрашиваемая версия не существует, последующие попытки загрузки этой версии завершатся ошибкой, даже если в путь поиска проверки перемещается правильная версия.</span><span class="sxs-lookup"><span data-stu-id="07a4c-141">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07a4c-142">Пример</span><span class="sxs-lookup"><span data-stu-id="07a4c-142">Example</span></span>  

 <span data-ttu-id="07a4c-143">В следующем примере показано, как отключить кэширование ошибок привязки сборок, возникающих из-за того, что сборка не была найдена проверкой.</span><span class="sxs-lookup"><span data-stu-id="07a4c-143">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07a4c-144">См. также</span><span class="sxs-lookup"><span data-stu-id="07a4c-144">See also</span></span>

- [<span data-ttu-id="07a4c-145">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="07a4c-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="07a4c-146">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="07a4c-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="07a4c-147">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="07a4c-147">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
