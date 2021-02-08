---
description: 'Дополнительные сведения: указание значений XML в качестве параметров'
title: Указание значений XML как параметров
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.openlocfilehash: 9c5b81270eeaec1fc0b3992971c9285863c92466
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767457"
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="c5967-103">Указание значений XML как параметров</span><span class="sxs-lookup"><span data-stu-id="c5967-103">Specifying XML Values as Parameters</span></span>

<span data-ttu-id="c5967-104">Если запрос требует параметров, значения которых представляет XML-строка, разработчики могут передать это значение с помощью экземпляра типа данных **SqlXml**.</span><span class="sxs-lookup"><span data-stu-id="c5967-104">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="c5967-105">Это не составляет никакой сложности, поскольку XML-столбцы в SQL Server принимают значения параметров точно так же, как другие типы данных.</span><span class="sxs-lookup"><span data-stu-id="c5967-105">There really are no tricks; XML columns in SQL Server accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5967-106">Пример</span><span class="sxs-lookup"><span data-stu-id="c5967-106">Example</span></span>  

 <span data-ttu-id="c5967-107">Следующее приложение командной строки создает новую таблицу в базе данных **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="c5967-107">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="c5967-108">Новая таблица содержит столбец с именем **SalesID** и XML-столбец с именем **SalesInfo**.</span><span class="sxs-lookup"><span data-stu-id="c5967-108">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5967-109">Образец базы данных **AdventureWorks** не устанавливается по умолчанию при установке SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c5967-109">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="c5967-110">Чтобы установить его, запустите программу установки SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c5967-110">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="c5967-111">Наш пример подготавливает объект <xref:System.Data.SqlClient.SqlCommand> для вставки строки в новую таблицу.</span><span class="sxs-lookup"><span data-stu-id="c5967-111">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="c5967-112">Сохраненный файл предоставляет XML-данные, необходимые для столбца **SalesInfo**.</span><span class="sxs-lookup"><span data-stu-id="c5967-112">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="c5967-113">Чтобы получить файл, необходимый для выполнения этого примера, создайте пустой текстовый файл в той же папке, где размещен проект.</span><span class="sxs-lookup"><span data-stu-id="c5967-113">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="c5967-114">Присвойте этому файлу имя MyTestStoreData.xml.</span><span class="sxs-lookup"><span data-stu-id="c5967-114">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="c5967-115">Откройте файл в Блокноте, скопируйте и вставьте в него следующий текст:</span><span class="sxs-lookup"><span data-stu-id="c5967-115">Open the file in Notepad and copy and paste the following text:</span></span>  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Xml  
  
Module Module1  
    Sub Main()  
  
        Using connection As SqlConnection = New SqlConnection(GetConnectionString())  
        connection.Open()  
  
        ' Create a sample table (dropping first if it already  
        ' exists.)  
        Dim commandNewTable As String = _  
         "IF EXISTS (SELECT * FROM dbo.sysobjects " & _  
         "WHERE id = object_id(N'[dbo].[XmlDataTypeSample]') " & _  
         "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " & _  
         "DROP TABLE [dbo].[XmlDataTypeSample];" & _  
         "CREATE TABLE [dbo].[XmlDataTypeSample](" & _  
         "[SalesID] [int] IDENTITY(1,1) NOT NULL, " & _  
         "[SalesInfo] [xml])"  
  
        Dim commandAdd As New _  
         SqlCommand(commandNewTable, connection)  
        commandAdd.ExecuteNonQuery()  
  
        Dim commandText As String = _  
         "INSERT INTO [dbo].[XmlDataTypeSample] " & _  
           "([SalesInfo] ) " & _  
           "VALUES(@xmlParameter )"  
  
        Dim command As New SqlCommand(commandText, connection)  
  
        ' Read the saved XML document as a
        ' SqlXml-data typed variable.  
        Dim newXml As SqlXml = _  
         New SqlXml(New XmlTextReader("MyTestStoreData.xml"))  
  
        ' Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml)  
  
        Dim result As Integer = command.ExecuteNonQuery()  
        Console.WriteLine(result & " row was added.")  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Using  
End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +
            "DROP TABLE [dbo].[XmlDataTypeSample];" +
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =
            "INSERT INTO [dbo].[XmlDataTypeSample] " +
            "([SalesInfo] ) " +
            "VALUES(@xmlParameter )";  
        SqlCommand command =
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a
        //  SqlXml-data typed variable.  
        SqlXml newXml =
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,
        // you can retrieve it from a configuration file.
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5967-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c5967-116">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="c5967-117">XML-данные в SQL Server</span><span class="sxs-lookup"><span data-stu-id="c5967-117">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="c5967-118">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5967-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
