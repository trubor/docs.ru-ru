---
description: 'Дополнительные сведения о: <add> Element для schemeSettings (Параметры URI)'
title: Элемент <add> для schemeSettings (параметры URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: c372577af1c7fbfe669455b50c8b55c82da4fc52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698625"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="4f74e-103">Элемент \<add> для schemeSettings (параметры URI)</span><span class="sxs-lookup"><span data-stu-id="4f74e-103">\<add> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="4f74e-104">Добавляет параметр схемы для имени схемы.</span><span class="sxs-lookup"><span data-stu-id="4f74e-104">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="4f74e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4f74e-105">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f74e-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4f74e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4f74e-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4f74e-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f74e-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4f74e-108">Attributes</span></span>  
  
|<span data-ttu-id="4f74e-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4f74e-109">Attribute</span></span>|<span data-ttu-id="4f74e-110">Описание</span><span class="sxs-lookup"><span data-stu-id="4f74e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f74e-111">name</span><span class="sxs-lookup"><span data-stu-id="4f74e-111">name</span></span>|<span data-ttu-id="4f74e-112">Имя схемы, к которой применяется этот параметр.</span><span class="sxs-lookup"><span data-stu-id="4f74e-112">The scheme name for which this setting applies.</span></span> <span data-ttu-id="4f74e-113">Поддерживаются только значения Name = "http" и Name = "HTTPS".</span><span class="sxs-lookup"><span data-stu-id="4f74e-113">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="4f74e-114">{Имя атрибута} Версию</span><span class="sxs-lookup"><span data-stu-id="4f74e-114">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="4f74e-115">Значение</span><span class="sxs-lookup"><span data-stu-id="4f74e-115">Value</span></span>|<span data-ttu-id="4f74e-116">Описание</span><span class="sxs-lookup"><span data-stu-id="4f74e-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f74e-117">женерикурипарсероптионс</span><span class="sxs-lookup"><span data-stu-id="4f74e-117">genericUriParserOptions</span></span>|<span data-ttu-id="4f74e-118">Параметры средства синтаксического анализа для этой схемы.</span><span class="sxs-lookup"><span data-stu-id="4f74e-118">The parser options for this scheme.</span></span> <span data-ttu-id="4f74e-119">Единственное поддерживаемое значение — Женерикурипарсероптионс = "Донтунескапепасдотсандслашес".</span><span class="sxs-lookup"><span data-stu-id="4f74e-119">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f74e-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4f74e-120">Child Elements</span></span>  

 <span data-ttu-id="4f74e-121">None</span><span class="sxs-lookup"><span data-stu-id="4f74e-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f74e-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4f74e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4f74e-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="4f74e-123">Element</span></span>|<span data-ttu-id="4f74e-124">Описание</span><span class="sxs-lookup"><span data-stu-id="4f74e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f74e-125">\<schemeSettings> Элемент (Параметры URI)</span><span class="sxs-lookup"><span data-stu-id="4f74e-125">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="4f74e-126">Определяет, как <xref:System.Uri> анализируется для определенных схем.</span><span class="sxs-lookup"><span data-stu-id="4f74e-126">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f74e-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="4f74e-127">Remarks</span></span>  

 <span data-ttu-id="4f74e-128">По умолчанию класс отменяет <xref:System.Uri?displayProperty=nameWithType> escape-символы в процентах, закодированные разделителями, перед выполнением сжатия пути.</span><span class="sxs-lookup"><span data-stu-id="4f74e-128">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="4f74e-129">Это было реализовано в качестве механизма безопасности для атак, подобных следующим:</span><span class="sxs-lookup"><span data-stu-id="4f74e-129">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4f74e-130">Если этот URI передается в модули, которые неправильно обрабатывают закодированные символы процента, это может привести к выполнению следующей команды на сервере:</span><span class="sxs-lookup"><span data-stu-id="4f74e-130">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="4f74e-131">По этой причине <xref:System.Uri?displayProperty=nameWithType> класс сначала отменяет escape-разделители путей, а затем применяет сжатие пути.</span><span class="sxs-lookup"><span data-stu-id="4f74e-131">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="4f74e-132">Результат передачи вредоносного URL-адреса выше в <xref:System.Uri?displayProperty=nameWithType> конструктор класса приводит к следующему URI:</span><span class="sxs-lookup"><span data-stu-id="4f74e-132">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4f74e-133">Это поведение по умолчанию можно изменить, чтобы не отменять escape-символы в процентах с помощью параметра конфигурации schemeSettings для определенной схемы.</span><span class="sxs-lookup"><span data-stu-id="4f74e-133">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4f74e-134">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="4f74e-134">Configuration Files</span></span>  

 <span data-ttu-id="4f74e-135">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4f74e-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f74e-136">Пример</span><span class="sxs-lookup"><span data-stu-id="4f74e-136">Example</span></span>  

 <span data-ttu-id="4f74e-137">В следующем примере показана конфигурация, используемая <xref:System.Uri> классом для поддержки неэкранированных разделителей пути в кодировке% для схемы HTTP.</span><span class="sxs-lookup"><span data-stu-id="4f74e-137">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f74e-138">См. также</span><span class="sxs-lookup"><span data-stu-id="4f74e-138">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="4f74e-139">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="4f74e-139">Network Settings Schema</span></span>](index.md)
