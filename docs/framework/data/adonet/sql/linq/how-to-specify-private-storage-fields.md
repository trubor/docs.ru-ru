---
description: Дополнительные сведения см. в статье как указать закрытые поля хранилища
title: Практическое руководство. Как указать поля закрытого хранения
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: 09f3566ca85a69f27794329ae12fc45d88bb518c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785904"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="12dc0-103">Практическое руководство. Как указать поля закрытого хранения</span><span class="sxs-lookup"><span data-stu-id="12dc0-103">How to: Specify Private Storage Fields</span></span>

<span data-ttu-id="12dc0-104">Используйте [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> свойство <xref:System.Data.Linq.Mapping.DataAttribute> атрибута для обозначения имени базового поля хранилища.</span><span class="sxs-lookup"><span data-stu-id="12dc0-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="12dc0-105">Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="12dc0-105">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="12dc0-106">Задание имени базового поля хранения</span><span class="sxs-lookup"><span data-stu-id="12dc0-106">To specify the name of an underlying storage field</span></span>  
  
1. <span data-ttu-id="12dc0-107">Добавьте свойство <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="12dc0-107">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="12dc0-108">Укажите имя поля в качестве значения свойства <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="12dc0-108">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12dc0-109">См. также</span><span class="sxs-lookup"><span data-stu-id="12dc0-109">See also</span></span>

- [<span data-ttu-id="12dc0-110">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="12dc0-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="12dc0-111">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="12dc0-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
