---
description: 'Дополнительные сведения: ограничения схемы'
title: Ограничения схемы
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 74ddfe5b8aaf9b8193e0c0b2a929ccde333eac26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719049"
---
# <a name="schema-restrictions"></a><span data-ttu-id="e30e5-103">Ограничения схемы</span><span class="sxs-lookup"><span data-stu-id="e30e5-103">Schema Restrictions</span></span>

<span data-ttu-id="e30e5-104">Вторым необязательным параметром метода **GetSchema** являются ограничения, используемые для ограничения объема возвращаемых сведений о схеме, передаваемые методу **GetSchema** в виде массива строк.</span><span class="sxs-lookup"><span data-stu-id="e30e5-104">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="e30e5-105">Позиция в массиве определяет значения, которые можно передать, и она эквивалентна номеру ограничения.</span><span class="sxs-lookup"><span data-stu-id="e30e5-105">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="e30e5-106">Например, в приведенной ниже таблице описываются ограничения, поддерживаемые коллекцией схемы Tables, использующей поставщик данных .NET Framework для SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e30e5-106">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="e30e5-107">Дополнительные ограничения для коллекций схем SQL Server перечислены в конце данного раздела.</span><span class="sxs-lookup"><span data-stu-id="e30e5-107">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="e30e5-108">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-108">Restriction Name</span></span>|<span data-ttu-id="e30e5-109">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-109">Parameter Name</span></span>|<span data-ttu-id="e30e5-110">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-110">Restriction Default</span></span>|<span data-ttu-id="e30e5-111">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-111">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-112">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-112">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-113">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-113">TABLE_CATALOG</span></span>|<span data-ttu-id="e30e5-114">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-114">1</span></span>|  
|<span data-ttu-id="e30e5-115">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-115">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-116">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-116">TABLE_SCHEMA</span></span>|<span data-ttu-id="e30e5-117">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-117">2</span></span>|  
|<span data-ttu-id="e30e5-118">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-118">Table</span></span>|@Name|<span data-ttu-id="e30e5-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-119">TABLE_NAME</span></span>|<span data-ttu-id="e30e5-120">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-120">3</span></span>|  
|<span data-ttu-id="e30e5-121">TableType</span><span class="sxs-lookup"><span data-stu-id="e30e5-121">TableType</span></span>|@TableType|<span data-ttu-id="e30e5-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e30e5-122">TABLE_TYPE</span></span>|<span data-ttu-id="e30e5-123">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-123">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="e30e5-124">Указание значений ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-124">Specifying Restriction Values</span></span>  

 <span data-ttu-id="e30e5-125">Чтобы использовать одно из ограничений коллекции схем Tables, необходимо создать массив строк с четырьмя элементами, затем поместить значение в элемент, совпадающий с номером ограничения.</span><span class="sxs-lookup"><span data-stu-id="e30e5-125">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="e30e5-126">Например, чтобы ограничить таблицы, возвращаемые методом **GetSchema** только таблицами из схемы "Sales", перед передачей массива методу **GetSchema** присвойте второму элементу массива значение "Sales".</span><span class="sxs-lookup"><span data-stu-id="e30e5-126">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e30e5-127">Коллекции ограничений для `SqlClient` и `OracleClient` имеют дополнительный столбец `ParameterName`.</span><span class="sxs-lookup"><span data-stu-id="e30e5-127">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="e30e5-128">Столбец ограничения по умолчанию оставлен для обратной совместимости, но не учитывается.</span><span class="sxs-lookup"><span data-stu-id="e30e5-128">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="e30e5-129">Чтобы свести к минимуму вероятности проведения атак путем внедрения кода SQL, при указании значений ограничений следует использовать параметризированные запросы, а не замену строк.</span><span class="sxs-lookup"><span data-stu-id="e30e5-129">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e30e5-130">Количество элементов в массиве должно быть меньше или равно количеству ограничений, поддерживаемых специальной коллекцией схем, в противном случае возникнет исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="e30e5-130">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="e30e5-131">Их может быть меньше максимального количества ограничений.</span><span class="sxs-lookup"><span data-stu-id="e30e5-131">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="e30e5-132">Предполагается, что отсутствующие ограничения имеют значение NULL (без ограничений).</span><span class="sxs-lookup"><span data-stu-id="e30e5-132">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="e30e5-133">Можно запросить управляемый поставщик платформа .NET Framework, чтобы определить список поддерживаемых ограничений, вызвав метод **GetSchema** с именем коллекции схем ограничений, которая является "ограничениями".</span><span class="sxs-lookup"><span data-stu-id="e30e5-133">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="e30e5-134">Будет возвращен объект <xref:System.Data.DataTable> со списком имен коллекций и ограничений, значениями ограничений по умолчанию и номерами ограничений.</span><span class="sxs-lookup"><span data-stu-id="e30e5-134">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e30e5-135">Пример</span><span class="sxs-lookup"><span data-stu-id="e30e5-135">Example</span></span>  

 <span data-ttu-id="e30e5-136">В следующих примерах показано, как использовать <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> метод поставщика данных платформа .NET Framework для класса SQL Server, <xref:System.Data.SqlClient.SqlConnection> чтобы получить сведения о схеме всех таблиц, содержащихся в образце базы данных **AdventureWorks** , а также ограничить сведения, возвращаемые только таблицам в схеме Sales:</span><span class="sxs-lookup"><span data-stu-id="e30e5-136">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="e30e5-137">Ограничения схемы SQL Server</span><span class="sxs-lookup"><span data-stu-id="e30e5-137">SQL Server Schema Restrictions</span></span>  

 <span data-ttu-id="e30e5-138">В приведенных ниже таблицах перечислены ограничения коллекций схем SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e30e5-138">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="e30e5-139">Пользователи</span><span class="sxs-lookup"><span data-stu-id="e30e5-139">Users</span></span>  
  
