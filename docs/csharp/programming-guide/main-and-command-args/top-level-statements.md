---
title: Операторы верхнего уровня. Руководство по программированию на C#
description: Узнайте об операторах верхнего уровня в C# 9 и более поздних версиях.
ms.date: 03/08/2021
helpviewer_keywords:
- C# language, top-level statements
- C# language, Main method
ms.openlocfilehash: 69ff5fd606f5e12f55bd3e6dfc15fc7e64d8352b
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190449"
---
# <a name="top-level-statements-c-programming-guide"></a><span data-ttu-id="fff45-103">Операторы верхнего уровня (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="fff45-103">Top-level statements (C# Programming Guide)</span></span>

<span data-ttu-id="fff45-104">Начиная с версии C# 9, метод `Main` не нужно явно включать в проект консольного приложения.</span><span class="sxs-lookup"><span data-stu-id="fff45-104">Starting in C# 9, you don't have to explicitly include a `Main` method in a console application project.</span></span> <span data-ttu-id="fff45-105">Вместо этого можно использовать *операторы верхнего уровня* для минимизации объема создаваемого кода.</span><span class="sxs-lookup"><span data-stu-id="fff45-105">Instead, you can use the *top-level statements* feature to minimize the code you have to write.</span></span> <span data-ttu-id="fff45-106">В этом случае компилятор создает класс и точку входа метода `Main` для приложения.</span><span class="sxs-lookup"><span data-stu-id="fff45-106">In this case, the compiler generates a class and `Main` method entry point for the application.</span></span>

<span data-ttu-id="fff45-107">Ниже приведен файл *Program.cs*, который является полноценной программой C# (версия С# 9):</span><span class="sxs-lookup"><span data-stu-id="fff45-107">Here's a *Program.cs* file that is a complete C# program in C# 9:</span></span>

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

<span data-ttu-id="fff45-108">Операторы верхнего уровня позволяют создавать простой программный код для небольших служебных программ, таких как Функции Azure и GitHub Actions.</span><span class="sxs-lookup"><span data-stu-id="fff45-108">Top-level statements let you write simple programs for small utilities such as Azure Functions and GitHub Actions.</span></span> <span data-ttu-id="fff45-109">Они также помогают начинающим программистам C# начать обучение и приступить к написанию кода.</span><span class="sxs-lookup"><span data-stu-id="fff45-109">They also make it simpler for new C# programmers to get started learning and writing code.</span></span>

<span data-ttu-id="fff45-110">В следующих разделах описываются правила, которые определяют использование операторов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="fff45-110">The following sections explain the rules on what you can and can't do with top-level statements.</span></span>

## <a name="only-one-top-level-file"></a><span data-ttu-id="fff45-111">Только один файл верхнего уровня</span><span class="sxs-lookup"><span data-stu-id="fff45-111">Only one top-level file</span></span>

<span data-ttu-id="fff45-112">Приложение должно иметь только одну точку входа, поэтому проект может содержать только один файл с операторами верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="fff45-112">An application must have only one entry point, so a project can have only one file with top-level statements.</span></span> <span data-ttu-id="fff45-113">Размещение операторов верхнего уровня в нескольких файлах в проекте приводит к следующей ошибке компилятора:</span><span class="sxs-lookup"><span data-stu-id="fff45-113">Putting top-level statements in more than one file in a project results in the following compiler error:</span></span>

> <span data-ttu-id="fff45-114">CS8802 Only one compilation unit can have top-level statements (Только одна единица компиляции может содержать операторы верхнего уровня).</span><span class="sxs-lookup"><span data-stu-id="fff45-114">CS8802 Only one compilation unit can have top-level statements.</span></span>

<span data-ttu-id="fff45-115">В проекте может содержаться любое количество дополнительных файлов с исходным кодом, в которых нет операторов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="fff45-115">A project can have any number of additional source code files that don't have top-level statements.</span></span>

