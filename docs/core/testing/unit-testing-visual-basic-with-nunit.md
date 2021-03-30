---
title: Модульное тестирование Visual Basic в .NET Core с помощью dotnet test и NUnit
description: Сведения о концепциях модульного тестирования в .NET Core в рамках пошаговой процедуры по созданию примера Visual Basic решения с помощью NUnit.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: 11334951d41c5cca24fcfb4853569e503cff97c5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874905"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Модульное тестирование библиотек .NET Core в Visual Basic с использованием dotnet test и NUnit

Этот учебник описывает пошаговую процедуру по созданию примера решения для изучения концепций модульного тестирования. Если при изучении учебника вы предпочитаете использовать готовое решение, [просмотрите или скачайте пример кода](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-vb-nunit/) перед началом работы. Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Предварительные требования

- [Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download) или более поздней версии.
- Текстовый редактор или редактор кода по вашему выбору.

## <a name="creating-the-source-project"></a>Создание исходного проекта

Откройте окно оболочки. Создайте каталог с именем *unit-testing-vb-nunit* для хранения решения. В этом каталоге выполните следующую команду, чтобы создать файл решения для библиотеки классов и тестового проекта:

```dotnetcli
dotnet new sln
```

Затем создайте каталог *PrimeService*. Ниже приведена актуальная структура файлов:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Перейдите в каталог *PrimeService* и выполните следующую команду, чтобы создать исходный проект:

```dotnetcli
dotnet new classlib -lang VB
```

Переименуйте *Class1.VB* в *PrimeService.VB*. Создайте сбойную реализацию класса `PrimeService`:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

Вернитесь в каталог *unit-testing-vb-using-mstest*. Чтобы добавить проект библиотеки классов в решение, выполните следующую команду:

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Создание тестового проекта

Затем создайте каталог *PrimeService.Tests*. Ниже представлена структура каталогов:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Перейдите в каталог *PrimeService.Tests* и создайте проект, выполнив следующую команду:

```dotnetcli
dotnet new nunit -lang VB
```

Команда [dotnet new](../tools/dotnet-new.md) создает тестовый проект, который использует NUnit в качестве библиотеки тестов. Созданный шаблон позволяет настроить средство выполнения тестов в файле *PrimeServiceTests.vbproj*:

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Тестовый проект требует других пакетов для создания и выполнения модульных тестов. Команда `dotnet new` на предыдущем шаге добавляет NUnit и адаптер тестирования NUnit. Теперь добавьте в проект библиотеку классов `PrimeService` в качестве еще одной зависимости. Используйте команду [`dotnet add reference`](../tools/dotnet-add-reference.md):

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Все содержимое файла можно просмотреть в [репозитории образцов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) на сайте GitHub.

Ниже показан окончательный макет решения:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

Выполните следующую команду в каталоге *unit-testing-vb-nunit*:

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>Создание первого теста

Напишите один тест сбоя теста, запустите его, а затем повторите этот процесс. В каталоге *PrimeService.Tests* переименуйте файл *UnitTest1.vb* в *PrimeService_IsPrimeShould.VB* и замените его содержимое следующим кодом:

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

Атрибут `<TestFixture>` указывает класс, который содержит тесты. Атрибут `<Test>` обозначает метод, который выполняется с помощью средства выполнения тестов. Из каталога *unit-testing-vb-nunit* выполните команду [`dotnet test`](../tools/dotnet-test.md) для создания тестов и библиотеки классов, а затем выполните тесты. Средство запуска тестов NUnit содержит точку входа в программу для выполнения тестов. `dotnet test` запускает средство выполнения тестов с помощью проекта модульного теста, который вы создали.

Тест не будет пройден. Вы еще не создали реализацию. Чтобы тест был пройден, напишите простейший код в классе `PrimeService`, который работает:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

Выполните команду `dotnet test` еще раз в каталоге *unit-testing-vb-nunit*. Команда `dotnet test` запускает сборку для проекта `PrimeService` и затем для проекта `PrimeService.Tests`. После сборки обоих проектов она запускает этот отдельный тест. Он выполняется.

## <a name="adding-more-features"></a>Добавление дополнительных возможностей

Теперь, когда тест проходит успешно, пора создать дополнительные тесты. Есть еще ряд элементарных случаев с простыми числами: 0, -1. Можно добавить их в качестве тестов с помощью атрибута `<Test>`, но это скоро станет утомительным. Есть другие атрибуты xUnit, которые позволяют создавать наборы похожих тестов.  Атрибут `<TestCase>` представляет набор тестов, которые выполняют один и тот же код, но имеют разные входные аргументы. С помощью атрибута `<TestCase>` можно указать значения для этих входных аргументов.

Вместо создания тестов примените эти два атрибута, чтобы создать последовательность тестов, которая проверяет несколько значений меньше 2, то есть наименьшего простого числа.

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Выполните команду `dotnet test`, и два из этих тестов завершаются ошибкой. Для успешного выполнения всех тестов нужно изменить предложение `if` в начале метода `Main` в файле *PrimeServices.cs*:

```vb
if candidate < 2
```

Продолжайте итерации, добавляя тесты, алгоритмы и код в главной библиотеке. В результате вы получите [готовую версию тестов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) и [полную реализацию библиотеки](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).

Вы создали небольшую библиотеку и набор модульных тестов для нее. Вы структурировали решение, чтобы сделать добавление новых пакетов и тестов частью обычного рабочего процесса и получить возможность сосредоточиться на задачах приложения.
