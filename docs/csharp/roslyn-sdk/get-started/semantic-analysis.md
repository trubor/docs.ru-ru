---
title: Начало работы с семантическим анализом
description: В этом учебнике содержатся общие сведения о работе с семантическим анализом с помощью пакета SDK для компилятора .NET.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 3119363822328c0e5fc67c2a2a4a917a7d37cfd2
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872565"
---
# <a name="get-started-with-semantic-analysis"></a>Начало работы с семантическим анализом

В учебнике предполагается, что вы знакомы с синтаксическим API. Вводные сведения можно найти в статье о [начале работы с синтаксическим анализом](syntax-analysis.md).

В этом учебнике вы изучите **символы** и **API привязки**. Эти API предоставляют сведения о _семантическом значении_ программы. Они позволяют задавать вопросы, касающиеся типов, представленных любыми символами в программе, и получать на них ответы.

Вам нужно установить **пакет SDK для .NET Compiler Platform**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Общие сведения о компиляциях и символах

В процессе работы с пакетом SDK для компилятора .NET вы узнаете различия между синтаксическим API и семантическим API. **Синтаксический API** позволяет получить представление о _структуре_ программы. Однако часто требуются более полные сведения о семантике или _значении_ программы. Хотя синтаксический анализ свободного файла либо фрагмента кода Visual Basic или C# можно выполнить изолированно, задавать вопросы, к примеру о типе переменной, в отрыве от реальности не имеет смысла. Значение имени типа может зависеть от ссылок на сборки, операций импорта пространств имен или других файлов кода. Ответы на эти вопросы можно получить с помощью **семантического API**, в частности класса <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType>.

Экземпляр <xref:Microsoft.CodeAnalysis.Compilation> является аналогом отдельного проекта с точки зрения компилятора и представляет все необходимое для компиляции программы Visual Basic или C#. **Компиляция** включает в себя набор компилируемых исходных файлов, ссылки на сборки и параметры компилятора. О значении кода можно рассуждать, используя в этом контексте все остальные сведения. <xref:Microsoft.CodeAnalysis.Compilation> позволяет находить **символы** — сущности, такие как типы, пространства имен, члены и переменные, на которые указывают имена и другие выражения. Процесс связывания имен и выражений с **символами** называется **привязкой**.

Как <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> является абстрактным классом с производными, соответствующими конкретному языку. При создании экземпляра компиляции необходимо вызвать фабричный метод в классе <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (или <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>).

## <a name="querying-symbols"></a>Выполнение запросов к символам

В этом учебнике мы снова обратимся к программе "Hello, World!". На этот раз вы будете запрашивать символы в программе, чтобы понять, какие типы они представляют. Вы будете запрашивать типы в пространстве имен и узнаете, как найти методы, доступные для типа.

