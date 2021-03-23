---
title: Руководство по программированию на C#. Main() и аргументы командной строки
description: Сведения о методе Main() и аргументах командной строки. Метод Main является точкой входа для исполняемой программы.
ms.date: 03/08/2021
f1_keywords:
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 05b2030133ca83cf87de7110f820eaad38fad756
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480190"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() и аргументы командной строки (Руководство по программированию на C#)

Метод `Main` — это точка входа приложения C#. (Библиотекам и службам точка входа в виде метода `Main` не требуется.) Когда приложение запускается, первым вызывается именно метод `Main`.

В программе на C# может существовать только одна точка входа. Если у вас есть несколько классов с методом `Main`, программу нужно компилировать с параметром компилятора **StartupObject**, чтобы указать, какой из методов `Main` будет использоваться в качестве точки входа. Дополнительные сведения см. в разделе [**StartupObject** (параметры компилятора C#)](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

Начиная с версии C# 9, можно не указывать метод `Main` и писать инструкции C# как включенные в метод `Main`, как показано в следующем примере:

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

Сведения о написании кода приложения с помощью неявного метода точки входа см. в статье [Инструкции верхнего уровня (руководство по программированию на C#)](top-level-statements.md).

## <a name="overview"></a>Обзор

- Метод `Main` — это точка входа для выполняемой программы. Это начальный и завершающий этапы управления программой.
- `Main` объявляется внутри класса или структуры. Метод `Main` должен быть [статическим](../../language-reference/keywords/static.md). Он может не быть [открытым](../../language-reference/keywords/public.md). (В предыдущем примере он по умолчанию получает уровень доступа [private](../../language-reference/keywords/private.md) (закрытый).) Класс или структура, в которой он объявлен, не обязаны быть статическими.
- Метод `Main` может иметь значение `void`, `int` или (начиная с C# 7.1) `Task`, а также тип возвращаемого значения `Task<int>`.
- Если только `Main` возвращает `Task` или `Task<int>`, объявление `Main` может включать модификатор [`async`](../../language-reference/keywords/async.md). Обратите внимание, что это, в частности, исключает метод `async void Main`.
- Метод `Main` может быть объявлен с параметром `string[]`, который содержит аргументы командной строки, или без него. Когда вы используете Visual Studio для создания Windows-приложений, вы можете добавить параметр вручную либо воспользоваться методом <xref:System.Environment.GetCommandLineArgs>, чтобы получить [аргументы командной строки](command-line-arguments.md). Параметры считываются как аргументы командной строки, индексы которых начинаются с нуля. В отличие от C и C++, имя программы не рассматривается как первый аргумент командной строки в массиве `args`, но является первым элементом метода <xref:System.Environment.GetCommandLineArgs>.

Ниже приведен список допустимых подписей `Main`:

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

В предыдущих примерах используется модификатор открытого метода доступа. Эта обычная схема использования, но она не является обязательной.

Добавление значений `async` и `Task`, а также типов возвращаемого значения `Task<int>` упрощает код программы, когда консольным приложениям требуется запустить и ожидать (`await`) асинхронные операции в `Main`.

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Методы](../classes-and-structs/methods.md)
- [Структура программы C#](../inside-a-program/index.md)
