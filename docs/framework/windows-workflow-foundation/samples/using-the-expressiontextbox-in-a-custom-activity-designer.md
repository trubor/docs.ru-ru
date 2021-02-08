---
description: 'Дополнительные сведения о: использование ExpressionTextBox в конструкторе настраиваемых действий'
title: Использование ExpressionTextBox в пользовательском конструкторе действия
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: c333832c2f955354233371c6572f8ae27e5d8643
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787764"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="117c3-103">Использование ExpressionTextBox в пользовательском конструкторе действия</span><span class="sxs-lookup"><span data-stu-id="117c3-103">Using the ExpressionTextBox in a Custom Activity Designer</span></span>

<span data-ttu-id="117c3-104">В этом образце показано, как использовать <xref:System.Activities.Presentation.View.ExpressionTextBox> в настраиваемом конструкторе действий.</span><span class="sxs-lookup"><span data-stu-id="117c3-104">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="117c3-105">Пользовательское действие `MultiAssign` присваивает два строковых значения двум строковым переменным.</span><span class="sxs-lookup"><span data-stu-id="117c3-105">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="117c3-106">Некоторые элементы управления <xref:System.Activities.Presentation.View.ExpressionTextBox> привязываются к аргументу <xref:System.Activities.InArgument>, а некоторые - к аргументу <xref:System.Activities.OutArgument>.</span><span class="sxs-lookup"><span data-stu-id="117c3-106">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="117c3-107">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="117c3-107">Sample details</span></span>

 <span data-ttu-id="117c3-108">`ArgumentToExpressionConverter` - это преобразователь типов, используемый для привязки выражений к аргументам.</span><span class="sxs-lookup"><span data-stu-id="117c3-108">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="117c3-109">Параметр `ConverterParameter` необходимо установить в соответствующее значение `In` или `Out`.</span><span class="sxs-lookup"><span data-stu-id="117c3-109">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="117c3-110">Тип `InOut` не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="117c3-110">`InOut` is not supported.</span></span>

 <span data-ttu-id="117c3-111">`UseLocationExpression`Атрибут используется в параметре `OutArgument` s, чтобы указать, что выражение должно быть выражением L-value ("левое значение" или "значение расположения").</span><span class="sxs-lookup"><span data-stu-id="117c3-111">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="117c3-112">В большинстве случаев левостороннее выражение является допустимым идентификатором Visual Basic, используемым для указания того, что возвращаемый аргумент `OutArgument` является переменной или именем аргумента.</span><span class="sxs-lookup"><span data-stu-id="117c3-112">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="117c3-113">В этом примере для атрибута `MaxLines` установлено значение 1, а значение атрибута `MinLines` не задано.</span><span class="sxs-lookup"><span data-stu-id="117c3-113">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="117c3-114">Это указывает, что текстовое поле <xref:System.Activities.Presentation.View.ExpressionTextBox> имеет фиксированный размер в одну строку независимо от объема текста, введенного пользователем.</span><span class="sxs-lookup"><span data-stu-id="117c3-114">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="117c3-115">Чтобы разрешить изменение размера текстового поля <xref:System.Activities.Presentation.View.ExpressionTextBox> в соответствии с объемом вводимых пользователем данных, задайте значение `MaxLines`, которое больше значения `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="117c3-115">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="117c3-116">Текстовое поле ExpressionTextBox может быть привязано только к аргументам и не может быть привязано к свойствам CLR.</span><span class="sxs-lookup"><span data-stu-id="117c3-116">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="117c3-117">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="117c3-117">To use this sample</span></span>

1. <span data-ttu-id="117c3-118">С помощью Visual Studio 2010 откройте файл Експрессионтекстбокссампле. sln.</span><span class="sxs-lookup"><span data-stu-id="117c3-118">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="117c3-119">Для построения решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="117c3-119">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="117c3-120">Запуск образца</span><span class="sxs-lookup"><span data-stu-id="117c3-120">To run this sample</span></span>

1. <span data-ttu-id="117c3-121">Добавьте в решение новое консольное приложение рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="117c3-121">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="117c3-122">Добавьте ссылку на проект **експрессионтекстбокссампле** из нового проекта консольного приложения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="117c3-122">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="117c3-123">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="117c3-123">Build the solution.</span></span>

4. <span data-ttu-id="117c3-124">Перетащите действие " **Многоназначение** " из области элементов в рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="117c3-124">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="117c3-125">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="117c3-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="117c3-126">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="117c3-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="117c3-127">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="117c3-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="117c3-128">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="117c3-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="117c3-129">См. также</span><span class="sxs-lookup"><span data-stu-id="117c3-129">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="117c3-130">Разработка приложений с помощью конструктора рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="117c3-130">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
