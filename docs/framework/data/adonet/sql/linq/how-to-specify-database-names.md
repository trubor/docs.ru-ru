---
description: Дополнительные сведения см. в статье как указать имена баз данных
title: Практическое руководство. Как указывать имена баз данных
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 231c78830e009ed3414609eb6dbe05c3745f3e05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785891"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="072b4-103">Практическое руководство. Как указывать имена баз данных</span><span class="sxs-lookup"><span data-stu-id="072b4-103">How to: Specify Database Names</span></span>

<span data-ttu-id="072b4-104">Для указания имени базы данных, если это имя не предоставлено во время подключения, используется свойство <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> атрибута <xref:System.Data.Linq.Mapping.DatabaseAttribute>.</span><span class="sxs-lookup"><span data-stu-id="072b4-104">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="072b4-105">Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="072b4-105">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="072b4-106">Указание имени базы данных</span><span class="sxs-lookup"><span data-stu-id="072b4-106">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="072b4-107">Добавьте атрибут <xref:System.Data.Linq.Mapping.DatabaseAttribute> к объявлению класса для базы данных.</span><span class="sxs-lookup"><span data-stu-id="072b4-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="072b4-108">Добавьте свойство <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> атрибуту <xref:System.Data.Linq.Mapping.DatabaseAttribute>.</span><span class="sxs-lookup"><span data-stu-id="072b4-108">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="072b4-109">Установите для свойства <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> значение имени, которое необходимо указать.</span><span class="sxs-lookup"><span data-stu-id="072b4-109">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072b4-110">См. также</span><span class="sxs-lookup"><span data-stu-id="072b4-110">See also</span></span>

- [<span data-ttu-id="072b4-111">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="072b4-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="072b4-112">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="072b4-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