|<span data-ttu-id="e30e5-140">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-140">Restriction Name</span></span>|<span data-ttu-id="e30e5-141">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-141">Parameter Name</span></span>|<span data-ttu-id="e30e5-142">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-142">Restriction Default</span></span>|<span data-ttu-id="e30e5-143">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-143">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-144">User_Name</span><span class="sxs-lookup"><span data-stu-id="e30e5-144">User_Name</span></span>|@Name|<span data-ttu-id="e30e5-145">name</span><span class="sxs-lookup"><span data-stu-id="e30e5-145">name</span></span>|<span data-ttu-id="e30e5-146">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-146">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="e30e5-147">Базы данных</span><span class="sxs-lookup"><span data-stu-id="e30e5-147">Databases</span></span>  
  
|<span data-ttu-id="e30e5-148">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-148">Restriction Name</span></span>|<span data-ttu-id="e30e5-149">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-149">Parameter Name</span></span>|<span data-ttu-id="e30e5-150">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-150">Restriction Default</span></span>|<span data-ttu-id="e30e5-151">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-151">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-152">Имя</span><span class="sxs-lookup"><span data-stu-id="e30e5-152">Name</span></span>|@Name|<span data-ttu-id="e30e5-153">Имя</span><span class="sxs-lookup"><span data-stu-id="e30e5-153">Name</span></span>|<span data-ttu-id="e30e5-154">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-154">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="e30e5-155">Таблицы</span><span class="sxs-lookup"><span data-stu-id="e30e5-155">Tables</span></span>  
  
|<span data-ttu-id="e30e5-156">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-156">Restriction Name</span></span>|<span data-ttu-id="e30e5-157">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-157">Parameter Name</span></span>|<span data-ttu-id="e30e5-158">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-158">Restriction Default</span></span>|<span data-ttu-id="e30e5-159">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-159">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-160">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-160">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-161">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-161">TABLE_CATALOG</span></span>|<span data-ttu-id="e30e5-162">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-162">1</span></span>|  
|<span data-ttu-id="e30e5-163">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-163">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-164">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-164">TABLE_SCHEMA</span></span>|<span data-ttu-id="e30e5-165">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-165">2</span></span>|  
|<span data-ttu-id="e30e5-166">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-166">Table</span></span>|@Name|<span data-ttu-id="e30e5-167">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-167">TABLE_NAME</span></span>|<span data-ttu-id="e30e5-168">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-168">3</span></span>|  
|<span data-ttu-id="e30e5-169">TableType</span><span class="sxs-lookup"><span data-stu-id="e30e5-169">TableType</span></span>|@TableType|<span data-ttu-id="e30e5-170">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e30e5-170">TABLE_TYPE</span></span>|<span data-ttu-id="e30e5-171">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-171">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e30e5-172">Столбцы</span><span class="sxs-lookup"><span data-stu-id="e30e5-172">Columns</span></span>  
  
