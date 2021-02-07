---
description: 'Дополнительные сведения: использование набора данных из веб-службы XML'
title: Использование набора данных из веб-службы XML
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 3c9112d259d5a6450a968ba87b33c4072f6dc44c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725133"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="5bf61-103">Использование набора данных из веб-службы XML</span><span class="sxs-lookup"><span data-stu-id="5bf61-103">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="5bf61-104">Объект <xref:System.Data.DataSet> не имеет привязки к каким-либо источникам, что позволяет частично упростить передачу данных через Интернет.</span><span class="sxs-lookup"><span data-stu-id="5bf61-104">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="5bf61-105">**Набор данных** является сериализуемым в том, что он может быть указан в качестве входных данных или выходных данных из веб-служб XML без дополнительного программирования, необходимого для потоковой передачи содержимого **набора данных** из веб-службы XML в клиент и обратно.</span><span class="sxs-lookup"><span data-stu-id="5bf61-105">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="5bf61-106">**Набор данных** неявно преобразуется в XML-поток с помощью формата DiffGram, передается по сети, а затем перестраивается из потока XML в качестве **набора данных** на стороне получения.</span><span class="sxs-lookup"><span data-stu-id="5bf61-106">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="5bf61-107">Это предоставляет простой и гибкий способ передачи и возврата реляционных данных с помощью веб-служб XML.</span><span class="sxs-lookup"><span data-stu-id="5bf61-107">This gives you a simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="5bf61-108">Дополнительные сведения о формате DiffGram см. в разделе [дельтами](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="5bf61-108">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="5bf61-109">В следующем примере показано, как создать веб-службу XML и клиент, которые используют **набор данных** для передачи реляционных данных (включая измененные данные) и разрешения всех обновлений обратно в исходный источник данных.</span><span class="sxs-lookup"><span data-stu-id="5bf61-109">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bf61-110">Передача `DataSet` или `DataTable` экземпляры в рамках вызовов веб-службы XML не являются безопасными, если входные данные не являются доверенными.</span><span class="sxs-lookup"><span data-stu-id="5bf61-110">Transmitting `DataSet` or `DataTable` instances as part of XML Web service calls is not safe if the input is not trusted.</span></span> <span data-ttu-id="5bf61-111">Дополнительные сведения см. в [статье Руководство по безопасности наборов данных и DataTable](security-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="5bf61-111">For more information, see [DataSet and DataTable security guidance](security-guidance.md).</span></span>
> <span data-ttu-id="5bf61-112">Также рекомендуется всегда учитывать последствия безопасности при создании веб-службы XML.</span><span class="sxs-lookup"><span data-stu-id="5bf61-112">We also recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="5bf61-113">Сведения о защите веб-службы XML см. в разделе [Защита веб-служб XML, созданных с помощью ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5bf61-113">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="5bf61-114">Создание веб-службы XML</span><span class="sxs-lookup"><span data-stu-id="5bf61-114">Create an XML web service</span></span>
  
1. <span data-ttu-id="5bf61-115">Создайте веб-службу XML.</span><span class="sxs-lookup"><span data-stu-id="5bf61-115">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="5bf61-116">В этом примере создается веб-служба XML, которая возвращает данные, в данном случае список клиентов из базы данных **Northwind** и получает **набор данных** с обновлениями данных, которые веб-служба XML разрешается обратно в исходный источник данных.</span><span class="sxs-lookup"><span data-stu-id="5bf61-116">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="5bf61-117">Веб-служба XML предоставляет два метода: **Customers** для возврата списка клиентов и **коде** для разрешения обновлений обратно в источник данных.</span><span class="sxs-lookup"><span data-stu-id="5bf61-117">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="5bf61-118">Веб-служба XML хранится в файле на веб-сервере DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="5bf61-118">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="5bf61-119">В следующем коде описано содержимое файла DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="5bf61-119">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     <span data-ttu-id="5bf61-120">В типичном сценарии метод **коде** будет написан для перехвата нарушений оптимистической блокировки.</span><span class="sxs-lookup"><span data-stu-id="5bf61-120">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="5bf61-121">Для простоты в данном примере это опущено.</span><span class="sxs-lookup"><span data-stu-id="5bf61-121">For simplicity, the example does not include this.</span></span> <span data-ttu-id="5bf61-122">Дополнительные сведения о оптимистичном параллелизме см. в разделе [Оптимистическая блокировка](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="5bf61-122">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="5bf61-123">Создайте посредник веб-службы XML.</span><span class="sxs-lookup"><span data-stu-id="5bf61-123">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="5bf61-124">Клиентам веб-службы XML необходим посредник SOAP, чтобы использовать предоставленные методы.</span><span class="sxs-lookup"><span data-stu-id="5bf61-124">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="5bf61-125">Этот посредник может быть создан с помощью среды Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5bf61-125">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="5bf61-126">Если задать веб-ссылку на существующую веб-службу из Visual Studio, все действия, описанные в этом шаге, будут производиться незаметно.</span><span class="sxs-lookup"><span data-stu-id="5bf61-126">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="5bf61-127">Если требуется создать класс посредника самостоятельно, читайте этот раздел далее.</span><span class="sxs-lookup"><span data-stu-id="5bf61-127">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="5bf61-128">Однако в большинстве случаев достаточно создать класс посредника для клиентского приложения с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5bf61-128">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="5bf61-129">Посредник можно создать с помощью средства WSDL.</span><span class="sxs-lookup"><span data-stu-id="5bf61-129">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="5bf61-130">Например, если веб-служба XML предоставляется по URL-адресу `http://myserver/data/DataSetSample.asmx` , выполните следующую команду, чтобы создать Visual Basic прокси .NET с пространством имен **дссампле** и сохранить его в файле Sample. vb.</span><span class="sxs-lookup"><span data-stu-id="5bf61-130">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="5bf61-131">Чтобы создать посредник C# в файле sample.cs, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="5bf61-131">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="5bf61-132">После создания посредник можно будет скомпилировать как библиотеку и импортировать в клиент веб-службы XML.</span><span class="sxs-lookup"><span data-stu-id="5bf61-132">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="5bf61-133">Чтобы скомпилировать код посредника Visual Basic .NET, хранящийся в файле sample.vb, в файл sample.dll, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="5bf61-133">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="5bf61-134">Чтобы скомпилировать код посредника C#, хранящийся в файле sample.cs, в файл sample.dll, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="5bf61-134">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="5bf61-135">Создайте клиент веб-службы XML.</span><span class="sxs-lookup"><span data-stu-id="5bf61-135">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="5bf61-136">Если вы хотите, чтобы Visual Studio автоматически создавала класс прокси веб-службы, просто создайте клиентский проект, а в окне Обозреватель решений щелкните правой кнопкой мыши проект и выберите пункт **Добавить**  >  **ссылку на службу**.</span><span class="sxs-lookup"><span data-stu-id="5bf61-136">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="5bf61-137">В диалоговом окне **Добавление ссылки на службу** выберите **Дополнительно** и щелкните **Добавить веб-ссылку**.</span><span class="sxs-lookup"><span data-stu-id="5bf61-137">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="5bf61-138">Выберите веб-службу из списка доступных веб-служб (для этого может потребоваться указать адрес конечной точки веб-службы, если веб-служба недоступна в текущем решении или на текущем компьютере).</span><span class="sxs-lookup"><span data-stu-id="5bf61-138">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="5bf61-139">Если посредник веб-службы XML создается самостоятельно (как описано в предыдущем шаге), его можно импортировать в код клиента и воспользоваться методами веб-службы XML.</span><span class="sxs-lookup"><span data-stu-id="5bf61-139">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="5bf61-140">Следующий пример кода импортирует библиотеку прокси-сервера, вызывает **клиентов** для получения списка клиентов, добавляет нового клиента, а затем возвращает **набор данных** с обновлениями **коде**.</span><span class="sxs-lookup"><span data-stu-id="5bf61-140">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="5bf61-141">В примере передается **набор данных** , возвращаемый **DataSet. Changed** в **коде** , так как только измененные строки необходимо передать в **коде**.</span><span class="sxs-lookup"><span data-stu-id="5bf61-141">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="5bf61-142">**Коде** возвращает разрешенный **набор данных**, который затем можно **объединить** в существующий **набор данных** , чтобы включить в него разрешенные изменения и любые сведения об ошибках строк из обновления.</span><span class="sxs-lookup"><span data-stu-id="5bf61-142">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="5bf61-143">В следующем коде предполагается, что вы использовали Visual Studio для создания веб-ссылки и переименовали веб-ссылку на Дссампле в диалоговом окне " **Добавление веб-ссылки** ".</span><span class="sxs-lookup"><span data-stu-id="5bf61-143">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     <span data-ttu-id="5bf61-144">Если класс посредника создается самостоятельно, следует выполнить следующие дополнительные шаги.</span><span class="sxs-lookup"><span data-stu-id="5bf61-144">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="5bf61-145">Чтобы скомпилировать образец, предоставьте созданную библиотеку посредника (sample.dll) и связанные с ней библиотеки .NET.</span><span class="sxs-lookup"><span data-stu-id="5bf61-145">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="5bf61-146">Чтобы скомпилировать версию Visual Basic .NET образца, которая хранится в файле client.vb, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="5bf61-146">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="5bf61-147">Чтобы скомпилировать версию C# образца, которая хранится в файле client.cs, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="5bf61-147">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5bf61-148">См. также</span><span class="sxs-lookup"><span data-stu-id="5bf61-148">See also</span></span>

- [<span data-ttu-id="5bf61-149">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5bf61-149">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="5bf61-150">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="5bf61-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="5bf61-151">DataTables</span><span class="sxs-lookup"><span data-stu-id="5bf61-151">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="5bf61-152">Заполнение набора данных с помощью адаптера данных DataAdapter</span><span class="sxs-lookup"><span data-stu-id="5bf61-152">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="5bf61-153">Обновление источников данных с объектами DataAdapter</span><span class="sxs-lookup"><span data-stu-id="5bf61-153">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="5bf61-154">Параметры DataAdapter</span><span class="sxs-lookup"><span data-stu-id="5bf61-154">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="5bf61-155">[Инструмент языка описания веб-служб (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5bf61-155">[Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="5bf61-156">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5bf61-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
