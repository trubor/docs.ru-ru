---
description: Дополнительные сведения о том, как заключать отправку данных с помощью транзакций.
title: Практическое руководство. Как объединить в пакеты отправку данных с помощью транзакций
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: a1bbebfcdb4b65e83c4ac6dc9b87b06f33f2cb41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739031"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="78199-103">Практическое руководство. Как объединить в пакеты отправку данных с помощью транзакций</span><span class="sxs-lookup"><span data-stu-id="78199-103">How to: Bracket Data Submissions by Using Transactions</span></span>

<span data-ttu-id="78199-104">Для объединения запросов к базе данных в брекеты можно использовать класс <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="78199-104">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="78199-105">Дополнительные сведения см. в разделе [Поддержка транзакций](transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="78199-105">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78199-106">Пример</span><span class="sxs-lookup"><span data-stu-id="78199-106">Example</span></span>  

 <span data-ttu-id="78199-107">В следующем коде отправка данных помещается в класс <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="78199-107">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="78199-108">См. также</span><span class="sxs-lookup"><span data-stu-id="78199-108">See also</span></span>

- [<span data-ttu-id="78199-109">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="78199-109">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="78199-110">Внесение и отправка изменений данных</span><span class="sxs-lookup"><span data-stu-id="78199-110">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="78199-111">Поддержка транзакций</span><span class="sxs-lookup"><span data-stu-id="78199-111">Transaction Support</span></span>](transaction-support.md)
