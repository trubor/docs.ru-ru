---
description: Дополнительные сведения о том, как выполнять команды SQL непосредственно.
title: Практическое руководство. Как прямо выполнять команды SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 9dd53b3582b6099bae51dc008debd8cb3142e386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786034"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="82a64-103">Практическое руководство. Как прямо выполнять команды SQL</span><span class="sxs-lookup"><span data-stu-id="82a64-103">How to: Directly Execute SQL Commands</span></span>

<span data-ttu-id="82a64-104">Если предположить наличие подключения <xref:System.Data.Linq.DataContext>, для выполнения команд, которые не возвращают объекты, можно воспользоваться методом <xref:System.Data.Linq.DataContext.ExecuteCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="82a64-104">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82a64-105">Пример</span><span class="sxs-lookup"><span data-stu-id="82a64-105">Example</span></span>  

 <span data-ttu-id="82a64-106">В следующем примере SQL Server увеличивает цену за единицу на 1.</span><span class="sxs-lookup"><span data-stu-id="82a64-106">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="82a64-107">См. также</span><span class="sxs-lookup"><span data-stu-id="82a64-107">See also</span></span>

- [<span data-ttu-id="82a64-108">Практическое руководство. Как прямо выполнять запросы SQL</span><span class="sxs-lookup"><span data-stu-id="82a64-108">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="82a64-109">Установка связи с базой данных</span><span class="sxs-lookup"><span data-stu-id="82a64-109">Communicating with the Database</span></span>](communicating-with-the-database.md)