|<span data-ttu-id="e30e5-173">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-173">Restriction Name</span></span>|<span data-ttu-id="e30e5-174">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-174">Parameter Name</span></span>|<span data-ttu-id="e30e5-175">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-175">Restriction Default</span></span>|<span data-ttu-id="e30e5-176">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-176">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-177">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-177">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-178">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-178">TABLE_CATALOG</span></span>|<span data-ttu-id="e30e5-179">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-179">1</span></span>|  
|<span data-ttu-id="e30e5-180">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-180">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-181">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-181">TABLE_SCHEMA</span></span>|<span data-ttu-id="e30e5-182">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-182">2</span></span>|  
|<span data-ttu-id="e30e5-183">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-183">Table</span></span>|@Table|<span data-ttu-id="e30e5-184">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-184">TABLE_NAME</span></span>|<span data-ttu-id="e30e5-185">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-185">3</span></span>|  
|<span data-ttu-id="e30e5-186">Столбец</span><span class="sxs-lookup"><span data-stu-id="e30e5-186">Column</span></span>|@Column|<span data-ttu-id="e30e5-187">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-187">COLUMN_NAME</span></span>|<span data-ttu-id="e30e5-188">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-188">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="e30e5-189">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="e30e5-189">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="e30e5-190">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-190">Restriction Name</span></span>|<span data-ttu-id="e30e5-191">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-191">Parameter Name</span></span>|<span data-ttu-id="e30e5-192">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-192">Restriction Default</span></span>|<span data-ttu-id="e30e5-193">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-193">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-194">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-194">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-195">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-195">TABLE_CATALOG</span></span>|<span data-ttu-id="e30e5-196">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-196">1</span></span>|  
|<span data-ttu-id="e30e5-197">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-197">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-198">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-198">TABLE_SCHEMA</span></span>|<span data-ttu-id="e30e5-199">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-199">2</span></span>|  
|<span data-ttu-id="e30e5-200">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-200">Table</span></span>|@Table|<span data-ttu-id="e30e5-201">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-201">TABLE_NAME</span></span>|<span data-ttu-id="e30e5-202">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-202">3</span></span>|  
|<span data-ttu-id="e30e5-203">Столбец</span><span class="sxs-lookup"><span data-stu-id="e30e5-203">Column</span></span>|@Column|<span data-ttu-id="e30e5-204">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-204">COLUMN_NAME</span></span>|<span data-ttu-id="e30e5-205">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-205">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e30e5-206">Представления</span><span class="sxs-lookup"><span data-stu-id="e30e5-206">Views</span></span>  
  
|<span data-ttu-id="e30e5-207">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-207">Restriction Name</span></span>|<span data-ttu-id="e30e5-208">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-208">Parameter Name</span></span>|<span data-ttu-id="e30e5-209">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-209">Restriction Default</span></span>|<span data-ttu-id="e30e5-210">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-210">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-211">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-211">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-212">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-212">TABLE_CATALOG</span></span>|<span data-ttu-id="e30e5-213">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-213">1</span></span>|  
|<span data-ttu-id="e30e5-214">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-214">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-215">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-215">TABLE_SCHEMA</span></span>|<span data-ttu-id="e30e5-216">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-216">2</span></span>|  
|<span data-ttu-id="e30e5-217">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-217">Table</span></span>|@Table|<span data-ttu-id="e30e5-218">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-218">TABLE_NAME</span></span>|<span data-ttu-id="e30e5-219">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-219">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="e30e5-220">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="e30e5-220">ViewColumns</span></span>  
  
