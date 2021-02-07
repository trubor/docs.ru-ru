---
description: 'Дополнительные сведения: инструкции по возврату наборов строк'
title: Практическое руководство. Как возвращать наборы строк
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b799ce82542e6929f42485508b3a2c36cc42ee60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723391"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="70b70-103">Практическое руководство. Как возвращать наборы строк</span><span class="sxs-lookup"><span data-stu-id="70b70-103">How to: Return Rowsets</span></span>

<span data-ttu-id="70b70-104">В данном примере показано возвращение набора строк из базы данных и включение входного параметра в результаты фильтрации.</span><span class="sxs-lookup"><span data-stu-id="70b70-104">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="70b70-105">При выполнении хранимой процедуры, возвращающей набор строк, используется *результирующий* класс, хранящий возвращаемые результаты из хранимой процедуры.</span><span class="sxs-lookup"><span data-stu-id="70b70-105">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="70b70-106">Дополнительные сведения см. в разделе [анализ исходного кода LINQ to SQL](analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="70b70-106">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70b70-107">Пример</span><span class="sxs-lookup"><span data-stu-id="70b70-107">Example</span></span>  

 <span data-ttu-id="70b70-108">В следующем примере представлена хранимая процедура, которая возвращает строки клиентов и использует входной параметр для возврата только тех строк, в которых "Лондон" указан как город клиентов.</span><span class="sxs-lookup"><span data-stu-id="70b70-108">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="70b70-109">В примере предполагается использование перечислимого класса `CustomersByCityResult`.</span><span class="sxs-lookup"><span data-stu-id="70b70-109">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```sql  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="70b70-110">См. также</span><span class="sxs-lookup"><span data-stu-id="70b70-110">See also</span></span>

- [<span data-ttu-id="70b70-111">Хранимые процедуры</span><span class="sxs-lookup"><span data-stu-id="70b70-111">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="70b70-112">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="70b70-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
