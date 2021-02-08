---
description: 'Дополнительные сведения о: <legacyImpersonationPolicy> element'
title: Элемент <legacyImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
ms.openlocfilehash: 36cc3336e8e3c0196ae20fc749fc2239c35c8584
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782368"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="55044-103">Элемент \<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="55044-103">\<legacyImpersonationPolicy> Element</span></span>

<span data-ttu-id="55044-104">Указывает, что удостоверение Windows не проходит через асинхронные точки, независимо от параметров потока для контекста выполнения в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="55044-104">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="55044-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55044-105">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55044-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="55044-106">Attributes and Elements</span></span>  

 <span data-ttu-id="55044-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="55044-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55044-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="55044-108">Attributes</span></span>  
  
|<span data-ttu-id="55044-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="55044-109">Attribute</span></span>|<span data-ttu-id="55044-110">Описание</span><span class="sxs-lookup"><span data-stu-id="55044-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="55044-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="55044-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="55044-112">Указывает, что объект не передается <xref:System.Security.Principal.WindowsIdentity> по асинхронным точкам, независимо от <xref:System.Threading.ExecutionContext> параметров потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="55044-112">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55044-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="55044-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="55044-114">Значение</span><span class="sxs-lookup"><span data-stu-id="55044-114">Value</span></span>|<span data-ttu-id="55044-115">Описание</span><span class="sxs-lookup"><span data-stu-id="55044-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="55044-116"><xref:System.Security.Principal.WindowsIdentity> проходит через асинхронные точки в зависимости от <xref:System.Threading.ExecutionContext> параметров потока для текущего потока.</span><span class="sxs-lookup"><span data-stu-id="55044-116"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="55044-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="55044-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="55044-118"><xref:System.Security.Principal.WindowsIdentity> не перетекает через асинхронные точки, независимо от <xref:System.Threading.ExecutionContext> параметров потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="55044-118"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55044-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="55044-119">Child Elements</span></span>  

 <span data-ttu-id="55044-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="55044-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55044-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="55044-121">Parent Elements</span></span>  
  
|<span data-ttu-id="55044-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="55044-122">Element</span></span>|<span data-ttu-id="55044-123">Описание</span><span class="sxs-lookup"><span data-stu-id="55044-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55044-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55044-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55044-125">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="55044-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55044-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="55044-126">Remarks</span></span>  

 <span data-ttu-id="55044-127">В платформа .NET Framework версиях 1,0 и 1,1, объект не <xref:System.Security.Principal.WindowsIdentity> проходит через определенные пользователем асинхронные точки.</span><span class="sxs-lookup"><span data-stu-id="55044-127">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="55044-128">Начиная с версии платформа .NET Framework 2,0, существует <xref:System.Threading.ExecutionContext> объект, который содержит сведения о выполняющемся в данный момент потоке и проходит через асинхронные точки в пределах домена приложения.</span><span class="sxs-lookup"><span data-stu-id="55044-128">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="55044-129"><xref:System.Security.Principal.WindowsIdentity>Включается в этот контекст выполнения и, следовательно, проходит через асинхронные точки, что означает, что если контекст олицетворения существует, он также будет работать.</span><span class="sxs-lookup"><span data-stu-id="55044-129">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="55044-130">Начиная с платформа .NET Framework 2,0, можно использовать `<legacyImpersonationPolicy>` элемент, чтобы указать, что не передается  <xref:System.Security.Principal.WindowsIdentity> через асинхронные точки.</span><span class="sxs-lookup"><span data-stu-id="55044-130">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55044-131">Общеязыковая среда выполнения (CLR) осведомлена об операциях олицетворения, выполняемых только с помощью управляемого кода, а не олицетворения, выполненных за пределами управляемого кода, например посредством вызова неуправляемого кода платформой или прямых вызовов функций Win32.</span><span class="sxs-lookup"><span data-stu-id="55044-131">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="55044-132">Только управляемые <xref:System.Security.Principal.WindowsIdentity> объекты могут передаваться по асинхронным точкам, если только `alwaysFlowImpersonationPolicy` элемент не имеет значение true ( `<alwaysFlowImpersonationPolicy enabled="true"/>` ).</span><span class="sxs-lookup"><span data-stu-id="55044-132">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="55044-133">Если задать `alwaysFlowImpersonationPolicy` для элемента значение true, удостоверение Windows всегда проходит через асинхронные точки независимо от того, как было выполнено олицетворение.</span><span class="sxs-lookup"><span data-stu-id="55044-133">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="55044-134">Дополнительные сведения о передаче неуправляемого олицетворения через асинхронные точки см. в разделе [ \<alwaysFlowImpersonationPolicy> element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="55044-134">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="55044-135">Это поведение по умолчанию можно изменить двумя способами.</span><span class="sxs-lookup"><span data-stu-id="55044-135">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="55044-136">В управляемом коде на основе каждого потока.</span><span class="sxs-lookup"><span data-stu-id="55044-136">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="55044-137">Можно подавить поток на основе каждого потока, изменив <xref:System.Threading.ExecutionContext> Параметры и с <xref:System.Security.SecurityContext> помощью <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> метода, или <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="55044-137">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="55044-138">В вызове неуправляемого интерфейса размещения для загрузки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="55044-138">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="55044-139">Если для загрузки среды CLR используется неуправляемый интерфейс размещения (вместо простого управляемого исполняемого файла), можно указать специальный флаг в вызове функции [функции CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="55044-139">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="55044-140">Чтобы включить режим совместимости для всего процесса, присвойте `flags` параметру [функции CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) значение STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="55044-140">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="55044-141">Дополнительные сведения см. в описании [ \<alwaysFlowImpersonationPolicy> элемента](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="55044-141">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="55044-142">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="55044-142">Configuration File</span></span>  

 <span data-ttu-id="55044-143">В приложении платформа .NET Framework этот элемент можно использовать только в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="55044-143">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="55044-144">Для приложения ASP.NET поток олицетворения можно настроить в файле aspnet.config, который находится в \<Windows Folder> каталоге \микрософт.нет\фрамеворк\вкс.КС.кскскскс.</span><span class="sxs-lookup"><span data-stu-id="55044-144">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="55044-145">ASP.NET по умолчанию отключает поток олицетворения в файле aspnet.config с помощью следующих параметров конфигурации:</span><span class="sxs-lookup"><span data-stu-id="55044-145">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="55044-146">В ASP.NET, если требуется разрешить поток олицетворения, необходимо явно использовать следующие параметры конфигурации:</span><span class="sxs-lookup"><span data-stu-id="55044-146">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="55044-147">Пример</span><span class="sxs-lookup"><span data-stu-id="55044-147">Example</span></span>  

 <span data-ttu-id="55044-148">В следующем примере показано, как задать устаревшее поведение, которое не пополняет удостоверение Windows в асинхронных точках.</span><span class="sxs-lookup"><span data-stu-id="55044-148">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55044-149">См. также</span><span class="sxs-lookup"><span data-stu-id="55044-149">See also</span></span>

- [<span data-ttu-id="55044-150">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="55044-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="55044-151">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="55044-151">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="55044-152">\<alwaysFlowImpersonationPolicy> Элемент</span><span class="sxs-lookup"><span data-stu-id="55044-152">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
