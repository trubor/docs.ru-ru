---
description: 'Дополнительные сведения: страница справки веб-службы HTTP WCF'
title: Страница справки веб-службы HTTP WCF
ms.date: 03/30/2017
ms.assetid: 63c7c695-44b6-4f31-bb9c-00f2763f525e
ms.openlocfilehash: 30025eec04402f8112197a95cee0efed093a0ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752643"
---
# <a name="wcf-web-http-service-help-page"></a><span data-ttu-id="36d75-103">Страница справки веб-службы HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="36d75-103">WCF Web HTTP Service Help Page</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="36d75-104">предоставляет автоматическую справочную страницу для службы WCF WEB HTTP.</span><span class="sxs-lookup"><span data-stu-id="36d75-104">provides an automatic help page for WCF WEB HTTP services.</span></span> <span data-ttu-id="36d75-105">На этой странице справки приводится описание каждой операции, форматов запроса и ответа, а также схем.</span><span class="sxs-lookup"><span data-stu-id="36d75-105">This help page lists a description of each operation, request and response formats, and schemas.</span></span> <span data-ttu-id="36d75-106">По умолчанию эта функциональная возможность отключена.</span><span class="sxs-lookup"><span data-stu-id="36d75-106">This functionality is turned off by default.</span></span> <span data-ttu-id="36d75-107">При просмотре пользователем веб-службы HTTP WCF и добавлении "/Help" в конец URL-адреса, например `http://localhost:8000/Customers/Help` , отображается страница справки, подобная приведенной ниже.</span><span class="sxs-lookup"><span data-stu-id="36d75-107">When a user browses to a WCF WEB HTTP service and appends "/Help" on to the end of the URL, for example `http://localhost:8000/Customers/Help`, a help page like the following is displayed.</span></span>  
  
 ![Откроется браузер с открытой страницей справки WCF.](./media/wcf-web-http-service-help-page/windows-communication-foundation-rest-help-page.gif)  
  
 <span data-ttu-id="36d75-109">Затем пользователь может щелкнуть любой метод из представленных на странице справки. Откроется страница, содержащая подробные сведения о методе, включая форматы сообщений и примеры ответов.</span><span class="sxs-lookup"><span data-stu-id="36d75-109">The user can then click any method listed in the help page and detailed page for that operation is displayed showing more information about the method, including message formats and example responses.</span></span> <span data-ttu-id="36d75-110">На следующем рисунке представлен пример справочной страницы для метода.</span><span class="sxs-lookup"><span data-stu-id="36d75-110">The following image is an example of a help page for a method.</span></span>  
  
 ![Браузер с подробными сведениями о странице справки WCF для метода Customers Open.](./media/wcf-web-http-service-help-page/windows-communication-foundation-rest-help-page-detail.gif)  
  
## <a name="using-the-wcf-web-http-help-page"></a><span data-ttu-id="36d75-112">Использование справочной страницы службы WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="36d75-112">Using the WCF Web HTTP Help Page</span></span>  

 <span data-ttu-id="36d75-113">На справочной странице службы WCF WEB HTTP дано краткое описание для каждой из представленных операций при условии, что оно было определено в <xref:System.ComponentModel.DescriptionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="36d75-113">The WCF WEB HTTP Help page displays a short description for each operation provided that you specify one using the <xref:System.ComponentModel.DescriptionAttribute>.</span></span> <span data-ttu-id="36d75-114">Этот атрибут принимает строку, которая содержит краткое описание операции, для которой он применен.</span><span class="sxs-lookup"><span data-stu-id="36d75-114">This attribute takes a string that contains a short description of the operation it is applied to.</span></span> <span data-ttu-id="36d75-115">Например, в следующем коде показано, как задать краткое описание с помощью <xref:System.ComponentModel.DescriptionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="36d75-115">For example, the following code shows how to use the <xref:System.ComponentModel.DescriptionAttribute> to provide a short description.</span></span>  
  
```csharp
[OperationContract]  
[WebGet(UriTemplate="/template1", BodyStyle = WebMessageBodyStyle.Bare)]  
[Description("Description for GET /template1")]  
SyndicationFeedFormatter GetTemplate1();  
```  
  
 <span data-ttu-id="36d75-116">Чтобы включить справочную страницу службы WCF WEB http, в конечные точки службы необходимо добавить соответствующее поведение.</span><span class="sxs-lookup"><span data-stu-id="36d75-116">To turn on the WCF WEB HTTP Help page, you must add an endpoint behavior to your service's endpoints.</span></span> <span data-ttu-id="36d75-117">Это можно сделать из кода или через файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="36d75-117">This can be done in configuration or code.</span></span> <span data-ttu-id="36d75-118">Чтобы включить справочную страницу службы WCF WEB HTTP в файле конфигурации, добавьте поведение конечной точки с элементом `<webHttp>``enableHelp`, установите `true` в значение, добавьте конечную точку и настройте ее для использования поведения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="36d75-118">To enable the WCF WEB HTTP Help age in configuration, add an endpoint behavior with a `<webHttp>` element, set `enableHelp` to `true`, and add an endpoint and configure it to use the endpoint behavior.</span></span> <span data-ttu-id="36d75-119">В следующем коде конфигурации показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="36d75-119">The following configuration code shows how to do this.</span></span>  
  
