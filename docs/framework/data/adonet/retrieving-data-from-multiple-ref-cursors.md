---
title: Извлечение данных нескольких REF CURSOR с использованием OracleDataReader
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: e205ad39ca91dec95e54fe26cd79012c6c41ee55
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739951"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a><span data-ttu-id="d4c3d-102">Извлечение данных нескольких REF CURSOR с использованием OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="d4c3d-102">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>

<span data-ttu-id="d4c3d-103">Этот пример на языке Microsoft Visual Basic выполняет хранимую процедуру PL/SQL, возвращающую два параметра REF CURSOR и считывающую значения, используя класс <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d4c3d-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

```vb
Private Sub Button1_Click( _
  ByVal sender As Object, ByVal e As System.EventArgs)  _
  Handles Button1.Click

  Dim connString As New String( _
      "Data Source=Oracle9i;User ID=scott;Password=[PLACEHOLDER];")
  Using conn As New OracleConnection(connString)
    Dim cmd As New OracleCommand()
    Dim rdr As OracleDataReader

    conn.Open()
    cmd.Connection = conn
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"
    cmd.CommandType = CommandType.StoredProcedure
    cmd.Parameters.Add(New OracleParameter( _
      "EMPCURSOR", OracleType.Cursor)).Direction = _
      ParameterDirection.Output
    cmd.Parameters.Add(New OracleParameter(_
      "DEPTCURSOR", OracleType.Cursor)).Direction = _
      ParameterDirection.Output

    rdr = cmd.ExecuteReader(CommandBehavior.CloseConnection)
    While (rdr.Read())
        REM do something with the values from the EMP table
    End While

    rdr.NextResult()
    While (rdr.Read())
        REM do something with the values from the DEPT table
    End While
    rdr.Close()
  End Using
End Sub
```

## <a name="see-also"></a><span data-ttu-id="d4c3d-104">См. также</span><span class="sxs-lookup"><span data-stu-id="d4c3d-104">See also</span></span>

- [<span data-ttu-id="d4c3d-105">REF CURSOR в Oracle</span><span class="sxs-lookup"><span data-stu-id="d4c3d-105">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="d4c3d-106">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d4c3d-106">ADO.NET Overview</span></span>](ado-net-overview.md)
