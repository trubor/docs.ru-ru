---
title: Создание консольного приложения .NET в Visual Studio Code
description: Узнайте, как создать консольное приложение .NET с помощью Visual Studio Code и .NET CLI.
ms.date: 11/17/2020
ms.openlocfilehash: 51e5a897985af7576de03659efdd8520cb8e58e6
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511870"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-code"></a>Учебник. Создание консольного приложения .NET в Visual Studio Code

В этом учебнике показано, как создать и запустить консольное приложение .NET с помощью Visual Studio Code и .NET CLI. Задачи проекта, такие как создание, компиляция и запуск проекта, выполняются с помощью .NET CLI, поэтому вы можете следовать этому руководству, используя при желании другой редактор кода и выполняя команды в терминале.

## <a name="prerequisites"></a>Предварительные требования

1. Установленная платформа [Visual Studio Code](https://code.visualstudio.com/) с [расширением C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp). См. сведения об [установке расширений Visual Studio Code из Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [Пакет SDK для .NET 5.0 или более поздней версии](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>Создание приложения

Создайте проект консольного приложения .NET с именем HelloWorld.

1. Запустите Visual Studio Code.

1. В главном меню выберите **Файл** > **Открыть папку** (в macOS выберите **File** > **Open...**  (Файл > Открыть)).

1. В диалоговом окне **Открытие папки** создайте папку *HelloWorld* и щелкните **Выбрать папку** (в macOS щелкните **Open** (Открыть)).

   Имя папки по умолчанию преобразуется в имя проекта и имя пространства имен. Вы добавите код позже в этом учебнике. Предполагается, что пространство имен проекта — `HelloWorld`.

1. Откройте **терминал** в Visual Studio Code, выбрав в основном меню пункт **Вид** > **Терминал**.

   Откроется окно **Терминал** с командной строкой в папке *HelloWorld*.

1. В **окне терминала** введите следующую команду:

   ```dotnetcli
   dotnet new console
   ```

Этот шаблон создает простое приложение Hello World. Он вызывает метод <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> для вывода ":::no-loc text="Hello World!":::" в окне консоли.

Код шаблона определяет класс `Program` с одним методом `Main`, который принимает в качестве аргумента массив <xref:System.String>.

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

`Main` — точка входа в приложение. Это метод, который автоматически вызывается средой выполнения при запуске приложения. Все аргументы, предоставленные в командной строке при запуске приложения, доступны через массив *args*.

## <a name="run-the-app"></a>Запуск приложения

Выполните следующие команды в **окне терминала**:

```dotnetcli
dotnet run
```

В программе отобразится сообщение "Hello World!", после чего она завершится.

![Команда dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>Улучшение приложения

Давайте расширим приложение. Теперь у пользователя будет запрашиваться имя, которое затем будет отображаться с датой и временем.

1. Откройте файл *Program.cs*, щелкнув его.

   Когда вы в первый раз открываете файл C# в Visual Studio Code, в редакторе загружается [OmniSharp](https://www.omnisharp.net/).

   ![Откройте файл Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. Когда в Visual Studio Code будет предложено добавить недостающие ресурсы для сборки и отладки приложения, выберите **Да**.

   ![Предупреждение о недостающих ресурсах](media/with-visual-studio-code/missing-assets.png)

1. В *Program.cs* замените содержимое метода `Main` (строка, вызывающая `Console.WriteLine`) следующим кодом:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   Этот код отображает запрос в окне консоли и ожидает, чтобы пользователь ввел строку текста и нажал клавишу <kbd>ВВОД</kbd>. Приложение сохраняет полученную строку в переменной с именем `name`. Оно также получает значение свойства <xref:System.DateTime.Now?displayProperty=nameWithType>, которое содержит текущее локальное время, и присваивает его переменной с именем `date`. Затем оно отображает эти значения в окне консоли. Наконец, приложение выводит запрос в окне консоли и вызывает метод <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> для ожидания ввода данных пользователем.

   <xref:System.Environment.NewLine> — это независимый от платформы и языка способ для представления разрыва строки. Его альтернативами являются `\n` в C# и `vbCrLf` в Visual Basic.

   Знак доллара (`$`) перед строкой позволяет вставить такие выражения, как имена переменных, в фигурные скобки в строке. Значение выражения вставляется в строку вместо выражения. Такой синтаксис называется [интерполированными строками](../../csharp/language-reference/tokens/interpolated.md).

1. Сохраните изменения.

   > [!IMPORTANT]
   > В Visual Studio Code необходимо явно сохранить изменения. В отличие от Visual Studio, изменения файлов не сохраняются автоматически при сборке и запуске приложения.

1. Запустите программу еще раз:

   ```dotnetcli
   dotnet run
   ```

1. В ответ на приглашение в командной строке введите имя и нажмите клавишу <kbd>ВВОД</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Окно терминала с измененными выходными данными программы":::

1. Нажмите любую клавишу для выхода из программы.

## <a name="additional-resources"></a>Дополнительные ресурсы

- [Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) (Настройка Visual Studio Code)

## <a name="next-steps"></a>Следующие шаги

В этом учебнике показано, как создать консольное приложение .NET. В следующем учебнике описывается отладка приложения.

> [!div class="nextstepaction"]
> [Отладка консольного приложения .NET с помощью Visual Studio Code](debugging-with-visual-studio-code.md)
