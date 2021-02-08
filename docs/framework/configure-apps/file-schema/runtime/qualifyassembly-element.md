---
description: 'Дополнительные сведения о: <qualifyAssembly> element'
title: Элемент <qualifyAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 16891cca40d907d0ca32aea7f610e84305fcd0e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802456"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="ca94f-103">Элемент \<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="ca94f-103">\<qualifyAssembly> Element</span></span>

<span data-ttu-id="ca94f-104">Задает полное имя сборки, которая должна загружаться динамически в случае использования неполного имени.</span><span class="sxs-lookup"><span data-stu-id="ca94f-104">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="ca94f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca94f-105">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca94f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ca94f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ca94f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ca94f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca94f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ca94f-108">Attributes</span></span>  
  
|<span data-ttu-id="ca94f-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ca94f-109">Attribute</span></span>|<span data-ttu-id="ca94f-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ca94f-110">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="ca94f-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ca94f-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca94f-112">Задает частичное имя сборки в том виде, в котором оно отображается в коде.</span><span class="sxs-lookup"><span data-stu-id="ca94f-112">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="ca94f-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ca94f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca94f-114">Задает полное имя сборки в том виде, в каком оно отображается в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="ca94f-114">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca94f-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ca94f-115">Child Elements</span></span>  

 <span data-ttu-id="ca94f-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ca94f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca94f-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ca94f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ca94f-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="ca94f-118">Element</span></span>|<span data-ttu-id="ca94f-119">Описание</span><span class="sxs-lookup"><span data-stu-id="ca94f-119">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="ca94f-120">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="ca94f-120">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="ca94f-121">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca94f-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ca94f-122">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="ca94f-122">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca94f-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="ca94f-123">Remarks</span></span>  

 <span data-ttu-id="ca94f-124">Вызов <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> метода с использованием частичных имен сборок приводит к тому, что среда CLR ищет сборку только в базовом каталоге приложения.</span><span class="sxs-lookup"><span data-stu-id="ca94f-124">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="ca94f-125">Используйте **\<qualifyAssembly>** элемент в файле конфигурации приложения, чтобы предоставить полные сведения о сборке (имя, версию, маркер открытого ключа и язык и региональные параметры) и вызвать поиск сборки в глобальном кэше сборок в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="ca94f-125">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="ca94f-126">Атрибут **FullName** должен включать четыре поля удостоверения сборки: имя, версия, токен открытого ключа и язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="ca94f-126">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="ca94f-127">Атрибут **партиалнаме** должен ссылаться на сборку частично.</span><span class="sxs-lookup"><span data-stu-id="ca94f-127">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="ca94f-128">Необходимо указать по крайней мере текстовое имя сборки (наиболее распространенный случай), но можно также включить версию, токен открытого ключа или язык и региональные параметры (или любое сочетание четырех, но не все четыре).</span><span class="sxs-lookup"><span data-stu-id="ca94f-128">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="ca94f-129">**Партиалнаме** должно соответствовать имени, указанному в вызове.</span><span class="sxs-lookup"><span data-stu-id="ca94f-129">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="ca94f-130">Например, нельзя указать в `"math"` файле конфигурации в качестве атрибута **партиалнаме** и вызвать `Assembly.Load("math, Version=3.3.3.3")` в коде.</span><span class="sxs-lookup"><span data-stu-id="ca94f-130">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca94f-131">Пример</span><span class="sxs-lookup"><span data-stu-id="ca94f-131">Example</span></span>  

 <span data-ttu-id="ca94f-132">Следующий пример логически включает вызов `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` .</span><span class="sxs-lookup"><span data-stu-id="ca94f-132">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca94f-133">См. также</span><span class="sxs-lookup"><span data-stu-id="ca94f-133">See also</span></span>

- [<span data-ttu-id="ca94f-134">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="ca94f-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ca94f-135">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="ca94f-135">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="ca94f-136">[Частичные ссылки на сборки](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ca94f-136">[Partial Assembly References](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
