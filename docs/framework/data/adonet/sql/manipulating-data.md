---
description: 'Дополнительные сведения: Управление данными'
title: Управление данными
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.openlocfilehash: dba948fe923e709f6564e6c64fd9adce7f3f15f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767691"
---
# <a name="manipulating-data"></a><span data-ttu-id="3b20e-103">Управление данными</span><span class="sxs-lookup"><span data-stu-id="3b20e-103">Manipulating Data</span></span>

<span data-ttu-id="3b20e-104">Перед введением функции MARS для решения определенных сценариев разработчикам приходилось использовать несколько подключений или курсоров на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="3b20e-104">Before the introduction of Multiple Active Result Sets (MARS), developers had to use either multiple connections or server-side cursors to solve certain scenarios.</span></span> <span data-ttu-id="3b20e-105">Кроме того, при использовании нескольких соединений в условиях транзакции приходилось прибегать к связанным соединениям (на основе системных хранимых процедур **sp_getbindtoken** и **sp_bindsession**).</span><span class="sxs-lookup"><span data-stu-id="3b20e-105">In addition, when multiple connections were used in a transactional situation, bound connections (with **sp_getbindtoken** and **sp_bindsession**) were required.</span></span> <span data-ttu-id="3b20e-106">В следующих сценариях показано, как использовать подключение с включенным режимом MARS вместо нескольких подключений.</span><span class="sxs-lookup"><span data-stu-id="3b20e-106">The following scenarios show how to use a MARS-enabled connection instead of multiple connections.</span></span>  
  
