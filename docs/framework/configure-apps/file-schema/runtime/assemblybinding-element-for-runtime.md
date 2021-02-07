---
description: 'Дополнительные сведения о: <assemblyBinding> Element для <runtime>'
title: Элемент <assemblyBinding> для <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: a797b541f9f13852234872f1eb2fc68a2eac727d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719231"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="9dbdc-103">Элемент \<assemblyBinding> для \<runtime></span><span class="sxs-lookup"><span data-stu-id="9dbdc-103">\<assemblyBinding> Element for \<runtime></span></span>

<span data-ttu-id="9dbdc-104">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-104">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="9dbdc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9dbdc-105">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9dbdc-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9dbdc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9dbdc-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9dbdc-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9dbdc-108">Attributes</span></span>  
  
|<span data-ttu-id="9dbdc-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9dbdc-109">Attribute</span></span>|<span data-ttu-id="9dbdc-110">Описание</span><span class="sxs-lookup"><span data-stu-id="9dbdc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9dbdc-111">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="9dbdc-111">**xmlns**</span></span>|<span data-ttu-id="9dbdc-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="9dbdc-113">Задает пространство имен XML, необходимое для привязки сборок.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-113">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="9dbdc-114">Используйте строку urn:schemas-microsoft-com:asm.v1 в качестве значения.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-114">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="9dbdc-115">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="9dbdc-115">**appliesTo**</span></span>|<span data-ttu-id="9dbdc-116">Задает версию среды выполнения, к которой применяется перенаправление сборки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-116">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="9dbdc-117">Этот необязательный атрибут содержит номер версии .NET Framework, к которой применяется перенаправление.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-117">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="9dbdc-118">Если атрибут **appliesTo** не указан, элемент **\<assemblyBinding>** применяется ко всем версиям платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-118">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="9dbdc-119">Атрибут **appliesTo** появился в платформа .NET Framework версии 1,1; он игнорируется платформа .NET Framework версии 1,0.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-119">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="9dbdc-120">Это означает, что при использовании платформы .NET Framework версии 1.0 применяются все элементы **\<assemblyBinding>** , даже если атрибут **appliesTo** задан.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-120">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9dbdc-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9dbdc-121">Child Elements</span></span>  
  
|<span data-ttu-id="9dbdc-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="9dbdc-122">Element</span></span>|<span data-ttu-id="9dbdc-123">Описание</span><span class="sxs-lookup"><span data-stu-id="9dbdc-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="9dbdc-124">Инкапсулирует политику привязки и расположение сборки.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-124">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="9dbdc-125">**\<dependentAssembly>** Для каждой сборки используется один тег.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-125">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[\<probing>](probing-element.md)|<span data-ttu-id="9dbdc-126">Задает вложенные папки, в которых среда CLR выполняет поиск при загрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-126">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="9dbdc-127">Указывает, применяет ли среда выполнения политику издателя.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-127">Specifies whether the runtime applies publisher policy.</span></span>|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="9dbdc-128">Задает полное имя сборки, которая должна загружаться динамически в случае использования неполного имени.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-128">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9dbdc-129">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9dbdc-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9dbdc-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="9dbdc-130">Element</span></span>|<span data-ttu-id="9dbdc-131">Описание</span><span class="sxs-lookup"><span data-stu-id="9dbdc-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9dbdc-132">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9dbdc-133">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-133">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9dbdc-134">Пример</span><span class="sxs-lookup"><span data-stu-id="9dbdc-134">Example</span></span>  

 <span data-ttu-id="9dbdc-135">В следующем примере показан способ перенаправления одной версии сборки на другую и предоставлена база кода.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-135">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="9dbdc-136">В следующем примере показано, как использовать атрибут **appliesTo** для перенаправления привязки платформа .NET Framework сборки.</span><span class="sxs-lookup"><span data-stu-id="9dbdc-136">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9dbdc-137">См. также</span><span class="sxs-lookup"><span data-stu-id="9dbdc-137">See also</span></span>

- [<span data-ttu-id="9dbdc-138">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="9dbdc-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9dbdc-139">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="9dbdc-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9dbdc-140">Перенаправление версий сборки</span><span class="sxs-lookup"><span data-stu-id="9dbdc-140">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
