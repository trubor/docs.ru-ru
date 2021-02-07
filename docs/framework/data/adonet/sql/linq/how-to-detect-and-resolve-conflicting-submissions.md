---
description: Дополнительные сведения о том, как обнаруживать и устранять конфликты.
title: Практическое руководство. Как обнаруживать и разрешать конфликты отправки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 7ccfc9aeba8a21c3f5e950569d7650af087416a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739044"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="faf24-103">Практическое руководство. Как обнаруживать и разрешать конфликты отправки</span><span class="sxs-lookup"><span data-stu-id="faf24-103">How to: Detect and Resolve Conflicting Submissions</span></span>

<span data-ttu-id="faf24-104">Технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] предоставляет целый ряд ресурсов для обнаружения и разрешения конфликтов, возникающих при внесении изменений в базу данных несколькими пользователями.</span><span class="sxs-lookup"><span data-stu-id="faf24-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="faf24-105">Дополнительные сведения см. [в разделе руководство. Управление конфликтами изменений](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="faf24-105">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="faf24-106">Пример</span><span class="sxs-lookup"><span data-stu-id="faf24-106">Example</span></span>  

 <span data-ttu-id="faf24-107">В следующем примере показан `try` / `catch` блок, который перехватывает <xref:System.Data.Linq.ChangeConflictException> исключение.</span><span class="sxs-lookup"><span data-stu-id="faf24-107">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="faf24-108">Сведения о сущностях и членах для каждого конфликта отображаются в окне «Консоль».</span><span class="sxs-lookup"><span data-stu-id="faf24-108">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="faf24-109">Для поддержки извлечения этих сведений необходимо включить директиву `using System.Reflection` (`Imports System.Reflection` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="faf24-109">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="faf24-110">Для получения дополнительной информации см. <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="faf24-110">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="faf24-111">См. также</span><span class="sxs-lookup"><span data-stu-id="faf24-111">See also</span></span>

- [<span data-ttu-id="faf24-112">Внесение и отправка изменений данных</span><span class="sxs-lookup"><span data-stu-id="faf24-112">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="faf24-113">Практическое руководство. Как управлять конфликтами изменений</span><span class="sxs-lookup"><span data-stu-id="faf24-113">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
