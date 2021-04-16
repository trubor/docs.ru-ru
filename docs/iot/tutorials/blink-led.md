---
title: Сигнал светодиодного индикатора
description: Сведения о включении и отключении сигнала (мигании) светодиодного индикатора с помощью библиотек Интернета вещей .NET.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 0d5db19faac0293b9982731f26dfd85d6ce07b3a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259034"
---
# <a name="blink-an-led"></a>Сигнал светодиодного индикатора

Контакты GPIO можно контролировать по отдельности. Это удобно для управления светодиодными индикаторами, ретрансляторами и другими устройствами с отслеживанием состояния. В этом разделе вы будете использовать .NET и контакты GPIO Raspberry Pi для подключения питания к светодиодному индикатору и активации повторяющегося мигания.

## <a name="prerequisites"></a>Предварительные требования

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- Светодиодный индикатор 5 мм
- Резистор 330 Ом
- монтажная плата;
- оптоволоконные кабеля с разъемами на обоих концах;
- Коммутационная плата GPIO Raspberry Pi (необязательно/рекомендуется)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a>Подготовка оборудования

Используйте компоненты оборудования для создания цепи, как показано на следующей схеме:

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="Схема Fritzing, демонстрирующая цепь со светодиодным индикатором и резистором" lightbox="../media/rpi-led_bb.png":::

На приведенном выше рисунке изображены следующие подключения:

- GPIO 18 к LED (более длинный, положительный вывод)
- Катод LED (более короткий, отрицательный вывод) к резистору 330 ОМ (любой конец)
- Резистор 330 ОМ (другой конец) к заземлению

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Создайте приложение

Выполните следующие действия в предпочитаемой среде разработки.

1. Создайте консольное приложение .NET с помощью [.NET CLI](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md). Назовите его *BlinkTutorial*.

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. Замените содержимое *Program.cs* кодом из этого примера.

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    В приведенном выше коде:

    - [Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `GpioController`. Объявление `using` гарантирует, что объект удален и аппаратные ресурсы освобождены должным образом.
    - Контакт GPIO 18 открыт для вывода.
    - Цикл `while` выполняется бесконечно. Каждая итерация:
        1. Записывает значение в контакт GPIO 18. Если `ledOn` имеет значение true, то записывает `PinValue.High` (вкл.). В противном случае записывается `PinValue.Low`.
        1. Переходит в спящий режим на 1000 мс.
        1. Переключает значение `ledOn`.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.

    ```bash
    ./BlinkTutorial
    ```

    Светодиодный индикатор мигает каждую секунду.

1. Завершите выполнение программы, нажав сочетание клавиш <kbd>CTRL+C</kbd>.

Поздравляем! Вы использовали GPIO для включения и отключения сигнала (мигания) светодиодного индикатора.

## <a name="get-the-source-code"></a>Получение исходного кода

Исходный код для этого учебника [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Считывание с датчика условий окружающей среды](../tutorials/temp-sensor.md)
