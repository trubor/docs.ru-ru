---
title: Работа с LINQ
description: В этом руководстве мы научим вас создавать последовательности с помощью LINQ, создавать методы для использования в запросах LINQ, а также различать упреждающее и отложенное вычисление.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e6c241e90865335707f8d050f4bf8772f945355d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874502"
---
# <a name="work-with-language-integrated-query-linq"></a><span data-ttu-id="002dc-103">Работа с запросами LINQ</span><span class="sxs-lookup"><span data-stu-id="002dc-103">Work with Language-Integrated Query (LINQ)</span></span>

## <a name="introduction"></a><span data-ttu-id="002dc-104">Введение</span><span class="sxs-lookup"><span data-stu-id="002dc-104">Introduction</span></span>

<span data-ttu-id="002dc-105">В этом руководстве описаны возможности .NET Core и C#.</span><span class="sxs-lookup"><span data-stu-id="002dc-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="002dc-106">Вы узнаете, как выполнять такие задачи.</span><span class="sxs-lookup"><span data-stu-id="002dc-106">You’ll learn how to:</span></span>

- <span data-ttu-id="002dc-107">создавать последовательности с помощью LINQ;</span><span class="sxs-lookup"><span data-stu-id="002dc-107">Generate sequences with LINQ.</span></span>
- <span data-ttu-id="002dc-108">писать методы, которые можно применять в запросах LINQ;</span><span class="sxs-lookup"><span data-stu-id="002dc-108">Write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="002dc-109">различать упреждающее и отложенное вычисление.</span><span class="sxs-lookup"><span data-stu-id="002dc-109">Distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="002dc-110">Вы освоите эти методы на примере приложения, которое демонстрирует один из основных навыков любого иллюзиониста: [тасовка по методу фаро](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="002dc-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="002dc-111">Так называют метод тасовки, при котором колода делится ровно на две части, а затем собирается заново так, что карты из каждой половины следуют строго поочередно.</span><span class="sxs-lookup"><span data-stu-id="002dc-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="002dc-112">Этот метод очень удобен для иллюзионистов, поскольку положение каждой карты после каждой тасовки точно известно, и через несколько циклов порядок карт восстанавливается.</span><span class="sxs-lookup"><span data-stu-id="002dc-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="002dc-113">Здесь же он используется в качестве не слишком серьезного примера для процессов управления последовательностями данных.</span><span class="sxs-lookup"><span data-stu-id="002dc-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="002dc-114">Приложение, которое вы создадите, будет моделировать колоду карт и выполнять для них серию тасовок, выводя новый порядок карт после каждой из них.</span><span class="sxs-lookup"><span data-stu-id="002dc-114">The application you'll build constructs a card deck and then performs a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="002dc-115">Вы сможете сравнить новый порядок карт с исходным.</span><span class="sxs-lookup"><span data-stu-id="002dc-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="002dc-116">Это руководство описывает несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="002dc-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="002dc-117">После каждого из них вы сможете запустить приложение и оценить результаты.</span><span class="sxs-lookup"><span data-stu-id="002dc-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="002dc-118">[Готовый пример](https://github.com/dotnet/samples/blob/main/csharp/getting-started/console-linq) доступен в репозитории dotnet/samples на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="002dc-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/main/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="002dc-119">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="002dc-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="002dc-120">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="002dc-120">Prerequisites</span></span>

<span data-ttu-id="002dc-121">Компьютер должен быть настроен для выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="002dc-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="002dc-122">Инструкции по установке см. на странице [Загрузка.NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="002dc-122">You can find the installation instructions on the [.NET Core Download](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="002dc-123">Это приложение можно запустить в ОС Windows, Ubuntu Linux или OS X, а также в контейнере Docker.</span><span class="sxs-lookup"><span data-stu-id="002dc-123">You can run this application on Windows, Ubuntu Linux, or OS X, or in a Docker container.</span></span> <span data-ttu-id="002dc-124">Вам потребуется редактор кода, но вы можете выбрать любой привычный для вас.</span><span class="sxs-lookup"><span data-stu-id="002dc-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="002dc-125">В примерах ниже используется кроссплатформенный редактор [Visual Studio Code](https://code.visualstudio.com/) с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="002dc-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross-platform editor.</span></span> <span data-ttu-id="002dc-126">Вы можете заменить его на любое другое средство, с которым вам удобно работать.</span><span class="sxs-lookup"><span data-stu-id="002dc-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="002dc-127">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="002dc-127">Create the Application</span></span>

<span data-ttu-id="002dc-128">Первым шагом является создание нового приложения.</span><span class="sxs-lookup"><span data-stu-id="002dc-128">The first step is to create a new application.</span></span> <span data-ttu-id="002dc-129">Откройте командную строку и создайте новый каталог для приложения.</span><span class="sxs-lookup"><span data-stu-id="002dc-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="002dc-130">Перейдите в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="002dc-130">Make that the current directory.</span></span> <span data-ttu-id="002dc-131">В командной строке введите команду `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="002dc-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="002dc-132">Эта команда создает начальный набор файлов для базового приложения Hello World.</span><span class="sxs-lookup"><span data-stu-id="002dc-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="002dc-133">Если вы раньше никогда не работали с C#, изучите структуру программы C# по [этому руководству](console-teleprompter.md).</span><span class="sxs-lookup"><span data-stu-id="002dc-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="002dc-134">Мы рекомендуем сначала ознакомиться с ним, а затем вернуться сюда и продолжить изучение LINQ.</span><span class="sxs-lookup"><span data-stu-id="002dc-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="create-the-data-set"></a><span data-ttu-id="002dc-135">Создание набора данных</span><span class="sxs-lookup"><span data-stu-id="002dc-135">Create the Data Set</span></span>

<span data-ttu-id="002dc-136">Перед началом работы убедитесь, что в верхней части файла `Program.cs`, созданного `dotnet new console`, находятся следующие строки:</span><span class="sxs-lookup"><span data-stu-id="002dc-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="002dc-137">Если эти три строки (инструкции `using`) находятся не в верхней части файла, наша программа не будет компилироваться.</span><span class="sxs-lookup"><span data-stu-id="002dc-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="002dc-138">Теперь, когда у вас есть все необходимые ссылки, посмотрите, из чего состоит колода карт.</span><span class="sxs-lookup"><span data-stu-id="002dc-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="002dc-139">Как правило, в колоде игральных карт четыре масти и в каждой масти по тринадцать значений.</span><span class="sxs-lookup"><span data-stu-id="002dc-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="002dc-140">Вы можете создать класс `Card` сразу же и заполнить коллекцию объектами `Card` вручную.</span><span class="sxs-lookup"><span data-stu-id="002dc-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="002dc-141">С помощью LINQ колоду карт можно создать гораздо быстрее, чем обычным способом.</span><span class="sxs-lookup"><span data-stu-id="002dc-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="002dc-142">Вместо класса `Card` вы можете создать две последовательности, представляющие масти и ранги соответственно.</span><span class="sxs-lookup"><span data-stu-id="002dc-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="002dc-143">Вы создадите два очень простых [*метода итератора*](../iterators.md#enumeration-sources-with-iterator-methods), которые будут создавать ранги и масти как <xref:System.Collections.Generic.IEnumerable%601> строк:</span><span class="sxs-lookup"><span data-stu-id="002dc-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

```csharp
// Program.cs
// The Main() method

static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="002dc-144">Разместите их под методом `Main` в вашем файле `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="002dc-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="002dc-145">Оба эти два метода используют синтаксис `yield return`, создавая последовательность по мере выполнения.</span><span class="sxs-lookup"><span data-stu-id="002dc-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="002dc-146">Компилятор создаст объект, который реализует интерфейс <xref:System.Collections.Generic.IEnumerable%601>, и сохранит в него последовательность строк по мере их получения.</span><span class="sxs-lookup"><span data-stu-id="002dc-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="002dc-147">Теперь с помощью этих методов итератора создайте колоду карт.</span><span class="sxs-lookup"><span data-stu-id="002dc-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="002dc-148">Поместите запрос LINQ в метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="002dc-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="002dc-149">Это описано ниже:</span><span class="sxs-lookup"><span data-stu-id="002dc-149">Here's a look at it:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

<span data-ttu-id="002dc-150">Несколько выражений `from` создают запрос <xref:System.Linq.Enumerable.SelectMany%2A>, который формирует одну последовательность из сочетаний каждого элемента первой последовательности с каждым элементом второй последовательности.</span><span class="sxs-lookup"><span data-stu-id="002dc-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="002dc-151">Для нашего примера важен порядок последовательности.</span><span class="sxs-lookup"><span data-stu-id="002dc-151">The order is important for our purposes.</span></span> <span data-ttu-id="002dc-152">Первый элемент первой последовательности (масти) поочередно сочетается с каждым элементом второй последовательности (ранги).</span><span class="sxs-lookup"><span data-stu-id="002dc-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="002dc-153">В итоге мы получаем все тринадцать карт первой масти.</span><span class="sxs-lookup"><span data-stu-id="002dc-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="002dc-154">Этот процесс повторяется для каждого элемента первой последовательности (масти).</span><span class="sxs-lookup"><span data-stu-id="002dc-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="002dc-155">Конечным результатом является колода карт, упорядоченная сначала по мастям, а затем по достоинствам.</span><span class="sxs-lookup"><span data-stu-id="002dc-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="002dc-156">Важно помнить, что независимо от того, будете ли вы записывать LINQ в синтаксисе запросов, показанном выше, или вместо этого будете использовать синтаксис методов, вы всегда можете перейти от одной формы синтаксиса к другой.</span><span class="sxs-lookup"><span data-stu-id="002dc-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="002dc-157">Приведенный выше запрос, записанный в синтаксисе запросов, можно записать в синтаксис метода следующим образом:</span><span class="sxs-lookup"><span data-stu-id="002dc-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="002dc-158">Компилятор преобразует инструкции LINQ, написанные с помощью синтаксиса запросов, в эквивалентный синтаксис вызова метода.</span><span class="sxs-lookup"><span data-stu-id="002dc-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="002dc-159">Таким образом, независимо от выбранного синтаксиса, две версии запроса дают одинаковый результат.</span><span class="sxs-lookup"><span data-stu-id="002dc-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="002dc-160">Выберите, какой синтаксис лучше всего подходит для вашей ситуации. Например, если вы работаете в команде, в которой у некоторых участников есть сложности с синтаксисом метода, попробуйте использовать синтаксис запроса.</span><span class="sxs-lookup"><span data-stu-id="002dc-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="002dc-161">Теперь давайте выполним пример, который вы создали к этому моменту.</span><span class="sxs-lookup"><span data-stu-id="002dc-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="002dc-162">Он отобразит все 52 карты колоды.</span><span class="sxs-lookup"><span data-stu-id="002dc-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="002dc-163">Возможно, вам будет интересно выполнить этот пример в отладчике и проследить за выполнением методов `Suits()` и `Ranks()`.</span><span class="sxs-lookup"><span data-stu-id="002dc-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="002dc-164">Вы сможете заметить, что каждая строка в каждой последовательности создается только по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="002dc-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Окно консоли с приложением, которое выводит 52 карты](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a><span data-ttu-id="002dc-166">Обработка порядка</span><span class="sxs-lookup"><span data-stu-id="002dc-166">Manipulate the Order</span></span>

<span data-ttu-id="002dc-167">Теперь рассмотрим, как вы будете тасовать карты в колоде.</span><span class="sxs-lookup"><span data-stu-id="002dc-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="002dc-168">Чтобы хорошо потасовать, сначала необходимо разделить колоду на две части.</span><span class="sxs-lookup"><span data-stu-id="002dc-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="002dc-169">Эту возможность вам предоставят методы <xref:System.Linq.Enumerable.Take%2A> и <xref:System.Linq.Enumerable.Skip%2A>, входящие в интерфейсы API LINQ.</span><span class="sxs-lookup"><span data-stu-id="002dc-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="002dc-170">Поместите их под циклом `foreach`:</span><span class="sxs-lookup"><span data-stu-id="002dc-170">Place them underneath the `foreach` loop:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

<span data-ttu-id="002dc-171">В стандартной библиотеке нет метода для тасовки, которым можно было бы воспользоваться, поэтому вам нужно написать собственный.</span><span class="sxs-lookup"><span data-stu-id="002dc-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="002dc-172">Метод для тасовки, который вы создадите, иллюстрирует несколько приемов, которые вы будете использовать в программах на основе LINQ, поэтому каждая часть этого процесса будет описана в действиях.</span><span class="sxs-lookup"><span data-stu-id="002dc-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="002dc-173">Чтобы добавить некоторые функции для взаимодействия с <xref:System.Collections.Generic.IEnumerable%601>, который будет возвращен в запросах LINQ, вам потребуется написать особые методы, называемые [методами расширения](../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="002dc-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="002dc-174">Короче говоря, метод расширения представляет собой специализированный *статический метод*, добавляющий новые функциональные возможности в уже имеющийся тип без изменения исходного типа, в который необходимо добавить функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="002dc-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="002dc-175">Переместите методы расширения в другое расположение, добавив новый файл *статического* класса в программу с именем `Extensions.cs`, а затем приступите к разработке первого метода расширения:</span><span class="sxs-lookup"><span data-stu-id="002dc-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

<span data-ttu-id="002dc-176">Обратите внимание на сигнатуру метода, в частности на параметры:</span><span class="sxs-lookup"><span data-stu-id="002dc-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="002dc-177">Как вы видите, для первого аргумента этого метода добавлен модификатор `this`.</span><span class="sxs-lookup"><span data-stu-id="002dc-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="002dc-178">Это означает, что метод вызывается так, как если бы он был методом-членом и имел тип, указанный для первого аргумента.</span><span class="sxs-lookup"><span data-stu-id="002dc-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="002dc-179">Такое объявление методов соответствует стандартному принципу, по которому для входа и выхода используется тип `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="002dc-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="002dc-180">Такая практика позволяет объединять методы LINQ в цепочку, чтобы создавать более сложные запросы.</span><span class="sxs-lookup"><span data-stu-id="002dc-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="002dc-181">Очевидно, что так как вы разделили колоду на две части, их необходимо соединить.</span><span class="sxs-lookup"><span data-stu-id="002dc-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="002dc-182">В коде это означает, что необходимо перечислить обе последовательности, полученные с помощью <xref:System.Linq.Enumerable.Take%2A> и <xref:System.Linq.Enumerable.Skip%2A> за один раз, применяя команду *`interleaving`* к элементам и создавая одну последовательность: колода карт, которая тасуется сейчас.</span><span class="sxs-lookup"><span data-stu-id="002dc-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="002dc-183">Чтобы создать метод LINQ, который работает с двумя последовательностями, важно хорошо понимать принципы работы <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="002dc-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="002dc-184">Интерфейс <xref:System.Collections.Generic.IEnumerable%601> содержит один метод: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="002dc-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="002dc-185">Этот метод <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> возвращает объект, у которого есть метод для перехода к следующему элементу и свойство, которое возвращает текущий элемент в последовательности.</span><span class="sxs-lookup"><span data-stu-id="002dc-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="002dc-186">С помощью этих двух членов вы выполните перебор всей коллекции и получение элементов.</span><span class="sxs-lookup"><span data-stu-id="002dc-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="002dc-187">Метод Interleave будет реализован как метод итератора, поэтому вы не будете создавать и возвращать коллекцию, а примените описанный выше синтаксис `yield return`.</span><span class="sxs-lookup"><span data-stu-id="002dc-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="002dc-188">Так выглядит реализация этого метода:</span><span class="sxs-lookup"><span data-stu-id="002dc-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="002dc-189">Теперь, добавив в проект этот метод, вернитесь к методу `Main` и один раз перетасуйте колоду:</span><span class="sxs-lookup"><span data-stu-id="002dc-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="002dc-190">Сравнение</span><span class="sxs-lookup"><span data-stu-id="002dc-190">Comparisons</span></span>

<span data-ttu-id="002dc-191">Через сколько тасовок колода снова соберется в исходном порядке?</span><span class="sxs-lookup"><span data-stu-id="002dc-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="002dc-192">Чтобы узнать это, вам нужно написать метод, который проверяет равенство двух последовательностей.</span><span class="sxs-lookup"><span data-stu-id="002dc-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="002dc-193">Создав такой метод, вы поместите код тасовки колоды в цикл, в котором будете проверять, расположены ли карты в правильном порядке.</span><span class="sxs-lookup"><span data-stu-id="002dc-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="002dc-194">Метод, который сравнивает две последовательности, будет очень простым.</span><span class="sxs-lookup"><span data-stu-id="002dc-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="002dc-195">По структуре он похож на метод, который мы создали для тасовки колоды.</span><span class="sxs-lookup"><span data-stu-id="002dc-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="002dc-196">Но теперь вместо команды `yield return`, которая возвращает элементы, вы будете сравнивать элементы каждой последовательности.</span><span class="sxs-lookup"><span data-stu-id="002dc-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="002dc-197">Если перечисление последовательности завершилось и все элементы попарно совпадают, то последовательности считаются одинаковыми:</span><span class="sxs-lookup"><span data-stu-id="002dc-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="002dc-198">Здесь мы видим в действии второй принцип LINQ: терминальные методы.</span><span class="sxs-lookup"><span data-stu-id="002dc-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="002dc-199">Они принимают последовательность в качестве входных данных (или две последовательности, как в нашем примере) и возвращают скалярное значение.</span><span class="sxs-lookup"><span data-stu-id="002dc-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="002dc-200">В цепочке методов для запроса LINQ терминальные методы всегда используются последними, отсюда и название "терминальный".</span><span class="sxs-lookup"><span data-stu-id="002dc-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="002dc-201">Этот принцип мы применяем при определении того, находится ли колода в исходном порядке.</span><span class="sxs-lookup"><span data-stu-id="002dc-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="002dc-202">Поместите код тасовки в цикл, который будет останавливаться в том случае, когда порядок последовательности восстановлен. Для проверки примените метод `SequenceEquals()`.</span><span class="sxs-lookup"><span data-stu-id="002dc-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="002dc-203">Как вы уже поняли, этот метод всегда будет последним в любом запросе, поскольку он возвращает одиночное значение, а не последовательность:</span><span class="sxs-lookup"><span data-stu-id="002dc-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="002dc-204">Выполните код и обратите внимание на то, как выполняется переупорядочивание колоды при каждой тасовке.</span><span class="sxs-lookup"><span data-stu-id="002dc-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="002dc-205">После 8 тасовок (итераций цикла do-while), колода возвращается к исходной конфигурации, в которой она находилась при создании из начального запроса LINQ.</span><span class="sxs-lookup"><span data-stu-id="002dc-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="002dc-206">Оптимизация</span><span class="sxs-lookup"><span data-stu-id="002dc-206">Optimizations</span></span>

<span data-ttu-id="002dc-207">Пример, который вы создали к этому моменту, выполняет *внутреннюю тасовку*, то есть первая и последняя карты колоды сохраняют свои позиции после каждой итерации.</span><span class="sxs-lookup"><span data-stu-id="002dc-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="002dc-208">Давайте внесем одно изменение: вместо этого мы будем использовать *внешнюю тасовку*, при которой все 52 карты изменяют свои позиции.</span><span class="sxs-lookup"><span data-stu-id="002dc-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="002dc-209">Для этого колоду нужно собирать так, чтобы первой картой в колоде стала первая карта из нижней половины.</span><span class="sxs-lookup"><span data-stu-id="002dc-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="002dc-210">Тогда самой нижней картой станет последняя карта из верхней половины колоды.</span><span class="sxs-lookup"><span data-stu-id="002dc-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="002dc-211">Это простое изменение в одной строке кода.</span><span class="sxs-lookup"><span data-stu-id="002dc-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="002dc-212">Обновите текущий запрос тасовки, переключив положения <xref:System.Linq.Enumerable.Take%2A> и <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="002dc-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="002dc-213">Это поменяет местами нижнюю и верхнюю половины колоды:</span><span class="sxs-lookup"><span data-stu-id="002dc-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="002dc-214">Снова запустите программу, и вы увидите, что для восстановления исходного порядка теперь требуется 52 итерации.</span><span class="sxs-lookup"><span data-stu-id="002dc-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="002dc-215">Также вы могли обратить внимание, что по мере выполнения программы она заметным образом замедляется.</span><span class="sxs-lookup"><span data-stu-id="002dc-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="002dc-216">Для этого есть сразу несколько причин.</span><span class="sxs-lookup"><span data-stu-id="002dc-216">There are a number of reasons for this.</span></span> <span data-ttu-id="002dc-217">Вы можете решить одну из самых существенных причин спада производительности — неэффективное использование [*отложенного вычисления*](../../standard/linq/deferred-execution-lazy-evaluation.md).</span><span class="sxs-lookup"><span data-stu-id="002dc-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../../standard/linq/deferred-execution-lazy-evaluation.md).</span></span>

<span data-ttu-id="002dc-218">Короче говоря, отложенное вычисление означает, что вычисление инструкции не выполняется, пока не понадобится ее значение.</span><span class="sxs-lookup"><span data-stu-id="002dc-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="002dc-219">Запросы LINQ — это инструкции, которые обрабатываются отложенным образом.</span><span class="sxs-lookup"><span data-stu-id="002dc-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="002dc-220">Последовательности создаются только тогда, когда происходит обращение к их элементам.</span><span class="sxs-lookup"><span data-stu-id="002dc-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="002dc-221">Обычно это дает LINQ огромное преимущество.</span><span class="sxs-lookup"><span data-stu-id="002dc-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="002dc-222">Но в некоторых программах, таких как в нашем примере, это приводит к экспоненциальному росту времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="002dc-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="002dc-223">Помните, что мы создали исходную колоду с помощью запроса LINQ.</span><span class="sxs-lookup"><span data-stu-id="002dc-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="002dc-224">Каждая последующая тасовка выполняет три запроса LINQ к колоде, полученной на предыдущем этапе.</span><span class="sxs-lookup"><span data-stu-id="002dc-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="002dc-225">И все эти запросы выполняются отложенно.</span><span class="sxs-lookup"><span data-stu-id="002dc-225">All these are performed lazily.</span></span> <span data-ttu-id="002dc-226">В частности, это означает, что запросы выполняются каждый раз при обращении к последовательности.</span><span class="sxs-lookup"><span data-stu-id="002dc-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="002dc-227">Таким образом, пока вы доберетесь до 52-й итерации, исходная колода будет заново создана очень много раз.</span><span class="sxs-lookup"><span data-stu-id="002dc-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="002dc-228">Чтобы наглядно это продемонстрировать, давайте создадим журнал выполнения.</span><span class="sxs-lookup"><span data-stu-id="002dc-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="002dc-229">Затем вы исправите эту проблему.</span><span class="sxs-lookup"><span data-stu-id="002dc-229">Then, you'll fix it.</span></span>

<span data-ttu-id="002dc-230">В вашем файле `Extensions.cs` введите или скопируйте приведенный ниже метод.</span><span class="sxs-lookup"><span data-stu-id="002dc-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="002dc-231">Этот метод расширения создает файл с именем `debug.log` в каталоге проекта и записывает в файл журнала, какой запрос выполняется в данный момент.</span><span class="sxs-lookup"><span data-stu-id="002dc-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="002dc-232">Этот метод расширения можно добавить к любому запросу, чтобы зафиксировать его выполнение.</span><span class="sxs-lookup"><span data-stu-id="002dc-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="002dc-233">Вы увидите красную волнистую линию под `File`, означающую, что его не существует.</span><span class="sxs-lookup"><span data-stu-id="002dc-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="002dc-234">Он не будет компилироваться, поскольку компилятор не знает, что такое `File`.</span><span class="sxs-lookup"><span data-stu-id="002dc-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="002dc-235">Чтобы решить эту проблему, добавьте следующую строку кода под самой первой строкой в `Extensions.cs`:</span><span class="sxs-lookup"><span data-stu-id="002dc-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="002dc-236">Это позволит решить проблему, и красная линия ошибки исчезнет.</span><span class="sxs-lookup"><span data-stu-id="002dc-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="002dc-237">Теперь давайте дополним определение каждого запроса сообщением для журнала:</span><span class="sxs-lookup"><span data-stu-id="002dc-237">Next, instrument the definition of each query with a log message:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
                .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
                .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="002dc-238">Обратите внимание, что запись в журнал не нужно выполнять при обращении к запросу.</span><span class="sxs-lookup"><span data-stu-id="002dc-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="002dc-239">Она выполняется только при создании исходного запроса.</span><span class="sxs-lookup"><span data-stu-id="002dc-239">You log only when you create the original query.</span></span> <span data-ttu-id="002dc-240">Программа по-прежнему работает очень долго, но теперь вы хорошо видите, почему.</span><span class="sxs-lookup"><span data-stu-id="002dc-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="002dc-241">Если у вас не хватит терпения выполнять внешнюю тасовку с ведением журнала, переключите программу обратно на внутреннюю тасовку.</span><span class="sxs-lookup"><span data-stu-id="002dc-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="002dc-242">На ней вы также заметите влияние отложенного вычисления.</span><span class="sxs-lookup"><span data-stu-id="002dc-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="002dc-243">За один запуск программа выполняет 2592 запроса, если учитывать все создания мастей и достоинств.</span><span class="sxs-lookup"><span data-stu-id="002dc-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="002dc-244">Вы можете повысить производительность кода, чтобы уменьшить количество выполнений.</span><span class="sxs-lookup"><span data-stu-id="002dc-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="002dc-245">Простой способ исправить — *кэшировать* результаты исходного запроса LINQ, который создает колоду карт.</span><span class="sxs-lookup"><span data-stu-id="002dc-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="002dc-246">В настоящее время вы выполняете запросы снова и снова каждый раз, когда цикл do-while проходит через итерацию, повторно создавая и перетасовывая колоду карт.</span><span class="sxs-lookup"><span data-stu-id="002dc-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="002dc-247">Чтобы кэшировать колоду карт, вы можете использовать методы LINQ <xref:System.Linq.Enumerable.ToArray%2A> и <xref:System.Linq.Enumerable.ToList%2A>. Когда вы добавляете их в запросы, они будут выполнять те действия, которые вы указали, но теперь они будут хранить результаты в массиве или списке в зависимости от того, какой метод вы вызовете.</span><span class="sxs-lookup"><span data-stu-id="002dc-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="002dc-248">Добавьте метод LINQ <xref:System.Linq.Enumerable.ToArray%2A> в оба запроса и снова запустите программу:</span><span class="sxs-lookup"><span data-stu-id="002dc-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="002dc-249">Теперь при внутренней тасовке выполняется всего 30 запросов.</span><span class="sxs-lookup"><span data-stu-id="002dc-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="002dc-250">Переключите программу на внешнюю тасовку, и вы заметите аналогичное улучшение: теперь выполняется 162 запроса.</span><span class="sxs-lookup"><span data-stu-id="002dc-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="002dc-251">Обратите внимание, что этот пример лишь **демонстрирует** варианты использования, в которых отложенное вычисление приводит к проблемам с производительностью.</span><span class="sxs-lookup"><span data-stu-id="002dc-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="002dc-252">Хотя очень важно знать, когда отложенное вычисление может повлиять на производительность кода, не менее важно понимать, что не все запросы должны выполняться упреждающе.</span><span class="sxs-lookup"><span data-stu-id="002dc-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="002dc-253">Если не использовать <xref:System.Linq.Enumerable.ToArray%2A>, производительность снизится. Это связано с тем, что каждое новое расположение карт вычисляется на основе предыдущего расположения.</span><span class="sxs-lookup"><span data-stu-id="002dc-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="002dc-254">Использование отложенного вычисления означает, что каждое расположение колоды строится с самого начала, из исходной колоды, включая вызов кода для создания `startingDeck`.</span><span class="sxs-lookup"><span data-stu-id="002dc-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="002dc-255">Это создает огромный объем дополнительной работы.</span><span class="sxs-lookup"><span data-stu-id="002dc-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="002dc-256">На практике некоторые алгоритмы хорошо работают с упреждающим вычислением, а другие хорошо выполняются с отложенным вычислением.</span><span class="sxs-lookup"><span data-stu-id="002dc-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="002dc-257">Для ежедневного использования отложенное вычисление обычно дает более хороший результат, если в качестве источника данных используется отдельный процесс, например база данных.</span><span class="sxs-lookup"><span data-stu-id="002dc-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="002dc-258">Для баз данных отложенное вычисление позволяет сложным запросам выполнять только один круговой путь к процессу базы данных и обратно к оставшемуся коду.</span><span class="sxs-lookup"><span data-stu-id="002dc-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="002dc-259">LINQ является гибким, независимо от того, используете ли вы отложенное или упреждающее вычисление, поэтому измерьте процессы и выберите тип вычислений, который обеспечивает наилучшую производительность.</span><span class="sxs-lookup"><span data-stu-id="002dc-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="002dc-260">Заключение</span><span class="sxs-lookup"><span data-stu-id="002dc-260">Conclusion</span></span>

<span data-ttu-id="002dc-261">В этом проекте вы изучили:</span><span class="sxs-lookup"><span data-stu-id="002dc-261">In this project, you covered:</span></span>

- <span data-ttu-id="002dc-262">использование запросов LINQ для агрегирования данных в осмысленную последовательность;</span><span class="sxs-lookup"><span data-stu-id="002dc-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="002dc-263">запись методов расширения для добавления собственных пользовательских функций в запросы LINQ;</span><span class="sxs-lookup"><span data-stu-id="002dc-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="002dc-264">поиск областей в коде, где могут возникнуть проблемы с производительностью наших запросов LINQ, например снижение скорости;</span><span class="sxs-lookup"><span data-stu-id="002dc-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="002dc-265">упреждающее и отложенное вычисление в отношении запросов LINQ и их влияние на производительность запросов.</span><span class="sxs-lookup"><span data-stu-id="002dc-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="002dc-266">Помимо LINQ вы узнали об использовании метода, который иллюзионисты используют для карточных фокусов.</span><span class="sxs-lookup"><span data-stu-id="002dc-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="002dc-267">Они используют тасовку по методу Фаро, потому что она позволяет хорошо контролировать положение каждой карты в колоде.</span><span class="sxs-lookup"><span data-stu-id="002dc-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="002dc-268">Теперь, когда вы все это знаете, не рассказывайте это остальным!</span><span class="sxs-lookup"><span data-stu-id="002dc-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="002dc-269">Дополнительные сведения о LINQ см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="002dc-269">For more information on LINQ, see:</span></span>

- [<span data-ttu-id="002dc-270">LINQ</span><span class="sxs-lookup"><span data-stu-id="002dc-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="002dc-271">Введение в LINQ</span><span class="sxs-lookup"><span data-stu-id="002dc-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="002dc-272">Основные операции запросов LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="002dc-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [<span data-ttu-id="002dc-273">Преобразования данных с помощью LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="002dc-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [<span data-ttu-id="002dc-274">Синтаксис запросов и синтаксис методов в LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="002dc-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [<span data-ttu-id="002dc-275">Возможности C#, поддерживающие LINQ</span><span class="sxs-lookup"><span data-stu-id="002dc-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
