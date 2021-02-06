---
description: 'Дополнительные сведения о <httpListener> элементе: Element (параметры сети)'
title: Элемент <httpListener> (параметры сети)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 18c139ad7767370ecd3a4116e352b7614914d199
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652865"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="a722c-103">Элемент \<httpListener> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="a722c-103">\<httpListener> Element (Network Settings)</span></span>

<span data-ttu-id="a722c-104">Настраивает параметры, используемые <xref:System.Net.HttpListener> классом.</span><span class="sxs-lookup"><span data-stu-id="a722c-104">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a><span data-ttu-id="a722c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a722c-105">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="a722c-106">Тип</span><span class="sxs-lookup"><span data-stu-id="a722c-106">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a722c-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a722c-107">Attributes and Elements</span></span>  

 <span data-ttu-id="a722c-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a722c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a722c-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a722c-109">Attributes</span></span>  
  
|<span data-ttu-id="a722c-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a722c-110">Attribute</span></span>|<span data-ttu-id="a722c-111">Описание</span><span class="sxs-lookup"><span data-stu-id="a722c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a722c-112">унескаперекуестурл</span><span class="sxs-lookup"><span data-stu-id="a722c-112">unescapeRequestUrl</span></span>|<span data-ttu-id="a722c-113">Логическое значение, указывающее, использует ли <xref:System.Net.HttpListener> экземпляр необработанный неэкранированный универсальный код ресурса (URI) вместо преобразованного URI.</span><span class="sxs-lookup"><span data-stu-id="a722c-113">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a722c-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a722c-114">Child Elements</span></span>  

 <span data-ttu-id="a722c-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a722c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a722c-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a722c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a722c-117">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="a722c-117">**Element**</span></span>|<span data-ttu-id="a722c-118">**Описание**</span><span class="sxs-lookup"><span data-stu-id="a722c-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a722c-119">параметры</span><span class="sxs-lookup"><span data-stu-id="a722c-119">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a722c-120">Настраивает основные параметры сети для пространства имен <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="a722c-120">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a722c-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="a722c-121">Remarks</span></span>  

 <span data-ttu-id="a722c-122">Атрибут **унескаперекуестурл** указывает <xref:System.Net.HttpListener> , использует ли необработанный неэкранированный универсальный код ресурса (URI) вместо преобразованного универсального кода ресурса (URI), в котором преобразовываются все значения в кодировке% и выполняются другие действия нормализации.</span><span class="sxs-lookup"><span data-stu-id="a722c-122">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="a722c-123">Когда <xref:System.Net.HttpListener> экземпляр получает запрос через `http.sys` службу, он создает экземпляр строки URI, предоставленной `http.sys` , и предоставляет его в качестве <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> Свойства.</span><span class="sxs-lookup"><span data-stu-id="a722c-123">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a722c-124">`http.sys`Служба предоставляет две строки URI запроса:</span><span class="sxs-lookup"><span data-stu-id="a722c-124">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="a722c-125">Необработанный URI</span><span class="sxs-lookup"><span data-stu-id="a722c-125">Raw URI</span></span>  
  
