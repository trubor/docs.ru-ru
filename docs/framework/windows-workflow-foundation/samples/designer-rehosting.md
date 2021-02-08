---
description: 'Дополнительные сведения: повторное размещение конструктора'
title: Повторное размещение конструктора
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 84401ba7cfc2b5515a9dcfda36289893e55660e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792535"
---
# <a name="designer-rehosting"></a><span data-ttu-id="18f67-103">Повторное размещение конструктора</span><span class="sxs-lookup"><span data-stu-id="18f67-103">Designer Rehosting</span></span>

<span data-ttu-id="18f67-104">Повторное размещение конструктора представляет собой обычный сценарий, предусматривающий размещение поля визуальной разработки рабочего процесса в пользовательском приложении.</span><span class="sxs-lookup"><span data-stu-id="18f67-104">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="18f67-105">Наиболее привычным приложением размещения является Visual Studio, однако в целом ряде сценариев может быть полезным отображение конструктора рабочих процессов в приложении.</span><span class="sxs-lookup"><span data-stu-id="18f67-105">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="18f67-106">Наблюдение за приложениями (позволяющее конечному пользователю визуально представить процесс, а также данные среды выполнения о процессе, такие как состояние, активное в настоящее время, агрегированные данные времени выполнения или другие сведения об экземпляре рабочего процесса).</span><span class="sxs-lookup"><span data-stu-id="18f67-106">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="18f67-107">Приложения, которые позволяют пользователю настраивать процесс с ограниченным набором действий.</span><span class="sxs-lookup"><span data-stu-id="18f67-107">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="18f67-108">Для поддержки этих типов приложений в составе платформы .NET Framework поставляется конструктор рабочих процессов, который может быть размещен в приложении WPF или в приложении WinForms с соответствующим кодом размещения WPF.</span><span class="sxs-lookup"><span data-stu-id="18f67-108">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="18f67-109">В этом примере демонстрируются следующее:</span><span class="sxs-lookup"><span data-stu-id="18f67-109">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="18f67-110">Повторное размещение конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="18f67-110">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="18f67-111">Кроме того, использование повторно размещенной области элементов и таблицы свойств.</span><span class="sxs-lookup"><span data-stu-id="18f67-111">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="18f67-112">Повторное размещение конструктора</span><span class="sxs-lookup"><span data-stu-id="18f67-112">Rehosting the designer</span></span>  

 <span data-ttu-id="18f67-113">Этот образец показывает, как создать макет WPF, содержащий конструктор, который можно видеть в следующем макете таблицы (код панели инструментов опущен в целях экономии места).</span><span class="sxs-lookup"><span data-stu-id="18f67-113">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="18f67-114">Обратите внимание на то, как именуются границы, которые содержат конструктор и таблицы свойств.</span><span class="sxs-lookup"><span data-stu-id="18f67-114">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="18f67-115">Затем в образце создается конструктор и связываются его первичные представления <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> и <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> с соответствующим контейнером в пользовательском интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="18f67-115">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="18f67-116">В следующем примере есть несколько дополнительных строк кода, которые заслуживают более подробного объяснения.</span><span class="sxs-lookup"><span data-stu-id="18f67-116">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="18f67-117"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A>Вызов необходим для связи конструкторов действий по умолчанию для действий, поставляемых с платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18f67-117">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="18f67-118"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> вызывается для передачи элемента WF, подлежащего редактированию.</span><span class="sxs-lookup"><span data-stu-id="18f67-118"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="18f67-119">Наконец, в область пользовательского интерфейса помещаются <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (первичное полотно) и <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (таблица свойств).</span><span class="sxs-lookup"><span data-stu-id="18f67-119">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="18f67-120">Использование повторно размещенной области инструментов</span><span class="sxs-lookup"><span data-stu-id="18f67-120">Using the rehosted toolbox</span></span>  

 <span data-ttu-id="18f67-121">В этом образце используется повторно размещенный элемент управления области инструментов декларативно в XAML.</span><span class="sxs-lookup"><span data-stu-id="18f67-121">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="18f67-122">Обратите внимание на то, что в коде каждый может передать некоторый тип в конструктор <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper>.</span><span class="sxs-lookup"><span data-stu-id="18f67-122">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a><span data-ttu-id="18f67-123">Использование образца</span><span class="sxs-lookup"><span data-stu-id="18f67-123">Using the sample</span></span>  
  
1. <span data-ttu-id="18f67-124">Откройте решение Десигнеррехостинг. sln в Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="18f67-124">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="18f67-125">Чтобы скомпилировать и запустить приложение, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="18f67-125">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="18f67-126">Приложение WPF начинается с повторно размещенного конструктора.</span><span class="sxs-lookup"><span data-stu-id="18f67-126">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="18f67-127">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="18f67-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="18f67-128">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="18f67-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="18f67-129">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="18f67-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18f67-130">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="18f67-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
