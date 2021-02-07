---
description: 'Дополнительные сведения: <baseAddressPrefixFilters>'
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 9212838393ead04bdcd475b314bb2707e6f899ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749679"
---
# \<baseAddressPrefixFilters>

<span data-ttu-id="1f52e-102">Представляет коллекцию элементов конфигурации, задающих сквозные фильтры, которые предоставляют механизм для выбора соответствующих привязок службы IIS (IIS) при размещении приложения Windows Communication Foundation (WCF) в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="1f52e-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1f52e-103">\<baseAddressPrefixFilters> не распознает "localhost"; Вместо этого используйте полное имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="1f52e-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**  
  
## <a name="syntax"></a><span data-ttu-id="1f52e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f52e-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f52e-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1f52e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1f52e-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1f52e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f52e-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f52e-107">Attributes</span></span>  

 <span data-ttu-id="1f52e-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1f52e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f52e-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1f52e-109">Child Elements</span></span>  
  
|<span data-ttu-id="1f52e-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="1f52e-110">Element</span></span>|<span data-ttu-id="1f52e-111">Описание</span><span class="sxs-lookup"><span data-stu-id="1f52e-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="1f52e-112">Добавляет элемент конфигурации, который задает префиксный фильтр для базовых адресов, используемых узлом службы.</span><span class="sxs-lookup"><span data-stu-id="1f52e-112">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f52e-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1f52e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="1f52e-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="1f52e-114">Element</span></span>|<span data-ttu-id="1f52e-115">Описание</span><span class="sxs-lookup"><span data-stu-id="1f52e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="1f52e-116">Определяет, какой тип среда размещения служб создает для конкретного транспорта.</span><span class="sxs-lookup"><span data-stu-id="1f52e-116">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f52e-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f52e-117">Remarks</span></span>  

 <span data-ttu-id="1f52e-118">Префиксный фильтр предоставляет способ для общих поставщиков услуг размещения задать, какие URI должны использоваться службой.</span><span class="sxs-lookup"><span data-stu-id="1f52e-118">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="1f52e-119">Это дает возможность общим узлам размещать несколько приложений с разными базовыми адресами для одной схемы на одном узле.</span><span class="sxs-lookup"><span data-stu-id="1f52e-119">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="1f52e-120">Веб-узлы IIS являются контейнерами виртуальных приложений, содержащими виртуальные каталоги.</span><span class="sxs-lookup"><span data-stu-id="1f52e-120">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="1f52e-121">Доступ к приложению на узле можно осуществлять через одну или несколько привязок службы IIS.</span><span class="sxs-lookup"><span data-stu-id="1f52e-121">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="1f52e-122">Привязки IIS предоставляют два блока данных: протокол привязки и данные привязки.</span><span class="sxs-lookup"><span data-stu-id="1f52e-122">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="1f52e-123">Протокол привязки (например, HTTP) определяет схему, посредством которой осуществляется связь, а данные привязки (например, IP-адрес, порт, заголовок узла) содержат сведения, используемые для доступа к узлу.</span><span class="sxs-lookup"><span data-stu-id="1f52e-123">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="1f52e-124">IIS поддерживает задание нескольких привязок IIS для каждого узла, что позволяет использовать несколько базовых адресов для каждой схемы.</span><span class="sxs-lookup"><span data-stu-id="1f52e-124">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="1f52e-125">Так как служба WCF, размещенная на сайте, допускает привязку только к одному базовому адресу для каждой схемы, можно использовать функцию фильтрации префиксов, чтобы выбрать необходимый базовый адрес размещенной службы.</span><span class="sxs-lookup"><span data-stu-id="1f52e-125">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="1f52e-126">Входящие базовые адреса, предоставляемые IIS, фильтруются с использованием дополнительного фильтра списка префиксов.</span><span class="sxs-lookup"><span data-stu-id="1f52e-126">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="1f52e-127">Например, сайт может содержать следующие базовые адреса:</span><span class="sxs-lookup"><span data-stu-id="1f52e-127">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="1f52e-128">Для задания префиксного фильтра на уровне домена приложений можно использовать следующий файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1f52e-128">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="1f52e-129">В этом примере `net.tcp://test1.fabrikam.com:8000` и `http://test2.fabrikam.com:9000` являются единственными базовыми адресами для соответствующих схем, которые могут пропускаться.</span><span class="sxs-lookup"><span data-stu-id="1f52e-129">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="1f52e-130">Если префикс не задан, по умолчанию пропускаются все адреса.</span><span class="sxs-lookup"><span data-stu-id="1f52e-130">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="1f52e-131">При задании префикса разрешается прохождение данных только с соответствующего базового адреса для данной схемы.</span><span class="sxs-lookup"><span data-stu-id="1f52e-131">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f52e-132">Фильтр не поддерживает какие-либо подстановочные знаки.</span><span class="sxs-lookup"><span data-stu-id="1f52e-132">The filter does not support any wildcards.</span></span> <span data-ttu-id="1f52e-133">Кроме того, среди базовых адресов, предоставляемых IIS, могут присутствовать адреса, привязанные к другим схемам, не представленным в списке `baseAddressPrefixFilters`.</span><span class="sxs-lookup"><span data-stu-id="1f52e-133">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="1f52e-134">Эти адреса не фильтруются.</span><span class="sxs-lookup"><span data-stu-id="1f52e-134">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f52e-135">См. также</span><span class="sxs-lookup"><span data-stu-id="1f52e-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="1f52e-136">Размещение</span><span class="sxs-lookup"><span data-stu-id="1f52e-136">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
