---
description: 'Дополнительные сведения о: <publisherPolicy> element'
title: Элемент <publisherPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: 35d729d5b195e010a80e7272312f14ac5802001b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802441"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="fea0b-103">Элемент \<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="fea0b-103">\<publisherPolicy> Element</span></span>

<span data-ttu-id="fea0b-104">Указывает, применяет ли среда выполнения политику издателя.</span><span class="sxs-lookup"><span data-stu-id="fea0b-104">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="fea0b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fea0b-105">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fea0b-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fea0b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fea0b-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fea0b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fea0b-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fea0b-108">Attributes</span></span>  
  
|<span data-ttu-id="fea0b-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fea0b-109">Attribute</span></span>|<span data-ttu-id="fea0b-110">Описание</span><span class="sxs-lookup"><span data-stu-id="fea0b-110">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="fea0b-111">Указывает, следует ли применять политику издателя.</span><span class="sxs-lookup"><span data-stu-id="fea0b-111">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="fea0b-112">применить атрибут</span><span class="sxs-lookup"><span data-stu-id="fea0b-112">apply Attribute</span></span>  
  
|<span data-ttu-id="fea0b-113">Значение</span><span class="sxs-lookup"><span data-stu-id="fea0b-113">Value</span></span>|<span data-ttu-id="fea0b-114">Описание</span><span class="sxs-lookup"><span data-stu-id="fea0b-114">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="fea0b-115">Применяет политику издателя.</span><span class="sxs-lookup"><span data-stu-id="fea0b-115">Applies publisher policy.</span></span> <span data-ttu-id="fea0b-116">Это параметр по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="fea0b-116">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="fea0b-117">Политика издателя не применяется.</span><span class="sxs-lookup"><span data-stu-id="fea0b-117">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fea0b-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fea0b-118">Child Elements</span></span>  

<span data-ttu-id="fea0b-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fea0b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fea0b-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fea0b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fea0b-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="fea0b-121">Element</span></span>|<span data-ttu-id="fea0b-122">Описание</span><span class="sxs-lookup"><span data-stu-id="fea0b-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="fea0b-123">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="fea0b-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="fea0b-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fea0b-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="fea0b-125">Инкапсулирует политику привязки и расположение каждой сборки.</span><span class="sxs-lookup"><span data-stu-id="fea0b-125">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="fea0b-126">`<dependentAssembly>`Для каждой сборки используется один элемент.</span><span class="sxs-lookup"><span data-stu-id="fea0b-126">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="fea0b-127">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="fea0b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fea0b-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="fea0b-128">Remarks</span></span>  

 <span data-ttu-id="fea0b-129">Когда поставщик компонента выпускает новую версию сборки, поставщик может включить политику издателя, чтобы приложения, использующие старую версию, теперь использовали новую версию.</span><span class="sxs-lookup"><span data-stu-id="fea0b-129">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="fea0b-130">Чтобы указать, следует ли применять политику издателя для определенной сборки, поставьте **\<publisherPolicy>** элемент в **\<dependentAssembly>** элемент.</span><span class="sxs-lookup"><span data-stu-id="fea0b-130">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="fea0b-131">Значение по умолчанию для атрибута **Apply** — **Да**.</span><span class="sxs-lookup"><span data-stu-id="fea0b-131">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="fea0b-132">Присвоение атрибуту **Apply** значения **No** переопределяет любые предыдущие параметры **Yes** для сборки.</span><span class="sxs-lookup"><span data-stu-id="fea0b-132">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="fea0b-133">Чтобы приложение явно игнорировало политику издателя с помощью [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) элемента в файле конфигурации приложения, требуется разрешение.</span><span class="sxs-lookup"><span data-stu-id="fea0b-133">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="fea0b-134">Разрешение предоставляется путем установки <xref:System.Security.Permissions.SecurityPermissionFlag> флага для <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="fea0b-134">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="fea0b-135">Дополнительные сведения см. в статье [разрешение безопасности перенаправления привязки сборок](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="fea0b-135">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fea0b-136">Пример</span><span class="sxs-lookup"><span data-stu-id="fea0b-136">Example</span></span>  

 <span data-ttu-id="fea0b-137">В следующем примере отключается политика издателя для сборки `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="fea0b-137">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fea0b-138">См. также</span><span class="sxs-lookup"><span data-stu-id="fea0b-138">See also</span></span>

- [<span data-ttu-id="fea0b-139">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="fea0b-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fea0b-140">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="fea0b-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fea0b-141">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="fea0b-141">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="fea0b-142">Перенаправление версий сборки</span><span class="sxs-lookup"><span data-stu-id="fea0b-142">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
