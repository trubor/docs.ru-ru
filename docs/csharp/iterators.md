---
title: Iterators
description: Сведения о том, как использовать встроенные итераторы C# и создавать собственные настраиваемые методы итераторов.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 357f05f6ae1a4cec7566ddc821036354c932af90
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872643"
---
# <a name="iterators"></a>Iterators

Почти каждой написанной вами программе придется выполнять итерацию определенной коллекции. Для этого вы напишете код, проверяющий каждый элемент в коллекции.

Кроме того, вы создадите методы итератора — методы, которые итератор (то есть объект, который проходит по контейнеру, в частности списки) создает для элементов соответствующего класса. Их можно использовать в следующих целях:

+ Выполнение определенного действия с каждым элементом в коллекции.
+ Перечисление настраиваемой коллекции.
+ Расширение [LINQ](linq/index.md) или других библиотек.
+ Создание конвейера данных, обеспечивающего эффективный поток данных через методы итератора.

В языке C# предусмотрены функции, позволяющие использовать оба сценария. В этой статье представлены общие сведения об этих функциях.

Это руководство описывает несколько шагов. После каждого из них вы сможете запустить приложение и оценить результаты. Вы также можете [просмотреть или загрузить готовый пример](https://github.com/dotnet/samples/blob/main/csharp/iterators) для этого раздела. Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../samples-and-tutorials/index.md#view-and-download-samples).

## <a name="iterating-with-foreach"></a>Итерация для каждого

Вы полнить перечисление коллекции несложно. Ключевое слово `foreach` перечисляет коллекцию, выполняя внедренный оператор по одному разу для каждого элемента в коллекции:

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

Больше ничего не требуется. Для итерации содержимого той или иной коллекции нужен только это оператор `foreach`. При этом в работе оператора `foreach` нет ничего сложного. Он создает код, необходимый для итерации коллекции, опираясь на два универсальных интерфейса, определенных в библиотеке ядра .NET: `IEnumerable<T>` и `IEnumerator<T>`. Более подробно этот механизм рассматривается ниже.

Оба этих интерфейса также имеют неуниверсальные аналоги: `IEnumerable` и `IEnumerator`. [Универсальные](programming-guide/generics/index.md) версии более предпочтительны для современного кода.

## <a name="enumeration-sources-with-iterator-methods"></a>Источники перечисления с применением методов итератора

Еще одна полезная функция языка C# позволяет выполнять сборку методов, создающих источник для перечисления. Это так называемые *методы итератора*. Метод итератора определяет, какие образом будут создаваться объекты в последовательности по запросу. Метод итератора определяется с помощью контекстных ключевых слов `yield return`.

Напишем метод итератора, выдающий последовательность целых чисел от 0 до 9:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

Отдельные операторы `yield return` в этом коде показывают, что в любом методе итератора можно использовать сразу несколько дискретных операторов `yield return`.
Другие языковые конструкции можно (и нужно) включать для того, чтобы код метода итератора стал более простым. Точно такую же последовательность чисел выдает определение метода, приведенное ниже:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Выбирать какой-то один из этих вариантов необязательно. В код можно добавлять столько операторов `yield return`, сколько требуется для вашего метода:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    index = 100;
    while (index < 110)
        yield return index++;
}
```

Это базовый синтаксис. Рассмотрим практический пример применения метода итератора. Допустим, вы занимаетесь проектом IoT и имеете дело с датчиками устройств, которые создают большой поток данных. Чтобы получить представление об этих данных, можно написать метод, формирующий выборку из каждого N-го элемента данных. С этой задачей справится вот такой небольшой метод итератора:

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

Методы итератора подчиняются одному важному ограничению: в одном и том же методе не могут одновременно присутствовать оператор `return` и оператор `yield return`. Этот код компилироваться не будет:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

Обычно это ограничение не вызывает проблем. Вы можете либо использовать в методе операторы `yield return`, либо разделить исходный метод на несколько отдельных методов, одни из которых будут включать оператор `return`, а другие — `yield return`.

Немного изменим последний метод, вставив в каждом случае оператор `yield return`:

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

В некоторых случаях метод итератора лучше разбить на два разных метода. В одном будет использоваться оператор `return`, а в другом — `yield return`. Допустим, вам нужно получить пустую коллекцию или первые пять нечетных чисел, используя логический аргумент. Для этого можно написать следующие два метода:

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index < 10)
    {
        if (index % 2 == 1)
            yield return index;
        index++;
    }
}
```

Посмотрите на приведенные выше методы. В первом используется стандартный оператор `return`, который возвращает либо пустую коллекцию, либо итератор, созданный вторым методом. Второй метод включает оператор `yield return`, создающий запрошенную последовательность.

## <a name="deeper-dive-into-foreach"></a>Подробнее об операторе `foreach`

Оператор `foreach` разворачивается в стандартную идиому, которая выполняет итерацию всех элементов в коллекции с помощью интерфейсов `IEnumerable<T>` и `IEnumerator<T>`. Кроме того, он сводит к минимуму ошибки, допускаемые разработчиками в результате неправильного управления ресурсами.

Компилятор преобразует цикл `foreach`, показанный в первом примере, в конструкцию следующего вида:

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Эта конструкция представляет код, создаваемый компилятором C# версии 5 или более поздней. До выхода версии 5 переменная `item` имела другую область:

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Изменения были обусловлены тем, что прежнее поведение этой переменной могло вызывать с трудом выявляемые и поддающиеся диагностике ошибки, связанные с лямбда-выражениями. Дополнительные сведения о лямбда-выражениях см. в разделе [Лямбда-выражения](language-reference/operators/lambda-expressions.md).

На практике компилятор создает несколько более сложный код и устраняет ситуации, когда объект, возвращаемый методом `GetEnumerator()`, реализует интерфейс `IDisposable`. Полная версия кода выглядит так:

```csharp
{
    var enumerator = collection.GetEnumerator();
    try
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally
    {
        // dispose of enumerator.
    }
}
```

Способ ликвидации перечислителя зависит от характеристик типа `enumerator`. Как правило, предложение `finally` разворачивается следующим образом:

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Однако если тип `enumerator` является запечатанным, а тип `enumerator` не подвергается явному преобразованию в тип `IDisposable`, предложение `finally` разворачивается в пустой блок:

```csharp
finally
{
}
```

Если же тип `enumerator` подвергается неявному преобразованию в тип `IDisposable`, а `enumerator` является типом значения, не допускающим значение NULL, предложение `finally` разворачивается следующим образом:

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

К счастью, запоминать все это не нужно. Оператор `foreach` обрабатывает все эти нюансы в фоновом режиме, а компилятор создает правильный код для любой из этих конструкций.
