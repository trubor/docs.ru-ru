---
description: 'Дополнительные сведения: <serviceMetadata>'
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: b519de04c333f9ddc12de72757587c9b38f29dba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682830"
---
# \<serviceMetadata>

<span data-ttu-id="ee017-102">Задает публикацию метаданных службы и связанных сведений.</span><span class="sxs-lookup"><span data-stu-id="ee017-102">Specifies the publication of service metadata and associated information.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="ee017-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ee017-103">Syntax</span></span>  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee017-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ee017-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ee017-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ee017-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee017-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ee017-106">Attributes</span></span>  
  
|<span data-ttu-id="ee017-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ee017-107">Attribute</span></span>|<span data-ttu-id="ee017-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ee017-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee017-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="ee017-109">externalMetadataLocation</span></span>|<span data-ttu-id="ee017-110">Универсальный код ресурса (URI), содержащий местоположение WSDL-файла, возвращаемый пользователю в ответ на запросы WSDL и MEX, вместо автоматически создаваемых WSDL.</span><span class="sxs-lookup"><span data-stu-id="ee017-110">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="ee017-111">Если атрибут не задан, по умолчанию возвращается WSDL.</span><span class="sxs-lookup"><span data-stu-id="ee017-111">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="ee017-112">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="ee017-112">The default is an empty string.</span></span>|  
|<span data-ttu-id="ee017-113">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="ee017-113">httpGetBinding</span></span>|<span data-ttu-id="ee017-114">Строковое значение, в котором указывается тип привязки, используемой для загрузки метаданных посредством HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="ee017-114">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="ee017-115">Это необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="ee017-115">This setting is optional.</span></span> <span data-ttu-id="ee017-116">Если он не указан, то будут использоваться привязки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ee017-116">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="ee017-117">Поддерживаются только привязки с внутренними элементами привязки, поддерживающими <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="ee017-117">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="ee017-118">Кроме этого, свойство <xref:System.ServiceModel.Channels.MessageVersion> привязки должно иметь значение <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee017-118">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="ee017-119">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee017-119">httpGetBindingConfiguration</span></span>|<span data-ttu-id="ee017-120">Строка, задающая имя привязки, указанной атрибутом `httpGetBinding`, который ссылается на дополнительные сведения конфигурации этой привязки.</span><span class="sxs-lookup"><span data-stu-id="ee017-120">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="ee017-121">Такое же имя должно быть задано в разделе `<bindings>`.</span><span class="sxs-lookup"><span data-stu-id="ee017-121">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="ee017-122">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="ee017-122">httpGetEnabled</span></span>|<span data-ttu-id="ee017-123">Логическое значение, указывающее, следует ли опубликовывать метаданные службы для извлечения с помощью запроса HTTP-GET.</span><span class="sxs-lookup"><span data-stu-id="ee017-123">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="ee017-124">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="ee017-124">The default is `false`.</span></span><br /><br /> <span data-ttu-id="ee017-125">Если атрибут httpGetUrl не указан, адрес, по которому публикуются метаданные, - это адрес службы плюс «?wsdl».</span><span class="sxs-lookup"><span data-stu-id="ee017-125">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="ee017-126">Например, если адрес службы — `http://localhost:8080/CalculatorService` , адрес МЕТАДАННЫХ HTTP/Get — `http://localhost:8080/CalculatorService?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="ee017-126">For example, if the service address is `http://localhost:8080/CalculatorService`, the HTTP/Get metadata address is `http://localhost:8080/CalculatorService?wsdl`.</span></span><br /><br /> <span data-ttu-id="ee017-127">Если это свойство имеет значение `false` или адрес службы не основан на HTTP или HTTPS, "? WSDL" игнорируется.</span><span class="sxs-lookup"><span data-stu-id="ee017-127">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="ee017-128">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="ee017-128">httpGetUrl</span></span>|<span data-ttu-id="ee017-129">URI, указывающий адрес, по которому метаданные публикуются для извлечения с использованием запроса HTTP-GET.</span><span class="sxs-lookup"><span data-stu-id="ee017-129">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="ee017-130">Если указан относительный URI, то он будет обрабатываться относительно базового адреса службы.</span><span class="sxs-lookup"><span data-stu-id="ee017-130">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="ee017-131">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="ee017-131">httpsGetBinding</span></span>|<span data-ttu-id="ee017-132">Строковое значение, в котором указывается тип привязки, используемой для загрузки метаданных посредством HTTPS GET.</span><span class="sxs-lookup"><span data-stu-id="ee017-132">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="ee017-133">Это необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="ee017-133">This setting is optional.</span></span> <span data-ttu-id="ee017-134">Если он не указан, то будут использоваться привязки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ee017-134">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="ee017-135">Поддерживаются только привязки с внутренними элементами привязки, поддерживающими <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="ee017-135">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="ee017-136">Кроме этого, свойство <xref:System.ServiceModel.Channels.MessageVersion> привязки должно иметь значение <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee017-136">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="ee017-137">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee017-137">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="ee017-138">Строка, задающая имя привязки, указанной атрибутом `httpsGetBinding`, который ссылается на дополнительные сведения конфигурации этой привязки.</span><span class="sxs-lookup"><span data-stu-id="ee017-138">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="ee017-139">Такое же имя должно быть задано в разделе `<bindings>`.</span><span class="sxs-lookup"><span data-stu-id="ee017-139">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="ee017-140">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="ee017-140">httpsGetEnabled</span></span>|<span data-ttu-id="ee017-141">Логическое значение, указывающее, следует ли опубликовывать метаданные службы для извлечения с помощью запроса HTTPS-GET.</span><span class="sxs-lookup"><span data-stu-id="ee017-141">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="ee017-142">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="ee017-142">The default is `false`.</span></span><br /><br /> <span data-ttu-id="ee017-143">Если атрибут httpsGetUrl не указан, адрес, по которому публикуются метаданные, - это адрес службы плюс «?wsdl».</span><span class="sxs-lookup"><span data-stu-id="ee017-143">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="ee017-144">Например, если адрес службы — " https://localhost:8080/CalculatorService ", адрес МЕТАДАННЫХ HTTP/GET — " https://localhost:8080/CalculatorService?wsdl ".</span><span class="sxs-lookup"><span data-stu-id="ee017-144">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="ee017-145">Если это свойство имеет значение `false` или адрес службы не основан на HTTP или HTTPS, "? WSDL" игнорируется.</span><span class="sxs-lookup"><span data-stu-id="ee017-145">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="ee017-146">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="ee017-146">httpsGetUrl</span></span>|<span data-ttu-id="ee017-147">URI, указывающий адрес, по которому метаданные публикуются для извлечения с использованием запроса HTTPS-GET.</span><span class="sxs-lookup"><span data-stu-id="ee017-147">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="ee017-148">policyVersion</span><span class="sxs-lookup"><span data-stu-id="ee017-148">policyVersion</span></span>|<span data-ttu-id="ee017-149">Строка, указывающая версию используемой спецификации Web Services Policy.</span><span class="sxs-lookup"><span data-stu-id="ee017-149">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="ee017-150">Это атрибут типа <xref:System.ServiceModel.Description.PolicyVersion>.</span><span class="sxs-lookup"><span data-stu-id="ee017-150">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee017-151">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ee017-151">Child Elements</span></span>  

 <span data-ttu-id="ee017-152">None</span><span class="sxs-lookup"><span data-stu-id="ee017-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee017-153">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ee017-153">Parent Elements</span></span>  
  