## <a name="no-other-entry-points"></a><span data-ttu-id="fff45-116">Другие точки входа отсутствуют</span><span class="sxs-lookup"><span data-stu-id="fff45-116">No other entry points</span></span>

<span data-ttu-id="fff45-117">Метод `Main` можно написать явным образом, но он не может функционировать как точка входа.</span><span class="sxs-lookup"><span data-stu-id="fff45-117">You can write a `Main` method explicitly, but it can't function as an entry point.</span></span> <span data-ttu-id="fff45-118">Компилятор выдает следующее предупреждение:</span><span class="sxs-lookup"><span data-stu-id="fff45-118">The compiler issues the following warning:</span></span>

> <span data-ttu-id="fff45-119">CS7022 The entry point of the program is global code; ignoring 'Main()' entry point (Точка входа программы является глобальным кодом; точка входа Main() игнорируется).</span><span class="sxs-lookup"><span data-stu-id="fff45-119">CS7022 The entry point of the program is global code; ignoring 'Main()' entry point.</span></span>

<span data-ttu-id="fff45-120">В проекте с операторами верхнего уровня нельзя использовать параметр компилятора [-main](../../language-reference/compiler-options/main-compiler-option.md) для выбора точки входа, даже если в проекте есть один или несколько методов `Main`.</span><span class="sxs-lookup"><span data-stu-id="fff45-120">In a project with top-level statements, you can't use the [-main](../../language-reference/compiler-options/main-compiler-option.md) compiler option to select the entry point, even if the project has one or more `Main` methods.</span></span>

## <a name="using-directives"></a><span data-ttu-id="fff45-121">Директивы `using`</span><span class="sxs-lookup"><span data-stu-id="fff45-121">`using` directives</span></span>

<span data-ttu-id="fff45-122">Если вы включаете директивы using, они должны быть первыми в файле, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="fff45-122">If you include using directives, they must come first in the file, as in this example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

## <a name="global-namespace"></a><span data-ttu-id="fff45-123">Глобальное пространство имен</span><span class="sxs-lookup"><span data-stu-id="fff45-123">Global namespace</span></span>

<span data-ttu-id="fff45-124">Операторы верхнего уровня неявно находятся в глобальном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="fff45-124">Top-level statements are implicitly in the global namespace.</span></span>

## <a name="namespaces-and-type-definitions"></a><span data-ttu-id="fff45-125">Пространства имен и определения типов</span><span class="sxs-lookup"><span data-stu-id="fff45-125">Namespaces and type definitions</span></span>

<span data-ttu-id="fff45-126">Файл с операторами верхнего уровня может также содержать пространства имен и определения типов, но они должны следовать за операторами верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="fff45-126">A file with top-level statements can also contain namespaces and type definitions, but they must come after the top-level statements.</span></span> <span data-ttu-id="fff45-127">Пример:</span><span class="sxs-lookup"><span data-stu-id="fff45-127">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-2/Program.cs":::

## `args`

<span data-ttu-id="fff45-128">Операторы верхнего уровня могут ссылаться на переменную `args` для обращения к любым введенным аргументам командной строки.</span><span class="sxs-lookup"><span data-stu-id="fff45-128">Top-level statements can reference the `args` variable to access any command-line arguments that were entered.</span></span> <span data-ttu-id="fff45-129">Переменная `args` никогда не имеет значение NULL, но ее значение `Length` равно нулю, если не были предоставлены аргументы командной строки.</span><span class="sxs-lookup"><span data-stu-id="fff45-129">The `args` variable is never null but its `Length` is zero if no command-line arguments were provided.</span></span> <span data-ttu-id="fff45-130">Пример:</span><span class="sxs-lookup"><span data-stu-id="fff45-130">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-3/Program.cs":::

## `await`

<span data-ttu-id="fff45-131">Асинхронный метод можно вызвать с помощью `await`.</span><span class="sxs-lookup"><span data-stu-id="fff45-131">You can call an async method by using `await`.</span></span> <span data-ttu-id="fff45-132">Пример:</span><span class="sxs-lookup"><span data-stu-id="fff45-132">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-4/Program.cs":::

