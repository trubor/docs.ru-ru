---
title: Асинхронное программирование на C#
description: Общие сведения о языковой поддержке асинхронного программирования в C# с помощью async, await, задач и Task<T>
ms.date: 06/04/2020
ms.openlocfilehash: ffc2289f3b5abfe3865e1a096ee91e2e649a6427
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624244"
---
# <a name="asynchronous-programming-with-async-and-await"></a><span data-ttu-id="06103-103">Асинхронное программирование с использованием ключевых слов async и await</span><span class="sxs-lookup"><span data-stu-id="06103-103">Asynchronous programming with async and await</span></span>

<span data-ttu-id="06103-104">[Модель асинхронного программирования на основе задач (TAP)](task-asynchronous-programming-model.md) предоставляет абстракцию асинхронного кода.</span><span class="sxs-lookup"><span data-stu-id="06103-104">The [Task asynchronous programming model (TAP)](task-asynchronous-programming-model.md) provides an abstraction over asynchronous code.</span></span> <span data-ttu-id="06103-105">Вы пишете код как последовательность операторов, как обычно.</span><span class="sxs-lookup"><span data-stu-id="06103-105">You write code as a sequence of statements, just like always.</span></span> <span data-ttu-id="06103-106">Вы можете читать этот код, как если бы каждая инструкция завершалась до начала следующей.</span><span class="sxs-lookup"><span data-stu-id="06103-106">You can read that code as though each statement completes before the next begins.</span></span> <span data-ttu-id="06103-107">Компилятор выполняет множество преобразований, так как некоторые из этих инструкций могут начать работу и вернуть <xref:System.Threading.Tasks.Task>, представляющий текущую работу.</span><span class="sxs-lookup"><span data-stu-id="06103-107">The compiler performs many transformations because some of those statements may start work and return a <xref:System.Threading.Tasks.Task> that represents the ongoing work.</span></span>

<span data-ttu-id="06103-108">Это и есть цель такого синтаксиса: сделать возможным код, который читается как последовательность операторов, но выполняется в гораздо более сложном порядке на основе выделения внешних ресурсов и при завершении задач.</span><span class="sxs-lookup"><span data-stu-id="06103-108">That's the goal of this syntax: enable code that reads like a sequence of statements, but executes in a much more complicated order based on external resource allocation and when tasks complete.</span></span> <span data-ttu-id="06103-109">Это аналогично тому, как люди дают инструкции для процессов, которые включают асинхронные задачи.</span><span class="sxs-lookup"><span data-stu-id="06103-109">It's analogous to how people give instructions for processes that include asynchronous tasks.</span></span> <span data-ttu-id="06103-110">В этой статье вы будете использовать пример инструкции для приготовления завтрака, чтобы увидеть, как ключевые слова `async` и `await` упрощают понимание кода, который включает в себя серию асинхронных инструкций.</span><span class="sxs-lookup"><span data-stu-id="06103-110">Throughout this article, you'll use an example of instructions for making a breakfast to see how the `async` and `await` keywords make it easier to reason about code, that includes a series of asynchronous instructions.</span></span> <span data-ttu-id="06103-111">Можно написать инструкции аналогично следующему списку, чтобы объяснить, как приготовить завтрак.</span><span class="sxs-lookup"><span data-stu-id="06103-111">You'd write the instructions something like the following list to explain how to make a breakfast:</span></span>

1. <span data-ttu-id="06103-112">Налить чашку кофе.</span><span class="sxs-lookup"><span data-stu-id="06103-112">Pour a cup of coffee.</span></span>
1. <span data-ttu-id="06103-113">Нагреть сковородку, а затем поджарить два яйца.</span><span class="sxs-lookup"><span data-stu-id="06103-113">Heat up a pan, then fry two eggs.</span></span>
1. <span data-ttu-id="06103-114">Поджарить три куска бекона.</span><span class="sxs-lookup"><span data-stu-id="06103-114">Fry three slices of bacon.</span></span>
1. <span data-ttu-id="06103-115">Сделать два тоста.</span><span class="sxs-lookup"><span data-stu-id="06103-115">Toast two pieces of bread.</span></span>
1. <span data-ttu-id="06103-116">Намазать тосты маслом и джемом.</span><span class="sxs-lookup"><span data-stu-id="06103-116">Add butter and jam to the toast.</span></span>
1. <span data-ttu-id="06103-117">Налить стакан апельсинового сока.</span><span class="sxs-lookup"><span data-stu-id="06103-117">Pour a glass of orange juice.</span></span>

<span data-ttu-id="06103-118">Если у вас есть кулинарный опыт, вы бы выполняли эти инструкции **асинхронно**.</span><span class="sxs-lookup"><span data-stu-id="06103-118">If you have experience with cooking, you'd execute those instructions **asynchronously**.</span></span> <span data-ttu-id="06103-119">Сначала вы бы поставили сковородку на огонь, а затем занялись бы беконом.</span><span class="sxs-lookup"><span data-stu-id="06103-119">You'd start warming the pan for eggs, then start the bacon.</span></span> <span data-ttu-id="06103-120">Потом бы поставили тосты, а вслед за этим принялись бы за яичницу.</span><span class="sxs-lookup"><span data-stu-id="06103-120">You'd put the bread in the toaster, then start the eggs.</span></span> <span data-ttu-id="06103-121">На каждом этапе процесса необходимо запустить задачу, а затем обратить внимание на другие задачи, которые требуют вашего внимания.</span><span class="sxs-lookup"><span data-stu-id="06103-121">At each step of the process, you'd start a task, then turn your attention to tasks that are ready for your attention.</span></span>

