---
title: Практическое руководство. Указание планировщика задач в блоке потока данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
ms.openlocfilehash: b8c27c1ca61356b36183bb74b8360e41f5324d25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722444"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="2de86-102">Практическое руководство. Указание планировщика задач в блоке потока данных</span><span class="sxs-lookup"><span data-stu-id="2de86-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>

<span data-ttu-id="2de86-103">В этом документе приводятся способы привязки определенного планировщика задач при использовании потока данных в приложении.</span><span class="sxs-lookup"><span data-stu-id="2de86-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="2de86-104">В этом пример используется класс <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> в приложении Windows Forms для указания того, когда активна задача чтения и когда активна задача записи.</span><span class="sxs-lookup"><span data-stu-id="2de86-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="2de86-105">Здесь также используется метод <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>, чтобы позволить блоку потока данных выполняться в потоке пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="2de86-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="2de86-106">Создание приложения Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2de86-106">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="2de86-107">Создайте проект **Приложение Windows Forms** на Visual C# или Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2de86-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="2de86-108">На следующих этапах проекту дается название `WriterReadersWinForms`.</span><span class="sxs-lookup"><span data-stu-id="2de86-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2. <span data-ttu-id="2de86-109">В конструкторе форм главной формы Form1.cs (Form1.vb для Visual Basic) добавьте четыре элемента управления <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="2de86-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="2de86-110">Установите свойству <xref:System.Windows.Forms.Control.Text%2A> значение **Reader 1** для `checkBox1`, **Reader 2** для `checkBox2`, **Reader 3** для `checkBox3` и **Writer** для `checkBox4`.</span><span class="sxs-lookup"><span data-stu-id="2de86-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="2de86-111">Задайте свойству <xref:System.Windows.Forms.Control.Enabled%2A> каждого элемента управления значение `False`.</span><span class="sxs-lookup"><span data-stu-id="2de86-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3. <span data-ttu-id="2de86-112">Добавьте на форму элемент управления <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="2de86-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="2de86-113">Задайте для свойства <xref:System.Windows.Forms.Timer.Interval%2A> значение `2500`.</span><span class="sxs-lookup"><span data-stu-id="2de86-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="2de86-114">Добавление функциональных возможностей потока данных</span><span class="sxs-lookup"><span data-stu-id="2de86-114">Adding Dataflow Functionality</span></span>  

 <span data-ttu-id="2de86-115">В этом разделе описываются способы создания блоков потока данных, участвующих в приложении, и привязки каждого из них к планировщику задач.</span><span class="sxs-lookup"><span data-stu-id="2de86-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="2de86-116">Добавление функциональных возможностей потока данных в приложение</span><span class="sxs-lookup"><span data-stu-id="2de86-116">To Add Dataflow Functionality to the Application</span></span>  
  
1. <span data-ttu-id="2de86-117">В проекте добавьте ссылку на System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="2de86-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="2de86-118">Убедитесь, что Form1.cs (Form1.vb для Visual Basic) содержит следующие операторы `using` (`Imports` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2de86-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. <span data-ttu-id="2de86-119">Добавьте данные-член <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> в класс `Form1`.</span><span class="sxs-lookup"><span data-stu-id="2de86-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. <span data-ttu-id="2de86-120">В конструкторе `Form1` после вызова `InitializeComponent` создайте объект <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, который переключает состояние объектов <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="2de86-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. <span data-ttu-id="2de86-121">В конструкторе `Form1` создайте объект <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> и четыре объекта <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, по одному объекту <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> для каждого объекта <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="2de86-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="2de86-122">Для каждого объекта <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> укажите объект <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, у которого свойству <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> задано свойство <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> для читателей и <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> для средства записи.</span><span class="sxs-lookup"><span data-stu-id="2de86-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. <span data-ttu-id="2de86-123">В конструкторе `Form1` запустите объект <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="2de86-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. <span data-ttu-id="2de86-124">В конструкторе форм главной формы создайте обработчик событий для события таймера <xref:System.Windows.Forms.Timer.Tick>.</span><span class="sxs-lookup"><span data-stu-id="2de86-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8. <span data-ttu-id="2de86-125">Реализуйте событие <xref:System.Windows.Forms.Timer.Tick> для таймера.</span><span class="sxs-lookup"><span data-stu-id="2de86-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="2de86-126">Поскольку блок потока данных `toggleCheckBox` работает с интерфейсом пользователя, важно, чтобы это действие происходило в потоке пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="2de86-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="2de86-127">Для этого в процессе создания этот объект предоставляет объект <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, у которого свойству <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> задано значение <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2de86-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2de86-128">Метод <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> создает объект <xref:System.Threading.Tasks.TaskScheduler>, выполняющий работу в текущем контексте синхронизации.</span><span class="sxs-lookup"><span data-stu-id="2de86-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="2de86-129">Поскольку конструктор `Form1` вызывается из потока пользовательского интерфейса, действие для блока потока данных `toggleCheckBox` также выполняется в потоке пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="2de86-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="2de86-130">В этом примере также используется класс <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>, чтобы обеспечить возможность одновременной работы для нескольких блоков потока данных и монопольной работы еще одного блока потока данных в отношении остальных блоков потока данных, выполняемых в этом же объекте <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>.</span><span class="sxs-lookup"><span data-stu-id="2de86-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="2de86-131">Этот способ полезен, когда несколько блоков потока данных совместно используют ресурс, и некоторым требуется монопольный доступ к этому ресурсу, поскольку это исключают потребность вручную синхронизировать доступ к этому ресурсу.</span><span class="sxs-lookup"><span data-stu-id="2de86-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="2de86-132">Исключение ручной синхронизации может сделать код более эффективным.</span><span class="sxs-lookup"><span data-stu-id="2de86-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2de86-133">Пример</span><span class="sxs-lookup"><span data-stu-id="2de86-133">Example</span></span>  

 <span data-ttu-id="2de86-134">В следующем примере приведен полный код Form1.cs (Form1.vb для Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2de86-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="2de86-135">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2de86-135">See also</span></span>

- [<span data-ttu-id="2de86-136">Поток данных</span><span class="sxs-lookup"><span data-stu-id="2de86-136">Dataflow</span></span>](dataflow-task-parallel-library.md)
