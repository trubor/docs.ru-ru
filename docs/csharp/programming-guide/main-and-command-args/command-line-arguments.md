---
title: Руководство по программированию на C#. Аргументы командной строки
description: Сведения об аргументах командной строки. Изучите пример, в котором используются аргументы командной строки в консольном приложении.
ms.date: 03/11/2021
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: f495efb3bc2c76a98f74c173d5b777ebe383edcb
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190415"
---
# <a name="command-line-arguments-c-programming-guide"></a>Аргументы командной строки (Руководство по программированию на C#)

Вы можете передавать аргументы в метод `Main`, определив метод одним из следующих способов:

| Код метода `Main`                 | Сигнатура `Main`                             |
|------------------------------------|----------------------------------------------|
| Без возвращаемого значения, без использования `await` | `static void Main(string[] args)`            |
| С возвращаемым значением, без использования `await`    | `static int Main(string[] args)`             |
| Без возвращаемого значения, с использованием `await`      | `static async Task Main(string[] args)`      |
| С возвращаемым значением, с использованием `await`         | `static async Task<int> Main(string[] args)` |

Если аргументы не используются, можно опустить `args` в сигнатуре метода, чтобы немного упростить код:

| Код метода `Main`                 | Сигнатура `Main`                |
|------------------------------------|---------------------------------|
| Без возвращаемого значения, без использования `await` | `static void Main()`            |
| С возвращаемым значением, без использования `await`    | `static int Main()`             |
| Без возвращаемого значения, с использованием `await`      | `static async Task Main()`      |
| С возвращаемым значением, с использованием `await`         | `static async Task<int> Main()` |

> [!NOTE]
> Чтобы включить аргументы командной строки в методе `Main` в приложении Windows Forms, необходимо вручную изменить сигнатуру `Main` в файле *program.cs*. Код, созданный с помощью конструктора Windows Forms, создает `Main` без входного параметра. Также можно использовать <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> или <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> для доступа к аргументам командной строки из любой точки в консоли или приложении Windows.

Параметр метода `Main` — это массив <xref:System.String>, представляющий аргументы командной строки. Как правило, определить, существуют ли аргументы, можно, проверив свойство `Length`, например:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

> [!TIP]
> Массив `args` не может иметь значение NULL. Поэтому доступ к свойству `Length` можно получить без проверки значения NULL.

Строковые аргументы также можно преобразовать в числовые типы с помощью класса <xref:System.Convert> или метода `Parse`. Например, следующая инструкция преобразует `string` в число `long` с помощью метода <xref:System.Int64.Parse%2A>:

```csharp
long num = Int64.Parse(args[0]);
```

Можно также использовать тип C# `long`, который является псевдонимом `Int64`:

```csharp
long num = long.Parse(args[0]);
```

Кроме того, можно использовать метод класса `Convert`, `ToInt64`:

```csharp
long num = Convert.ToInt64(s);
```

Дополнительные сведения см. в разделах <xref:System.Int64.Parse%2A> и <xref:System.Convert>.

## <a name="example"></a>Пример

В следующем примере показано использование аргументов командной строки в консольном приложении. Приложение принимает один аргумент времени выполнения, преобразует аргумент в целое число и вычисляет факториал числа. Если не указано никаких аргументов, приложение выдает сообщение, поясняющее правильное использование программы.

Чтобы скомпилировать и запустить приложение из командной строки, выполните следующие действия.

1. Вставьте следующий код в любой текстовый редактор и сохраните файл как текстовый файл с именем *Factorial.cs*.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. На **начальном** экране или в меню **Пуск** откройте окно **командной строки разработчика** Visual Studio и перейдите к папке, содержащей файл, который вы только что создали.

3. Введите следующую команду для компиляции приложения.
  
     `csc Factorial.cs`  
  
     Если для приложения не выдаются ошибки компиляции, создается исполняемый файл с именем *Factorial.exe*.
  
4. Введите приведенную ниже команду для вычисления факториала числа 3:
  
     `Factorial 3`  
  
5. Код создает следующие выходные данные: `The factorial of 3 is 6.`

> [!NOTE]
> При выполнении приложения в Visual Studio аргументы командной строки можно указать на [странице "Отладка" в конструкторе проектов](/visualstudio/ide/reference/debug-page-project-designer).

## <a name="see-also"></a>См. также

- <xref:System.Environment?displayProperty=nameWithType>
- [Руководство по программированию на C#](../index.md)
- [Main() и аргументы командной строки](index.md)
- [Отображение аргументов командной строки](how-to-display-command-line-arguments.md)
- [Значения, возвращаемые методом main()](main-return-values.md)
- [Классы](../classes-and-structs/classes.md)
