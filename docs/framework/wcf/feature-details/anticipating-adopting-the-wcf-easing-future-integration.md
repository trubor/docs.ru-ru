---
description: 'Дополнительные сведения о том, как предполагается внедрять Windows Communication Foundation: ускорение интеграции в будущем'
title: 'Планирование перехода на платформу Windows Communication Foundation: упрощение будущей интеграции'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 512e35e8a4cd6057c96e96a1474f393c3f006525
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643882"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="4b4b9-103">Планирование перехода на платформу Windows Communication Foundation: упрощение будущей интеграции</span><span class="sxs-lookup"><span data-stu-id="4b4b9-103">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>

<span data-ttu-id="4b4b9-104">Если вы используете ASP.NET сегодня и предложит использовать WCF в будущем, в этом разделе приводятся рекомендации по обеспечению совместной работы новых веб-служб ASP.NET и приложений WCF.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-104">If you use ASP.NET today, and anticipate using WCF in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with WCF applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="4b4b9-105">Основные рекомендации</span><span class="sxs-lookup"><span data-stu-id="4b4b9-105">General Recommendations</span></span>  

 <span data-ttu-id="4b4b9-106">Используйте для создания новых служб ASP.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-106">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="4b4b9-107">Это обеспечит доступ к усовершенствованиям, появившимся в новой версии.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-107">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="4b4b9-108">Тем не менее он также позволяет использовать компоненты ASP.NET 2,0 вместе с компонентами WCF в одном приложении.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-108">However, it will also allow for the possibility of using ASP.NET 2.0 components together with WCF components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="4b4b9-109">Протоколы</span><span class="sxs-lookup"><span data-stu-id="4b4b9-109">Protocols</span></span>  

 <span data-ttu-id="4b4b9-110">Используйте новую функцию ASP.NET 2.0 для проверки соответствия спецификации WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="4b4b9-110">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="4b4b9-111">Веб-службы ASP.NET, которые соответствуют стандартному профилю WS-I 1,1, будут взаимодействовать с клиентами WCF с помощью предопределенной привязки WCF, <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="4b4b9-111">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with WCF clients by using WCF predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="4b4b9-112">Разработка служб</span><span class="sxs-lookup"><span data-stu-id="4b4b9-112">Service Development</span></span>  

 <span data-ttu-id="4b4b9-113">Избегайте использования атрибута <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> для маршрутизации сообщений методами по полному имени элемента текста сообщения протокола SOAP вместо заголовка HTTP SOAPAction.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-113">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> <span data-ttu-id="4b4b9-114">WCF использует заголовок SOAPAction HTTP для маршрутизации сообщений.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-114">WCF uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="4b4b9-115">Представление данных</span><span class="sxs-lookup"><span data-stu-id="4b4b9-115">Data Representation</span></span>  

 <span data-ttu-id="4b4b9-116">XML-код, в который тип сериализуется сериализатором <xref:System.Xml.Serialization.XmlSerializer>, по умолчанию семантически идентичен XML-коду, в который тип сериализуется сериализатором <xref:System.Runtime.Serialization.DataContractSerializer>, при условии, что пространство имен для XML задано явным образом.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-116">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="4b4b9-117">При определении типа данных для использования с веб-службами ASP.NET в будущем для внедрения WCF выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-117">When defining a data type for use with ASP.NET Web services in anticipation of adopting WCF in the future, do the following:</span></span>  
  
1. <span data-ttu-id="4b4b9-118">Задавайте тип с использованием классов .NET Framework, а не схемы XML.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-118">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2. <span data-ttu-id="4b4b9-119">Добавляйте в класс только атрибуты <xref:System.SerializableAttribute> и <xref:System.Xml.Serialization.XmlRootAttribute>, используя последний для явного задания пространства имен для типа.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-119">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="4b4b9-120">Не добавляйте дополнительные атрибуты из пространства имен <xref:System.Xml.Serialization> для задания способа преобразования класса .NET Framework в XML.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-120">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="4b4b9-121">Используя этот подход, вы впоследствии сможете превратить классы .NET в контракты данных, добавив атрибуты <xref:System.Runtime.Serialization.DataContractAttribute> и <xref:System.Runtime.Serialization.DataMemberAttribute>, без значительного изменения XML-кода, в который классы сериализуются для передачи.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-121">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="4b4b9-122">Типы, используемые в сообщениях ASP.NET веб-служб, будут обрабатываться в виде контрактов данных приложениями WCF, а также с другими преимуществами, более высокой производительностью в приложениях WCF.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-122">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by WCF applications, yielding, amongst other benefits, better performance in WCF applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="4b4b9-123">Безопасность</span><span class="sxs-lookup"><span data-stu-id="4b4b9-123">Security</span></span>  

 <span data-ttu-id="4b4b9-124">Избегайте использования параметров проверки подлинности, предусмотренных в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-124">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="4b4b9-125">Клиенты WCF не поддерживают их.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-125">WCF clients do not support them.</span></span> <span data-ttu-id="4b4b9-126">Если необходимо обеспечить защиту службы, используйте параметры, предоставляемые WCF, так как эти параметры расширены и основаны на стандартных протоколах.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-126">If a service needs to be secured, use the options provided by WCF, because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b4b9-127">См. также</span><span class="sxs-lookup"><span data-stu-id="4b4b9-127">See also</span></span>

- [<span data-ttu-id="4b4b9-128">Планирование перехода на платформу Windows Communication Foundation: упрощение будущей миграции</span><span class="sxs-lookup"><span data-stu-id="4b4b9-128">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](anticipating-adopting-wcf-migration.md)
