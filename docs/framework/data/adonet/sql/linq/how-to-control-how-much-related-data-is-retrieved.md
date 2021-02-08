---
description: Дополнительные сведения о том, как управлять объемом получаемых связанных данных.
title: Практическое руководство. Как управлять объемом получаемых взаимосвязанных данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: becf1282d18d5c630da3e3be27c62ebae404d940
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786047"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="9bc34-103">Практическое руководство. Как управлять объемом получаемых взаимосвязанных данных</span><span class="sxs-lookup"><span data-stu-id="9bc34-103">How to: Control How Much Related Data Is Retrieved</span></span>

<span data-ttu-id="9bc34-104">Используйте метод <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>, чтобы указать, какие данные, связанные с основными целевыми объектами, должны быть одновременно извлечены.</span><span class="sxs-lookup"><span data-stu-id="9bc34-104">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="9bc34-105">Например, если известно, что понадобятся сведения о заказах клиентов, можно использовать метод <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>, чтобы гарантировать извлечение данных о заказах одновременно с извлечением с данных о клиентах.</span><span class="sxs-lookup"><span data-stu-id="9bc34-105">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="9bc34-106">Благодаря такому подходу для получения обоих наборов сведений требуется одно обращение к базе данных.</span><span class="sxs-lookup"><span data-stu-id="9bc34-106">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9bc34-107">Данные, связанные с основными целевыми объектами запроса, можно извлекать посредством извлечения перекрестного произведения объектов в виде одной большой проекции, как, например, в случае извлечения заказов одновременно с извлечением клиентов.</span><span class="sxs-lookup"><span data-stu-id="9bc34-107">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="9bc34-108">Однако такой подход имеет свои недостатки.</span><span class="sxs-lookup"><span data-stu-id="9bc34-108">But this approach often has disadvantages.</span></span> <span data-ttu-id="9bc34-109">Например, результаты являются всего лишь проекциями, а не сущностями, которые могут быть изменены и сохранены технологией [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bc34-109">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="9bc34-110">Кроме того, может извлекаться большой объем ненужных данных.</span><span class="sxs-lookup"><span data-stu-id="9bc34-110">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc34-111">Пример</span><span class="sxs-lookup"><span data-stu-id="9bc34-111">Example</span></span>  

 <span data-ttu-id="9bc34-112">В следующем примере при выполнении запроса извлекаются все заказы (`Orders`) для всех клиентов (`Customers`), расположенных в Лондоне.</span><span class="sxs-lookup"><span data-stu-id="9bc34-112">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="9bc34-113">В результате, при последующем доступе к свойству `Orders` объекта `Customer` не инициируется новый запрос базы данных.</span><span class="sxs-lookup"><span data-stu-id="9bc34-113">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9bc34-114">См. также</span><span class="sxs-lookup"><span data-stu-id="9bc34-114">See also</span></span>

- [<span data-ttu-id="9bc34-115">Запрос к базе данных</span><span class="sxs-lookup"><span data-stu-id="9bc34-115">Querying the Database</span></span>](querying-the-database.md)
