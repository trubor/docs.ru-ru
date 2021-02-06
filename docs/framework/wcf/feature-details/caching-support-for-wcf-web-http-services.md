---
description: 'Подробнее: поддержка кэширования для служб WCF Web HTTP'
title: Поддержка кэширования для веб-служб HTTP WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: a1f7351566c06010ed70093a1cab3697ae0e9356
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643492"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="978aa-103">Поддержка кэширования для веб-служб HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="978aa-103">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="978aa-104">позволяет использовать механизм декларативного кэширования, уже доступный в ASP.NET в веб-службах HTTP WCF.</span><span class="sxs-lookup"><span data-stu-id="978aa-104">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="978aa-105">Это позволяет кэшировать ответы от операций службы WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="978aa-105">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="978aa-106">Когда пользователь отправляет инструкцию HTTP GET службе, настроенной для кэширования, ASP.NET отправляет обратно кэшированный ответ, метод службы при этом не вызывается.</span><span class="sxs-lookup"><span data-stu-id="978aa-106">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="978aa-107">По истечении срока действия кэш в следующий раз, когда пользователь отправит инструкцию HTTP GET, будет вызван метод службы и ответ будет снова кэширован.</span><span class="sxs-lookup"><span data-stu-id="978aa-107">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="978aa-108">Дополнительные сведения о кэшировании ASP.NET см. в разделе [Общие сведения о кэшировании ASP.NET](/previous-versions/aspnet/ms178597(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="978aa-108">For more information about ASP.NET caching, see [ASP.NET Caching Overview](/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="978aa-109">Кэширование базовой службы Web HTTP</span><span class="sxs-lookup"><span data-stu-id="978aa-109">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="978aa-110">Чтобы включить кэширование веб-служб HTTP, необходимо сначала включить совместимость с ASP.NET, применив <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> к параметру службы значение <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> или <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> .</span><span class="sxs-lookup"><span data-stu-id="978aa-110">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="978aa-111">В платформа .NET Framework 4 появился новый атрибут <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> с именем, который позволяет указать имя профиля кэша.</span><span class="sxs-lookup"><span data-stu-id="978aa-111">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="978aa-112">Этот атрибут применяется к операции службы.</span><span class="sxs-lookup"><span data-stu-id="978aa-112">This attribute is applied to a service operation.</span></span> <span data-ttu-id="978aa-113">В следующем примере атрибут <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> применяется к службе для включения совместимости с ASP.NET, а операция `GetCustomer` настраивается для кэширования.</span><span class="sxs-lookup"><span data-stu-id="978aa-113">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="978aa-114">Атрибут <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> задает профиль кэширования, содержащий используемые параметры кэширования.</span><span class="sxs-lookup"><span data-stu-id="978aa-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract]
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
<span data-ttu-id="978aa-115">Также включите режим совместимости ASP.NET в файле Web.config, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="978aa-115">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="978aa-116">Если режим совместимости с ASP.NET не включен и используется <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, то возникнет исключение.</span><span class="sxs-lookup"><span data-stu-id="978aa-116">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="978aa-117">Имя профиля кэша, заданное атрибутом <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, идентифицирует профиль кэша, добавленный в файл конфигурации Web.config.</span><span class="sxs-lookup"><span data-stu-id="978aa-117">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="978aa-118">Профиль кэша определяется с помощью `outputCacheSetting` элемента <>, как показано в следующем примере конфигурации.</span><span class="sxs-lookup"><span data-stu-id="978aa-118">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="978aa-119">Этот же элемент конфигурации доступен приложениям ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="978aa-119">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="978aa-120">Дополнительные сведения о профилях кэша ASP.NET см. в разделе <xref:System.Web.Configuration.OutputCacheProfile> .</span><span class="sxs-lookup"><span data-stu-id="978aa-120">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="978aa-121">Самыми важными атрибутами для служб Web HTTP в профиле кэша являются `cacheDuration` и `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="978aa-121">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="978aa-122">Оба атрибута обязательные.</span><span class="sxs-lookup"><span data-stu-id="978aa-122">Both of these attributes are required.</span></span> <span data-ttu-id="978aa-123">`cacheDuration` задает время (в секундах), в течение которого ответ должен храниться в кэше.</span><span class="sxs-lookup"><span data-stu-id="978aa-123">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="978aa-124">`varyByParam` позволяет задать параметр строки запроса, используемый для кэширования ответов.</span><span class="sxs-lookup"><span data-stu-id="978aa-124">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="978aa-125">Все запросы, составленные с разными значениями параметра строки запроса, кэшируются отдельно.</span><span class="sxs-lookup"><span data-stu-id="978aa-125">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="978aa-126">Например, после выполнения начального запроса `http://MyServer/MyHttpService/MyOperation?param=10` все последующие запросы, выполненные с использованием того же URI, будут возвращены в кэшированный ответ (при условии, что продолжительность кэширования не истекла).</span><span class="sxs-lookup"><span data-stu-id="978aa-126">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="978aa-127">Ответы для аналогичного запроса, имеющего другое значение для параметра строки запроса, кэшируются отдельно.</span><span class="sxs-lookup"><span data-stu-id="978aa-127">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="978aa-128">Если такое раздельное кэширование нежелательно, установите параметр `varyByParam` в значение «none».</span><span class="sxs-lookup"><span data-stu-id="978aa-128">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="978aa-129">Зависимость кэша SQL</span><span class="sxs-lookup"><span data-stu-id="978aa-129">SQL Cache Dependency</span></span>  

  <span data-ttu-id="978aa-130">Ответы службы Web HTTP также могут быть кэшироваться с зависимостью от кэша SQL.</span><span class="sxs-lookup"><span data-stu-id="978aa-130">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="978aa-131">Если служба WCF Web HTTP зависит от данных, которые хранятся в базе данных SQL, можно кэшировать ответ службы и аннулировать кэшированный ответ при изменении данных в таблице базы данных SQL.</span><span class="sxs-lookup"><span data-stu-id="978aa-131">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="978aa-132">Это полностью настраивается в файле Web.config.</span><span class="sxs-lookup"><span data-stu-id="978aa-132">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="978aa-133">Сначала определите строку подключения в `connectionStrings` элементе <>.</span><span class="sxs-lookup"><span data-stu-id="978aa-133">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="978aa-134">Затем необходимо включить зависимость кэша SQL в `caching` элементе <> в `system.web` элементе <>, как показано в следующем примере конфигурации.</span><span class="sxs-lookup"><span data-stu-id="978aa-134">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="978aa-135">В данном случае зависимость кэша SQL включена и задан интервал опроса в 1000 миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="978aa-135">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="978aa-136">Каждый раз при истечении времени опроса таблица базы данных проверяется на предмет обновлений.</span><span class="sxs-lookup"><span data-stu-id="978aa-136">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="978aa-137">Если найдены изменения, то содержимое кэша удаляется, при этом при следующем вызове операции службы новый ответ будет помещен в кэш.</span><span class="sxs-lookup"><span data-stu-id="978aa-137">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="978aa-138">В элементе <`sqlCacheDependency`> добавьте базы данных и сослаться на строки подключения в `databases` элементе <>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="978aa-138">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="978aa-139">Далее необходимо настроить параметры кэша вывода в `caching` элементе <>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="978aa-139">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="978aa-140">Здесь время кэширования устанавливается равным 60 секундам, устанавливается `varyByParam` в значение None и `sqlDependency` задается разделенный точками с запятой список пар имен баз данных и таблиц, разделенных двоеточиями.</span><span class="sxs-lookup"><span data-stu-id="978aa-140">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="978aa-141">При изменении данных в `MyTable` ответ для операции службы удаляется из кэша. При вызове операции формируется новый ответ (путем вызова операции службы), который помещается в кэш и возвращается клиенту.</span><span class="sxs-lookup"><span data-stu-id="978aa-141">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="978aa-142">Чтобы ASP.NET получить доступ к базе данных SQL, необходимо использовать [средство регистрации ASP.NET SQL Server](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="978aa-142">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="978aa-143">Помимо этого, необходимо разрешить соответствующей учетной записи пользователя доступ к базе данных и таблице.</span><span class="sxs-lookup"><span data-stu-id="978aa-143">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="978aa-144">Дополнительные сведения см. в разделе [доступ к SQL Server из веб-приложения](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="978aa-144">For more information, see [Accessing SQL Server from a Web Application](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="978aa-145">Условное кэширование на основе HTTP GET</span><span class="sxs-lookup"><span data-stu-id="978aa-145">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="978aa-146">В сценариях Web HTTP условный HTTP-запрос GET часто используется службами для реализации интеллектуального кэширования HTTP, как описано в [спецификации HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span><span class="sxs-lookup"><span data-stu-id="978aa-146">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="978aa-147">Для этого служба должна задать значение заголовка ETag в HTTP-ответе.</span><span class="sxs-lookup"><span data-stu-id="978aa-147">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="978aa-148">Также необходимо посмотреть заголовок If-None-Match в запросе HTTP, чтобы проверить, совпадает ли какой-либо элемент ETag с текущим элементом ETag.</span><span class="sxs-lookup"><span data-stu-id="978aa-148">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="978aa-149">Для запросов GET и HEAD метод <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> получает значение ETag и сравнивает его с заголовком If-None-Match запроса.</span><span class="sxs-lookup"><span data-stu-id="978aa-149">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="978aa-150">Если заголовок присутствует и имеется совпадение, <xref:System.ServiceModel.Web.WebFaultException> вызывается исключение с кодом состояния HTTP 304 (не изменено) и заголовок ETag добавляется в ответ с соответствующим ETag.</span><span class="sxs-lookup"><span data-stu-id="978aa-150">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="978aa-151">Одна перегрузка метода <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> получает последнюю измененную дату и проверяет ее относительно заголовка If-Modified-Since запроса.</span><span class="sxs-lookup"><span data-stu-id="978aa-151">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="978aa-152">Если заголовок присутствует и источник не был изменен, то возникает исключение <xref:System.ServiceModel.Web.WebFaultException> с кодом состояния HTTP 304 (нет изменений).</span><span class="sxs-lookup"><span data-stu-id="978aa-152">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="978aa-153">Для запросов PUT, POST и DELETE метод <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> получает текущее значение ETag источника.</span><span class="sxs-lookup"><span data-stu-id="978aa-153">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="978aa-154">Если текущее значение ETag равно null, метод проверяет, что заголовок If-None-Match имеет значение "\*".</span><span class="sxs-lookup"><span data-stu-id="978aa-154">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="978aa-155">Если текущее значение ETag не является значением по умолчанию, то метод проверяет текущее значение ETag относительно заголовка If-Match запроса.</span><span class="sxs-lookup"><span data-stu-id="978aa-155">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="978aa-156">В обоих случаях метод выдает исключение <xref:System.ServiceModel.Web.WebFaultException> с кодом состояния HTTP 412 (предварительное условие не выполнено), если ожидаемый заголовок не присутствует в запросе либо его значение не проходит проверку условия, и задает заголовку ETag текущее значение ETag.</span><span class="sxs-lookup"><span data-stu-id="978aa-156">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="978aa-157">Методы `CheckConditional` и <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> гарантируют, что значение ETag, заданное для заголовка ответа, является допустимым значением ETag в соответствии со спецификацией протокола HTTP.</span><span class="sxs-lookup"><span data-stu-id="978aa-157">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="978aa-158">Это предполагает заключение значения ETag в двойные кавычки (если они отсутствуют) и правильное экранирование символов двойных кавычек внутри строки.</span><span class="sxs-lookup"><span data-stu-id="978aa-158">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="978aa-159">Нестрогое сравнение ETag не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="978aa-159">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="978aa-160">В следующем примере показано использование этих методов.</span><span class="sxs-lookup"><span data-stu-id="978aa-160">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;

        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="978aa-161">Соображения безопасности</span><span class="sxs-lookup"><span data-stu-id="978aa-161">Security Considerations</span></span>  

 <span data-ttu-id="978aa-162">Не должны кэшироваться ответы для запросов, требующих авторизации, так как авторизация не выполняется при получении ответа из кэша.</span><span class="sxs-lookup"><span data-stu-id="978aa-162">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="978aa-163">Кэширование таких ответов серьезно снижает безопасность.</span><span class="sxs-lookup"><span data-stu-id="978aa-163">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="978aa-164">Обычно запросы, требующие авторизации, содержат данные конкретного пользователя, в силу чего кэширование на стороне сервера просто не имеет смысла.</span><span class="sxs-lookup"><span data-stu-id="978aa-164">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="978aa-165">В таких ситуациях практичнее использовать кэширование на стороне клиента или вовсе не использовать кэширование.</span><span class="sxs-lookup"><span data-stu-id="978aa-165">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
