---
title: Модульное тестирование кода C# в .NET Core с использованием dotnet test и xUnit
description: Сведения о концепциях модульного тестирования в C# и .NET Core в рамках пошаговой процедуры по созданию примера решения с помощью команды dotnet test и xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 10/21/2020
ms.openlocfilehash: fb4434fc4eebc009fa0bbe075d4d2290bff3b0bf
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873475"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Модульное тестирование C# в .NET Core с использованием dotnet test и xUnit

В этом руководстве описано, как создать решение c проектом модульного теста и проектом исходного кода. Чтобы работать с руководством на примере готового решения, [просмотрите или скачайте этот пример кода](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-using-dotnet-test/). Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).

## <a name="create-the-solution"></a>Создание решения

В этом разделе описано, как создать решение, которое содержит проект исходного кода и тестовый проект. Полное решение имеет следующую структуру каталогов:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

В инструкциях далее описано, как создать тестовое решение. См. [команды для быстрого создания тестового решения и дополнительные инструкции](#create-test-cmd).

* Откройте окно оболочки.
* Выполните следующую команду:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  Команда [`dotnet new sln`](../tools/dotnet-new.md) создает новое решение в каталоге *unit-testing-using-dotnet-test*.
* Теперь перейдите в папку *unit-testing-using-dotnet-test*.
* Выполните следующую команду:

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   Команда [`dotnet new classlib`](../tools/dotnet-new.md) создает новый проект библиотеки классов в папке *PrimeService*. Новая библиотека классов будет содержать код для тестирования.
* Переименуйте *Class1.cs* в *PrimeService.cs*.
* Замените код файла *PrimeService.cs* на код, приведенный ниже.
  
  ```csharp
  using System;

  namespace Prime.Services
  {
      public class PrimeService
      {
          public bool IsPrime(int candidate)
          {
              throw new NotImplementedException("Not implemented.");
          }
      }
  }
  ```

* Предыдущий код:
  * Создает исключение <xref:System.NotImplementedException> с сообщением о том, что код не реализован.
  * Мы обновим его позже.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* Выполните приведенную ниже команду в каталоге *unit-testing-using-dotnet-test*, чтобы добавить в решение проект библиотеки классов.

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Создайте проект *PrimeService.Tests*, выполнив следующую команду

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Предыдущая команда позволяет:
  * Создает проект *PrimeService.Tests* в каталоге *PrimeService.Tests*. В тестовом проекте используется библиотека тестов [xUnit](https://xunit.net/).
  * Настраивает средство выполнения тестов, добавляя следующие элементы `<PackageReference />` в файл проекта:
    * Microsoft.NET.Test.Sdk
    * xunit
    * xunit.runner.visualstudio

* Добавьте тестовый проект в файл решения, выполнив следующую команду:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* Добавьте в проект *PrimeService.Tests* библиотеку классов `PrimeService` в качестве зависимости:

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Команды для создания решения

В этом разделе перечислены все команды, описанные в предыдущем разделе. Пропустите этот раздел, если вы уже выполнили действия из предыдущего раздела.

Следующие команды создают тестовое решение на компьютере Windows. В macOS и UNIX измените в команде `ren` версию ОС на значение `ren`, чтобы переименовать файл:

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

Выполните инструкции по замене кода в файле *PrimeService.cs*, предложенные в предыдущем разделе.

## <a name="create-a-test"></a>Создание теста

Разработка на основе тестирования (TDD) обычно подразумевает написание теста до реализации целевого кода. В этом руководстве используется подход TDD. Метод `IsPrime` является вызываемым, но он пока не реализован. Тестовый вызов `IsPrime` завершается ошибкой. При использовании TDD мы создаем тест, который ожидаемо завершается ошибкой. Затем мы обновляем целевой код, чтобы пройти только созданный тест. Этот подход повторяется циклически: сначала вы создаете тест, который не выполняется, а затем обновляете целевой код, чтобы выполнить тест.

Обновите проект *PrimeService.Tests*.

* Удалите *PrimeService.Tests/UnitTest1.cs*.
* Создайте файл *PrimeService.Tests/PrimeService_IsPrimeShould.cs*.
* Замените код файла *PrimeService_IsPrimeShould.cs* кодом, приведенным ниже.

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var primeService = new PrimeService();
            bool result = primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

Атрибут `[Fact]` объявляет метод теста, который выполняется средством выполнения тестов. В папке *PrimeService.Tests* выполните `dotnet test`. Команда [dotnet test](../tools/dotnet-test.md) компилирует оба проекта и выполняет тесты. Средство запуска тестов xUnit содержит точку входа в программу для выполнения тестов. `dotnet test` запускает средство выполнения тестов, используя проект модульного тестирования.

Тест возвращает ошибку, так как мы еще не реализовали `IsPrime`. Согласно концепции TDD, нужно создавать только такой код, который позволит пройти этот тест. Обновите `IsPrime`, включив в него следующий код.

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Запустите `dotnet test`. Тест проходит.

### <a name="add-more-tests"></a>Добавьте дополнительные тесты.

Добавьте проверку простых чисел для 0 и -1. Можно скопировать предыдущий тест и изменить в нем код, чтобы использовать 0 и -1:

```csharp
var primeService = new PrimeService();
bool result = primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Копирование кода теста, в котором изменяется только один параметр, приводит к дублированию кода и раздуванию теста. Следующие атрибуты xUnit позволяют создавать набор сходных тестов.

- `[Theory]` представляет набор тестов, которые выполняют один и тот же код, но имеют разные входные аргументы.
- Атрибут `[InlineData]` задает значения для этих входных данных.

Чтобы не создавать новые тесты, примените указанные выше атрибуты xUnit для создания единой теории. Замените представленный ниже код.

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var primeService = new PrimeService();
    bool result = primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

следующим кодом:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

В приведенном выше коде `[Theory]` и `[InlineData]` позволяют тестировать несколько значений, не превышающих 2. Число 2 является наименьшим простым числом.

Выполните команду `dotnet test`, и два теста завершатся ошибкой. Поместите следующие код в метод `IsPrime`, чтобы успешно пройти все тесты:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Согласно концепции TDD, добавьте новые тесты, которые завершаются ошибкой, а затем обновите целевой код. Вы также можете изучить [готовую версию тестов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) и [полную реализацию библиотеки](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

Составленный нами метод `IsPrime` не является эффективным алгоритмом для тестирования простых чисел.

### <a name="additional-resources"></a>Дополнительные ресурсы

- [Официальный сайт xUnit.net](https://xunit.net)
- [Тестирование логики контроллера в ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