Окончательный код этого примера доступен в [репозитории на сайте GitHub](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Типы синтаксического дерева используют наследование для описания различных элементов синтаксиса, которые являются допустимыми в разных местах в программе. Применение этих API часто означает приведение свойств или элементов коллекции к конкретным производным типам. В следующих примерах назначения и приведения являются отдельными инструкциями, использующими явно типизированные переменные. Прочитайте код, чтобы увидеть типы возвращаемых значений API и тип среды выполнения возвращаемых объектов. На практике более распространено использование неявно типизированных переменных и имен API для описания типа рассматриваемых объектов.

Создайте новый проект C# для **автономного средства анализа кода**:

* В Visual Studio последовательно выберите **Файл** > **Создать** > **Проект**, чтобы открыть диалоговое окно "Новый проект".
* В разделе **Visual C#**  > **Расширяемость** выберите **Автономное средство анализа кода**.
* Присвойте проекту имя "**SemanticQuickStart**" и нажмите кнопку "ОК".

Вы будете анализировать программу "Hello World!", показанную ранее.
Добавьте текст для программы "Hello World" в качестве константы в класс `Program`:

[!code-csharp[Declare the program test](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Затем добавьте в константу `programText` следующий код для создания дерева синтаксиса для текста кода.  Добавьте следующую строку в метод `Main`:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Далее постройте <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> из уже созданного дерева. В примере "Hello World!" используются типы <xref:System.String> и <xref:System.Console>. Необходимо сослаться на сборку, объявляющую эти два типа при компиляции. Добавьте следующую строку в метод `Main` для создания компиляции дерева синтаксиса, включая ссылку на соответствующую сборку:

[!code-csharp[Create the compilation](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

Метод <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> добавит ссылки на компиляцию. Метод <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> загрузит сборку как ссылку.

## <a name="querying-the-semantic-model"></a>Выполнение запросов к семантической модели

К существующему объекту <xref:Microsoft.CodeAnalysis.Compilation> можно отправить запрос на класс <xref:Microsoft.CodeAnalysis.SemanticModel> для любого класса <xref:Microsoft.CodeAnalysis.SyntaxTree>, содержащегося в этом объекте <xref:Microsoft.CodeAnalysis.Compilation>. Семантическую модель можно представить как источник всей информации, которая обычно доступна из IntelliSense. <xref:Microsoft.CodeAnalysis.SemanticModel> может ответить, какие имена находятся в области в том или ином расположении, какие элементы доступны в определенном методе, какие переменные используются в неком блоке текста, на что ссылается некое имя или выражение, а также на другие подобные вопросы. Добавьте этот оператор для создания семантической модели:

[!code-csharp[Create the semantic model](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Привязка имени

<xref:Microsoft.CodeAnalysis.Compilation> создает <xref:Microsoft.CodeAnalysis.SemanticModel> из <xref:Microsoft.CodeAnalysis.SyntaxTree>. После создания модели можно выполнить запрос на поиск первой директивы `using` и получение сведений о символах для пространства имен `System`. Добавьте следующие две строки в метод `Main` для создания семантической модели и получения символа для первого оператора using:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

В предыдущем коде показано, как привязать имя в первой директиве `using`, чтобы получить <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> для пространства имен `System`. В предыдущем коде также демонстрируется, что для поиска структуры кода используется **синтаксическая модель**, а для понимания ее значения — **семантическая модель**. **Синтаксическая модель** находит строку `System` в операторе using. **Семантическая модель** располагает всеми сведениями о типах, определенных в пространстве имен `System`.

Из объекта <xref:Microsoft.CodeAnalysis.SymbolInfo> можно получить интерфейс <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> с помощью свойства <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType>. Это свойство возвращает символ, на который ссылается это выражение. Для выражений, не ссылающихся ни на какие объекты (например, числовые литералы), это свойство имеет значение `null`. Если <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> не задано значение NULL, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> обозначает тип символа. В этом примере свойству <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> присваивается значение <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Добавьте приведенный ниже код в метод `Main`. Он возвращает символ для пространства имен `System`, а затем отображает все дочерние пространства имен, объявленные в пространстве имен `System`:

[!code-csharp[Display all the child namespaces](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Запустите программу. Вы должны увидеть следующие результаты:

```output
System.Collections
System.Configuration
System.Deployment
System.Diagnostics
System.Globalization
System.IO
System.Numerics
System.Reflection
System.Resources
System.Runtime
System.Security
System.StubHelpers
System.Text
System.Threading
Press any key to continue . . .
```

> [!NOTE]
> Выходные данные не содержат каждое пространство имен, имеющее дочернее пространство имен от пространства имен `System`. В них отображается каждое пространство имен, которое присутствует в этой компиляции и ссылается только на сборку, где объявлено `System.String`. Этой компиляции неизвестно о пространствах имен, объявленных в других сборках.

### <a name="binding-an-expression"></a>Привязка выражения

В предыдущем коде показано, как найти символ путем привязки к имени. В программе C# существуют и другие не являющиеся именами выражения, которые можно привязать. Чтобы продемонстрировать эту возможность, выполним привязку к простому строковому литералу.

Программа "Hello World" содержит класс <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, строку "Hello World", отображаемую в консоли.

Строку "Hello World" можно найти путем поиска одного строкового литерала в программе. Затем после обнаружения узла синтаксиса получите сведения о типе для этого узла из семантической модели. Добавьте приведенный ниже код в метод `Main`:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

Структура <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> содержит свойство <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType>, которое обеспечивает доступ к семантическим сведениям о типе литерала. В этом примере типом является `string`. Добавьте объявление, которое присваивает это свойство локальной переменной:

[!code-csharp[Find the semantic information about the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Чтобы завершить действия в этом учебнике, сформируем запрос LINQ, который создает последовательность всех открытых методов, объявленных в типе `string` и возвращающих `string`. Поскольку запрос сложный, мы будем создавать его построчно, а затем перестроим в один запрос. Источником для этого запроса является последовательность всех элементов, объявленных в типе `string`:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Эта исходная последовательность содержит все элементы, включая свойства и поля, поэтому ее нужно отфильтровать с помощью метода <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType>, чтобы найти элементы, которые являются объектами <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType>:

[!code-csharp[Filter the sequence to only methods](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Затем добавьте другой фильтр, чтобы вернуть только открытые методы, возвращающие `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Выберите только свойство имени и только уникальные имена, удаляя все перегрузки:

[!code-csharp[find the distinct names.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Можно также создать полный запрос с помощью синтаксиса запросов LINQ и затем отобразить имена всех методов в консоли:

[!code-csharp[build and display the results of this query.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Выполните сборку и запуск программы. Вы должны увидеть следующий результат:

```output
Join
Substring
Trim
TrimStart
TrimEnd
Normalize
PadLeft
PadRight
ToLower
ToLowerInvariant
ToUpper
ToUpperInvariant
ToString
Insert
Replace
Remove
Format
Copy
Concat
Intern
IsInterned
Press any key to continue . . .
```

Вы использовали семантический API для поиска и отображения сведений о символах, которые являются частью этой программы.
