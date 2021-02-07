---
description: Дополнительные сведения см. в статье как представить столбцы как Database-Generated
title: Практическое руководство. Как представить столбцы как сформированные базой данных
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 01828ef3f73257d20023168f0ea471ee7e3863c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695636"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="447d0-103">Практическое руководство. Как представить столбцы как сформированные базой данных</span><span class="sxs-lookup"><span data-stu-id="447d0-103">How to: Represent Columns as Database-Generated</span></span>

<span data-ttu-id="447d0-104">Используйте [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> свойство <xref:System.Data.Linq.Mapping.ColumnAttribute> атрибута для обозначения поля или свойства, представляющего столбец, сформированный базой данных.</span><span class="sxs-lookup"><span data-stu-id="447d0-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="447d0-105">Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="447d0-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="447d0-106">Назначение поля или свойства, представляющего столбец, созданный базой данных</span><span class="sxs-lookup"><span data-stu-id="447d0-106">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="447d0-107">Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="447d0-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="447d0-108">В качестве значения свойства задайте `true`.</span><span class="sxs-lookup"><span data-stu-id="447d0-108">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="447d0-109">См. также</span><span class="sxs-lookup"><span data-stu-id="447d0-109">See also</span></span>

- [<span data-ttu-id="447d0-110">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="447d0-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="447d0-111">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="447d0-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
