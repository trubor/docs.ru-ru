---
title: Считывание значений с аналогово-цифрового преобразователя
description: Сведения о считывании значений переменного напряжения с аналогово-цифрового преобразователя.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 509616e3423fbb83b74bfbb8ecec1a7df49f0a20
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259748"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="read-values-from-an-analog-to-digital-converter"></a>Считывание значений с аналогово-цифрового преобразователя

Аналогово-цифровой преобразователь (ADC) — это устройство, которое может считывать аналоговое значение входного напряжения и преобразовывать его в цифровое значение. ADC используются для считывания значений с терморезисторов, потенциометров и других устройств, которые изменяют сопротивление в зависимости от определенных условий.

В этом разделе вы будете использовать .NET для считывания значений с аналогово-цифрового преобразователя при модуляции входного напряжения с помощью потенциометра.

## <a name="prerequisites"></a>Предварительные требования

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- Аналогово-цифровой преобразователь [MCP3008](https://www.microchip.com/wwwproducts/MCP3008)
- 3-контактный потенциометр
- монтажная плата;
- оптоволоконные кабеля с разъемами на обоих концах;
- Коммутационная плата GPIO Raspberry Pi (необязательно/рекомендуется)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a>Подготовка оборудования

Используйте компоненты оборудования для создания цепи, как показано на следующей схеме:

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="Схема Fritzing, демонстрирующая цепь с устройством ADC MCP3008 и потенциометром" lightbox="../media/rpi-trimpot_spi.png":::

Для взаимодействия MCP3008 использует последовательный интерфейс для периферийных устройств (SPI). Ниже перечислены подключения от MCP3008 к устройству Raspberry Pi и потенциометру.

- V<sub>DD</sub> к 3,3V (показано красным цветом)
- V<sub>REF</sub> к 3,3V (показано красным цветом)
- AGND к заземлению (показано черным цветом)
- CLK к SCLK (показано оранжевым цветом)
- D<sub>OUT</sub> к MISO (показано оранжевым цветом)
- D<sub>IN</sub> к MOSI (показано оранжевым цветом)
- CS/SHDN к CE0 (показано зеленым цветом)
- DGND к заземлению (показано черным цветом)
- CH0 к переменному (среднему) контакту на потенциометре (показано желтым цветом)

Подайте напряжение 3,3 и заземление на внешние контакты на потенциометре. Последовательность не имеет значения.

При необходимости смотрите следующую схему контактов:

| MCP3008  | GPIO Raspberry Pi |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="Схема контактов MCP3008" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Диаграмма, показывающая схему контактов верхнего контактного ряда GPIO Raspberry Pi. Изображение взято с Raspberry Pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br />[Изображение взято с Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Создайте приложение

Выполните следующие действия в предпочитаемой среде разработки.

1. Создайте консольное приложение .NET с помощью [.NET CLI](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md). Назовите его *AdcTutorial*.

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. Замените содержимое *Program.cs* кодом из этого примера.

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    В приведенном выше коде:

    - Для `hardwareSpiSettings` задан новый экземпляр `SpiConnectionSettings`. Конструктор задает параметру `busId`значение 0 и параметру `chipSelectLine` — значение 0.
    - [Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `SpiDevice` путем вызова `SpiDevice.Create` и передачи `hardwareSpiSettings`. `SpiDevice` представляет шину SPI. Объявление `using` гарантирует, что объект удален и аппаратные ресурсы освобождены должным образом.
    - Другое объявление `using` создает экземпляр `Mcp3008` и передает `SpiDevice` конструктору.
    - Цикл `while` выполняется бесконечно. Каждая итерация:
        1. Считывает значение CH0 из устройства ADC путем вызова `mcp.Read(0)`.
        1. Делит значение на 10,24. MCP3008 — это 10-битное устройство ADC, что означает, что оно возвращает 1024 возможных значений в диапазоне от 0 до 1023. Деление значения на 10,24 представляет значение в процентах.
        1. Округляет десятичное значение до ближайшего целого числа.
        1. Выводит значение на консоль в виде процента.
        1. Переходит в спящий режим на 500 мс.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.

    ```bash
    ./AdcTutorial
    ```

    Обратите внимание на изменение выходных данных, происходящее при вращении ручки потенциометра. Это происходит из-за того, что потенциометр меняет напряжение, подаваемое в CH0 на устройстве ADC. Для создания значения ADC сравнивает входное напряжение в CH0 с опорным напряжением, подаваемым на V<sub>REF</sub>.

1. Завершите выполнение программы, нажав сочетание клавиш <kbd>CTRL+C</kbd>.

Поздравляем! Вы считали значения с аналогово-цифрового преобразователя с помощью SPI.

## <a name="get-the-source-code"></a>Получение исходного кода

Исходный код для этого учебника [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Использование GPIO для мигания светодиодного индикатора](../tutorials/blink-led.md)
