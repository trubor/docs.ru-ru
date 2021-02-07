---
description: Дополнительные сведения о синхронизации наборов данных и XmlDataDocument
title: Синхронизация набора данных и XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: c3bb1af305dfc319cb2c4783f4e4edc108e9d737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739564"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="c7df9-103">Синхронизация набора данных и XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="c7df9-103">DataSet and XmlDataDocument Synchronization</span></span>

<span data-ttu-id="c7df9-104">ADO.NET <xref:System.Data.DataSet> обеспечивает реляционное представление данных.</span><span class="sxs-lookup"><span data-stu-id="c7df9-104">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="c7df9-105">Для доступа к иерархическим данным можно использовать классы XML, доступные на платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7df9-105">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="c7df9-106">Исторически эти два представления данных использовались раздельно.</span><span class="sxs-lookup"><span data-stu-id="c7df9-106">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="c7df9-107">Однако платформа .NET Framework обеспечивает синхронный доступ в режиме реального времени к реляционным и иерархическим представлениям данных через объект **DataSet** и <xref:System.Xml.XmlDataDocument> объект соответственно.</span><span class="sxs-lookup"><span data-stu-id="c7df9-107">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="c7df9-108">Если **набор данных** синхронизирован с **XmlDataDocument**, то оба объекта работают с одним набором данных.</span><span class="sxs-lookup"><span data-stu-id="c7df9-108">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="c7df9-109">Это означает, что если в **набор данных** внесено изменение, это изменение будет отражено в **объекте XmlDataDocument** и наоборот.</span><span class="sxs-lookup"><span data-stu-id="c7df9-109">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="c7df9-110">Связь между **набором данных** и объектом **XmlDataDocument** создает большую гибкость, позволяя одному приложению, использование одного набора данных для доступа ко всему набору служб, построенных на основе **набора данных** (например, веб-форм и Windows Forms элементов управления и конструкторов Visual Studio .NET), а также набора служб XML, включая язык XSL, преобразования XSL (XSLT) и язык XML Path (XPath).</span><span class="sxs-lookup"><span data-stu-id="c7df9-110">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="c7df9-111">Не обязательно выбирать конкретный набор служб для приложения. Доступны оба.</span><span class="sxs-lookup"><span data-stu-id="c7df9-111">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="c7df9-112">Существует несколько способов синхронизации **набора данных** с **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-112">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="c7df9-113">Можно сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="c7df9-113">You can:</span></span>  
  
