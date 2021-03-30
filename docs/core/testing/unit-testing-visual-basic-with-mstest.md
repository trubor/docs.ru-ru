---
title: Модульное тестирование .NET Core в Visual Basic с помощью dotnet test и MSTest
description: Сведения о концепциях модульного тестирования в .NET Core в рамках пошаговой процедуры по созданию примера Visual Basic решения с помощью MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9ab85b2e688f5f31d0981fbee618212ac6ea5a19
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873501"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a>Модульное тестирование библиотек .NET Core в Visual Basic с использованием dotnet test и MSTest

Этот учебник описывает пошаговую процедуру по созданию примера решения для изучения концепций модульного тестирования. Если при изучении учебника вы предпочитаете использовать готовое решение, [просмотрите или скачайте пример кода](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-vb-mstest/) перед началом работы. Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Создание исходного проекта

Откройте окно оболочки. Создайте каталог с именем *unit-testing-vb-mstest* для хранения решения.
В этом каталоге выполните команду выполните команду [`dotnet new sln`](../tools/dotnet-new.md), чтобы создать решение. Этот метод упрощает управление библиотекой классов и проектом модульного теста.
В каталоге решения создайте каталог *PrimeService*. На данный момент структура каталогов и файлов выглядит следующим образом:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

Перейдите в каталог *PrimeService* и выполните команду [`dotnet new classlib -lang VB`](../tools/dotnet-new.md), чтобы создать исходный проект. Переименуйте *Class1.VB* в *PrimeService.VB*. Создайте сбойную реализацию класса `PrimeService`:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Вернитесь в каталог *unit-testing-vb-using-mstest*. Чтобы добавить проект библиотеки классов в решение, выполните команду [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md).

## <a name="creating-the-test-project"></a>Создание тестового проекта

Затем создайте каталог *PrimeService.Tests*. Ниже представлена структура каталогов:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Перейдите в каталог *PrimeService.Tests* и создайте проект с помощью [`dotnet new mstest -lang VB`](../tools/dotnet-new.md). Эта команда создает тестовый проект, использующий MSTest в качестве библиотеки тестов. Созданный шаблон настраивает средство выполнения тестов в файле *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Тестовый проект требует других пакетов для создания и выполнения модульных тестов. Команда `dotnet new` на предыдущем шаге добавила MSTest и средство выполнения тестов MSTest. Теперь добавьте в проект библиотеку классов `PrimeService` в качестве еще одной зависимости. Используйте команду [`dotnet add reference`](../tools/dotnet-add-reference.md):

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Все содержимое файла можно просмотреть в [репозитории образцов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) на сайте GitHub.

Ниже показан окончательный макет решения:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Выполните команду [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) в каталоге *unit-testing-vb-mstest*.

## <a name="creating-the-first-test"></a>Создание первого теста

Напишите один тест сбоя теста, запустите его, а затем повторите этот процесс. Удалите файл *UnitTest1.vb* из каталога *PrimeService.Tests* и создайте файл Visual Basic с именем *PrimeService_IsPrimeShould.VB*. Добавьте следующий код:

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

Атрибут `<TestClass>` указывает класс, который содержит тесты. Атрибут `<TestMethod>` обозначает метод, который выполняется с помощью средства выполнения тестов. Из каталога *unit-testing-vb-mstest* выполните команду [`dotnet test`](../tools/dotnet-test.md) для создания тестов и библиотеки классов, а затем выполните тесты. Средство запуска тестов MSTest содержит точку входа в программу для выполнения тестов. `dotnet test` запускает средство выполнения тестов с помощью проекта модульного теста, который вы создали.

Тест не будет пройден. Вы еще не создали реализацию. Чтобы тест был пройден, напишите простейший код в классе `PrimeService`, который работает:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

Выполните команду `dotnet test` еще раз в каталоге *unit-testing-vb-mstest*. Команда `dotnet test` запускает сборку для проекта `PrimeService` и затем для проекта `PrimeService.Tests`. После сборки обоих проектов она запускает этот отдельный тест. Он выполняется.

## <a name="adding-more-features"></a>Добавление дополнительных возможностей

Теперь, когда тест проходит успешно, пора создать дополнительные тесты. Есть еще ряд элементарных случаев с простыми числами: 0, -1. Можно добавить их в качестве тестов с помощью атрибута `<TestMethod>`, но это скоро станет утомительным. Есть другие атрибуты MSTest, которые позволяют создавать наборы похожих тестов.  Атрибут `<DataTestMethod>` представляет набор тестов, которые выполняют один и тот же код, но имеют разные входные аргументы. С помощью атрибута `<DataRow>` можно указать значения для этих входных аргументов.

Вместо того чтобы создавать новые тесты, используйте эти два атрибута, чтобы создать единый алгоритм, который проверяет несколько значений меньше 2, то есть наименьшего простого числа:

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-mstest/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Выполните команду `dotnet test`, и два из этих тестов завершаются ошибкой. Для успешного выполнения всех тестов нужно изменить предложение `if` в начале метода:

```vb
if candidate < 2
```

Продолжайте итерации, добавляя тесты, алгоритмы и код в главной библиотеке. В результате вы получите [готовую версию тестов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) и [полную реализацию библиотеки](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).

Вы создали небольшую библиотеку и набор модульных тестов для нее. Вы структурировали решение, чтобы сделать добавление новых пакетов и тестов частью обычного рабочего процесса и получить возможность сосредоточиться на задачах приложения.
