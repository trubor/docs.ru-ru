---
description: Дополнительные сведения см. в статье как указать, когда создаются исключения параллелизма
title: Практическое руководство. Как указать, когда возникают исключения параллелизма
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: d445cabfd2498f3599d874c2b7983a86c2c36c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785878"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="3f8f3-103">Практическое руководство. Как указать, когда возникают исключения параллелизма</span><span class="sxs-lookup"><span data-stu-id="3f8f3-103">How to: Specify When Concurrency Exceptions are Thrown</span></span>

<span data-ttu-id="3f8f3-104">Если в связи с конфликтами оптимистической блокировки обновление объектов не выполняется, в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] вызывается исключение <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="3f8f3-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="3f8f3-105">Дополнительные сведения см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f8f3-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="3f8f3-106">Перед отправкой изменений в базу данных можно указать момент возникновения исключений блокировки.</span><span class="sxs-lookup"><span data-stu-id="3f8f3-106">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="3f8f3-107">Создавать исключение при первом сбое (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="3f8f3-107">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="3f8f3-108">Завершить все попытки обновления, собрать все ошибки и сообщить о них в исключении (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="3f8f3-108">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="3f8f3-109">Созданное исключение <xref:System.Data.Linq.ChangeConflictException> предоставляет доступ к коллекции <xref:System.Data.Linq.ChangeConflictCollection>.</span><span class="sxs-lookup"><span data-stu-id="3f8f3-109">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="3f8f3-110">Данная коллекция содержит сведения о каждом конфликте (сопоставленном с одной неудачной попыткой обновления), включая доступ к коллекции <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f8f3-110">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="3f8f3-111">Каждый конфликт члена сопоставляется с одним членом в обновлении, которое привело к сбою проверки блокировки.</span><span class="sxs-lookup"><span data-stu-id="3f8f3-111">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f8f3-112">Пример</span><span class="sxs-lookup"><span data-stu-id="3f8f3-112">Example</span></span>  

 <span data-ttu-id="3f8f3-113">В следующем коде приведены примеры обоих значений.</span><span class="sxs-lookup"><span data-stu-id="3f8f3-113">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3f8f3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3f8f3-114">See also</span></span>

- [<span data-ttu-id="3f8f3-115">Практическое руководство. Как управлять конфликтами изменений</span><span class="sxs-lookup"><span data-stu-id="3f8f3-115">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="3f8f3-116">Внесение и отправка изменений данных</span><span class="sxs-lookup"><span data-stu-id="3f8f3-116">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
