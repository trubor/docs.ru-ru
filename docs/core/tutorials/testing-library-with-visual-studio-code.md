---
title: Тестирование библиотеки классов .NET с помощью Visual Studio Code
description: Узнайте, как использовать Visual Studio Code и CLI .NET для создания и запуска проекта модульного теста для библиотеки классов .NET.
ms.date: 11/17/2020
ms.openlocfilehash: bc8741e11504f94e54ccc45a5ad93408a3fe9309
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511818"
---
# <a name="tutorial-test-a-net-class-library-using-visual-studio-code"></a>Учебник. Тестирование библиотеки классов .NET с помощью Visual Studio Code

В этом руководстве показано, как автоматизировать модульное тестирование путем добавления тестового проекта в решение.

## <a name="prerequisites"></a>Предварительные требования

- В этом руководстве используется решение, созданное при работе со статьей [Создание библиотеки классов .NET в Visual Studio Code](library-with-visual-studio-code.md).

## <a name="create-a-unit-test-project"></a>Создание проекта модульного теста

Модульные тесты обеспечивают автоматическое тестирование программного обеспечения во время разработки и публикации. В этом руководстве используется платформа тестирования MSTest. [MSTest](https://github.com/Microsoft/testfx-docs) — это одна из трех доступных для выбора платформ тестирования. Другими являются [xUnit](https://xunit.net/) и [nUnit](https://nunit.org/).

1. Запустите Visual Studio Code.

1. Откройте решение`ClassLibraryProjects`, созданное при работе со статьей [Создание библиотеки классов .NET в Visual Studio Code](library-with-visual-studio-code.md).

1. Создайте проект модульного теста с именем StringLibraryTest.

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   Шаблон проекта создает файл UnitTest1.cs со следующим кодом:

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   Исходный код, созданный шаблоном модульного теста, выполняет следующие действия.

   - Он импортирует пространство имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, которое содержит типы, используемые для модульного тестирования.
   - Он применяет атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> к классу `UnitTest1`.
   - Он применяет атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> для определения `TestMethod1`.

   При запуске модульного теста автоматически выполняются все методы теста, помеченные атрибутом [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), в тестовом классе, помеченном атрибутом [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute).

1. Добавьте тестовый проект в решение.

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a>Добавление ссылки на проект

Чтобы тестовый проект работал с классом `StringLibrary`, добавьте в проект `StringLibraryTest` ссылку на проект `StringLibrary`.

1. Выполните следующую команду:

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a>Добавление и выполнение методов модульного теста

При запуске модульного теста Visual Studio выполняет каждый метод, помеченный атрибутом <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>, в классе, помеченном атрибутом <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>. Метод теста завершается, когда происходит первый сбой или когда все тесты, содержащиеся в методе, будут успешно выполнены.

В самых распространенных тестах вызываются члены класса <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Многие методы утверждения (Assert) принимают по крайней мере два параметра, из которых один представляет ожидаемый результат теста, а второй — фактический результат теста. Наиболее популярные из этих методов класса `Assert` перечислены в следующей таблице:

| Методы утверждения     | Функция |
| ------------------ | -------- |
| `Assert.AreEqual`  | Проверяет равенство двух значений или объектов. Утверждение не выполняется, если значения или объекты не равны. |
| `Assert.AreSame`   | Проверяет, что две объектные переменные ссылаются на один и тот же объект. Утверждение не выполняется, если переменные ссылаются на разные объекты. |
| `Assert.IsFalse`   | Проверяет, что условие имеет значение `false`. Утверждение не выполняется, если условие имеет значение `true`. |
| `Assert.IsNotNull` | Проверяет, что объект не имеет значение `null`. Утверждение не выполняется, если объект является `null`. |

Вы можете также использовать метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> в методе теста, чтобы указать тип исключения, которое он должен создавать. Такой тест считается не выполненным, если заявленное исключение не было создано.

Для тестирования метода `StringLibrary.StartsWithUpper` необходимо предоставить несколько строк, которые начинаются с символов верхнего регистра. Предполагается, что в этих случаях метод возвратит `true`, поэтому можно вызвать метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>. Представьте также несколько строк, которые не начинаются с символов верхнего регистра. Предполагается, что в этих случаях метод возвратит `false`, поэтому можно вызвать метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.

Так как метод библиотеки обрабатывает строки, необходимо также убедиться, что он обрабатывает [пустую строку (`String.Empty`)](xref:System.String.Empty), а также строку `null`. Пустая строка не содержит символов, а ее свойство <xref:System.String.Length> равно 0. Строка `null` является неинициализированной строкой. Метод `StartsWithUpper` можно вызвать напрямую как статический метод и передать ему один аргумент типа <xref:System.String>. Или метод `StartsWithUpper` можно вызвать как метод расширения для переменной `string`, которой назначено значение `null`.

Вы определите три метода, каждый из которых вызывает метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> для каждого элемента в массиве строк. Вы вызовете перегруженную версию метода, которая позволяет указать сообщение об ошибке, отображаемое в случае сбоя теста. В этом сообщении определяется строка, вызвавшая сбой.

Создание методов теста:

1. Откройте файл *StringLibraryTest/UnitTest1.cs* и замените все его содержимое следующим кодом:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   Тест на символы верхнего регистра в методе `TestStartsWithUpper` включает заглавную греческую букву "альфа" (U+0391) и заглавную кириллическую букву "М" (U+041C). Тест на символы нижнего регистра в методе `TestDoesNotStartWithUpper` включает строчную греческую букву "альфа" (U+03B1) и строчную кириллическую букву "г" (U+0433).

1. Сохраните изменения.

1. Запустите тесты.

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   В выходных данных терминала показано, что все тесты пройдены.

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.

   Passed!  - Failed:     0, Passed:     3, Skipped:     0, Total:     3, Duration: 3 ms - StringLibraryTest.dll (net5.0)
   ```

## <a name="handle-test-failures"></a>Обработка сбоев теста

Выполняя разработку на основе тестирования (TDD), вы сначала пишете тесты, и они завершаются сбоем при первом запуске. Затем вы добавляете код в приложение, и тест успешно выполняется. В рамках этого учебника вы создали тест после написания кода приложения для его проверки, поэтому тест был пройден. Чтобы проверить, завершается ли тест ошибкой, как и ожидается, добавьте недопустимое значение во входные данные теста.

1. Измените массив `words` в методе `TestDoesNotStartWithUpper`, включив в него строку "Error".

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Запустите тесты.

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   В выходных данных терминала показано, что один тест завершается ошибкой, и выдается сообщение об ошибке для непройденного теста. "Assert.IsFalse failed. Expected for 'Error': false; actual: True". Из-за этого сбоя строки в массиве, расположенные после слова "Error", не проверялись.

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.
     Failed TestDoesNotStartWithUpper [28 ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
        at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper() in C:\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Failed!  - Failed:     1, Passed:     2, Skipped:     0, Total:     3, Duration: 31 ms - StringLibraryTest.dll (net5.0)
   ```

1. Удалите строку "Error", которую вы добавили на шаге 1. Еще раз запустите тест. Теперь тесты будут пройдены.

## <a name="test-the-release-version-of-the-library"></a>Тестирование версии выпуска для библиотеки

Теперь, когда все тесты пройдены при выполнении сборки в режиме отладки, следует запустить все тесты еще раз, теперь уже для сборки библиотеки в режиме выпуска. Некоторые факторы, например оптимизации компилятора, иногда могут вызывать разное поведение сборки в режимах отладки и выпуска.

1. Запустите тесты с конфигурацией сборки "Выпуск".

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   Все тесты будут пройдены.

## <a name="debug-tests"></a>Отладка тестов

Если в качестве IDE вы используете Visual Studio Code, то можете следовать инструкциям из руководства по [отладке консольного приложения .NET с помощью Visual Studio Code](debugging-with-visual-studio-code.md), чтобы выполнить отладку кода с применением проекта модульного теста. Вместо запуска проекта приложения *ShowCase* , откройте *StringLibraryTest/UnitTest1.cs* и выберите элемент **Выполнить все тесты** между строками 7 и 8. Если вы не можете найти его, нажмите клавиши <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>, чтобы открыть палитру команд, и введите команду **перезагрузки окна**.

Visual Studio Code запускает тестовый проект с присоединенным отладчиком. Выполнение будет прервано в любой точке останова, добавленной в тестовый проект или базовый код библиотеки.

## <a name="additional-resources"></a>Дополнительные ресурсы

* [Модульное тестирование в .NET](../testing/index.md)

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы выполнили модульное тестирование библиотеки классов. Чтобы сделать библиотеку доступной другим пользователям, опубликуйте ее в [NuGet](https://nuget.org) в качестве пакета. Чтобы узнать, как это делать, следуйте указаниям в руководстве по NuGet:

> [!div class="nextstepaction"]
> [Создание и публикация пакета с помощью CLI dotnet](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

Если библиотека опубликована как пакет NuGet, ее могут устанавливать и использовать другие пользователи. Чтобы узнать, как это делать, следуйте указаниям в руководстве по NuGet:

> [!div class="nextstepaction"]
> [Установка и использование пакета с помощью CLI dotnet](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

Библиотеку не нужно распространять как пакет. Ее можно объединить с консольным приложением, где она используется. Чтобы узнать, как опубликовать консольное приложение, ознакомьтесь с предыдущим руководством в этой серии:

> [!div class="nextstepaction"]
> [Публикация консольного приложения .NET с помощью Visual Studio Code](publishing-with-visual-studio-code.md)
