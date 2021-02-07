---
description: 'Дополнительные сведения о: Ораклетипес'
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 5444fd8e9eec6172394bdca68ada38cf02e7c2c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672404"
---
# <a name="oracletypes"></a><span data-ttu-id="c5309-103">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="c5309-103">OracleTypes</span></span>

<span data-ttu-id="c5309-104">Поставщик данных .NET Framework для Oracle содержит несколько структур, которые можно использовать для работы с типами данных Oracle.</span><span class="sxs-lookup"><span data-stu-id="c5309-104">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="c5309-105">В их числе <xref:System.Data.OracleClient.OracleNumber> и <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="c5309-105">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5309-106">Полное описание этих структур см. в разделе <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="c5309-106">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="c5309-107">Далее приведены примеры на языке C#.</span><span class="sxs-lookup"><span data-stu-id="c5309-107">The following C# examples:</span></span>  
  
- <span data-ttu-id="c5309-108">Создайте таблицу Oracle и заполните ее данными.</span><span class="sxs-lookup"><span data-stu-id="c5309-108">Create an Oracle table and load it with data.</span></span>  
  
- <span data-ttu-id="c5309-109">Воспользуйтесь объектом <xref:System.Data.OracleClient.OracleDataReader> для доступа к данным и несколькими структурами <xref:System.Data.OracleClient.OracleType> для отображения этих данных.</span><span class="sxs-lookup"><span data-stu-id="c5309-109">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="c5309-110">Создание таблицы Oracle</span><span class="sxs-lookup"><span data-stu-id="c5309-110">Creating an Oracle Table</span></span>  

 <span data-ttu-id="c5309-111">В этом примере создается и загружается данными таблица Oracle.</span><span class="sxs-lookup"><span data-stu-id="c5309-111">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="c5309-112">Пример следует выполнить до запуска следующего примера.</span><span class="sxs-lookup"><span data-stu-id="c5309-112">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="c5309-113">Получение данных из таблицы Oracle</span><span class="sxs-lookup"><span data-stu-id="c5309-113">Retrieving Data from the Oracle Table</span></span>  

 <span data-ttu-id="c5309-114">В этом примере используется **OracleDataReader** для доступа к данным и используются несколько структур **OracleType** для вывода данных.</span><span class="sxs-lookup"><span data-stu-id="c5309-114">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5309-115">См. также</span><span class="sxs-lookup"><span data-stu-id="c5309-115">See also</span></span>

- [<span data-ttu-id="c5309-116">Oracle и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5309-116">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="c5309-117">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5309-117">ADO.NET Overview</span></span>](ado-net-overview.md)
