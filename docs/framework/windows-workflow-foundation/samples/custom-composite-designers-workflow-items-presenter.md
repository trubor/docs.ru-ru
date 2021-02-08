---
description: 'Дополнительные сведения: Пользовательские составные конструкторы — предоставление элементов рабочих процессов'
title: Пользовательские составные конструкторы - средство представления элементов рабочего процесса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 07970763e12eccd981370f1241642cc28f675824
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792587"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="e8db4-103">Пользовательские составные конструкторы - средство представления элементов рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="e8db4-103">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="e8db4-104"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> является типом ключа в модели программирования конструктора WF, позволяющим редактирование коллекции содержащихся элементов.</span><span class="sxs-lookup"><span data-stu-id="e8db4-104">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="e8db4-105">В этом образце показано, как построить конструктор действий, который предоставляет доступ к такой изменяемой коллекции.</span><span class="sxs-lookup"><span data-stu-id="e8db4-105">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="e8db4-106">В этом примере демонстрируются следующее:</span><span class="sxs-lookup"><span data-stu-id="e8db4-106">This sample demonstrates:</span></span>

- <span data-ttu-id="e8db4-107">Создание настраиваемого конструктора действий с <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8db4-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="e8db4-108">Создание конструктора действий с "свернутым" и "развернутым" представлением.</span><span class="sxs-lookup"><span data-stu-id="e8db4-108">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="e8db4-109">Переопределение конструктора по умолчанию в повторно размещенном приложении.</span><span class="sxs-lookup"><span data-stu-id="e8db4-109">Overriding a default designer in a rehosted application.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="e8db4-110">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="e8db4-110">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="e8db4-111">Откройте пример решения **усингворкфловитемспресентер. sln** для C# или для Visual Basic в Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="e8db4-111">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for Visual Basic in Visual Studio 2010.</span></span>

2. <span data-ttu-id="e8db4-112">Выполните сборку и запуск решения.</span><span class="sxs-lookup"><span data-stu-id="e8db4-112">Build and run the solution.</span></span>

   <span data-ttu-id="e8db4-113">Откроется переразмещенное приложение конструктора рабочих процессов, и вы можете перетаскивать действия на холст.</span><span class="sxs-lookup"><span data-stu-id="e8db4-113">A rehosted workflow designer application opens, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="e8db4-114">Описание образца</span><span class="sxs-lookup"><span data-stu-id="e8db4-114">Sample Highlights</span></span>

<span data-ttu-id="e8db4-115">Код для этого образца показывает следующее.</span><span class="sxs-lookup"><span data-stu-id="e8db4-115">The code for this sample shows the following:</span></span>

- <span data-ttu-id="e8db4-116">Действие, для которого построен конструктор: `Parallel`</span><span class="sxs-lookup"><span data-stu-id="e8db4-116">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="e8db4-117">Создание настраиваемого конструктора действий с <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8db4-117">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e8db4-118">Некоторые замечания.</span><span class="sxs-lookup"><span data-stu-id="e8db4-118">A few things to point out:</span></span>

  - <span data-ttu-id="e8db4-119">Обратите внимание на использование привязки данных WPF для привязки к `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="e8db4-119">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="e8db4-120">`ModelItem` - свойство `WorkflowElementDesigner`, которое относится к базовому объекту, для которого используется конструктор, в данном случае - `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="e8db4-120">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="e8db4-121">Шаблон <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> может использоваться для указания видимого изображения, отображаемого между отдельными элементами коллекции.</span><span class="sxs-lookup"><span data-stu-id="e8db4-121">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="e8db4-122"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> является шаблоном, который может быть предоставлен для определения макета элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="e8db4-122"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="e8db4-123">В данном случае используется горизонтальный элемент StackPanel.</span><span class="sxs-lookup"><span data-stu-id="e8db4-123">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="e8db4-124">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="e8db4-124">This following example code shows this.</span></span>

  ```xaml
  <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                Items="{Binding Path=ModelItem.Branches}">
      <sad:WorkflowItemsPresenter.SpacerTemplate>
        <DataTemplate>
          <Ellipse Width="10" Height="10" Fill="Black"/>
        </DataTemplate>
      </sad:WorkflowItemsPresenter.SpacerTemplate>
      <sad:WorkflowItemsPresenter.ItemsPanel>
        <ItemsPanelTemplate>
          <StackPanel Orientation="Horizontal"/>
        </ItemsPanelTemplate>
      </sad:WorkflowItemsPresenter.ItemsPanel>
    </sad:WorkflowItemsPresenter>
  ```

