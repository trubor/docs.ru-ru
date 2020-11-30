---
title: Практическое руководство. Реализация клиента асинхронной модели, основанной на событиях
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 44bcc831ddf6fa292fd96d8e79ad54f7be2f65c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678094"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c254d-102">Практическое руководство. Реализация клиента асинхронной модели, основанной на событиях</span><span class="sxs-lookup"><span data-stu-id="c254d-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="c254d-103">В приведенном ниже примере кода показано, как использовать компонент, который соответствует принципам [асинхронной модели на основе событий](event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c254d-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="c254d-104">В форме для этого примера используется компонент `PrimeNumberCalculator`, который описывается в статье [Пошаговое руководство. Реализация компонента, поддерживающего асинхронную модель, основанную на событиях](component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c254d-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="c254d-105">Запустив проект с этим примером, вы увидите форму расчета простых чисел с сеткой и двумя кнопками: **Start New Task** (Выполнить новую задачу) и **Cancel** (Отменить).</span><span class="sxs-lookup"><span data-stu-id="c254d-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="c254d-106">Вы можете нажать кнопку **Start New Task** (Выполнить новую задачу) несколько раз подряд, и при каждом нажатии запустится асинхронная операция вычисления, которая проверяет, является ли случайное проверяемое число простым.</span><span class="sxs-lookup"><span data-stu-id="c254d-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="c254d-107">Форма периодически обновляется, отображая ход выполнения и накопленные результаты.</span><span class="sxs-lookup"><span data-stu-id="c254d-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="c254d-108">Каждой операции присваивается уникальный идентификатор задачи.</span><span class="sxs-lookup"><span data-stu-id="c254d-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="c254d-109">Результат вычисления отображается в столбце **Result** (Результат). Если проверяемое число не является простым, оно дополняется отметкой **Composite** (Составное) и значением его первого делителя.</span><span class="sxs-lookup"><span data-stu-id="c254d-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="c254d-110">Кнопка **Cancel** (Отменить) позволяет отменить все операции, ожидающие выполнения.</span><span class="sxs-lookup"><span data-stu-id="c254d-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="c254d-111">Вы можете выбрать несколько элементов.</span><span class="sxs-lookup"><span data-stu-id="c254d-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c254d-112">Большинство чисел не будут простыми.</span><span class="sxs-lookup"><span data-stu-id="c254d-112">Most numbers will not be prime.</span></span> <span data-ttu-id="c254d-113">Если после нескольких операций вам не удастся найти простое число, просто запустите еще несколько задач. Рано или поздно простые числа будут обнаружены.</span><span class="sxs-lookup"><span data-stu-id="c254d-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c254d-114">Пример</span><span class="sxs-lookup"><span data-stu-id="c254d-114">Example</span></span>  

 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="c254d-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c254d-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
