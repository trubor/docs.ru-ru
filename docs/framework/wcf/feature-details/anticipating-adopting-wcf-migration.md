---
description: 'Дополнительные сведения о том, как предполагается внедрять Windows Communication Foundation: ускорение миграции в будущем'
title: 'Планирование перехода на платформу Windows Communication Foundation: упрощение будущей миграции'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 6ea81b1dd01ed45ff62fa50c1b17442f88fc05af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643817"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="3faac-103">Планирование перехода на платформу Windows Communication Foundation: упрощение будущей миграции</span><span class="sxs-lookup"><span data-stu-id="3faac-103">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>

<span data-ttu-id="3faac-104">Чтобы упростить миграцию новых приложений ASP.NET в WCF, следуйте приведенным выше рекомендациям, а также приведенным ниже рекомендациям.</span><span class="sxs-lookup"><span data-stu-id="3faac-104">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="3faac-105">Протоколы</span><span class="sxs-lookup"><span data-stu-id="3faac-105">Protocols</span></span>  

 <span data-ttu-id="3faac-106">Отключите поддержку ASP.NET 2.0 для SOAP 1.2:</span><span class="sxs-lookup"><span data-stu-id="3faac-106">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>
      </webServices>  
     </system.web>
</configuration>  
```  
  
 <span data-ttu-id="3faac-107">Это рекомендуется, так как WCF требует, чтобы сообщения, которые были согласованы с различными протоколами, например SOAP 1,1 и SOAP 1,2, могли использовать разные конечные точки.</span><span class="sxs-lookup"><span data-stu-id="3faac-107">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="3faac-108">Если веб-служба ASP.NET 2,0 настроена для поддержки как SOAP 1,1, так и SOAP 1,2, которая является конфигурацией по умолчанию, то она не может быть перенесена в одну конечную точку WCF по исходному адресу, которая наверняка будет совместима со всеми существующими клиентами веб-службы ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3faac-108">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="3faac-109">Кроме того, выбор версии SOAP 1.2 вместо версии 1.1 будет более строго ограничивать клиентуру службы.</span><span class="sxs-lookup"><span data-stu-id="3faac-109">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="3faac-110">Разработка служб</span><span class="sxs-lookup"><span data-stu-id="3faac-110">Service Development</span></span>  

 <span data-ttu-id="3faac-111">WCF позволяет определять контракты служб, применяя <xref:System.ServiceModel.ServiceContractAttribute> либо к интерфейсам, либо к классам.</span><span class="sxs-lookup"><span data-stu-id="3faac-111">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="3faac-112">Рекомендуется применять этот атрибут для интерфейса, а не для класса, поскольку при этом создается определение контракта, который может быть по-разному реализован любым количеством классов.</span><span class="sxs-lookup"><span data-stu-id="3faac-112">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="3faac-113">ASP.NET 2.0 поддерживает возможность применения атрибута <xref:System.Web.Services.WebService> для интерфейсов и классов.</span><span class="sxs-lookup"><span data-stu-id="3faac-113">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="3faac-114">Однако, как уже было сказано, в ASP.NET 2.0 существует недостаток, из-за которого параметр Namespace атрибута <xref:System.Web.Services.WebService> не имеет силы, если этот атрибут применяется для интерфейса, а не класса.</span><span class="sxs-lookup"><span data-stu-id="3faac-114">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="3faac-115">Поскольку как правило, рекомендуется изменять пространство имен службы по умолчанию, `http://tempuri.org` используя параметр Namespace <xref:System.Web.Services.WebService> атрибута, он должен продолжить определение веб-служб ASP.NET, применяя <xref:System.ServiceModel.ServiceContractAttribute> атрибут к интерфейсам или к классам.</span><span class="sxs-lookup"><span data-stu-id="3faac-115">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="3faac-116">Обеспечьте минимально возможный код в методах, с помощью которых определяются эти интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="3faac-116">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="3faac-117">Заставьте их делегировать свою работу в другие классы.</span><span class="sxs-lookup"><span data-stu-id="3faac-117">Have them delegate their work to other classes.</span></span> <span data-ttu-id="3faac-118">Новые типы служб WCF могут также делегировать свои важный работу этим классам.</span><span class="sxs-lookup"><span data-stu-id="3faac-118">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="3faac-119">Обеспечьте явные имена для операций службы, используя параметр `MessageName` атрибута <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3faac-119">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="3faac-120">Это важно, так как имена по умолчанию для операций в ASP.NET отличаются от имен по умолчанию, предоставляемых WCF.</span><span class="sxs-lookup"><span data-stu-id="3faac-120">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="3faac-121">Обеспечение явных имен исключает необходимость полагаться на имена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3faac-121">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="3faac-122">Не реализуйте операции веб-службы ASP.NET с помощью полиморфизмных методов, так как WCF не поддерживает реализацию операций с методами с использованием полиморфизма.</span><span class="sxs-lookup"><span data-stu-id="3faac-122">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="3faac-123">Используйте атрибут <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>, чтобы обеспечить явные значения для заголовков SOAPAction HTTP, по которым запросы HTTP будут направляться в методы.</span><span class="sxs-lookup"><span data-stu-id="3faac-123">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="3faac-124">При использовании этого подхода не придется полагаться на значения SOAPAction по умолчанию, используемые ASP.NET и WCF.</span><span class="sxs-lookup"><span data-stu-id="3faac-124">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="3faac-125">Избегайте использования расширений SOAP.</span><span class="sxs-lookup"><span data-stu-id="3faac-125">Avoid using SOAP extensions.</span></span> <span data-ttu-id="3faac-126">Если требуются расширения SOAP, определите, является ли цель, для которой они считаются, функцией, уже предоставляемой WCF.</span><span class="sxs-lookup"><span data-stu-id="3faac-126">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="3faac-127">Если это действительно так, снова рассмотрите вариант выбора, чтобы не внедрять WCF немедленно.</span><span class="sxs-lookup"><span data-stu-id="3faac-127">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="3faac-128">Управление состоянием</span><span class="sxs-lookup"><span data-stu-id="3faac-128">State Management</span></span>  

 <span data-ttu-id="3faac-129">Избегайте поддержания состояния в службах.</span><span class="sxs-lookup"><span data-stu-id="3faac-129">Avoid having to maintain state in services.</span></span> <span data-ttu-id="3faac-130">Не только поддержание состояния, как правило, нарушает масштабируемость приложения, но механизмы управления состоянием ASP.NET и WCF сильно отличаются, хотя WCF поддерживает механизмы ASP.NET в режиме совместимости ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3faac-130">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="3faac-131">Обработка исключений</span><span class="sxs-lookup"><span data-stu-id="3faac-131">Exception Handling</span></span>  

 <span data-ttu-id="3faac-132">При разработке структур типов данных, которые должны передаваться и приниматься службой, разработайте также структуры для представления различных типов исключений, которые могут происходить в службе и подлежать передаче клиенту.</span><span class="sxs-lookup"><span data-stu-id="3faac-132">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="3faac-133">Предоставьте таким классам возможность сериализовать себя в XML:</span><span class="sxs-lookup"><span data-stu-id="3faac-133">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```csharp  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 <span data-ttu-id="3faac-134">Затем классы могут использоваться для предоставления сведений в отношении явно вызванных экземпляров <xref:System.Web.Services.Protocols.SoapException>:</span><span class="sxs-lookup"><span data-stu-id="3faac-134">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="3faac-135">Эти классы исключений можно легко использовать с <xref:System.ServiceModel.FaultException%601> классом WCF для создания нового `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="3faac-135">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="3faac-136">Безопасность</span><span class="sxs-lookup"><span data-stu-id="3faac-136">Security</span></span>  

 <span data-ttu-id="3faac-137">Ниже приведены некоторые рекомендации по безопасности.</span><span class="sxs-lookup"><span data-stu-id="3faac-137">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="3faac-138">Избегайте использования профилей ASP.NET 2,0, так как их использование приведет к ограничению использования режима интеграции ASP.NET, если служба была перенесена в WCF.</span><span class="sxs-lookup"><span data-stu-id="3faac-138">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="3faac-139">Избегайте использования списков управления доступом для управления доступом к службам, так как ASP.NET веб-службы поддерживают списки ACL с помощью службы IIS (IIS), WCF не — так как веб-службы ASP.NET зависят от служб IIS для размещения, и WCF не обязательно должна размещаться в IIS.</span><span class="sxs-lookup"><span data-stu-id="3faac-139">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="3faac-140">Не принимайте во внимание использование поставщиков ролей ASP.NET 2.0 для авторизации доступа к ресурсам службы.</span><span class="sxs-lookup"><span data-stu-id="3faac-140">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3faac-141">См. также</span><span class="sxs-lookup"><span data-stu-id="3faac-141">See also</span></span>

- [<span data-ttu-id="3faac-142">Планирование перехода на платформу Windows Communication Foundation: упрощение будущей интеграции</span><span class="sxs-lookup"><span data-stu-id="3faac-142">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](anticipating-adopting-the-wcf-easing-future-integration.md)
