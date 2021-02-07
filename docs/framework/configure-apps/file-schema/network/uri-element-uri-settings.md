---
description: 'Дополнительные сведения о <uri> элементе: Element (Параметры URI)'
title: Элемент <uri> (параметры URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: dc30778fdf5babfb87da0e32829ed9a3ae412c2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740123"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="4b77e-103">Элемент \<uri> (параметры URI)</span><span class="sxs-lookup"><span data-stu-id="4b77e-103">\<uri> Element (Uri Settings)</span></span>

<span data-ttu-id="4b77e-104">Содержит параметры, определяющие, как платформа .NET Framework обрабатывает веб-адреса, выраженные с помощью универсальных идентификаторов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="4b77e-104">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="4b77e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4b77e-105">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b77e-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4b77e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4b77e-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4b77e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b77e-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4b77e-108">Attributes</span></span>  

 <span data-ttu-id="4b77e-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4b77e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4b77e-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4b77e-110">Child Elements</span></span>  
  
|<span data-ttu-id="4b77e-111">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="4b77e-111">**Element**</span></span>|<span data-ttu-id="4b77e-112">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4b77e-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4b77e-113">IDN</span><span class="sxs-lookup"><span data-stu-id="4b77e-113">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="4b77e-114">Определяет, применяется ли к доменным именам анализ международных доменных имен (IDN).</span><span class="sxs-lookup"><span data-stu-id="4b77e-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="4b77e-115">Элемент iriParsing</span><span class="sxs-lookup"><span data-stu-id="4b77e-115">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="4b77e-116">Указывает, применяется ли синтаксический анализ международного идентификатора ресурса (IRI) <xref:System.Uri> , и должны применяться правила синтаксического анализа IRI.</span><span class="sxs-lookup"><span data-stu-id="4b77e-116">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="4b77e-117">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="4b77e-117">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="4b77e-118">Определяет, как <xref:System.Uri> анализируется для определенных схем.</span><span class="sxs-lookup"><span data-stu-id="4b77e-118">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b77e-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4b77e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4b77e-120">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="4b77e-120">**Element**</span></span>|<span data-ttu-id="4b77e-121">**Описание**</span><span class="sxs-lookup"><span data-stu-id="4b77e-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4b77e-122">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="4b77e-122">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="4b77e-123">Содержит параметры для всех пространств имен.</span><span class="sxs-lookup"><span data-stu-id="4b77e-123">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b77e-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="4b77e-124">Remarks</span></span>  

 <span data-ttu-id="4b77e-125">`uri`Элемент содержит параметры для элементов <xref:System.Uri> класса, используемых классами в <xref:System.Net> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="4b77e-125">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="4b77e-126">Параметры настраивают поддержку для IRI и IDN.</span><span class="sxs-lookup"><span data-stu-id="4b77e-126">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b77e-127">Пример</span><span class="sxs-lookup"><span data-stu-id="4b77e-127">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4b77e-128">Описание</span><span class="sxs-lookup"><span data-stu-id="4b77e-128">Description</span></span>  

 <span data-ttu-id="4b77e-129">В следующем примере показана конфигурация, используемая <xref:System.Uri> классом для поддержки синтаксического анализа IRI и имен IDN.</span><span class="sxs-lookup"><span data-stu-id="4b77e-129">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="4b77e-130">В этом примере также очищаются все параметры схемы, а затем добавляется поддержка не экранирования процентов для пути, закодированного для схемы HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b77e-130">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4b77e-131">Код</span><span class="sxs-lookup"><span data-stu-id="4b77e-131">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b77e-132">См. также</span><span class="sxs-lookup"><span data-stu-id="4b77e-132">See also</span></span>

- [<span data-ttu-id="4b77e-133">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="4b77e-133">Network Settings Schema</span></span>](index.md)
