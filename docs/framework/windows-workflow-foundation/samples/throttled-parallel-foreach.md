---
description: 'Дополнительные сведения: регулируемое параллельное ForEach'
title: Параллельное действие ForEach с ограничением
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 2c1d1386f0b8c5b3c68d60bc83386ccfdf5e7875
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741683"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="ddf86-103">Параллельное действие ForEach с ограничением</span><span class="sxs-lookup"><span data-stu-id="ddf86-103">Throttled Parallel ForEach</span></span>

<span data-ttu-id="ddf86-104">Действие `ThrottleParallelForEach` аналогично действию <xref:System.Activities.Statements.ParallelForEach%601>, за одним исключением, которое позволяет настроить коэффициент распараллеливания для ограничения количества одновременно выполняющихся ветвей.</span><span class="sxs-lookup"><span data-stu-id="ddf86-104">The `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="ddf86-105">Действие `ThrottleParallelForEach` является производным от действия <xref:System.Activities.NativeActivity>, поскольку оно должно планировать другие действия (дочерние действия), что можно сделать только через класс <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="ddf86-105">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="ddf86-106">Проекты</span><span class="sxs-lookup"><span data-stu-id="ddf86-106">Projects</span></span>

|<span data-ttu-id="ddf86-107">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="ddf86-107">**ProjectName**</span></span>|<span data-ttu-id="ddf86-108">**Описание**</span><span class="sxs-lookup"><span data-stu-id="ddf86-108">**Description**</span></span>|<span data-ttu-id="ddf86-109">**Основные файлы**</span><span class="sxs-lookup"><span data-stu-id="ddf86-109">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="ddf86-110">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="ddf86-110">ThrottledParallelForEach</span></span>|<span data-ttu-id="ddf86-111">Содержит действие `ThrottledParallelForEach` и его конструктор.</span><span class="sxs-lookup"><span data-stu-id="ddf86-111">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="ddf86-112">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="ddf86-112">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="ddf86-113">Определение действия `ThrottledParallelForEach`.</span><span class="sxs-lookup"><span data-stu-id="ddf86-113">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="ddf86-114">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="ddf86-114">CodeTestClient</span></span>|<span data-ttu-id="ddf86-115">Образец клиентского приложения, осуществляющего конфигурирование и запуск рабочего процесса с использованием `ThrottledParallelForEach` при помощи императивного кода.</span><span class="sxs-lookup"><span data-stu-id="ddf86-115">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="ddf86-116">Program.cs</span><span class="sxs-lookup"><span data-stu-id="ddf86-116">Program.cs</span></span><br /><br /> <span data-ttu-id="ddf86-117">Определяет и выполняет экземпляр образца рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="ddf86-117">Defines and runs an instance of the sample workflow.</span></span>|

## <a name="to-use-this-sample"></a><span data-ttu-id="ddf86-118">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="ddf86-118">To use this sample</span></span>

1. <span data-ttu-id="ddf86-119">С помощью Visual Studio 2010 откройте файл Сроттледпараллелфореач. sln.</span><span class="sxs-lookup"><span data-stu-id="ddf86-119">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2. <span data-ttu-id="ddf86-120">Для построения решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="ddf86-120">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="ddf86-121">Чтобы запустить решение, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="ddf86-121">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ddf86-122">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="ddf86-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ddf86-123">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="ddf86-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ddf86-124">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="ddf86-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ddf86-125">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="ddf86-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
