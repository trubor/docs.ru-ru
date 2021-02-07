---
description: 'Дополнительные сведения о: <appDomainManagerAssembly> element'
title: Элемент <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: fcd461a8c8727679df3974028ddbc4b689c73e5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719309"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="99a1e-103">Элемент \<appDomainManagerAssembly></span><span class="sxs-lookup"><span data-stu-id="99a1e-103">\<appDomainManagerAssembly> Element</span></span>

<span data-ttu-id="99a1e-104">Указывает сборку, предоставляющую диспетчер домена приложения для домена приложения, по умолчанию используемого в процессе.</span><span class="sxs-lookup"><span data-stu-id="99a1e-104">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="99a1e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="99a1e-105">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99a1e-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="99a1e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="99a1e-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="99a1e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99a1e-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="99a1e-108">Attributes</span></span>  
  
|<span data-ttu-id="99a1e-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="99a1e-109">Attribute</span></span>|<span data-ttu-id="99a1e-110">Описание</span><span class="sxs-lookup"><span data-stu-id="99a1e-110">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="99a1e-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="99a1e-111">Required attribute.</span></span> <span data-ttu-id="99a1e-112">Указывает отображаемое имя сборки, предоставляющей Диспетчер доменов приложений для домена приложения по умолчанию в процессе.</span><span class="sxs-lookup"><span data-stu-id="99a1e-112">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99a1e-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="99a1e-113">Child Elements</span></span>  

 <span data-ttu-id="99a1e-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="99a1e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99a1e-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="99a1e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="99a1e-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="99a1e-116">Element</span></span>|<span data-ttu-id="99a1e-117">Описание</span><span class="sxs-lookup"><span data-stu-id="99a1e-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="99a1e-118">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99a1e-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="99a1e-119">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="99a1e-119">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99a1e-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="99a1e-120">Remarks</span></span>  

 <span data-ttu-id="99a1e-121">Чтобы указать тип диспетчера домена приложения, необходимо указать и этот элемент, и [\<appDomainManagerType>](appdomainmanagertype-element.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="99a1e-121">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="99a1e-122">Если один из этих элементов не указан, другой игнорируется.</span><span class="sxs-lookup"><span data-stu-id="99a1e-122">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="99a1e-123">Когда загружается домен приложения по умолчанию, создается <xref:System.TypeLoadException> исключение, если указанная сборка не существует или сборка не содержит тип, указанный в элементе, [\<appDomainManagerType>](appdomainmanagertype-element.md) и процесс не запускается.</span><span class="sxs-lookup"><span data-stu-id="99a1e-123">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="99a1e-124">Если сборка найдена, но сведения о версии не совпадают, <xref:System.IO.FileLoadException> создается исключение.</span><span class="sxs-lookup"><span data-stu-id="99a1e-124">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="99a1e-125">При указании типа диспетчера домена приложения для домена приложения по умолчанию другие домены приложений, созданные из домена приложения по умолчанию, наследуют тип диспетчера домена приложения.</span><span class="sxs-lookup"><span data-stu-id="99a1e-125">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="99a1e-126">Используйте <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> Свойства и, <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> чтобы указать другой тип диспетчера домена приложения для нового домена приложения.</span><span class="sxs-lookup"><span data-stu-id="99a1e-126">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="99a1e-127">Чтобы указать тип диспетчера доменов приложений, приложение должно иметь полное доверие.</span><span class="sxs-lookup"><span data-stu-id="99a1e-127">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="99a1e-128">(Например, приложение, работающее на рабочем столе, имеет полное доверие.) Если приложение не имеет полного доверия, <xref:System.TypeLoadException> создается исключение.</span><span class="sxs-lookup"><span data-stu-id="99a1e-128">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="99a1e-129">Сведения о формате отображаемого имени сборки см. в описании <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> Свойства.</span><span class="sxs-lookup"><span data-stu-id="99a1e-129">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="99a1e-130">Этот элемент конфигурации доступен только в платформа .NET Framework 4 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="99a1e-130">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99a1e-131">Пример</span><span class="sxs-lookup"><span data-stu-id="99a1e-131">Example</span></span>  

 <span data-ttu-id="99a1e-132">В следующем примере показано, как указать, что диспетчер домена приложения для домена приложения по умолчанию процесса — это `MyMgr` тип в `AdMgrExample` сборке.</span><span class="sxs-lookup"><span data-stu-id="99a1e-132">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99a1e-133">См. также</span><span class="sxs-lookup"><span data-stu-id="99a1e-133">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="99a1e-134">\<appDomainManagerType> Элемент</span><span class="sxs-lookup"><span data-stu-id="99a1e-134">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="99a1e-135">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="99a1e-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="99a1e-136">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="99a1e-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="99a1e-137">Метод SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="99a1e-137">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
