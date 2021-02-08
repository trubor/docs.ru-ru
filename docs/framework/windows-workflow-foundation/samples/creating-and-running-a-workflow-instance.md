---
description: 'Дополнительные сведения: создание и запуск экземпляра рабочего процесса'
title: Создание и запуск экземпляра рабочего процесса
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 2efd4a0017f450c21954e363af33be69c659624e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787855"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="cb05e-103">Создание и запуск экземпляра рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="cb05e-103">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="cb05e-104">В этом образце показано, как выполнить экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="cb05e-104">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="cb05e-105">Здесь показано синхронное и асинхронное выполнение.</span><span class="sxs-lookup"><span data-stu-id="cb05e-105">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cb05e-106">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="cb05e-106">Demonstrates</span></span>

<span data-ttu-id="cb05e-107"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="cb05e-107"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="cb05e-108">Разговор</span><span class="sxs-lookup"><span data-stu-id="cb05e-108">Discussion</span></span>

<span data-ttu-id="cb05e-109">В первой части образца используется метод <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb05e-109">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="cb05e-110">Это основной способ выполнения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="cb05e-110">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="cb05e-111">Рабочие процессы, запускаемые методом <xref:System.Activities.WorkflowInvoker.Invoke%2A>, выполняются синхронно.</span><span class="sxs-lookup"><span data-stu-id="cb05e-111">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="cb05e-112">Во второй части образца используется класс <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="cb05e-112">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="cb05e-113">Класс <xref:System.Activities.WorkflowApplication> предоставляет дополнительные возможности управления каждым экземпляром, включая возможность взаимодействия с выполняющимся рабочим процессом и возможность асинхронного выполнения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="cb05e-113"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb05e-114">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="cb05e-114">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb05e-115">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="cb05e-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cb05e-116">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="cb05e-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb05e-117">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="cb05e-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="cb05e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="cb05e-118">See also</span></span>

- [<span data-ttu-id="cb05e-119">Использование WorkflowInvoker и WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="cb05e-119">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
