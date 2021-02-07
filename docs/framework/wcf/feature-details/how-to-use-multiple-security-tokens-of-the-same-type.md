---
description: 'Дополнительные сведения: как использовать несколько маркеров безопасности одного типа'
title: Практическое руководство. Использование нескольких маркеров безопасности одного типа
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 0cbf831c82fdc2aee5a09237c586286a5776d234
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734260"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="42053-103">Практическое руководство. Использование нескольких маркеров безопасности одного типа</span><span class="sxs-lookup"><span data-stu-id="42053-103">How to: Use Multiple Security Tokens of the Same Type</span></span>

- <span data-ttu-id="42053-104">В платформа .NET Framework 3,0 клиентское сообщение содержит только один маркер любого заданного типа.</span><span class="sxs-lookup"><span data-stu-id="42053-104">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="42053-105">Теперь клиентские сообщения могут содержать несколько маркеров одного типа.</span><span class="sxs-lookup"><span data-stu-id="42053-105">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="42053-106">В этом разделе описывается, как включать в сообщение клиента несколько маркеров одного типа.</span><span class="sxs-lookup"><span data-stu-id="42053-106">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="42053-107">Обратите внимание, что настроить таким образом службу невозможно: служба может содержать только один вспомогательный маркер.</span><span class="sxs-lookup"><span data-stu-id="42053-107">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="42053-108">Использование нескольких маркеров безопасности одного типа</span><span class="sxs-lookup"><span data-stu-id="42053-108">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="42053-109">Создайте пустую коллекцию элементов привязки для заполнения.</span><span class="sxs-lookup"><span data-stu-id="42053-109">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="42053-110">Создайте элемент привязки <xref:System.ServiceModel.Channels.SecurityBindingElement>, вызвав метод <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="42053-110">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="42053-111">Создайте коллекцию <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="42053-111">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="42053-112">Добавьте в коллекцию маркеры SAML.</span><span class="sxs-lookup"><span data-stu-id="42053-112">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="42053-113">Добавьте коллекцию к элементу привязки <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="42053-113">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="42053-114">Добавьте элементы привязки в коллекцию элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="42053-114">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="42053-115">Верните новую пользовательскую привязку, созданную из коллекции элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="42053-115">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="42053-116">Пример</span><span class="sxs-lookup"><span data-stu-id="42053-116">Example</span></span>  

 <span data-ttu-id="42053-117">Ниже приводится весь метод, описанный в предыдущей процедуре.</span><span class="sxs-lookup"><span data-stu-id="42053-117">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
