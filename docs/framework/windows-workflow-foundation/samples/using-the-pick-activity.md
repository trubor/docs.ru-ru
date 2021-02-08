---
description: 'Дополнительные сведения о: использование действия "скомплектовать"'
title: Использование действия Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 3c7a96c6250db8b9301dfeba858568d5638a29f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787751"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="8ce21-103">Использование действия Pick</span><span class="sxs-lookup"><span data-stu-id="8ce21-103">Using the Pick Activity</span></span>

<span data-ttu-id="8ce21-104">Этот образец демонстрирует применение действия <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="8ce21-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="8ce21-105">Действие <xref:System.Activities.Statements.Pick> обеспечивает моделирование потока управления на основе событий.</span><span class="sxs-lookup"><span data-stu-id="8ce21-105">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="8ce21-106">Поведение действия аналогично поведению оператора C# `switch`, выполняющего только одну из ветвей оператора `switch`.</span><span class="sxs-lookup"><span data-stu-id="8ce21-106">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="8ce21-107">В отличие от оператора `switch`, который выполняет ветвь в зависимости от значения, действие <xref:System.Activities.Statements.Pick> выполняет ветвь в зависимости от того, как было завершено действие.</span><span class="sxs-lookup"><span data-stu-id="8ce21-107">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="8ce21-108">Этот образец предлагает пользователю ввести свое имя в строке консоли за отведенный для этого период времени.</span><span class="sxs-lookup"><span data-stu-id="8ce21-108">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="8ce21-109">Действие <xref:System.Activities.Statements.Pick> в образце имеет две ветви, которые выполняются или не выполняются в зависимости от того, ввел или не ввел пользователь свое имя за отведенные для этого 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="8ce21-109">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="8ce21-110">Если пользователь успеет ввести имя в течение 5 секунд, будет выполнена первая ветвь, содержащая пользовательское действие `ReadLine`. В противном случае будет выполнена другая ветвь, содержащая действие <xref:System.Activities.Statements.Delay>.</span><span class="sxs-lookup"><span data-stu-id="8ce21-110">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="8ce21-111">После ввода в консоли имени пользователя это имя будет выведено на экран консоли.</span><span class="sxs-lookup"><span data-stu-id="8ce21-111">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="8ce21-112">Если в течение 5 секунд ввод не был осуществлен, время ожидания операции истечет и операция будет завершена.</span><span class="sxs-lookup"><span data-stu-id="8ce21-112">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8ce21-113">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="8ce21-113">Demonstrates</span></span>

 <span data-ttu-id="8ce21-114">Действие <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="8ce21-114"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="8ce21-115">Разговор</span><span class="sxs-lookup"><span data-stu-id="8ce21-115">Discussion</span></span>

 <span data-ttu-id="8ce21-116">В этом образце приведены образцы рабочего процесса, создаваемого в конструкторе, и кодированного рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="8ce21-116">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="8ce21-117">Рабочий процесс конструктора в версии примера конструктора демонстрируется создание рабочего процесса в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="8ce21-117">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="8ce21-118">Включаются следующие файлы.</span><span class="sxs-lookup"><span data-stu-id="8ce21-118">The following files are included:</span></span>

- <span data-ttu-id="8ce21-119">Program.cs: содержит функцию `Main`, выполняющую образец рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="8ce21-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="8ce21-120">ReadString.cs: настраиваемое действие, считывающее входные данные с консоли.</span><span class="sxs-lookup"><span data-stu-id="8ce21-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="8ce21-121">Sequence1.xaml: рабочий процесс, созданный с помощью конструктора, использующего действие Pick.</span><span class="sxs-lookup"><span data-stu-id="8ce21-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="8ce21-122">Закодированный рабочий процесс в кодированной версии примера показано, как создать рабочий процесс в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="8ce21-122">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="8ce21-123">Включаются следующие файлы.</span><span class="sxs-lookup"><span data-stu-id="8ce21-123">The following files are included:</span></span>

- <span data-ttu-id="8ce21-124">Program.cs: содержит функцию `Main`, выполняющую образец рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="8ce21-124">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="8ce21-125">ReadString.cs: настраиваемое действие, считывающее входные данные с консоли.</span><span class="sxs-lookup"><span data-stu-id="8ce21-125">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="8ce21-126">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="8ce21-126">To use this sample</span></span>

1. <span data-ttu-id="8ce21-127">В Visual Studio 2010 откройте файл решения скомплектовать. sln.</span><span class="sxs-lookup"><span data-stu-id="8ce21-127">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="8ce21-128">Для построения решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="8ce21-128">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="8ce21-129">Чтобы запустить решение, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="8ce21-129">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ce21-130">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8ce21-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8ce21-131">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="8ce21-131">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8ce21-132">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="8ce21-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8ce21-133">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="8ce21-133">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
