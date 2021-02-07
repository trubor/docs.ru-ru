---
description: Дополнительные сведения см. в статье как получить сведения о конфликте элементов
title: Практическое руководство. Как получить сведения о конфликтах элементов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 2a33aba1a113bdfd66bdc341bfc9ae59406f2c40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723404"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="a16d0-103">Практическое руководство. Как получить сведения о конфликтах элементов</span><span class="sxs-lookup"><span data-stu-id="a16d0-103">How to: Retrieve Member Conflict Information</span></span>

<span data-ttu-id="a16d0-104">Класс <xref:System.Data.Linq.MemberChangeConflict> можно использовать для получения сведений об отдельных членах конфликта.</span><span class="sxs-lookup"><span data-stu-id="a16d0-104">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="a16d0-105">В этом же контексте можно предусмотреть пользовательскую обработку конфликта для любого члена.</span><span class="sxs-lookup"><span data-stu-id="a16d0-105">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="a16d0-106">Дополнительные сведения см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a16d0-106">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a16d0-107">Пример</span><span class="sxs-lookup"><span data-stu-id="a16d0-107">Example</span></span>  

 <span data-ttu-id="a16d0-108">Следующий код выполняет итерацию объектов <xref:System.Data.Linq.ObjectChangeConflict>.</span><span class="sxs-lookup"><span data-stu-id="a16d0-108">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="a16d0-109">Итерация выполняется для каждого объекта <xref:System.Data.Linq.MemberChangeConflict>.</span><span class="sxs-lookup"><span data-stu-id="a16d0-109">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a16d0-110">Для предоставления сведений <xref:System.Reflection> добавьте пространство имен <xref:System.Data.Linq.MemberChangeConflict.Member%2A>.</span><span class="sxs-lookup"><span data-stu-id="a16d0-110">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a16d0-111">См. также</span><span class="sxs-lookup"><span data-stu-id="a16d0-111">See also</span></span>

- [<span data-ttu-id="a16d0-112">Практическое руководство. Как управлять конфликтами изменений</span><span class="sxs-lookup"><span data-stu-id="a16d0-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
