---
title: Начало работы с синтаксическими преобразованиями (API-интерфейсы Roslyn)
description: Введение в обходы, отправка запросов и прохождение деревьев синтаксиса.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: f12727332256acd9bbe828b9149376080facd156
ms.sourcegitcommit: 652f62fc8f3ab6a264681b6eb5211ac7539bd115
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "105964827"
---
# <a name="get-started-with-syntax-transformation"></a>Начало работы с синтаксическими преобразованиями

В основе этого руководства лежат концепции и методы, описанные в кратких руководствах [Начало работы с функциями синтаксического анализа](syntax-analysis.md) и [Начало работы с семантическим анализом](semantic-analysis.md). Если вы еще не изучили их, сделайте это до начала работы с этим руководством.

В этом кратком руководстве вы изучите методы создания и преобразования деревьев синтаксиса. Объединив их с методами, рассмотренными в предыдущих кратких руководствах, вы сможете создать рефакторинг в командной строке!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Неизменность и платформа компилятора .NET

**Неизменность** является фундаментальным принципом платформы компилятора .NET. Неизменяемые структуры данных невозможно изменить после их создания. Такие структуры данных могут безопасно анализироваться и совместно использоваться несколькими объектами-получателями одновременно. Не возникает опасности, что один объект-получатель непредсказуемо повлияет на работу других. Это означает, что анализатору не нужно применять блокировки или другие меры для поддержки параллелизма. Это правило применяется к деревьям синтаксиса, компиляциям, символам, семантическим моделям и любым другим структурам данных, с которыми вы можете работать. Вместо того чтобы изменять существующие структуры, интерфейсы API создают новые объекты с учетом требуемых изменений. Чтобы применить этот принцип к деревьям синтаксиса, после преобразования следует создавать новые деревья.

## <a name="create-and-transform-trees"></a>Создание и преобразование деревьев

Для синтаксических преобразований можно выбрать одну из двух стратегий. **Фабричные методы** лучше всего использовать при поиске конкретных узлов для замены или конкретных расположений, в которые нужно вставить новый код. **Модули записи** лучше подходят, когда нужно просканировать весь проект и найти структуры кода, которые нужно заменить.

### <a name="create-nodes-with-factory-methods"></a>Создание узлов с помощью фабричных методов

В первом синтаксическом преобразовании демонстрируется использование фабричных методов. Здесь вы замените инструкцию `using System.Collections;` инструкцией `using System.Collections.Generic;`. В этом примере показано, как создать объекты <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> с помощью фабричных методов <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType>. Для каждого типа **узла**, **маркера** или **trivia** имеется фабричный метод, создающий экземпляр этого типа. Чтобы создать синтаксическое дерево, нужно иерархически создавать его узлы, начиная снизу. Затем преобразуйте существующую программу, заменив существующие узлы только что созданным деревом.

Запустите Visual Studio и создайте проект C# для **автономного средства анализа кода**. В Visual Studio последовательно выберите **Файл** > **Создать** > **Проект**, чтобы открыть диалоговое окно "Новый проект". В разделе **Visual C#**  > **Расширяемость** выберите **Stand-Alone Code Analysis Tool** (Автономное средство анализа кода). Это краткое руководство содержит два примера проектов. Присвойте решению имя **SyntaxTransformationQuickStart**, а проекту — имя **ConstructionCS**. Нажмите кнопку **ОК**.

Этот проект использует методы класса <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> для создания объекта <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, представляющего пространство имен `System.Collections.Generic`.

Добавьте следующую директиву в начало `Program.cs`.

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Создайте **узлы синтаксиса имени** для построения дерева, представляющего инструкцию `using System.Collections.Generic;`. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> является базовым классом для четырех типов имен, применяющихся в C#. Сочетания этих четырех типов имен позволяют создать любое имя, которое может присутствовать в языке C#:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> представляет имена простых одиночных идентификаторов, например `System` и `Microsoft`;
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType> представляет имя универсального типа или метода, например `List<int>`;
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType> представляет полное имя в формате `<left-name>.<right-identifier-or-generic-name>`, например `System.IO`;
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType> представляет выражение имени через внешний псевдоним сборки, например `LibraryV2::Foo`.

