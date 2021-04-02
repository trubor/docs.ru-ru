---
description: 'Дополнительные сведения о: для каждого... Оператор Next (Visual Basic)'
title: Оператор For Each…Next
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: 85fb426fdc2d7961603a3ddcc882f9fdce0c70a2
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079626"
---
# <a name="for-eachnext-statement-visual-basic"></a>Оператор For Each...Next (Visual Basic)

Повторяет группу операторов для каждого элемента в коллекции.

## <a name="syntax"></a>Синтаксис

```vb
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>Компоненты

|Термин|Определение|
|---|---|
|`element`|Требуется в `For Each` инструкции. Необязательный в `Next` инструкции. Переменная. Используется для прохода по элементам коллекции.|
|`datatype`|Необязательный [`Option Infer`](option-infer-statement.md) параметр, если имеет значение On (по умолчанию) или `element` уже объявлен; требуется, если `Option Infer` параметр имеет значение OFF и `element` еще не объявлен. Тип данных `element`.|
|`group`|Обязательный. Переменная типа, которая является типом коллекции или объектом. Ссылается на коллекцию, для которой `statements` повторяются.|
|`statements`|Необязательный элемент. Одна или несколько инструкций между `For Each` и `Next` выполняются для каждого элемента в `group` .|
|`Continue For`|Необязательный элемент. Передает управление в начало `For Each` цикла.|
|`Exit For`|Необязательный элемент. Передает управление за пределы `For Each` цикла.|
|`Next`|Обязательный. Завершает определение `For Each` цикла.|

## <a name="simple-example"></a>Простой пример

Используйте `For Each` цикл..., `Next` Если нужно повторить набор инструкций для каждого элемента коллекции или массива.

> [!TIP]
> A [для... Оператор Next](for-next-statement.md) работает хорошо, когда можно связать каждую итерацию цикла с управляющей переменной и определить начальные и конечные значения переменной. Однако при работе с коллекцией концепция начальных и конечных значений не имеет смысла, и вам не обязательно быть уверенным, сколько элементов имеет коллекция. В таком случае `For Each` цикл... `Next` часто является лучшим выбором.

В следующем примере `For Each` ...`Next` выполняет перебор всех элементов коллекции списков.

:::code language="vb" source="./snippets/for-each-next-statement/vb/Examples.vb" id="init":::

Дополнительные примеры см. в разделе [коллекции](../../../standard/collections/index.md) и [массивы](../../programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Nested Loops

Можно вложить `For Each` циклы, поместив один цикл в другой.

В следующем примере демонстрируется вложенное `For Each` ...`Next` сотрудник.

:::code language="vb" source="./snippets/for-each-next-statement/vb/Examples.vb" id="nested":::

При вложении циклов каждый цикл должен иметь уникальную `element` переменную.

Можно также вкладывать различные виды управляющих структур друг в друга. Дополнительные сведения см. в разделе [вложенные структуры управления](../../programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Выход и продолжение для

Оператор [Exit For](exit-statement.md) вызывает завершение выполнения `For` ...`Next` выполняет цикл и передает управление оператору, который следует за `Next` оператором.

`Continue For`Оператор передает управление сразу в следующую итерацию цикла. Дополнительные сведения см. в разделе [оператор continue](continue-statement.md).

В следующем примере показано, как использовать `Continue For` операторы и `Exit For` .

:::code language="vb" source="./snippets/for-each-next-statement/vb/Examples.vb" id="exitcontinue":::

В цикле можно разместить любое количество `Exit For` операторов `For Each` . При использовании внутри вложенных `For Each` циклов `Exit For` выполнение вызывает выход из внутреннего цикла и передает управление следующему более высокому уровню вложенности.

`Exit For` часто используется после вычисления некоторого условия, например в `If` ... `Then` ...`Else` дереве. Может потребоваться использовать `Exit For` для следующих условий:

- Продолжение итерации не требуется или невозможно. Это может быть вызвано ошибочным значением или запросом на завершение.

- Исключение перехвачено в `Try` ... `Catch` ...`Finally`. `Exit For` В конце блока можно использовать `Finally` .

- Существует бесконечный цикл, который может выполняться с большим или даже бесконечным числом раз. При обнаружении такого условия можно использовать `Exit For` для экранирования цикла. Дополнительные сведения см. в разделе [Do... Loop, инструкция](do-loop-statement.md).

## <a name="iterators"></a>Iterators

*Итератор* используется для выполнения пользовательской итерации по коллекции. Итератор может быть функцией или `Get` методом доступа. Он использует `Yield` инструкцию для возвращения каждого элемента коллекции по одному за раз.

Итератор вызывается с помощью `For Each...Next` оператора. Каждая итерация цикла `For Each` вызывает итератор. При `Yield` достижении оператора в итераторе возвращается выражение в `Yield` операторе, а текущее расположение в коде сохраняется. При следующем вызове итератора выполнение возобновляется с этого места.

В следующем примере используется функция итератора. Функция итератора содержит `Yield` оператор, который находится внутри блока [for... Следующий](for-next-statement.md) цикл. В `ListEvenNumbers` методе каждая итерация `For Each` тела оператора создает вызов функции итератора, который переходит к следующему `Yield` оператору.

:::code language="vb" source="./snippets/for-each-next-statement/vb/Examples.vb" id="iterator":::

Дополнительные сведения см. в разделе [итераторы](../../programming-guide/concepts/iterators.md), [оператор yield](yield-statement.md)и [итератор](../modifiers/iterator.md).

## <a name="technical-implementation"></a>Техническая реализация

Когда `For Each` ...`Next` выполняется инструкция, Visual Basic вычисляет коллекцию только один раз перед началом цикла. Если блок инструкций изменяется `element` или `group` , эти изменения не влияют на итерацию цикла.

Когда все элементы в коллекции были последовательно назначены `element` , `For Each` цикл останавливается и управление передается оператору, следующему за `Next` оператором.

Если [параметр Infer](option-infer-statement.md) имеет значение On (значение по умолчанию), то компилятор Visual Basic может определить тип данных `element` . Если он отключен и не `element` объявлен вне цикла, необходимо объявить его в `For Each` операторе. Чтобы объявить тип данных `element` явным образом, используйте `As` предложение. Если тип данных элемента не определен за пределами `For Each` конструкции... `Next` , его область является телом цикла. Обратите внимание, что нельзя объявлять `element` как за пределами, так и внутри цикла.

При необходимости можно указать `element` в `Next` инструкции. Это повышает удобочитаемость программы, особенно при наличии вложенных `For Each` циклов. Необходимо указать ту же переменную, которая указана в соответствующем `For Each` операторе.

Может возникнуть необходимость избежать изменения значения `element` внутри цикла. Это может усложнить чтение и отладку кода. Изменение значения `group` не влияет на коллекцию или ее элементы, которые были определены при первом входе в цикл.

При вложении циклов, если `Next` оператор внешнего уровня вложенности встречается перед `Next` внутренним уровнем, компилятор сообщает об ошибке. Однако компилятор может обнаружить эту перекрытие ошибки только в том случае, если указать `element` в каждой `Next` инструкции.

Если код зависит от прохода по коллекции в определенном порядке, то `For Each` цикл... `Next` не является лучшим выбором, если не известно о характеристиках объекта перечислителя, предоставляемого коллекцией. Порядок обхода не определяется Visual Basic, а <xref:System.Collections.IEnumerator.MoveNext%2A> методом объекта перечислителя. Поэтому вы не сможете предсказать, какой элемент коллекции первым должен возвращаться `element` , или что будет возвращено после заданного элемента. Вы можете достичь более надежных результатов, используя другую структуру цикла, например `For` ... `Next` или `Do` ... `Loop`

Среда выполнения должна иметь возможность преобразования элементов в `group` `element` . Оператор [ `Option Strict` ] определяет, разрешены ли расширяющие и сужающие преобразования ( `Option Strict` значение по умолчанию) или разрешены только расширяющие преобразования ( `Option Strict` включено). Дополнительные сведения см. в разделе [сужающие преобразования](#narrowing-conversions).

Тип данных `group` должен быть ссылочным типом, ссылающимся на коллекцию или массив, который является перечислимым. Чаще всего это означает, что `group` ссылается на объект, реализующий <xref:System.Collections.IEnumerable> интерфейс `System.Collections` пространства имен или <xref:System.Collections.Generic.IEnumerable%601> интерфейс `System.Collections.Generic` пространства имен. `System.Collections.IEnumerable` Определяет <xref:System.Collections.IEnumerable.GetEnumerator%2A> метод, который возвращает объект перечислителя для коллекции. Объект перечислителя реализует `System.Collections.IEnumerator` интерфейс `System.Collections` пространства имен и предоставляет <xref:System.Collections.IEnumerator.Current%2A> Свойства и <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> методы и. Visual Basic использует их для прохода по коллекции.

### <a name="narrowing-conversions"></a>сужающие преобразования

Если параметр `Option Strict` имеет значение `On` , сужающие преобразования обычно приводят к ошибкам компилятора. Однако в `For Each` операторе преобразования из элементов в `group` в `element` вычисляются и выполняются во время выполнения, а ошибки компилятора, вызванные сужающими преобразованиями, подавляются.

В следующем примере присваивание в `m` качестве начального значения для `n` не компилируется, если `Option Strict` имеет значение ON, так как преобразование `Long` в в `Integer` представляет собой понижающие преобразования. Однако в `For Each` инструкции не сообщается об ошибке компилятора, даже если для назначения `number` требуется такое же преобразование из `Long` в `Integer` . В `For Each` инструкции, содержащей большое число, при <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> применении к большому числу возникает ошибка времени выполнения.

:::code language="vb" source="./snippets/for-each-next-statement/vb/Program.vb":::

### <a name="ienumerator-calls"></a>Вызовы IEnumerator

При `For Each` начале выполнения цикла... `Next` Visual Basic проверяет, ссылается ли на `group` допустимый объект коллекции. В противном случае вызывается исключение. В противном случае он вызывает <xref:System.Collections.IEnumerator.MoveNext%2A> метод и <xref:System.Collections.IEnumerator.Current%2A> свойство объекта перечислителя, чтобы вернуть первый элемент. Если значение `MoveNext` указывает, что следующий элемент отсутствует, то есть если коллекция пуста, `For Each` цикл останавливается и управление передается оператору, следующему за `Next` оператором. В противном случае Visual Basic задает `element` первый элемент и выполняет блок операторов.

Каждый раз, когда Visual Basic обнаруживает `Next` оператор, он возвращается в `For Each` инструкцию. Снова вызывает метод `MoveNext` и `Current` , чтобы вернуть следующий элемент, и снова он либо выполняет блок, либо останавливает цикл в зависимости от результата. Этот процесс будет продолжен до тех пор, пока не `MoveNext` будет указано, что следующий элемент или `Exit For` оператор не обнаружен.

**Изменение коллекции.** Объект перечислителя, возвращаемый <xref:System.Collections.IEnumerable.GetEnumerator%2A> обычным способом, не позволяет изменить коллекцию, добавляя, удаляя, заменяя или переупорядочивая любые элементы. При изменении коллекции после запуска `For Each` цикла... `Next` объект перечислителя станет недопустимым, а следующая попытка доступа к элементу вызовет <xref:System.InvalidOperationException> исключение.

Однако эта блокировка изменений не определяется Visual Basic, а реализацией <xref:System.Collections.IEnumerable> интерфейса. Можно реализовать таким `IEnumerable` образом, чтобы можно было вносить изменения во время итерации. Если вы планируете выполнять такие динамические изменения, убедитесь, что понимаете характеристики реализации используемой `IEnumerable` коллекции.

**Изменение элементов коллекции.** <xref:System.Collections.IEnumerator.Current%2A>Свойство объекта перечислителя доступно [только для чтения](../modifiers/readonly.md)и возвращает локальную копию каждого элемента коллекции. Это означает, что нельзя изменять сами элементы в `For Each` цикле... `Next` Любые изменения влияют только на локальную копию из `Current` и не отражаются обратно в базовую коллекцию. Однако если элемент является ссылочным типом, можно изменить члены экземпляра, на который он указывает. В следующем примере изменяется `BackColor` элемент каждого `thisControl` элемента. Однако вы не можете изменить `thisControl` само себя.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

В предыдущем примере можно изменить `BackColor` элемент каждого `thisControl` элемента, хотя он не может изменить `thisControl` сам элемент.

**Обход массивов.** Поскольку <xref:System.Array> класс реализует <xref:System.Collections.IEnumerable> интерфейс, все массивы предоставляют <xref:System.Array.GetEnumerator%2A> метод. Это означает, что можно выполнить итерацию массива с помощью `For Each` цикла... `Next` Однако можно только считывать элементы массива. Их нельзя изменить.

## <a name="example"></a>Пример

В следующем примере выводится список всех папок в папке C:\. каталог с помощью <xref:System.IO.DirectoryInfo> класса.

:::code language="vb" source="./snippets/for-each-next-statement/vb/Examples.vb" id="foreachdir":::

## <a name="example"></a>Пример

Приведенный ниже пример демонстрирует процедуру сортировки коллекции. В этом примере выполняется сортировка экземпляров `Car` класса, которые хранятся в <xref:System.Collections.Generic.List%601> . Класс `Car` реализует интерфейс <xref:System.IComparable%601>, который требует реализации метода <xref:System.IComparable%601.CompareTo%2A>.

Каждый вызов <xref:System.IComparable%601.CompareTo%2A> метода выполняет одно сравнение, которое используется для сортировки. Написанный пользователем код в методе `CompareTo` возвращает значение для каждого сравнения текущего объекта с другим объектом. Возвращаемое значение меньше нуля, если текущий объект меньше другого объекта, больше нуля, если текущий объект больше другого объекта, и равняется нулю, если объекты равны. Это позволяет определить в коде условия для отношения «больше», «меньше» и «равно».

В методе `ListCars` оператор `cars.Sort()` сортирует список. Этот вызов метода <xref:System.Collections.Generic.List%601.Sort%2A><xref:System.Collections.Generic.List%601> приводит к тому, что метод `CompareTo` вызывается автоматически для объектов `Car` в `List`.

:::code language="vb" source="./snippets/for-each-next-statement/vb/Examples.vb" id="sort":::

## <a name="see-also"></a>См. также раздел

- [Коллекции](../../../standard/collections/index.md)
- [Оператор For…Next](for-next-statement.md)
- [Циклические структуры](../../programming-guide/language-features/control-flow/loop-structures.md)
- [Оператор While…End While](while-end-while-statement.md)
- [Оператор Do…Loop](do-loop-statement.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Инициализаторы объектов: именованные и анонимные типы](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Инициализаторы коллекций](../../programming-guide/language-features/collection-initializers/index.md)
- [Массивы](../../programming-guide/language-features/arrays/index.md)