- <span data-ttu-id="e8db4-125">Выполнение связи объекта `DesignerAttribute` с типом `Parallel`, а затем вывод указанных атрибутов.</span><span class="sxs-lookup"><span data-stu-id="e8db4-125">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="e8db4-126">Сначала зарегистрируйте все конструкторы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e8db4-126">First, register all of the default designers.</span></span>

    <span data-ttu-id="e8db4-127">Ниже приведен пример кода.</span><span class="sxs-lookup"><span data-stu-id="e8db4-127">The following is the code example.</span></span>

    ```csharp
    // register metadata
    (new DesignerMetadata()).Register();
    RegisterCustomMetadata();
    ```

    ```vb
    ' register metadata
    Dim metadata = New DesignerMetadata()
    metadata.Register()
    ' register custom metadata
    RegisterCustomMetadata()
    ```

  - <span data-ttu-id="e8db4-128">Далее переопределите параллель в методе `RegisterCustomMetadata`.</span><span class="sxs-lookup"><span data-stu-id="e8db4-128">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="e8db4-129">В следующем коде это показано на языках C# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e8db4-129">The following code shows this in C# and Visual Basic.</span></span>

    ```csharp
    void RegisterCustomMetadata()
    {
          AttributeTableBuilder builder = new AttributeTableBuilder();
          builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
          MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

    ```vb
    Sub RegisterCustomMetadata()
       Dim builder As New AttributeTableBuilder()
       builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))
       MetadataStore.AddAttributeTable(builder.CreateTable())
    End Sub
    ```

- <span data-ttu-id="e8db4-130">Наконец, обратите внимание на использование различных шаблонов данных и триггеров для выбора соответствующего шаблона на основании свойства `IsRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="e8db4-130">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="e8db4-131">Ниже приведен пример кода.</span><span class="sxs-lookup"><span data-stu-id="e8db4-131">The following is the code example.</span></span>

  ```xaml
  <sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"
      xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">
    <sad:ActivityDesigner.Resources>
      <DataTemplate x:Key="Expanded">
        <StackPanel>
          <TextBlock>This is the Expanded View</TextBlock>
          <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                      Items="{Binding Path=ModelItem.Branches}">
            <sad:WorkflowItemsPresenter.SpacerTemplate>
              <DataTemplate>
                <Ellipse Width="10" Height="10" Fill="Black"/>
              </DataTemplate>
            </sad:WorkflowItemsPresenter.SpacerTemplate>
            <sad:WorkflowItemsPresenter.ItemsPanel>
              <ItemsPanelTemplate>
                <StackPanel Orientation="Horizontal"/>
              </ItemsPanelTemplate>
            </sad:WorkflowItemsPresenter.ItemsPanel>
          </sad:WorkflowItemsPresenter>
        </StackPanel>
      </DataTemplate>
      <DataTemplate x:Key="Collapsed">
        <TextBlock>This is the Collapsed View</TextBlock>
      </DataTemplate>
      <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
        <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
        <Style.Triggers>
          <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">
            <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
          </DataTrigger>
        </Style.Triggers>
      </Style>
    </sad: ActivityDesigner.Resources>
    <Grid>
      <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
    </Grid>
  </sad: ActivityDesigner>
  ```

> [!IMPORTANT]
> <span data-ttu-id="e8db4-132">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e8db4-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8db4-133">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e8db4-133">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e8db4-134">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="e8db4-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8db4-135">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="e8db4-135">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="e8db4-136">См. также</span><span class="sxs-lookup"><span data-stu-id="e8db4-136">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="e8db4-137">Разработка приложений с помощью конструктора рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="e8db4-137">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
