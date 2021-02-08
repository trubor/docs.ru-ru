---
description: 'Дополнительные сведения: как использовать функции Scalar-Valued User-Defined'
title: Практическое руководство. Как применять определяемые пользователем скалярные функции
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: e606dd3f840b8f082928217c6118b48d8d4a2e5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785814"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="49c1e-103">Практическое руководство. Как применять определяемые пользователем скалярные функции</span><span class="sxs-lookup"><span data-stu-id="49c1e-103">How to: Use Scalar-Valued User-Defined Functions</span></span>

<span data-ttu-id="49c1e-104">Для сопоставления клиентского метода, определенного в классе, с пользовательской функцией используется атрибут <xref:System.Data.Linq.Mapping.FunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="49c1e-104">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="49c1e-105">Обратите внимание, что тело метода создает выражение, перехватывающее назначение вызова метода, и передает это выражение в <xref:System.Data.Linq.DataContext> для преобразования и выполнения.</span><span class="sxs-lookup"><span data-stu-id="49c1e-105">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49c1e-106">Прямое выполнение возможно только при вызове функции вне запроса.</span><span class="sxs-lookup"><span data-stu-id="49c1e-106">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="49c1e-107">Дополнительные сведения см. [в разделе инструкции. вызов User-Defined функций встроенной функции](how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="49c1e-107">For more information, see [How to: Call User-Defined Functions Inline](how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49c1e-108">Пример</span><span class="sxs-lookup"><span data-stu-id="49c1e-108">Example</span></span>  

 <span data-ttu-id="49c1e-109">В следующем коде SQL представлена скалярная пользовательская функция `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="49c1e-109">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 <span data-ttu-id="49c1e-110">Для этого кода следует отобразить клиентский метод, подобный следующему.</span><span class="sxs-lookup"><span data-stu-id="49c1e-110">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="49c1e-111">См. также</span><span class="sxs-lookup"><span data-stu-id="49c1e-111">See also</span></span>

- [<span data-ttu-id="49c1e-112">Определяемые пользователем функции</span><span class="sxs-lookup"><span data-stu-id="49c1e-112">User-Defined Functions</span></span>](user-defined-functions.md)
