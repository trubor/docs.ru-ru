---
title: Практическое руководство. Отмена блока потока данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
ms.openlocfilehash: c0f184720849a0c21fdeda1de4543a2443d60674
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713357"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="7c295-102">Практическое руководство. Отмена блока потока данных</span><span class="sxs-lookup"><span data-stu-id="7c295-102">How to: Cancel a Dataflow Block</span></span>

<span data-ttu-id="7c295-103">В этом документе показано, как включить отмену в приложении.</span><span class="sxs-lookup"><span data-stu-id="7c295-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="7c295-104">В этом примере используется Windows Forms для отображения позиции активности рабочих элементов в конвейере потока данных, а также последствий отмены.</span><span class="sxs-lookup"><span data-stu-id="7c295-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="7c295-105">Создание приложения Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c295-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="7c295-106">Создайте проект **Приложение Windows Forms** на C# или Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7c295-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="7c295-107">На следующих этапах проекту дается название `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="7c295-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="7c295-108">В конструкторе форм главной формы Form1.cs (Form1.vb для Visual Basic) добавьте элемент управления <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="7c295-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="7c295-109">Добавьте элемент управления <xref:System.Windows.Forms.ToolStripButton> к элементу управления <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="7c295-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="7c295-110">Задайте свойству <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> значение <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, а свойству <xref:System.Windows.Forms.ToolStripItem.Text%2A> — **Добавить рабочие элементы**.</span><span class="sxs-lookup"><span data-stu-id="7c295-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="7c295-111">Добавьте второй элемент управления <xref:System.Windows.Forms.ToolStripButton> к элементу управления <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="7c295-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="7c295-112">Задайте свойству <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>значение <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, свойству <xref:System.Windows.Forms.ToolStripItem.Text%2A> значение **Отмена**, а свойству <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> — значение `False`.</span><span class="sxs-lookup"><span data-stu-id="7c295-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="7c295-113">Добавьте четыре объекта <xref:System.Windows.Forms.ToolStripProgressBar> в элемент управления <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="7c295-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="7c295-114">Создание конвейера потока данных</span><span class="sxs-lookup"><span data-stu-id="7c295-114">Creating the Dataflow Pipeline</span></span>  

 <span data-ttu-id="7c295-115">В этом разделе описано, как создать конвейер потока данных, который обрабатывает рабочие элементы и обновляет индикаторы выполнения.</span><span class="sxs-lookup"><span data-stu-id="7c295-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="7c295-116">Создание конвейера потока данных</span><span class="sxs-lookup"><span data-stu-id="7c295-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="7c295-117">В проекте добавьте ссылку на System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="7c295-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="7c295-118">Убедитесь, что Form1.cs (Form1.vb для Visual Basic) содержит следующие операторы `using` (`Imports` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7c295-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="7c295-119">Добавьте класс `WorkItem` как внутренний тип класса `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7c295-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="7c295-120">Добавьте в класс `Form1` следующие данные-члены.</span><span class="sxs-lookup"><span data-stu-id="7c295-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="7c295-121">Добавьте в класс `CreatePipeline` метод `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7c295-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="7c295-122">Поскольку блоки потоков данных `incrementProgress` и `decrementProgress` работают с интерфейсом пользователя, важно, чтобы эти действия происходили в потоке пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="7c295-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="7c295-123">Для этого в процессе создания каждый из этих объектов предоставляет объект <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, в котором свойству <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> задано значение <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7c295-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7c295-124">Метод <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> создает объект <xref:System.Threading.Tasks.TaskScheduler>, выполняющий работу в текущем контексте синхронизации.</span><span class="sxs-lookup"><span data-stu-id="7c295-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="7c295-125">Поскольку конструктор `Form1` вызывается из потока пользовательского интерфейса, действия для блоков потоков данных `incrementProgress` и `decrementProgress` также выполняются в потоке пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="7c295-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="7c295-126">В этом примере задается свойство <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> при создании частей конвейера.</span><span class="sxs-lookup"><span data-stu-id="7c295-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="7c295-127">Поскольку свойство <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> полностью отменяет выполнение блока потока данных, весь конвейер должен быть заново создан после того, как пользователь отменит операцию и затем захочет добавить нескольких рабочих элементов в конвейер.</span><span class="sxs-lookup"><span data-stu-id="7c295-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="7c295-128">Пример, демонстрирующий альтернативный способ отмены блока потока данных, чтобы другие работы могли выполняться после отмены операции, см. в разделе [Пошаговое руководство. Использование потока данных в приложении Windows Forms](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="7c295-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="7c295-129">Подключение конвейера потока данных к пользовательскому интерфейсу</span><span class="sxs-lookup"><span data-stu-id="7c295-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  

 <span data-ttu-id="7c295-130">В этом разделе описывается, как подключить конвейер потока данных к интерфейсу пользователя.</span><span class="sxs-lookup"><span data-stu-id="7c295-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="7c295-131">Как созданием конвейера, так и добавлением рабочих элементов в конвейере управляет обработчик событий для кнопки **Добавление рабочих элементов**.</span><span class="sxs-lookup"><span data-stu-id="7c295-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="7c295-132">Отмена инициируется кнопкой **Отмена**.</span><span class="sxs-lookup"><span data-stu-id="7c295-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="7c295-133">Когда пользователь нажимает какую-либо из этих кнопок, соответствующее действие выполняется асинхронным образом.</span><span class="sxs-lookup"><span data-stu-id="7c295-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="7c295-134">Подключение конвейера потока данных к пользовательскому интерфейсу</span><span class="sxs-lookup"><span data-stu-id="7c295-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="7c295-135">В конструкторе форм главной формы создайте обработчик событий для события <xref:System.Windows.Forms.ToolStripItem.Click> кнопки **Добавить рабочие элементы**.</span><span class="sxs-lookup"><span data-stu-id="7c295-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="7c295-136">Реализуйте событие <xref:System.Windows.Forms.ToolStripItem.Click> для кнопки **Добавить рабочие элементы**.</span><span class="sxs-lookup"><span data-stu-id="7c295-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="7c295-137">В конструкторе форм главной формы создайте обработчик событий для события <xref:System.Windows.Forms.ToolStripItem.Click> кнопки **Отмена**.</span><span class="sxs-lookup"><span data-stu-id="7c295-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="7c295-138">Реализуйте обработчик события <xref:System.Windows.Forms.ToolStripItem.Click> для кнопки **Отмена**.</span><span class="sxs-lookup"><span data-stu-id="7c295-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="7c295-139">Пример</span><span class="sxs-lookup"><span data-stu-id="7c295-139">Example</span></span>  

 <span data-ttu-id="7c295-140">В следующем примере приведен полный код Form1.cs (Form1.vb для Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7c295-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="7c295-141">Ниже показано запущенное приложение.</span><span class="sxs-lookup"><span data-stu-id="7c295-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="7c295-142">![Приложение Windows Forms](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="7c295-142">![The Windows Forms Application](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="7c295-143">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7c295-143">See also</span></span>

- [<span data-ttu-id="7c295-144">Поток данных</span><span class="sxs-lookup"><span data-stu-id="7c295-144">Dataflow</span></span>](dataflow-task-parallel-library.md)
