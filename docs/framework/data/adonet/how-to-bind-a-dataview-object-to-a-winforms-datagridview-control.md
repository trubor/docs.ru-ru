---
description: Дополнительные сведения см. в статье как привязать объект DataView к элементу управления Windows Forms DataGridView
title: Практическое руководство. Связывание объекта DataView с элементом управления DataGridView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 59bc1a0f6b7b2b0d6da4fa6d88e06922d95c9f46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723911"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="330f1-103">Практическое руководство. Связывание объекта DataView с элементом управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="330f1-103">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>

<span data-ttu-id="330f1-104">Элемент управления <xref:System.Windows.Forms.DataGridView> предоставляет мощный и гибкий способ отображения данных в табличном формате.</span><span class="sxs-lookup"><span data-stu-id="330f1-104">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="330f1-105">Элемент управления <xref:System.Windows.Forms.DataGridView> поддерживает стандартную модель привязки данных Windows Forms, поэтому он выполняет привязку к <xref:System.Data.DataView> и другим различным источникам данных.</span><span class="sxs-lookup"><span data-stu-id="330f1-105">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="330f1-106">Однако в большинстве случаев выполняется привязка к компоненту <xref:System.Windows.Forms.BindingSource>, управляющему взаимодействием с источником данных.</span><span class="sxs-lookup"><span data-stu-id="330f1-106">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="330f1-107">Дополнительные сведения об <xref:System.Windows.Forms.DataGridView> элементе управления см. в разделе [Общие сведения о элементе управления DataGridView](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="330f1-107">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="330f1-108">Соединение элемента управления DataGridView с объектом DataView</span><span class="sxs-lookup"><span data-stu-id="330f1-108">To connect a DataGridView control to a DataView</span></span>  
  
1. <span data-ttu-id="330f1-109">Реализуйте метод, обрабатывающий получение данных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="330f1-109">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="330f1-110">В следующем примере реализован метод `GetData`, инициализирующий компонент <xref:System.Data.SqlClient.SqlDataAdapter> и использующий его для заполнения объекта <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="330f1-110">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="330f1-111">Убедитесь, что переменной `connectionString` присвоено значение, соответствующее базе данных.</span><span class="sxs-lookup"><span data-stu-id="330f1-111">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="330f1-112">Потребуется доступ к SQL Server с установленным образцом базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="330f1-112">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <span data-ttu-id="330f1-113">В обработчике событий <xref:System.Windows.Forms.Form.Load> формы привяжите элемент управления <xref:System.Windows.Forms.DataGridView> к компоненту <xref:System.Windows.Forms.BindingSource> и вызовите метод `GetData` для получения данных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="330f1-113">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="330f1-114">Объект <xref:System.Data.DataView> создается из LINQ to DataSet запроса к контакту <xref:System.Data.DataTable> и затем привязывается к <xref:System.Windows.Forms.BindingSource> компоненту.</span><span class="sxs-lookup"><span data-stu-id="330f1-114">The <xref:System.Data.DataView> is created from a LINQ to DataSet query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="330f1-115">См. также</span><span class="sxs-lookup"><span data-stu-id="330f1-115">See also</span></span>

- [<span data-ttu-id="330f1-116">Привязка данных и LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="330f1-116">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
