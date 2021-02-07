---
description: 'Дополнительные сведения: создание пользовательского заголовка со знаком и-или зашифрованным'
title: Создание подписанного и зашифрованного пользовательского заголовка
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: d3952eeb37cbe09f72e179fcaa50c650fe9aa90d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705178"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="fc58c-103">Создание подписанного и зашифрованного пользовательского заголовка</span><span class="sxs-lookup"><span data-stu-id="fc58c-103">Creating a custom header that is signed and-or encrypted</span></span>

<span data-ttu-id="fc58c-104">При вызове службы, которая не является службой WCF, с помощью клиента WCF иногда приходится применять пользовательские заголовки протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="fc58c-104">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="fc58c-105">В WCF имеется ошибка канонизации, которая не позволяет подписанным и зашифрованным пользовательским заголовкам работать со службами, не являющимися службами WCF.</span><span class="sxs-lookup"><span data-stu-id="fc58c-105">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="fc58c-106">Проблема вызывается неверной канонизацией пространств имен XML по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="fc58c-106">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="fc58c-107">Она возникает только при вызове служб, не являющихся службами WCF, с подписанными и/или зашифрованными пользовательскими заголовками.</span><span class="sxs-lookup"><span data-stu-id="fc58c-107">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="fc58c-108">Когда служба получает сообщение, содержащее подписанный и/или зашифрованный пользовательский заголовок, ей не удается проверить сигнатуру.</span><span class="sxs-lookup"><span data-stu-id="fc58c-108">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="fc58c-109">Данный обходный путь решения проблемы обходит проблему канонизации, позволяет работать со службами, которые не являются службами WCF, но не мешает работать и со службами WCF.</span><span class="sxs-lookup"><span data-stu-id="fc58c-109">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="fc58c-110">Определение пользовательского заголовка</span><span class="sxs-lookup"><span data-stu-id="fc58c-110">Defining the custom header</span></span>  

 <span data-ttu-id="fc58c-111">Пользовательские заголовки определяются посредством определения контракта сообщения и отметки элементов, которые должны отправляться в форме заголовков, атрибутом <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fc58c-111">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="fc58c-112">Чтобы обойти ошибку канонизации, необходимо, чтобы сериализатор XML объявлял пространство имен в пользовательском заголовке с помощью префикса вместо объявления пространства имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="fc58c-112">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="fc58c-113">В коде ниже показывается определение типа данных, который будет использоваться в качестве заголовка сообщения, с правильным объявлением пространства имен.</span><span class="sxs-lookup"><span data-stu-id="fc58c-113">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
```csharp
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="fc58c-114">Этот код объявляет новый тип, `msgHeaderElement`, который будет сериализоваться с помощью сериализатора XML.</span><span class="sxs-lookup"><span data-stu-id="fc58c-114">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="fc58c-115">Когда экземпляр данного типа сериализуется, он будет определять пространство имен с префиксом «h», тем самым обходя ошибку канонизации.</span><span class="sxs-lookup"><span data-stu-id="fc58c-115">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="fc58c-116">Затем контракт сообщения определяет экземпляр `msgHeaderElement` и отмечает его атрибутом <xref:System.ServiceModel.MessageHeaderAttribute>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="fc58c-116">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
```csharp
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc58c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="fc58c-117">See also</span></span>

- [<span data-ttu-id="fc58c-118">Контракт сообщения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="fc58c-118">Default Message Contract</span></span>](../samples/default-message-contract.md)
- [<span data-ttu-id="fc58c-119">Контракты сообщений</span><span class="sxs-lookup"><span data-stu-id="fc58c-119">Message Contracts</span></span>](../samples/message-contracts.md)
- [<span data-ttu-id="fc58c-120">Использование контрактов сообщений</span><span class="sxs-lookup"><span data-stu-id="fc58c-120">Using Message Contracts</span></span>](using-message-contracts.md)
