---
description: 'Дополнительные сведения: Поиск строк'
title: Поиск строк
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: bf4752255945d5bbc0dd5551cd6e84c98fd78c3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652475"
---
# <a name="finding-rows"></a><span data-ttu-id="32c06-103">Поиск строк</span><span class="sxs-lookup"><span data-stu-id="32c06-103">Finding Rows</span></span>

<span data-ttu-id="32c06-104">При помощи методов <xref:System.Data.DataView.Find%2A> и <xref:System.Data.DataView.FindRows%2A> объекта <xref:System.Data.DataView> можно производить поиск строк по значениям их ключей сортировки.</span><span class="sxs-lookup"><span data-stu-id="32c06-104">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="32c06-105">Регистр значений поиска в методах **Find** и **FindRows** определяется свойством **CaseSensitive** базового класса <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="32c06-105">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="32c06-106">Чтобы был возвращен результат, значения для поиска должны полностью совпадать со значениями ключей сортировки.</span><span class="sxs-lookup"><span data-stu-id="32c06-106">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="32c06-107">Метод **Find** возвращает целое число с индексом <xref:System.Data.DataRowView> , который соответствует условиям поиска.</span><span class="sxs-lookup"><span data-stu-id="32c06-107">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="32c06-108">Если критерию поиска соответствует более одной строки, возвращается только индекс первого соответствующего **DataRowView** .</span><span class="sxs-lookup"><span data-stu-id="32c06-108">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="32c06-109">Если совпадений не найдено, функция **Find** возвращает значение-1.</span><span class="sxs-lookup"><span data-stu-id="32c06-109">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="32c06-110">Чтобы вернуть результаты поиска, соответствующие нескольким строкам, используйте метод **FindRows** .</span><span class="sxs-lookup"><span data-stu-id="32c06-110">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="32c06-111">**FindRows** работает так же, как метод **Find** , за исключением того, что он возвращает массив **DataRowView** , который ссылается на все совпадающие строки в **объекте DataView**.</span><span class="sxs-lookup"><span data-stu-id="32c06-111">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="32c06-112">Если совпадений не найдено, массив **DataRowView** будет пустым.</span><span class="sxs-lookup"><span data-stu-id="32c06-112">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="32c06-113">Чтобы использовать методы **Find** или **FindRows** , необходимо указать порядок сортировки, задав для **апплидефаултсорт** **значение true** или воспользовавшись свойством **Sort** .</span><span class="sxs-lookup"><span data-stu-id="32c06-113">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="32c06-114">Если никакого порядка сортировки не задано, то формируется исключение.</span><span class="sxs-lookup"><span data-stu-id="32c06-114">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="32c06-115">Методы **Find** и **FindRows** принимают массив значений в качестве входных данных, длина которых совпадает с числом столбцов в порядке сортировки.</span><span class="sxs-lookup"><span data-stu-id="32c06-115">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="32c06-116">В случае сортировки в одном столбце можно передавать одно значение.</span><span class="sxs-lookup"><span data-stu-id="32c06-116">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="32c06-117">Массив объектов передается для порядков сортировки, содержащих несколько столбцов.</span><span class="sxs-lookup"><span data-stu-id="32c06-117">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="32c06-118">Обратите внимание, что при сортировке по нескольким столбцам значения в массиве объектов должны соответствовать порядку столбцов, указанных в свойстве **Sort** объекта **DataView**.</span><span class="sxs-lookup"><span data-stu-id="32c06-118">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="32c06-119">В следующем примере кода показан метод **Find** , вызываемый для **DataView** с одним порядком сортировки столбца.</span><span class="sxs-lookup"><span data-stu-id="32c06-119">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="32c06-120">Если свойство **Sort** указывает несколько столбцов, необходимо передать массив объектов со значениями поиска для каждого столбца в порядке, указанном свойством **Sort** , как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="32c06-120">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="32c06-121">См. также</span><span class="sxs-lookup"><span data-stu-id="32c06-121">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="32c06-122">Объекты DataView</span><span class="sxs-lookup"><span data-stu-id="32c06-122">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="32c06-123">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="32c06-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
