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
# <a name="read-environmental-conditions-from-a-sensor"></a><span data-ttu-id="9fe47-103">Считывание с датчика условий окружающей среды</span><span class="sxs-lookup"><span data-stu-id="9fe47-103">Read environmental conditions from a sensor</span></span>

<span data-ttu-id="9fe47-104">Одним из наиболее распространенных сценариев использования устройств Интернета вещей является определение условий окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="9fe47-104">One of the most common scenarios for IoT devices is detection of environmental conditions.</span></span> <span data-ttu-id="9fe47-105">Существует множество датчиков для отслеживания температуры, влажности, атмосферного давления и многих других показаний.</span><span class="sxs-lookup"><span data-stu-id="9fe47-105">A variety of sensors are available to monitor temperature, humidity, barometric pressure, and more.</span></span>

<span data-ttu-id="9fe47-106">В этом разделе вы будете использовать .NET для считывания с датчика условий окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="9fe47-106">In this topic, you will use .NET to read environmental conditions from a sensor.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9fe47-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="9fe47-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="9fe47-108">Коммутационная плата [BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) датчика влажности, давления, температуры</span><span class="sxs-lookup"><span data-stu-id="9fe47-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) humidity/barometric pressure/temperature sensor breakout</span></span>
- <span data-ttu-id="9fe47-109">оптоволоконные кабеля с разъемами на обоих концах;</span><span class="sxs-lookup"><span data-stu-id="9fe47-109">Jumper wires</span></span>
- <span data-ttu-id="9fe47-110">Монтажная плата (необязательно)</span><span class="sxs-lookup"><span data-stu-id="9fe47-110">Breadboard (optional)</span></span>
- <span data-ttu-id="9fe47-111">Коммутационная плата GPIO Raspberry Pi (необязательно)</span><span class="sxs-lookup"><span data-stu-id="9fe47-111">Raspberry Pi GPIO breakout board (optional)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> <span data-ttu-id="9fe47-112">Существует множество производителей коммутационных плат BME280.</span><span class="sxs-lookup"><span data-stu-id="9fe47-112">There are many manufacturers of BME280 breakouts.</span></span> <span data-ttu-id="9fe47-113">Большинство конструкций похожи, и производители не видят никакой разницы в функционале.</span><span class="sxs-lookup"><span data-stu-id="9fe47-113">Most designs are similar, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="9fe47-114">В этом руководстве предпринимается попытка отразить отличия.</span><span class="sxs-lookup"><span data-stu-id="9fe47-114">This tutorial attempts to account for variations.</span></span> <span data-ttu-id="9fe47-115">Убедитесь, что коммутационная плата BME280 имеет интерфейс I2C.</span><span class="sxs-lookup"><span data-stu-id="9fe47-115">Ensure your BME280 breakout includes an Inter-Integrated Circuit (I2C) interface.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="9fe47-116">Подготовка оборудования</span><span class="sxs-lookup"><span data-stu-id="9fe47-116">Prepare the hardware</span></span>

<span data-ttu-id="9fe47-117">Используйте компоненты оборудования для создания цепи, как показано на следующей схеме:</span><span class="sxs-lookup"><span data-stu-id="9fe47-117">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Схема Fritzing, демонстрирующая подключение от устройства Raspberry Pi к коммутационной плате BME280" lightbox="../media/rpi-bmp280_i2c.png":::

<span data-ttu-id="9fe47-119">Ниже приведен перечень подключений от устройства Raspberry Pi к плате BME280.</span><span class="sxs-lookup"><span data-stu-id="9fe47-119">The following are the connections from the Raspberry Pi to the BME280 breakout:</span></span>