```xml  
<endpointBehaviors>  
   <behavior name="RESTEndpointBehavior">  
      <webHttp enableHelp="true"/>  
   </behavior>  
</endpointBehaviors>  
<!-- ... -->  
<services>  
   <service behaviorConfiguration="RESTWebServiceBehavior" name="RESTWebService">      <endpoint address="" kind="webHttpEndpoint" behaviorConfiguration="RESTEndpointBehavior" contract="IHello" />  
  
      <!-- ... -->  
   </service>  
</services>  
```  
  
 <span data-ttu-id="36d75-120">Чтобы включить справочную страницу службы WCF WEB HTTP из кода, добавьте конечную точку службы и добавьте <xref:System.ServiceModel.Description.WebHttpBehavior> к параметру конечной точки <xref:System.ServiceModel.Description.WebHttpBehavior.HelpEnabled%2A> со значением `true`.</span><span class="sxs-lookup"><span data-stu-id="36d75-120">To enable the WCF Web HTTP Help page in code, add a service endpoint and add a <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint setting <xref:System.ServiceModel.Description.WebHttpBehavior.HelpEnabled%2A> to `true`.</span></span> <span data-ttu-id="36d75-121">В следующем примере кода показано, как это сделать:</span><span class="sxs-lookup"><span data-stu-id="36d75-121">The following code shows how to do this.</span></span>  
  
```csharp
using (WebServiceHost host = new WebServiceHost(typeof(Service), new Uri("http://localhost:8000/Customers")))  
{  
   host.AddServiceEndpoint(typeof(ICustomerCollection), new WebHttpBinding(), "");
   host.Description.Endpoints[0].Behaviors.Add(new WebHttpBehavior { EnableHelp = true });  
   // ...  
}  
```  
  
 <span data-ttu-id="36d75-122">Справочная страница построена на основе формата XHTML, где разметка определяет различные части страницы.</span><span class="sxs-lookup"><span data-stu-id="36d75-122">The help page is XHTML based with mark-up that identifies the different parts of the page.</span></span> <span data-ttu-id="36d75-123">Это позволяет клиентам производить программный доступ к странице через объект <xref:System.Xml.Linq.XElement> или другие API-интерфейсы XLinq.</span><span class="sxs-lookup"><span data-stu-id="36d75-123">This enables clients to programmatically access the page using <xref:System.Xml.Linq.XElement> or other XLinq APIs.</span></span>  
  
## <a name="schemas-used-in-the-wcf-web-http-service-help-page"></a><span data-ttu-id="36d75-124">Схемы, используемые на справочной странице веб-службы WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="36d75-124">Schemas Used in the WCF Web HTTP Service Help Page</span></span>  

 <span data-ttu-id="36d75-125">На справочной странице службы WCF Web HTTP используются следующие схемы.</span><span class="sxs-lookup"><span data-stu-id="36d75-125">The following schemas are used in the WCF Web HTTP service help page.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/" attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="http://schemas.microsoft.com/2003/10/Serialization/" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="anyType" nillable="true" type="xs:anyType" />  
  <xs:element name="anyURI" nillable="true" type="xs:anyURI" />  
  <xs:element name="base64Binary" nillable="true" type="xs:base64Binary" />  
  <xs:element name="boolean" nillable="true" type="xs:boolean" />  
  <xs:element name="byte" nillable="true" type="xs:byte" />  
  <xs:element name="dateTime" nillable="true" type="xs:dateTime" />  
  <xs:element name="decimal" nillable="true" type="xs:decimal" />  
  <xs:element name="double" nillable="true" type="xs:double" />  
  <xs:element name="float" nillable="true" type="xs:float" />  
  <xs:element name="int" nillable="true" type="xs:int" />  
  <xs:element name="long" nillable="true" type="xs:long" />  
  <xs:element name="QName" nillable="true" type="xs:QName" />  
  <xs:element name="short" nillable="true" type="xs:short" />  
  <xs:element name="string" nillable="true" type="xs:string" />  
  <xs:element name="unsignedByte" nillable="true" type="xs:unsignedByte" />  
  <xs:element name="unsignedInt" nillable="true" type="xs:unsignedInt" />  
  <xs:element name="unsignedLong" nillable="true" type="xs:unsignedLong" />  
  <xs:element name="unsignedShort" nillable="true" type="xs:unsignedShort" />  
  <xs:element name="char" nillable="true" type="tns:char" />  
  <xs:simpleType name="char">  
    <xs:restriction base="xs:int" />  
  </xs:simpleType>  
  <xs:element name="duration" nillable="true" type="tns:duration" />  
  <xs:simpleType name="duration">  
    <xs:restriction base="xs:duration">  
      <xs:pattern value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?" />  
      <xs:minInclusive value="-P10675199DT2H48M5.4775808S" />  
      <xs:maxInclusive value="P10675199DT2H48M5.4775807S" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:element name="guid" nillable="true" type="tns:guid" />  
  <xs:simpleType name="guid">  
    <xs:restriction base="xs:string">  
      <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:attribute name="FactoryType" type="xs:QName" />  
  <xs:attribute name="Id" type="xs:ID" />  
  <xs:attribute name="Ref" type="xs:IDREF" />  
