---
description: 'Дополнительные сведения о: задача 2. размещение конструктор рабочих процессов'
title: Задача 2. Размещение конструктора рабочих процессов
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 5a00c9db831575dfe7f6f2b6e041f18877c60118
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755204"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="7e350-103">Задача 2. Размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="7e350-103">Task 2: Host the Workflow Designer</span></span>

<span data-ttu-id="7e350-104">В этом разделе описывается процедура размещения экземпляра конструктор рабочих процессов Windows в приложении Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="7e350-104">This topic describes the procedure for hosting an instance of the Windows Workflow Designer in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="7e350-105">Процедура настраивает элемент управления **Grid** , содержащий конструктор, программно создает экземпляр <xref:System.Activities.Presentation.WorkflowDesigner> , содержащий действие по умолчанию <xref:System.Activities.Statements.Sequence> , регистрирует метаданные конструктора для обеспечения поддержки конструктора для всех встроенных действий и размещает конструктор рабочих процессов в приложении WPF.</span><span class="sxs-lookup"><span data-stu-id="7e350-105">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the Workflow Designer in the WPF application.</span></span>

## <a name="to-host-the-workflow-designer"></a><span data-ttu-id="7e350-106">Размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="7e350-106">To host the workflow designer</span></span>

1. <span data-ttu-id="7e350-107">Откройте проект Хостингаппликатион, созданный в [задаче 1: создание нового приложения Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="7e350-107">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>

2. <span data-ttu-id="7e350-108">Измените размер окна, чтобы упростить использование конструктор рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="7e350-108">Adjust the size of the window to make it easier to use the Workflow Designer.</span></span> <span data-ttu-id="7e350-109">Для этого выберите **MainWindow** в конструкторе, нажмите клавишу F4, чтобы открыть окно **свойства** , и в разделе **макет** установите для **ширины** значение 600, а для **высоты** — значение 350.</span><span class="sxs-lookup"><span data-stu-id="7e350-109">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>

3. <span data-ttu-id="7e350-110">Задайте имя сетки, выбрав Панель **сетки** в конструкторе (щелкните поле в **MainWindow**) и задайте для свойства **Name** в верхней части окна **Свойства** значение "grid1".</span><span class="sxs-lookup"><span data-stu-id="7e350-110">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>

4. <span data-ttu-id="7e350-111">В окне **Свойства** нажмите кнопку с многоточием (**...**) рядом со `ColumnDefinitions` свойством, чтобы открыть диалоговое окно **Редактор коллекции** .</span><span class="sxs-lookup"><span data-stu-id="7e350-111">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>

5. <span data-ttu-id="7e350-112">В диалоговом окне **Редактор коллекций** нажмите кнопку **Добавить** три раза, чтобы вставить три столбца в макет.</span><span class="sxs-lookup"><span data-stu-id="7e350-112">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="7e350-113">Первый столбец будет содержать **область элементов**, второй столбец будет размещать конструктор рабочих процессов, а третий столбец будет использоваться для инспектора свойств.</span><span class="sxs-lookup"><span data-stu-id="7e350-113">The first column will contain the **Toolbox**, the second column will host the Workflow Designer, and the third column will be used for the property inspector.</span></span>

6. <span data-ttu-id="7e350-114">Задайте `Width` для свойства среднего столбца значение 4 \*.</span><span class="sxs-lookup"><span data-stu-id="7e350-114">Set the `Width` property of the middle column to the value "4\*".</span></span>

7. <span data-ttu-id="7e350-115">Нажмите кнопку **OK**, чтобы сохранить изменения.</span><span class="sxs-lookup"><span data-stu-id="7e350-115">Click **OK** to save the changes.</span></span> <span data-ttu-id="7e350-116">В файл *MainWindow. XAML* добавляется следующий код XAML:</span><span class="sxs-lookup"><span data-stu-id="7e350-116">The following XAML is added to your *MainWindow.xaml* file:</span></span>

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. <span data-ttu-id="7e350-117">В **Обозреватель решений** щелкните правой кнопкой мыши файл *MainWindow. XAML* и выберите **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="7e350-117">In **Solution Explorer**, right-click *MainWindow.xaml* and select **View Code**.</span></span> <span data-ttu-id="7e350-118">Измените код, выполнив следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="7e350-118">Modify the code by following these steps:</span></span>

    1. <span data-ttu-id="7e350-119">Добавьте приведенные ниже пространства имен.</span><span class="sxs-lookup"><span data-stu-id="7e350-119">Add the following namespaces:</span></span>

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. <span data-ttu-id="7e350-120">Чтобы объявить поле закрытого члена для хранения экземпляра <xref:System.Activities.Presentation.WorkflowDesigner> , добавьте в класс следующий код `MainWindow` :</span><span class="sxs-lookup"><span data-stu-id="7e350-120">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class:</span></span>

        ```csharp
        public partial class MainWindow : Window
        {
            private WorkflowDesigner wd;

            public MainWindow()
            {
                InitializeComponent();
            }
        }
        ```

    3. <span data-ttu-id="7e350-121">Добавьте следующий метод `AddDesigner` в класс `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="7e350-121">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="7e350-122">Реализация создает экземпляр <xref:System.Activities.Presentation.WorkflowDesigner> , добавляет <xref:System.Activities.Statements.Sequence> к нему действие и помещает его в средний столбец **сетки** grid1.</span><span class="sxs-lookup"><span data-stu-id="7e350-122">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. <span data-ttu-id="7e350-123">Зарегистрируйте метаданные конструктора, чтобы добавить поддержку конструктора для всех встроенных действий.</span><span class="sxs-lookup"><span data-stu-id="7e350-123">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="7e350-124">Это позволяет удалять действия из панели элементов на исходное <xref:System.Activities.Statements.Sequence> действие в конструктор рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="7e350-124">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the Workflow Designer.</span></span> <span data-ttu-id="7e350-125">Для этого добавьте `RegisterMetadata` метод в `MainWindow` класс:</span><span class="sxs-lookup"><span data-stu-id="7e350-125">To do this, add the `RegisterMetadata` method to the `MainWindow` class:</span></span>

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        <span data-ttu-id="7e350-126">Дополнительные сведения о регистрации конструкторов действий см. [в разделе инструкции. Создание пользовательского конструктора действий](how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="7e350-126">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>

    5. <span data-ttu-id="7e350-127">В конструкторе класса `MainWindow` добавьте вызовы объявленных ранее методов для регистрации метаданных для поддержки конструктора и создания <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="7e350-127">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > <span data-ttu-id="7e350-128">Метод `RegisterMetadata` регистрирует метаданные конструктора встроенных действий, включая действие <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="7e350-128">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="7e350-129">Поскольку метод `AddDesigner` использует действие <xref:System.Activities.Statements.Sequence>, сначала необходимо вызвать метод `RegisterMetadata`.</span><span class="sxs-lookup"><span data-stu-id="7e350-129">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>

9. <span data-ttu-id="7e350-130">Нажмите клавишу <kbd>F5</kbd> , чтобы создать и запустить решение.</span><span class="sxs-lookup"><span data-stu-id="7e350-130">Press <kbd>F5</kbd> to build and run the solution.</span></span>

10. <span data-ttu-id="7e350-131">См. раздел [Задача 3. Создание панелей элементов и PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) , чтобы узнать, как добавить **панель элементов** и поддержку **PropertyGrid** в переразмещенный конструктор рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="7e350-131">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e350-132">См. также</span><span class="sxs-lookup"><span data-stu-id="7e350-132">See also</span></span>

- [<span data-ttu-id="7e350-133">Повторное размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="7e350-133">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="7e350-134">Задача 1. Создание нового приложения Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="7e350-134">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="7e350-135">Задача 3. Создание области элементов и сетки свойств</span><span class="sxs-lookup"><span data-stu-id="7e350-135">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
