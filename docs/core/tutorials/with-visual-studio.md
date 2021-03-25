---
title: Создание консольного приложения .NET в Visual Studio
description: Узнайте, как создать консольное приложение .NET с помощью C# или Visual Basic в Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3986ef4083b964799be33d2876570ac4cf2082b8
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511857"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a>Учебник. Создание консольного приложения .NET в Visual Studio

В этом учебнике показано, как создать и запустить консольное приложение .NET с помощью Visual Studio 2019.

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019 версии 16.8 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой **Кроссплатформенная разработка .NET Core**. Пакет SDK для .NET 5.0 устанавливается автоматически при выборе этой рабочей нагрузки.

  См. раздел [Установка пакета SDK для .NET с помощью Visual Studio](../install/windows.md#install-with-visual-studio).

## <a name="create-the-app"></a>Создание приложения

Создайте проект консольного приложения .NET с именем HelloWorld.

1. Запустите Visual Studio 2019.

1. Выберите **Сервис** > **Параметры** > **Среда** > **Предварительная версия функций**, а затем выберите **Показывать все шаблоны .NET Core в новом проекте (требуется перезапуск)** .

   :::image type="content" source="media/with-visual-studio/dotnet-options.png" alt-text="Параметр &quot;Показывать все шаблоны .NET&quot;":::

1. Закройте и снова откройте Visual Studio.

1. На начальной странице выберите **Создать проект**.

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Кнопка &quot;Создать проект&quot;, выбранная на начальной странице Visual Studio":::

1. На странице **Создание проекта** введите в поле поиска **консоль**. Затем выберите **C#** или **Visual Basic** из списка языков, а затем — **Все платформы** из списка платформ. Выберите шаблон **Консольное приложение** и нажмите **Далее**.

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="Окно &quot;Создание проекта&quot; с выбранными фильтрами":::

   > [!TIP]
   > Если вы не видите шаблоны .NET, вероятно, у вас не установлена требуемая рабочая нагрузка. В сообщении **Не удается найти то, что ищете?** выберите ссылку **Установка других средств и компонентов**. Откроется Visual Studio Installer. Убедитесь, что у вас установлена рабочая нагрузка **Кроссплатформенная разработка .NET Core**.

1. В диалоговом окне **Настройка нового проекта** в поле **Имя проекта** введите **HelloWorld**. Нажмите кнопку **Далее**.

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="Окно настройки нового проекта с полями имени проекта, расположения и имени решения":::

1. В диалоговом окне **Дополнительные сведения** выберите **.NET 5.0 (текущая)** , а затем нажмите **Создать**.

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="Диалоговое окно &quot;Дополнительные сведения&quot;":::

Этот шаблон создает простое приложение Hello World. Он вызывает метод <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> для отображения сообщения "Hello World!" в окне консоли.

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

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine("Hello World!")
    End Sub
End Module
```

`Main` — точка входа в приложение. Это метод, который автоматически вызывается средой выполнения при запуске приложения. Все аргументы, предоставленные в командной строке при запуске приложения, доступны через массив *args*.

Если нужный язык не отображается, измените выбор языка в верхней части страницы.

## <a name="run-the-app"></a>Запуск приложения

1. Нажмите клавиши <kbd>CTRL</kbd>+<kbd>F5</kbd>, чтобы запустить программу без отладки.

   Откроется окно консоли с текстом "Hello World!" на экране.

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Окно консоли с приложением Hello World и надписью &quot;Чтобы продолжить, нажмите любую клавишу&quot;":::

1. Для закрытия консольного окна нажмите любую клавишу.

## <a name="enhance-the-app"></a>Улучшение приложения

Давайте расширим приложение. Теперь у пользователя будет запрашиваться имя, которое затем будет отображаться с датой и временем.

1. В *Program.cs* или *Program.vb* замените содержимое метода `Main` (строка, вызывающая `Console.WriteLine`) следующим кодом:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   Этот код отображает запрос в окне консоли и ожидает, чтобы пользователь ввел строку текста и нажал клавишу <kbd>ВВОД</kbd>. Приложение сохраняет полученную строку в переменной с именем `name`. Оно также получает значение свойства <xref:System.DateTime.Now?displayProperty=nameWithType>, которое содержит текущее локальное время, и присваивает его переменной с именем `date` (`currentDate` в Visual Basic). Затем оно отображает эти значения в окне консоли. Наконец, приложение выводит запрос в окне консоли и вызывает метод <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> для ожидания ввода данных пользователем.

   <xref:System.Environment.NewLine> — это независимый от платформы и языка способ для представления разрыва строки. Его альтернативами являются `\n` в C# и `vbCrLf` в Visual Basic.

   Знак доллара (`$`) перед строкой позволяет вставить такие выражения, как имена переменных, в фигурные скобки в строке. Значение выражения вставляется в строку вместо выражения. Такой синтаксис называется [интерполированными строками](../../csharp/language-reference/tokens/interpolated.md).

1. Нажмите клавиши <kbd>CTRL</kbd>+<kbd>F5</kbd>, чтобы запустить программу без отладки.

1. В ответ на приглашение в командной строке введите имя и нажмите клавишу <kbd>ВВОД</kbd>.

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="Окно консоли с измененными выходными данными программы":::

1. Для закрытия консольного окна нажмите любую клавишу.

## <a name="additional-resources"></a>Дополнительные ресурсы

- [Текущие выпуски и выпуски с долгосрочной поддержкой](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a>Следующие шаги

В этом учебнике показано, как создать консольное приложение .NET. В следующем учебнике описывается отладка приложения.

> [!div class="nextstepaction"]
> [Отладка консольного приложения .NET с помощью Visual Studio](debugging-with-visual-studio.md)