<span data-ttu-id="06103-122">Приготовление завтрака представляет собой хороший пример асинхронной непараллельной работы.</span><span class="sxs-lookup"><span data-stu-id="06103-122">Cooking breakfast is a good example of asynchronous work that isn't parallel.</span></span> <span data-ttu-id="06103-123">Один пользователь (или поток) может обрабатывать все эти задачи.</span><span class="sxs-lookup"><span data-stu-id="06103-123">One person (or thread) can handle all these tasks.</span></span> <span data-ttu-id="06103-124">Продолжая аналогию с завтраком, один человек может приготовить завтрак асинхронно путем запуска очередной задачи до завершения предыдущей.</span><span class="sxs-lookup"><span data-stu-id="06103-124">Continuing the breakfast analogy, one person can make breakfast asynchronously by starting the next task before the first completes.</span></span> <span data-ttu-id="06103-125">Готовка продолжается вне зависимости от того, следит ли за ней кто-либо.</span><span class="sxs-lookup"><span data-stu-id="06103-125">The cooking progresses whether or not someone is watching it.</span></span> <span data-ttu-id="06103-126">Как только вы начали греть сковороду для яичницы, можно заняться обжаркой бекона.</span><span class="sxs-lookup"><span data-stu-id="06103-126">As soon as you start warming the pan for the eggs, you can begin frying the bacon.</span></span> <span data-ttu-id="06103-127">Когда бекон будет жариться, можно поместить хлеб в тостер.</span><span class="sxs-lookup"><span data-stu-id="06103-127">Once the bacon starts, you can put the bread into the toaster.</span></span>

<span data-ttu-id="06103-128">Для параллельного алгоритма потребовалось бы несколько поваров (или потоков).</span><span class="sxs-lookup"><span data-stu-id="06103-128">For a parallel algorithm, you'd need multiple cooks (or threads).</span></span> <span data-ttu-id="06103-129">Один готовит яйца, один — бекон и т. д.</span><span class="sxs-lookup"><span data-stu-id="06103-129">One would make the eggs, one the bacon, and so on.</span></span> <span data-ttu-id="06103-130">Каждый из них будет заниматься только одной задачей.</span><span class="sxs-lookup"><span data-stu-id="06103-130">Each one would be focused on just that one task.</span></span> <span data-ttu-id="06103-131">Каждый повар (или поток) будет заблокирован синхронным ожиданием готовности бекона или тостов.</span><span class="sxs-lookup"><span data-stu-id="06103-131">Each cook (or thread) would be blocked synchronously waiting for bacon to be ready to flip, or the toast to pop.</span></span>

<span data-ttu-id="06103-132">Теперь рассмотрим эти же инструкции, написанные на C#.</span><span class="sxs-lookup"><span data-stu-id="06103-132">Now, consider those same instructions written as C# statements:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-starter/Program.cs" highlight="8-27":::

:::image type="content" source="media/synchronous-breakfast.png" alt-text="Синхронное приготовление завтрака":::

<span data-ttu-id="06103-134">Синхронное приготовление завтрака заняло примерно 30 минут, так как общее время является суммой времен выполнения каждой задачи.</span><span class="sxs-lookup"><span data-stu-id="06103-134">The synchronously prepared breakfast, took roughly 30 minutes because the total is the sum of each individual task.</span></span>

> [!NOTE]
> <span data-ttu-id="06103-135">Классы `Coffee`, `Egg`, `Bacon`, `Toast` и `Juice` пусты.</span><span class="sxs-lookup"><span data-stu-id="06103-135">The `Coffee`, `Egg`, `Bacon`, `Toast`, and `Juice` classes are empty.</span></span> <span data-ttu-id="06103-136">Они просто являются классами меток, используемыми в целях демонстрации, не содержат свойств и не используются для выполнения других задач.</span><span class="sxs-lookup"><span data-stu-id="06103-136">They are simply marker classes for the purpose of demonstration, contain no properties, and serve no other purpose.</span></span>

<span data-ttu-id="06103-137">Компьютеры не рассматривают эти инструкции так же, как люди.</span><span class="sxs-lookup"><span data-stu-id="06103-137">Computers don't interpret those instructions the same way people do.</span></span> <span data-ttu-id="06103-138">Компьютер будет задерживаться над каждой инструкцией до момента, когда работа будет завершена, прежде чем перейдет к следующему оператору.</span><span class="sxs-lookup"><span data-stu-id="06103-138">The computer will block on each statement until the work is complete before moving on to the next statement.</span></span> <span data-ttu-id="06103-139">Вряд ли такой завтрак вас устроит.</span><span class="sxs-lookup"><span data-stu-id="06103-139">That creates an unsatisfying breakfast.</span></span> <span data-ttu-id="06103-140">Более поздние задачи не будут начаты до завершения предыдущих.</span><span class="sxs-lookup"><span data-stu-id="06103-140">The later tasks wouldn't be started until the earlier tasks had completed.</span></span> <span data-ttu-id="06103-141">Потребуется гораздо больше времени для приготовления завтрака, к тому же часть уже остынет еще до подачи.</span><span class="sxs-lookup"><span data-stu-id="06103-141">It would take much longer to create the breakfast, and some items would have gotten cold before being served.</span></span>

<span data-ttu-id="06103-142">Если требуется, чтобы компьютер асинхронно выполнил инструкции выше, необходимо писать асинхронный код.</span><span class="sxs-lookup"><span data-stu-id="06103-142">If you want the computer to execute the above instructions asynchronously, you must write asynchronous code.</span></span>

