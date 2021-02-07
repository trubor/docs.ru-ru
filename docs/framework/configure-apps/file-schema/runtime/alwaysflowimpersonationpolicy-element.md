---
description: 'Дополнительные сведения о: <alwaysFlowImpersonationPolicy> element'
title: Элемент <alwaysFlowImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 5ee8e763eddb810143522ce9e6df780ee77c26c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719374"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="37575-103">Элемент \<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="37575-103">\<alwaysFlowImpersonationPolicy> Element</span></span>

<span data-ttu-id="37575-104">Указывает, что удостоверение Windows всегда проходит через асинхронные точки, независимо от того, как было выполнено олицетворение.</span><span class="sxs-lookup"><span data-stu-id="37575-104">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a><span data-ttu-id="37575-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37575-105">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37575-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="37575-106">Attributes and Elements</span></span>  

 <span data-ttu-id="37575-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="37575-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37575-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="37575-108">Attributes</span></span>  
  
|<span data-ttu-id="37575-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="37575-109">Attribute</span></span>|<span data-ttu-id="37575-110">Описание</span><span class="sxs-lookup"><span data-stu-id="37575-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="37575-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="37575-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="37575-112">Указывает, проходит ли идентификация Windows между асинхронными точками.</span><span class="sxs-lookup"><span data-stu-id="37575-112">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="37575-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="37575-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="37575-114">Значение</span><span class="sxs-lookup"><span data-stu-id="37575-114">Value</span></span>|<span data-ttu-id="37575-115">Описание</span><span class="sxs-lookup"><span data-stu-id="37575-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="37575-116">Удостоверение Windows не передается через асинхронные точки, если олицетворение не выполняется через управляемые методы, такие как <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> .</span><span class="sxs-lookup"><span data-stu-id="37575-116">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="37575-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="37575-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="37575-118">Удостоверение Windows всегда проходит через асинхронные точки независимо от того, как было выполнено олицетворение.</span><span class="sxs-lookup"><span data-stu-id="37575-118">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37575-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="37575-119">Child Elements</span></span>  

 <span data-ttu-id="37575-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="37575-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37575-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="37575-121">Parent Elements</span></span>  
  
|<span data-ttu-id="37575-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="37575-122">Element</span></span>|<span data-ttu-id="37575-123">Описание</span><span class="sxs-lookup"><span data-stu-id="37575-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="37575-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37575-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="37575-125">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="37575-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37575-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="37575-126">Remarks</span></span>  

 <span data-ttu-id="37575-127">В платформа .NET Framework версиях 1,0 и 1,1 идентификатор Windows не проходит через асинхронные точки.</span><span class="sxs-lookup"><span data-stu-id="37575-127">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="37575-128">В платформа .NET Framework версии 2,0 имеется <xref:System.Threading.ExecutionContext> объект, который содержит сведения о выполняемом в данный момент потоке и передает его между асинхронными точками в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="37575-128">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="37575-129">Также передается <xref:System.Security.Principal.WindowsIdentity> как часть информации, которая проходит через асинхронные точки, при условии, что олицетворение достигается с помощью управляемых методов, таких как <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> , а не с помощью других средств, таких как вызов неуправляемого кода в машинные методы.</span><span class="sxs-lookup"><span data-stu-id="37575-129">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="37575-130">Этот элемент позволяет указать, что удостоверение Windows выполняет потоковую передачу через асинхронные точки независимо от того, как было достигнуто олицетворение.</span><span class="sxs-lookup"><span data-stu-id="37575-130">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="37575-131">Это поведение по умолчанию можно изменить двумя способами.</span><span class="sxs-lookup"><span data-stu-id="37575-131">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="37575-132">В управляемом коде на основе каждого потока.</span><span class="sxs-lookup"><span data-stu-id="37575-132">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="37575-133">Можно подавить поток на основе каждого потока, изменив <xref:System.Threading.ExecutionContext> Параметры и с <xref:System.Security.SecurityContext> помощью <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> метода, или <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="37575-133">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="37575-134">В вызове неуправляемого интерфейса размещения для загрузки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="37575-134">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="37575-135">Если для загрузки среды CLR используется неуправляемый интерфейс размещения (вместо простого управляемого исполняемого файла), можно указать специальный флаг в вызове функции [функции CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="37575-135">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="37575-136">Чтобы включить режим совместимости для всего процесса, задайте для `flags` параметра [CorBindToRuntimeEx функции](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) значение `STARTUP_ALWAYSFLOW_IMPERSONATION` .</span><span class="sxs-lookup"><span data-stu-id="37575-136">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="37575-137">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="37575-137">Configuration File</span></span>  

 <span data-ttu-id="37575-138">В приложении платформа .NET Framework этот элемент можно использовать только в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="37575-138">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="37575-139">Для приложения ASP.NET поток олицетворения можно настроить в файле aspnet.config, который находится в \<Windows Folder> каталоге \микрософт.нет\фрамеворк\вкс.КС.кскскскс.</span><span class="sxs-lookup"><span data-stu-id="37575-139">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="37575-140">ASP.NET по умолчанию отключает поток олицетворения в файле aspnet.config с помощью следующих параметров конфигурации:</span><span class="sxs-lookup"><span data-stu-id="37575-140">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="37575-141">В ASP.NET, если требуется разрешить поток олицетворения, необходимо явно использовать следующие параметры конфигурации:</span><span class="sxs-lookup"><span data-stu-id="37575-141">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="37575-142">Пример</span><span class="sxs-lookup"><span data-stu-id="37575-142">Example</span></span>  

 <span data-ttu-id="37575-143">В следующем примере показано, как указать, что удостоверение Windows проходит через асинхронные точки, даже если олицетворение достигается через средства, отличные от управляемых методов.</span><span class="sxs-lookup"><span data-stu-id="37575-143">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37575-144">См. также</span><span class="sxs-lookup"><span data-stu-id="37575-144">See also</span></span>

- [<span data-ttu-id="37575-145">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="37575-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="37575-146">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="37575-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="37575-147">\<legacyImpersonationPolicy> Элемент</span><span class="sxs-lookup"><span data-stu-id="37575-147">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
