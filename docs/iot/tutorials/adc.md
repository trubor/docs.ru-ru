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
# <a name="read-values-from-an-analog-to-digital-converter"></a><span data-ttu-id="60081-103">Считывание значений с аналогово-цифрового преобразователя</span><span class="sxs-lookup"><span data-stu-id="60081-103">Read values from an analog-to-digital converter</span></span>

<span data-ttu-id="60081-104">Аналогово-цифровой преобразователь (ADC) — это устройство, которое может считывать аналоговое значение входного напряжения и преобразовывать его в цифровое значение.</span><span class="sxs-lookup"><span data-stu-id="60081-104">An analog-to-digital converter (ADC) is a device that can read an analog input voltage value and convert it into a digital value.</span></span> <span data-ttu-id="60081-105">ADC используются для считывания значений с терморезисторов, потенциометров и других устройств, которые изменяют сопротивление в зависимости от определенных условий.</span><span class="sxs-lookup"><span data-stu-id="60081-105">ADCs are used for reading values from thermistors, potentiometers, and other devices that change resistance based on certain conditions.</span></span>

<span data-ttu-id="60081-106">В этом разделе вы будете использовать .NET для считывания значений с аналогово-цифрового преобразователя при модуляции входного напряжения с помощью потенциометра.</span><span class="sxs-lookup"><span data-stu-id="60081-106">In this topic, you will use .NET to read values from an ADC as you modulate the input voltage with a potentiometer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="60081-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="60081-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="60081-108">Аналогово-цифровой преобразователь [MCP3008](https://www.microchip.com/wwwproducts/MCP3008)</span><span class="sxs-lookup"><span data-stu-id="60081-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) analog-to-digital converter</span></span>
- <span data-ttu-id="60081-109">3-контактный потенциометр</span><span class="sxs-lookup"><span data-stu-id="60081-109">Three-pin potentiometer</span></span>
- <span data-ttu-id="60081-110">монтажная плата;</span><span class="sxs-lookup"><span data-stu-id="60081-110">Breadboard</span></span>
- <span data-ttu-id="60081-111">оптоволоконные кабеля с разъемами на обоих концах;</span><span class="sxs-lookup"><span data-stu-id="60081-111">Jumper wires</span></span>
- <span data-ttu-id="60081-112">Коммутационная плата GPIO Raspberry Pi (необязательно/рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="60081-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="60081-113">Подготовка оборудования</span><span class="sxs-lookup"><span data-stu-id="60081-113">Prepare the hardware</span></span>

<span data-ttu-id="60081-114">Используйте компоненты оборудования для создания цепи, как показано на следующей схеме:</span><span class="sxs-lookup"><span data-stu-id="60081-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="Схема Fritzing, демонстрирующая цепь с устройством ADC MCP3008 и потенциометром" lightbox="../media/rpi-trimpot_spi.png":::

<span data-ttu-id="60081-116">Для взаимодействия MCP3008 использует последовательный интерфейс для периферийных устройств (SPI).</span><span class="sxs-lookup"><span data-stu-id="60081-116">The MCP3008 uses Serial Peripheral Interface (SPI) to communicate.</span></span> <span data-ttu-id="60081-117">Ниже перечислены подключения от MCP3008 к устройству Raspberry Pi и потенциометру.</span><span class="sxs-lookup"><span data-stu-id="60081-117">The following are the connections from the MCP3008 to the Raspberry Pi and potentiometer:</span></span>

- <span data-ttu-id="60081-118">V<sub>DD</sub> к 3,3V (показано красным цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-118">V<sub>DD</sub> to 3.3V (shown in red)</span></span>
- <span data-ttu-id="60081-119">V<sub>REF</sub> к 3,3V (показано красным цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-119">V<sub>REF</sub> to 3.3V (red)</span></span>
- <span data-ttu-id="60081-120">AGND к заземлению (показано черным цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-120">AGND to ground (black)</span></span>
- <span data-ttu-id="60081-121">CLK к SCLK (показано оранжевым цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-121">CLK to SCLK (orange)</span></span>
- <span data-ttu-id="60081-122">D<sub>OUT</sub> к MISO (показано оранжевым цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-122">D<sub>OUT</sub> to MISO (orange)</span></span>
- <span data-ttu-id="60081-123">D<sub>IN</sub> к MOSI (показано оранжевым цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-123">D<sub>IN</sub> to MOSI (orange)</span></span>
- <span data-ttu-id="60081-124">CS/SHDN к CE0 (показано зеленым цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-124">CS/SHDN to CE0 (green)</span></span>
- <span data-ttu-id="60081-125">DGND к заземлению (показано черным цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-125">DGND to ground (black)</span></span>
- <span data-ttu-id="60081-126">CH0 к переменному (среднему) контакту на потенциометре (показано желтым цветом)</span><span class="sxs-lookup"><span data-stu-id="60081-126">CH0 to variable (middle) pin on potentiometer (yellow)</span></span>

<span data-ttu-id="60081-127">Подайте напряжение 3,3 и заземление на внешние контакты на потенциометре.</span><span class="sxs-lookup"><span data-stu-id="60081-127">Supply 3.3V and ground to the outer pins on the potentiometer.</span></span> <span data-ttu-id="60081-128">Последовательность не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="60081-128">Order is unimportant.</span></span>

<span data-ttu-id="60081-129">При необходимости смотрите следующую схему контактов:</span><span class="sxs-lookup"><span data-stu-id="60081-129">Refer to the following pinout diagrams as needed:</span></span>

| <span data-ttu-id="60081-130">MCP3008</span><span class="sxs-lookup"><span data-stu-id="60081-130">MCP3008</span></span>  | <span data-ttu-id="60081-131">GPIO Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="60081-131">Raspberry Pi GPIO</span></span> |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="Схема контактов MCP3008" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Диаграмма, показывающая схему контактов верхнего контактного ряда GPIO Raspberry Pi. Изображение взято с Raspberry Pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="60081-134">[Изображение взято с Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span><span class="sxs-lookup"><span data-stu-id="60081-134">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="60081-135">Создайте приложение</span><span class="sxs-lookup"><span data-stu-id="60081-135">Create the app</span></span>

<span data-ttu-id="60081-136">Выполните следующие действия в предпочитаемой среде разработки.</span><span class="sxs-lookup"><span data-stu-id="60081-136">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="60081-137">Создайте консольное приложение .NET с помощью [.NET CLI](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="60081-137">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="60081-138">Назовите его *AdcTutorial*.</span><span class="sxs-lookup"><span data-stu-id="60081-138">Name it *AdcTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="60081-139">Замените содержимое *Program.cs* кодом из этого примера.</span><span class="sxs-lookup"><span data-stu-id="60081-139">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    <span data-ttu-id="60081-140">В приведенном выше коде:</span><span class="sxs-lookup"><span data-stu-id="60081-140">In the preceding code:</span></span>

    - <span data-ttu-id="60081-141">Для `hardwareSpiSettings` задан новый экземпляр `SpiConnectionSettings`.</span><span class="sxs-lookup"><span data-stu-id="60081-141">`hardwareSpiSettings` is set to a new instance of `SpiConnectionSettings`.</span></span> <span data-ttu-id="60081-142">Конструктор задает параметру `busId`значение 0 и параметру `chipSelectLine` — значение 0.</span><span class="sxs-lookup"><span data-stu-id="60081-142">The constructor sets the `busId` parameter to 0 and the `chipSelectLine` parameter to 0.</span></span>
    - <span data-ttu-id="60081-143">[Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `SpiDevice` путем вызова `SpiDevice.Create` и передачи `hardwareSpiSettings`.</span><span class="sxs-lookup"><span data-stu-id="60081-143">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `SpiDevice` by calling `SpiDevice.Create` and passing in `hardwareSpiSettings`.</span></span> <span data-ttu-id="60081-144">`SpiDevice` представляет шину SPI.</span><span class="sxs-lookup"><span data-stu-id="60081-144">This `SpiDevice` represents the SPI bus.</span></span> <span data-ttu-id="60081-145">Объявление `using` гарантирует, что объект удален и аппаратные ресурсы освобождены должным образом.</span><span class="sxs-lookup"><span data-stu-id="60081-145">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="60081-146">Другое объявление `using` создает экземпляр `Mcp3008` и передает `SpiDevice` конструктору.</span><span class="sxs-lookup"><span data-stu-id="60081-146">Another `using` declaration creates an instance of `Mcp3008` and passes the `SpiDevice` into the constructor.</span></span>
    - <span data-ttu-id="60081-147">Цикл `while` выполняется бесконечно.</span><span class="sxs-lookup"><span data-stu-id="60081-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="60081-148">Каждая итерация:</span><span class="sxs-lookup"><span data-stu-id="60081-148">Each iteration:</span></span>
        1. <span data-ttu-id="60081-149">Считывает значение CH0 из устройства ADC путем вызова `mcp.Read(0)`.</span><span class="sxs-lookup"><span data-stu-id="60081-149">Reads the value of CH0 on the ADC by calling `mcp.Read(0)`.</span></span>
        1. <span data-ttu-id="60081-150">Делит значение на 10,24.</span><span class="sxs-lookup"><span data-stu-id="60081-150">Divides the value by 10.24.</span></span> <span data-ttu-id="60081-151">MCP3008 — это 10-битное устройство ADC, что означает, что оно возвращает 1024 возможных значений в диапазоне от 0 до 1023.</span><span class="sxs-lookup"><span data-stu-id="60081-151">The MCP3008 is a 10-bit ADC, which means it returns 1024 possible values ranging 0-1023.</span></span> <span data-ttu-id="60081-152">Деление значения на 10,24 представляет значение в процентах.</span><span class="sxs-lookup"><span data-stu-id="60081-152">Dividing the value by 10.24 represents the value as a percentage.</span></span>
        1. <span data-ttu-id="60081-153">Округляет десятичное значение до ближайшего целого числа.</span><span class="sxs-lookup"><span data-stu-id="60081-153">Rounds the value to the nearest integer.</span></span>
        1. <span data-ttu-id="60081-154">Выводит значение на консоль в виде процента.</span><span class="sxs-lookup"><span data-stu-id="60081-154">Writes the value to the console formatted as a percentage.</span></span>
        1. <span data-ttu-id="60081-155">Переходит в спящий режим на 500 мс.</span><span class="sxs-lookup"><span data-stu-id="60081-155">Sleeps 500 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="60081-156">Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="60081-156">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./AdcTutorial
    ```

    <span data-ttu-id="60081-157">Обратите внимание на изменение выходных данных, происходящее при вращении ручки потенциометра.</span><span class="sxs-lookup"><span data-stu-id="60081-157">Observe the output as you rotate the potentiometer dial.</span></span> <span data-ttu-id="60081-158">Это происходит из-за того, что потенциометр меняет напряжение, подаваемое в CH0 на устройстве ADC.</span><span class="sxs-lookup"><span data-stu-id="60081-158">This is due to the potentiometer varying the voltage supplied to CH0 on the ADC.</span></span> <span data-ttu-id="60081-159">Для создания значения ADC сравнивает входное напряжение в CH0 с опорным напряжением, подаваемым на V<sub>REF</sub>.</span><span class="sxs-lookup"><span data-stu-id="60081-159">The ADC compares the input voltage on CH0 to the reference voltage supplied to V<sub>REF</sub> to generate a value.</span></span>

1. <span data-ttu-id="60081-160">Завершите выполнение программы, нажав сочетание клавиш <kbd>CTRL+C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="60081-160">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="60081-161">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="60081-161">Congratulations!</span></span> <span data-ttu-id="60081-162">Вы считали значения с аналогово-цифрового преобразователя с помощью SPI.</span><span class="sxs-lookup"><span data-stu-id="60081-162">You've used SPI to read values from an analog-to-digital converter.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="60081-163">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="60081-163">Get the source code</span></span>

<span data-ttu-id="60081-164">Исходный код для этого учебника [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span><span class="sxs-lookup"><span data-stu-id="60081-164">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="60081-165">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="60081-165">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60081-166">Использование GPIO для мигания светодиодного индикатора</span><span class="sxs-lookup"><span data-stu-id="60081-166">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
