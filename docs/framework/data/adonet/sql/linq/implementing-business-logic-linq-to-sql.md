---
description: 'Дополнительные сведения: реализация бизнес-логики (LINQ to SQL)'
title: Реализация бизнес-логики (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3f2b7085db3832f37da7520c8f75b6bc120125f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803884"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="6aaeb-103">Реализация бизнес-логики (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="6aaeb-103">Implementing Business Logic (LINQ to SQL)</span></span>

<span data-ttu-id="6aaeb-104">Термин "бизнес-логика" в данном разделе относится к любым пользовательским правилам или проверкам, которые применяются к данным перед их вставкой, обновлением или удалением в базе данных.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-104">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="6aaeb-105">Бизнес-логику также иногда называют терминами "бизнес-правила" или "логика домена".</span><span class="sxs-lookup"><span data-stu-id="6aaeb-105">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="6aaeb-106">В многоуровневых приложениях бизнес-логика реализуется в виде логического уровня, и ее можно изменять независимо от уровня представления данных или уровня доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-106">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="6aaeb-107">Бизнес-логика может вызываться уровнем доступа к данным перед обновлением, вставкой или удалением данных в базе данных или после выполнения этих операций.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-107">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="6aaeb-108">Бизнес-логика может представлять собой простую схему проверки совместимости типа поля с типом столбца таблицы.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-108">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="6aaeb-109">Она также может состоять из набора объектов, взаимодействующих произвольным и довольно сложным образом.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-109">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="6aaeb-110">Правила могут реализовываться в виде хранимых процедур для базы данных или в качестве объектов, содержащихся в памяти.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-110">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="6aaeb-111">Однако реализация бизнес-логики [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] позволяет использовать разделяемые классы и разделяемые методы для отделения бизнес-логики от кода доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-111">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="6aaeb-112">Способы вызова бизнес-логики технологией LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6aaeb-112">How LINQ to SQL Invokes Your Business Logic</span></span>  

 <span data-ttu-id="6aaeb-113">При создании класса сущности во время разработки либо вручную, либо с помощью реляционный конструктор объектов или SQLMetal он определяется как разделяемый класс.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-113">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="6aaeb-114">Это означает, что в отдельном файле с исходным кодом можно определить другую часть этого класса сущностей, содержащего пользовательскую бизнес-логику.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-114">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="6aaeb-115">Во время компиляции обе части объединяются в один класс.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-115">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="6aaeb-116">Но если вы хотите повторно создать классы сущностей с помощью реляционный конструктор объектов или SQLMetal, это можно сделать, и ваша часть класса не будет изменена.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-116">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="6aaeb-117">Разделяемые классы, которые определяют сущности, и класс <xref:System.Data.Linq.DataContext> содержат разделяемые методы.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-117">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="6aaeb-118">Эти методы являются точками расширения, которые можно использовать для применения бизнес-логики перед обновлением, вставкой или удалением сущности или свойства сущности, а также после выполнения этих операций.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-118">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="6aaeb-119">Разделяемые методы можно рассматривать как события времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-119">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="6aaeb-120">Генератор кода определяет сигнатуру метода и вызывает эти методы в методах доступа к свойствам "get" и "set", конструкторе `DataContext` и в некоторых случаях неявным образом при вызове метода <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-120">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="6aaeb-121">Однако, если не реализовать определенный разделяемый метод, все ссылки на него и определение удаляются во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-121">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="6aaeb-122">В определении реализации, созданном в отдельном файле с исходным кодом, можно выполнить любую требуемую пользовательскую логику.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-122">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="6aaeb-123">Можно использовать разделяемый класс в качестве уровня домена или вызывать его из определения реализации разделяемого метода в отдельном объекте или объектах.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-123">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="6aaeb-124">В любом случае бизнес-логика полностью отделена как от кода уровня доступа к данным, так и от кода уровня представления данных.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-124">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="6aaeb-125">Более подробное рассмотрение точек расширения</span><span class="sxs-lookup"><span data-stu-id="6aaeb-125">A Closer Look at the Extensibility Points</span></span>  

 <span data-ttu-id="6aaeb-126">В следующем примере показана часть кода, созданного реляционный конструктор объектов для `DataContext` класса, который имеет две таблицы: `Customers` и `Orders` .</span><span class="sxs-lookup"><span data-stu-id="6aaeb-126">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="6aaeb-127">Обратите внимание, что методы "Insert", "Update" и "Delete" определены для каждой таблицы в классе.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-127">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 <span data-ttu-id="6aaeb-128">Если реализовать методы "Insert", "Update" и "Delete" в разделяемом классе, то при вызове метода [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] среда выполнения <xref:System.Data.Linq.DataContext.SubmitChanges%2A> вызовет их вместо собственных методов, используемых по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-128">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="6aaeb-129">Это позволяет переопределить поведение, реализуемое по умолчанию для операций создания, чтения, обновления и удаления.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-129">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="6aaeb-130">Дополнительные сведения см. [в разделе Пошаговое руководство. Настройка поведения при вставке, обновлении и удалении классов сущностей](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="6aaeb-130">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="6aaeb-131">Метод `OnCreated` вызывается в классе конструктора.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-131">The `OnCreated` method is called in the class constructor.</span></span>  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 <span data-ttu-id="6aaeb-132">Классы сущностей имеют три метода, вызываемые средой выполнения [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] при создании, загрузке и проверки сущности (при вызове метода `SubmitChanges`).</span><span class="sxs-lookup"><span data-stu-id="6aaeb-132">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="6aaeb-133">Классы сущностей также имеют два разделяемых метода для каждого свойства. Один метод вызывается перед заданием свойства, а другой — после.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-133">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="6aaeb-134">В следующем примере кода демонстрируются некоторые методы, созданные для класса `Customer`.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-134">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 <span data-ttu-id="6aaeb-135">Эти методы вызывается в методе доступа "set" для свойства, как показано в следующем примере для свойства `CustomerID`:</span><span class="sxs-lookup"><span data-stu-id="6aaeb-135">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 <span data-ttu-id="6aaeb-136">В пользовательской части класса создается определение реализации метода.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-136">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="6aaeb-137">В Visual Studio после ввода `partial` вы увидите IntelliSense для определений методов в другой части класса.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-137">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 <span data-ttu-id="6aaeb-138">Дополнительные сведения о добавлении бизнес-логики в приложение с помощью разделяемых методов см. в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="6aaeb-138">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="6aaeb-139">Практическое руководство. Добавление проверки в классы сущностей</span><span class="sxs-lookup"><span data-stu-id="6aaeb-139">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="6aaeb-140">Пошаговое руководство. Настройка поведения вставки, обновления и удаления классов сущностей</span><span class="sxs-lookup"><span data-stu-id="6aaeb-140">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="6aaeb-141">[Пошаговое руководство. Добавление проверки к классам сущностей](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6aaeb-141">[Walkthrough: Adding Validation to Entity Classes](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aaeb-142">См. также</span><span class="sxs-lookup"><span data-stu-id="6aaeb-142">See also</span></span>

- [<span data-ttu-id="6aaeb-143">Разделяемые классы и методы</span><span class="sxs-lookup"><span data-stu-id="6aaeb-143">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="6aaeb-144">Разделяемые методы</span><span class="sxs-lookup"><span data-stu-id="6aaeb-144">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="6aaeb-145">Средства LINQ to SQL в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6aaeb-145">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="6aaeb-146">SqlMetal.exe (средство создания кода)</span><span class="sxs-lookup"><span data-stu-id="6aaeb-146">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