|<span data-ttu-id="e30e5-221">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-221">Restriction Name</span></span>|<span data-ttu-id="e30e5-222">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-222">Parameter Name</span></span>|<span data-ttu-id="e30e5-223">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-223">Restriction Default</span></span>|<span data-ttu-id="e30e5-224">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-224">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-225">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-225">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-226">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-226">VIEW_CATALOG</span></span>|<span data-ttu-id="e30e5-227">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-227">1</span></span>|  
|<span data-ttu-id="e30e5-228">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-228">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-229">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-229">VIEW_SCHEMA</span></span>|<span data-ttu-id="e30e5-230">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-230">2</span></span>|  
|<span data-ttu-id="e30e5-231">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-231">Table</span></span>|@Table|<span data-ttu-id="e30e5-232">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-232">VIEW_NAME</span></span>|<span data-ttu-id="e30e5-233">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-233">3</span></span>|  
|<span data-ttu-id="e30e5-234">Столбец</span><span class="sxs-lookup"><span data-stu-id="e30e5-234">Column</span></span>|@Column|<span data-ttu-id="e30e5-235">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-235">COLUMN_NAME</span></span>|<span data-ttu-id="e30e5-236">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-236">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e30e5-237">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e30e5-237">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e30e5-238">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-238">Restriction Name</span></span>|<span data-ttu-id="e30e5-239">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-239">Parameter Name</span></span>|<span data-ttu-id="e30e5-240">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-240">Restriction Default</span></span>|<span data-ttu-id="e30e5-241">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-241">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-242">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-242">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-243">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-243">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e30e5-244">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-244">1</span></span>|  
|<span data-ttu-id="e30e5-245">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-245">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-246">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-246">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e30e5-247">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-247">2</span></span>|  
|<span data-ttu-id="e30e5-248">Имя</span><span class="sxs-lookup"><span data-stu-id="e30e5-248">Name</span></span>|@Name|<span data-ttu-id="e30e5-249">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-249">SPECIFIC_NAME</span></span>|<span data-ttu-id="e30e5-250">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-250">3</span></span>|  
|<span data-ttu-id="e30e5-251">Параметр</span><span class="sxs-lookup"><span data-stu-id="e30e5-251">Parameter</span></span>|@Parameter|<span data-ttu-id="e30e5-252">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-252">PARAMETER_NAME</span></span>|<span data-ttu-id="e30e5-253">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-253">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e30e5-254">Процедуры</span><span class="sxs-lookup"><span data-stu-id="e30e5-254">Procedures</span></span>  
  
|<span data-ttu-id="e30e5-255">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-255">Restriction Name</span></span>|<span data-ttu-id="e30e5-256">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-256">Parameter Name</span></span>|<span data-ttu-id="e30e5-257">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-257">Restriction Default</span></span>|<span data-ttu-id="e30e5-258">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-258">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-259">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-259">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-260">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-260">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e30e5-261">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-261">1</span></span>|  
|<span data-ttu-id="e30e5-262">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-262">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-263">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-263">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e30e5-264">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-264">2</span></span>|  
|<span data-ttu-id="e30e5-265">Имя</span><span class="sxs-lookup"><span data-stu-id="e30e5-265">Name</span></span>|@Name|<span data-ttu-id="e30e5-266">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-266">SPECIFIC_NAME</span></span>|<span data-ttu-id="e30e5-267">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-267">3</span></span>|  
|<span data-ttu-id="e30e5-268">Тип</span><span class="sxs-lookup"><span data-stu-id="e30e5-268">Type</span></span>|@Type|<span data-ttu-id="e30e5-269">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e30e5-269">ROUTINE_TYPE</span></span>|<span data-ttu-id="e30e5-270">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-270">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="e30e5-271">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="e30e5-271">IndexColumns</span></span>  
  
