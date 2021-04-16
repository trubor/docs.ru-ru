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
# <a name="blink-an-led"></a><span data-ttu-id="affb1-103">Сигнал светодиодного индикатора</span><span class="sxs-lookup"><span data-stu-id="affb1-103">Blink an LED</span></span>

<span data-ttu-id="affb1-104">Контакты GPIO можно контролировать по отдельности.</span><span class="sxs-lookup"><span data-stu-id="affb1-104">General-purpose I/O (GPIO) pins can be controlled individually.</span></span> <span data-ttu-id="affb1-105">Это удобно для управления светодиодными индикаторами, ретрансляторами и другими устройствами с отслеживанием состояния.</span><span class="sxs-lookup"><span data-stu-id="affb1-105">This is useful for controlling LEDs, relays, and other stateful devices.</span></span> <span data-ttu-id="affb1-106">В этом разделе вы будете использовать .NET и контакты GPIO Raspberry Pi для подключения питания к светодиодному индикатору и активации повторяющегося мигания.</span><span class="sxs-lookup"><span data-stu-id="affb1-106">In this topic, you will use .NET and your Raspberry Pi's GPIO pins to power an LED and blink it repeatedly.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="affb1-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="affb1-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="affb1-108">Светодиодный индикатор 5 мм</span><span class="sxs-lookup"><span data-stu-id="affb1-108">5 mm LED</span></span>
- <span data-ttu-id="affb1-109">Резистор 330 Ом</span><span class="sxs-lookup"><span data-stu-id="affb1-109">330 Ω resistor</span></span>
- <span data-ttu-id="affb1-110">монтажная плата;</span><span class="sxs-lookup"><span data-stu-id="affb1-110">Breadboard</span></span>
- <span data-ttu-id="affb1-111">оптоволоконные кабеля с разъемами на обоих концах;</span><span class="sxs-lookup"><span data-stu-id="affb1-111">Jumper wires</span></span>
- <span data-ttu-id="affb1-112">Коммутационная плата GPIO Raspberry Pi (необязательно/рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="affb1-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="affb1-113">Подготовка оборудования</span><span class="sxs-lookup"><span data-stu-id="affb1-113">Prepare the hardware</span></span>

<span data-ttu-id="affb1-114">Используйте компоненты оборудования для создания цепи, как показано на следующей схеме:</span><span class="sxs-lookup"><span data-stu-id="affb1-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="Схема Fritzing, демонстрирующая цепь со светодиодным индикатором и резистором" lightbox="../media/rpi-led_bb.png":::

<span data-ttu-id="affb1-116">На приведенном выше рисунке изображены следующие подключения:</span><span class="sxs-lookup"><span data-stu-id="affb1-116">The image above depicts the following connections:</span></span>

- <span data-ttu-id="affb1-117">GPIO 18 к LED (более длинный, положительный вывод)</span><span class="sxs-lookup"><span data-stu-id="affb1-117">GPIO 18 to LED anode (longer, positive lead)</span></span>
- <span data-ttu-id="affb1-118">Катод LED (более короткий, отрицательный вывод) к резистору 330 ОМ (любой конец)</span><span class="sxs-lookup"><span data-stu-id="affb1-118">LED cathode (shorter, negative lead) to 330 Ω resistor (either end)</span></span>
- <span data-ttu-id="affb1-119">Резистор 330 ОМ (другой конец) к заземлению</span><span class="sxs-lookup"><span data-stu-id="affb1-119">330 Ω resistor (other end) to ground</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="affb1-120">Создайте приложение</span><span class="sxs-lookup"><span data-stu-id="affb1-120">Create the app</span></span>

<span data-ttu-id="affb1-121">Выполните следующие действия в предпочитаемой среде разработки.</span><span class="sxs-lookup"><span data-stu-id="affb1-121">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="affb1-122">Создайте консольное приложение .NET с помощью [.NET CLI](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="affb1-122">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="affb1-123">Назовите его *BlinkTutorial*.</span><span class="sxs-lookup"><span data-stu-id="affb1-123">Name it *BlinkTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="affb1-124">Замените содержимое *Program.cs* кодом из этого примера.</span><span class="sxs-lookup"><span data-stu-id="affb1-124">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    <span data-ttu-id="affb1-125">В приведенном выше коде:</span><span class="sxs-lookup"><span data-stu-id="affb1-125">In the preceding code:</span></span>

    - <span data-ttu-id="affb1-126">[Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `GpioController`.</span><span class="sxs-lookup"><span data-stu-id="affb1-126">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `GpioController`.</span></span> <span data-ttu-id="affb1-127">Объявление `using` гарантирует, что объект удален и аппаратные ресурсы освобождены должным образом.</span><span class="sxs-lookup"><span data-stu-id="affb1-127">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="affb1-128">Контакт GPIO 18 открыт для вывода.</span><span class="sxs-lookup"><span data-stu-id="affb1-128">GPIO pin 18 is opened for output</span></span>
    - <span data-ttu-id="affb1-129">Цикл `while` выполняется бесконечно.</span><span class="sxs-lookup"><span data-stu-id="affb1-129">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="affb1-130">Каждая итерация:</span><span class="sxs-lookup"><span data-stu-id="affb1-130">Each iteration:</span></span>
        1. <span data-ttu-id="affb1-131">Записывает значение в контакт GPIO 18.</span><span class="sxs-lookup"><span data-stu-id="affb1-131">Writes a value to GPIO pin 18.</span></span> <span data-ttu-id="affb1-132">Если `ledOn` имеет значение true, то записывает `PinValue.High` (вкл.).</span><span class="sxs-lookup"><span data-stu-id="affb1-132">If `ledOn` is true, it writes `PinValue.High` (on).</span></span> <span data-ttu-id="affb1-133">В противном случае записывается `PinValue.Low`.</span><span class="sxs-lookup"><span data-stu-id="affb1-133">Otherwise, it writes `PinValue.Low`.</span></span>
        1. <span data-ttu-id="affb1-134">Переходит в спящий режим на 1000 мс.</span><span class="sxs-lookup"><span data-stu-id="affb1-134">Sleeps 1000 ms.</span></span>
        1. <span data-ttu-id="affb1-135">Переключает значение `ledOn`.</span><span class="sxs-lookup"><span data-stu-id="affb1-135">Toggles the value of `ledOn`.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="affb1-136">Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="affb1-136">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./BlinkTutorial
    ```

    <span data-ttu-id="affb1-137">Светодиодный индикатор мигает каждую секунду.</span><span class="sxs-lookup"><span data-stu-id="affb1-137">The LED blinks off and on every second.</span></span>

1. <span data-ttu-id="affb1-138">Завершите выполнение программы, нажав сочетание клавиш <kbd>CTRL+C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="affb1-138">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="affb1-139">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="affb1-139">Congratulations!</span></span> <span data-ttu-id="affb1-140">Вы использовали GPIO для включения и отключения сигнала (мигания) светодиодного индикатора.</span><span class="sxs-lookup"><span data-stu-id="affb1-140">You've used GPIO to blink an LED.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="affb1-141">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="affb1-141">Get the source code</span></span>

<span data-ttu-id="affb1-142">Исходный код для этого учебника [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial).</span><span class="sxs-lookup"><span data-stu-id="affb1-142">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="affb1-143">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="affb1-143">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="affb1-144">Считывание с датчика условий окружающей среды</span><span class="sxs-lookup"><span data-stu-id="affb1-144">Learn how to read environmental conditions from a sensor</span></span>](../tutorials/temp-sensor.md)
