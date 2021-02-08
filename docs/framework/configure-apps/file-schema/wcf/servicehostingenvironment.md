---
description: 'Дополнительные сведения: <serviceHostingEnvironment>'
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 95243a1cf9cea734b7f35a1400a8b5b865767976
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786724"
---
# \<serviceHostingEnvironment>

<span data-ttu-id="c9ffa-102">Этот элемент определяет тип, который среда размещения служб создает для определенного транспорта.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="c9ffa-103">Если этот элемент является пустым, используется тип, применяемый по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="c9ffa-104">Этот элемент может применяться только на уровне файлов конфигурации приложения или компьютера.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**  
  
## <a name="syntax"></a><span data-ttu-id="c9ffa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9ffa-105">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9ffa-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c9ffa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c9ffa-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9ffa-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c9ffa-108">Attributes</span></span>  
  
|<span data-ttu-id="c9ffa-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c9ffa-109">Attribute</span></span>|<span data-ttu-id="c9ffa-110">Описание</span><span class="sxs-lookup"><span data-stu-id="c9ffa-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9ffa-111">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="c9ffa-111">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="c9ffa-112">Логическое значение, указывающее, включен ли режим совместимости ASP.NET для текущего приложения.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-112">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="c9ffa-113">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="c9ffa-114">Если этот атрибут имеет значение `true` , запросы к службам Windows Communication Foundation (WCF) проходят через конвейер HTTP ASP.NET, и связь по протоколам, отличным от HTTP, запрещена.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-114">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="c9ffa-115">Дополнительные сведения см. в разделе [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="c9ffa-115">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="c9ffa-116">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="c9ffa-116">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="c9ffa-117">Целое число, указывающее минимальный объем свободной памяти, который должен быть доступен системе, прежде чем служба WCF сможет быть активирована.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-117">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="c9ffa-118">**Внимание!**  Если указать этот атрибут вместе с частичным доверием в web.configном файле службы WCF, то при запуске службы будет возникать исключение <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="c9ffa-118">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="c9ffa-119">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="c9ffa-119">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="c9ffa-120">Логическое значение, которое определяет, разрешается ли использование нескольких привязок IIS для одного узла.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-120">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="c9ffa-121">Службы IIS состоят из веб-узлов, являющихся контейнерами виртуальных приложений, содержащих виртуальные каталоги.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-121">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="c9ffa-122">Доступ к приложению на узле можно осуществлять через одну или несколько привязок IIS.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-122">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="c9ffa-123">Привязка IIS предоставляет два блока данных: протокол привязки и данные привязки.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-123">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="c9ffa-124">Протокол привязки определяет схему, посредством которой осуществляется связь, а данные привязки содержат сведения, используемые для доступа к узлу.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-124">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="c9ffa-125">Примером протокола привязки является HTTP, в котором данные привязки могут содержать IP-адрес, порт, заголовок узла и т. п.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-125">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="c9ffa-126">IIS поддерживает задание нескольких привязок IIS для каждого узла, что позволяет использовать несколько базовых адресов для каждой схемы.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-126">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="c9ffa-127">Однако служба Windows Communication Foundation (WCF), размещенная на сайте, позволяет привязать только к одному baseAddress на схему.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-127">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="c9ffa-128">Чтобы включить несколько привязок IIS на сайт для службы Windows Communication Foundation (WCF), присвойте этому атрибуту значение `true` .</span><span class="sxs-lookup"><span data-stu-id="c9ffa-128">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="c9ffa-129">Следует иметь в виду, что привязки к нескольким узлам поддерживаются только в протоколе HTTP.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-129">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="c9ffa-130">Адрес конечной точки в файле конфигурации должен быть полным URI.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-130">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9ffa-131">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c9ffa-131">Child Elements</span></span>  
  
|<span data-ttu-id="c9ffa-132">Элемент</span><span class="sxs-lookup"><span data-stu-id="c9ffa-132">Element</span></span>|<span data-ttu-id="c9ffa-133">Описание</span><span class="sxs-lookup"><span data-stu-id="c9ffa-133">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="c9ffa-134">Коллекция элементов конфигурации, которые задают префиксные фильтры для базовых адресов, используемых узлом службы.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-134">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[\<serviceActivations>](serviceactivations.md)|<span data-ttu-id="c9ffa-135">Раздел конфигурации, в котором описываются параметры активации.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-135">A configuration section that describes activation settings.</span></span>|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="c9ffa-136">Коллекция элементов конфигурации, которые определяют тип конкретного транспорта.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-136">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9ffa-137">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c9ffa-137">Parent Elements</span></span>  
  
|<span data-ttu-id="c9ffa-138">Элемент</span><span class="sxs-lookup"><span data-stu-id="c9ffa-138">Element</span></span>|<span data-ttu-id="c9ffa-139">Описание</span><span class="sxs-lookup"><span data-stu-id="c9ffa-139">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9ffa-140">serviceModel</span><span class="sxs-lookup"><span data-stu-id="c9ffa-140">serviceModel</span></span>|<span data-ttu-id="c9ffa-141">Корневой элемент всех элементов конфигурации Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c9ffa-141">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9ffa-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9ffa-142">Remarks</span></span>  

 <span data-ttu-id="c9ffa-143">По умолчанию службы WCF выполняются параллельно с ASP.NET в размещенных доменах приложений (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="c9ffa-143">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="c9ffa-144">Хотя WCF и ASP.NET могут существовать вместе в одном домене приложений, по умолчанию конвейер HTTP ASP.NET не обрабатывает запросы WCF.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-144">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="c9ffa-145">В результате несколько элементов платформы приложений ASP.NET будут недоступны службам WCF.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-145">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="c9ffa-146">К ним относятся</span><span class="sxs-lookup"><span data-stu-id="c9ffa-146">These include</span></span>  
  
- <span data-ttu-id="c9ffa-147">Авторизация файла/URL-адреса ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c9ffa-147">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="c9ffa-148">Олицетворение ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c9ffa-148">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="c9ffa-149">Состояние сеанса на основании файлов Cookie</span><span class="sxs-lookup"><span data-stu-id="c9ffa-149">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="c9ffa-150">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="c9ffa-150">HttpContext.Current</span></span>  
  
- <span data-ttu-id="c9ffa-151">Расширяемость конвейера через настраиваемый элемент HttpModule</span><span class="sxs-lookup"><span data-stu-id="c9ffa-151">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="c9ffa-152">Если службам WCF нужно функционировать в контексте ASP.NET и взаимодействовать только по протоколу HTTP, можно использовать режим совместимости ASP.NET WCF.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-152">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="c9ffa-153">Этот режим включается, когда атрибут `aspNetCompatibilityEnabled` имеет значение `true` на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-153">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="c9ffa-154">В реализации службы должна быть объявлена возможность выполнения в режиме совместимости с помощью класса <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-154">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="c9ffa-155">Если режим совместимости включен, это приводит к следующему.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-155">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="c9ffa-156">Авторизация файла/URL-адреса ASP.NET принудительно выполняется до авторизации WCF.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-156">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="c9ffa-157">Решение об авторизации основано на удостоверении запроса уровня транспорта.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-157">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="c9ffa-158">Удостоверения уровня сообщения не учитываются.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-158">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="c9ffa-159">Операции служб WCF начинают выполняться в контексте олицетворения ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-159">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="c9ffa-160">Если для конкретной службы включены и олицетворение ASP.NET, и олицетворение WCF, применяется контекст олицетворения WCF.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-160">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="c9ffa-161">HttpContext.Current может использоваться из кода службы WCF, и предотвращается представление службами конечных точек, работающих по протоколу, отличному от HTTP.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-161">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="c9ffa-162">Запросы WCF обрабатываются конвейером ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-162">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="c9ffa-163">Элемент HttpModules, заданный для обработки входящих запросов, также может обрабатывать запросы WCF.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-163">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="c9ffa-164">Они могут включать компоненты платформы ASP.NET (например, <xref:System.Web.SessionState.SessionStateModule>), а также настраиваемые модули сторонних поставщиков.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-164">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9ffa-165">Пример</span><span class="sxs-lookup"><span data-stu-id="c9ffa-165">Example</span></span>  

 <span data-ttu-id="c9ffa-166">В следующем образце кода показано, как включить режим совместимости ASP.</span><span class="sxs-lookup"><span data-stu-id="c9ffa-166">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="c9ffa-167">Код</span><span class="sxs-lookup"><span data-stu-id="c9ffa-167">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="c9ffa-168">См. также</span><span class="sxs-lookup"><span data-stu-id="c9ffa-168">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="c9ffa-169">Размещение</span><span class="sxs-lookup"><span data-stu-id="c9ffa-169">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="c9ffa-170">Службы WCF и ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c9ffa-170">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
