---
description: 'Дополнительные сведения: обработка ошибок WCF Web HTTP'
title: Обработка ошибок веб-протокола HTTP WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 88483c249bc1b6b866517ca10b348c0885fc34fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779483"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="80f13-103">Обработка ошибок веб-протокола HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="80f13-103">WCF Web HTTP Error Handling</span></span>

<span data-ttu-id="80f13-104">Обработка ошибок веб-протокола HTTP Windows Communication Foundation (WCF) позволяет возвращать ошибки из служб WCF Web HTTP, которые указывают код состояния HTTP и возвращают сведения об ошибке, используя тот же формат, что и операция (например, XML или JSON).</span><span class="sxs-lookup"><span data-stu-id="80f13-104">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="80f13-105">Обработка ошибок веб-протокола HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="80f13-105">WCF Web HTTP Error Handling</span></span>  

 <span data-ttu-id="80f13-106">Класс <xref:System.ServiceModel.Web.WebFaultException> содержит конструктор, позволяющий указать код состояния HTTP.</span><span class="sxs-lookup"><span data-stu-id="80f13-106">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="80f13-107">Затем этот код состояния возвращается клиенту.</span><span class="sxs-lookup"><span data-stu-id="80f13-107">This status code is then returned to the client.</span></span> <span data-ttu-id="80f13-108">Общая версия класса <xref:System.ServiceModel.Web.WebFaultException>, <xref:System.ServiceModel.Web.WebFaultException%601> позволяет возвращать определенный пользователем тип, содержащий сведения о возникшей ошибке.</span><span class="sxs-lookup"><span data-stu-id="80f13-108">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="80f13-109">Этот пользовательский объект сериализуется с помощью формата, указанного операцией и возвращенного клиенту.</span><span class="sxs-lookup"><span data-stu-id="80f13-109">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="80f13-110">Следующий пример показывает, как вернуть код состояния HTTP.</span><span class="sxs-lookup"><span data-stu-id="80f13-110">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="80f13-111">В следующем примере показано, как вернуть код состояния HTTP и дополнительные сведения в типе, определяемом пользователем.</span><span class="sxs-lookup"><span data-stu-id="80f13-111">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="80f13-112">`MyErrorDetail` - определяемый пользователем тип, который содержит дополнительные сведения о возникшей ошибке.</span><span class="sxs-lookup"><span data-stu-id="80f13-112">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="80f13-113">В приведенном выше коде возвращается ответ HTTP с кодом состояния «доступ запрещен» и экземпляром объекта `MyErrorDetails` в теле ответа.</span><span class="sxs-lookup"><span data-stu-id="80f13-113">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="80f13-114">Формат объекта `MyErrorDetails` определяется следующими элементами.</span><span class="sxs-lookup"><span data-stu-id="80f13-114">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="80f13-115">Значение параметра `ResponseFormat` атрибута <xref:System.ServiceModel.Web.WebGetAttribute> или <xref:System.ServiceModel.Web.WebInvokeAttribute>, указанного в операции службы.</span><span class="sxs-lookup"><span data-stu-id="80f13-115">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="80f13-116">Значение <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="80f13-116">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="80f13-117">Значение свойства <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> при обращении к <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="80f13-117">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="80f13-118">Дополнительные сведения о влиянии этих значений на форматирование операции см. в разделе [веб-форматирование WCF](wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="80f13-118">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="80f13-119">Исключение <xref:System.ServiceModel.Web.WebFaultException> является <xref:System.ServiceModel.FaultException> и, следовательно, может быть использовано в качестве модели программирования ошибок для служб, предоставляющих конечные точки SOAP, а также сетевые конечные точки HTTP.</span><span class="sxs-lookup"><span data-stu-id="80f13-119"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f13-120">См. также</span><span class="sxs-lookup"><span data-stu-id="80f13-120">See also</span></span>

- [<span data-ttu-id="80f13-121">Модель веб-программирования HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="80f13-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="80f13-122">Форматирование веб-объектов HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="80f13-122">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)
- [<span data-ttu-id="80f13-123">Определение и задание сбоев</span><span class="sxs-lookup"><span data-stu-id="80f13-123">Defining and Specifying Faults</span></span>](../defining-and-specifying-faults.md)
- [<span data-ttu-id="80f13-124">Обработка исключений и сбоев</span><span class="sxs-lookup"><span data-stu-id="80f13-124">Handling Exceptions and Faults</span></span>](../extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="80f13-125">Сбои при отправке и получении</span><span class="sxs-lookup"><span data-stu-id="80f13-125">Sending and Receiving Faults</span></span>](../sending-and-receiving-faults.md)
