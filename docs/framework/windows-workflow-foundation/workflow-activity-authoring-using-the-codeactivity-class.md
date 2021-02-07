---
description: Дополнительные сведения см. в статье Создание действий рабочего процесса с помощью класса CodeActivity.
title: Разработка действий рабочих процессов с помощью класса CodeActivity
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 393b6c586a88e876484f6888441d5bb82b4c0dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754918"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="10e29-103">Разработка действий рабочих процессов с помощью класса CodeActivity</span><span class="sxs-lookup"><span data-stu-id="10e29-103">Workflow Activity Authoring Using the CodeActivity Class</span></span>

<span data-ttu-id="10e29-104">Действия, созданные путем наследования от <xref:System.Activities.CodeActivity>, могут реализовывать базовое императивное поведение путем переопределения метода <xref:System.Activities.CodeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="10e29-104">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

## <a name="using-codeactivitycontext"></a><span data-ttu-id="10e29-105">Использование CodeActivityContext</span><span class="sxs-lookup"><span data-stu-id="10e29-105">Using CodeActivityContext</span></span>

 <span data-ttu-id="10e29-106">Доступ к функциям среды выполнения рабочего процесса можно получить из метода <xref:System.Activities.CodeActivity.Execute%2A> при помощи элементов параметра `context` типа <xref:System.Activities.CodeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="10e29-106">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="10e29-107">Функции, доступные посредством <xref:System.Activities.CodeActivityContext>:</span><span class="sxs-lookup"><span data-stu-id="10e29-107">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>

- <span data-ttu-id="10e29-108">Возврат и задание значений аргументов и переменных.</span><span class="sxs-lookup"><span data-stu-id="10e29-108">Getting and setting the values of variables and arguments.</span></span>

- <span data-ttu-id="10e29-109">Пользовательские функции отслеживания с использованием <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="10e29-109">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="10e29-110">Доступ к свойствам выполнения действия с помощью <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="10e29-110">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="10e29-111">Создание настраиваемого действия, которое наследуется от CodeActivity</span><span class="sxs-lookup"><span data-stu-id="10e29-111">To create a custom activity that inherits from CodeActivity</span></span>

1. <span data-ttu-id="10e29-112">Откройте Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="10e29-112">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="10e29-113">Выберите **файл**, **создать**, а затем **проект**.</span><span class="sxs-lookup"><span data-stu-id="10e29-113">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="10e29-114">Выберите **Рабочий процесс 4,0** в разделе **Visual C#** в окне **типы проектов** и выберите узел **v2010** .</span><span class="sxs-lookup"><span data-stu-id="10e29-114">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="10e29-115">В окне **шаблоны** выберите пункт **Библиотека действий** .</span><span class="sxs-lookup"><span data-stu-id="10e29-115">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="10e29-116">Задайте имя для нового проекта HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="10e29-116">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="10e29-117">Щелкните правой кнопкой мыши Activity1. XAML в проекте Хеллоактивити и выберите **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="10e29-117">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="10e29-118">Щелкните правой кнопкой мыши проект Хеллоактивити и выберите **Добавить** , а затем — **класс**.</span><span class="sxs-lookup"><span data-stu-id="10e29-118">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="10e29-119">Задайте имя для нового класса HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="10e29-119">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="10e29-120">В файле HelloActivity.cs добавьте следующие директивы `using`.</span><span class="sxs-lookup"><span data-stu-id="10e29-120">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="10e29-121">Сделайте так, чтобы новый класс наследовал от действия <xref:System.Activities.CodeActivity> путем добавления базового класса к объявлению класса.</span><span class="sxs-lookup"><span data-stu-id="10e29-121">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <span data-ttu-id="10e29-122">Добавьте функциональные возможности к классу путем добавления метода <xref:System.Activities.CodeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="10e29-122">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="10e29-123">Используйте объект <xref:System.Activities.CodeActivityContext> для создания записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="10e29-123">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
