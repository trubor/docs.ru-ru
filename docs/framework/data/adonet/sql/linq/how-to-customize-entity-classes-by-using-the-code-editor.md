---
description: Дополнительные сведения см. в статье как настроить классы сущностей с помощью редактора кода.
title: Практическое руководство. Как настроить классы сущностей с помощью редактора кода
ms.date: 03/30/2017
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
ms.openlocfilehash: 6b4e8b5dcd5cb11095667fe95293a376cc63ade8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738992"
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="9ce49-103">Практическое руководство. Как настроить классы сущностей с помощью редактора кода</span><span class="sxs-lookup"><span data-stu-id="9ce49-103">How to: Customize Entity Classes by Using the Code Editor</span></span>

<span data-ttu-id="9ce49-104">Разработчики, использующие Visual Studio, могут использовать реляционный конструктор объектов для создания или настройки классов сущностей.</span><span class="sxs-lookup"><span data-stu-id="9ce49-104">Developers using Visual Studio can use the Object Relational Designer to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="9ce49-105">Можно также использовать редактор кода Visual Studio для написания собственного кода сопоставления или для настройки уже созданного кода.</span><span class="sxs-lookup"><span data-stu-id="9ce49-105">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="9ce49-106">Дополнительные сведения см. в разделе [сопоставление на основе атрибутов](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="9ce49-106">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="9ce49-107">В подразделах данного раздела описаны способы настройки объектной модели.</span><span class="sxs-lookup"><span data-stu-id="9ce49-107">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="9ce49-108">Практическое руководство. Как указывать имена баз данных</span><span class="sxs-lookup"><span data-stu-id="9ce49-108">How to: Specify Database Names</span></span>](how-to-specify-database-names.md)  
 <span data-ttu-id="9ce49-109">Описание использования <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-109">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="9ce49-110">Практическое руководство. Как представить таблицы в виде классов</span><span class="sxs-lookup"><span data-stu-id="9ce49-110">How to: Represent Tables as Classes</span></span>](how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="9ce49-111">Описание использования <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-111">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="9ce49-112">Практическое руководство. Как представить столбцы в виде членов класса</span><span class="sxs-lookup"><span data-stu-id="9ce49-112">How to: Represent Columns as Class Members</span></span>](how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="9ce49-113">Описание использования <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-113">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="9ce49-114">Практическое руководство. Как представить первичные ключи</span><span class="sxs-lookup"><span data-stu-id="9ce49-114">How to: Represent Primary Keys</span></span>](how-to-represent-primary-keys.md)  
 <span data-ttu-id="9ce49-115">Описание использования <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-115">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="9ce49-116">Практическое руководство. Как сопоставлять связи баз данных</span><span class="sxs-lookup"><span data-stu-id="9ce49-116">How to: Map Database Relationships</span></span>](how-to-map-database-relationships.md)  
 <span data-ttu-id="9ce49-117">Содержатся примеры использования атрибута <xref:System.Data.Linq.Mapping.AssociationAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-117">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="9ce49-118">Практическое руководство. Как представить столбцы как сформированные базой данных</span><span class="sxs-lookup"><span data-stu-id="9ce49-118">How to: Represent Columns as Database-Generated</span></span>](how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="9ce49-119">Описание использования <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-119">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="9ce49-120">Практическое руководство. Как представить столбцы как столбцы отметки времени или версии</span><span class="sxs-lookup"><span data-stu-id="9ce49-120">How to: Represent Columns as Timestamp or Version Columns</span></span>](how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="9ce49-121">Описание использования <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-121">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="9ce49-122">Практическое руководство. Как указать типы данных базы данных</span><span class="sxs-lookup"><span data-stu-id="9ce49-122">How to: Specify Database Data Types</span></span>](how-to-specify-database-data-types.md)  
 <span data-ttu-id="9ce49-123">Описание использования <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-123">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="9ce49-124">Практическое руководство. Как представить вычисляемые столбцы</span><span class="sxs-lookup"><span data-stu-id="9ce49-124">How to: Represent Computed Columns</span></span>](how-to-represent-computed-columns.md)  
 <span data-ttu-id="9ce49-125">Описание использования <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-125">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="9ce49-126">Практическое руководство. Как указать поля закрытого хранения</span><span class="sxs-lookup"><span data-stu-id="9ce49-126">How to: Specify Private Storage Fields</span></span>](how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="9ce49-127">Описание использования <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-127">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="9ce49-128">Практическое руководство. Как представлять столбцы, допускающие значения NULL</span><span class="sxs-lookup"><span data-stu-id="9ce49-128">How to: Represent Columns as Allowing Null Values</span></span>](how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="9ce49-129">Описание использования <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-129">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="9ce49-130">Практическое руководство. Как сопоставить иерархии наследования</span><span class="sxs-lookup"><span data-stu-id="9ce49-130">How to: Map Inheritance Hierarchies</span></span>](how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="9ce49-131">Описываются сопоставления, необходимые для определения иерархии наследования.</span><span class="sxs-lookup"><span data-stu-id="9ce49-131">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="9ce49-132">Практическое руководство. Как организовать проверку наличия конфликтов параллелизма</span><span class="sxs-lookup"><span data-stu-id="9ce49-132">How to: Specify Concurrency-Conflict Checking</span></span>](how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="9ce49-133">Описание использования <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ce49-133">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce49-134">См. также</span><span class="sxs-lookup"><span data-stu-id="9ce49-134">See also</span></span>

- [<span data-ttu-id="9ce49-135">SqlMetal.exe (средство создания кода)</span><span class="sxs-lookup"><span data-stu-id="9ce49-135">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