|<span data-ttu-id="e30e5-272">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-272">Restriction Name</span></span>|<span data-ttu-id="e30e5-273">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-273">Parameter Name</span></span>|<span data-ttu-id="e30e5-274">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-274">Restriction Default</span></span>|<span data-ttu-id="e30e5-275">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-275">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-276">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-276">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-277">db_name()</span><span class="sxs-lookup"><span data-stu-id="e30e5-277">db_name()</span></span>|<span data-ttu-id="e30e5-278">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-278">1</span></span>|  
|<span data-ttu-id="e30e5-279">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-279">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-280">user_name()</span><span class="sxs-lookup"><span data-stu-id="e30e5-280">user_name()</span></span>|<span data-ttu-id="e30e5-281">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-281">2</span></span>|  
|<span data-ttu-id="e30e5-282">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-282">Table</span></span>|@Table|<span data-ttu-id="e30e5-283">o.name</span><span class="sxs-lookup"><span data-stu-id="e30e5-283">o.name</span></span>|<span data-ttu-id="e30e5-284">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-284">3</span></span>|  
|<span data-ttu-id="e30e5-285">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="e30e5-285">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="e30e5-286">x.name</span><span class="sxs-lookup"><span data-stu-id="e30e5-286">x.name</span></span>|<span data-ttu-id="e30e5-287">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-287">4</span></span>|  
|<span data-ttu-id="e30e5-288">Столбец</span><span class="sxs-lookup"><span data-stu-id="e30e5-288">Column</span></span>|@Column|<span data-ttu-id="e30e5-289">c.name</span><span class="sxs-lookup"><span data-stu-id="e30e5-289">c.name</span></span>|<span data-ttu-id="e30e5-290">5</span><span class="sxs-lookup"><span data-stu-id="e30e5-290">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e30e5-291">Индексы</span><span class="sxs-lookup"><span data-stu-id="e30e5-291">Indexes</span></span>  
  
|<span data-ttu-id="e30e5-292">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-292">Restriction Name</span></span>|<span data-ttu-id="e30e5-293">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-293">Parameter Name</span></span>|<span data-ttu-id="e30e5-294">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-294">Restriction Default</span></span>|<span data-ttu-id="e30e5-295">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-295">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-296">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-296">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-297">db_name()</span><span class="sxs-lookup"><span data-stu-id="e30e5-297">db_name()</span></span>|<span data-ttu-id="e30e5-298">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-298">1</span></span>|  
|<span data-ttu-id="e30e5-299">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-299">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-300">user_name()</span><span class="sxs-lookup"><span data-stu-id="e30e5-300">user_name()</span></span>|<span data-ttu-id="e30e5-301">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-301">2</span></span>|  
|<span data-ttu-id="e30e5-302">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-302">Table</span></span>|@Table|<span data-ttu-id="e30e5-303">o.name</span><span class="sxs-lookup"><span data-stu-id="e30e5-303">o.name</span></span>|<span data-ttu-id="e30e5-304">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-304">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="e30e5-305">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="e30e5-305">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="e30e5-306">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-306">Restriction Name</span></span>|<span data-ttu-id="e30e5-307">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-307">Parameter Name</span></span>|<span data-ttu-id="e30e5-308">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-308">Restriction Default</span></span>|<span data-ttu-id="e30e5-309">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-309">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-310">assembly_name</span><span class="sxs-lookup"><span data-stu-id="e30e5-310">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="e30e5-311">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="e30e5-311">assemblies.name</span></span>|<span data-ttu-id="e30e5-312">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-312">1</span></span>|  
|<span data-ttu-id="e30e5-313">udt_name</span><span class="sxs-lookup"><span data-stu-id="e30e5-313">udt_name</span></span>|@UDTName|<span data-ttu-id="e30e5-314">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="e30e5-314">types.assembly_class</span></span>|<span data-ttu-id="e30e5-315">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-315">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="e30e5-316">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="e30e5-316">ForeignKeys</span></span>  
  
