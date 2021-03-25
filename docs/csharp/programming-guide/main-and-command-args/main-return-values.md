---
title: Руководство по программированию на C#. Значения, возвращаемые методом Main()
description: Сведения о значениях, возвращаемые методом Main(). Изучите примеры кода и созданный компилятором код, а также ознакомьтесь с дополнительными ресурсами.
ms.date: 03/11/2021
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 6f4001ecd490d5627d3a1ec74ecf7d593451e104
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190363"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="fba80-104">Значения, возвращаемые методом Main() (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="fba80-104">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="fba80-105">Вы можете возвратить `int` из метода `Main`, определив метод одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="fba80-105">You can return an `int` from the `Main` method by defining the method in one of the following ways:</span></span>

| <span data-ttu-id="fba80-106">Код метода `Main`</span><span class="sxs-lookup"><span data-stu-id="fba80-106">`Main` method code</span></span>             | <span data-ttu-id="fba80-107">Сигнатура `Main`</span><span class="sxs-lookup"><span data-stu-id="fba80-107">`Main` signature</span></span>                             |
|--------------------------------|----------------------------------------------|
| <span data-ttu-id="fba80-108">Без использования `args` или `await`</span><span class="sxs-lookup"><span data-stu-id="fba80-108">No use of `args` or `await`</span></span>    | `static int Main()`                          |
| <span data-ttu-id="fba80-109">С использованием `args`, без использования `await`</span><span class="sxs-lookup"><span data-stu-id="fba80-109">Uses `args`, no use of `await`</span></span> | `static int Main(string[] args)`             |
| <span data-ttu-id="fba80-110">Без использования `args`, с использованием `await`</span><span class="sxs-lookup"><span data-stu-id="fba80-110">No use of `args`, uses `await`</span></span> | `static async Task<int> Main()`              |
| <span data-ttu-id="fba80-111">С использованием `args` и `await`</span><span class="sxs-lookup"><span data-stu-id="fba80-111">Uses `args` and `await`</span></span>        | `static async Task<int> Main(string[] args)` |

<span data-ttu-id="fba80-112">Если значение, возвращаемое методом `Main`, не используется, возврат `void` или `Task` несколько упрощает код.</span><span class="sxs-lookup"><span data-stu-id="fba80-112">If the return value from `Main` is not used, returning `void` or `Task` allows for slightly simpler code.</span></span>

| <span data-ttu-id="fba80-113">Код метода `Main`</span><span class="sxs-lookup"><span data-stu-id="fba80-113">`Main` method code</span></span>             | <span data-ttu-id="fba80-114">Сигнатура `Main`</span><span class="sxs-lookup"><span data-stu-id="fba80-114">`Main` signature</span></span>                        |
|--------------------------------|-----------------------------------------|
| <span data-ttu-id="fba80-115">Без использования `args` или `await`</span><span class="sxs-lookup"><span data-stu-id="fba80-115">No use of `args` or `await`</span></span>    | `static void Main()`                    |
| <span data-ttu-id="fba80-116">С использованием `args`, без использования `await`</span><span class="sxs-lookup"><span data-stu-id="fba80-116">Uses `args`, no use of `await`</span></span> | `static void Main(string[] args)`       |
| <span data-ttu-id="fba80-117">Без использования `args`, с использованием `await`</span><span class="sxs-lookup"><span data-stu-id="fba80-117">No use of `args`, uses `await`</span></span> | `static async Task Main()`              |
| <span data-ttu-id="fba80-118">С использованием `args` и `await`</span><span class="sxs-lookup"><span data-stu-id="fba80-118">Uses `args` and `await`</span></span>        | `static async Task Main(string[] args)` |

<span data-ttu-id="fba80-119">Однако возврат `int` или `Task<int>` позволяет программе передавать информацию о своем состоянии другим программам и скриптам, которые вызывают исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="fba80-119">However, returning `int` or `Task<int>` enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span>

<span data-ttu-id="fba80-120">В следующем примере показано, как можно получить доступ к коду завершения для процесса.</span><span class="sxs-lookup"><span data-stu-id="fba80-120">The following example shows how the exit code for the process can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="fba80-121">Пример</span><span class="sxs-lookup"><span data-stu-id="fba80-121">Example</span></span>

