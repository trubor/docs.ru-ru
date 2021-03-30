---
title: Организация и тестирование проектов с помощью .NET CLI
description: В этом учебнике объясняется, как упорядочить и протестировать проекты .NET из командной строки.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: c668cff48a2418cc1bc34aef78ea26c863d9de6a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872682"
---
# <a name="organizing-and-testing-projects-with-the-net-cli"></a>Организация и тестирование проектов с помощью .NET CLI

Это руководство служит продолжением документа [Учебник. Создание консольного приложения с помощью .NET в Visual Studio Code](with-visual-studio-code.md), и с его помощью мы переходим от создания простых консольных приложений к разработке более сложных и структурированных приложений. В этом руководстве будет описано, как упорядочить код с помощью папок и расширить консольное приложение с помощью платформы тестирования [xUnit](https://xunit.net/).

## <a name="using-folders-to-organize-code"></a>Упорядочение кода с помощью папок

Если вы хотите добавить новые типы в консольное приложение, это можно сделать, добавив в приложение файлы, содержащие эти типы. Например, если добавить в проект файлы, содержащие типы `AccountInformation` и `MonthlyReportRecords`, это позволит получить плоскую и удобную для навигации структуру файлов проекта:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Однако этот подход можно применять только для относительно небольших проектов. Можете представить, что произойдет, если добавить в проект 20 типов? С таким количеством файлов в корневом каталоге проекта навигация по проекту и поддержка проекта будут представлять трудности.

Чтобы упорядочить проект, создайте новую папку для файлов типов и назовите ее *Models*. Поместите файлы типов в папку *Models*:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Проекты, в которых файлы логически упорядочены в папки, легко поддерживать. Они также отличаются удобной навигацией. В следующем разделе мы создадим более сложный пример проекта с папками и модульным тестированием.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Упорядочение и тестирование проекта на основе примера проекта с новыми типами для животных

### <a name="prerequisites"></a>Предварительные требования

* [Пакет SDK для .NET 5.0](https://dotnet.microsoft.com/download) или более поздней версии

### <a name="building-the-sample"></a>Создание примера

Для выполнения следующих действий можно воспользоваться [примером проекта с новыми типами для животных](https://github.com/dotnet/samples/tree/main/core/console-apps/NewTypesMsBuild) или создать собственные файлы и папки. Типы логически организованы в структуру папок, которая позволяет добавлять дополнительные типы. Тесты также организованы в структуру папок, которая позволяет добавлять дополнительные тесты.

В этом примере используются два типа, `Dog` и `Cat`, которые реализуют общий интерфейс `IPet`. Цель проекта `NewTypes` — упорядочить типы, связанные с животными, в папку *Pets*. Если впоследствии добавляется другой набор типов *WildAnimals*, они помещаются в папку *NewTypes* вместе с папкой *Pets*. Папка *WildAnimals* может содержать типы для животных, которые не являются домашними, например `Squirrel` и `Rabbit`. При таком добавлении типов структура проекта всегда остается хорошо упорядоченной.

Создайте следующую структуру папок, которая включает следующие файлы с указанным содержимым:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

*IPet.cs*:

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

Выполните следующую команду:

```dotnetcli
dotnet run
```

Вы получите следующие выходные данные:

```console
Woof!
Meow!
```

Необязательное упражнение: добавьте в проект новый тип животных, например `Bird`. Сделайте так, чтобы метод `TalkToOwner` для птицы возвращал владельцу `Tweet!`. Снова запустите приложение. Выходные данные будут включать `Tweet!`

### <a name="testing-the-sample"></a>Тестирование примера

Проект `NewTypes` развернут, и вы упорядочили типы, связанные с животными, в отдельную папку. Теперь давайте создадим тестовый проект и напишем тесты с помощью платформы тестирования [xUnit](https://xunit.net/). Модульное тестирование позволяет автоматически проверять правильную работу типов домашних животных.

Вернитесь в папку *src*, создайте папку *test*, а внутри нее — папку *NewTypesTests*. В командной строке перейдите в каталог *NewTypesTests* и выполните команду `dotnet new xunit`. Эта команда создает два файла: *NewTypesTests.csproj* и *UnitTest1.cs*.

Сейчас в тестовом проекте нельзя проверять типы в `NewTypes`. Для этого необходимо добавить в проект `NewTypes` ссылку на проект. Чтобы добавить ссылку на проект, выполните команду [`dotnet add reference`](../tools/dotnet-add-reference.md):

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Также можно добавить ссылку на проект вручную. Для этого добавьте узел `<ItemGroup>` в файл *NewTypesTests.csproj*:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

Файл *NewTypesTests.csproj* содержит следующие элементы:

* Ссылка на пакет `Microsoft.NET.Test.Sdk`, инфраструктура тестирования .NET
* Ссылка на пакет `xunit`, платформа тестирования xUnit
* Ссылка на пакет `xunit.runner.visualstudio`, средство выполнения тестов
* Ссылка на проект `NewTypes`, код для тестирования

Переименуйте файл *UnitTest1.cs* в *PetTests.cs* и замените код в файле на следующий:

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

Необязательное упражнение: если ранее был добавлен тип `Bird`, который предоставляет владельцу `Tweet!`, добавьте метод теста в файл *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, который проверит правильность работы метода `TalkToOwner` для типа `Bird`.

> [!NOTE]
> Несмотря на то, что значения `expected` и `actual` должны быть равны, в начальных проверочных утверждениях с проверкой `Assert.NotEqual` указывается, что они *не равны*. Всегда создавайте тест таким образом, чтобы он завершался с ошибкой, чтобы проверить логику теста. Убедившись, что тест не пройден, измените утверждение так, чтобы тест был пройден.

Ниже показана полная структура проекта:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

Запустите тест в папке *test/NewTypesTests*. Запустите тесты, выполнив команду [`dotnet test`](../tools/dotnet-test.md). Эта команда запускает средство запуска тестов, указанное в файле проекта.

Как и ожидалось, тест завершается с ошибкой, и в консоли отображаются следующие выходные данные:

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.50]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
  Failed PetTests.DogTalkToOwnerReturnsWoof [6 ms]
  Error Message:
   Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
  Stack Trace:
     at PetTests.DogTalkToOwnerReturnsWoof() in C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\PetTests.cs:line 13

Failed!  - Failed:     1, Passed:     1, Skipped:     0, Total:     2, Duration: 8 ms - NewTypesTests.dll (net5.0)
```

Измените проверочные утверждения в тестах с `Assert.NotEqual` на `Assert.Equal`:

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

Повторно запустите тесты, выполнив `dotnet test` команду, и получите следующие выходные данные:

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     2, Skipped:     0, Total:     2, Duration: 2 ms - NewTypesTests.dll (net5.0)
```

Тесты завершены успешно. Методы типов животных возвращают правильные значения при взаимодействии с владельцем.

Вы познакомились с тем, как упорядочить и тестировать проекты с помощью xUnit. Теперь вы можете приметь эти методы в собственных проектах. *Удачного программирования!*
