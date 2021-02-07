---
description: 'Дополнительные сведения: заполнение набора данных с помощью одного или нескольких ССЫЛОЧных КУРСОРов'
title: Заполнение набора данных с помощью одного или нескольких параметров REF CURSOR
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 99863e79-5b00-467e-a105-4ffa42de3ff7
ms.openlocfilehash: 6df871a9ab708a4275f15a136f3f99b6a98e1fe1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724158"
---
# <a name="filling-a-dataset-using-one-or-more-ref-cursors"></a><span data-ttu-id="58c8f-103">Заполнение набора данных с помощью одного или нескольких параметров REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="58c8f-103">Filling a DataSet Using One or More REF CURSORs</span></span>

<span data-ttu-id="58c8f-104">В этом примере Microsoft Visual Basic выполняется хранимая процедура PL/SQL, которая возвращает два параметра REF CURSOR и заполняет объект <xref:System.Data.DataSet> возвращенными строками.</span><span class="sxs-lookup"><span data-stu-id="58c8f-104">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>

```vb
Private Sub Button1_Click(ByVal sender As Object, _
  ByVal e As System.EventArgs) Handles Button1.Click

  Dim connString As New String(_
    "Data Source=Oracle9i;User ID=scott;Password=[PLACEHOLDER];")
  Dim ds As New DataSet()
    Using conn As New OracleConnection(connString)
    Dim cmd As New OracleCommand()

    cmd.Connection = conn
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"
    cmd.CommandType = CommandType.StoredProcedure
    cmd.Parameters.Add(New OracleParameter( _
      "EMPCURSOR", OracleType.Cursor)).Direction = _
      ParameterDirection.Output
    cmd.Parameters.Add(New OracleParameter( _
      "DEPTCURSOR", OracleType.Cursor)).Direction = _
       ParameterDirection.Output

    Dim da As New OracleDataAdapter(cmd)
    da.TableMappings.Add("Table", "Emp")
    da.TableMappings.Add("Table1", "Dept")
    da.Fill(ds)

    ds.Relations.Add("EmpDept", ds.Tables("Dept").Columns("Deptno"), _
      ds.Tables("Emp").Columns("Deptno"), False)

    DataGrid1.DataSource = ds.Tables("Dept")
  End Using
```

## <a name="see-also"></a><span data-ttu-id="58c8f-105">См. также</span><span class="sxs-lookup"><span data-stu-id="58c8f-105">See also</span></span>

- [<span data-ttu-id="58c8f-106">REF CURSOR в Oracle</span><span class="sxs-lookup"><span data-stu-id="58c8f-106">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="58c8f-107">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="58c8f-107">ADO.NET Overview</span></span>](ado-net-overview.md)
