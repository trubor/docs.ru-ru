---
description: Дополнительные сведения см. в статье как указать типы данных базы данных
title: Практическое руководство. Как указать типы данных базы данных
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 004a16fe9dd0cda608485b13b03ce922d6a9f671
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785917"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="f9df1-103">Практическое руководство. Как указать типы данных базы данных</span><span class="sxs-lookup"><span data-stu-id="f9df1-103">How to: Specify Database Data Types</span></span>

<span data-ttu-id="f9df1-104">Используйте [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> свойство <xref:System.Data.Linq.Mapping.ColumnAttribute> атрибута, чтобы указать точный текст, определяющий столбец в объявлении таблицы T-SQL.</span><span class="sxs-lookup"><span data-stu-id="f9df1-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="f9df1-105">Свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> следует задавать, только если для создания экземпляра базы данных планируется использовать <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9df1-105">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="f9df1-106">Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9df1-106">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="f9df1-107">Задание текста для определения типа данных в таблице T-SQL</span><span class="sxs-lookup"><span data-stu-id="f9df1-107">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="f9df1-108">Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f9df1-108">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="f9df1-109">В качестве значения свойства <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> укажите точный текст, используемый T-SQL.</span><span class="sxs-lookup"><span data-stu-id="f9df1-109">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9df1-110">См. также</span><span class="sxs-lookup"><span data-stu-id="f9df1-110">See also</span></span>

- [<span data-ttu-id="f9df1-111">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f9df1-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="f9df1-112">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="f9df1-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
