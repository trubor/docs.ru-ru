---
description: 'Дополнительные сведения о <schemeSettings> элементе: Element (Параметры URI)'
title: Элемент <schemeSettings> (параметры URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 218676c10a8acaa79c2eb2146214e77beee9a972
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698444"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="bbf85-103">Элемент \<schemeSettings> (параметры URI)</span><span class="sxs-lookup"><span data-stu-id="bbf85-103">\<schemeSettings> Element (Uri Settings)</span></span>

<span data-ttu-id="bbf85-104">Определяет, как <xref:System.Uri> анализируется для определенных схем.</span><span class="sxs-lookup"><span data-stu-id="bbf85-104">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="bbf85-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bbf85-105">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbf85-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="bbf85-106">Attributes and Elements</span></span>  

 <span data-ttu-id="bbf85-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bbf85-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbf85-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="bbf85-108">Attributes</span></span>  

 <span data-ttu-id="bbf85-109">None</span><span class="sxs-lookup"><span data-stu-id="bbf85-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bbf85-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="bbf85-110">Child Elements</span></span>  
  
|<span data-ttu-id="bbf85-111">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bbf85-111">**Element**</span></span>|<span data-ttu-id="bbf85-112">**Описание**</span><span class="sxs-lookup"><span data-stu-id="bbf85-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bbf85-113">add</span><span class="sxs-lookup"><span data-stu-id="bbf85-113">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="bbf85-114">Добавляет параметр схемы для имени схемы.</span><span class="sxs-lookup"><span data-stu-id="bbf85-114">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="bbf85-115">пусто</span><span class="sxs-lookup"><span data-stu-id="bbf85-115">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="bbf85-116">Удаляет все существующие параметры схемы.</span><span class="sxs-lookup"><span data-stu-id="bbf85-116">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="bbf85-117">remove</span><span class="sxs-lookup"><span data-stu-id="bbf85-117">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="bbf85-118">Удаляет параметр схемы для имени схемы.</span><span class="sxs-lookup"><span data-stu-id="bbf85-118">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbf85-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="bbf85-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bbf85-120">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="bbf85-120">**Element**</span></span>|<span data-ttu-id="bbf85-121">**Описание**</span><span class="sxs-lookup"><span data-stu-id="bbf85-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bbf85-122">uri</span><span class="sxs-lookup"><span data-stu-id="bbf85-122">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="bbf85-123">Содержит параметры, определяющие, как платформа .NET Framework обрабатывает веб-адреса, выраженные с помощью универсальных идентификаторов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="bbf85-123">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbf85-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="bbf85-124">Remarks</span></span>  

 <span data-ttu-id="bbf85-125">По умолчанию класс отменяет <xref:System.Uri?displayProperty=nameWithType> escape-символы в процентах, закодированные разделителями, перед выполнением сжатия пути.</span><span class="sxs-lookup"><span data-stu-id="bbf85-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="bbf85-126">Это было реализовано в качестве механизма безопасности для атак, подобных следующим:</span><span class="sxs-lookup"><span data-stu-id="bbf85-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="bbf85-127">Если этот URI передается в модули, которые неправильно обрабатывают закодированные символы процента, это может привести к выполнению следующей команды на сервере:</span><span class="sxs-lookup"><span data-stu-id="bbf85-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="bbf85-128">По этой причине <xref:System.Uri?displayProperty=nameWithType> класс сначала отменяет escape-разделители путей, а затем применяет сжатие пути.</span><span class="sxs-lookup"><span data-stu-id="bbf85-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="bbf85-129">Результат передачи вредоносного URL-адреса выше в <xref:System.Uri?displayProperty=nameWithType> конструктор класса приводит к следующему URI:</span><span class="sxs-lookup"><span data-stu-id="bbf85-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="bbf85-130">Это поведение по умолчанию можно изменить, чтобы не отменять escape-символы в процентах с помощью параметра конфигурации schemeSettings для определенной схемы.</span><span class="sxs-lookup"><span data-stu-id="bbf85-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bbf85-131">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="bbf85-131">Configuration Files</span></span>  

 <span data-ttu-id="bbf85-132">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="bbf85-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf85-133">Пример</span><span class="sxs-lookup"><span data-stu-id="bbf85-133">Example</span></span>  

 <span data-ttu-id="bbf85-134">В следующем примере показана конфигурация, используемая <xref:System.Uri> классом для поддержки неэкранированных разделителей пути в кодировке% для схемы HTTP.</span><span class="sxs-lookup"><span data-stu-id="bbf85-134">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="bbf85-135">Сведения об элементе</span><span class="sxs-lookup"><span data-stu-id="bbf85-135">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="bbf85-136">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="bbf85-136">Namespace</span></span>|<span data-ttu-id="bbf85-137">система</span><span class="sxs-lookup"><span data-stu-id="bbf85-137">System</span></span>|  
|<span data-ttu-id="bbf85-138">Имя схемы</span><span class="sxs-lookup"><span data-stu-id="bbf85-138">Schema Name</span></span>||  
|<span data-ttu-id="bbf85-139">Файл проверки</span><span class="sxs-lookup"><span data-stu-id="bbf85-139">Validation File</span></span>||  
|<span data-ttu-id="bbf85-140">Может быть пустым</span><span class="sxs-lookup"><span data-stu-id="bbf85-140">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="bbf85-141">См. также</span><span class="sxs-lookup"><span data-stu-id="bbf85-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="bbf85-142">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="bbf85-142">Network Settings Schema</span></span>](index.md)
