---
description: 'Дополнительные сведения о: <assemblyIdentity> Element для <runtime>'
title: Элемент <assemblyIdentity> для <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: d53c4f7f5207fbcf9ad4a8f82667eacc1f57f5e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719192"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="08922-103">Элемент \<assemblyIdentity> для \<runtime></span><span class="sxs-lookup"><span data-stu-id="08922-103">\<assemblyIdentity> Element for \<runtime></span></span>

<span data-ttu-id="08922-104">Содержит идентифицирующие сведения о сборке.</span><span class="sxs-lookup"><span data-stu-id="08922-104">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="08922-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08922-105">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08922-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="08922-106">Attributes and Elements</span></span>  

 <span data-ttu-id="08922-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="08922-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08922-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="08922-108">Attributes</span></span>  
  
|<span data-ttu-id="08922-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="08922-109">Attribute</span></span>|<span data-ttu-id="08922-110">Описание</span><span class="sxs-lookup"><span data-stu-id="08922-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="08922-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="08922-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="08922-112">Имя сборки</span><span class="sxs-lookup"><span data-stu-id="08922-112">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="08922-113">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="08922-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="08922-114">Строка, указывающая язык и страну или регион сборки.</span><span class="sxs-lookup"><span data-stu-id="08922-114">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="08922-115">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="08922-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="08922-116">Шестнадцатеричное значение, указывающее строгое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="08922-116">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="08922-117">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="08922-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="08922-118">Одно из значений "x86", "amd64", "MSIL" или "ia64", определяющее архитектуру процессора для сборки, содержащей код, зависящий от процессора.</span><span class="sxs-lookup"><span data-stu-id="08922-118">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="08922-119">В значениях регистр не учитывается.</span><span class="sxs-lookup"><span data-stu-id="08922-119">The values are not case-sensitive.</span></span> <span data-ttu-id="08922-120">Если атрибуту присвоено любое другое значение, весь `<assemblyIdentity>` элемент игнорируется.</span><span class="sxs-lookup"><span data-stu-id="08922-120">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="08922-121">См. раздел <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="08922-121">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="08922-122">Атрибут processorArchitecture</span><span class="sxs-lookup"><span data-stu-id="08922-122">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="08922-123">Значение</span><span class="sxs-lookup"><span data-stu-id="08922-123">Value</span></span>|<span data-ttu-id="08922-124">Описание</span><span class="sxs-lookup"><span data-stu-id="08922-124">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="08922-125">Только архитектура AMD x86-64.</span><span class="sxs-lookup"><span data-stu-id="08922-125">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="08922-126">Только архитектура Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="08922-126">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="08922-127">Код нейтрален по отношению к процессору и разрядности слова.</span><span class="sxs-lookup"><span data-stu-id="08922-127">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="08922-128">32-разрядный процессор x86, либо собственный, либо в среде Windows on Windows (WOW) на 64-разрядной платформе.</span><span class="sxs-lookup"><span data-stu-id="08922-128">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08922-129">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="08922-129">Child Elements</span></span>  

 <span data-ttu-id="08922-130">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="08922-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08922-131">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="08922-131">Parent Elements</span></span>  
  
|<span data-ttu-id="08922-132">Элемент</span><span class="sxs-lookup"><span data-stu-id="08922-132">Element</span></span>|<span data-ttu-id="08922-133">Описание</span><span class="sxs-lookup"><span data-stu-id="08922-133">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="08922-134">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="08922-134">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="08922-135">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08922-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="08922-136">Инкапсулирует политику привязки и расположение каждой сборки.</span><span class="sxs-lookup"><span data-stu-id="08922-136">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="08922-137">`<dependentAssembly>`Для каждой сборки используется один элемент.</span><span class="sxs-lookup"><span data-stu-id="08922-137">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="08922-138">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="08922-138">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08922-139">Remarks</span><span class="sxs-lookup"><span data-stu-id="08922-139">Remarks</span></span>  

 <span data-ttu-id="08922-140">Каждый **\<dependentAssembly>** элемент должен иметь один **\<assemblyIdentity>** дочерний элемент.</span><span class="sxs-lookup"><span data-stu-id="08922-140">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="08922-141">Если `processorArchitecture` атрибут имеется, `<assemblyIdentity>` элемент применяется только к сборке с соответствующей архитектурой процессора.</span><span class="sxs-lookup"><span data-stu-id="08922-141">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="08922-142">Если `processorArchitecture` атрибут отсутствует, `<assemblyIdentity>` элемент может применяться к сборке с любой архитектурой процессора.</span><span class="sxs-lookup"><span data-stu-id="08922-142">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="08922-143">В следующем примере показан файл конфигурации для двух сборок с одинаковым именем, предназначенных для двух разных архитектур процессора, чьи версии не поддерживали синхронизацию. При выполнении приложения на платформе x86 первый `<assemblyIdentity>` элемент применяется, а другой игнорируется.</span><span class="sxs-lookup"><span data-stu-id="08922-143">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="08922-144">Если приложение выполняется на платформе, отличной от x86 или ia64, то оба они игнорируются.</span><span class="sxs-lookup"><span data-stu-id="08922-144">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="08922-145">Если файл конфигурации содержит элемент без `<assemblyIdentity>` `processorArchitecture` атрибута и не содержит элемент, соответствующий платформе, то используется элемент без `processorArchitecture` атрибута.</span><span class="sxs-lookup"><span data-stu-id="08922-145">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08922-146">Пример</span><span class="sxs-lookup"><span data-stu-id="08922-146">Example</span></span>  

 <span data-ttu-id="08922-147">В следующем примере показано, как предоставить сведения о сборке.</span><span class="sxs-lookup"><span data-stu-id="08922-147">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08922-148">См. также</span><span class="sxs-lookup"><span data-stu-id="08922-148">See also</span></span>

- [<span data-ttu-id="08922-149">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="08922-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="08922-150">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="08922-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="08922-151">Перенаправление версий сборки</span><span class="sxs-lookup"><span data-stu-id="08922-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