## <a name="exit-code-for-the-process"></a><span data-ttu-id="fff45-133">Код завершения для процесса</span><span class="sxs-lookup"><span data-stu-id="fff45-133">Exit code for the process</span></span>

<span data-ttu-id="fff45-134">Чтобы вернуть значение `int` при завершении работы приложения, используйте оператор `return`, как в методе `Main`, который возвращает `int`.</span><span class="sxs-lookup"><span data-stu-id="fff45-134">To return an `int` value when the application ends, use the `return` statement as you would in a `Main` method that returns an `int`.</span></span> <span data-ttu-id="fff45-135">Пример:</span><span class="sxs-lookup"><span data-stu-id="fff45-135">For example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-5/Program.cs":::

## <a name="implicit-entry-point-method"></a><span data-ttu-id="fff45-136">Неявный метод точки входа</span><span class="sxs-lookup"><span data-stu-id="fff45-136">Implicit entry point method</span></span>

<span data-ttu-id="fff45-137">Компилятор создает метод, используемый в качестве точки входа программы для проекта с операторами верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="fff45-137">The compiler generates a method to serve as the program entry point for a project with top-level statements.</span></span> <span data-ttu-id="fff45-138">Имя этого метода на самом деле не `Main`, это описание реализации, на которое код не может ссылаться напрямую.</span><span class="sxs-lookup"><span data-stu-id="fff45-138">The name of this method isn't actually `Main`, it's an implementation detail that your code can't reference directly.</span></span> <span data-ttu-id="fff45-139">Сигнатура метода зависит от того, содержат ли операторы верхнего уровня ключевое слово `await` или оператор `return`.</span><span class="sxs-lookup"><span data-stu-id="fff45-139">The signature of the method depends on whether the top-level statements contain the `await` keyword or the `return` statement.</span></span> <span data-ttu-id="fff45-140">В следующей таблице показано, как будет выглядеть сигнатура метода; имя метода `Main` в таблице используется для удобства.</span><span class="sxs-lookup"><span data-stu-id="fff45-140">The following table shows what the method signature would look like, using the method name `Main` in the table for convenience.</span></span>

| <span data-ttu-id="fff45-141">Код верхнего уровня содержит</span><span class="sxs-lookup"><span data-stu-id="fff45-141">Top-level code contains</span></span>| <span data-ttu-id="fff45-142">Неявная сигнатура `Main`</span><span class="sxs-lookup"><span data-stu-id="fff45-142">Implicit `Main` signature</span></span>                    |
|------------------------|----------------------------------------------|
| <span data-ttu-id="fff45-143">`await` и `return`</span><span class="sxs-lookup"><span data-stu-id="fff45-143">`await` and `return`</span></span>   | `static async Task<int> Main(string[] args)` |
| `await`                | `static async Task Main(string[] args)`      |
| `return`               | `static int Main(string[] args)`             |
| <span data-ttu-id="fff45-144">Ни `await`, ни `return`</span><span class="sxs-lookup"><span data-stu-id="fff45-144">No `await` or `return`</span></span> | `static void Main(string[] args)`            |

## <a name="c-language-specification"></a><span data-ttu-id="fff45-145">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="fff45-145">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
[<span data-ttu-id="fff45-146">Инструкции верхнего уровня</span><span class="sxs-lookup"><span data-stu-id="fff45-146">Top-level statements</span></span>](~/_csharplang/proposals/csharp-9.0/top-level-statements.md)

## <a name="see-also"></a><span data-ttu-id="fff45-147">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fff45-147">See also</span></span>

- [<span data-ttu-id="fff45-148">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="fff45-148">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fff45-149">Методы</span><span class="sxs-lookup"><span data-stu-id="fff45-149">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="fff45-150">Структура программы C#</span><span class="sxs-lookup"><span data-stu-id="fff45-150">Inside a C# Program</span></span>](../inside-a-program/index.md)
