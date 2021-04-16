---
title: Считывание с датчика условий окружающей среды
description: Сведения о считывания показаний температуры, атмосферного давления и влажности с помощью библиотек Интернета вещей .NET.
author: camsoper
ms.author: casoper
ms.date: 11/14/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: bc5c2b9f0876603c152da859547c58b83826969c
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259841"
---
# <a name="read-environmental-conditions-from-a-sensor"></a>Считывание с датчика условий окружающей среды

Одним из наиболее распространенных сценариев использования устройств Интернета вещей является определение условий окружающей среды. Существует множество датчиков для отслеживания температуры, влажности, атмосферного давления и многих других показаний.

В этом разделе вы будете использовать .NET для считывания с датчика условий окружающей среды.

## <a name="prerequisites"></a>Предварительные требования

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- Коммутационная плата [BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) датчика влажности, давления, температуры
- оптоволоконные кабеля с разъемами на обоих концах;
- Монтажная плата (необязательно)
- Коммутационная плата GPIO Raspberry Pi (необязательно)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> Существует множество производителей коммутационных плат BME280. Большинство конструкций похожи, и производители не видят никакой разницы в функционале. В этом руководстве предпринимается попытка отразить отличия. Убедитесь, что коммутационная плата BME280 имеет интерфейс I2C.

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>Подготовка оборудования

Используйте компоненты оборудования для создания цепи, как показано на следующей схеме:

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Схема Fritzing, демонстрирующая подключение от устройства Raspberry Pi к коммутационной плате BME280" lightbox="../media/rpi-bmp280_i2c.png":::

Ниже приведен перечень подключений от устройства Raspberry Pi к плате BME280.

- 3,3V к VIN *или* 3V3 (показано красным цветом)
- GND (заземление) к GND (черный)
- SDA (GPIO 2) к SDI *или* SDA (синий)
- SCL (GPIO 3) к SCK *или* SCL (оранжевый)

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Создайте приложение

Выполните следующие действия в предпочитаемой среде разработки.

1. Создайте консольное приложение .NET с помощью [.NET CLI](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md). Назовите его *SensorTutorial*.

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. Замените содержимое *Program.cs* кодом из этого примера.

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    В приведенном выше коде:

    - Для `i2cSettings` задан новый экземпляр `I2cConnectionSettings`. Конструктор задает параметру `busId` значение 1, а параметру `deviceAddress` — значение `Bme280.DefaultI2cAddress`.

        > [!IMPORTANT]
        > Некоторые производители коммутационных плат BME280 используют значение дополнительного адреса. Для этих устройств используйте `Bme280.SecondaryI2cAddress`.

    - [Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `I2cDevice` путем вызова `I2cDevice.Create` и передачи `i2cSettings`. Класс `I2cDevice` представляет шину I2C. Объявление `using` гарантирует, что объект удален и аппаратные ресурсы освобождены должным образом.
    - Другое объявление `using` создает экземпляр `Bme280` для представления датчика. `I2cDevice` передается конструктору.
    - Время, необходимое микросхеме для выполнения измерений с текущими параметрами микросхемы (заданными по умолчанию), определяется путем вызова `GetMeasurementDuration`.
    - Цикл `while` выполняется бесконечно. Каждая итерация:
        1. Очищает окно консоли.
        1. Задает режим питания `Bmx280PowerMode.Forced`. В этом случае микросхема проводит одно измерение, сохраняет результаты, а затем переходит в спящий режим.
        1. Считывает значения температуры, давления, влажности и высоты над уровнем моря.

            > [!NOTE]
            > Высота над уровнем моря вычисляется привязкой устройства. Для получения оценки эта перегрузка метода `TryReadAltitude` использует среднее значение давления на уровне моря.

        1. Записывает текущие условия среды в консоль.
        1. Переходит в спящий режим на 1000 мс.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.

    ```bash
    ./SensorTutorial
    ```

    Наблюдайте за выходными данными датчика в консоли.

1. Завершите выполнение программы, нажав сочетание клавиш <kbd>CTRL+C</kbd>.

Поздравляем! Вы использовали I2C для считывания с датчика показаний температуры, влажности, давления.

## <a name="get-the-source-code"></a>Получение исходного кода

Исходный код для этого учебника [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Отображение текста на ЖК-дисплее](../tutorials/lcd-display.md)
