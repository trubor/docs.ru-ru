---
description: 'Дополнительные сведения о: <appDomainManagerType> element'
title: Элемент <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 633dcce2e370bda96efc61447611519d0ed04a3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787140"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="aeff0-103">Элемент \<appDomainManagerType></span><span class="sxs-lookup"><span data-stu-id="aeff0-103">\<appDomainManagerType> Element</span></span>

<span data-ttu-id="aeff0-104">Указывает тип, который служит диспетчером домена приложения для домена приложения, используемого по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aeff0-104">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="aeff0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aeff0-105">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aeff0-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="aeff0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="aeff0-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="aeff0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aeff0-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="aeff0-108">Attributes</span></span>  
  
|<span data-ttu-id="aeff0-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="aeff0-109">Attribute</span></span>|<span data-ttu-id="aeff0-110">Описание</span><span class="sxs-lookup"><span data-stu-id="aeff0-110">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="aeff0-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="aeff0-111">Required attribute.</span></span> <span data-ttu-id="aeff0-112">Указывает имя типа, включая пространство имен, которое служит диспетчером доменов приложений для домена приложения по умолчанию в процессе.</span><span class="sxs-lookup"><span data-stu-id="aeff0-112">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aeff0-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="aeff0-113">Child Elements</span></span>  

 <span data-ttu-id="aeff0-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="aeff0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aeff0-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="aeff0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="aeff0-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="aeff0-116">Element</span></span>|<span data-ttu-id="aeff0-117">Описание</span><span class="sxs-lookup"><span data-stu-id="aeff0-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aeff0-118">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aeff0-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="aeff0-119">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="aeff0-119">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeff0-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="aeff0-120">Remarks</span></span>  

 <span data-ttu-id="aeff0-121">Чтобы указать тип диспетчера домена приложения, необходимо указать и этот элемент, и [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="aeff0-121">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="aeff0-122">Если один из этих элементов не указан, другой игнорируется.</span><span class="sxs-lookup"><span data-stu-id="aeff0-122">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="aeff0-123">При загрузке домена приложения по умолчанию создается <xref:System.TypeLoadException> исключение, если указанный тип не существует в сборке, заданной [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) элементом, и процесс не запускается.</span><span class="sxs-lookup"><span data-stu-id="aeff0-123">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="aeff0-124">При указании типа диспетчера домена приложения для домена приложения по умолчанию другие домены приложений, созданные из домена приложения по умолчанию, наследуют тип диспетчера домена приложения.</span><span class="sxs-lookup"><span data-stu-id="aeff0-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="aeff0-125">Используйте <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> Свойства и, <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> чтобы указать другой тип диспетчера домена приложения для нового домена приложения.</span><span class="sxs-lookup"><span data-stu-id="aeff0-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="aeff0-126">Чтобы указать тип диспетчера доменов приложений, приложение должно иметь полное доверие.</span><span class="sxs-lookup"><span data-stu-id="aeff0-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="aeff0-127">(Например, приложение, работающее на рабочем столе, имеет полное доверие.) Если приложение не имеет полного доверия, <xref:System.TypeLoadException> создается исключение.</span><span class="sxs-lookup"><span data-stu-id="aeff0-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="aeff0-128">Формат типа и пространства имен совпадает с форматом, используемым для <xref:System.Type.FullName%2A?displayProperty=nameWithType> Свойства.</span><span class="sxs-lookup"><span data-stu-id="aeff0-128">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="aeff0-129">Этот элемент конфигурации доступен только в платформа .NET Framework 4 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="aeff0-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeff0-130">Пример</span><span class="sxs-lookup"><span data-stu-id="aeff0-130">Example</span></span>  

 <span data-ttu-id="aeff0-131">В следующем примере показано, как указать, что диспетчер домена приложения для домена приложения по умолчанию процесса — это `MyMgr` тип в `AdMgrExample` сборке.</span><span class="sxs-lookup"><span data-stu-id="aeff0-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aeff0-132">См. также</span><span class="sxs-lookup"><span data-stu-id="aeff0-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="aeff0-133">\<appDomainManagerAssembly> Элемент</span><span class="sxs-lookup"><span data-stu-id="aeff0-133">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="aeff0-134">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="aeff0-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="aeff0-135">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="aeff0-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="aeff0-136">Метод SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="aeff0-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
