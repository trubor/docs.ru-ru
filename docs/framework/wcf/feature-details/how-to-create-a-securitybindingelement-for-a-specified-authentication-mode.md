---
description: Дополнительные сведения о том, как создать SecurityBindingElement для указанного режима проверки подлинности.
title: Практическое руководство. Создание SecurityBindingElement для заданного режима проверки подлинности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: cb0831787b6d54daf561fc2750f1efe81bebfb0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734481"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="f823d-103">Практическое руководство. Создание SecurityBindingElement для заданного режима проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="f823d-103">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>

<span data-ttu-id="f823d-104">Windows Communication Foundation (WCF) предоставляет несколько режимов, с помощью которых клиенты и службы проходят проверку подлинности друг за другом.</span><span class="sxs-lookup"><span data-stu-id="f823d-104">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="f823d-105">Для этих режимов проверки подлинности можно создать привязки безопасности с помощью статических методов класса <xref:System.ServiceModel.Channels.SecurityBindingElement> или с помощью конфигурации, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f823d-105">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="f823d-106">Дополнительные сведения о 18 режимах проверки подлинности см. в статье [SecurityBindingElement Authentication modes](securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="f823d-106">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f823d-107">Пример</span><span class="sxs-lookup"><span data-stu-id="f823d-107">Example</span></span>  

 <span data-ttu-id="f823d-108">В следующем примере кода показаны методы создания привязок для различных методов проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="f823d-108">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f823d-109">После создания объекта <xref:System.ServiceModel.Channels.SecurityBindingElement> некоторые свойства являются неизменяемыми, такие как <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> и <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="f823d-109">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="f823d-110">Вызов `set` для этих свойств не изменяет их.</span><span class="sxs-lookup"><span data-stu-id="f823d-110">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f823d-111">См. также</span><span class="sxs-lookup"><span data-stu-id="f823d-111">See also</span></span>

- [<span data-ttu-id="f823d-112">Режимы проверки подлинности SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f823d-112">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)
- [<span data-ttu-id="f823d-113">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f823d-113">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