## <a name="using-multiple-commands-with-mars"></a><span data-ttu-id="3b20e-107">Использование нескольких команд с помощью режима MARS</span><span class="sxs-lookup"><span data-stu-id="3b20e-107">Using Multiple Commands with MARS</span></span>  

 <span data-ttu-id="3b20e-108">В следующем консольном приложении показано, как использовать два объекта <xref:System.Data.SqlClient.SqlDataReader> с двумя объектами <xref:System.Data.SqlClient.SqlCommand> и один объект <xref:System.Data.SqlClient.SqlConnection> с включенным режимом MARS.</span><span class="sxs-lookup"><span data-stu-id="3b20e-108">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with two <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3b20e-109">Пример</span><span class="sxs-lookup"><span data-stu-id="3b20e-109">Example</span></span>  

 <span data-ttu-id="3b20e-110">В примере открывается одно соединение с базой данных **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="3b20e-110">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="3b20e-111">С помощью объекта <xref:System.Data.SqlClient.SqlCommand> создается <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="3b20e-111">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="3b20e-112">По мере использования модуля чтения открывается второй класс <xref:System.Data.SqlClient.SqlDataReader>, который использует данные из первого класса <xref:System.Data.SqlClient.SqlDataReader> в качестве входных данных для второго средства чтения.</span><span class="sxs-lookup"><span data-stu-id="3b20e-112">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b20e-113">В следующем примере используется образец базы данных **AdventureWorks**, входящий в состав SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b20e-113">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="3b20e-114">В строке подключения в примере кода предполагается, что база данных установлена и доступна на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="3b20e-114">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="3b20e-115">При необходимости измените строку подключения для вашей среды.</span><span class="sxs-lookup"><span data-stu-id="3b20e-115">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Module Module1  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim vendorID As Integer  
  
    Dim vendorCmd As SqlCommand  
    Dim productCmd As SqlCommand  
    Dim productReader As SqlDataReader  
  
    Dim vendorSQL As String = & _
      "SELECT VendorId, Name FROM Purchasing.Vendor"  
    Dim productSQL As String = _  
        "SELECT Production.Product.Name FROM Production.Product " & _  
        "INNER JOIN Purchasing.ProductVendor " & _  
        "ON Production.Product.ProductID = " & _  
        "Purchasing.ProductVendor.ProductID " & _  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId"  
  
    Using awConnection As New SqlConnection(connectionString)  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      productCmd = New SqlCommand(productSQL, awConnection)  
      productCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      awConnection.Open()  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorId"))  
  
          productCmd.Parameters("@VendorId").Value = vendorID  
  
          ' The following line of code requires  
          ' a MARS-enabled connection.  
          productReader = productCmd.ExecuteReader()  
          Using productReader  
            While productReader.Read()  
              Console.WriteLine("  " & CStr(productReader("Name")))  
            End While  
          End Using  
        End While  
      End Using  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks; MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a><span data-ttu-id="3b20e-116">Считывание и обновление данных с помощью режима MARS</span><span class="sxs-lookup"><span data-stu-id="3b20e-116">Reading and Updating Data with MARS</span></span>  

 <span data-ttu-id="3b20e-117">Режим MARS позволяет использовать соединение как для операций чтения, так и для операций языка обработки данных (DML) с более чем одной ожидающей операцией.</span><span class="sxs-lookup"><span data-stu-id="3b20e-117">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="3b20e-118">Эта функция устраняет необходимость приложения решать проблемы, связанные с ошибками во время подключения.</span><span class="sxs-lookup"><span data-stu-id="3b20e-118">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="3b20e-119">Кроме того, режим MARS может заменить использование курсоров на стороне сервера, которые обычно потребляют больше ресурсов.</span><span class="sxs-lookup"><span data-stu-id="3b20e-119">In addition, MARS can replace the use of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="3b20e-120">Наконец, несколько операций могут осуществляться одновременно в одном соединении, поэтому в них может совместно использоваться один и тот же контекст транзакции, в результате чего отпадает необходимость использования системных хранимых процедур **sp_getbindtoken** и **sp_bindsession**.</span><span class="sxs-lookup"><span data-stu-id="3b20e-120">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3b20e-121">Пример</span><span class="sxs-lookup"><span data-stu-id="3b20e-121">Example</span></span>  

 <span data-ttu-id="3b20e-122">В следующем консольном приложении показано, как использовать два объекта <xref:System.Data.SqlClient.SqlDataReader> с тремя объектами <xref:System.Data.SqlClient.SqlCommand> и один объект <xref:System.Data.SqlClient.SqlConnection> с включенным режимом MARS.</span><span class="sxs-lookup"><span data-stu-id="3b20e-122">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="3b20e-123">Первый объект команды получает список поставщиков с кредитоспособностью — 5.</span><span class="sxs-lookup"><span data-stu-id="3b20e-123">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="3b20e-124">Второй объект команды использует идентификатор поставщика из <xref:System.Data.SqlClient.SqlDataReader> для загрузки второго объекта <xref:System.Data.SqlClient.SqlDataReader> со всеми продуктами данного поставщика.</span><span class="sxs-lookup"><span data-stu-id="3b20e-124">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="3b20e-125">Каждая запись продукта посещается вторым <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="3b20e-125">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="3b20e-126">Для определения нового состояния **OnOrderQty** выполняется вычисление.</span><span class="sxs-lookup"><span data-stu-id="3b20e-126">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="3b20e-127">Затем используется третий объект команды для занесения в таблицу **ProductVendor** нового значения.</span><span class="sxs-lookup"><span data-stu-id="3b20e-127">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="3b20e-128">Весь процесс выполняется в рамках одной транзакции, которая откатывается в конце.</span><span class="sxs-lookup"><span data-stu-id="3b20e-128">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b20e-129">В следующем примере используется образец базы данных **AdventureWorks**, входящий в состав SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b20e-129">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="3b20e-130">В строке подключения в примере кода предполагается, что база данных установлена и доступна на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="3b20e-130">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="3b20e-131">При необходимости измените строку подключения для вашей среды.</span><span class="sxs-lookup"><span data-stu-id="3b20e-131">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim updateTx As SqlTransaction  
    Dim vendorCmd As SqlCommand  
    Dim prodVendCmd As SqlCommand  
    Dim updateCmd As SqlCommand  
  
    Dim prodVendReader As SqlDataReader  
  
    Dim vendorID As Integer  
    Dim productID As Integer  
    Dim minOrderQty As Integer  
    Dim maxOrderQty As Integer  
    Dim onOrderQty As Integer  
    Dim recordsUpdated As Integer  
    Dim totalRecordsUpdated As Integer  
  
    Dim vendorSQL As String = _  
        "SELECT VendorID, Name FROM Purchasing.Vendor " & _  
        "WHERE CreditRating = 5"  
    Dim prodVendSQL As String = _  
        "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " & _  
        "FROM Purchasing.ProductVendor " & _  
        "WHERE VendorID = @VendorID"  
    Dim updateSQL As String = _  
        "UPDATE Purchasing.ProductVendor " & _
        "SET OnOrderQty = @OrderQty " & _  
        "WHERE ProductID = @ProductID AND VendorID = @VendorID"  
  
    Using awConnection As New SqlConnection(connectionString)  
      awConnection.Open()  
      updateTx = awConnection.BeginTransaction()  
  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      vendorCmd.Transaction = updateTx  
  
      prodVendCmd = New SqlCommand(prodVendSQL, awConnection)  
      prodVendCmd.Transaction = updateTx  
      prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      updateCmd = New SqlCommand(updateSQL, awConnection)  
      updateCmd.Transaction = updateTx  
      updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int)  
      updateCmd.Parameters.Add("@ProductID", SqlDbType.Int)  
      updateCmd.Parameters.Add("@VendorID", SqlDbType.Int)  
  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorID"))  
          prodVendCmd.Parameters("@VendorID").Value = vendorID  
          prodVendReader = prodVendCmd.ExecuteReader()  
  
          Using prodVendReader  
            While (prodVendReader.Read)  
              productID = CInt(prodVendReader("ProductID"))  
  
              If IsDBNull(prodVendReader("OnOrderQty")) Then  
                minOrderQty = CInt(prodVendReader("MinOrderQty"))  
                onOrderQty = minOrderQty  
              Else  
                maxOrderQty = CInt(prodVendReader("MaxOrderQty"))  
                onOrderQty = CInt(maxOrderQty / 2)  
              End If  
  
              updateCmd.Parameters("@OrderQty").Value = onOrderQty  
              updateCmd.Parameters("@ProductID").Value = productID  
              updateCmd.Parameters("@VendorID").Value = vendorID  
  
              recordsUpdated = updateCmd.ExecuteNonQuery()  
              totalRecordsUpdated += recordsUpdated  
            End While  
          End Using  
        End While  
      End Using  
  
      Console.WriteLine("Total Records Updated: " & _
        CStr(totalRecordsUpdated))  
      updateTx.Rollback()  
      Console.WriteLine("Transaction Rolled Back")  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +
    "Initial Catalog=AdventureWorks;" +
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b20e-132">См. также</span><span class="sxs-lookup"><span data-stu-id="3b20e-132">See also</span></span>

- [<span data-ttu-id="3b20e-133">Режим MARS</span><span class="sxs-lookup"><span data-stu-id="3b20e-133">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="3b20e-134">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3b20e-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