- <span data-ttu-id="a722c-126">Преобразованный URI</span><span class="sxs-lookup"><span data-stu-id="a722c-126">Converted URI</span></span>  
  
 <span data-ttu-id="a722c-127">Необработанный универсальный код ресурса (URI) указан <xref:System.Uri?displayProperty=nameWithType> в строке запроса HTTP-запроса:</span><span class="sxs-lookup"><span data-stu-id="a722c-127">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="a722c-128">Необработанный URI, предоставленный `http.sys` для запроса, упомянутого выше, имеет значение "/Пас/".</span><span class="sxs-lookup"><span data-stu-id="a722c-128">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="a722c-129">Представляет строку, следующую за HTTP-командой в том виде, в котором она была отправлена по сети.</span><span class="sxs-lookup"><span data-stu-id="a722c-129">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="a722c-130">`http.sys`Служба создает преобразованный универсальный код ресурса (URI) из информации, предоставленной в запросе, используя URI, указанный в строке запроса HTTP, и заголовок узла для определения сервера-источника, на который должен быть направлен запрос.</span><span class="sxs-lookup"><span data-stu-id="a722c-130">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="a722c-131">Это делается путем сравнения информации из запроса с набором зарегистрированных префиксов URI.</span><span class="sxs-lookup"><span data-stu-id="a722c-131">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="a722c-132">В документации по пакету SDK для HTTP-сервера этот преобразованный универсальный код ресурса (URI) называется структурой HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="a722c-132">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="a722c-133">Чтобы иметь возможность сравнить запрос с зарегистрированными префиксами URI, необходимо выполнить некоторую нормализацию запроса.</span><span class="sxs-lookup"><span data-stu-id="a722c-133">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="a722c-134">Для примера выше преобразованный URI будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a722c-134">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="a722c-135">`http.sys`Служба объединяет <xref:System.Uri.Host%2A?displayProperty=nameWithType> значение свойства и строку в строке запроса для создания преобразованного универсального кода ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="a722c-135">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="a722c-136">Кроме того, `http.sys` <xref:System.Uri?displayProperty=nameWithType> класс также выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="a722c-136">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="a722c-137">Отменяет экранирование всех закодированных в процентах значений.</span><span class="sxs-lookup"><span data-stu-id="a722c-137">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="a722c-138">Преобразует символы, не входящие в набор ASCII, в кодировку UTF-16 в символьное представление.</span><span class="sxs-lookup"><span data-stu-id="a722c-138">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="a722c-139">Обратите внимание, что символы UTF-8 и ANSI/DBCS поддерживаются, а также символы Юникода (Кодировка Юникода с использованием формата% Укскскскс).</span><span class="sxs-lookup"><span data-stu-id="a722c-139">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="a722c-140">Выполняет другие шаги нормализации, например сжатие пути.</span><span class="sxs-lookup"><span data-stu-id="a722c-140">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="a722c-141">Поскольку запрос не содержит никаких сведений о кодировке, используемой для значений, закодированных в процентах, возможно, вам не удастся определить правильную кодировку путем анализа значений, закодированных в процентах.</span><span class="sxs-lookup"><span data-stu-id="a722c-141">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="a722c-142">Поэтому `http.sys` предоставляет два раздела реестра для изменения процесса:</span><span class="sxs-lookup"><span data-stu-id="a722c-142">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="a722c-143">Ключ реестра</span><span class="sxs-lookup"><span data-stu-id="a722c-143">Registry Key</span></span>|<span data-ttu-id="a722c-144">Значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="a722c-144">Default Value</span></span>|<span data-ttu-id="a722c-145">Описание</span><span class="sxs-lookup"><span data-stu-id="a722c-145">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="a722c-146">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="a722c-146">EnableNonUTF8</span></span>|<span data-ttu-id="a722c-147">1</span><span class="sxs-lookup"><span data-stu-id="a722c-147">1</span></span>|<span data-ttu-id="a722c-148">Если значение равно нулю, `http.sys` принимает только URL-адреса в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a722c-148">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="a722c-149">Если значение не равно нулю, `http.sys` в запросах также принимается URL-адреса в кодировке ANSI или в кодировке DBCS.</span><span class="sxs-lookup"><span data-stu-id="a722c-149">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="a722c-150">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="a722c-150">FavorUTF8</span></span>|<span data-ttu-id="a722c-151">1</span><span class="sxs-lookup"><span data-stu-id="a722c-151">1</span></span>|<span data-ttu-id="a722c-152">Если ненулевое значение, `http.sys` всегда пытается декодировать URL-адрес как UTF-8. Если преобразование завершается неудачно и EnableNonUTF8 не равно нулю, Http.sys попытается декодировать его как ANSI или DBCS.</span><span class="sxs-lookup"><span data-stu-id="a722c-152">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="a722c-153">Если ноль (и EnableNonUTF8 не равен нулю), `http.sys` попытается декодировать его как ANSI или DBCS; если это не удается, то пытается выполнить преобразование UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a722c-153">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="a722c-154">Когда <xref:System.Net.HttpListener> получает запрос, он использует преобразованный универсальный код ресурса (URI) из в `http.sys` качестве входных данных <xref:System.Net.HttpListenerRequest.Url%2A> Свойства.</span><span class="sxs-lookup"><span data-stu-id="a722c-154">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="a722c-155">Есть необходимость в поддержке символов помимо символов и чисел в URI.</span><span class="sxs-lookup"><span data-stu-id="a722c-155">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="a722c-156">Примером является следующий универсальный код ресурса (URI), который используется для получения сведений о клиенте для номера клиента «1/3812»:</span><span class="sxs-lookup"><span data-stu-id="a722c-156">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="a722c-157">Обратите внимание на косую черту в формате URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="a722c-157">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="a722c-158">Это необходимо, поскольку в данном случае символ косой черты представляет данные, а не разделитель пути.</span><span class="sxs-lookup"><span data-stu-id="a722c-158">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="a722c-159">Передача строки в конструктор URI приводит к следующему URI:</span><span class="sxs-lookup"><span data-stu-id="a722c-159">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="a722c-160">Разделение пути на сегменты приведет к следующим элементам:</span><span class="sxs-lookup"><span data-stu-id="a722c-160">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="a722c-161">Это не цель отправителя запроса.</span><span class="sxs-lookup"><span data-stu-id="a722c-161">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="a722c-162">Если атрибут **унескаперекуестурл** имеет значение **false**, то при <xref:System.Net.HttpListener> получении запроса он использует необработанный универсальный код ресурса (URI) вместо преобразованного универсального кода ресурса (URI) в `http.sys` качестве входных данных для <xref:System.Net.HttpListenerRequest.Url%2A> Свойства.</span><span class="sxs-lookup"><span data-stu-id="a722c-162">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="a722c-163">Значение по умолчанию для атрибута **унескаперекуестурл** — **true**.</span><span class="sxs-lookup"><span data-stu-id="a722c-163">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="a722c-164"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>Свойство можно использовать для получения текущего значения атрибута **унескаперекуестурл** из применимых файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a722c-164">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a722c-165">Пример</span><span class="sxs-lookup"><span data-stu-id="a722c-165">Example</span></span>  

 <span data-ttu-id="a722c-166">В следующем примере показано, как настроить <xref:System.Net.HttpListener> класс при получении запроса на использование необработанного универсального кода ресурса (URI) вместо преобразованного универсального кода ресурса (URI) в `http.sys` качестве входных данных для <xref:System.Net.HttpListenerRequest.Url%2A> Свойства.</span><span class="sxs-lookup"><span data-stu-id="a722c-166">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="a722c-167">Сведения об элементе</span><span class="sxs-lookup"><span data-stu-id="a722c-167">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="a722c-168">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="a722c-168">Namespace</span></span>|<span data-ttu-id="a722c-169">System.Net</span><span class="sxs-lookup"><span data-stu-id="a722c-169">System.Net</span></span>|  
|<span data-ttu-id="a722c-170">Имя схемы</span><span class="sxs-lookup"><span data-stu-id="a722c-170">Schema Name</span></span>||  
|<span data-ttu-id="a722c-171">Файл проверки</span><span class="sxs-lookup"><span data-stu-id="a722c-171">Validation File</span></span>||  
|<span data-ttu-id="a722c-172">Может быть пустым</span><span class="sxs-lookup"><span data-stu-id="a722c-172">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="a722c-173">См. также</span><span class="sxs-lookup"><span data-stu-id="a722c-173">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="a722c-174">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="a722c-174">Network Settings Schema</span></span>](index.md)
