---
description: 'Дополнительные сведения: метод Load'
title: Метод Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: a14008597d88ad4af93c3646998244d94b5561d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651526"
---
# <a name="the-load-method"></a><span data-ttu-id="a55bf-103">Метод Load</span><span class="sxs-lookup"><span data-stu-id="a55bf-103">The Load Method</span></span>

<span data-ttu-id="a55bf-104">Метод <xref:System.Data.DataTable.Load%2A> используется для загрузки в таблицу <xref:System.Data.DataTable> строк из источника данных.</span><span class="sxs-lookup"><span data-stu-id="a55bf-104">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="a55bf-105">Это перегруженный метод, который в простейшей форме принимает один параметр — **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-105">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="a55bf-106">В этой форме он просто загружает **таблицу данных DataTable** со строками.</span><span class="sxs-lookup"><span data-stu-id="a55bf-106">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="a55bf-107">При необходимости можно указать параметр **loadOption** для управления добавлением данных в **таблицу DataTable**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-107">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="a55bf-108">Параметр **loadOption** особенно полезен в случаях, когда объект **DataTable** уже содержит строки данных, поскольку он описывает, как входящие данные из источника данных будут объединены с данными, уже находящихся в таблице.</span><span class="sxs-lookup"><span data-stu-id="a55bf-108">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="a55bf-109">Например, **пресервекуррентвалуес** (значение по умолчанию) указывает, что в случаях, когда строка помечена как **добавленная** в **таблицу** данных, **исходное** значение или каждый столбец задается в соответствии с содержимым соответствующей строки из источника.</span><span class="sxs-lookup"><span data-stu-id="a55bf-109">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="a55bf-110">**Текущее** значение будет хранить значения, назначенные при добавлении строки, а **RowState** строки будет **изменено**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-110">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="a55bf-111">В следующей таблице приведено краткое описание значений перечисления <xref:System.Data.LoadOption>.</span><span class="sxs-lookup"><span data-stu-id="a55bf-111">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="a55bf-112">Значение LoadOption</span><span class="sxs-lookup"><span data-stu-id="a55bf-112">LoadOption value</span></span>|<span data-ttu-id="a55bf-113">Описание</span><span class="sxs-lookup"><span data-stu-id="a55bf-113">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="a55bf-114">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="a55bf-114">**OverwriteRow**</span></span>|<span data-ttu-id="a55bf-115">Если входящие строки имеют то же значение **PrimaryKey** , что и строка, уже находящиеся в **DataTable**, то **исходные** и **текущие** значения каждого столбца заменяются значениями во входной строке, а для свойства **RowState** устанавливается значение **без изменений**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-115">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="a55bf-116">Строки из источника данных, которые еще не существуют в **DataTable** , добавляются со значением **RowState** без **изменений**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-116">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="a55bf-117">Этот параметр в силе обновляет содержимое **таблицы DataTable** , чтобы оно соответствовало содержимому источника данных.</span><span class="sxs-lookup"><span data-stu-id="a55bf-117">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="a55bf-118">**PreserveCurrentValues (значение по умолчанию)**</span><span class="sxs-lookup"><span data-stu-id="a55bf-118">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="a55bf-119">Если входящие строки имеют то же значение **PrimaryKey** , что и строка, уже находящиеся в **DataTable**, то **исходное** значение устанавливается на содержимое входящей строки, а **Текущее** значение не изменяется.</span><span class="sxs-lookup"><span data-stu-id="a55bf-119">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="a55bf-120">При **добавлении** или **изменении** **RowState** оно **изменяется на изменено**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-120">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="a55bf-121">Если параметр **RowState** **удален**, он остается **удаленным**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-121">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="a55bf-122">Строки из источника данных, которые еще не существуют в **DataTable** , добавляются, а для **RowState** устанавливается значение **без изменений**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-122">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="a55bf-123">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="a55bf-123">**UpdateCurrentValues**</span></span>|<span data-ttu-id="a55bf-124">Если входящие строки имеют то же значение **PrimaryKey** , что и строка, уже находящиеся в **DataTable**, **Текущее** значение копируется в **исходное** значение, а **Текущее** значение затем устанавливается в содержимое входящей строки.</span><span class="sxs-lookup"><span data-stu-id="a55bf-124">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="a55bf-125">Если свойство **RowState** в **таблице DataTable** было **добавлено**, то свойство **RowState** остается **добавленным**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-125">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="a55bf-126">Для строк, помеченных как **измененные** или **Удаленные**, свойство **RowState** **изменяется**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-126">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="a55bf-127">Строки из источника данных, которые еще не существуют в **DataTable** , добавляются, а для свойства **RowState** устанавливается значение **added**.</span><span class="sxs-lookup"><span data-stu-id="a55bf-127">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="a55bf-128">В следующем примере метод **Load** используется для вывода списка дней рождения сотрудников в базе данных **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="a55bf-128">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="a55bf-129">См. также</span><span class="sxs-lookup"><span data-stu-id="a55bf-129">See also</span></span>

- [<span data-ttu-id="a55bf-130">Управление данными в таблице данных</span><span class="sxs-lookup"><span data-stu-id="a55bf-130">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="a55bf-131">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a55bf-131">ADO.NET Overview</span></span>](../ado-net-overview.md)
