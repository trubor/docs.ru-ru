---
description: Дополнительные сведения см. в LINQ to SQL объектной модели
title: Модель объектов LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: be4021019d09d1479364b25268eefda50b6eaa6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681270"
---
# <a name="the-linq-to-sql-object-model"></a><span data-ttu-id="3cbc9-103">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3cbc9-103">The LINQ to SQL Object Model</span></span>

<span data-ttu-id="3cbc9-104">В службах [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] объектная модель, выраженная в языке программирования разработчика, сопоставляется с моделью данных реляционной базы данных.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model expressed in the programming language of the developer is mapped to the data model of a relational database.</span></span> <span data-ttu-id="3cbc9-105">После этого операции с данными выполняются в соответствии с объектной моделью.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-105">Operations on the data are then conducted according to the object model.</span></span>  
  
 <span data-ttu-id="3cbc9-106">В данном сценарии команды базы данных (например, `INSERT`) не выполняются в базе данных.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-106">In this scenario, you do not issue database commands (for example, `INSERT`) to the database.</span></span> <span data-ttu-id="3cbc9-107">Вместо этого изменение значений и выполнение методов происходит в рамках объектной модели.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-107">Instead, you change values and execute methods within your object model.</span></span> <span data-ttu-id="3cbc9-108">Если необходимо отправить запрос к базе данных или передать изменения, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] преобразует требования в корректные команды SQL и отправляет эти команды в базу данных.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-108">When you want to query the database or send it changes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your requests into the correct SQL commands and sends those commands to the database.</span></span>  
  
 ![Снимок экрана, на котором показана объектная модель LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="3cbc9-110">Наиболее фундаментальные элементы в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] объектной модели и их связи с элементами в реляционной модели данных приведены в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="3cbc9-110">The most fundamental elements in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model and their relationship to elements in the relational data model are summarized in the following table:</span></span>  
  
