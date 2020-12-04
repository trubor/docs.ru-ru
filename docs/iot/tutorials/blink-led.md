---
title: Сигнал светодиодного индикатора
description: Сведения о том, как мигающий светодиодный индикатор с помощью библиотек Интернета вещей .NET.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 07a050c0655f9cae3d7f2b924c0dd07ac1c6c0b9
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594149"
---
# <a name="blink-an-led"></a><span data-ttu-id="416c0-103">Сигнал светодиодного индикатора</span><span class="sxs-lookup"><span data-stu-id="416c0-103">Blink an LED</span></span>

<span data-ttu-id="416c0-104">ПИН-коды универсального ввода-вывода (GPIO) можно контролировать отдельно.</span><span class="sxs-lookup"><span data-stu-id="416c0-104">General-purpose I/O (GPIO) pins can be controlled individually.</span></span> <span data-ttu-id="416c0-105">Это полезно для управления индикаторами, ретрансляторами и другими устройствами с отслеживанием состояния.</span><span class="sxs-lookup"><span data-stu-id="416c0-105">This is useful for controlling LEDs, relays, and other stateful devices.</span></span> <span data-ttu-id="416c0-106">В этом разделе вы будете использовать .NET и контакты GPIO Raspberry Pi для питания СВЕТОИНДИКАТОРА и мигающие его повторно.</span><span class="sxs-lookup"><span data-stu-id="416c0-106">In this topic, you will use .NET and your Raspberry Pi's GPIO pins to power an LED and blink it repeatedly.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="416c0-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="416c0-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="416c0-108">ИНДИКАТОР на 5 мм</span><span class="sxs-lookup"><span data-stu-id="416c0-108">5 mm LED</span></span>
- <span data-ttu-id="416c0-109">резистор ω 330</span><span class="sxs-lookup"><span data-stu-id="416c0-109">330 Ω resistor</span></span>
- <span data-ttu-id="416c0-110">монтажная плата;</span><span class="sxs-lookup"><span data-stu-id="416c0-110">Breadboard</span></span>
- <span data-ttu-id="416c0-111">оптоволоконные кабеля с разъемами на обоих концах;</span><span class="sxs-lookup"><span data-stu-id="416c0-111">Jumper wires</span></span>
- <span data-ttu-id="416c0-112">Raspberry Pi GPIO (необязательно/рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="416c0-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="416c0-113">Подготовка оборудования</span><span class="sxs-lookup"><span data-stu-id="416c0-113">Prepare the hardware</span></span>

<span data-ttu-id="416c0-114">Используйте аппаратные компоненты для создания канала, как показано на следующей схеме:</span><span class="sxs-lookup"><span data-stu-id="416c0-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="Схема Фритзинг, показывающая канал с ИНДИКАТОРом и резистором" lightbox="../media/rpi-led_bb.png":::

<span data-ttu-id="416c0-116">На приведенном выше рисунке изображены следующие подключения:</span><span class="sxs-lookup"><span data-stu-id="416c0-116">The image above depicts the following connections:</span></span>

- <span data-ttu-id="416c0-117">GPIO 18 — анод LED (более длинный, положительный)</span><span class="sxs-lookup"><span data-stu-id="416c0-117">GPIO 18 to LED anode (longer, positive lead)</span></span>
- <span data-ttu-id="416c0-118">Катод индикатора (короткий, отрицательный) до 330 Ωного резистора (End)</span><span class="sxs-lookup"><span data-stu-id="416c0-118">LED cathode (shorter, negative lead) to 330 Ω resistor (either end)</span></span>
- <span data-ttu-id="416c0-119">330 ω резистор (другой конец) к заземлению</span><span class="sxs-lookup"><span data-stu-id="416c0-119">330 Ω resistor (other end) to ground</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="416c0-120">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="416c0-120">Create the app</span></span>

<span data-ttu-id="416c0-121">Выполните следующие действия в предпочитаемой среде разработки:</span><span class="sxs-lookup"><span data-stu-id="416c0-121">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="416c0-122">Создайте новое консольное приложение .NET с помощью [интерфейса командной строки .NET](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="416c0-122">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="416c0-123">Назовите его *блинктуториал*.</span><span class="sxs-lookup"><span data-stu-id="416c0-123">Name it *BlinkTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="416c0-124">Замените содержимое *Program.cs* кодом из этого примера.</span><span class="sxs-lookup"><span data-stu-id="416c0-124">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    <span data-ttu-id="416c0-125">В предыдущем коде:</span><span class="sxs-lookup"><span data-stu-id="416c0-125">In the preceding code:</span></span>

    - <span data-ttu-id="416c0-126">[Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `GpioController` .</span><span class="sxs-lookup"><span data-stu-id="416c0-126">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `GpioController`.</span></span> <span data-ttu-id="416c0-127">`using`Объявление гарантирует, что объект удален и аппаратные ресурсы освобождаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="416c0-127">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="416c0-128">Для выходных данных открыт ПИН-код GPIO 18</span><span class="sxs-lookup"><span data-stu-id="416c0-128">GPIO pin 18 is opened for output</span></span>
    - <span data-ttu-id="416c0-129">`while`Цикл выполняется бессрочно.</span><span class="sxs-lookup"><span data-stu-id="416c0-129">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="416c0-130">Каждая итерация:</span><span class="sxs-lookup"><span data-stu-id="416c0-130">Each iteration:</span></span>
        1. <span data-ttu-id="416c0-131">Записывает значение в GPIO-контактный 18.</span><span class="sxs-lookup"><span data-stu-id="416c0-131">Writes a value to GPIO pin 18.</span></span> <span data-ttu-id="416c0-132">Если `ledOn` имеет значение true, то записывает `PinValue.High` (on).</span><span class="sxs-lookup"><span data-stu-id="416c0-132">If `ledOn` is true, it writes `PinValue.High` (on).</span></span> <span data-ttu-id="416c0-133">В противном случае он выполняет запись `PinValue.Low` .</span><span class="sxs-lookup"><span data-stu-id="416c0-133">Otherwise, it writes `PinValue.Low`.</span></span>
        1. <span data-ttu-id="416c0-134">Спящий режим 1000 мс.</span><span class="sxs-lookup"><span data-stu-id="416c0-134">Sleeps 1000 ms.</span></span>
        1. <span data-ttu-id="416c0-135">Переключает значение `ledOn` .</span><span class="sxs-lookup"><span data-stu-id="416c0-135">Toggles the value of `ledOn`.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="416c0-136">Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="416c0-136">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./BlinkTutorial
    ```

    <span data-ttu-id="416c0-137">ИНДИКАТОР мигает и включается каждую секунду.</span><span class="sxs-lookup"><span data-stu-id="416c0-137">The LED blinks off and on every second.</span></span>

1. <span data-ttu-id="416c0-138">Завершите программу, нажав клавиши <kbd>CTRL + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="416c0-138">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="416c0-139">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="416c0-139">Congratulations!</span></span> <span data-ttu-id="416c0-140">Вы использовали GPIO для мигания индикатора.</span><span class="sxs-lookup"><span data-stu-id="416c0-140">You've used GPIO to blink an LED.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="416c0-141">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="416c0-141">Get the source code</span></span>

<span data-ttu-id="416c0-142">Источник этого руководства [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="416c0-142">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="416c0-143">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="416c0-143">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="416c0-144">Узнайте, как считывать условия окружающей среды из датчика.</span><span class="sxs-lookup"><span data-stu-id="416c0-144">Learn how to read environmental conditions from a sensor</span></span>](../tutorials/temp-sensor.md)