Используйте метод <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)>, чтобы создать узел <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>. Добавьте приведенный ниже код в метод `Main` объекта `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

В представленном выше коде создается объект <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> и присваивается его переменной `name`. Многие API-интерфейсы Roslyn возвращают базовые классы, что упрощает работу со связанными типами. Переменную `name` класса <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> можно использовать многократно при создании <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Не используйте определение типа при создании образца. Этот шаг для проекта вы сделаете автоматическим.

Итак, вы создали имя. Теперь нужно добавить в дерево больше узлов, создав <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Новое дерево использует `name` в качестве левой части имени, а новый объект <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> в качестве пространства имен `Collections`, то есть в правой части <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Добавьте следующий код в файл `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Снова выполните этот код и проверьте результаты. Вы создаете дерево узлов, представляющее код. Точно так же вы создадите <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> для пространства имен `System.Collections.Generic`. Добавьте следующий код в файл `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Запустите программу еще раз и убедитесь, что вы создаете дерево для добавления кода.

### <a name="create-a-modified-tree"></a>Создание измененного дерева

На текущий момент вы создали небольшое синтаксическое дерево, которое содержит одну инструкцию. API-интерфейсы для создания узлов отлично подходят для создания блоков небольшого размера, например для одного оператора. Но для более крупных блоков кода следует использовать методы, которые заменяют или добавляют узлы в существующее дерево. Не забывайте, что синтаксические деревья являются неизменяемыми. **API синтаксиса** не предоставляет механизмов для изменения существующего синтаксического дерева после его создания. Но зато в нем есть методы, которые позволяют создавать новые деревья на основе существующих с определенными изменениями. Методы `With*` определяются в конкретных классах, производных от <xref:Microsoft.CodeAnalysis.SyntaxNode>, или в методах расширения, объявленных в классе <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions>. Эти методы позволяют создать узел, применяя изменения к дочерним свойствам существующего узла. Кроме того, можно использовать метод расширения <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> для замены узлов-потомков в поддереве. Этот метод также позволяет обновить родительский узел, чтобы он указывал на новый дочерний элемент, и повторяет этот процесс вверх по всему дереву. Этот процесс называется _повторным прохождением_.

На следующем шаге вы создадите дерево, которое представляет целую (небольшую) программу и измените его. Добавьте следующий код в начало класса `Program`:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> В примере кода используется пространство имен `System.Collections`, а не `System.Collections.Generic`.

Добавьте следующий код в нижнюю часть метода `Main`, чтобы выполнить синтаксический анализ текста и создать дерево:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

В этом примере используется метод <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType>, чтобы заменить имя в узле <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> тем именем, созданном в предыдущем фрагменте кода.

Создайте узел <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> с помощью метода <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)>, чтобы заменить имя `System.Collections` тем именем, которое создано в предыдущем фрагменте кода. Добавьте следующий код в конец метода `Main`:

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Запустите программу и внимательно изучите выходные данные. `newUsing` не помещается в корневой узел дерева. Исходное дерево не изменяется.

Добавьте следующий код, используя метод расширения <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A>, чтобы создать новое дерево. Новое дерево формируется путем замены существующего импорта обновленным узлом `newUsing`. Назначьте это новое дерево существующей переменной `root`:

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Запустите программу еще раз. На этот раз дерево правильно импортирует пространство имен `System.Collections.Generic`.

### <a name="transform-trees-using-syntaxrewriters"></a>Преобразование деревьев с помощью `SyntaxRewriters`

Методы `With*` и <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> удобны для преобразования отдельных ветвей в синтаксическом дереве. Класс <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> выполняет множественные преобразования синтаксического дерева. Класс <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> является подклассом <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> применяет преобразование к конкретному типу объекта <xref:Microsoft.CodeAnalysis.SyntaxNode>. Преобразования можно применить к нескольким типам объектов <xref:Microsoft.CodeAnalysis.SyntaxNode> везде, где они встречаются в синтаксическом дереве. В втором проекте в этом кратком руководстве выполняется рефакторинг в командной строке, при котором удаляются явные типы из объявлений локальных переменных везде, где используются определения типа.

Создайте новый проект C# для **автономного средства анализа кода**. В Visual Studio щелкните правой кнопкой мыши узел решения `SyntaxTransformationQuickStart`. Выберите **Добавить** > **Новый проект**, чтобы открыть диалоговое окно **Новый проект**. В разделе **Visual C#**  > **Расширяемость** выберите **Автономное средство анализа кода**. Присвойте проекту имя `TransformationCS` и нажмите кнопку "ОК".

На первом шаге создается класс, производный от <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter>, чтобы выполнять преобразования. Добавьте в проект новый файл класса. В Visual Studio выберите **Проект** > **Добавить класс...** . В диалоговом окне **Добавление нового элемента** введите имя файла `TypeInferenceRewriter.cs`.

В файл `TypeInferenceRewriter.cs` добавьте следующие директивы using:

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Теперь укажите класс `TypeInferenceRewriter` как расширение класса <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter>:

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Добавьте следующий код, чтобы объявить частное поле только для чтения, в котором будет храниться объект <xref:Microsoft.CodeAnalysis.SemanticModel>, и инициализируйте его в конструкторе. Это поле потребуется вам позже, чтобы указать, где можно использовать определение типа:

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Переопределите метод <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)>:

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Многие API-интерфейсы Roslyn объявляют типы возвращаемых значений, которые являются базовыми классами для фактически возвращаемых типов среды выполнения. Во многих сценариях один тип узла может быть заменен другим типом или даже удален. В этом примере метод <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> возвращает <xref:Microsoft.CodeAnalysis.SyntaxNode>, а не тип, производный от <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Этот модуль записи возвращает новый узел <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>, основанный на существующем узле.

В этом кратком руководстве рассматриваются объявления локальных переменных. Вы можете добавить в пример кода другие объявления, например циклов `foreach`, циклов `for`, выражений LINQ и лямбда-выражений. Также этот модуль записи преобразует объявления только в простейшем формате:

```csharp
Type variable = expression;
```

Если вы хотите поэкспериментировать самостоятельно, в готовый пример попробуйте добавить объявления переменных следующих типов:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Добавьте следующий код в текст метода `VisitLocalDeclarationStatement`, чтобы пропускать перезапись этих форм объявления:

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Этот метод указывает, что перезапись не происходит, возвращая неизмененное значение параметра `node`. Если ни одно из выражений `if` не принимает значение true, этот узел представляет возможное объявление с инициализацией. Добавьте следующие инструкции, чтобы извлечь имя типа, указанное в объявлении, и связать его с помощью поля <xref:Microsoft.CodeAnalysis.SemanticModel> для получения символа типа:

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Теперь, чтобы связать выражение инициализатора, добавьте такое выражение:

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Наконец, добавьте следующую инструкцию `if`, чтобы заменять существующее имя типа ключевым словом `var`, если тип выражения инициализатора соответствует указанному типу:

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Условная запись нужна потому, что объявление может приводить выражение инициализатора к базовому классу или интерфейсу. Если вам потребуется такое поведение, типы слева и справа от оператора назначения не будут совпадать. Удаление явного указания типа в таких случаях изменит семантику программы. `var` задается как идентификатор, а не ключевое слово, так как `var` является контекстным ключевым словом. Начальные и конечные элементы trivia (пробелы) передаются из старого имени типа в ключевое слово `var`, чтобы сохранить вертикальные пробелы и отступы. Гораздо проще использовать `ReplaceNode` вместо `With*` для преобразования <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>, так как имя типа по сути является внучатым элементом для оператора объявления.

Итак, вы завершили создание `TypeInferenceRewriter`. Теперь вернитесь к файлу `Program.cs`, чтобы завершить работу с этим примером. Создайте тест <xref:Microsoft.CodeAnalysis.Compilation> и получите из него <xref:Microsoft.CodeAnalysis.SemanticModel>. Используйте этот <xref:Microsoft.CodeAnalysis.SemanticModel> для проверки `TypeInferenceRewriter`. Это будет последний шаг процедуры. Одновременно с этим объявите переменную, которая будет выполнять роль заполнителя для тестовой компиляции:

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Подождите пару секунд, и в этой строке появится волнистая линия, которая обозначает ошибку: метод `CreateTestCompilation` не существует. Нажмите клавиши **CTRL+точка**, чтобы открыть меню лампочки. Затем нажмите клавишу "ВВОД", чтобы вызвать команду **Сгенерировать заглушку метода**. Эта команда создаст заглушку для метода `CreateTestCompilation` в классе `Program`. Этот метод вы заполните позднее:

![Создание метода C# по данным использования](./media/syntax-transformation/generate-from-usage.png)

Создайте следующий код, который последовательно перебирает все <xref:Microsoft.CodeAnalysis.SyntaxTree> в тесте <xref:Microsoft.CodeAnalysis.Compilation>. Для каждого из них инициализируйте новый `TypeInferenceRewriter` с классом <xref:Microsoft.CodeAnalysis.SemanticModel> для этого дерева:

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

В созданной инструкции `foreach` добавьте приведенный ниже код, чтобы выполнить преобразование для каждого исходного дерева. Этот код проверяет, были ли внесены правки, и если были — записывает преобразованное дерево. Модуль записи должен изменять дерево только в том случае, если он встречает одно или несколько объявлений локальных переменных, которые можно упростить с помощью определения типа:

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Вы увидите волнистые линии под фрагментом кода `File.WriteAllText`. Выберите значок лампочки и добавьте необходимую инструкцию `using System.IO;`.

Вы почти закончили! Осталось только последнее действие: создать тест <xref:Microsoft.CodeAnalysis.Compilation>. Так как вы еще не использовали определение типа в этом кратком руководстве, это будет отличным тестовым случаем. К сожалению, создание компиляции из файла проекта C# не входит в это пошаговое руководство. Но вы можете применить обходной путь, если внимательно выполняли все инструкции. Замените содержимое метода `CreateTestCompilation` следующим кодом. Этот код позволяет создать компиляцию теста, которая очень удачно совпадает с проектом, описанным в этом кратком руководстве:

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Скрестите пальцы и запустите проект. В Visual Studio выберите **Отладка** > **Начать отладку**. В Visual Studio появится сообщение о том, что файлы в проекте были изменены. Щелкните **Да для всех**, чтобы повторно загрузить все измененные файлы. Изучите их и поразитесь, что вам удалось сделать. Обратите особое внимание, насколько чище выглядит код без ненужных явных описателей типов.

Поздравляем! С помощью **API-интерфейсов компилятора** вы создали собственное средство для рефакторинга, которое ищет определенные синтаксические выражения во всех файлах проекта C#, анализирует и преобразует семантику исходного кода по указанным шаблонам. Теперь вы официально считаетесь разработчиком средства рефакторинга!
