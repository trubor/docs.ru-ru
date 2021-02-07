---
description: 'Дополнительные сведения о: <bindingRedirect> element'
title: Элемент <bindingRedirect>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: 833ee73fa11d179ac855f3ac4d2bca8d7a2226ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719179"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="48874-103">Элемент \<bindingRedirect></span><span class="sxs-lookup"><span data-stu-id="48874-103">\<bindingRedirect> Element</span></span>

<span data-ttu-id="48874-104">Перенаправляет одну версию сборки на другую.</span><span class="sxs-lookup"><span data-stu-id="48874-104">Redirects one assembly version to another.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a><span data-ttu-id="48874-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="48874-105">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48874-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="48874-106">Attributes and Elements</span></span>  

 <span data-ttu-id="48874-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="48874-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48874-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="48874-108">Attributes</span></span>  
  
|<span data-ttu-id="48874-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="48874-109">Attribute</span></span>|<span data-ttu-id="48874-110">Описание</span><span class="sxs-lookup"><span data-stu-id="48874-110">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="48874-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="48874-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="48874-112">Задает первоначально запрошенную версию сборки.</span><span class="sxs-lookup"><span data-stu-id="48874-112">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="48874-113">Номер версии сборки имеет формат *основной. дополнительный. сборка. Редакция*.</span><span class="sxs-lookup"><span data-stu-id="48874-113">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="48874-114">Допустимые значения для каждой части этого номера версии — от 0 до 65535.</span><span class="sxs-lookup"><span data-stu-id="48874-114">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="48874-115">Диапазон версий можно также задать в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="48874-115">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="48874-116">*n. n. n. n-n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="48874-116">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="48874-117">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="48874-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="48874-118">Указывает версию сборки, используемую вместо первоначально запрошенной версии в формате: *n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="48874-118">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="48874-119">Это значение может указывать более раннюю версию, чем `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="48874-119">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48874-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="48874-120">Child Elements</span></span>  
  
|<span data-ttu-id="48874-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="48874-121">Element</span></span>|<span data-ttu-id="48874-122">Описание</span><span class="sxs-lookup"><span data-stu-id="48874-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48874-123">None</span><span class="sxs-lookup"><span data-stu-id="48874-123">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="48874-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="48874-124">Parent Elements</span></span>  
  
|<span data-ttu-id="48874-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="48874-125">Element</span></span>|<span data-ttu-id="48874-126">Описание</span><span class="sxs-lookup"><span data-stu-id="48874-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="48874-127">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="48874-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="48874-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48874-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="48874-129">Инкапсулирует политику привязки и расположение каждой сборки.</span><span class="sxs-lookup"><span data-stu-id="48874-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="48874-130">Для каждой сборки используется только один элемент dependentAssembly.</span><span class="sxs-lookup"><span data-stu-id="48874-130">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="48874-131">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="48874-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48874-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="48874-132">Remarks</span></span>  

 <span data-ttu-id="48874-133">При сборке приложения .NET Framework с использованием сборки со строгим именем приложение во время выполнения по умолчанию будет использовать эту версию сборки, даже если доступна новая версия.</span><span class="sxs-lookup"><span data-stu-id="48874-133">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="48874-134">Однако приложение можно настроить для выполнения с новой версией сборки.</span><span class="sxs-lookup"><span data-stu-id="48874-134">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="48874-135">Дополнительные сведения о том, как среда выполнения использует эти файлы для определения используемой версии сборки, см. в разделе [как среда выполнения находит сборки](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="48874-135">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="48874-136">Перенаправление нескольких версий сборок можно выполнить, включив в элемент `bindingRedirect` несколько элементов `dependentAssembly`.</span><span class="sxs-lookup"><span data-stu-id="48874-136">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="48874-137">Можно также выполнить перенаправление с более новой версии на более раннюю версию сборки.</span><span class="sxs-lookup"><span data-stu-id="48874-137">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="48874-138">Для явного перенаправления привязки сборки в файле конфигурации приложения необходимо разрешение безопасности.</span><span class="sxs-lookup"><span data-stu-id="48874-138">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="48874-139">Это относится к перенаправлению как сборок платформы .NET Framework, так и сторонних сборок.</span><span class="sxs-lookup"><span data-stu-id="48874-139">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="48874-140">Разрешение предоставляется путем установки <xref:System.Security.Permissions.SecurityPermissionFlag> флага для <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="48874-140">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="48874-141">Дополнительные сведения см. в статье [разрешение безопасности перенаправления привязки сборок](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="48874-141">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48874-142">Пример</span><span class="sxs-lookup"><span data-stu-id="48874-142">Example</span></span>  

 <span data-ttu-id="48874-143">В следующем примере показан способ перенаправления одной версии сборки на другую.</span><span class="sxs-lookup"><span data-stu-id="48874-143">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48874-144">См. также</span><span class="sxs-lookup"><span data-stu-id="48874-144">See also</span></span>

- [<span data-ttu-id="48874-145">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="48874-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="48874-146">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="48874-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="48874-147">Перенаправление версий сборки</span><span class="sxs-lookup"><span data-stu-id="48874-147">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
