---
description: 'Дополнительные сведения о: дерево элементов модели программирования'
title: Программирование дерева элементов модели
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 8dfcab99bb5e32d202fe2bdc09d63d8b7da6e748
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741865"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="3e447-103">Программирование дерева элементов модели</span><span class="sxs-lookup"><span data-stu-id="3e447-103">Programming Model Item Tree</span></span>

<span data-ttu-id="3e447-104">В этом образце показано, как перемещаться по <xref:System.Activities.Presentation.Model.ModelItem> дереву с помощью декларативной привязки данных из древовидного представления Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="3e447-104">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="3e447-105">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="3e447-105">Sample Details</span></span>

 <span data-ttu-id="3e447-106"><xref:System.Activities.Presentation.Model.ModelItem>Дерево является абстракцией, используемой инфраструктурой Конструктор рабочих процессов Windows для предоставления данных об изменяемом базовом экземпляре.</span><span class="sxs-lookup"><span data-stu-id="3e447-106">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="3e447-107">На следующем рисунке показаны различные уровни инфраструктуры в конструктор рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="3e447-107">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![Схема, показывающая архитектуру конструктор рабочих процессов.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="3e447-109">Элемент <xref:System.Activities.Presentation.Model.ModelItem> состоит из указателя базового значения, а также коллекции объектов <xref:System.Activities.Presentation.Model.ModelProperty>.</span><span class="sxs-lookup"><span data-stu-id="3e447-109">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="3e447-110">Объект <xref:System.Activities.Presentation.Model.ModelProperty> в свою очередь включает данные, такие как имя и тип свойства, и указатель значения, который в свою очередь является еще одним элементом <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="3e447-110">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="3e447-111">Преобразователь значений используется для манипуляции некоторыми элементами <xref:System.Activities.Presentation.Model.ModelItem>, возвращаемыми свойством <xref:System.Activities.Presentation.Model.ModelProperty>, чтобы они правильно отображались в представлении дерева.</span><span class="sxs-lookup"><span data-stu-id="3e447-111">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="3e447-112">Далее в образце показано, как императивно программировать с использованием дерева <xref:System.Activities.Presentation.Model.ModelItem> при помощи императивных инструкций, в соответствии со следующим примером.</span><span class="sxs-lookup"><span data-stu-id="3e447-112">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="3e447-113">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="3e447-113">To use this sample</span></span>

1. <span data-ttu-id="3e447-114">Откройте решение Программингмоделитемтри. sln в Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="3e447-114">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="3e447-115">Создайте решение, выбрав пункт **построить решение** в меню **Сборка** .</span><span class="sxs-lookup"><span data-stu-id="3e447-115">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="3e447-116">Нажмите клавишу F5 для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="3e447-116">Press F5 to run the application.</span></span> <span data-ttu-id="3e447-117">Затем отображается форма WPF.</span><span class="sxs-lookup"><span data-stu-id="3e447-117">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="3e447-118">Нажмите кнопку **Загрузить WF** , чтобы загрузить <xref:System.Activities.Presentation.Model.ModelItem> и привязать его к представлению в виде дерева.</span><span class="sxs-lookup"><span data-stu-id="3e447-118">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="3e447-119">При нажатии кнопки " **изменить дерево элементов модели** " выполняется предыдущий код для добавления элемента в дерево и задания свойства.</span><span class="sxs-lookup"><span data-stu-id="3e447-119">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e447-120">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="3e447-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3e447-121">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="3e447-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3e447-122">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="3e447-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3e447-123">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3e447-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="3e447-124">См. также</span><span class="sxs-lookup"><span data-stu-id="3e447-124">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