<span data-ttu-id="06103-143">Эти проблемы важны для программ, которые вы пишете уже сегодня.</span><span class="sxs-lookup"><span data-stu-id="06103-143">These concerns are important for the programs you write today.</span></span> <span data-ttu-id="06103-144">При написании клиентских программ требуется, чтобы пользовательский интерфейс реагировал на ввод данных пользователем.</span><span class="sxs-lookup"><span data-stu-id="06103-144">When you write client programs, you want the UI to be responsive to user input.</span></span> <span data-ttu-id="06103-145">Приложения не должны блокировать телефон при скачивании данных из Интернета.</span><span class="sxs-lookup"><span data-stu-id="06103-145">Your application shouldn't make a phone appear frozen while it's downloading data from the web.</span></span> <span data-ttu-id="06103-146">При написании серверных программ не стоит блокировать потоки.</span><span class="sxs-lookup"><span data-stu-id="06103-146">When you write server programs, you don't want threads blocked.</span></span> <span data-ttu-id="06103-147">Эти потоки могут обслуживать другие запросы.</span><span class="sxs-lookup"><span data-stu-id="06103-147">Those threads could be serving other requests.</span></span> <span data-ttu-id="06103-148">Использование синхронного кода в ситуации, когда существуют асинхронные альтернативы, мешает масштабированию с минимальными затратами.</span><span class="sxs-lookup"><span data-stu-id="06103-148">Using synchronous code when asynchronous alternatives exist hurts your ability to scale out less expensively.</span></span> <span data-ttu-id="06103-149">Вы платите за эти заблокированные потоки.</span><span class="sxs-lookup"><span data-stu-id="06103-149">You pay for those blocked threads.</span></span>

<span data-ttu-id="06103-150">Успешные современные приложения требуют использования асинхронного кода.</span><span class="sxs-lookup"><span data-stu-id="06103-150">Successful modern applications require asynchronous code.</span></span> <span data-ttu-id="06103-151">Без поддержки языком при написании асинхронного кода требуются обратные вызовы, события завершения или другие способы, заслоняющие исходное назначение кода.</span><span class="sxs-lookup"><span data-stu-id="06103-151">Without language support, writing asynchronous code required callbacks, completion events, or other means that obscured the original intent of the code.</span></span> <span data-ttu-id="06103-152">Преимуществом синхронного кода является то, что эти пошаговые действия упрощают проверку и анализ.</span><span class="sxs-lookup"><span data-stu-id="06103-152">The advantage of the synchronous code is that its step-by-step actions make it easy to scan and understand.</span></span> <span data-ttu-id="06103-153">Традиционные асинхронные модели заставляют сосредоточиваться на асинхронности кода, а не на фундаментальных действиях в нем.</span><span class="sxs-lookup"><span data-stu-id="06103-153">Traditional asynchronous models forced you to focus on the asynchronous nature of the code, not on the fundamental actions of the code.</span></span>

## <a name="dont-block-await-instead"></a><span data-ttu-id="06103-154">Не блокировать, а использовать await</span><span class="sxs-lookup"><span data-stu-id="06103-154">Don't block, await instead</span></span>

<span data-ttu-id="06103-155">Приведенный выше код демонстрирует дурную практику: использование синхронного кода для выполнения асинхронных операций.</span><span class="sxs-lookup"><span data-stu-id="06103-155">The preceding code demonstrates a bad practice: constructing synchronous code to perform asynchronous operations.</span></span> <span data-ttu-id="06103-156">В таком виде код блокирует выполняющий поток, не позволяя делать другие действия.</span><span class="sxs-lookup"><span data-stu-id="06103-156">As written, this code blocks the thread executing it from doing any other work.</span></span> <span data-ttu-id="06103-157">Он не будет прерван, пока задачи выполняются.</span><span class="sxs-lookup"><span data-stu-id="06103-157">It won't be interrupted while any of the tasks are in progress.</span></span> <span data-ttu-id="06103-158">Все равно что стоять и смотреть на тостер, пока поджаривается хлеб.</span><span class="sxs-lookup"><span data-stu-id="06103-158">It would be as though you stared at the toaster after putting the bread in.</span></span> <span data-ttu-id="06103-159">Пока тост не готов, вы всех игнорируете.</span><span class="sxs-lookup"><span data-stu-id="06103-159">You'd ignore anyone talking to you until the toast popped.</span></span>

<span data-ttu-id="06103-160">Давайте начнем менять этот код, чтобы не блокировать поток во время выполнения задачи.</span><span class="sxs-lookup"><span data-stu-id="06103-160">Let's start by updating this code so that the thread doesn't block while tasks are running.</span></span> <span data-ttu-id="06103-161">Ключевое слово `await` позволяет обойтись без блокировки для запуска задачи, а затем продолжить выполнение, когда задача завершается.</span><span class="sxs-lookup"><span data-stu-id="06103-161">The `await` keyword provides a non-blocking way to start a task, then continue execution when that task completes.</span></span> <span data-ttu-id="06103-162">Простая асинхронная версия кода для приготовления завтрака будет выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="06103-162">A simple asynchronous version of the make a breakfast code would look like the following snippet:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V2/Program.cs" ID="SnippetMain":::

> [!IMPORTANT]
> <span data-ttu-id="06103-163">Общее затраченное время примерно такое же, как у начальной синхронной версии.</span><span class="sxs-lookup"><span data-stu-id="06103-163">The total elapsed time is roughly the same as the initial synchronous version.</span></span> <span data-ttu-id="06103-164">Этот код можно улучшить, используя ряд ключевых возможностей асинхронного программирования.</span><span class="sxs-lookup"><span data-stu-id="06103-164">The code has yet to take advantage of some of the key features of asynchronous programming.</span></span>

