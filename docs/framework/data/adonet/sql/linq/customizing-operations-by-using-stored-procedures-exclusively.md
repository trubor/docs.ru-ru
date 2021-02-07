---
description: 'Дополнительные сведения: Настройка операций с монопольным использованием хранимых процедур'
title: Настройка операций за счет исключительного использования хранимых процедур
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 4ddcc6b4face1abccb502e12617105a734bb5f0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729553"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="12947-103">Настройка операций за счет исключительного использования хранимых процедур</span><span class="sxs-lookup"><span data-stu-id="12947-103">Customizing Operations by Using Stored Procedures Exclusively</span></span>

<span data-ttu-id="12947-104">Распространенным сценарием является доступ к данным с использованием только хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="12947-104">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12947-105">Пример</span><span class="sxs-lookup"><span data-stu-id="12947-105">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="12947-106">Описание</span><span class="sxs-lookup"><span data-stu-id="12947-106">Description</span></span>  

 <span data-ttu-id="12947-107">Вы можете изменить пример, предоставленный в разделе [Настройка операций, используя хранимые процедуры](customizing-operations-by-using-stored-procedures.md) , заменив даже первый запрос (который вызывает динамическое выполнение SQL) вызовом метода, который создает оболочку для хранимой процедуры.</span><span class="sxs-lookup"><span data-stu-id="12947-107">You can modify the example provided in [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="12947-108">Предположим, что `CustomersByCity` является методом, как в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="12947-108">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="12947-109">Код</span><span class="sxs-lookup"><span data-stu-id="12947-109">Code</span></span>  

 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="12947-110">Следующий код выполняется без динамического SQL.</span><span class="sxs-lookup"><span data-stu-id="12947-110">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="12947-111">См. также</span><span class="sxs-lookup"><span data-stu-id="12947-111">See also</span></span>

- [<span data-ttu-id="12947-112">Ответственность разработчика при переопределении поведения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="12947-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)
