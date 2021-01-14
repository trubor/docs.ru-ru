---
title: Практическое руководство. Создание рабочего процесса
description: Выполните одно из трех действий в этом разделе, чтобы создать рабочий процесс в рамках этого учебника по Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: ea9fd023ba15ae23a10f5b8cf6f82c49ca9af6c8
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190446"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="f419b-103">Практическое руководство. Создание рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="f419b-103">How to: Create a Workflow</span></span>

<span data-ttu-id="f419b-104">Рабочие процессы могут создаваться как из встроенных, так и из пользовательских действий.</span><span class="sxs-lookup"><span data-stu-id="f419b-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="f419b-105">В подразделах этого раздела приводится пошаговая процедура создания рабочего процесса, который использует как встроенные действия, такие как <xref:System.Activities.Statements.Flowchart> действие, так и пользовательские действия из предыдущего раздела [Практическое руководство. Создание действия](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="f419b-105">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="f419b-106">Рабочий процесс моделирует игру по угадыванию числа.</span><span class="sxs-lookup"><span data-stu-id="f419b-106">The workflow models a number guessing game.</span></span> <span data-ttu-id="f419b-107">Для завершения учебника требуется только один из подразделов в этом разделе. Необходимо выбрать стиль, который вас интересует, и выполнить шаг.</span><span class="sxs-lookup"><span data-stu-id="f419b-107">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="f419b-108">Однако при необходимости можно завершить все подразделы.</span><span class="sxs-lookup"><span data-stu-id="f419b-108">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f419b-109">Каждый раздел в учебнике «Приступая к работе» построен на основе предыдущих разделов.</span><span class="sxs-lookup"><span data-stu-id="f419b-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="f419b-110">Для выполнения этой статьи сначала необходимо выполнить действия [по созданию действия](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="f419b-110">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f419b-111">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="f419b-111">In This Section</span></span>  

 [<span data-ttu-id="f419b-112">Практическое руководство. Создание последовательного рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="f419b-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="f419b-113">Описывает, как создать последовательный рабочий процесс с помощью действия <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="f419b-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="f419b-114">Практическое руководство. Создание рабочего процесса c блок-схемой</span><span class="sxs-lookup"><span data-stu-id="f419b-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="f419b-115">Описывает, как создать рабочий процесс блок-схемы с помощью действия <xref:System.Activities.Statements.Flowchart>.</span><span class="sxs-lookup"><span data-stu-id="f419b-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="f419b-116">Практическое руководство. Создание рабочего процесса конечного автомата</span><span class="sxs-lookup"><span data-stu-id="f419b-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="f419b-117">Описывает способы создания рабочего процесса конечного автомата с помощью действия <xref:System.Activities.Statements.StateMachine>.</span><span class="sxs-lookup"><span data-stu-id="f419b-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f419b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f419b-118">See also</span></span>

- [<span data-ttu-id="f419b-119">Программирование в Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="f419b-119">Windows Workflow Foundation Programming</span></span>](programming.md)
