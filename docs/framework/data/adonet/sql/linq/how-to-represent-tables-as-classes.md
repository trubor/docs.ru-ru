---
description: Дополнительные сведения см. в статье как представить таблицы как классы.
title: Практическое руководство. Как представить таблицы в виде классов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 9ec5b7309d7d10eaa6e4da6cd6fe4b1d03df1dd9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723586"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="00bd4-103">Практическое руководство. Как представить таблицы в виде классов</span><span class="sxs-lookup"><span data-stu-id="00bd4-103">How to: Represent Tables as Classes</span></span>

<span data-ttu-id="00bd4-104">Используйте [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> атрибут, чтобы назначить класс как класс сущности, связанный с таблицей базы данных.</span><span class="sxs-lookup"><span data-stu-id="00bd4-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="00bd4-105">Сопоставление класса с таблицей базы данных</span><span class="sxs-lookup"><span data-stu-id="00bd4-105">To map a class to a database table</span></span>  
  
- <span data-ttu-id="00bd4-106">Добавьте в объявление класса атрибут <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="00bd4-106">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00bd4-107">Пример</span><span class="sxs-lookup"><span data-stu-id="00bd4-107">Example</span></span>  

 <span data-ttu-id="00bd4-108">Следующий код определяет класс `Customer` как класс сущности, связанный с таблицей базы данных `Customers`.</span><span class="sxs-lookup"><span data-stu-id="00bd4-108">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="00bd4-109">Если можно определить имя, указывать свойство <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> нет необходимости.</span><span class="sxs-lookup"><span data-stu-id="00bd4-109">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="00bd4-110">Если имя не указано, оно будет считаться совпадающим с именем свойства или поля.</span><span class="sxs-lookup"><span data-stu-id="00bd4-110">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00bd4-111">См. также</span><span class="sxs-lookup"><span data-stu-id="00bd4-111">See also</span></span>

- [<span data-ttu-id="00bd4-112">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="00bd4-112">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="00bd4-113">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="00bd4-113">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