|<span data-ttu-id="3cbc9-111">Объектная модель LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3cbc9-111">LINQ to SQL Object Model</span></span>|<span data-ttu-id="3cbc9-112">Реляционная модель данных</span><span class="sxs-lookup"><span data-stu-id="3cbc9-112">Relational Data Model</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="3cbc9-113">Класс сущностей</span><span class="sxs-lookup"><span data-stu-id="3cbc9-113">Entity class</span></span>|<span data-ttu-id="3cbc9-114">Таблица</span><span class="sxs-lookup"><span data-stu-id="3cbc9-114">Table</span></span>|  
|<span data-ttu-id="3cbc9-115">Член класса</span><span class="sxs-lookup"><span data-stu-id="3cbc9-115">Class member</span></span>|<span data-ttu-id="3cbc9-116">Столбец</span><span class="sxs-lookup"><span data-stu-id="3cbc9-116">Column</span></span>|  
|<span data-ttu-id="3cbc9-117">Взаимосвязь</span><span class="sxs-lookup"><span data-stu-id="3cbc9-117">Association</span></span>|<span data-ttu-id="3cbc9-118">Отношение внешнего ключа</span><span class="sxs-lookup"><span data-stu-id="3cbc9-118">Foreign-key relationship</span></span>|  
|<span data-ttu-id="3cbc9-119">Метод</span><span class="sxs-lookup"><span data-stu-id="3cbc9-119">Method</span></span>|<span data-ttu-id="3cbc9-120">Хранимая процедура или функция</span><span class="sxs-lookup"><span data-stu-id="3cbc9-120">Stored Procedure or Function</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3cbc9-121">Следующие сведения подразумевают наличие базовых знаний о реляционной модели данных и правилах.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-121">The following descriptions assume that you have a basic knowledge of the relational data model and rules.</span></span>  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a><span data-ttu-id="3cbc9-122">Таблицы классов сущностей и баз данных LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3cbc9-122">LINQ to SQL Entity Classes and Database Tables</span></span>  

 <span data-ttu-id="3cbc9-123">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] таблица базы данных представлена *классом сущностей*.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-123">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a database table is represented by an *entity class*.</span></span> <span data-ttu-id="3cbc9-124">Класс сущностей аналогичен любому другому создаваемому классу за исключением того, что для снабжения класса примечаниями используются специальные данные, связывающие его с таблицей базы данных.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-124">An entity class is like any other class you might create except that you annotate the class by using special information that associates the class with a database table.</span></span> <span data-ttu-id="3cbc9-125">Для этого к объявлению класса добавляется пользовательский атрибут (<xref:System.Data.Linq.Mapping.TableAttribute>), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-125">You make this annotation by adding a custom attribute (<xref:System.Data.Linq.Mapping.TableAttribute>) to your class declaration, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cbc9-126">Пример</span><span class="sxs-lookup"><span data-stu-id="3cbc9-126">Example</span></span>  

 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 <span data-ttu-id="3cbc9-127">В базе данных могут быть сохранены только экземпляры классов, объявленные как таблицы (то есть классы сущностей).</span><span class="sxs-lookup"><span data-stu-id="3cbc9-127">Only instances of classes declared as tables (that is, entity classes) can be saved to the database.</span></span>  
  
 <span data-ttu-id="3cbc9-128">Дополнительные сведения см. в разделе табличный атрибут в [сопоставлении на основе атрибутов](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3cbc9-128">For more information, see the Table Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a><span data-ttu-id="3cbc9-129">Столбцы членов класса и базы данных LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3cbc9-129">LINQ to SQL Class Members and Database Columns</span></span>  

 <span data-ttu-id="3cbc9-130">Кроме связывания классов с таблицами, можно назначить поля или свойства для представления столбцов базы данных.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-130">In addition to associating classes with tables, you designate fields or properties to represent database columns.</span></span> <span data-ttu-id="3cbc9-131">Для этого [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] определяет атрибут <xref:System.Data.Linq.Mapping.ColumnAttribute>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-131">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] defines the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cbc9-132">Пример</span><span class="sxs-lookup"><span data-stu-id="3cbc9-132">Example</span></span>  

 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 <span data-ttu-id="3cbc9-133">В базе данных сохраняются или из нее извлекаются только те поля и свойства, которые сопоставлены столбцам.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-133">Only fields and properties mapped to columns are persisted to or retrieved from the database.</span></span> <span data-ttu-id="3cbc9-134">Поля и свойства, не объявленные в качестве столбцов, считаются временными частями логики приложения.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-134">Those not declared as columns are considered as transient parts of your application logic.</span></span>  
  
 <span data-ttu-id="3cbc9-135">Атрибут <xref:System.Data.Linq.Mapping.ColumnAttribute> имеет целый ряд свойств, которые можно использовать для настройки членов, представляющих столбцы (например, назначение члена, представляющего столбец первичного ключа).</span><span class="sxs-lookup"><span data-stu-id="3cbc9-135">The <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute has a variety of properties that you can use to customize these members that represent columns (for example, designating a member as representing a primary key column).</span></span> <span data-ttu-id="3cbc9-136">Дополнительные сведения см. в разделе атрибут столбца в [сопоставлении на основе атрибутов](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3cbc9-136">For more information, see the Column Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a><span data-ttu-id="3cbc9-137">Связи и отношения внешнего ключа баз данных LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3cbc9-137">LINQ to SQL Associations and Database Foreign-key Relationships</span></span>  

 <span data-ttu-id="3cbc9-138">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] можно представить ассоциации базы данных (например, связи внешнего ключа с первичным ключом), применяя <xref:System.Data.Linq.Mapping.AssociationAttribute> атрибут.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-138">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you represent database associations (such as foreign-key to primary-key relationships) by applying the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="3cbc9-139">В следующем сегменте кода `Order` класс содержит `Customer` свойство с <xref:System.Data.Linq.Mapping.AssociationAttribute> атрибутом.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-139">In the following segment of code, the `Order` class contains a `Customer` property that has an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="3cbc9-140">Это свойство и его атрибут предоставляют класс `Order` с отношением для класса `Customer`.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-140">This property and its attribute provide the `Order` class with a relationship to the `Customer` class.</span></span>  
  
 <span data-ttu-id="3cbc9-141">В следующем примере кода представлено свойство `Customer` из класса `Order`.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-141">The following code example shows the `Customer` property from the `Order` class.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cbc9-142">Пример</span><span class="sxs-lookup"><span data-stu-id="3cbc9-142">Example</span></span>  

 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 <span data-ttu-id="3cbc9-143">Дополнительные сведения см. в разделе Атрибут Association в [сопоставлении на основе атрибутов](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3cbc9-143">For more information, see the Association Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a><span data-ttu-id="3cbc9-144">Хранимые процедуры методов и баз данных LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-144">LINQ to SQL Methods and Database Stored Procedures</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3cbc9-145">поддерживает хранимые процедуры и пользовательские функции.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-145">supports stored procedures and user-defined functions.</span></span> <span data-ttu-id="3cbc9-146">В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] эти абстракции, определенные в базе данных, сопоставляются с клиентскими объектами, что позволяет обращаться к ним строго типизированным способом из клиентского кода.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-146">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you map these database-defined abstractions to client objects so that you can access them in a strongly typed manner from client code.</span></span> <span data-ttu-id="3cbc9-147">Подписи методов очень схожи с сигнатурами процедур и функций, определенных в базе данных.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-147">The method signatures resemble as closely as possible the signatures of the procedures and functions defined in the database.</span></span> <span data-ttu-id="3cbc9-148">Для определения этих методов можно использовать IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-148">You can use IntelliSense to discover these methods.</span></span>  
  
 <span data-ttu-id="3cbc9-149">В качестве набора результатов, возвращенного вызовом сопоставленной процедуры, выступает строго типизированная коллекция.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-149">A result set that is returned by a call to a mapped procedure is a strongly typed collection.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3cbc9-150">сопоставляет хранимые процедуры и функции с методами с помощью атрибутов <xref:System.Data.Linq.Mapping.FunctionAttribute> и <xref:System.Data.Linq.Mapping.ParameterAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-150">maps stored procedures and functions to methods by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> and <xref:System.Data.Linq.Mapping.ParameterAttribute> attributes.</span></span> <span data-ttu-id="3cbc9-151">Методы, представляющие хранимые процедуры, отличаются от методов, представляющих пользовательские функции, свойством <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-151">Methods representing stored procedures are distinguished from those representing user-defined functions by the <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> property.</span></span> <span data-ttu-id="3cbc9-152">Если данное свойство имеет значение `false` (значение по умолчанию), значит метод представляет хранимую процедуру.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-152">If this property is set to `false` (the default), the method represents a stored procedure.</span></span> <span data-ttu-id="3cbc9-153">Если свойству задано значение `true`, метод представляет функцию базы данных.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-153">If it is set to `true`, the method represents a database function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cbc9-154">При использовании Visual Studio можно использовать реляционный конструктор объектов для создания методов, сопоставленных с хранимыми процедурами и определяемыми пользователем функциями.</span><span class="sxs-lookup"><span data-stu-id="3cbc9-154">If you are using Visual Studio, you can use the Object Relational Designer to create methods mapped to stored procedures and user-defined functions.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cbc9-155">Пример</span><span class="sxs-lookup"><span data-stu-id="3cbc9-155">Example</span></span>  

 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 <span data-ttu-id="3cbc9-156">Дополнительные сведения см. в разделах атрибут функции, атрибут хранимой процедуры и атрибуты параметра в [сопоставлении на основе атрибутов](attribute-based-mapping.md) и [хранимых процедурах](stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3cbc9-156">For more information, see the Function Attribute, Stored Procedure Attribute, and Parameter Attribute sections of [Attribute-Based Mapping](attribute-based-mapping.md) and [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cbc9-157">См. также</span><span class="sxs-lookup"><span data-stu-id="3cbc9-157">See also</span></span>

- [<span data-ttu-id="3cbc9-158">Сопоставление, основанное на атрибутах</span><span class="sxs-lookup"><span data-stu-id="3cbc9-158">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="3cbc9-159">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="3cbc9-159">Background Information</span></span>](background-information.md)