> [!TIP]
> <span data-ttu-id="06103-165">Тексты методов `FryEggsAsync`, `FryBaconAsync` и `ToastBreadAsync` были обновлены так, чтобы возвращать `Task<Egg>`, `Task<Bacon>` и `Task<Toast>`, соответственно.</span><span class="sxs-lookup"><span data-stu-id="06103-165">The method bodies of the `FryEggsAsync`, `FryBaconAsync`, and `ToastBreadAsync` have all been updated to return `Task<Egg>`, `Task<Bacon>`, and `Task<Toast>` respectively.</span></span> <span data-ttu-id="06103-166">Методы переименованы и теперь содержат суффикс "Async".</span><span class="sxs-lookup"><span data-stu-id="06103-166">The methods are renamed from their original version to include the "Async" suffix.</span></span> <span data-ttu-id="06103-167">Их реализации показаны в составе [окончательной версии](#final-version) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="06103-167">Their implementations are shown as part of the [final version](#final-version) later in this article.</span></span>

<span data-ttu-id="06103-168">Этот код не блокируется при приготовлении яиц или бекона.</span><span class="sxs-lookup"><span data-stu-id="06103-168">This code doesn't block while the eggs or the bacon are cooking.</span></span> <span data-ttu-id="06103-169">Этот код, однако, не запускает других задач.</span><span class="sxs-lookup"><span data-stu-id="06103-169">This code won't start any other tasks though.</span></span> <span data-ttu-id="06103-170">По-прежнему придется поместить тост в тостер и смотреть на него, пока он не выскочит.</span><span class="sxs-lookup"><span data-stu-id="06103-170">You'd still put the toast in the toaster and stare at it until it pops.</span></span> <span data-ttu-id="06103-171">Но по крайней мере можно отвечать всем, кто хочет вашего внимания.</span><span class="sxs-lookup"><span data-stu-id="06103-171">But at least, you'd respond to anyone that wanted your attention.</span></span> <span data-ttu-id="06103-172">В ресторане, где будет размещаться несколько заказов, повар сможет начать готовить другой завтрак, пока первый готовится.</span><span class="sxs-lookup"><span data-stu-id="06103-172">In a restaurant where multiple orders are placed, the cook could start another breakfast while the first is cooking.</span></span>

<span data-ttu-id="06103-173">Теперь поток завтрака не блокируется в ожидании любой запущенной задачи, которая еще не завершена.</span><span class="sxs-lookup"><span data-stu-id="06103-173">Now, the thread working on the breakfast isn't blocked while awaiting any started task that hasn't yet finished.</span></span> <span data-ttu-id="06103-174">Для некоторых приложений это изменение — все, что требуется.</span><span class="sxs-lookup"><span data-stu-id="06103-174">For some applications, this change is all that's needed.</span></span> <span data-ttu-id="06103-175">Приложение с графическим интерфейсом будет отвечать пользователю после этого изменения.</span><span class="sxs-lookup"><span data-stu-id="06103-175">A GUI application still responds to the user with just this change.</span></span> <span data-ttu-id="06103-176">Тем не менее в этом сценарии нам нужно больше.</span><span class="sxs-lookup"><span data-stu-id="06103-176">However, for this scenario, you want more.</span></span> <span data-ttu-id="06103-177">Нам не требуется последовательное выполнение каждой из задач компонента.</span><span class="sxs-lookup"><span data-stu-id="06103-177">You don't want each of the component tasks to be executed sequentially.</span></span> <span data-ttu-id="06103-178">Лучше запускать каждую из задач компонента, не ожидая завершения предыдущей задачи.</span><span class="sxs-lookup"><span data-stu-id="06103-178">It's better to start each of the component tasks before awaiting the previous task's completion.</span></span>

## <a name="start-tasks-concurrently"></a><span data-ttu-id="06103-179">Одновременный запуск задач</span><span class="sxs-lookup"><span data-stu-id="06103-179">Start tasks concurrently</span></span>

<span data-ttu-id="06103-180">Во многих случаях требуется запускать сразу несколько независимых задач.</span><span class="sxs-lookup"><span data-stu-id="06103-180">In many scenarios, you want to start several independent tasks immediately.</span></span> <span data-ttu-id="06103-181">Затем, когда каждая задача завершается, можно продолжить другую работу, которая уже готова к этому.</span><span class="sxs-lookup"><span data-stu-id="06103-181">Then, as each task finishes, you can continue other work that's ready.</span></span> <span data-ttu-id="06103-182">В нашей аналогии — так завтрак готовится быстрее.</span><span class="sxs-lookup"><span data-stu-id="06103-182">In the breakfast analogy, that's how you get breakfast done more quickly.</span></span> <span data-ttu-id="06103-183">Вы также приготовите все примерно в одно и то же время.</span><span class="sxs-lookup"><span data-stu-id="06103-183">You also get everything done close to the same time.</span></span> <span data-ttu-id="06103-184">Вы получите горячий завтрак.</span><span class="sxs-lookup"><span data-stu-id="06103-184">You'll get a hot breakfast.</span></span>

<span data-ttu-id="06103-185"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> и связанные типы — это классы, позволяющие делать выводы о задачах, которые находятся в процессе выполнения.</span><span class="sxs-lookup"><span data-stu-id="06103-185">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> and related types are classes you can use to reason about tasks that are in progress.</span></span> <span data-ttu-id="06103-186">Это позволяет писать код, который точнее определяет, как будет фактически готовиться завтрак.</span><span class="sxs-lookup"><span data-stu-id="06103-186">That enables you to write code that more closely resembles the way you'd actually create breakfast.</span></span> <span data-ttu-id="06103-187">Вы начинаете готовить яйца, бекон и тосты примерно в одно и то же время.</span><span class="sxs-lookup"><span data-stu-id="06103-187">You'd start cooking the eggs, bacon, and toast at the same time.</span></span> <span data-ttu-id="06103-188">По мере необходимости вы обращаете внимание на отдельные задачи, переходите к другим, а затем ждете третьих, которые нуждаются в обработке.</span><span class="sxs-lookup"><span data-stu-id="06103-188">As each requires action, you'd turn your attention to that task, take care of the next action, then await for something else that requires your attention.</span></span>

<span data-ttu-id="06103-189">Вы начинаете задачу и удерживаете объект <xref:System.Threading.Tasks.Task>, представляющий работу.</span><span class="sxs-lookup"><span data-stu-id="06103-189">You start a task and hold on to the <xref:System.Threading.Tasks.Task> object that represents the work.</span></span> <span data-ttu-id="06103-190">Вы вызываете `await` для каждой задачи, прежде чем начать работу с ее результатами.</span><span class="sxs-lookup"><span data-stu-id="06103-190">You'll `await` each task before working with its result.</span></span>

<span data-ttu-id="06103-191">Давайте внесем эти изменения в код для приготовления завтрака.</span><span class="sxs-lookup"><span data-stu-id="06103-191">Let's make these changes to the breakfast code.</span></span> <span data-ttu-id="06103-192">Первым делом сохраним задачи для отдельных операций при их запуске, чтобы не ждать их:</span><span class="sxs-lookup"><span data-stu-id="06103-192">The first step is to store the tasks for operations when they start, rather than awaiting them:</span></span>

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");

Task<Egg> eggsTask = FryEggsAsync(2);
Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");

Task<Bacon> baconTask = FryBaconAsync(3);
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Task<Toast> toastTask = ToastBreadAsync(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");

Juice oj = PourOJ();
Console.WriteLine("oj is ready");
Console.WriteLine("Breakfast is ready!");
```

<span data-ttu-id="06103-193">Затем вы можете переместить инструкции `await` для бекона и яиц в конец метода, сразу перед подачей завтрака:</span><span class="sxs-lookup"><span data-stu-id="06103-193">Next, you can move the `await` statements for the bacon and eggs to the end of the method, before serving breakfast:</span></span>

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");

Task<Egg> eggsTask = FryEggsAsync(2);
Task<Bacon> baconTask = FryBaconAsync(3);
Task<Toast> toastTask = ToastBreadAsync(2);

Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

:::image type="content" source="media/asynchronous-breakfast.png" alt-text="Асинхронное приготовление завтрака":::

<span data-ttu-id="06103-195">Асинхронное приготовление завтрака заняло примерно 20 минут. Это позволило сэкономить время, так как некоторые задачи можно было выполнять параллельно.</span><span class="sxs-lookup"><span data-stu-id="06103-195">The asynchronously prepared breakfast took roughly 20 minutes, this time savings is because some tasks ran concurrently.</span></span>

<span data-ttu-id="06103-196">Предыдущий код работает лучше.</span><span class="sxs-lookup"><span data-stu-id="06103-196">The preceding code works better.</span></span> <span data-ttu-id="06103-197">Запуск всех асинхронных задач выполняется за один раз.</span><span class="sxs-lookup"><span data-stu-id="06103-197">You start all the asynchronous tasks at once.</span></span> <span data-ttu-id="06103-198">Вы ожидаете каждую задачу только в том случае, когда требуются результаты.</span><span class="sxs-lookup"><span data-stu-id="06103-198">You await each task only when you need the results.</span></span> <span data-ttu-id="06103-199">Приведенный выше код может быть похож на код в веб-приложении, который отправляет запросы для разных микрослужб, а затем объединяет результаты в одну страницу.</span><span class="sxs-lookup"><span data-stu-id="06103-199">The preceding code may be similar to code in a web application that makes requests of different microservices, then combines the results into a single page.</span></span> <span data-ttu-id="06103-200">Вы отправляете все запросы сразу, а затем вызываете `await`, чтобы соединить все задачи и создать веб-страницу.</span><span class="sxs-lookup"><span data-stu-id="06103-200">You'll make all the requests immediately, then `await` all those tasks and compose the web page.</span></span>

## <a name="composition-with-tasks"></a><span data-ttu-id="06103-201">Сочетаемость задач</span><span class="sxs-lookup"><span data-stu-id="06103-201">Composition with tasks</span></span>

 <span data-ttu-id="06103-202">У вас все готово для завтрака в одно и то же время, за исключением тостов.</span><span class="sxs-lookup"><span data-stu-id="06103-202">You have everything ready for breakfast at the same time except the toast.</span></span> <span data-ttu-id="06103-203">Приготовление тоста — композиция асинхронной операции (поджарить хлеб) и синхронной операции (добавить масло и джем).</span><span class="sxs-lookup"><span data-stu-id="06103-203">Making the toast is the composition of an asynchronous operation (toasting the bread), and synchronous operations (adding the butter and the jam).</span></span> <span data-ttu-id="06103-204">Обновление этого кода иллюстрирует важную концепцию:</span><span class="sxs-lookup"><span data-stu-id="06103-204">Updating this code illustrates an important concept:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06103-205">композиция асинхронной операции, за которой следует синхронная задача, является асинхронной операцией.</span><span class="sxs-lookup"><span data-stu-id="06103-205">The composition of an asynchronous operation followed by synchronous work is an asynchronous operation.</span></span> <span data-ttu-id="06103-206">Говоря иначе, если какая-либо часть операции является асинхронной, то и вся операция является асинхронной.</span><span class="sxs-lookup"><span data-stu-id="06103-206">Stated another way, if any portion of an operation is asynchronous, the entire operation is asynchronous.</span></span>

<span data-ttu-id="06103-207">Приведенный выше код показал, что можно использовать объекты <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601> для хранения выполняемых задач.</span><span class="sxs-lookup"><span data-stu-id="06103-207">The preceding code showed you that you can use <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> objects to hold running tasks.</span></span> <span data-ttu-id="06103-208">Вы вызываете `await` для каждой задачи, прежде чем использовать ее результат.</span><span class="sxs-lookup"><span data-stu-id="06103-208">You `await` each task before using its result.</span></span> <span data-ttu-id="06103-209">Следующим шагом является создание методов, которые представляют сочетание другой работы.</span><span class="sxs-lookup"><span data-stu-id="06103-209">The next step is to create methods that represent the combination of other work.</span></span> <span data-ttu-id="06103-210">Перед подачей завтрака требуется дождаться задачи, представляющей поджарку хлеба перед добавлением масла и джема.</span><span class="sxs-lookup"><span data-stu-id="06103-210">Before serving breakfast, you want to await the task that represents toasting the bread before adding butter and jam.</span></span> <span data-ttu-id="06103-211">Вы можете представить эту работу следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="06103-211">You can represent that work with the following code:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V3/Program.cs" ID="SnippetComposeToastTask":::

<span data-ttu-id="06103-212">Предыдущий метод имеет `async` модификатор в сигнатуре.</span><span class="sxs-lookup"><span data-stu-id="06103-212">The preceding method has the `async` modifier in its signature.</span></span> <span data-ttu-id="06103-213">Он сообщает компилятору, что этот метод содержит инструкцию `await`; она содержит асинхронные операции.</span><span class="sxs-lookup"><span data-stu-id="06103-213">That signals to the compiler that this method contains an `await` statement; it contains asynchronous operations.</span></span> <span data-ttu-id="06103-214">Этот метод представляет задачу, в рамках которой поджаривается хлеб, а затем добавляется масло и джем.</span><span class="sxs-lookup"><span data-stu-id="06103-214">This method represents the task that toasts the bread, then adds butter and jam.</span></span> <span data-ttu-id="06103-215">Этот метод возвращает <xref:System.Threading.Tasks.Task%601>, представляющий сочетание этих трех операций.</span><span class="sxs-lookup"><span data-stu-id="06103-215">This method returns a <xref:System.Threading.Tasks.Task%601> that represents the composition of those three operations.</span></span> <span data-ttu-id="06103-216">Теперь вид основного блока кода будет таким:</span><span class="sxs-lookup"><span data-stu-id="06103-216">The main block of code now becomes:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V3/Program.cs" ID="SnippetMain":::

<span data-ttu-id="06103-217">Предыдущее изменение показывает важную методику для работы с асинхронным кодом.</span><span class="sxs-lookup"><span data-stu-id="06103-217">The previous change illustrated an important technique for working with asynchronous code.</span></span> <span data-ttu-id="06103-218">Составные задачи можно создавать, разделяя операции в новом методе, который возвращает задачу.</span><span class="sxs-lookup"><span data-stu-id="06103-218">You compose tasks by separating the operations into a new method that returns a task.</span></span> <span data-ttu-id="06103-219">Вы можете выбрать, когда следует ожидать выполнения созданной задачи.</span><span class="sxs-lookup"><span data-stu-id="06103-219">You can choose when to await that task.</span></span> <span data-ttu-id="06103-220">Одновременно можно запускать другие задачи.</span><span class="sxs-lookup"><span data-stu-id="06103-220">You can start other tasks concurrently.</span></span>

## <a name="asynchronous-exceptions"></a><span data-ttu-id="06103-221">Асинхронные исключения</span><span class="sxs-lookup"><span data-stu-id="06103-221">Asynchronous exceptions</span></span>

<span data-ttu-id="06103-222">До этого момента вы неявно предполагали, что все эти задачи были выполнены успешно.</span><span class="sxs-lookup"><span data-stu-id="06103-222">Up to this point, you've implicitly assumed that all these tasks complete successfully.</span></span> <span data-ttu-id="06103-223">Асинхронные методы создают исключения, точно так же, как и синхронные методы.</span><span class="sxs-lookup"><span data-stu-id="06103-223">Asynchronous methods throw exceptions, just like their synchronous counterparts.</span></span> <span data-ttu-id="06103-224">В целом поддержка исключений и обработки ошибок в асинхронном коде преследует те же цели, что и поддержка асинхронного кода в целом: необходимо написать код, который выглядит как последовательность синхронных инструкций.</span><span class="sxs-lookup"><span data-stu-id="06103-224">Asynchronous support for exceptions and error handling strives for the same goals as asynchronous support in general: You should write code that reads like a series of synchronous statements.</span></span> <span data-ttu-id="06103-225">Когда задачи не могут быть успешно завершены, они выдают исключения.</span><span class="sxs-lookup"><span data-stu-id="06103-225">Tasks throw exceptions when they can't complete successfully.</span></span> <span data-ttu-id="06103-226">Клиентский код может перехватывать эти исключения, когда запущенная задача ожидается (`awaited`).</span><span class="sxs-lookup"><span data-stu-id="06103-226">The client code can catch those exceptions when a started task is `awaited`.</span></span> <span data-ttu-id="06103-227">Например, предположим, что тостер загорается во время приготовления тоста.</span><span class="sxs-lookup"><span data-stu-id="06103-227">For example, let's assume that the toaster catches fire while making the toast.</span></span> <span data-ttu-id="06103-228">Это можно смоделировать, изменив метод `ToastBreadAsync` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="06103-228">You can simulate that by modifying the `ToastBreadAsync` method to match the following code:</span></span>

```csharp
private static async Task<Toast> ToastBreadAsync(int slices)
{
    for (int slice = 0; slice < slices; slice++)
    {
        Console.WriteLine("Putting a slice of bread in the toaster");
    }
    Console.WriteLine("Start toasting...");
    await Task.Delay(2000);
    Console.WriteLine("Fire! Toast is ruined!");
    throw new InvalidOperationException("The toaster is on fire");
    await Task.Delay(1000);
    Console.WriteLine("Remove toast from toaster");

    return new Toast();
}
```

> [!NOTE]
> <span data-ttu-id="06103-229">При компиляции предыдущего кода будет выдано предупреждение о наличии недостижимого кода.</span><span class="sxs-lookup"><span data-stu-id="06103-229">You'll get a warning when you compile the preceding code regarding unreachable code.</span></span> <span data-ttu-id="06103-230">Это сделано намеренно, поскольку после того, как тостер загорится, дальнейшие операции не будут выполняться обычным образом.</span><span class="sxs-lookup"><span data-stu-id="06103-230">That's intentional, because once the toaster catches fire, operations won't proceed normally.</span></span>

<span data-ttu-id="06103-231">Запустите приложение после внесения этих изменений, и вы получите следующий результат:</span><span class="sxs-lookup"><span data-stu-id="06103-231">Run the application after making these changes, and you'll output similar to the following text:</span></span>

```console
Pouring coffee
coffee is ready
Warming the egg pan...
putting 3 slices of bacon in the pan
cooking first side of bacon...
Putting a slice of bread in the toaster
Putting a slice of bread in the toaster
Start toasting...
Fire! Toast is ruined!
flipping a slice of bacon
flipping a slice of bacon
flipping a slice of bacon
cooking the second side of bacon...
cracking 2 eggs
cooking the eggs ...
Put bacon on plate
Put eggs on plate
eggs are ready
bacon is ready
Unhandled exception. System.InvalidOperationException: The toaster is on fire
   at AsyncBreakfast.Program.ToastBreadAsync(Int32 slices) in Program.cs:line 65
   at AsyncBreakfast.Program.MakeToastWithButterAndJamAsync(Int32 number) in Program.cs:line 36
   at AsyncBreakfast.Program.Main(String[] args) in Program.cs:line 24
   at AsyncBreakfast.Program.<Main>(String[] args)
```

<span data-ttu-id="06103-232">Обратите внимание, что между возгоранием тостера и выдачей исключения выполняется довольно много задач.</span><span class="sxs-lookup"><span data-stu-id="06103-232">Notice that there's quite a few tasks completing between when the toaster catches fire and the exception is observed.</span></span> <span data-ttu-id="06103-233">Если задача, которая выполняется асинхронно, выдает исключение, эта задача завершается ***с ошибкой***.</span><span class="sxs-lookup"><span data-stu-id="06103-233">When a task that runs asynchronously throws an exception, that Task is ***faulted***.</span></span> <span data-ttu-id="06103-234">Созданное исключение находится в свойстве <xref:System.Threading.Tasks.Task.Exception?displayProperty=nameWithType> объекта Task.</span><span class="sxs-lookup"><span data-stu-id="06103-234">The Task object holds the exception thrown in the <xref:System.Threading.Tasks.Task.Exception?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="06103-235">Задачи, завершившиеся с ошибкой, выдают исключение, когда эти задачи ожидаются.</span><span class="sxs-lookup"><span data-stu-id="06103-235">Faulted tasks throw an exception when they're awaited.</span></span>

<span data-ttu-id="06103-236">Существует два важных механизма, работу которых нужно понимать: как исключение хранится в задаче, завершившейся с ошибкой, и как оно распаковывается и выдается повторно, когда код ожидает задачу, завершившуюся с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="06103-236">There are two important mechanisms to understand: how an exception is stored in a faulted task, and how an exception is unpackaged and rethrown when code awaits a faulted task.</span></span>

<span data-ttu-id="06103-237">Когда асинхронный код выдает исключение, это исключение хранится в `Task`.</span><span class="sxs-lookup"><span data-stu-id="06103-237">When code running asynchronously throws an exception, that exception is stored in the `Task`.</span></span> <span data-ttu-id="06103-238">Свойство <xref:System.Threading.Tasks.Task.Exception?displayProperty=nameWithType> имеет значение <xref:System.AggregateException?displayProperty=nameWithType>, потому что во время асинхронного выполнения может быть выдано несколько исключений.</span><span class="sxs-lookup"><span data-stu-id="06103-238">The <xref:System.Threading.Tasks.Task.Exception?displayProperty=nameWithType> property is an <xref:System.AggregateException?displayProperty=nameWithType> because more than one exception may be thrown during asynchronous work.</span></span> <span data-ttu-id="06103-239">Все выданные исключения добавляются в коллекцию <xref:System.AggregateException.InnerExceptions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06103-239">Any exception thrown is added to the <xref:System.AggregateException.InnerExceptions?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="06103-240">Если это свойство `Exception` имеет значение null, то создается новое исключение `AggregateException`, и выданное исключение становится первым элементом в коллекции.</span><span class="sxs-lookup"><span data-stu-id="06103-240">If that `Exception` property is null, a new `AggregateException` is created and the thrown exception is the first item in the collection.</span></span>

<span data-ttu-id="06103-241">Чаще всего для задачи, завершившейся с ошибкой, свойство `Exception` содержит только одно исключение.</span><span class="sxs-lookup"><span data-stu-id="06103-241">The most common scenario for a faulted task is that the `Exception` property contains exactly one exception.</span></span> <span data-ttu-id="06103-242">Когда код ожидает (`awaits`) задачу, завершившуюся сбоем, первое исключение в коллекции <xref:System.AggregateException.InnerExceptions?displayProperty=nameWithType> выдается повторно.</span><span class="sxs-lookup"><span data-stu-id="06103-242">When code `awaits` a faulted task, the first exception in the <xref:System.AggregateException.InnerExceptions?displayProperty=nameWithType> collection is rethrown.</span></span> <span data-ttu-id="06103-243">Поэтому в выходных данных этого примера мы видим `InvalidOperationException` вместо `AggregateException`.</span><span class="sxs-lookup"><span data-stu-id="06103-243">That's why the output from this example shows an `InvalidOperationException` instead of an `AggregateException`.</span></span> <span data-ttu-id="06103-244">Извлечение первого внутреннего исключения делает работу с асинхронными методами настолько похожей на работу с синхронными методами, насколько это возможно.</span><span class="sxs-lookup"><span data-stu-id="06103-244">Extracting the first inner exception makes working with asynchronous methods as similar as possible to working with their synchronous counterparts.</span></span> <span data-ttu-id="06103-245">Если ваш сценарий может создать несколько исключений, вы можете проверить свойство `Exception` в коде.</span><span class="sxs-lookup"><span data-stu-id="06103-245">You can examine the `Exception` property in your code when your scenario may generate multiple exceptions.</span></span>

<span data-ttu-id="06103-246">Перед тем как продолжить, закомментируйте эти две строки в методе `ToastBreadAsync`.</span><span class="sxs-lookup"><span data-stu-id="06103-246">Before going on, comment out these two lines in your `ToastBreadAsync` method.</span></span> <span data-ttu-id="06103-247">Ведь вы не хотите, чтобы у вас появилась еще одна проблема:</span><span class="sxs-lookup"><span data-stu-id="06103-247">You don't want to start another fire:</span></span>

```csharp
Console.WriteLine("Fire! Toast is ruined!");
throw new InvalidOperationException("The toaster is on fire");
```

## <a name="await-tasks-efficiently"></a><span data-ttu-id="06103-248">Эффективное ожидание задач</span><span class="sxs-lookup"><span data-stu-id="06103-248">Await tasks efficiently</span></span>

<span data-ttu-id="06103-249">Ряд инструкций `await` в конце приведенного выше кода можно улучшить с помощью методов класса `Task`.</span><span class="sxs-lookup"><span data-stu-id="06103-249">The series of `await` statements at the end of the preceding code can be improved by using methods of the `Task` class.</span></span> <span data-ttu-id="06103-250">Один из этих API — <xref:System.Threading.Tasks.Task.WhenAll%2A>, который возвращает <xref:System.Threading.Tasks.Task>; она завершается после завершения всех задач в списке аргументов, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="06103-250">One of those APIs is <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns a <xref:System.Threading.Tasks.Task> that completes when all the tasks in its argument list have completed, as shown in the following code:</span></span>

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

<span data-ttu-id="06103-251">Другой вариант — использовать <xref:System.Threading.Tasks.Task.WhenAny%2A>, который возвращает `Task<Task>`, выполняемый по завершении любого из своих аргументов.</span><span class="sxs-lookup"><span data-stu-id="06103-251">Another option is to use <xref:System.Threading.Tasks.Task.WhenAny%2A>, which returns a `Task<Task>` that completes when any of its arguments completes.</span></span> <span data-ttu-id="06103-252">Можно ожидать возвращенной задачи, зная, что она уже завершена.</span><span class="sxs-lookup"><span data-stu-id="06103-252">You can await the returned task, knowing that it has already finished.</span></span> <span data-ttu-id="06103-253">В следующем коде показано, как использовать <xref:System.Threading.Tasks.Task.WhenAny%2A> для ожидания первой задачи, чтобы затем обработать ее результат.</span><span class="sxs-lookup"><span data-stu-id="06103-253">The following code shows how you could use <xref:System.Threading.Tasks.Task.WhenAny%2A> to await the first task to finish and then process its result.</span></span> <span data-ttu-id="06103-254">После обработки результата завершенной задачи удалим ее из списка задач, передаваемого в `WhenAny`.</span><span class="sxs-lookup"><span data-stu-id="06103-254">After processing the result from the completed task, you remove that completed task from the list of tasks passed to `WhenAny`.</span></span>

```csharp
var breakfastTasks = new List<Task> { eggsTask, baconTask, toastTask };
while (breakfastTasks.Count > 0)
{
    Task finishedTask = await Task.WhenAny(breakfastTasks);
    if (finishedTask == eggsTask)
    {
        Console.WriteLine("eggs are ready");
    }
    else if (finishedTask == baconTask)
    {
        Console.WriteLine("bacon is ready");
    }
    else if (finishedTask == toastTask)
    {
        Console.WriteLine("toast is ready");
    }
    breakfastTasks.Remove(finishedTask);
}
```

<span data-ttu-id="06103-255">После всех этих изменений окончательная версия кода выглядит так: <a id="final-version"></a></span><span class="sxs-lookup"><span data-stu-id="06103-255">After all those changes, the final version of the code looks like this: <a id="final-version"></a></span></span>
:::code language="csharp" source="snippets/index/AsyncBreakfast-final/Program.cs" highlight="9-40":::

:::image type="content" source="media/whenany-async-breakfast.png" alt-text="Асинхронное приготовление завтрака при завершении любого из аргументов":::

<span data-ttu-id="06103-257">Окончательная версия асинхронного приготовления завтрака заняла примерно 15 минут, так как в этом случае некоторые задачи выполнялись параллельно, а также одновременно отслеживались несколько задач из кода и действия выполнялись только тогда, когда это было необходимо.</span><span class="sxs-lookup"><span data-stu-id="06103-257">The final version of the asynchronously prepared breakfast took roughly 15 minutes because some tasks ran concurrently, and the code monitored multiple tasks at once and only take action when it was needed.</span></span>

<span data-ttu-id="06103-258">Этот итоговый код выполняется асинхронно.</span><span class="sxs-lookup"><span data-stu-id="06103-258">This final code is asynchronous.</span></span> <span data-ttu-id="06103-259">Он более точно отражает, как пользователь будет готовить завтрак.</span><span class="sxs-lookup"><span data-stu-id="06103-259">It more accurately reflects how a person would cook a breakfast.</span></span> <span data-ttu-id="06103-260">Сравните предыдущий код с первым примером кода в этой статье.</span><span class="sxs-lookup"><span data-stu-id="06103-260">Compare the preceding code with the first code sample in this article.</span></span> <span data-ttu-id="06103-261">Основные действия по-прежнему очевидны при прочтении.</span><span class="sxs-lookup"><span data-stu-id="06103-261">The core actions are still clear from reading the code.</span></span> <span data-ttu-id="06103-262">Этот код можно прочитать так же, как указания по приготовлению завтрака в начале этой статьи.</span><span class="sxs-lookup"><span data-stu-id="06103-262">You can read this code the same way you'd read those instructions for making a breakfast at the beginning of this article.</span></span> <span data-ttu-id="06103-263">Возможности языка для `async` и `await` делают возможными преобразования, которые любой человек производит, выполняя эти инструкции: запуск задач без блокировки в ожидании их завершения.</span><span class="sxs-lookup"><span data-stu-id="06103-263">The language features for `async` and `await` provide the translation every person makes to follow those written instructions: start tasks as you can and don't block waiting for tasks to complete.</span></span>

## <a name="next-steps"></a><span data-ttu-id="06103-264">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="06103-264">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="06103-265">Исследование реальных сценариев для асинхронных программ</span><span class="sxs-lookup"><span data-stu-id="06103-265">Explore real world scenarios for asynchronous programs</span></span>](../../../async.md)
