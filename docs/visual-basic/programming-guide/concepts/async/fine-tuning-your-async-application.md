---
description: 'Дополнительные сведения о: Fine-Tuning приложения в асинхронном приложении (Visual Basic)'
title: Настройка асинхронного приложения
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 1e31ffdee4d2af9379e8073010ed2b1925023e43
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464421"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="384ad-103">Fine-Tuning Your Async Application (Visual Basic) (Настройка асинхронного приложения (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="384ad-103">Fine-Tuning Your Async Application (Visual Basic)</span></span>

<span data-ttu-id="384ad-104">Методы и свойства, доступные при использовании типа <xref:System.Threading.Tasks.Task>, позволяют сделать приложение более точным и гибким.</span><span class="sxs-lookup"><span data-stu-id="384ad-104">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="384ad-105">В подразделах этого раздела приводятся примеры, в которых используются <xref:System.Threading.CancellationToken> и важные методы `Task`, такие как <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="384ad-105">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="384ad-106">С помощью `WhenAny` и `WhenAll` можно легко запускать несколько задач и ожидать их завершения путем наблюдения за одной из них.</span><span class="sxs-lookup"><span data-stu-id="384ad-106">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="384ad-107">`WhenAny` возвращает задачу, которая завершается после завершения любой задачи в коллекции.</span><span class="sxs-lookup"><span data-stu-id="384ad-107">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="384ad-108">Примеры использования см `WhenAny` . в разделе  [Отмена оставшихся асинхронных задач после завершения одной операции (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)и [Запуск нескольких асинхронных задач и их обработка по мере их завершения (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="384ad-108">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="384ad-109">`WhenAll` возвращает задачу, которая завершается после завершения всех задач в коллекции.</span><span class="sxs-lookup"><span data-stu-id="384ad-109">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="384ad-110">Дополнительные сведения и пример использования см. в `WhenAll` разделе [Практическое руководство. расширение асинхронного пошагового руководства с помощью Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="384ad-110">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="384ad-111">Этот раздел содержит следующие примеры.</span><span class="sxs-lookup"><span data-stu-id="384ad-111">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="384ad-112">[Отмена асинхронной задачи или списка задач (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="384ad-112">[Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="384ad-113">Отмена асинхронных задач после определенного периода времени (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="384ad-113">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](cancel-async-tasks-after-a-period-of-time.md)  
  
- <span data-ttu-id="384ad-114">[Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md) (Отмена оставшихся асинхронных задач после завершения одной из них в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="384ad-114">[Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)</span></span>  
  
- <span data-ttu-id="384ad-115">[Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md) (Запуск нескольких асинхронных задач и их обработка по мере завершения в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="384ad-115">[Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="384ad-116">Для выполнения примеров необходимо, чтобы на компьютере были установлены Visual Studio 2012 или более поздняя версия и .NET Framework 4.5 или более поздняя версия.</span><span class="sxs-lookup"><span data-stu-id="384ad-116">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="384ad-117">Проекты создают пользовательский интерфейс, содержащий кнопку, которая запускает процесс, и кнопку, которая его отменяет, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="384ad-117">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="384ad-118">Кнопки называются `startButton` и `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="384ad-118">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="384ad-119">![Окно WPF с кнопкой "Отмена"](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Диалоговое окно с кнопкой запуска и остановки")</span><span class="sxs-lookup"><span data-stu-id="384ad-119">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="384ad-120">Скачать полный проект Windows Presentation Foundation (WPF) можно со страницы [Пример асинхронности. Тонкая настройка приложения](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="384ad-120">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="384ad-121">См. также</span><span class="sxs-lookup"><span data-stu-id="384ad-121">See also</span></span>

- [<span data-ttu-id="384ad-122">Асинхронное программирование с использованием ключевых слов Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="384ad-122">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
