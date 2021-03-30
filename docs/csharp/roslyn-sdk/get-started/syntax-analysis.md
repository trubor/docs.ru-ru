---
title: Начало работы с функциями синтаксического анализа (Roslyn API)
description: Введение в обходы, отправка запросов и прохождение деревьев синтаксиса.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: 7fea6145ed927ed197295b08ab35dbf177920061
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872513"
---
# <a name="get-started-with-syntax-analysis"></a>Начало работы с функциями синтаксического анализа

В этом учебнике рассматривается **синтаксический API**. Синтаксический API предоставляет доступ к структурам данных, описывающих программы на языке C# или Visual Basic. Эти структуры данных достаточно подробны, чтобы обеспечивать полное представление любой программы любого размера. Эти структуры могут описывать готовые программы, обеспечивающие корректное выполнение и работу. Они также могут описывать неполные программы по мере их написания в редакторе.

Для обеспечения такого богатого выражения структуры данных и API, составляющие синтаксический API, имеют высокую сложность. Начнем с описания структуры данных для типичной программы "Hello, World!".

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Посмотрите на текст предыдущей программы. Вы узнаете знакомые элементы. Весь текст представляет один исходный файл, или **блок компиляции**. Первые три строки этого исходного файла являются **директивами using**. Остальной исходный код содержится в **объявлении пространства имен**. Объявление пространства имен содержит дочернее **объявление класса**. Объявление класса содержит одно **объявление метода**.

Синтаксический API создает древовидную структуру, корень которой представляет блок компиляции. Узлы в дереве представляют директивы using, объявление пространства имен и все остальные элементы программы. Структура дерева продолжается до самых нижних уровней. Строка "Hello World!" представляет собой **токен строкового литерала**, который является потомком **аргумента**. Синтаксический API предоставляет доступ к структуре программы. Можно создавать запросы к определенным практикам написания кода, выполнять обход всего дерева для понимания кода и создавать новые деревья путем изменения существующего дерева.

Это краткое описание представляет собой обзор видов сведений, к которым можно получить доступ с помощью синтаксического API. Синтаксический API является не более чем формальным API, который описывает уже знакомые конструкции кода из C#. Все возможности включают в себя сведения о форматировании кода, в том числе об использовании разрывов строк, пробелов и отступов. С помощью этих сведений можно полностью представить код как написанный и прочитанный программистами или компилятором. Эта структура позволяет взаимодействовать с исходным кодом на глубоко осмысленном уровне. Это уже не просто строки текста, а данные, представляющие структуру программы на языке C#.

Чтобы приступить к работе, потребуется установить **пакет SDK для .NET Compiler Platform**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Основные сведения о синтаксисе деревьев

Синтаксический API используется для любого анализа структуры кода C#. **Синтаксический API** предоставляет средства синтаксического анализа, деревья синтаксиса и служебные программы для анализа и создания деревьев синтаксиса. С его помощью выполняется поиск определенных элементов синтаксиса в коде или чтение кода программы.

Дерево синтаксиса — это структура данных, которая используется компиляторами C# и Visual Basic для понимания программ на языках C# и Visual Basic. Деревья синтаксиса создает тот же синтаксический анализатор, что выполняется при построении проекта или при нажатии на клавишу F5. Деревья синтаксиса полностью соответствуют языку. Каждый бит сведений в файле кода представлен в дереве. При записи дерева синтаксиса в текст воспроизводится в точности тот исходный текст, который был проанализирован. Деревья синтаксиса являются **неизменяемыми**. После создания дерево синтаксиса невозможно изменить. Пользователи могут анализировать деревья в нескольких потоках без блокировки и принятия других меры по обеспечению параллелизма, поскольку данные не изменяются. Можно использовать API для создания новых деревьев посредством изменения существующего дерева.

Ниже перечислены четыре основных стандартных блока деревьев синтаксиса.

* Класс <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, экземпляр которого представляет дерево синтаксического анализа целиком. <xref:Microsoft.CodeAnalysis.SyntaxTree> является абстрактным классом с производными, соответствующими конкретному языку. Для синтаксического анализа текста на языке C# (или Visual Basic) используются методы синтаксического анализа класса <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (или <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>).
* Класс <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>, экземпляры которого представляют такие синтаксические конструкции, как объявления, инструкции, предложения и выражения.
* Структура <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType>, которая представляет отдельные ключевые слова, идентификаторы, операторы или знаки препинания.
* И, наконец, структура <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType>, которая представляет малозначимые с точки зрения синтаксиса элементы сведений, такие как пробелы между токенами, директивы предварительной обработки и комментарии.

Заметки, токены и узлы иерархически компонуются для формирования дерева, которое полностью представляет все содержимое в фрагменте кода Visual Basic или C#. Эту структуру можно посмотреть с помощью окна **визуализатора синтаксиса**. В Visual Studio выберите **Вид** > **Другие окна** > **Визуализатор синтаксиса**. Например, предыдущий исходный файл на языке C# при просмотре с помощью **визуализатора синтаксиса** выглядит, как показано на следующем рисунке.

