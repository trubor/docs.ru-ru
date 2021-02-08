---
description: 'Дополнительные сведения: Пользовательские составные конструкторы — представление элементов рабочего процесса'
title: Пользовательские составные конструкторы - средство представления элементов рабочего процесса
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 20a3bddf7efd69b6138d6b8a5caae250aa377999
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787816"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="eca3f-103">Пользовательские составные конструкторы - средство представления элементов рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="eca3f-103">Custom Composite Designers - Workflow Item Presenter</span></span>

<span data-ttu-id="eca3f-104"><xref:System.Activities.Presentation.WorkflowItemPresenter>— Это тип ключа в модели программирования КОНСТРУКТОРА WF, который позволяет создавать "Drop Zone", где можно разместить произвольное действие.</span><span class="sxs-lookup"><span data-stu-id="eca3f-104">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="eca3f-105">В этом образце показано, как создать конструктор действий, который охватывает такую "область перетаскивания".</span><span class="sxs-lookup"><span data-stu-id="eca3f-105">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

<span data-ttu-id="eca3f-106">В этом примере демонстрируются следующее:</span><span class="sxs-lookup"><span data-stu-id="eca3f-106">This sample demonstrates:</span></span>

- <span data-ttu-id="eca3f-107">Создание настраиваемого конструктора действий с <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="eca3f-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="eca3f-108">Регистрация пользовательского конструктора с использованием хранилища метаданных.</span><span class="sxs-lookup"><span data-stu-id="eca3f-108">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="eca3f-109">Программирование повторно размещенной области элементов декларативно и принудительно.</span><span class="sxs-lookup"><span data-stu-id="eca3f-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="eca3f-110">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="eca3f-110">Sample Details</span></span>

<span data-ttu-id="eca3f-111">Код для этого образца показывает следующее:</span><span class="sxs-lookup"><span data-stu-id="eca3f-111">The code for this sample shows:</span></span>

- <span data-ttu-id="eca3f-112">Для класса `SimpleNativeActivity` создается конструктор пользовательских действий.</span><span class="sxs-lookup"><span data-stu-id="eca3f-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="eca3f-113">Создание настраиваемого конструктора действий с <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="eca3f-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 <span data-ttu-id="eca3f-114">Обратите внимание на использование привязки данных WPF для привязки к `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="eca3f-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="eca3f-115">`ModelItem` — Это свойство <xref:System.Activities.Presentation.ActivityDesigner> , которое ссылается на базовый объект, для которого используется конструктор, в данном случае **симпленативеактивити**.</span><span class="sxs-lookup"><span data-stu-id="eca3f-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="eca3f-116">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="eca3f-116">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="eca3f-117">Откройте решение в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eca3f-117">Open the solution in Visual Studio.</span></span>

2. <span data-ttu-id="eca3f-118">Нажмите клавишу **F5** , чтобы скомпилировать и запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="eca3f-118">Press **F5** to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eca3f-119">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="eca3f-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eca3f-120">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="eca3f-120">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="eca3f-121">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="eca3f-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eca3f-122">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="eca3f-122">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`

## <a name="see-also"></a><span data-ttu-id="eca3f-123">См. также</span><span class="sxs-lookup"><span data-stu-id="eca3f-123">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="eca3f-124">Разработка приложений с помощью конструктора рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="eca3f-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
