---
description: 'Дополнительные сведения о: Аннотирование типизированных наборов данных'
title: Создание примечаний к типизированным наборам данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 6f5838e94d88fd6c9b3a1991d4c8023d5892b784
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739707"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="15a2b-103">Создание примечаний к типизированным наборам данных</span><span class="sxs-lookup"><span data-stu-id="15a2b-103">Annotating Typed DataSets</span></span>

<span data-ttu-id="15a2b-104">Заметки дают возможность изменять имена элементов в типизированных <xref:System.Data.DataSet> без изменения базовой схемы.</span><span class="sxs-lookup"><span data-stu-id="15a2b-104">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="15a2b-105">Изменение имен элементов в базовой схеме приведет к тому, что типизированный **набор данных** будет ссылаться на объекты, не существующие в источнике данных, а также будет потеряна ссылка на объекты, существующие в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="15a2b-105">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="15a2b-106">С помощью заметок можно настроить имена объектов в типизированном **наборе данных** с более информативными именами, сделать код более удобочитаемым, а типизированный **набор данных** проще использовать для использования клиентами, при этом не изменяя базовую схему.</span><span class="sxs-lookup"><span data-stu-id="15a2b-106">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="15a2b-107">Например, следующий элемент схемы для таблицы **Customers** базы данных **Northwind** приведет к появлению имени объекта **DataRow** **кустомерсров** и <xref:System.Data.DataRowCollection> именованных **клиентов**.</span><span class="sxs-lookup"><span data-stu-id="15a2b-107">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="15a2b-108">**Датаровколлектион** имя **клиентов** имеет смысл в клиентском коде, но имя **DataRow** **кустомерсров** является ошибочным, поскольку является одним объектом.</span><span class="sxs-lookup"><span data-stu-id="15a2b-108">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="15a2b-109">Кроме того, в обычных сценариях объект будет называться без идентификатора **строки** , а вместо этого будет просто называться объектом **Customer** .</span><span class="sxs-lookup"><span data-stu-id="15a2b-109">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="15a2b-110">Решение заключается в создании заметка схемы и определении новых имен для объектов **DataRow** и **датаровколлектион** .</span><span class="sxs-lookup"><span data-stu-id="15a2b-110">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="15a2b-111">Далее приводится версия предыдущей схемы с добавленными заметками.</span><span class="sxs-lookup"><span data-stu-id="15a2b-111">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="15a2b-112">При указании значения **типеднаме** для **Customer** будет выдаваться имя объекта **DataRow** **Customer**.</span><span class="sxs-lookup"><span data-stu-id="15a2b-112">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="15a2b-113">Указание значения **типедплурал** для **клиентов** сохраняет имя **датаровколлектион** **клиентов**.</span><span class="sxs-lookup"><span data-stu-id="15a2b-113">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="15a2b-114">В следующей таблице показаны доступные для использования заметки.</span><span class="sxs-lookup"><span data-stu-id="15a2b-114">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="15a2b-115">Annotation</span><span class="sxs-lookup"><span data-stu-id="15a2b-115">Annotation</span></span>|<span data-ttu-id="15a2b-116">Описание</span><span class="sxs-lookup"><span data-stu-id="15a2b-116">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="15a2b-117">**typedName**</span><span class="sxs-lookup"><span data-stu-id="15a2b-117">**typedName**</span></span>|<span data-ttu-id="15a2b-118">Имя объекта.</span><span class="sxs-lookup"><span data-stu-id="15a2b-118">Name of the object.</span></span>|  
|<span data-ttu-id="15a2b-119">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="15a2b-119">**typedPlural**</span></span>|<span data-ttu-id="15a2b-120">Имя коллекции объектов.</span><span class="sxs-lookup"><span data-stu-id="15a2b-120">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="15a2b-121">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="15a2b-121">**typedParent**</span></span>|<span data-ttu-id="15a2b-122">Имя объекта при ссылке на родительскую связь.</span><span class="sxs-lookup"><span data-stu-id="15a2b-122">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="15a2b-123">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="15a2b-123">**typedChildren**</span></span>|<span data-ttu-id="15a2b-124">Имя метода, возвращающего объекты по дочерней связи.</span><span class="sxs-lookup"><span data-stu-id="15a2b-124">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="15a2b-125">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="15a2b-125">**nullValue**</span></span>|<span data-ttu-id="15a2b-126">Значение, если базовое значение равно **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="15a2b-126">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="15a2b-127">См. следующую таблицу для **NullValue** Annotations.</span><span class="sxs-lookup"><span data-stu-id="15a2b-127">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="15a2b-128">Значение по умолчанию — **_throw**.</span><span class="sxs-lookup"><span data-stu-id="15a2b-128">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="15a2b-129">В следующей таблице приведены значения, которые можно указать для аннотации **NullValue** .</span><span class="sxs-lookup"><span data-stu-id="15a2b-129">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="15a2b-130">Значение nullValue</span><span class="sxs-lookup"><span data-stu-id="15a2b-130">nullValue Value</span></span>|<span data-ttu-id="15a2b-131">Описание</span><span class="sxs-lookup"><span data-stu-id="15a2b-131">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="15a2b-132">*Заменяющее значение*</span><span class="sxs-lookup"><span data-stu-id="15a2b-132">*Replacement Value*</span></span>|<span data-ttu-id="15a2b-133">Задает возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="15a2b-133">Specify a value to be returned.</span></span> <span data-ttu-id="15a2b-134">Возвращаемое значение должно соответствовать типу элемента.</span><span class="sxs-lookup"><span data-stu-id="15a2b-134">The returned value must match the type of the element.</span></span> <span data-ttu-id="15a2b-135">Например, чтобы для целочисленных полей вместо null возвращался 0, используйте `nullValue="0"`.</span><span class="sxs-lookup"><span data-stu-id="15a2b-135">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="15a2b-136">**_throw**</span><span class="sxs-lookup"><span data-stu-id="15a2b-136">**_throw**</span></span>|<span data-ttu-id="15a2b-137">Создание исключения.</span><span class="sxs-lookup"><span data-stu-id="15a2b-137">Throw an exception.</span></span> <span data-ttu-id="15a2b-138">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="15a2b-138">This is the default.</span></span>|  
|<span data-ttu-id="15a2b-139">**_null**</span><span class="sxs-lookup"><span data-stu-id="15a2b-139">**_null**</span></span>|<span data-ttu-id="15a2b-140">Возвращает ссылку null или создает исключение, если встречается примитивный тип.</span><span class="sxs-lookup"><span data-stu-id="15a2b-140">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="15a2b-141">**_empty**</span><span class="sxs-lookup"><span data-stu-id="15a2b-141">**_empty**</span></span>|<span data-ttu-id="15a2b-142">Для строк возвращает **String. Empty**, в противном случае возвращает объект, созданный из пустого конструктора.</span><span class="sxs-lookup"><span data-stu-id="15a2b-142">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="15a2b-143">Если встречается примитивный тип, вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="15a2b-143">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="15a2b-144">В следующей таблице показаны значения по умолчанию для объектов в типизированном **наборе данных** и доступных аннотациях.</span><span class="sxs-lookup"><span data-stu-id="15a2b-144">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="15a2b-145">Объект/Метод/Событие</span><span class="sxs-lookup"><span data-stu-id="15a2b-145">Object/Method/Event</span></span>|<span data-ttu-id="15a2b-146">По умолчанию</span><span class="sxs-lookup"><span data-stu-id="15a2b-146">Default</span></span>|<span data-ttu-id="15a2b-147">Annotation</span><span class="sxs-lookup"><span data-stu-id="15a2b-147">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="15a2b-148">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="15a2b-148">**DataTable**</span></span>|<span data-ttu-id="15a2b-149">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="15a2b-149">TableNameDataTable</span></span>|<span data-ttu-id="15a2b-150">typedPlural</span><span class="sxs-lookup"><span data-stu-id="15a2b-150">typedPlural</span></span>|  
|<span data-ttu-id="15a2b-151">**DataTable** Метод</span><span class="sxs-lookup"><span data-stu-id="15a2b-151">**DataTable** Methods</span></span>|<span data-ttu-id="15a2b-152">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="15a2b-152">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="15a2b-153">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="15a2b-153">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="15a2b-154">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="15a2b-154">DeleteTableNameRow</span></span>|<span data-ttu-id="15a2b-155">typedName</span><span class="sxs-lookup"><span data-stu-id="15a2b-155">typedName</span></span>|  
|<span data-ttu-id="15a2b-156">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="15a2b-156">**DataRowCollection**</span></span>|<span data-ttu-id="15a2b-157">TableName</span><span class="sxs-lookup"><span data-stu-id="15a2b-157">TableName</span></span>|<span data-ttu-id="15a2b-158">typedPlural</span><span class="sxs-lookup"><span data-stu-id="15a2b-158">typedPlural</span></span>|  
|<span data-ttu-id="15a2b-159">**Строку**</span><span class="sxs-lookup"><span data-stu-id="15a2b-159">**DataRow**</span></span>|<span data-ttu-id="15a2b-160">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="15a2b-160">TableNameRow</span></span>|<span data-ttu-id="15a2b-161">typedName</span><span class="sxs-lookup"><span data-stu-id="15a2b-161">typedName</span></span>|  
|<span data-ttu-id="15a2b-162">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="15a2b-162">**DataColumn**</span></span>|<span data-ttu-id="15a2b-163">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="15a2b-163">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="15a2b-164">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="15a2b-164">DataRow.ColumnName</span></span>|<span data-ttu-id="15a2b-165">typedName</span><span class="sxs-lookup"><span data-stu-id="15a2b-165">typedName</span></span>|  
|<span data-ttu-id="15a2b-166">**Свойство**</span><span class="sxs-lookup"><span data-stu-id="15a2b-166">**Property**</span></span>|<span data-ttu-id="15a2b-167">PropertyName</span><span class="sxs-lookup"><span data-stu-id="15a2b-167">PropertyName</span></span>|<span data-ttu-id="15a2b-168">typedName</span><span class="sxs-lookup"><span data-stu-id="15a2b-168">typedName</span></span>|  
|<span data-ttu-id="15a2b-169">**Дочерний элемент** Возмож</span><span class="sxs-lookup"><span data-stu-id="15a2b-169">**Child** Accessor</span></span>|<span data-ttu-id="15a2b-170">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="15a2b-170">GetChildTableNameRows</span></span>|<span data-ttu-id="15a2b-171">typedChildren</span><span class="sxs-lookup"><span data-stu-id="15a2b-171">typedChildren</span></span>|  
|<span data-ttu-id="15a2b-172">**Родительский элемент** Возмож</span><span class="sxs-lookup"><span data-stu-id="15a2b-172">**Parent** Accessor</span></span>|<span data-ttu-id="15a2b-173">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="15a2b-173">TableNameRow</span></span>|<span data-ttu-id="15a2b-174">typedParent</span><span class="sxs-lookup"><span data-stu-id="15a2b-174">typedParent</span></span>|  
|<span data-ttu-id="15a2b-175">**Набор данных** Событиях</span><span class="sxs-lookup"><span data-stu-id="15a2b-175">**DataSet** Events</span></span>|<span data-ttu-id="15a2b-176">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="15a2b-176">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="15a2b-177">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="15a2b-177">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="15a2b-178">typedName</span><span class="sxs-lookup"><span data-stu-id="15a2b-178">typedName</span></span>|  
  
 <span data-ttu-id="15a2b-179">Чтобы использовать зааннотации типизированного **набора данных** , необходимо включить следующую ссылку **xmlns** в схему языка определения схемы XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="15a2b-179">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="15a2b-180">Сведения о создании XSD на основе таблиц базы данных см <xref:System.Data.DataSet.WriteXmlSchema%2A> . в разделе или [Работа с DataSets в Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="15a2b-180">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="15a2b-181">Ниже приведен пример схемы с заметками, которая предоставляет таблицу **Customers** базы данных **Northwind** с отношением к включенной таблице **Orders** .</span><span class="sxs-lookup"><span data-stu-id="15a2b-181">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="15a2b-182">В следующем примере кода используется строго типизированный **набор данных** , созданный из образца схемы.</span><span class="sxs-lookup"><span data-stu-id="15a2b-182">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="15a2b-183">Он использует один из них <xref:System.Data.SqlClient.SqlDataAdapter> для заполнения таблицы **Customers** , а другой — <xref:System.Data.SqlClient.SqlDataAdapter> для заполнения таблицы **Orders** .</span><span class="sxs-lookup"><span data-stu-id="15a2b-183">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="15a2b-184">Строго типизированный **набор данных** определяет **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="15a2b-184">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="15a2b-185">См. также</span><span class="sxs-lookup"><span data-stu-id="15a2b-185">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="15a2b-186">Типизированные наборы данных</span><span class="sxs-lookup"><span data-stu-id="15a2b-186">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="15a2b-187">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="15a2b-187">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="15a2b-188">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="15a2b-188">ADO.NET Overview</span></span>](../ado-net-overview.md)
