---
description: Дополнительные сведения см. в статье как разрешить запросы метаданных при авторизации.
title: 'Как выполнить: Разрешение запросов метаданных в процессе авторизации'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: a9f5ab7db73aaa8a2a420a60c3172f1b1a738fb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742749"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="d8318-103">Как выполнить: Разрешение запросов метаданных в процессе авторизации</span><span class="sxs-lookup"><span data-stu-id="d8318-103">How To: Allow Metadata Requests While Authorizing</span></span>

<span data-ttu-id="d8318-104">В процессе настраиваемой авторизации может потребоваться разрешить обработку запроса для метаданных.</span><span class="sxs-lookup"><span data-stu-id="d8318-104">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="d8318-105">Следующий раздел содержит пошаговое руководство для проверки такого запроса.</span><span class="sxs-lookup"><span data-stu-id="d8318-105">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="d8318-106">Дополнительные сведения об авторизации Windows Communication Foundation (WCF) см. в разделе [авторизация](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="d8318-106">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="d8318-107">Разрешение запросов метаданных в процессе авторизации</span><span class="sxs-lookup"><span data-stu-id="d8318-107">To allow metadata requests during authorization</span></span>  
  
1. <span data-ttu-id="d8318-108">Создайте расширение класса <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="d8318-108">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2. <span data-ttu-id="d8318-109">Переопределите метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="d8318-109">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="d8318-110">Метод возвращает логическое значение `true` или `false`, в зависимости от того, разрешена ли авторизация.</span><span class="sxs-lookup"><span data-stu-id="d8318-110">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="d8318-111">Информация о текущей процедуре находится в классе <xref:System.ServiceModel.OperationContext> и передается как параметр методу.</span><span class="sxs-lookup"><span data-stu-id="d8318-111">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3. <span data-ttu-id="d8318-112">При переопределении проверяются имя контракта, пространство имен и действие, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d8318-112">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="d8318-113">При выполнении этих условий возвращается логическое значение `true.`</span><span class="sxs-lookup"><span data-stu-id="d8318-113">If the conditions are valid, then return `true.`</span></span>  
  
4. <span data-ttu-id="d8318-114">Используйте точку расширения для использования класса.</span><span class="sxs-lookup"><span data-stu-id="d8318-114">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="d8318-115">Дополнительные сведения см. [в разделе инструкции. Создание настраиваемого диспетчера авторизации для службы](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="d8318-115">For more information, see [How to: Create a Custom Authorization Manager for a Service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8318-116">Пример</span><span class="sxs-lookup"><span data-stu-id="d8318-116">Example</span></span>  

 <span data-ttu-id="d8318-117">В следующем примере показано переопределение метода <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8318-117">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d8318-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d8318-118">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="d8318-119">Авторизация</span><span class="sxs-lookup"><span data-stu-id="d8318-119">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="d8318-120">Управление утверждениями и авторизацией с помощью модели удостоверения</span><span class="sxs-lookup"><span data-stu-id="d8318-120">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