|<span data-ttu-id="ee017-154">Элемент</span><span class="sxs-lookup"><span data-stu-id="ee017-154">Element</span></span>|<span data-ttu-id="ee017-155">Описание</span><span class="sxs-lookup"><span data-stu-id="ee017-155">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ee017-156">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="ee017-156">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee017-157">Remarks</span><span class="sxs-lookup"><span data-stu-id="ee017-157">Remarks</span></span>  

 <span data-ttu-id="ee017-158">Элемент конфигурации позволяет управлять возможностями публикации метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="ee017-158">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="ee017-159">Чтобы предотвратить непреднамеренное раскрытие потенциально конфиденциальных метаданных службы, конфигурация по умолчанию для служб Windows Communication Foundation (WCF) отключает публикацию метаданных.</span><span class="sxs-lookup"><span data-stu-id="ee017-159">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="ee017-160">Такое расширение функциональности по умолчанию защищено, но это также означает, что при этом невозможно использовать средство импорта метаданных (например, Svcutil.exe) для создания клиентского кода, необходимого для вызова службы, если поведение публикации не включено явно в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ee017-160">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="ee017-161">Включить такое поведение публикации для службы можно с помощью элемента конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ee017-161">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="ee017-162">Подробный пример настройки этого поведения см. в разделе [поведение публикации метаданных](../../../wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="ee017-162">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="ee017-163">Дополнительные атрибуты `httpGetBinding` и `httpsGetBinding` позволяют настроить привязки, используемые для извлечения метаданных посредством HTTP-GET (или HTTPS-GET).</span><span class="sxs-lookup"><span data-stu-id="ee017-163">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="ee017-164">Если они не заданы, для извлечения метаданных применяются привязки по умолчанию (`HttpTransportBindingElement` для HTTP и `HttpsTransportBindingElement` для HTTPS).</span><span class="sxs-lookup"><span data-stu-id="ee017-164">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="ee017-165">Обратите внимание, что эти атрибуты нельзя использовать вместе со встроенными привязками WCF.</span><span class="sxs-lookup"><span data-stu-id="ee017-165">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="ee017-166">Поддерживаются только привязки с внутренними элементами привязки, поддерживающими <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="ee017-166">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="ee017-167">Кроме этого, свойство <xref:System.ServiceModel.Channels.MessageVersion> привязки должно иметь значение <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee017-167">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="ee017-168">Для снижения подверженности службы действиям недобросовестных пользователей перенос можно защитить с помощью механизма SSL по протоколу HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="ee017-168">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="ee017-169">Для этого необходимо вначале выполнить привязку подходящего сертификата X.509 к конкретному порту компьютера, на котором размещена служба.</span><span class="sxs-lookup"><span data-stu-id="ee017-169">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="ee017-170">(Дополнительные сведения см. в разделе [Работа с сертификатами](../../../wcf/feature-details/working-with-certificates.md).) Во вторых, добавьте этот элемент в конфигурацию службы и присвойте `httpsGetEnabled` атрибуту значение `true` .</span><span class="sxs-lookup"><span data-stu-id="ee017-170">(For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="ee017-171">После этого следует присвоить атрибуту `httpsGetUrl` URL-адрес конечной точки метаданных службы, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ee017-171">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a><span data-ttu-id="ee017-172">Пример</span><span class="sxs-lookup"><span data-stu-id="ee017-172">Example</span></span>  

 <span data-ttu-id="ee017-173">В следующем примере служба настраивается для предоставления метаданных с помощью \<serviceMetadata> элемента.</span><span class="sxs-lookup"><span data-stu-id="ee017-173">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="ee017-174">Здесь также настраивается конечная точка предоставления доступа к контракту `IMetadataExchange` как реализации протокола WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="ee017-174">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="ee017-175">В примере используется привязка `mexHttpBinding`, являющаяся удобной стандартной привязкой, эквивалентной привязке `wsHttpBinding` с режимом безопасности `None`.</span><span class="sxs-lookup"><span data-stu-id="ee017-175">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="ee017-176">В конечной точке используется относительный адрес MEX, который при разрешении по базовому адресу служб приводит к адресу конечной точки `http://localhost/servicemodelsamples/service.svc/mex` .</span><span class="sxs-lookup"><span data-stu-id="ee017-176">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="ee017-177">См. также</span><span class="sxs-lookup"><span data-stu-id="ee017-177">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="ee017-178">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="ee017-178">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ee017-179">Поведение публикации метаданных</span><span class="sxs-lookup"><span data-stu-id="ee017-179">Metadata Publishing Behavior</span></span>](../../../wcf/samples/metadata-publishing-behavior.md)
