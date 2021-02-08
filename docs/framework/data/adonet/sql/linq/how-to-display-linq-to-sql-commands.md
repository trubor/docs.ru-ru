---
description: 'Дополнительные сведения: инструкции по отображению команд LINQ to SQL'
title: Практическое руководство. Как отображать команды LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: 480e7c1cbcceb09f0d727d03569d6277e0dd754b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785995"
---
# <a name="how-to-display-linq-to-sql-commands"></a><span data-ttu-id="5aa62-103">Практическое руководство. Как отображать команды LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5aa62-103">How to: Display LINQ to SQL Commands</span></span>

<span data-ttu-id="5aa62-104">Для отображения команд SQL и других сведений используется оператор <xref:System.Data.Linq.DataContext.GetCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="5aa62-104">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> to display SQL commands and other information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aa62-105">Пример</span><span class="sxs-lookup"><span data-stu-id="5aa62-105">Example</span></span>  

 <span data-ttu-id="5aa62-106">В следующем примере в окне консоли отображается результат запроса, за которым следуют созданные команды SQL, тип команд и тип подключения.</span><span class="sxs-lookup"><span data-stu-id="5aa62-106">In the following example, the console window displays the output from the query, followed by the SQL commands that are generated, the type of commands, and the type of connection.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 <span data-ttu-id="5aa62-107">Выводится следующий результат.</span><span class="sxs-lookup"><span data-stu-id="5aa62-107">Output appears as follows:</span></span>  
  
```console  
Customers from London:  
    Thomas Hardy  
    Victoria Ashworth  
    Elizabeth Brown  
    Ann Devon  
    Simon Crowther  
    Marie Bertrand  
    Hari Kumar  
    Dominique Perrier  
```  
  
```console  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a><span data-ttu-id="5aa62-108">См. также</span><span class="sxs-lookup"><span data-stu-id="5aa62-108">See also</span></span>

- [<span data-ttu-id="5aa62-109">Поддержка отладки</span><span class="sxs-lookup"><span data-stu-id="5aa62-109">Debugging Support</span></span>](debugging-support.md)
