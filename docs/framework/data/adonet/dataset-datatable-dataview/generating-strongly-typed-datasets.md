---
description: 'Дополнительные сведения: создание строго типизированных наборов данных'
title: Создание строго типизированных наборов данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: c69aecc5a0a541c868dac3037c9dd0dbc3fe8383
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652436"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="14e5d-103">Создание строго типизированных наборов данных</span><span class="sxs-lookup"><span data-stu-id="14e5d-103">Generating Strongly Typed DataSets</span></span>

<span data-ttu-id="14e5d-104">Учитывая схему XML, которая соответствует стандарту языка определения схемы XML (XSD), можно создать строго типизированную <xref:System.Data.DataSet> программу с помощью средства XSD.exe, предоставляемого пакетом средств разработки программного обеспечения (SDK) для Windows.</span><span class="sxs-lookup"><span data-stu-id="14e5d-104">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="14e5d-105">(Чтобы создать схему XSD из таблиц базы данных, см <xref:System.Data.DataSet.WriteXmlSchema%2A> . статью или [Работа с DataSets в Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="14e5d-105">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="14e5d-106">В следующем коде показан синтаксис для создания **набора данных** с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="14e5d-106">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```console  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="14e5d-107">В этом синтаксисе `/d` директива указывает средству создать **набор данных**, а указывает, `/l:` какой язык следует использовать (например, C# или Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="14e5d-107">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="14e5d-108">Необязательная `/eld` директива указывает, что можно использовать LINQ to DataSet для запроса к созданному **набору данных.**</span><span class="sxs-lookup"><span data-stu-id="14e5d-108">The optional `/eld` directive specifies that you can use LINQ to DataSet to query against the generated **DataSet.**</span></span> <span data-ttu-id="14e5d-109">Данный параметр используется при указании параметра `/d`.</span><span class="sxs-lookup"><span data-stu-id="14e5d-109">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="14e5d-110">Дополнительные сведения см. в разделе [запросы к типизированным наборам данных](../querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="14e5d-110">For more information, see [Querying Typed DataSets](../querying-typed-datasets.md).</span></span> <span data-ttu-id="14e5d-111">Необязательная `/n:` директива указывает средству создавать пространство имен для **набора данных** с именем **кссдсчема. Namespace**.</span><span class="sxs-lookup"><span data-stu-id="14e5d-111">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="14e5d-112">Выходом команды является файл XSDSchemaFileName.cs, который можно скомпилировать и использовать в приложении ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="14e5d-112">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="14e5d-113">Созданный код можно скомпилировать в виде библиотеки или модуля.</span><span class="sxs-lookup"><span data-stu-id="14e5d-113">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="14e5d-114">В следующем коде показан синтаксис для компиляции созданного кода в виде библиотеки с помощью компилятора C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="14e5d-114">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```console  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="14e5d-115">Директива `/t:` служит для этого инструмента указанием по компиляции библиотеки, а директива `/r:` указывает зависимые библиотеки, которые необходимо скомпилировать.</span><span class="sxs-lookup"><span data-stu-id="14e5d-115">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="14e5d-116">Выходом команды является файл XSDSchemaFileName.dll, который можно передать компилятору при компилировании приложения ADO.NET с помощью директивы `/r:`.</span><span class="sxs-lookup"><span data-stu-id="14e5d-116">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="14e5d-117">В следующем коде показан синтаксис обеспечения доступа к пространству имен, переданному инструменту XSD.exe в приложении ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="14e5d-117">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="14e5d-118">В следующем примере кода используется типизированный **набор данных** с именем **кустомердатасет** для загрузки списка клиентов из базы данных **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="14e5d-118">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="14e5d-119">После загрузки данных с помощью метода **Fill** в примере выполняется циклический перебор каждого клиента в таблице **Customers** с помощью объекта типизированной **кустомерсров** (**DataRow**).</span><span class="sxs-lookup"><span data-stu-id="14e5d-119">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="14e5d-120">Это обеспечивает прямой доступ к столбцу **CustomerID** , в отличие от **датаколумнколлектион**.</span><span class="sxs-lookup"><span data-stu-id="14e5d-120">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 <span data-ttu-id="14e5d-121">Ниже приведена схема XML, используемая для примера.</span><span class="sxs-lookup"><span data-stu-id="14e5d-121">The following is the XML Schema used for the example:</span></span>
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14e5d-122">См. также</span><span class="sxs-lookup"><span data-stu-id="14e5d-122">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="14e5d-123">Типизированные наборы данных</span><span class="sxs-lookup"><span data-stu-id="14e5d-123">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="14e5d-124">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="14e5d-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="14e5d-125">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="14e5d-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
