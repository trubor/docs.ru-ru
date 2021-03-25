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
# <a name="main-return-values-c-programming-guide"></a>Значения, возвращаемые методом Main() (Руководство по программированию на C#)

Вы можете возвратить `int` из метода `Main`, определив метод одним из следующих способов:

| Код метода `Main`             | Сигнатура `Main`                             |
|--------------------------------|----------------------------------------------|
| Без использования `args` или `await`    | `static int Main()`                          |
| С использованием `args`, без использования `await` | `static int Main(string[] args)`             |
| Без использования `args`, с использованием `await` | `static async Task<int> Main()`              |
| С использованием `args` и `await`        | `static async Task<int> Main(string[] args)` |

Если значение, возвращаемое методом `Main`, не используется, возврат `void` или `Task` несколько упрощает код.

| Код метода `Main`             | Сигнатура `Main`                        |
|--------------------------------|-----------------------------------------|
| Без использования `args` или `await`    | `static void Main()`                    |
| С использованием `args`, без использования `await` | `static void Main(string[] args)`       |
| Без использования `args`, с использованием `await` | `static async Task Main()`              |
| С использованием `args` и `await`        | `static async Task Main(string[] args)` |

Однако возврат `int` или `Task<int>` позволяет программе передавать информацию о своем состоянии другим программам и скриптам, которые вызывают исполняемый файл.

В следующем примере показано, как можно получить доступ к коду завершения для процесса.

## <a name="example"></a>Пример

В этом примере используются программы командной строки [.NET Core](../../../core/introduction.md). Если вы не знакомы с программами командной строки .NET Core, можете обратиться к [этой статье по началу работы](../../../core/tutorials/with-visual-studio-code.md).

Измените метод `Main` в файле *program.cs* следующим образом:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

При запуске программы в Windows значение, возвращаемое функцией `Main`, сохраняется в переменной среды. Эту переменную среды можно получить из пакетного файла с помощью `ERRORLEVEL` или в PowerShell с помощью `$LastExitCode`.

Для сборки приложения можно выполнить команду `dotnet build` [интерфейса командной строки .NET](../../../core/tools/dotnet.md).

Затем создайте скрипт PowerShell для запуска приложения и отображения результата. Вставьте следующий код в текстовый файл и сохраните его под именем `test.ps1` в папке проекта. Запустите скрипт PowerShell, введя команду `test.ps1` в командной строке PowerShell.

Так как код возвращает нулевое значение, пакетный файл сообщает об успехе. Но если изменить файл MainReturnValTest.cs, чтобы он возвращал ненулевое значение, и затем повторно скомпилировать программу, то при последующем выполнении скрипта PowerShell будет выдано сообщение об ошибке.

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

## <a name="sample-output"></a>Пример полученных результатов

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Значения, возвращаемые асинхронным методом main

Возвращаемые значения асинхронного метода main перемещают стандартный код, необходимый для вызова асинхронных методов в `Main`, в код, созданный компилятором. Ранее для вызова асинхронного кода и для запуска программы до завершения асинхронной операции приходилось использовать следующую конструкцию:

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

Теперь ее можно заменить на:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Преимущество нового синтаксиса состоит в том, что компилятор всегда формирует правильный код.

## <a name="compiler-generated-code"></a>Код, создаваемый компилятором

Если точка входа приложения возвращает `Task` или `Task<int>`, то компилятор создает новую точку входа, которая вызывает метод точки входа, объявленный в коде приложения. Предположим, что эта точка входа называется `$GeneratedMain`. В этом случае компилятор создает следующий код для этих точек входа:

- `static Task Main()` приводит к тому, что компилятор формирует эквивалент `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` приводит к тому, что компилятор формирует эквивалент `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` приводит к тому, что компилятор формирует эквивалент `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` приводит к тому, что компилятор формирует эквивалент `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Если бы в примерах использовался модификатор `async` метода `Main`, компилятор сформировал бы точно такой же код.

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Справочник по C#](../../language-reference/index.md)
- [Main() и аргументы командной строки](index.md)
- [Отображение аргументов командной строки](./how-to-display-command-line-arguments.md)
