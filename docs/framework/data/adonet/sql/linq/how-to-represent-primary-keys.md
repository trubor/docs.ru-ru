---
description: Дополнительные сведения о том, как представлять первичные ключи.
title: Практическое руководство. Как представить первичные ключи
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 1fbac2d60bd730718b5330bfd48910a61deae15c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723612"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="b44f6-103">Практическое руководство. Как представить первичные ключи</span><span class="sxs-lookup"><span data-stu-id="b44f6-103">How to: Represent Primary Keys</span></span>

<span data-ttu-id="b44f6-104">Используйте [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> свойство <xref:System.Data.Linq.Mapping.ColumnAttribute> атрибута, чтобы назначить свойство или поле для представления первичного ключа столбца базы данных.</span><span class="sxs-lookup"><span data-stu-id="b44f6-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="b44f6-105">Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="b44f6-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b44f6-106">не поддерживает вычисляемые столбцы в качестве первичных ключей.</span><span class="sxs-lookup"><span data-stu-id="b44f6-106">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="b44f6-107">Назначение свойства или поля в качестве первичного ключа</span><span class="sxs-lookup"><span data-stu-id="b44f6-107">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="b44f6-108">Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b44f6-108">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="b44f6-109">В качестве значения задайте `true`.</span><span class="sxs-lookup"><span data-stu-id="b44f6-109">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44f6-110">См. также</span><span class="sxs-lookup"><span data-stu-id="b44f6-110">See also</span></span>

- [<span data-ttu-id="b44f6-111">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b44f6-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b44f6-112">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="b44f6-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
