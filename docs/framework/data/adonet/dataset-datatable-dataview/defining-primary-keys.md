---
description: 'Дополнительные сведения: Определение первичных ключей'
title: Определение первичных ключей
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 2becfbd124af723f55edb39666352fc501044045
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652553"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="bc4b1-103">Определение первичных ключей</span><span class="sxs-lookup"><span data-stu-id="bc4b1-103">Defining Primary Keys</span></span>

<span data-ttu-id="bc4b1-104">База данных обычно содержит столбец или группу столбцов, уникально определяющих каждую строку в таблице.</span><span class="sxs-lookup"><span data-stu-id="bc4b1-104">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="bc4b1-105">Такие столбцы или группы столбцов называются первичными ключами.</span><span class="sxs-lookup"><span data-stu-id="bc4b1-105">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="bc4b1-106">При определении одного объекта в <xref:System.Data.DataColumn> качестве <xref:System.Data.DataTable.PrimaryKey%2A> для <xref:System.Data.DataTable> таблицы автоматически присваивает <xref:System.Data.DataColumn.AllowDBNull%2A> свойству столбца **значение false** , а <xref:System.Data.DataColumn.Unique%2A> свойству — **значение true**.</span><span class="sxs-lookup"><span data-stu-id="bc4b1-106">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="bc4b1-107">Для первичных ключей с несколькими столбцами автоматически присваивается **значение false** только для свойства **AllowDbNull** .</span><span class="sxs-lookup"><span data-stu-id="bc4b1-107">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="bc4b1-108">Свойство **PrimaryKey** <xref:System.Data.DataTable> принимает в качестве значения массив из одного или нескольких объектов **DataColumn** , как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="bc4b1-108">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="bc4b1-109">В первом примере в качестве первичного ключа определяется один столбец.</span><span class="sxs-lookup"><span data-stu-id="bc4b1-109">The first example defines a single column as the primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 <span data-ttu-id="bc4b1-110">Следующий пример определяет два столбца в качестве первичного ключа.</span><span class="sxs-lookup"><span data-stu-id="bc4b1-110">The following example defines two columns as a primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc4b1-111">См. также</span><span class="sxs-lookup"><span data-stu-id="bc4b1-111">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="bc4b1-112">Определение схемы таблицы данных</span><span class="sxs-lookup"><span data-stu-id="bc4b1-112">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="bc4b1-113">DataTables</span><span class="sxs-lookup"><span data-stu-id="bc4b1-113">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="bc4b1-114">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bc4b1-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