- <span data-ttu-id="c7df9-114">Заполните **набор данных** схемой (то есть реляционной структурой) и данными, а затем синхронизируйте его с новым **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-114">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="c7df9-115">Это обеспечивает иерархическое представление существующих реляционных данных.</span><span class="sxs-lookup"><span data-stu-id="c7df9-115">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="c7df9-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="c7df9-116">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
- <span data-ttu-id="c7df9-117">Заполнить **набор данных** только схемой (например, строго типизированным **набором данных**), синхронизировать его с **XmlDataDocument**, а затем загрузить **XmlDataDocument** из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="c7df9-117">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="c7df9-118">Это обеспечивает реляционное представление существующих иерархических данных.</span><span class="sxs-lookup"><span data-stu-id="c7df9-118">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="c7df9-119">Имена таблиц и столбцов в схеме **набора данных** должны совпадать с именами XML-элементов, с которыми они должны быть синхронизированы.</span><span class="sxs-lookup"><span data-stu-id="c7df9-119">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="c7df9-120">Это соответствие с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="c7df9-120">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="c7df9-121">Обратите внимание, что схема **набора данных** должна соответствовать только тем XML-элементам, которые необходимо предоставить в реляционном представлении.</span><span class="sxs-lookup"><span data-stu-id="c7df9-121">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="c7df9-122">Таким образом, может существовать очень большой XML-документ и очень малое реляционное «окно» для этого документа.</span><span class="sxs-lookup"><span data-stu-id="c7df9-122">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="c7df9-123">Объект **XmlDataDocument** сохраняет весь XML-документ, несмотря на то, что **набор данных** предоставляет только небольшую часть.</span><span class="sxs-lookup"><span data-stu-id="c7df9-123">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="c7df9-124">(Подробный пример см. в разделе [синхронизация набора данных с XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="c7df9-124">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="c7df9-125">В следующем примере кода показаны шаги для создания **набора данных** и заполнения его схемы, а затем выполняется его синхронизация с **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-125">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="c7df9-126">Обратите внимание, что схема **набора данных** должна соответствовать только элементам объекта **XmlDataDocument** , которые необходимо предоставить с помощью **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-126">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="c7df9-127">Невозможно загрузить объект **XmlDataDocument** , если он синхронизирован с **набором** данных, содержащим данные.</span><span class="sxs-lookup"><span data-stu-id="c7df9-127">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="c7df9-128">В таком случае возникнет исключение.</span><span class="sxs-lookup"><span data-stu-id="c7df9-128">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="c7df9-129">Создайте новый объект **XmlDataDocument** и загрузите его из XML-документа, а затем получите доступ к реляционному представлению данных с помощью свойства **DataSet** объекта **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-129">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="c7df9-130">Необходимо задать схему **набора данных** , прежде чем можно будет просматривать любые данные в **объекте XmlDataDocument** с помощью **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-130">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="c7df9-131">Имена таблиц и столбцов в схеме **набора данных** опять же должны совпадать с именами XML-элементов, с которыми они должны быть синхронизированы.</span><span class="sxs-lookup"><span data-stu-id="c7df9-131">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="c7df9-132">Это соответствие с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="c7df9-132">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="c7df9-133">В следующем примере кода показано, как получить доступ к реляционному представлению данных в **объекте XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-133">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="c7df9-134">Другое преимущество синхронизации **XmlDataDocument** с **набором данных** заключается в том, что сохраняется достоверность XML-документа.</span><span class="sxs-lookup"><span data-stu-id="c7df9-134">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="c7df9-135">Если **набор данных** заполняется из XML-документа с помощью метода **ReadXml**, то при записи данных обратно в виде XML-документа с помощью метода **WriteXml** он может значительно отличаться от исходного XML-документа.</span><span class="sxs-lookup"><span data-stu-id="c7df9-135">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="c7df9-136">Это обусловлено тем, что **набор данных** не поддерживает форматирование, например, пробелы или иерархические данные, например порядок элементов, из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="c7df9-136">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="c7df9-137">**Набор данных** также не содержит элементов из XML-документа, которые были пропущены, так как они не соответствуют схеме **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-137">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="c7df9-138">Синхронизация объекта **XmlDataDocument** с **набором данных** позволяет поддерживать форматирование и иерархическую структуру элементов исходного XML-документа в **объекте XmlDataDocument**, а **набор** данных содержит только данные и сведения о схеме, соответствующие **набору данных**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-138">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="c7df9-139">При синхронизации **набора данных** с **XmlDataDocument** результаты могут различаться в зависимости от того, <xref:System.Data.DataRelation> являются ли объекты вложенными.</span><span class="sxs-lookup"><span data-stu-id="c7df9-139">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="c7df9-140">Дополнительные сведения см. в разделе [вложенность связей](nesting-datarelations.md)данных.</span><span class="sxs-lookup"><span data-stu-id="c7df9-140">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7df9-141">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="c7df9-141">In This Section</span></span>  

 [<span data-ttu-id="c7df9-142">Синхронизация набора данных с XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="c7df9-142">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="c7df9-143">Демонстрирует синхронизацию строго типизированного **набора данных** с минимальной схемой с помощью **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-143">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="c7df9-144">Выполнение запроса XPath к набору данных</span><span class="sxs-lookup"><span data-stu-id="c7df9-144">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="c7df9-145">Демонстрирует выполнение запроса XPath к содержимому **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-145">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="c7df9-146">Применение преобразования XSLT к набору данных</span><span class="sxs-lookup"><span data-stu-id="c7df9-146">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="c7df9-147">Демонстрирует применение преобразования XSLT к содержимому **набора данных**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-147">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7df9-148">См. также</span><span class="sxs-lookup"><span data-stu-id="c7df9-148">Related Sections</span></span>  

 [<span data-ttu-id="c7df9-149">Использование XML в наборах данных</span><span class="sxs-lookup"><span data-stu-id="c7df9-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="c7df9-150">Описывает взаимодействие **набора** данных с XML в качестве источника данных, включая загрузку и сохранение содержимого **набора данных** в виде XML-данных.</span><span class="sxs-lookup"><span data-stu-id="c7df9-150">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="c7df9-151">Вложение отношений DataRelation</span><span class="sxs-lookup"><span data-stu-id="c7df9-151">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="c7df9-152">Описывает важность вложенных объектов **DataRelation** , когда представляет содержимое **набора** данных в виде XML-данных, и описывает создание этих связей.</span><span class="sxs-lookup"><span data-stu-id="c7df9-152">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="c7df9-153">Наборы данных, таблицы данных и объекты DataView</span><span class="sxs-lookup"><span data-stu-id="c7df9-153">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="c7df9-154">Описывает **набор данных** и способ его использования для управления данными приложения и взаимодействия с источниками данных, включая реляционные базы данных и XML.</span><span class="sxs-lookup"><span data-stu-id="c7df9-154">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="c7df9-155">Содержит справочные сведения о классе **XmlDataDocument** .</span><span class="sxs-lookup"><span data-stu-id="c7df9-155">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7df9-156">См. также</span><span class="sxs-lookup"><span data-stu-id="c7df9-156">See also</span></span>

- [<span data-ttu-id="c7df9-157">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c7df9-157">ADO.NET Overview</span></span>](../ado-net-overview.md)
