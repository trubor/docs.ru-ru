---
description: Дополнительные сведения см. в статье обработка ошибок в действии блок-схемы с помощью TryCatch.
title: Обработка ошибок в действии блок-схемы с помощью TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 9ab323117e5b26696a07624117e8acc8c0beacff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755354"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="88bad-103">Обработка ошибок в действии блок-схемы с помощью TryCatch</span><span class="sxs-lookup"><span data-stu-id="88bad-103">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="88bad-104">В этом образце показано использование действия <xref:System.Activities.Statements.TryCatch> в рамках действия сложного потока управления.</span><span class="sxs-lookup"><span data-stu-id="88bad-104">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="88bad-105">В этом образце промокод и несколько дочерних элементов передаются как переменные в действие <xref:System.Activities.Statements.Flowchart>, которое вычисляет скидку на основе формулы, которая соответствует промокоду.</span><span class="sxs-lookup"><span data-stu-id="88bad-105">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="88bad-106">Образец включает императивный код и версии конструктора рабочих процессов образца.</span><span class="sxs-lookup"><span data-stu-id="88bad-106">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="88bad-107">В следующей таблице представлены переменные для действия `CreateFlowchartWithFaults`.</span><span class="sxs-lookup"><span data-stu-id="88bad-107">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="88bad-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="88bad-108">Parameters</span></span>|<span data-ttu-id="88bad-109">Описание</span><span class="sxs-lookup"><span data-stu-id="88bad-109">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="88bad-110">promoCode</span><span class="sxs-lookup"><span data-stu-id="88bad-110">promoCode</span></span>|<span data-ttu-id="88bad-111">Промокод.</span><span class="sxs-lookup"><span data-stu-id="88bad-111">The promotion code.</span></span> <span data-ttu-id="88bad-112">Тип: строка</span><span class="sxs-lookup"><span data-stu-id="88bad-112">Type: String</span></span><br /><br /> <span data-ttu-id="88bad-113">Возможные значения с описанием в скобках.</span><span class="sxs-lookup"><span data-stu-id="88bad-113">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="88bad-114">-Single (одиночная)</span><span class="sxs-lookup"><span data-stu-id="88bad-114">-   Single (Single)</span></span><br /><span data-ttu-id="88bad-115">— МНК (в браке нет детей).</span><span class="sxs-lookup"><span data-stu-id="88bad-115">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="88bad-116">— МВК (в браке).</span><span class="sxs-lookup"><span data-stu-id="88bad-116">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="88bad-117">numKids</span><span class="sxs-lookup"><span data-stu-id="88bad-117">numKids</span></span>|<span data-ttu-id="88bad-118">Число детей.</span><span class="sxs-lookup"><span data-stu-id="88bad-118">The number of children.</span></span> <span data-ttu-id="88bad-119">Тип: int</span><span class="sxs-lookup"><span data-stu-id="88bad-119">Type: int</span></span>|

<span data-ttu-id="88bad-120">Действие `CreateFlowchartWithFaults` использует действие <xref:System.Activities.Statements.FlowSwitch%601>, которое производит переключения на аргументе `promoCode` и вычисляет скидку с использованием следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="88bad-120">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="88bad-121">Значение параметра `promoCode`</span><span class="sxs-lookup"><span data-stu-id="88bad-121">Value of `promoCode`</span></span>|<span data-ttu-id="88bad-122">Скидка (%)</span><span class="sxs-lookup"><span data-stu-id="88bad-122">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="88bad-123">Один</span><span class="sxs-lookup"><span data-stu-id="88bad-123">Single</span></span>|<span data-ttu-id="88bad-124">10</span><span class="sxs-lookup"><span data-stu-id="88bad-124">10</span></span>|
|<span data-ttu-id="88bad-125">MNK</span><span class="sxs-lookup"><span data-stu-id="88bad-125">MNK</span></span>|<span data-ttu-id="88bad-126">15</span><span class="sxs-lookup"><span data-stu-id="88bad-126">15</span></span>|
|<span data-ttu-id="88bad-127">MWK</span><span class="sxs-lookup"><span data-stu-id="88bad-127">MWK</span></span>|<span data-ttu-id="88bad-128">15 + (1 – 1/ `numberOfKids` ) \* 10 **Примечание.**  возможно, это вычисление может вызвать исключение <xref:System.DivideByZeroException> .</span><span class="sxs-lookup"><span data-stu-id="88bad-128">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="88bad-129">Поэтому вычисление скидки упаковано в действие <xref:System.Activities.Statements.TryCatch>, которое кэширует исключение <xref:System.DivideByZeroException> и устанавливает скидку в нуль.</span><span class="sxs-lookup"><span data-stu-id="88bad-129">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="88bad-130">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="88bad-130">To use this sample</span></span>

1. <span data-ttu-id="88bad-131">С помощью Visual Studio 2010 откройте файл решения Фловчартвисфаулсандлинг. sln.</span><span class="sxs-lookup"><span data-stu-id="88bad-131">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="88bad-132">Для построения решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="88bad-132">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="88bad-133">Чтобы запустить решение, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="88bad-133">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88bad-134">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="88bad-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="88bad-135">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="88bad-135">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="88bad-136">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="88bad-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="88bad-137">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="88bad-137">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="88bad-138">См. также</span><span class="sxs-lookup"><span data-stu-id="88bad-138">See also</span></span>

- [<span data-ttu-id="88bad-139">Рабочие процессы блок-схемы</span><span class="sxs-lookup"><span data-stu-id="88bad-139">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="88bad-140">Исключения</span><span class="sxs-lookup"><span data-stu-id="88bad-140">Exceptions</span></span>](../exceptions.md)