<span data-ttu-id="fba80-122">В этом примере используются программы командной строки [.NET Core](../../../core/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="fba80-122">This example uses [.NET Core](../../../core/introduction.md) command-line tools.</span></span> <span data-ttu-id="fba80-123">Если вы не знакомы с программами командной строки .NET Core, можете обратиться к [этой статье по началу работы](../../../core/tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="fba80-123">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="fba80-124">Измените метод `Main` в файле *program.cs* следующим образом:</span><span class="sxs-lookup"><span data-stu-id="fba80-124">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="fba80-125">При запуске программы в Windows значение, возвращаемое функцией `Main`, сохраняется в переменной среды.</span><span class="sxs-lookup"><span data-stu-id="fba80-125">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="fba80-126">Эту переменную среды можно получить из пакетного файла с помощью `ERRORLEVEL` или в PowerShell с помощью `$LastExitCode`.</span><span class="sxs-lookup"><span data-stu-id="fba80-126">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from PowerShell.</span></span>

<span data-ttu-id="fba80-127">Для сборки приложения можно выполнить команду `dotnet build` [интерфейса командной строки .NET](../../../core/tools/dotnet.md).</span><span class="sxs-lookup"><span data-stu-id="fba80-127">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="fba80-128">Затем создайте скрипт PowerShell для запуска приложения и отображения результата.</span><span class="sxs-lookup"><span data-stu-id="fba80-128">Next, create a PowerShell script to run the application and display the result.</span></span> <span data-ttu-id="fba80-129">Вставьте следующий код в текстовый файл и сохраните его под именем `test.ps1` в папке проекта.</span><span class="sxs-lookup"><span data-stu-id="fba80-129">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="fba80-130">Запустите скрипт PowerShell, введя команду `test.ps1` в командной строке PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fba80-130">Run the PowerShell script by typing `test.ps1` at the PowerShell prompt.</span></span>

<span data-ttu-id="fba80-131">Так как код возвращает нулевое значение, пакетный файл сообщает об успехе.</span><span class="sxs-lookup"><span data-stu-id="fba80-131">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="fba80-132">Но если изменить файл MainReturnValTest.cs, чтобы он возвращал ненулевое значение, и затем повторно скомпилировать программу, то при последующем выполнении скрипта PowerShell будет выдано сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="fba80-132">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the PowerShell script will report failure.</span></span>

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="fba80-133">Пример полученных результатов</span><span class="sxs-lookup"><span data-stu-id="fba80-133">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="fba80-134">Значения, возвращаемые асинхронным методом main</span><span class="sxs-lookup"><span data-stu-id="fba80-134">Async Main return values</span></span>

<span data-ttu-id="fba80-135">Возвращаемые значения асинхронного метода main перемещают стандартный код, необходимый для вызова асинхронных методов в `Main`, в код, созданный компилятором.</span><span class="sxs-lookup"><span data-stu-id="fba80-135">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="fba80-136">Ранее для вызова асинхронного кода и для запуска программы до завершения асинхронной операции приходилось использовать следующую конструкцию:</span><span class="sxs-lookup"><span data-stu-id="fba80-136">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="fba80-137">Теперь ее можно заменить на:</span><span class="sxs-lookup"><span data-stu-id="fba80-137">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="fba80-138">Преимущество нового синтаксиса состоит в том, что компилятор всегда формирует правильный код.</span><span class="sxs-lookup"><span data-stu-id="fba80-138">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="fba80-139">Код, создаваемый компилятором</span><span class="sxs-lookup"><span data-stu-id="fba80-139">Compiler-generated code</span></span>

<span data-ttu-id="fba80-140">Если точка входа приложения возвращает `Task` или `Task<int>`, то компилятор создает новую точку входа, которая вызывает метод точки входа, объявленный в коде приложения.</span><span class="sxs-lookup"><span data-stu-id="fba80-140">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="fba80-141">Предположим, что эта точка входа называется `$GeneratedMain`. В этом случае компилятор создает следующий код для этих точек входа:</span><span class="sxs-lookup"><span data-stu-id="fba80-141">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="fba80-142">`static Task Main()` приводит к тому, что компилятор формирует эквивалент `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="fba80-142">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="fba80-143">`static Task Main(string[])` приводит к тому, что компилятор формирует эквивалент `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="fba80-143">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="fba80-144">`static Task<int> Main()` приводит к тому, что компилятор формирует эквивалент `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="fba80-144">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="fba80-145">`static Task<int> Main(string[])` приводит к тому, что компилятор формирует эквивалент `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="fba80-145">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="fba80-146">Если бы в примерах использовался модификатор `async` метода `Main`, компилятор сформировал бы точно такой же код.</span><span class="sxs-lookup"><span data-stu-id="fba80-146">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="fba80-147">См. также</span><span class="sxs-lookup"><span data-stu-id="fba80-147">See also</span></span>

- [<span data-ttu-id="fba80-148">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="fba80-148">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fba80-149">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="fba80-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="fba80-150">Main() и аргументы командной строки</span><span class="sxs-lookup"><span data-stu-id="fba80-150">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="fba80-151">Отображение аргументов командной строки</span><span class="sxs-lookup"><span data-stu-id="fba80-151">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