</xs:schema>  
  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:tns="http://microsoft.com/wsdl/types/" elementFormDefault="qualified" targetNamespace="http://microsoft.com/wsdl/types/" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:simpleType name="guid">  
    <xs:restriction base="xs:string">  
      <xs:pattern value="[0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{12}" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="char">  
    <xs:restriction base="xs:unsignedShort" />  
  </xs:simpleType>  
</xs:schema>  
  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:tns="http://schemas.datacontract.org/2004/07/System" elementFormDefault="qualified" targetNamespace="http://schemas.datacontract.org/2004/07/System" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://schemas.microsoft.com/2003/10/Serialization/" />  
  <xs:complexType name="DateTimeOffset">  
    <xs:annotation>  
      <xs:appinfo>  
        <IsValueType xmlns="http://schemas.microsoft.com/2003/10/Serialization/">true</IsValueType>  
      </xs:appinfo>  
    </xs:annotation>  
    <xs:sequence>  
      <xs:element name="DateTime" type="xs:dateTime" />  
      <xs:element name="OffsetMinutes" type="xs:short" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="DateTimeOffset" nillable="true" type="tns:DateTimeOffset" />  
  <xs:complexType name="DBNull">  
    <xs:sequence />  
  </xs:complexType>  
  <xs:element name="DBNull" nillable="true" type="tns:DBNull" />  
</xs:schema>  
  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:ser="http://schemas.microsoft.com/2003/10/Serialization/" elementFormDefault="qualified" targetNamespace="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://schemas.microsoft.com/2003/10/Serialization/" />  
  <xs:complexType name="ArrayOfboolean">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="boolean" type="xs:boolean" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfboolean" nillable="true" type="tns:ArrayOfboolean" />  
  <xs:complexType name="ArrayOfchar">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="char" type="ser:char" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfchar" nillable="true" type="tns:ArrayOfchar" />  
  <xs:complexType name="ArrayOfdateTime">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="dateTime" type="xs:dateTime" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfdateTime" nillable="true" type="tns:ArrayOfdateTime" />  
  <xs:complexType name="ArrayOfdecimal">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="decimal" type="xs:decimal" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfdecimal" nillable="true" type="tns:ArrayOfdecimal" />  
  <xs:complexType name="ArrayOfdouble">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="double" type="xs:double" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfdouble" nillable="true" type="tns:ArrayOfdouble" />  
  <xs:complexType name="ArrayOffloat">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="float" type="xs:float" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOffloat" nillable="true" type="tns:ArrayOffloat" />  
  <xs:complexType name="ArrayOfguid">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="guid" type="ser:guid" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfguid" nillable="true" type="tns:ArrayOfguid" />  
  <xs:complexType name="ArrayOfint">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="int" type="xs:int" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfint" nillable="true" type="tns:ArrayOfint" />  
  <xs:complexType name="ArrayOflong">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="long" type="xs:long" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOflong" nillable="true" type="tns:ArrayOflong" />  
  <xs:complexType name="ArrayOfshort">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="short" type="xs:short" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfshort" nillable="true" type="tns:ArrayOfshort" />  
  <xs:complexType name="ArrayOfstring">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="string" nillable="true" type="xs:string" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfstring" nillable="true" type="tns:ArrayOfstring" />  
  <xs:complexType name="ArrayOfduration">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="duration" type="ser:duration" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfduration" nillable="true" type="tns:ArrayOfduration" />  
  <xs:complexType name="ArrayOfunsignedInt">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="unsignedInt" type="xs:unsignedInt" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfunsignedInt" nillable="true" type="tns:ArrayOfunsignedInt" />  
  <xs:complexType name="ArrayOfunsignedLong">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="unsignedLong" type="xs:unsignedLong" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfunsignedLong" nillable="true" type="tns:ArrayOfunsignedLong" />  
  <xs:complexType name="ArrayOfunsignedShort">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="unsignedShort" type="xs:unsignedShort" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfunsignedShort" nillable="true" type="tns:ArrayOfunsignedShort" />  
  <xs:complexType name="ArrayOfQName">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="unbounded" name="QName" nillable="true" type="xs:QName" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:element name="ArrayOfQName" nillable="true" type="tns:ArrayOfQName" />  
</xs:schema>  
```  
  
 <span data-ttu-id="36d75-126">Дополнительные сведения о схеме сериализации контракта данных см. в разделе [Справочник по схеме контракта данных](data-contract-schema-reference.md).</span><span class="sxs-lookup"><span data-stu-id="36d75-126">For more information about the data contract serialization schema, see [Data Contract Schema Reference](data-contract-schema-reference.md).</span></span>