**Узел синтаксиса**: синий | **Токен синтаксиса**: зеленый | **Заметки к синтаксису**: красный ![Файл кода C#](media/walkthrough-csharp-syntax-figure1.png)

При перемещении по структуре дерева вы можете найти в файле кода все инструкции, выражения, токены и пробелы.

С помощью синтаксического API можно найти все, что угодно, в файле кода, но большинство сценариев предусматривает исследование небольших фрагментов кода либо поиск определенных инструкций или фрагментов. Ниже приводятся два примера, иллюстрирующие типичные сценарии использования для просмотра структуры кода или поиска отдельных инструкций.

## <a name="traversing-trees"></a>Обход деревьев

Узлы дерева синтаксиса можно исследовать двумя способами. Можно выполнить обход дерева для исследования каждого узла или выполнить запрос к определенным элементам или узлам.

### <a name="manual-traversal"></a>Обход вручную

Окончательный код этого примера доступен в [репозитории на сайте GitHub](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Типы синтаксического дерева используют наследование для описания различных элементов синтаксиса, которые являются допустимыми в разных местах в программе. Применение этих API часто означает приведение свойств или элементов коллекции к конкретным производным типам. В следующих примерах назначения и приведения являются отдельными инструкциями, использующими явно типизированные переменные. Прочитайте код, чтобы увидеть типы возвращаемых значений API и тип среды выполнения возвращаемых объектов. На практике более распространено использование неявно типизированных переменных и имен API для описания типа рассматриваемых объектов.

Создайте новый проект C# для **автономного средства анализа кода**:

* В Visual Studio последовательно выберите **Файл** > **Создать** > **Проект**, чтобы открыть диалоговое окно "Новый проект".
* В разделе **Visual C#**  > **Расширяемость** выберите **Автономное средство анализа кода**.
* Присвойте проекту имя "**SyntaxTreeManualTraversal**" и нажмите кнопку ОК.

Вы будете анализировать программу "Hello World!", показанную ранее.
Добавьте текст для программы "Hello World" в качестве константы в класс `Program`:

[!code-csharp[Declare the program text](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Затем добавьте в константу `programText` следующий код для создания **дерева синтаксиса** для текста кода.  Добавьте следующую строку в метод `Main`:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Эти две строки создают дерево и извлекают корневой узел этого дерева. Теперь можно исследовать узлы в дереве. Добавьте следующие строки в метод `Main` для отображения некоторых свойств корневого узла дерева:

[!code-csharp[Examine the root node](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Запустите приложение для просмотра сведений, которые код собрал о корневом узле этого дерева.

Как правило, для получения сведений о коде выполняется обход дерева. В этом примере анализируется известный вам код для изучения API. Добавьте следующий код для исследования первого элемента узла `root`:

[!code-csharp[Find the first member](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Этот элемент — <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Он представляет все, что входит в объявление `namespace HelloWorld`. Добавьте следующий код, чтобы посмотреть, какие узлы объявляются внутри пространства имен `HelloWorld`:

[!code-csharp[Find the class declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Запустите программу, чтобы посмотреть, что вы узнали.

Теперь, когда известно, что объявление является <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, объявите новую переменную этого типа для исследования объявления класса. Этот класс содержит только один элемент: метод `Main`. Добавьте следующий код, чтобы найти метод `Main`, и приведите его к <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Узел объявления метода содержит полные синтаксические сведения о методе. Давайте посмотрим тип возвращаемого значения для метода `Main`, количество и типы аргументов, а также основной текст метода. Добавьте следующий код:

[!code-csharp[Examine the syntax of the main method](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Запустите программу, чтобы просмотреть все полученные сведения об этой программе:

```text
The tree is a CompilationUnit node.
The tree has 1 elements in it.
The tree has 4 using statements. They are:
        System
        System.Collections
        System.Linq
        System.Text
The first member is a NamespaceDeclaration.
There are 1 members declared in this namespace.
The first member is a ClassDeclaration.
There are 1 members declared in the Program class.
The first member is a MethodDeclaration.
The return type of the Main method is void.
The method has 1 parameters.
The type of the args parameter is string[].
The body text of the Main method follows:
        {
            Console.WriteLine("Hello, World!");
        }
```

### <a name="query-methods"></a>Методы запросов

Помимо обхода деревьев можно также исследовать деревья синтаксиса с помощью методов запросов, определенных в <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Эти методы известны всем, кто знаком с XPath. Эти методы можно использовать совместно с LINQ для быстрого поиска в дереве. <xref:Microsoft.CodeAnalysis.SyntaxNode> содержит такие методы запросов, как <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> и <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Эти методы запроса можно использовать для поиска аргументов к методу `Main` в качестве альтернативы навигации по дереву. Добавьте следующий код в конец метода `Main`:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

В первой инструкции используется выражение LINQ и метод <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> для обнаружения того же параметра, что и в предыдущем примере.

Запустите программу, и выражение LINQ обнаружит тот же параметр, что и при навигации по дереву вручную.

В этом образце используются инструкции `WriteLine` для отображения сведений о деревьях синтаксиса по мере их обхода. Гораздо больше сведений можно получить, запустив готовую программу в отладчике. Можно просмотреть другие свойства и методы в составе дерева синтаксиса, созданного для программы "hello world".

## <a name="syntax-walkers"></a>Средства обхода синтаксиса

Часто бывает необходимо найти все узлы определенного типа в дереве синтаксиса, например каждое объявление свойств в файле. Путем расширения класса <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> и переопределения метода <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> можно обработать каждое объявление свойств в дереве синтаксиса, не зная заранее его структуры. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> — это особый тип <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor>, который рекурсивно обходит узел и все его дочерние элементы.

Этот пример реализует <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> для исследования дерева синтаксиса. Он собирает обнаруженные директивы `using`, которые не импортируют пространство имен `System`.

Создайте новый проект C# для **автономного средства анализа кода**. Присвойте ему имя "**SyntaxWalker**".

Окончательный код этого примера доступен в [репозитории на сайте GitHub](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/SyntaxQuickStart). Пример на GitHub содержит оба проекта, описанные в этом учебнике.

Как показано в предыдущем примере, можно определить строковую константу, которая будет содержать текст программы для анализа:

[!code-csharp[Define the code text to analyzer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Этот исходный текст содержит директивы `using`, расположенные в четырех разных местах: на уровне файлов, в пространстве имен верхнего уровня и в двух вложенных пространствах имен. В этом примере представлен основной сценарий использования класса <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> для выполнения запросов к коду. Было бы сложно посетить каждый узел в корневом дереве синтаксиса для поиска объявлений using. Вместо этого создается производный класс и переопределяется метод, который вызывается только в том случае, когда текущий узел в дереве является директивой using. Обходчик не работает с узлами других типов. Этот единичный метод проверяет каждую из инструкций `using` и создает коллекцию пространств имен, которые не входят в пространство имен `System`. Создается <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> для проверки всех инструкций `using`, но только инструкций `using`.

Теперь, когда вы определили текст программы, необходимо создать `SyntaxTree` и получить корень этого дерева:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Теперь создайте новый класс. В Visual Studio выберите **Проект** > **Добавить новый элемент**. В диалоге **Добавление нового элемента** введите имя файла *UsingCollector.cs*.

Вы реализуете функцию обходчика `using` в классе `UsingCollector`. Для начала сделайте класс `UsingCollector` производным от <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Потребуется хранилище для хранения узлов пространства имен, которые вы будете собирать.  Объявите свойство только для чтения в классе `UsingCollector`. Эта переменная будет использоваться для хранения найденных узлов <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax>:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Базовый класс, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>, реализует логику для посещения каждого узла в дереве синтаксиса. Производный класс переопределяет методы, вызываемые для определенных интересующих вас узлов. В этом примере вас интересует любая директива `using`. Это означает, что требуется переопределить метод <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)>. Единственный аргумент этого метода — объект <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType>. Это важное преимущество обходчиков: они вызывают переопределенные методы с использованием аргументов, уже приведенных к типу конкретного узла. Класс <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> имеет свойство <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name>, которое содержит имя импортируемого пространства имен. Это <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Добавьте следующий код в переопределение <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)>:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Как и в прошлом примере, были добавлены разнообразные инструкции `WriteLine` для облегчения понимания этого метода. Вы можете посмотреть, когда он вызывается и какие при этом передаются аргументы.

Наконец, необходимо добавить две строки кода для создания `UsingCollector` и направить его в корневой узел для сбора всех инструкций `using`. Затем добавьте цикл `foreach` для отображения всех инструкций `using`, найденных сборщиком:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Скомпилируйте и запустите программу. Вы должны увидеть следующий результат.

```console
        VisitUsingDirective called with System.
        VisitUsingDirective called with System.Collections.Generic.
        VisitUsingDirective called with System.Linq.
        VisitUsingDirective called with System.Text.
        VisitUsingDirective called with Microsoft.CodeAnalysis.
                Success. Adding Microsoft.CodeAnalysis.
        VisitUsingDirective called with Microsoft.CodeAnalysis.CSharp.
                Success. Adding Microsoft.CodeAnalysis.CSharp.
        VisitUsingDirective called with Microsoft.
                Success. Adding Microsoft.
        VisitUsingDirective called with System.ComponentModel.
        VisitUsingDirective called with Microsoft.Win32.
                Success. Adding Microsoft.Win32.
        VisitUsingDirective called with System.Runtime.InteropServices.
        VisitUsingDirective called with System.CodeDom.
        VisitUsingDirective called with Microsoft.CSharp.
                Success. Adding Microsoft.CSharp.
Microsoft.CodeAnalysis
Microsoft.CodeAnalysis.CSharp
Microsoft
Microsoft.Win32
Microsoft.CSharp
Press any key to continue . . .
```

Поздравляем! Вы использовали **синтаксический API** для поиска определенных типов инструкций и объявлений C# в исходном коде C#.
