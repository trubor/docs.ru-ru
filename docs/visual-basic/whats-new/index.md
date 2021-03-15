---
description: 'Узнайте подробнее о: Новые возможности Visual Basic'
title: Новые возможности
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: 1e5f7dec0476d0b7fbf09fa3b253d3d5dfedf426
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190376"
---
# <a name="whats-new-for-visual-basic"></a>Новые возможности Visual Basic

В этой статье перечислены названия основных возможностей в каждой версии Visual Basic, а также подробно описаны новые и усовершенствованные возможности в самых поздних версиях этого языка программирования.

## <a name="current-version"></a>Текущая версия

Visual Basic 16.9 / Visual Studio 2019 версии 16.9\
Описание новых функций см. в статье о [Visual Basic 16.9](#visual-basic-169).

Вы можете скачать последний пакет SDK для .NET на странице [скачиваемых файлов .NET](https://dotnet.microsoft.com/download).

## <a name="previous-versions"></a>Предыдущие версии

Visual Basic 16.0/Visual Studio 2019 версии 16.0\
Описание новых функций см. в статье о [Visual Basic 16.0](#visual-basic-160).

Visual Basic 15.5/Visual Studio 2017 версии 15.5\
Описание новых функций см. в статье о [Visual Basic 15.5](#visual-basic-155).

Visual Basic 15.3/Visual Studio 2017 версии 15.3\
Описание новых функций см. в статье о [Visual Basic 15.3](#visual-basic-153).

Visual Basic 15 / Visual Studio 2017\
Описание новых функций см. в статье о [Visual Basic 2017](#visual-basic-15).

Visual Basic/Visual Studio 2015\
Описание новых функций см. в статье о [Visual Basic 14](#visual-basic-14).

Visual Basic/Visual Studio 2013\
CTP-версии платформы компиляции .NET (Roslyn)

Visual Basic/Visual Studio 2012\
Ключевые слова `Async` и `await`, итераторы, атрибуты сведений о вызывающем объекте

Visual Basic, Visual Studio 2010\
Автоматически реализуемые свойства, инициализаторы коллекций, неявное продолжение строки, динамические типы, универсальная ковариантность и контрвариантность, доступ к глобальному пространству имен

Visual Basic/Visual Studio 2008\
Интегрированные запросы языка (LINQ), XML-литералы, определение локального типа, инициализаторы объектов, анонимные типы, методы расширений, определение локального типа `var`, лямбда-выражения, оператор `if`, типы значений, допускающие значение NULL

Visual Basic/Visual Studio 2005\
Тип `My` и вспомогательные типы (доступ к приложению, компьютеру, файловой системе, сети)

Visual Basic/Visual Studio .NET 2003\
Операторы поразрядного сдвига, объявление переменных цикла

Visual Basic/Visual Studio .NET 2002\
Первый выпуск Visual Basic .NET

## <a name="visual-basic-169"></a>Visual Basic 16.9

Visual Basic 16.9 позволяет использовать свойства только для инициализации.

## <a name="visual-basic-160"></a>Visual Basic 16.0

Visual Basic 16.0 фокусируется на предоставлении большего числа функций среды выполнения Visual Basic (microsoft.visualbasic.dll) в .NET Core и является первой версией Visual Basic, ориентированной на .NET Core. Многие части среды выполнения Visual Basic зависят от WinForms и будут добавлены в более поздней версии Visual Basic.

**Комментарии можно использовать в большем количестве мест внутри операторов**.

В Visual Basic 15.8 и более ранних версиях комментарии можно использовать только в пустых строках, в конце оператора или в определенных местах внутри оператора, где разрешено неявное продолжение строки. Начиная с Visual Basic 16.0 комментарии также допускаются после явных продолжений строк и внутри оператора в строке, начинающейся с пробела, за которым следует символ подчеркивания.

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

**Оптимизированное преобразование чисел с плавающей запятой в целые числа**

В предыдущих версиях Visual Basic преобразование значений [Double](../language-reference/data-types/double-data-type.md) и [Single](../language-reference/data-types/single-data-type.md) в целые числа обеспечивало относительно низкую производительность. Visual Basic 15.8 значительно повышает производительность преобразования чисел с плавающей запятой в целые числа, когда вы передаете значение, возвращаемое любым из следующих методов одной из [встроенных функций преобразования целого числа в Visual Basic](../language-reference/functions/type-conversion-functions.md) (CByte, CShort, CInt, CLng, CSByte, CUShort, CUInt, CULng), или когда значение, возвращаемое любым из следующих методов, неявно приводится к целочисленному типу, когда для [Option Strict](../language-reference/statements/option-strict-statement.md) задано значение `Off`:

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Эта оптимизация позволяет коду выполняться быстрее — до двух раз быстрее для кода, который выполняет большое количество преобразований в целочисленные типы. В следующем примере показано несколько простых вызовов методов, которые затрагивает эта оптимизация:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

Обратите внимание, что значения с плавающей запятой усекаются, а не округляются.

## <a name="visual-basic-155"></a>Visual Basic 15.5

[Неконечные именованные аргументы](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

В Visual Basic 15.3 и более ранних версиях при включении в вызов метода аргументов по положению и по имени позиционные аргументы должны были предшествовать именованным. Начиная с Visual Basic 15.5, позиционные и именованные аргументы могут появляться в любом порядке при условии, что все аргументы до последнего позиционного аргумента находятся в правильном положении. Это особенно полезно, если именованные аргументы используются, чтобы сделать код более удобочитаемым.

Например, следующий вызов метода имеет два позиционных аргумента между именованным аргументом. Именованный аргумент показывает, что значение 19 представляет возраст.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[Модификатор доступа к члену `Private Protected`](../language-reference/modifiers/private-protected.md)

Это новое сочетание ключевых слов определяет член, доступный для всех членов содержащего его класса, а также типы, производные от содержащего член класса, но только в том случае, если они присутствуют и в сборке, содержащей член. Так как структуры нельзя наследовать, `Private Protected` можно применять только к членам класса.

**Начальный шестнадцатеричный/двоичный/восьмеричный разделитель**

В Visual Basic 2017 поддерживается использование подчеркивания (`_`) в качестве разделителя цифр. Начиная с Visual Basic 15.5, в качестве начального разделителя между префиксом и двоичными, шестнадцатеричными или восьмеричными цифрами можно использовать знак подчеркивания. В следующем примере начальный разделитель цифр используется для определения 3 271 948 384 в качестве шестнадцатеричного числа:

```vb
Dim number As Integer = &H_C305_F860
```

Чтобы использовать символ подчеркивания в качестве начального разделителя, нужно добавить в файл проекта Visual Basic (\*.vbproj) следующий элемент:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**Вывод именованного кортежа**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

При присвоении значения элементов кортежа из переменных Visual Basic выводит имя элементов кортежа из соответствующих имен переменных; нет необходимости явно называть элемент кортежа. В следующем примере вывод используется для создания кортежа с тремя именованными элементами: `state`, `stateName` и `capital`.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Дополнительные параметры компилятора**

Теперь компилятор командной строки Visual Basic поддерживает параметры [ **-refout**](../reference/command-line-compiler/refout-compiler-option.md) и [ **-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) для управления выводом базовых сборок. **-refout** определяет выходной каталог базовой сборки, а **-refonly** указывает, что в результате компиляции будет выводиться только базовая сборка.

## <a name="visual-basic-15"></a>Visual Basic 15

[**Кортежи**](../programming-guide/language-features/data-types/tuples.md)

Кортежи представляют собой облегченную структуру данных, которая обычно используется для получения сразу нескольких значений за один вызов метода. Как правило, для получения нескольких значений с помощью одного метода необходимо выполнить одно из следующих действий:

- Определить пользовательский тип (`Class` или `Structure`). Это трудоемкое решение.

- Определить один или несколько параметров `ByRef` помимо возврата значения из метода.

Поддержка кортежей в Visual Basic позволяет быстро определить кортеж, при необходимости назначить его значениям семантические имена и быстро извлечь его значения. В следующем примере показан вызов метода <xref:System.Int32.TryParse%2A> и получение кортежа.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

После этого можно вызвать метод и обработать возвращенный кортеж в коде следующего вида.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**Двоичные литералы и разделители разрядов**

Двоичный литерал можно определить с помощью префикса `&B` или `&b`. Для повышения удобочитаемости в качестве разделителя разрядов можно использовать символ подчеркивания (`_`). В следующем примере обе эти функции используют для того, чтобы назначить значение `Byte` и отобразить его как десятичное, шестнадцатеричное или двоичное число.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Дополнительные сведения см. в разделе "Назначения литералов" статей, посвященных типам данных [Byte](../language-reference/data-types/byte-data-type.md#literal-assignments), [Integer](../language-reference/data-types/integer-data-type.md#literal-assignments), [Long](../language-reference/data-types/long-data-type.md#literal-assignments), [Short](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments) и [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments).

[**Поддержка значений C#, возвращаемых по ссылке**](../programming-guide/language-features/procedures/ref-return-values.md)

Начиная с версии 7.0 C# поддерживает значения, возвращаемые по ссылке. Это значит, что в случае, если вызывающий метод получает значение, возвращаемое по ссылке, он может изменить значение ссылки. Visual Basic не позволяет создавать методы со значениями, возвращаемыми по ссылке, но разрешает получать и изменять такие значения.

Например, следующий класс `Sentence`, написанный на языке C#, включает метод `FindNext`, который выполняет поиск следующего слова в предложении, которое начинается с заданной подстроки. Строка возвращается как значение, возвращаемое по ссылке, а переменная `Boolean`, переданная в метод по ссылке, показывает, дал ли поиск какие-то результаты. Это означает, что вызывающий объект может не только читать, но и изменять возвращаемое значение, а внесенные изменения отражаются в классе `Sentence`.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Проще всего изменить найденное в предложении слово с помощью представленного ниже кода. Обратите внимание на то, что при этом значение назначается не методу, а выражению, которое возвращается этим методом и представляет собой значение, возвращаемое по ссылке.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Проблема этого кода состоит в том, что в случае, если совпадений нет, метод возвращает первое слово. Поскольку код в этом примере не проверяет значение аргумента `Boolean`, чтобы определить наличие совпадений, в случае, если совпадений нет, он изменяет первое слово. В следующем примере эта проблема решена — если совпадений нет, первое слово заменяется само на себя.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Лучше использовать вспомогательный метод, в который значение, возвращаемое по ссылке, передается по ссылке. Впоследствии вспомогательный метод сможет изменить аргумент, передаваемый ему по ссылке. Эту задачу решает следующий код.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Дополнительные сведения см. в разделе [Значения, возвращаемые по ссылке](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[NameOf](../language-reference/operators/nameof.md)

Можно получить неполное имя строки типа или элемента для использования в сообщении об ошибке, не выполняя жесткого программирования строки.  Это позволяет сохранить правильный код при рефакторинге.  Эта возможность также полезна для прикрепления связей MVC контроллера model-view-controller и инициирования событий изменения свойств.

[Интерполяция строк](../programming-guide/language-features/strings/interpolated-strings.md)

Для создания строк можно использовать выражения интерполяции строк.  Интерполированное строковое выражение выглядит как шаблонная строка, которая содержит выражения.  Интерполированную строку проще понять с точки зрения аргументов, чем [составное форматирование](../../standard/base-types/composite-formatting.md).

[Доступ к членам и индексация с проверкой на значение NULL](../language-reference/operators/null-conditional-operators.md)

Прежде чем осуществлять доступ к элементу (`?.`) или выполнять операцию с индексом (`?[]`), можно протестировать значение null в очень простой синтаксической конструкции.  Эти операторы позволяют писать меньше кода для проверок значений null, особенно если речь идет о внедрении в структуры данных.  Если левый операнд или объектная ссылка имеет значение null, операция также возвращает значение null.

[Многострочные строковые литералы](../programming-guide/language-features/strings/string-basics.md)

Строковые литералы могут содержать последовательности новых строк.  Прежний обходной путь, связанный с использованием `<xml><![CDATA[...text with newlines...]]></xml>.Value`, больше не потребуется.

**Комментарии**

Комментарии можно поместить после неявных продолжений строк, внутри выражений инициализатора и среди условий выражения LINQ.

**Оптимизированное разрешение полных доменных имен**

Имея код, например `Threading.Thread.Sleep(1000)`, Visual Basic выполняла поиск пространства имен «Потоки», обнаруживала, что это пространство имен было неоднозначным в потоках System.Threading и System.Windows.Threading, и сообщала об ошибке.  Теперь Visual Basic рассматривает оба возможных пространства имен одновременно.  При отображении списка завершения редактор Visual Studio отображает в нем элементы обоих типов.

**Литералы даты с годом на первом месте**

Литералы даты могут быть указаны в формате гггг-мм-дд, `#2015-03-17 16:10 PM#`.

**Свойства интерфейса Readonly**

С помощью свойства readwrite можно реализовать свойства интерфейса readonly. Интерфейс гарантирует минимальную функциональность и не препятствует функционированию реализующего класса, который разрешает задавать значения для свойства.

[TypeOf \<expr> IsNot \<type>](../language-reference/operators/typeof-operator.md)

Для удобства чтения кода `TypeOf` теперь можно использовать с `IsNot`.

[#Disable Warning \<ID> и #Enable Warning \<ID>](../language-reference/directives/disable-enable.md)

Можно отключить и включить конкретные предупреждения для областей в исходном файле.

**Усовершенствования комментариев XML-документации**

При написании комментариев к документу разработчик получает доступ к интеллектуальному редактору и поддержку при сборке, что позволяет проверять названия параметров, грамотно обрабатывать `crefs` (универсальные типы, операторы и т. д.), выделение цветом и рефакторинг.

[Определения частичных модулей и интерфейсов](../language-reference/modifiers/partial.md)

Помимо классов и структур можно также объявлять частичные модули и интерфейсы.

[Директивы #Region внутри основной части метода](../language-reference/directives/region-directive.md)

Разделители #Region... #End Region можно поместить в любом месте файла, внутри функций и даже в основной части функции.

[Определения переопределений являются неявными перегрузками](../language-reference/modifiers/overrides.md)

Если добавить в определение модификатор `Overrides`, компилятор неявно добавляет `Overloads`, чтобы в общих случаях можно было вводить меньше кода.

**В аргументах атрибутов можно использовать объекты CObj**

Компилятор, используемый для вывода ошибки, связанной с тем, что при использовании в конструкциях атрибутов CObj(...) не являлся константой.

**Объявление и использование неоднозначных методов из разных интерфейсов**

Ранее следующий код выдавал ошибки, которые не позволяли объявить `IMock` или вызвать `GetDetails` (если эти значения были объявлены в C#).

```vb
Interface ICustomer
  Sub GetDetails(x As Integer)
End Interface

Interface ITime
  Sub GetDetails(x As String)
End Interface

Interface IMock : Inherits ICustomer, ITime
  Overloads Sub GetDetails(x As Char)
End Interface

Interface IMock2 : Inherits ICustomer, ITime
End Interface
```

Теперь компилятор использует стандартные правила разрешения перегрузки, чтобы выбрать оптимальную `GetDetails` для вызова, а в Visual Basic можно объявить связи интерфейса, как показано в примере.

## <a name="see-also"></a>См. также

- [Новые возможности Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017)
- [Новые возможности Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019)
