---
title: Считывание значений с аналогово-цифрового преобразователя
description: Узнайте, как считывать значения переменного напряжения с помощью аналогового в цифровом преобразователе.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 7cf25f181997ed66639842727be57e7824ef5466
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739991"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="read-values-from-an-analog-to-digital-converter"></a><span data-ttu-id="cc233-103">Считывание значений с аналогово-цифрового преобразователя</span><span class="sxs-lookup"><span data-stu-id="cc233-103">Read values from an analog-to-digital converter</span></span>

<span data-ttu-id="cc233-104">Аналогово-цифровой преобразователь (ADC) — это устройство, которое может считывать значение аналогового входного напряжения и преобразовывать его в цифровое значение.</span><span class="sxs-lookup"><span data-stu-id="cc233-104">An analog-to-digital converter (ADC) is a device that can read an analog input voltage value and convert it into a digital value.</span></span> <span data-ttu-id="cc233-105">ADCs используется для считывания значений из сермисторс, потентиометерс и других устройств, которые меняют сопротивления на основе определенных условий.</span><span class="sxs-lookup"><span data-stu-id="cc233-105">ADCs are used for reading values from thermistors, potentiometers, and other devices that change resistance based on certain conditions.</span></span>

<span data-ttu-id="cc233-106">В этом разделе вы будете использовать .NET для чтения значений из ADC при модуляции входного напряжения с помощью потентиометер.</span><span class="sxs-lookup"><span data-stu-id="cc233-106">In this topic, you will use .NET to read values from an ADC as you modulate the input voltage with a potentiometer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc233-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="cc233-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="cc233-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> аналоговый для цифрового преобразователя</span><span class="sxs-lookup"><span data-stu-id="cc233-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> analog-to-digital converter</span></span>
- <span data-ttu-id="cc233-109">3-контактный потентиометер</span><span class="sxs-lookup"><span data-stu-id="cc233-109">Three-pin potentiometer</span></span>
- <span data-ttu-id="cc233-110">монтажная плата;</span><span class="sxs-lookup"><span data-stu-id="cc233-110">Breadboard</span></span>
- <span data-ttu-id="cc233-111">оптоволоконные кабеля с разъемами на обоих концах;</span><span class="sxs-lookup"><span data-stu-id="cc233-111">Jumper wires</span></span>
- <span data-ttu-id="cc233-112">Raspberry Pi GPIO (необязательно/рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="cc233-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="cc233-113">Подготовка оборудования</span><span class="sxs-lookup"><span data-stu-id="cc233-113">Prepare the hardware</span></span>

<span data-ttu-id="cc233-114">Используйте аппаратные компоненты для создания канала, как показано на следующей схеме:</span><span class="sxs-lookup"><span data-stu-id="cc233-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="Схема Фритзинг, показывающая цепь с MCP3008 ADC и потентиометер" lightbox="../media/rpi-trimpot_spi.png":::

<span data-ttu-id="cc233-116">MCP3008 использует для взаимодействия интерфейс Serial периферийные устройства (SPI).</span><span class="sxs-lookup"><span data-stu-id="cc233-116">The MCP3008 uses Serial Peripheral Interface (SPI) to communicate.</span></span> <span data-ttu-id="cc233-117">Ниже приведены подключения из MCP3008 к Raspberry Pi и потентиометер:</span><span class="sxs-lookup"><span data-stu-id="cc233-117">The following are the connections from the MCP3008 to the Raspberry Pi and potentiometer:</span></span>

- <span data-ttu-id="cc233-118">V<sub>дд</sub> в 3,3 в (отображается красным цветом)</span><span class="sxs-lookup"><span data-stu-id="cc233-118">V<sub>DD</sub> to 3.3V (shown in red)</span></span>
- <span data-ttu-id="cc233-119">V<sub>ссылка</sub> на 3,3 в (красный)</span><span class="sxs-lookup"><span data-stu-id="cc233-119">V<sub>REF</sub> to 3.3V (red)</span></span>
- <span data-ttu-id="cc233-120">АГНД на землю (черный)</span><span class="sxs-lookup"><span data-stu-id="cc233-120">AGND to ground (black)</span></span>
- <span data-ttu-id="cc233-121">КЛК СКЛК (оранжевый)</span><span class="sxs-lookup"><span data-stu-id="cc233-121">CLK to SCLK (orange)</span></span>
- <span data-ttu-id="cc233-122">Г<sub>в</sub> мисо (оранжевый)</span><span class="sxs-lookup"><span data-stu-id="cc233-122">D<sub>OUT</sub> to MISO (orange)</span></span>
- <span data-ttu-id="cc233-123">D<sub>в</sub> Моси (оранжевый)</span><span class="sxs-lookup"><span data-stu-id="cc233-123">D<sub>IN</sub> to MOSI (orange)</span></span>
- <span data-ttu-id="cc233-124">CS/SHDN CE0 (зеленый)</span><span class="sxs-lookup"><span data-stu-id="cc233-124">CS/SHDN to CE0 (green)</span></span>
- <span data-ttu-id="cc233-125">ДГНД на землю (черный)</span><span class="sxs-lookup"><span data-stu-id="cc233-125">DGND to ground (black)</span></span>
- <span data-ttu-id="cc233-126">CH0 в переменную (средний) ПИН-код на потентиометер (желтый)</span><span class="sxs-lookup"><span data-stu-id="cc233-126">CH0 to variable (middle) pin on potentiometer (yellow)</span></span>

<span data-ttu-id="cc233-127">Предоставьте напряжение 3,3 в и заземление на внешних контактах на потентиометер.</span><span class="sxs-lookup"><span data-stu-id="cc233-127">Supply 3.3V and ground to the outer pins on the potentiometer.</span></span> <span data-ttu-id="cc233-128">Порядок не важен.</span><span class="sxs-lookup"><span data-stu-id="cc233-128">Order is unimportant.</span></span>

<span data-ttu-id="cc233-129">При необходимости ознакомьтесь со следующими схемами контактов:</span><span class="sxs-lookup"><span data-stu-id="cc233-129">Refer to the following pinout diagrams as needed:</span></span>

| <span data-ttu-id="cc233-130">MCP3008</span><span class="sxs-lookup"><span data-stu-id="cc233-130">MCP3008</span></span>  | <span data-ttu-id="cc233-131">Raspberry Pi GPIO</span><span class="sxs-lookup"><span data-stu-id="cc233-131">Raspberry Pi GPIO</span></span> |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="Схема, показывающая схему контактов MCP3008" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Схема, показывающая схему контактов заголовка Raspberry Pi GPIO. Образ с Raspberry Pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="cc233-134">[Образ с Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span><span class="sxs-lookup"><span data-stu-id="cc233-134">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="cc233-135">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="cc233-135">Create the app</span></span>

<span data-ttu-id="cc233-136">Выполните следующие действия в предпочитаемой среде разработки:</span><span class="sxs-lookup"><span data-stu-id="cc233-136">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="cc233-137">Создайте новое консольное приложение .NET с помощью [интерфейса командной строки .NET](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="cc233-137">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="cc233-138">Назовите его *адктуториал*.</span><span class="sxs-lookup"><span data-stu-id="cc233-138">Name it *AdcTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="cc233-139">Замените содержимое *Program.cs* кодом из этого примера.</span><span class="sxs-lookup"><span data-stu-id="cc233-139">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    <span data-ttu-id="cc233-140">В приведенном выше коде:</span><span class="sxs-lookup"><span data-stu-id="cc233-140">In the preceding code:</span></span>

    - <span data-ttu-id="cc233-141">`hardwareSpiSettings` параметру присваивается новый экземпляр `SpiConnectionSettings` .</span><span class="sxs-lookup"><span data-stu-id="cc233-141">`hardwareSpiSettings` is set to a new instance of `SpiConnectionSettings`.</span></span> <span data-ttu-id="cc233-142">Конструктор задает `busId` для параметра значение 0, а параметр — значение `chipSelectLine` 0.</span><span class="sxs-lookup"><span data-stu-id="cc233-142">The constructor sets the `busId` parameter to 0 and the `chipSelectLine` parameter to 0.</span></span>
    - <span data-ttu-id="cc233-143">[Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `SpiDevice` путем вызова `SpiDevice.Create` и передачи `hardwareSpiSettings` .</span><span class="sxs-lookup"><span data-stu-id="cc233-143">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `SpiDevice` by calling `SpiDevice.Create` and passing in `hardwareSpiSettings`.</span></span> <span data-ttu-id="cc233-144">`SpiDevice`Представляет собой ШИНУ SPI.</span><span class="sxs-lookup"><span data-stu-id="cc233-144">This `SpiDevice` represents the SPI bus.</span></span> <span data-ttu-id="cc233-145">`using`Объявление гарантирует, что объект удален и аппаратные ресурсы освобождаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="cc233-145">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="cc233-146">Другое `using` объявление создает экземпляр `Mcp3008` и передает его в `SpiDevice` конструктор.</span><span class="sxs-lookup"><span data-stu-id="cc233-146">Another `using` declaration creates an instance of `Mcp3008` and passes the `SpiDevice` into the constructor.</span></span>
    - <span data-ttu-id="cc233-147">`while`Цикл выполняется бессрочно.</span><span class="sxs-lookup"><span data-stu-id="cc233-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="cc233-148">Каждая итерация:</span><span class="sxs-lookup"><span data-stu-id="cc233-148">Each iteration:</span></span>
        1. <span data-ttu-id="cc233-149">Считывает значение CH0 в соединителе ADC путем вызова `mcp.Read(0)` .</span><span class="sxs-lookup"><span data-stu-id="cc233-149">Reads the value of CH0 on the ADC by calling `mcp.Read(0)`.</span></span>
        1. <span data-ttu-id="cc233-150">Делит значение на 10,24.</span><span class="sxs-lookup"><span data-stu-id="cc233-150">Divides the value by 10.24.</span></span> <span data-ttu-id="cc233-151">MCP3008 — это 10-разрядное средство ADC, которое означает, что он возвращает 1024 возможных значений в диапазоне от 0-1023.</span><span class="sxs-lookup"><span data-stu-id="cc233-151">The MCP3008 is a 10-bit ADC, which means it returns 1024 possible values ranging 0-1023.</span></span> <span data-ttu-id="cc233-152">Деление значения на 10,24 представляет значение в процентах.</span><span class="sxs-lookup"><span data-stu-id="cc233-152">Dividing the value by 10.24 represents the value as a percentage.</span></span>
        1. <span data-ttu-id="cc233-153">Округляет значение до ближайшего целого.</span><span class="sxs-lookup"><span data-stu-id="cc233-153">Rounds the value to the nearest integer.</span></span>
        1. <span data-ttu-id="cc233-154">Записывает значение на консоль в формате процента.</span><span class="sxs-lookup"><span data-stu-id="cc233-154">Writes the value to the console formatted as a percentage.</span></span>
        1. <span data-ttu-id="cc233-155">Спящий режим 500 мс.</span><span class="sxs-lookup"><span data-stu-id="cc233-155">Sleeps 500 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="cc233-156">Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="cc233-156">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./AdcTutorial
    ```

    <span data-ttu-id="cc233-157">Обратите внимание на выходные данные при вращении потентиометер набора.</span><span class="sxs-lookup"><span data-stu-id="cc233-157">Observe the output as you rotate the potentiometer dial.</span></span> <span data-ttu-id="cc233-158">Это происходит из-за того, что потентиометер напряжение, передаваемое CH0 в ADC.</span><span class="sxs-lookup"><span data-stu-id="cc233-158">This is due to the potentiometer varying the voltage supplied to CH0 on the ADC.</span></span> <span data-ttu-id="cc233-159">ADC сравнивает входное напряжение в CH0 со ссылочным напряжением, передаваемым на V<sub>ref</sub> для создания значения.</span><span class="sxs-lookup"><span data-stu-id="cc233-159">The ADC compares the input voltage on CH0 to the reference voltage supplied to V<sub>REF</sub> to generate a value.</span></span>

1. <span data-ttu-id="cc233-160">Завершите программу, нажав клавиши <kbd>CTRL + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="cc233-160">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="cc233-161">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="cc233-161">Congratulations!</span></span> <span data-ttu-id="cc233-162">Вы использовали SPI для считывания значений из аналогового в цифровом преобразователе.</span><span class="sxs-lookup"><span data-stu-id="cc233-162">You've used SPI to read values from an analog-to-digital converter.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="cc233-163">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="cc233-163">Get the source code</span></span>

<span data-ttu-id="cc233-164">Источник этого руководства [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="cc233-164">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cc233-165">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="cc233-165">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc233-166">Научитесь использовать общего назначения ввода-вывода для мигания индикатора</span><span class="sxs-lookup"><span data-stu-id="cc233-166">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