- <span data-ttu-id="9fe47-120">3,3V к VIN *или* 3V3 (показано красным цветом)</span><span class="sxs-lookup"><span data-stu-id="9fe47-120">3.3V to VIN *OR* 3V3 (shown in red)</span></span>
- <span data-ttu-id="9fe47-121">GND (заземление) к GND (черный)</span><span class="sxs-lookup"><span data-stu-id="9fe47-121">Ground to GND (black)</span></span>
- <span data-ttu-id="9fe47-122">SDA (GPIO 2) к SDI *или* SDA (синий)</span><span class="sxs-lookup"><span data-stu-id="9fe47-122">SDA (GPIO 2) to SDI *OR* SDA (blue)</span></span>
- <span data-ttu-id="9fe47-123">SCL (GPIO 3) к SCK *или* SCL (оранжевый)</span><span class="sxs-lookup"><span data-stu-id="9fe47-123">SCL (GPIO 3) to SCK *OR* SCL (orange)</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="9fe47-124">Создайте приложение</span><span class="sxs-lookup"><span data-stu-id="9fe47-124">Create the app</span></span>

<span data-ttu-id="9fe47-125">Выполните следующие действия в предпочитаемой среде разработки.</span><span class="sxs-lookup"><span data-stu-id="9fe47-125">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="9fe47-126">Создайте консольное приложение .NET с помощью [.NET CLI](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9fe47-126">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="9fe47-127">Назовите его *SensorTutorial*.</span><span class="sxs-lookup"><span data-stu-id="9fe47-127">Name it *SensorTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="9fe47-128">Замените содержимое *Program.cs* кодом из этого примера.</span><span class="sxs-lookup"><span data-stu-id="9fe47-128">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    <span data-ttu-id="9fe47-129">В приведенном выше коде:</span><span class="sxs-lookup"><span data-stu-id="9fe47-129">In the preceding code:</span></span>

    - <span data-ttu-id="9fe47-130">Для `i2cSettings` задан новый экземпляр `I2cConnectionSettings`.</span><span class="sxs-lookup"><span data-stu-id="9fe47-130">`i2cSettings` is set to a new instance of `I2cConnectionSettings`.</span></span> <span data-ttu-id="9fe47-131">Конструктор задает параметру `busId` значение 1, а параметру `deviceAddress` — значение `Bme280.DefaultI2cAddress`.</span><span class="sxs-lookup"><span data-stu-id="9fe47-131">The constructor sets the `busId` parameter to 1 and the `deviceAddress` parameter to `Bme280.DefaultI2cAddress`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="9fe47-132">Некоторые производители коммутационных плат BME280 используют значение дополнительного адреса.</span><span class="sxs-lookup"><span data-stu-id="9fe47-132">Some BME280 breakout manufacturers use the secondary address value.</span></span> <span data-ttu-id="9fe47-133">Для этих устройств используйте `Bme280.SecondaryI2cAddress`.</span><span class="sxs-lookup"><span data-stu-id="9fe47-133">For those devices, use `Bme280.SecondaryI2cAddress`.</span></span>

    - <span data-ttu-id="9fe47-134">[Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `I2cDevice` путем вызова `I2cDevice.Create` и передачи `i2cSettings`.</span><span class="sxs-lookup"><span data-stu-id="9fe47-134">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in `i2cSettings`.</span></span> <span data-ttu-id="9fe47-135">Класс `I2cDevice` представляет шину I2C.</span><span class="sxs-lookup"><span data-stu-id="9fe47-135">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="9fe47-136">Объявление `using` гарантирует, что объект удален и аппаратные ресурсы освобождены должным образом.</span><span class="sxs-lookup"><span data-stu-id="9fe47-136">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="9fe47-137">Другое объявление `using` создает экземпляр `Bme280` для представления датчика.</span><span class="sxs-lookup"><span data-stu-id="9fe47-137">Another `using` declaration creates an instance of `Bme280` to represent the sensor.</span></span> <span data-ttu-id="9fe47-138">`I2cDevice` передается конструктору.</span><span class="sxs-lookup"><span data-stu-id="9fe47-138">The `I2cDevice` is passed in the constructor.</span></span>
    - <span data-ttu-id="9fe47-139">Время, необходимое микросхеме для выполнения измерений с текущими параметрами микросхемы (заданными по умолчанию), определяется путем вызова `GetMeasurementDuration`.</span><span class="sxs-lookup"><span data-stu-id="9fe47-139">The time required for the chip to take measurements with the chip's current (default) settings is retrieved by calling `GetMeasurementDuration`.</span></span>
    - <span data-ttu-id="9fe47-140">Цикл `while` выполняется бесконечно.</span><span class="sxs-lookup"><span data-stu-id="9fe47-140">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="9fe47-141">Каждая итерация:</span><span class="sxs-lookup"><span data-stu-id="9fe47-141">Each iteration:</span></span>
        1. <span data-ttu-id="9fe47-142">Очищает окно консоли.</span><span class="sxs-lookup"><span data-stu-id="9fe47-142">Clears the console.</span></span>
        1. <span data-ttu-id="9fe47-143">Задает режим питания `Bmx280PowerMode.Forced`.</span><span class="sxs-lookup"><span data-stu-id="9fe47-143">Sets the power mode to `Bmx280PowerMode.Forced`.</span></span> <span data-ttu-id="9fe47-144">В этом случае микросхема проводит одно измерение, сохраняет результаты, а затем переходит в спящий режим.</span><span class="sxs-lookup"><span data-stu-id="9fe47-144">This forces the chip to perform one measurement, store the results, and then sleep.</span></span>
        1. <span data-ttu-id="9fe47-145">Считывает значения температуры, давления, влажности и высоты над уровнем моря.</span><span class="sxs-lookup"><span data-stu-id="9fe47-145">Reads the values for temperature, pressure, humidity, and altitude.</span></span>

            > [!NOTE]
            > <span data-ttu-id="9fe47-146">Высота над уровнем моря вычисляется привязкой устройства.</span><span class="sxs-lookup"><span data-stu-id="9fe47-146">Altitude is calculated by the device binding.</span></span> <span data-ttu-id="9fe47-147">Для получения оценки эта перегрузка метода `TryReadAltitude` использует среднее значение давления на уровне моря.</span><span class="sxs-lookup"><span data-stu-id="9fe47-147">This overload of `TryReadAltitude` uses mean sea level pressure to generate an estimate.</span></span>

        1. <span data-ttu-id="9fe47-148">Записывает текущие условия среды в консоль.</span><span class="sxs-lookup"><span data-stu-id="9fe47-148">Writes the current environmental conditions to the console.</span></span>
        1. <span data-ttu-id="9fe47-149">Переходит в спящий режим на 1000 мс.</span><span class="sxs-lookup"><span data-stu-id="9fe47-149">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="9fe47-150">Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="9fe47-150">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./SensorTutorial
    ```

    <span data-ttu-id="9fe47-151">Наблюдайте за выходными данными датчика в консоли.</span><span class="sxs-lookup"><span data-stu-id="9fe47-151">Observe the sensor output in the console.</span></span>

1. <span data-ttu-id="9fe47-152">Завершите выполнение программы, нажав сочетание клавиш <kbd>CTRL+C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9fe47-152">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="9fe47-153">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="9fe47-153">Congratulations!</span></span> <span data-ttu-id="9fe47-154">Вы использовали I2C для считывания с датчика показаний температуры, влажности, давления.</span><span class="sxs-lookup"><span data-stu-id="9fe47-154">You've used I2C to read values from a temperature/humidity/barometric pressure sensor!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="9fe47-155">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="9fe47-155">Get the source code</span></span>

<span data-ttu-id="9fe47-156">Исходный код для этого учебника [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial).</span><span class="sxs-lookup"><span data-stu-id="9fe47-156">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9fe47-157">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="9fe47-157">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9fe47-158">Отображение текста на ЖК-дисплее</span><span class="sxs-lookup"><span data-stu-id="9fe47-158">Learn how to display text on an LCD</span></span>](../tutorials/lcd-display.md)
