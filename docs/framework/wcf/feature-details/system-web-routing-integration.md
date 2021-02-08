---
description: Дополнительные сведения об интеграции System. Web. Routing
title: Интеграция с System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 8f396d5a3cad30f5cc67cb0cf44fad76a0bb54c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793341"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="e91a0-103">Интеграция с System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="e91a0-103">System.Web.Routing Integration</span></span>

<span data-ttu-id="e91a0-104">При размещении службы Windows Communication Foundation (WCF) в службе IIS вы размещаете SVC-файл в виртуальном каталоге.</span><span class="sxs-lookup"><span data-stu-id="e91a0-104">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="e91a0-105">Этот SVC-файл указывает фабрику узла службы, которую необходимо использовать, а также класс, реализующий эту службу.</span><span class="sxs-lookup"><span data-stu-id="e91a0-105">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="e91a0-106">При выполнении запросов к службе вы задаете SVC файл в URI, например: `http://contoso.com/EmployeeServce.svc` .</span><span class="sxs-lookup"><span data-stu-id="e91a0-106">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="e91a0-107">Для разработчиков служб REST такой тип URI не является оптимальным.</span><span class="sxs-lookup"><span data-stu-id="e91a0-107">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="e91a0-108">URI для служб REST указывают определенный ресурс и обычно не имеют модулей.</span><span class="sxs-lookup"><span data-stu-id="e91a0-108">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="e91a0-109"><xref:System.Web.Routing>Функция интеграции позволяет разместить службу WCF RESTful, которая реагирует на URI без расширения.</span><span class="sxs-lookup"><span data-stu-id="e91a0-109">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="e91a0-110">Дополнительные сведения о маршрутизации см. в разделе [ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e91a0-110">For more information about routing see [ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="e91a0-111">Использование интеграции System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="e91a0-111">Using System.Web.Routing Integration</span></span>  

 <span data-ttu-id="e91a0-112">Для использования возможности интеграции <xref:System.Web.Routing> с помощью класса <xref:System.ServiceModel.Activation.ServiceRoute> создайте один или несколько маршрутов и добавьте их в <xref:System.Web.Routing.RouteTable> в файле Global.asax.</span><span class="sxs-lookup"><span data-stu-id="e91a0-112">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="e91a0-113">Это маршруты указывают относительные URI, по которым отвечает служба.</span><span class="sxs-lookup"><span data-stu-id="e91a0-113">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="e91a0-114">В приведенном ниже примере показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="e91a0-114">The following example shows how to do this.</span></span>  
  
```aspx-csharp  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));
   }  
</script>  
```  
  
 <span data-ttu-id="e91a0-115">Все запросы направляются по относительному URI, который начинается с Customers службы `Service`.</span><span class="sxs-lookup"><span data-stu-id="e91a0-115">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="e91a0-116">В файл Web.config необходимо добавить модуль `System.Web.Routing.UrlRoutingModule`, установить атрибут `runAllManagedModulesForAllRequests` в значение `true` и добавить обработчик `UrlRoutingHandler` в элемент`<system.webServer>`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e91a0-116">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 <span data-ttu-id="e91a0-117">Это позволит загрузить модуль и обработчик, которые необходимы для маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="e91a0-117">This loads a module and handler required for routing.</span></span> <span data-ttu-id="e91a0-118">Дополнительные сведения см. в разделе [Маршрутизация](routing.md).</span><span class="sxs-lookup"><span data-stu-id="e91a0-118">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="e91a0-119">Необходимо также установить атрибут `aspNetCompatibilityEnabled` в значение `true` в элементе `<serviceHostingEnvironment>`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e91a0-119">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="e91a0-120">Класс, реализующий службу, должен соответствовать требованиям к совместимости ASP.NET, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e91a0-120">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="e91a0-121">См. также</span><span class="sxs-lookup"><span data-stu-id="e91a0-121">See also</span></span>

- [<span data-ttu-id="e91a0-122">Модель веб-программирования HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="e91a0-122">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="e91a0-123">[Маршрутизация ASP.NET](/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e91a0-123">[ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
