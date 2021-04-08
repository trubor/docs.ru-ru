---
title: Руководство по программированию на C#. Соглашения о написании кода на C#
description: Узнайте о соглашениях о написании кода в C#. Соглашения о написании кода помогают сделать код единообразным, а также упрощают его копирование, изменение и обслуживание.
ms.date: 03/31/2021
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.openlocfilehash: 019bf02ea3cdfec2c4ae0d73b5b375781c5fcd9a
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231327"
---
# <a name="c-coding-conventions-c-programming-guide"></a>Соглашения о написании кода на C# (Руководство по программированию на C#)

Соглашения о написании кода предназначены для реализации следующих целей.  
  
- Создание согласованного вида кода, позволяющего читателям сосредоточиться на содержимом, а не на структуре.  
  
- Предоставление читателям возможности делать предположения, основанные на опыте, и поэтому быстрее понимать код.  
  
- Упрощение процессов копирования, изменения и обслуживания кода.  
  
- Предоставление лучших методик C#.  

Майкрософт использует приведенные в этой статье рекомендации для разработки примеров и документации.  
  
## <a name="naming-conventions"></a>Соглашения об именах  
  
- В коротких примерах, где нет [директив using](../../language-reference/keywords/using-directive.md), рекомендуется использовать полные указания для пространства имен. Если известно, что пространство имен импортируется в проект по умолчанию, вам не нужно указывать полные имена из этого пространства имен. Полные имена, если они слишком длинные для одной строки, можно разбить после точки (.), как показано в следующем примере.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet1":::

- Вам не нужно изменять имена объектов, созданных с помощью инструментов разработки Visual Studio, чтобы привести их в соответствие с другими рекомендациями.  
  
## <a name="layout-conventions"></a>Соглашения о макете  

Чтобы выделить структуру кода и облегчить чтение кода, в хорошем макете используется форматирование. Примеры и образцы корпорации Майкрософт соответствуют следующим соглашениям.  
  
