---
title: Создание консольного приложения .NET с помощью Visual Studio для Mac
description: Узнайте, как создать консольное приложение .NET с помощью Visual Studio для Mac.
ms.date: 11/30/2020
ms.openlocfilehash: 4add8309338b8618265a66b9e71dab2df38ca8d0
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511831"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-for-mac"></a>Учебник. Создание консольного приложения .NET с помощью Visual Studio для Mac

В этом руководстве показано, как создать и запустить консольное приложение .NET с помощью Visual Studio для Mac.

> [!NOTE]
> Ваш отзыв очень важен. Вы можете отправить отзыв о Visual Studio для Mac команде разработчиков двумя способами.
>
> * В Visual Studio для Mac выберите пункт **Справка** > **Сообщить о проблеме** в меню или элемент **Сообщить о проблеме** на экране приветствия. При этом открывается окно для заполнения отчета об ошибках. Отслеживать свои отзывы можно на портале [сообщества разработчиков](https://aka.ms/feedback/report?space=41).
> * Чтобы внести предложение, выберите пункт **Справка** > **Отправить предложение** в меню или элемент **Отправить предложение** на экране приветствия. При этом открывается [веб-страница сообщества разработчиков Visual Studio для Mac](https://aka.ms/feedback/suggest?space=41).

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio для Mac 8.8 или более поздней версии.](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) Выберите вариант установки .NET Core. Установка Xamarin является необязательным шагом для разработки в .NET. Дополнительные сведения см. в следующих ресурсах:

  * [Учебник. Установка Visual Studio для Mac](/visualstudio/mac/installation).
  * [Поддерживаемые версии macOS](../install/windows.md).
  * [Версии .NET, поддерживаемые Visual Studio для Mac.](/visualstudio/mac/net-core-support)

## <a name="create-the-app"></a>Создание приложения

1. Запустите Visual Studio для Mac.

1. Выберите **Создать** в окне запуска.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Кнопка Создать на экране запуска Visual Studio для Mac":::

1. В узле **Web and Console** (Интернет и Консоль) диалогового окна **Создание проекта** выберите **Приложение**. Выберите шаблон **Консольное приложение** и нажмите кнопку **Далее**.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Список шаблонов для создания проектов":::

1. В раскрывающемся списке **Целевая платформа** диалогового окна **Configure your new Console Application** (Настройка нового консольного приложения) выберите **.NET 5.0** и щелкните **Далее**.

1. Введите HelloWorld в поле **Имя проекта** и щелкните **Создать**.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Диалоговое окно настройки нового консольного приложения":::

Этот шаблон создает простое приложение Hello World. Он вызывает метод <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> для отображения сообщения "Hello World!" в окне терминала.

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

`Main` — точка входа в приложение. Это метод, который автоматически вызывается средой выполнения при запуске приложения. Все аргументы, предоставленные в командной строке при запуске приложения, доступны через массив `args`.

## <a name="run-the-app"></a>Запуск приложения

1. Чтобы запустить приложение без отладки, выберите <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd>+<kbd>Command</kbd>+<kbd>ВВОД</kbd>).

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="В терминале отобразится сообщение Hello World!":::

1. Закройте окно **терминала**.

## <a name="enhance-the-app"></a>Улучшение приложения

Давайте расширим приложение. Теперь у пользователя будет запрашиваться имя, которое затем будет отображаться с датой и временем.

1. В *Program.cs* замените содержимое метода `Main` (строка, вызывающая `Console.WriteLine`) следующим кодом:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   Этот код отображает запрос в окне консоли и ожидает, чтобы пользователь ввел строку текста и нажал клавишу <kbd>ВВОД</kbd>. Приложение сохраняет полученную строку в переменной с именем `name`. Оно также получает значение свойства <xref:System.DateTime.Now?displayProperty=nameWithType>, которое содержит текущее локальное время, и присваивает его переменной с именем `date`. Затем оно отображает эти значения в окне консоли. Наконец, приложение выводит запрос в окне консоли и вызывает метод <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> для ожидания ввода данных пользователем.

   <xref:System.Environment.NewLine> — это независимый от платформы и языка способ для представления разрыва строки. Его альтернативами являются `\n` в C# и `vbCrLf` в Visual Basic.

   Знак доллара (`$`) перед строкой позволяет вставить такие выражения, как имена переменных, в фигурные скобки в строке. Значение выражения вставляется в строку вместо выражения. Такой синтаксис называется [интерполированными строками](../../csharp/language-reference/tokens/interpolated.md).

1. Чтобы запустить приложение, выберите <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd>+<kbd>Command</kbd>+<kbd>ВВОД</kbd>).

1. В ответ на приглашение в командной строке введите имя и нажмите клавишу <kbd>ВВОД</kbd>.

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Терминал с измененными выходными данными программы":::

1. Закройте терминал.

## <a name="next-steps"></a>Следующие шаги

В этом учебнике показано, как создать консольное приложение .NET. В следующем учебнике описывается отладка приложения.

> [!div class="nextstepaction"]
> [Отладка консольного приложения .NET с помощью Visual Studio для Mac](debugging-with-visual-studio-mac.md)
