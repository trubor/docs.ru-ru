---
description: 'Дополнительные сведения: как настроить привязку System-Provided'
title: Практическое руководство. Изменение привязки, предоставляемой системой
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: c0463a8e427e6503f0e68bc58eb488f9b0bad15a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668959"
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="d0893-103">Практическое руководство. Изменение привязки, предоставляемой системой</span><span class="sxs-lookup"><span data-stu-id="d0893-103">How to: Customize a System-Provided Binding</span></span>

<span data-ttu-id="d0893-104">Windows Communication Foundation (WCF) включает несколько предоставляемых системой привязок, которые позволяют настроить некоторые свойства базовых элементов привязки, но не все свойства.</span><span class="sxs-lookup"><span data-stu-id="d0893-104">Windows Communication Foundation (WCF) includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="d0893-105">В данном разделе показано, как задать свойства в элементах привязки, чтобы создать пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="d0893-105">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 <span data-ttu-id="d0893-106">Дополнительные сведения о том, как непосредственно создавать и настраивать элементы привязки без использования привязок, предоставляемых системой, см. в разделе [пользовательские привязки](custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="d0893-106">For more information about how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](custom-bindings.md).</span></span>  
  
 <span data-ttu-id="d0893-107">Дополнительные сведения о создании и расширении пользовательских привязок см. в разделе [Расширение привязок](extending-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="d0893-107">For more information about creating and extending custom bindings, see [Extending Bindings](extending-bindings.md).</span></span>  
  
 <span data-ttu-id="d0893-108">В WCF все привязки состоят из *элементов привязки*.</span><span class="sxs-lookup"><span data-stu-id="d0893-108">In WCF all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="d0893-109">Каждый элемент привязки наследуется от класса <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d0893-109">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="d0893-110">Привязки, предоставляемые системой, такие как <xref:System.ServiceModel.BasicHttpBinding>, создают и настраивают собственные элементы привязки.</span><span class="sxs-lookup"><span data-stu-id="d0893-110">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="d0893-111">В данном разделе показано, как получить доступ и изменить свойства этих элементов привязки, которые не предоставляются непосредственно в привязке, в частности, класс <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d0893-111">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="d0893-112">Отдельные элементы привязки содержатся в коллекции, представленной классом <xref:System.ServiceModel.Channels.BindingElementCollection>, и добавляются в следующем порядке: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding и Transport.</span><span class="sxs-lookup"><span data-stu-id="d0893-112">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="d0893-113">Обратите внимание, что все перечисленные элементы привязки являются обязательными для каждой привязки.</span><span class="sxs-lookup"><span data-stu-id="d0893-113">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="d0893-114">Пользовательские элементы привязки также могут отображаться в коллекции элементов привязки и должны отображаться в указанном выше порядке.</span><span class="sxs-lookup"><span data-stu-id="d0893-114">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="d0893-115">Например, пользовательский транспорт должен быть последним элементом в коллекции элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="d0893-115">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="d0893-116">Класс <xref:System.ServiceModel.BasicHttpBinding> содержит три элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="d0893-116">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1. <span data-ttu-id="d0893-117">Необязательный элемент привязки безопасности: класс <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, используемый с транспортом HTTP (безопасность на уровне сообщений), или класс <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, используемый при предоставлении безопасности на уровне транспорта, при этом используется транспорт HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d0893-117">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2. <span data-ttu-id="d0893-118">Обязательный элемент привязки кодировщика сообщений: элемент <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> или элемент <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d0893-118">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3. <span data-ttu-id="d0893-119">Обязательный элемент привязки транспорта: элемент <xref:System.ServiceModel.Channels.HttpTransportBindingElement> или элемент <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d0893-119">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="d0893-120">В этом примере мы создаем экземпляр привязки, создаем *пользовательскую привязку* , просматриваете элементы привязки в пользовательской привязке, а когда найдете элемент привязки HTTP, свойству присваивается значение `KeepAliveEnabled` `false` .</span><span class="sxs-lookup"><span data-stu-id="d0893-120">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="d0893-121">Свойство `KeepAliveEnabled` не представлено напрямую в привязке `BasicHttpBinding`, поэтому необходимо создать пользовательскую привязку, чтобы перейти вниз к элементу привязки и присвоить этому свойству значение.</span><span class="sxs-lookup"><span data-stu-id="d0893-121">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="d0893-122">Изменение привязки, предоставляемой системой</span><span class="sxs-lookup"><span data-stu-id="d0893-122">To modify a system-provided binding</span></span>  
  
1. <span data-ttu-id="d0893-123">Создайте экземпляр класса <xref:System.ServiceModel.BasicHttpBinding> и установите для него режим безопасности на уровне сообщений.</span><span class="sxs-lookup"><span data-stu-id="d0893-123">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. <span data-ttu-id="d0893-124">Создайте пользовательскую привязку из привязки и создайте класс <xref:System.ServiceModel.Channels.BindingElementCollection> из одного из свойств пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="d0893-124">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. <span data-ttu-id="d0893-125">Выполните цикл по классу <xref:System.ServiceModel.Channels.BindingElementCollection> и при нахождении класса <xref:System.ServiceModel.Channels.HttpTransportBindingElement> присвойте его свойству <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> значение `false`.</span><span class="sxs-lookup"><span data-stu-id="d0893-125">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d0893-126">См. также</span><span class="sxs-lookup"><span data-stu-id="d0893-126">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d0893-127">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="d0893-127">Custom Bindings</span></span>](custom-bindings.md)
