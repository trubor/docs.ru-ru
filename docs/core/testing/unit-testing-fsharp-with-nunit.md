---
title: Модульное тестирование F# в .NET Core с помощью dotnet test и NUnit
description: Сведения о концепциях модульного тестирования для F# в .NET Core в рамках пошаговой процедуры по созданию примера решения с помощью команды dotnet-test и NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 54513d3063ea0a3be8da73bcbd55962e839c6e2c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875061"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Модульное тестирование библиотек F# в .NET Core с использованием dotnet-test и NUnit

Этот учебник описывает пошаговую процедуру по созданию примера решения для изучения концепций модульного тестирования. Если при изучении учебника вы предпочитаете использовать готовое решение, [просмотрите или скачайте пример кода](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp-nunit/) перед началом работы. Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Предварительные требования

- [Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download) или более поздней версии.
- Текстовый редактор или редактор кода по вашему выбору.

## <a name="creating-the-source-project"></a>Создание исходного проекта

Откройте окно оболочки. Создайте каталог с именем *unit-testing-with-fsharp* для хранения решения.
В этом каталоге выполните следующую команду, чтобы создать файл решения для библиотеки классов и тестового проекта:

```dotnetcli
dotnet new sln
```

Затем создайте каталог *MathService*. Ниже приведена актуальная структура каталогов и файлов:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Перейдите к каталогу *MathService* и выполните следующую команду, чтобы создать исходный проект:

```dotnetcli
dotnet new classlib -lang "F#"
```

Создайте реализацию службы вычислений со сбоем:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Вернитесь в каталог *unit-testing-with-fsharp*. Чтобы добавить проект библиотеки классов в решение, выполните следующую команду:

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a>Создание тестового проекта

Затем создайте каталог *MathService.Tests*. Ниже представлена структура каталогов:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Перейдите к каталогу *MathService.Tests* и создайте проект, выполнив следующую команду:

```dotnetcli
dotnet new nunit -lang "F#"
```

При этом создается тестовый проект, который использует NUnit в качестве среды тестирования. Созданный шаблон настраивает средство выполнения тестов в файле *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Тестовый проект требует других пакетов для создания и выполнения модульных тестов. Команда `dotnet new` на предыдущем шаге добавляет NUnit и адаптер тестирования NUnit. Теперь добавьте в проект библиотеку классов `MathService` в качестве еще одной зависимости. Использование команды `dotnet add reference`:

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

Все содержимое файла можно просмотреть в [репозитории образцов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) на сайте GitHub.

Ниже показан окончательный макет решения:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

Выполните следующую команду в каталоге *unit-testing-with-fsharp*:

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>Создание первого теста

Напишите один тест сбоя теста, запустите его, а затем повторите этот процесс. Откройте файл *UnitTest1.fs* и добавьте следующий код:

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

Атрибут `[<TestFixture>]` обозначает класс, который содержит тесты. Атрибут `[<Test>]` обозначает метод теста, который выполняется с помощью средства выполнения тестов. В каталоге *unit-testing-with-fsharp* выполните команду `dotnet test` для создания тестов и библиотеки классов, а затем выполните тесты. Средство запуска тестов NUnit содержит точку входа в программу для выполнения тестов. `dotnet test` запускает средство выполнения тестов с помощью проекта модульного теста, который вы создали.

Эти два теста демонстрируют самые простые тесты, которые выполняются и завершаются сбоем. `My test` выполняется успешно, а `Fail every time` завершается сбоем. Сейчас создайте тест для метода `squaresOfOdds`. Метод `squaresOfOdds` возвращает последовательность квадратов всех нечетных целочисленных значений, которые являются частью входной последовательности. Вместо того чтобы писать все эти функции одновременно, можно постепенно создавать тесты, проверяющие функциональность. Если тест выполняется успешно, создается необходимая функция метода.

Самый простой тест — вызов `squaresOfOdds` со всеми четными числами, где результатом должна быть пустая последовательность целых чисел.  Вот этот тест:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Обратите внимание, что последовательность `expected` преобразована в список. Платформа NUnit зависит от многих стандартных типов .NET. Эта зависимость означает, что ваш открытый интерфейс и ожидаемые результаты поддерживают интерфейс <xref:System.Collections.ICollection>, а не <xref:System.Collections.IEnumerable>.

Когда вы запустите этот тест, он завершится сбоем. Вы еще не создали реализацию. Чтобы этот тест прошел успешно, напишите простейший код в классе *Library.fs* в своем рабочем проекте MathService:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

В каталоге *unit-testing-with-fsharp* снова выполните команду `dotnet test`. Команда `dotnet test` запускает сборку для проекта `MathService` и затем для проекта `MathService.Tests`. После сборки обоих проектов команда позволяет запустить ваши тесты. Теперь два теста пройдены.

## <a name="completing-the-requirements"></a>Выполнение требований

Теперь, когда тест проходит успешно, пора создать дополнительные тесты. Следующий простой пример работает с последовательностью, единственным нечетным числом которой является `1`. Число 1 использовать проще, потому что квадрат 1 равен 1. Вот этот тест:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Когда вы запустите `dotnet test`, новый тест завершится ошибкой. Необходимо обновить метод `squaresOfOdds`, чтобы обработать этот новый тест. Чтобы тест выполнялся успешно, необходимо отфильтровать все четные числа из последовательности. Чтобы сделать это, напишите небольшую функцию фильтра и используйте `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Обратите внимание на вызов `Seq.toList`. В результате создается список, который реализует интерфейс <xref:System.Collections.ICollection>.

Нужно выполнить еще один шаг: определить квадрат каждого из нечетных чисел. Начнем с написания нового теста:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Чтобы вычислить квадрат каждого нечетного числа, можно исправить тест, пропустив фильтрованную последовательность через операцию сопоставления:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

Вы создали небольшую библиотеку и набор модульных тестов для нее. Вы структурировали решение, чтобы сделать добавление новых пакетов и тестов частью обычного рабочего процесса и получить возможность сосредоточиться на задачах приложения.

## <a name="see-also"></a>См. также

- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