- Использование параметров редактора кода по умолчанию (логичные отступы, отступы по четыре символа, использование пробелов для табуляции). Дополнительные сведения см. в разделе ["Параметры", "Текстовый редактор", C#, "Форматирование"](/visualstudio/ide/reference/options-text-editor-csharp-formatting).  
  
- Запись только одного оператора в строке.  
  
- Запись только одного объявления в строке.  
  
- Если отступ для дополнительных строк не ставится автоматически, необходимо сделать для них отступ на одну позицию табуляции (четыре пробела).  
  
- Добавление по крайней мере одной пустой строки между определениями методов и свойств.  
  
- Использование скобок для ясности предложений в выражениях, как показано в следующем коде.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet2":::

## <a name="commenting-conventions"></a>Соглашения о комментариях  
  
- Комментарий размещается на отдельной строке, а не в конце строки кода.  
  
- Текст комментария начинается с заглавной буквы.  
  
- Текст комментария завершается точкой.  
  
- Между разделителем комментария (/ /) и текстом комментария вставляется один пробел, как показано в следующем примере.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet3":::

- Не создавайте форматированные блоки из звездочек вокруг комментариев.  
  
## <a name="language-guidelines"></a>Рекомендации по использованию языка  

В следующих подразделах описаны методики, которыми руководствуется команда C# для подготовки примеров и образцов кода.  
  
### <a name="string-data-type"></a>Строковый тип данных  
  
- Для сцепления коротких строк рекомендуется использовать [интерполяцию строк](../../language-reference/tokens/interpolated.md), как показано в следующем коде.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet6":::

- Для добавления строк в циклах, особенно при работе с текстами больших размеров, используйте объект <xref:System.Text.StringBuilder>.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

### <a name="implicitly-typed-local-variables"></a>Неявно типизированные локальные переменные  
  
- В случаях, когда тип переменной понятен из правой части назначения или когда точный тип не важен, рекомендуется использовать [неявное типизирование](../classes-and-structs/implicitly-typed-local-variables.md) для локальных переменных.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet8":::
  
- Если тип в правой части назначения не является очевидным, не рекомендуется использовать [var](../../language-reference/keywords/var.md). Не полагайтесь на то, что имя метода предоставляет информацию о типе. Тип переменной можно считать очевидным, если используется оператор `new` или явное приведение типа.
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet9":::

- Не полагайтесь на имя переменной при указании ее типа. Имя может быть неверным. В следующем примере имя переменной `inputInt` вводит в заблуждение. На самом деле это строка.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet10":::

- Рекомендуется избегать использования `var` вместо [dynamic](../../language-reference/builtin-types/reference-types.md). Используйте `dynamic`, если требуется определение типа во время выполнения. Дополнительные сведения см. в статье [Использование типа dynamic (руководство по программированию на C#)](../types/using-type-dynamic.md).
  
- Рекомендуется использовать неявное типизирование для определения типа переменной цикла в циклах [for](../../language-reference/keywords/for.md).  
  
  В следующем примере неявное типизирование используется в операторе `for`.  

    :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet7":::

- Не используйте неявную типизацию для определения типа переменной цикла в циклах [foreach](../../language-reference/keywords/foreach-in.md).

  В следующем примере явное типизирование используется в операторе `foreach`.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet12":::

  > [!NOTE]
  > Следите за тем, чтобы случайно не изменить тип элемента итерируемой коллекции. Например, можно легко переключиться с <xref:System.Linq.IQueryable?displayProperty=nameWithType> на <xref:System.Collections.IEnumerable?displayProperty=nameWithType> в инструкции `foreach`, изменяющей выполнение запроса.

### <a name="unsigned-data-types"></a>Беззнаковые типы данных  
  
Как правило, рекомендуется использовать `int` вместо беззнаковых типов. В C# обычно используется `int`. Использование `int` упрощает взаимодействие с другими библиотеками.  
  
### <a name="arrays"></a>Массивы  
  
При инициализации массивов в строке объявления рекомендуется использовать сокращенный синтаксис. В следующем примере видно, что `var` нельзя использовать вместо `string[]`.  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13a":::

Если экземпляр создается явно, можно использовать `var`.

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13b":::

Если вы указали размер массива, нужно поочередно инициализировать все элементы.
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet13c":::
  
### <a name="delegates"></a>Делегаты  
  
Используйте [`Func<>` и `Action<>`](../../../standard/delegates-lambdas.md) вместо определения типов делегатов. В классе определите метод делегата.  

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14a":::

Вызывайте метод с помощью сигнатуры, которую определяет делегат `Func<>` или `Action<>`.

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15a":::

Если вы создаете экземпляры типа делегата, используйте сокращенный синтаксис. В классе определите тип делегата и метод с соответствующей сигнатурой.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet14b":::

Создайте экземпляр типа делегата и вызовите его. В следующем объявлении используется сокращенный синтаксис.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15b":::

В следующем объявлении используется полный синтаксис.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet15c":::

### <a name="try-catch-and-using-statements-in-exception-handling"></a>Операторы `try`-`catch` и `using` при обработке исключений  
  
- Рекомендуется использовать оператор [try-catch](../../language-reference/keywords/try-catch.md) для обработки большей части исключений.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet16":::

- Использование [оператора C# using](../../language-reference/keywords/using-statement.md) упрощает код. При наличии оператора [try-finally](../../language-reference/keywords/try-finally.md), код которого в блоке `finally` содержит только вызов метода <xref:System.IDisposable.Dispose%2A>, вместо него рекомендуется использовать оператор `using`.

  В следующем примере оператор `try`-`finally` вызывает `Dispose` только в блоке `finally`.
  
   :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17a":::

  То же самое можно сделать с помощью оператора `using`.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17b":::

  В C# 8 и более поздних версиях используйте новый [синтаксис `using` ](../../language-reference/keywords/using-statement.md), в котором не требуются скобки:

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet17c":::

### <a name="-and--operators"></a>Операторы `&&` и `||`  
  
Чтобы избежать возникновения исключений и увеличить производительность за счет пропуска необязательных сравнений, используйте [`&&`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) вместо [`&`](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) и [`||`](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) вместо [`|`](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) при выполнении сравнений, как показано в следующем примере.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet18":::

Если делитель равен нулю, второе условие в операторе `if` вызовет ошибку времени выполнения. При этом оператор && сразу прекращает выполнение, если первое выражение ложно. Это означает, что второе выражение не будет вычисляться. Оператор & всегда вычисляет оба выражения, и если значение `divisor` равно 0, возникает ошибка времени выполнения.
  
### <a name="new-operator"></a>Оператор `new`  
  
- Используйте одну из сокращенных форм создания экземпляров объектов, как показано в следующих объявлениях. Во втором примере используется синтаксис, который появился в версии C# 9.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet19":::
  
  ```csharp
  ExampleClass instance2 = new();
  ```
  
  Предыдущие объявления эквивалентны следующему объявлению.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet20":::

- Используйте инициализаторы объектов, чтобы упростить создание объектов, как показано в следующем примере.

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21a":::

  В следующем примере задаются точно такие же свойства, как и в предыдущем, но без использования инициализаторов.
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet21b":::

### <a name="event-handling"></a>Обработка событий  
  
Если вы определяете обработчик событий, который не нужно удалять позже, используйте лямбда-выражение.  
  
:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet22":::

Лямбда-выражение сокращает приведенное ниже традиционное определение.

:::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet23":::

### <a name="static-members"></a>Статические члены  
  
Для вызова [статических](../../language-reference/keywords/static.md) членов следует использовать имя класса: *ClassName.StaticMember*. В этом случае код становится более удобочитаемым за счет четкого доступа.  Не присваивайте статическому элементу, определенному в базовом классе, имя производного класса.  Во время компиляции кода его читаемость нарушается, и если добавить статический член с тем же именем в производный классе, код может быть поврежден.  
  
### <a name="linq-queries"></a>Запросы LINQ  
  
- Используйте значимые имена для переменных запроса. В следующем примере используется `seattleCustomers` для клиентов, находящихся в Сиэтле.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- Рекомендуется использовать псевдонимы для уверенности в том, что в именах свойств анонимных типов верно используются прописные буквы при помощи правил использования прописных и строчных букв языка Pascal.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet26":::

- Переименуйте свойства, если имена свойств в результате могут быть неоднозначными. Например, если запрос возвращает имя клиента и идентификатор распространителя, не оставляйте имена в виде `Name` и `ID`, а переименуйте их, чтобы было ясно, что `Name` — имя клиента и `ID` — идентификатор распространителя.  
  
  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet27":::

- Рекомендуется использовать неявное типизирование в объявлении переменных запроса и переменных диапазона.  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet25":::

- Выравнивайте предложения запроса под предложением [from](../../language-reference/keywords/from-clause.md), как показано в предыдущих примерах.  

- Чтобы гарантировать, что более поздние предложения запроса работают с ограниченным, отфильтрованным набором данных, используйте предложение [where](../../language-reference/keywords/where-clause.md) перед другими предложениями запроса.  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet29":::

- Используйте несколько предложений `from` для доступа к внутренним коллекциям вместо предложения [join](../../language-reference/keywords/join-clause.md). Например, коллекция объектов `Student` может содержать коллекцию результатов тестирования. При выполнении следующего запроса возвращаются результаты, превышающие 90 балов, а также фамилии учащихся, получивших такие оценки.  

  :::code language="csharp" source="../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs" id="Snippet30":::

## <a name="security"></a>Безопасность  

Следуйте указаниям, изложенным в [правилах написания безопасного кода](../../../standard/security/secure-coding-guidelines.md).  
  
## <a name="see-also"></a>См. также

- [Рекомендации по написанию кода среды выполнения .NET](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)
- [Соглашения о написании кода в Visual Basic](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [Правила написания безопасного кода](../../../standard/security/secure-coding-guidelines.md)
