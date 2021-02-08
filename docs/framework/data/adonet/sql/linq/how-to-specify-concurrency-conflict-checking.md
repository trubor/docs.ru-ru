---
description: Дополнительные сведения см. в статье как указать проверку Concurrency-Conflict
title: Практическое руководство. Как организовать проверку наличия конфликтов параллелизма
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: a1c1c771dba95e558d86764d023625a63e9e53bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785930"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="b09f8-103">Практическое руководство. Как организовать проверку наличия конфликтов параллелизма</span><span class="sxs-lookup"><span data-stu-id="b09f8-103">How to: Specify Concurrency-Conflict Checking</span></span>

<span data-ttu-id="b09f8-104">Можно указать, какие столбцы базы данных должны проверяться на наличие конфликтов параллелизма при вызове метода <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="b09f8-104">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="b09f8-105">Дополнительные сведения см. [в разделе инструкции. Указание элементов, проверяемых на наличие конфликтов параллелизма](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="b09f8-105">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b09f8-106">Пример</span><span class="sxs-lookup"><span data-stu-id="b09f8-106">Example</span></span>  

 <span data-ttu-id="b09f8-107">В следующем примере кода указывается, что член `HomePage` никогда не должен включаться в проверки обновлений.</span><span class="sxs-lookup"><span data-stu-id="b09f8-107">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="b09f8-108">Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="b09f8-108">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b09f8-109">См. также</span><span class="sxs-lookup"><span data-stu-id="b09f8-109">See also</span></span>

- [<span data-ttu-id="b09f8-110">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b09f8-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b09f8-111">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="b09f8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