|<span data-ttu-id="e30e5-317">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-317">Restriction Name</span></span>|<span data-ttu-id="e30e5-318">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-318">Parameter Name</span></span>|<span data-ttu-id="e30e5-319">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-319">Restriction Default</span></span>|<span data-ttu-id="e30e5-320">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-320">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-321">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-321">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-322">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-322">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="e30e5-323">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-323">1</span></span>|  
|<span data-ttu-id="e30e5-324">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-324">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-325">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-325">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="e30e5-326">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-326">2</span></span>|  
|<span data-ttu-id="e30e5-327">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-327">Table</span></span>|@Table|<span data-ttu-id="e30e5-328">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-328">TABLE_NAME</span></span>|<span data-ttu-id="e30e5-329">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-329">3</span></span>|  
|<span data-ttu-id="e30e5-330">Имя</span><span class="sxs-lookup"><span data-stu-id="e30e5-330">Name</span></span>|@Name|<span data-ttu-id="e30e5-331">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-331">CONSTRAINT_NAME</span></span>|<span data-ttu-id="e30e5-332">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-332">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="e30e5-333">Ограничения схемы SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="e30e5-333">SQL Server 2008 Schema Restrictions</span></span>  

 <span data-ttu-id="e30e5-334">В приведенных ниже таблицах перечислены ограничения коллекций схем SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="e30e5-334">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="e30e5-335">Эти ограничения действуют, начиная с версии .NET Framework 3.5 с пакетом обновления 1 (SP1) и SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="e30e5-335">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="e30e5-336">Они не поддерживаются в предыдущих версиях .NET Framework и SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e30e5-336">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="e30e5-337">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="e30e5-337">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="e30e5-338">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-338">Restriction Name</span></span>|<span data-ttu-id="e30e5-339">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-339">Parameter Name</span></span>|<span data-ttu-id="e30e5-340">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-340">Restriction Default</span></span>|<span data-ttu-id="e30e5-341">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-341">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-342">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-342">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-343">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-343">TABLE_CATALOG</span></span>|<span data-ttu-id="e30e5-344">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-344">1</span></span>|  
|<span data-ttu-id="e30e5-345">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-345">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-346">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-346">TABLE_SCHEMA</span></span>|<span data-ttu-id="e30e5-347">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-347">2</span></span>|  
|<span data-ttu-id="e30e5-348">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-348">Table</span></span>|@Table|<span data-ttu-id="e30e5-349">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-349">TABLE_NAME</span></span>|<span data-ttu-id="e30e5-350">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-350">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="e30e5-351">AllColumns</span><span class="sxs-lookup"><span data-stu-id="e30e5-351">AllColumns</span></span>  
  
|<span data-ttu-id="e30e5-352">Имя ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-352">Restriction Name</span></span>|<span data-ttu-id="e30e5-353">имени параметра</span><span class="sxs-lookup"><span data-stu-id="e30e5-353">Parameter Name</span></span>|<span data-ttu-id="e30e5-354">Значение ограничения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e30e5-354">Restriction Default</span></span>|<span data-ttu-id="e30e5-355">Номер ограничения</span><span class="sxs-lookup"><span data-stu-id="e30e5-355">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e30e5-356">Каталог</span><span class="sxs-lookup"><span data-stu-id="e30e5-356">Catalog</span></span>|@Catalog|<span data-ttu-id="e30e5-357">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e30e5-357">TABLE_CATALOG</span></span>|<span data-ttu-id="e30e5-358">1</span><span class="sxs-lookup"><span data-stu-id="e30e5-358">1</span></span>|  
|<span data-ttu-id="e30e5-359">Владелец</span><span class="sxs-lookup"><span data-stu-id="e30e5-359">Owner</span></span>|@Owner|<span data-ttu-id="e30e5-360">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e30e5-360">TABLE_SCHEMA</span></span>|<span data-ttu-id="e30e5-361">2</span><span class="sxs-lookup"><span data-stu-id="e30e5-361">2</span></span>|  
|<span data-ttu-id="e30e5-362">Таблица</span><span class="sxs-lookup"><span data-stu-id="e30e5-362">Table</span></span>|@Table|<span data-ttu-id="e30e5-363">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-363">TABLE_NAME</span></span>|<span data-ttu-id="e30e5-364">3</span><span class="sxs-lookup"><span data-stu-id="e30e5-364">3</span></span>|  
|<span data-ttu-id="e30e5-365">Столбец</span><span class="sxs-lookup"><span data-stu-id="e30e5-365">Column</span></span>|@Column|<span data-ttu-id="e30e5-366">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e30e5-366">COLUMN_NAME</span></span>|<span data-ttu-id="e30e5-367">4</span><span class="sxs-lookup"><span data-stu-id="e30e5-367">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e30e5-368">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e30e5-368">See also</span></span>

- [<span data-ttu-id="e30e5-369">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e30e5-369">ADO.NET Overview</span></span>](ado-net-overview.md)
