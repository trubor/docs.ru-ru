---
description: 'Дополнительные сведения о: <clear> Element для schemeSettings (Параметры URI)'
title: Элемент <clear> для schemeSettings (параметры URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 719296285c9a7da26eb6eaf16c630a63a10698b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740461"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="c518e-103">Элемент \<clear> для schemeSettings (параметры URI)</span><span class="sxs-lookup"><span data-stu-id="c518e-103">\<clear> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="c518e-104">Удаляет все существующие параметры схемы.</span><span class="sxs-lookup"><span data-stu-id="c518e-104">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="c518e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c518e-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c518e-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c518e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c518e-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c518e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c518e-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c518e-108">Attributes</span></span>  

 <span data-ttu-id="c518e-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="c518e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c518e-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c518e-110">Child Elements</span></span>  

 <span data-ttu-id="c518e-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="c518e-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c518e-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c518e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c518e-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="c518e-113">Element</span></span>|<span data-ttu-id="c518e-114">Описание</span><span class="sxs-lookup"><span data-stu-id="c518e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c518e-115">\<schemeSettings> Элемент (Параметры URI)</span><span class="sxs-lookup"><span data-stu-id="c518e-115">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="c518e-116">Определяет, как <xref:System.Uri> анализируется для определенных схем.</span><span class="sxs-lookup"><span data-stu-id="c518e-116">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c518e-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="c518e-117">Remarks</span></span>  

 <span data-ttu-id="c518e-118">По умолчанию класс отменяет <xref:System.Uri?displayProperty=nameWithType> escape-символы в процентах, закодированные разделителями, перед выполнением сжатия пути.</span><span class="sxs-lookup"><span data-stu-id="c518e-118">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="c518e-119">Это было реализовано в качестве механизма безопасности для атак, подобных следующим:</span><span class="sxs-lookup"><span data-stu-id="c518e-119">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c518e-120">Если этот URI передается в модули, которые неправильно обрабатывают закодированные символы процента, это может привести к выполнению следующей команды на сервере:</span><span class="sxs-lookup"><span data-stu-id="c518e-120">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="c518e-121">По этой причине <xref:System.Uri?displayProperty=nameWithType> класс сначала отменяет escape-разделители путей, а затем применяет сжатие пути.</span><span class="sxs-lookup"><span data-stu-id="c518e-121">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="c518e-122">Результат передачи вредоносного URL-адреса выше в <xref:System.Uri?displayProperty=nameWithType> конструктор класса приводит к следующему URI:</span><span class="sxs-lookup"><span data-stu-id="c518e-122">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c518e-123">Это поведение по умолчанию можно изменить, чтобы не отменять escape-символы в процентах с помощью параметра конфигурации schemeSettings для определенной схемы.</span><span class="sxs-lookup"><span data-stu-id="c518e-123">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c518e-124">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="c518e-124">Configuration Files</span></span>  

 <span data-ttu-id="c518e-125">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c518e-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c518e-126">Пример</span><span class="sxs-lookup"><span data-stu-id="c518e-126">Example</span></span>  

 <span data-ttu-id="c518e-127">В следующем примере показана конфигурация, используемая <xref:System.Uri> классом, который очищает все параметры схемы и добавляет поддержку для разделителей пути, не экранированных в процентах, для схемы HTTP.</span><span class="sxs-lookup"><span data-stu-id="c518e-127">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c518e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="c518e-128">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="c518e-129">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="c518e-129">Network Settings Schema</span></span>](index.md)
