---
description: Дополнительные сведения см. в статье как представить столбцы как столбцы меток времени или версий.
title: Практическое руководство. Как представить столбцы как столбцы отметки времени или версии
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 042e6a62c66b3f1ef522453157560e5e4c0f7de6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712510"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="e6e88-103">Практическое руководство. Как представить столбцы как столбцы отметки времени или версии</span><span class="sxs-lookup"><span data-stu-id="e6e88-103">How to: Represent Columns as Timestamp or Version Columns</span></span>

<span data-ttu-id="e6e88-104">Используйте [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> свойство <xref:System.Data.Linq.Mapping.ColumnAttribute> атрибута для обозначения поля или свойства, представляющего столбец базы данных, который содержит метки времени базы данных или номера версий.</span><span class="sxs-lookup"><span data-stu-id="e6e88-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="e6e88-105">Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6e88-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="e6e88-106">Назначение поля или свойства, представляющего столбец версии или отметки времени</span><span class="sxs-lookup"><span data-stu-id="e6e88-106">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="e6e88-107">Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e6e88-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="e6e88-108">Задайте свойству <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="e6e88-108">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e88-109">См. также</span><span class="sxs-lookup"><span data-stu-id="e6e88-109">See also</span></span>

- [<span data-ttu-id="e6e88-110">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e6e88-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="e6e88-111">Практическое руководство. Как указать, для каких элементов тестируется возникновение конфликтов параллелизма</span><span class="sxs-lookup"><span data-stu-id="e6e88-111">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="e6e88-112">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="e6e88-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
