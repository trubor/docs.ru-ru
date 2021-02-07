---
description: Дополнительные сведения см. в статье как реализовать CopyToDataTable <T> , где универсальный тип T не является DataRow
title: Практическое руководство. Реализация CopyToDataTable<T>, где универсальный тип T не является объектом DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 742e4f0a4854cbb1a37a5401abc628cd4d239b26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723807"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="5d527-103">Практическое руководство. Реализация CopyToDataTable\<T>, где универсальный тип T не является объектом DataRow</span><span class="sxs-lookup"><span data-stu-id="5d527-103">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>

<span data-ttu-id="5d527-104">Объект <xref:System.Data.DataTable> часто используется для связывания данных.</span><span class="sxs-lookup"><span data-stu-id="5d527-104">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="5d527-105">Метод <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> принимает результаты запроса и копирует данные в <xref:System.Data.DataTable>, которую в дальнейшем можно использовать для привязки данных.</span><span class="sxs-lookup"><span data-stu-id="5d527-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="5d527-106">Однако методы <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> работают только с источником, реализующим интерфейс <xref:System.Collections.Generic.IEnumerable%601>, в котором общий параметр `T` принадлежит к типу <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="5d527-106">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="5d527-107">Хотя это и полезно, это не позволяет создавать таблицы из последовательности скалярных типов, из запросов, проецирующих анонимные типы, или из запросов, содержащих соединение таблиц.</span><span class="sxs-lookup"><span data-stu-id="5d527-107">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="5d527-108">В этом разделе описано применение пользовательских методов расширений `CopyToDataTable<T>`, принимающих общий параметр `T` типа, отличного от <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="5d527-108">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="5d527-109">Логика создания объекта <xref:System.Data.DataTable> из источника <xref:System.Collections.Generic.IEnumerable%601> содержится в классе `ObjectShredder<T>`, который затем помещается в два перегруженных метода расширений `CopyToDataTable<T>`.</span><span class="sxs-lookup"><span data-stu-id="5d527-109">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="5d527-110">Метод `Shred` класса `ObjectShredder<T>` возвращает заполненный объект <xref:System.Data.DataTable> и принимает три входных параметра: источник <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Data.DataTable> и перечисление <xref:System.Data.LoadOption>.</span><span class="sxs-lookup"><span data-stu-id="5d527-110">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="5d527-111">Исходная схема возвращенного объекта <xref:System.Data.DataTable> основана на схеме типа `T`.</span><span class="sxs-lookup"><span data-stu-id="5d527-111">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="5d527-112">Если в качестве входных данных используется существующая таблица, ее схема должна быть согласована со схемой типа `T`.</span><span class="sxs-lookup"><span data-stu-id="5d527-112">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="5d527-113">Каждое общее свойство и поле типа `T` в возвращенной таблице преобразуется в тип <xref:System.Data.DataColumn>.</span><span class="sxs-lookup"><span data-stu-id="5d527-113">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="5d527-114">Если исходная последовательность содержит тип, производный от `T`, то схема возвращенной таблицы расширяется дополнительными общими свойствами и полями.</span><span class="sxs-lookup"><span data-stu-id="5d527-114">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="5d527-115">Примеры использования пользовательских методов `CopyToDataTable<T>` см. в разделе [Создание таблицы данных из запроса](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5d527-115">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="5d527-116">Реализация пользовательских \<T> методов CopyToDataTable в приложении</span><span class="sxs-lookup"><span data-stu-id="5d527-116">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="5d527-117">Реализуйте класс `ObjectShredder<T>` для создания объекта <xref:System.Data.DataTable> из источника <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="5d527-117">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="5d527-118">В предыдущем примере предполагается, что свойства и поля объекта не допускают `DataColumn` значения NULL.</span><span class="sxs-lookup"><span data-stu-id="5d527-118">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="5d527-119">Чтобы обрабатывались свойства и поля с типами значений, допускающими значение null, используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="5d527-119">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="5d527-120">Реализуйте пользовательские методы расширений `CopyToDataTable<T>` в классе:</span><span class="sxs-lookup"><span data-stu-id="5d527-120">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="5d527-121">Добавьте в приложение класс `ObjectShredder<T>` и методы расширений `CopyToDataTable<T>`.</span><span class="sxs-lookup"><span data-stu-id="5d527-121">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="5d527-122">См. также</span><span class="sxs-lookup"><span data-stu-id="5d527-122">See also</span></span>

- [<span data-ttu-id="5d527-123">Создание DataTable из запроса</span><span class="sxs-lookup"><span data-stu-id="5d527-123">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="5d527-124">Руководство по программированию</span><span class="sxs-lookup"><span data-stu-id="5d527-124">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
