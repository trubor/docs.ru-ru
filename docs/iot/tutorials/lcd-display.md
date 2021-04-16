---
title: Отображение текста на ЖК-дисплее
description: Сведения об отображении символов на ЖК-дисплеях с помощью библиотек Интернета вещей .NET.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 005b40a7d9f46b84fcd90541248f5f4fd243e612
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "102255551"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="display-text-on-an-lcd"></a>Отображение текста на ЖК-дисплее

Символьные ЖК-дисплеи удобно использовать для отображения информации без внешнего монитора. Обычные символьные ЖК-дисплеи можно подключить напрямую к контактам GPIO, но в этом случае требуется использовать до 10 контактов GPIO. В сценариях, требующих подключения к комбинации устройств, зачастую нецелесообразно выделять большую часть верхнего контактного ряда GPIO для символьного дисплея.

Многие производители продают символьные ЖК-дисплеи размером 20x4 со встроенным расширителем GPIO. Символьный дисплей напрямую подключается к расширителю GPIO, который затем подключается к устройству Raspberry Pi через последовательный протокол I2C.

В этом разделе вы будете использовать .NET для отображения текста на символьном ЖК-дисплее с помощью расширителя GPIO I2C.

## <a name="prerequisites"></a>Предварительные требования

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [Символьный ЖК-дисплей размером 20x4 с интерфейсом I2C](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)
- оптоволоконные кабеля с разъемами на обоих концах;
- Монтажная плата (необязательно/рекомендуется)
- Коммутационная плата GPIO Raspberry Pi (необязательно/рекомендуется)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> Существует множество производителей символьных ЖК-дисплеев. Большинство конструкций похожи, и производители не видят никакой разницы в функционале. Для справки: это руководство было разработано для [LCD2004](https://www.sunfounder.com/lcd2004-module.html).

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>Подготовка оборудования

Используйте соединительные провода, чтобы подключить четыре контакта на расширителе I2C к устройству Raspberry Pi следующим образом:

- DGND к заземлению
- VCC к 5V
- SDA к SDA (GPIO 2)
- SCL к SCL (GPIO 3)

При необходимости ознакомьтесь со следующими рисунками:

| Интерфейс I2C (обратная сторона дисплея) | GPIO Raspberry Pi |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="Изображение обратной стороны символьного дисплея с расширителем I2C GPIO." lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Диаграмма, показывающая схему контактов верхнего контактного ряда GPIO Raspberry Pi. Изображение взято с Raspberry Pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br />[Изображение взято с Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Создайте приложение

Выполните следующие действия в предпочитаемой среде разработки.

1. Создайте консольное приложение .NET с помощью [.NET CLI](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md). Назовите его *LcdTutorial*.

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. Замените содержимое *Program.cs* кодом из этого примера.

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    В приведенном выше коде:

    - [Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `I2cDevice`, вызывая метод `I2cDevice.Create` и передавая новый класс `I2cConnectionSettings` с параметрами `busId` и `deviceAddress`. Класс `I2cDevice` представляет шину I2C. Объявление `using` гарантирует, что объект удален и аппаратные ресурсы освобождены должным образом.

        > [!WARNING]
        > Адрес устройства для расширителя GPIO зависит от микросхемы, используемой производителем. Расширители GPIO, оснащенные PCF8574, используют адрес `0x27`, а расширители с микросхемами PCF8574A используют `0x3F`. Обратитесь к документации по ЖК-дисплею.

    - Другое объявление `using` создает экземпляр `Pcf8574` и передает `I2cDevice` конструктору. Этот экземпляр представляет расширитель GPIO.
    - Другое объявление `using` создает экземпляр `Lcd2004` для представления дисплея. Конструктору передается несколько параметров, описывающих настройки, которые будут использоваться для взаимодействия с расширителем GPIO. Расширитель GPIO передается в качестве параметра `controller`.
    - Цикл `while` выполняется бесконечно. Каждая итерация:
        1. Очищает экран.
        1. Устанавливает курсор в первую позицию в текущей строке.
        1. Записывает текущее время для отображения в текущей позиции курсора.
        1. Выполняет итерацию счетчика текущей строки.
        1. Переходит в спящий режим на 1000 мс.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.

    ```bash
    ./LcdTutorial
    ```

    Наблюдайте за отображением текущего времени в каждой строке на символьном ЖК-дисплее.

    > [!TIP]
    > Если дисплей светится, но текст не отображается, попробуйте настроить контрастность с помощью регулятора на обратной стороне экрана.

1. Завершите выполнение программы, нажав сочетание клавиш <kbd>CTRL+C</kbd>.

Поздравляем! Вы вывели текст на ЖК-монитор, используя расширитель GPIO I2C.

## <a name="get-the-source-code"></a>Получение исходного кода

Исходный код для этого учебника [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Использование GPIO для мигания светодиодного индикатора](../tutorials/blink-led.md)
