---
title: Отображение текста на ЖК-дисплее
description: Узнайте, как отображать символы на жидкокристаллических дисплеях с помощью библиотек Интернета вещей .NET.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: d4c3e373207e23877903491871f4d09e11000c1a
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594134"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="display-text-on-an-lcd"></a><span data-ttu-id="520a2-103">Отображение текста на ЖК-дисплее</span><span class="sxs-lookup"><span data-stu-id="520a2-103">Display text on an LCD</span></span>

<span data-ttu-id="520a2-104">Отображение символов LCD удобно для отображения информации без внешнего монитора.</span><span class="sxs-lookup"><span data-stu-id="520a2-104">LCD character displays are useful for displaying information without the need for an external monitor.</span></span> <span data-ttu-id="520a2-105">Общедоступные дисплеи LCD могут быть подключены непосредственно к контактам GPIO, но такой подход требует использования до 10 ПИН-кодов GPIO.</span><span class="sxs-lookup"><span data-stu-id="520a2-105">Common LCD character displays can be connected directly to the GPIO pins, but such an approach requires the use of up to 10 GPIO pins.</span></span> <span data-ttu-id="520a2-106">В сценариях, требующих подключения к комбинации устройств, часто бывает непрактичным, что большая часть заголовка GPIO к отображению символов нецелесообразна.</span><span class="sxs-lookup"><span data-stu-id="520a2-106">For scenarios that require connecting to a combination of devices, devoting so much of the GPIO header to a character display is often impractical.</span></span>

<span data-ttu-id="520a2-107">Многие производители продают 20x4 ЖК-экран с интегрированным расширительом GPIO.</span><span class="sxs-lookup"><span data-stu-id="520a2-107">Many manufacturers sell 20x4 LCD character displays with an integrated GPIO expander.</span></span> <span data-ttu-id="520a2-108">Отображение символов напрямую подключается к расширительу GPIO, который подключается к устройству Raspberry Pi через последовательный протокол Inter-Integrated канала (I2C).</span><span class="sxs-lookup"><span data-stu-id="520a2-108">The character display connects directly to the GPIO expander, which then connects to the Raspberry Pi via the Inter-Integrated Circuit (I2C) serial protocol.</span></span>

<span data-ttu-id="520a2-109">В этом разделе вы будете использовать .NET для показа текста на ЖК-дисплее с помощью расширителя I2C GPIO.</span><span class="sxs-lookup"><span data-stu-id="520a2-109">In this topic, you will use .NET to display text on an LCD character display using an I2C GPIO expander.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="520a2-110">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="520a2-110">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="520a2-111">[Отображение символов ЖК-дисплея 20x4 с помощью интерфейса I2C](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="520a2-111">[20x4 LCD Character Display with I2C interface](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="520a2-112">оптоволоконные кабеля с разъемами на обоих концах;</span><span class="sxs-lookup"><span data-stu-id="520a2-112">Jumper wires</span></span>
- <span data-ttu-id="520a2-113">Монтажная плата (необязательно/рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="520a2-113">Breadboard (optional/recommended)</span></span>
- <span data-ttu-id="520a2-114">Raspberry Pi GPIO (необязательно/рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="520a2-114">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> <span data-ttu-id="520a2-115">Отображается множество производителей символов ЖК.</span><span class="sxs-lookup"><span data-stu-id="520a2-115">There are many manufacturers of LCD character displays.</span></span> <span data-ttu-id="520a2-116">Большинство структур идентичны, и изготовитель не должен делать никаких отличий от функциональности.</span><span class="sxs-lookup"><span data-stu-id="520a2-116">Most designs are identical, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="520a2-117">Для справки Этот учебник был разработан с [LCD2004](https://www.sunfounder.com/lcd2004-module.html) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="520a2-117">For reference, this tutorial was developed with the [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="520a2-118">Подготовка оборудования</span><span class="sxs-lookup"><span data-stu-id="520a2-118">Prepare the hardware</span></span>

<span data-ttu-id="520a2-119">Используйте перемычки перемычек, чтобы подключить четыре контакта в расширитель I2C к устройству Raspberry Pi следующим образом:</span><span class="sxs-lookup"><span data-stu-id="520a2-119">Use jumper wires to connect the four pins on the I2C GPIO expander to the Raspberry Pi as follows:</span></span>

- <span data-ttu-id="520a2-120">От ЗАЗЕМЛЕНия к заземлению</span><span class="sxs-lookup"><span data-stu-id="520a2-120">GND to ground</span></span>
- <span data-ttu-id="520a2-121">От VCC до 5</span><span class="sxs-lookup"><span data-stu-id="520a2-121">VCC to 5V</span></span>
- <span data-ttu-id="520a2-122">От SDA к SDA (GPIO 2)</span><span class="sxs-lookup"><span data-stu-id="520a2-122">SDA to SDA (GPIO 2)</span></span>
- <span data-ttu-id="520a2-123">SCL для SCL (GPIO 3)</span><span class="sxs-lookup"><span data-stu-id="520a2-123">SCL to SCL (GPIO 3)</span></span>

<span data-ttu-id="520a2-124">При необходимости ознакомьтесь со следующими рисунками:</span><span class="sxs-lookup"><span data-stu-id="520a2-124">Refer to the following figures as needed:</span></span>

| <span data-ttu-id="520a2-125">Интерфейс I2C (задняя часть экрана)</span><span class="sxs-lookup"><span data-stu-id="520a2-125">I2C interface (back of display)</span></span> | <span data-ttu-id="520a2-126">Raspberry Pi GPIO</span><span class="sxs-lookup"><span data-stu-id="520a2-126">Raspberry Pi GPIO</span></span> |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="Изображение обратной стороны отображения символов, показывающее расширитель I2C GPIO." lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Схема, показывающая схему контактов заголовка Raspberry Pi GPIO. Образ с Raspberry Pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="520a2-129">[Образ с Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="520a2-129">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="520a2-130">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="520a2-130">Create the app</span></span>

<span data-ttu-id="520a2-131">Выполните следующие действия в предпочитаемой среде разработки:</span><span class="sxs-lookup"><span data-stu-id="520a2-131">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="520a2-132">Создайте новое консольное приложение .NET с помощью [интерфейса командной строки .NET](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="520a2-132">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="520a2-133">Назовите его *лкдтуториал*.</span><span class="sxs-lookup"><span data-stu-id="520a2-133">Name it *LcdTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="520a2-134">Замените содержимое *Program.cs* кодом из этого примера.</span><span class="sxs-lookup"><span data-stu-id="520a2-134">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    <span data-ttu-id="520a2-135">В предыдущем коде:</span><span class="sxs-lookup"><span data-stu-id="520a2-135">In the preceding code:</span></span>

    - <span data-ttu-id="520a2-136">[Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `I2cDevice` , вызывая метод `I2cDevice.Create` и передавая новый `I2cConnectionSettings` с `busId` `deviceAddress` параметрами и.</span><span class="sxs-lookup"><span data-stu-id="520a2-136">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in a new `I2cConnectionSettings` with the `busId` and `deviceAddress` parameters.</span></span> <span data-ttu-id="520a2-137">Это `I2cDevice` представляет ШИНУ I2C.</span><span class="sxs-lookup"><span data-stu-id="520a2-137">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="520a2-138">`using`Объявление гарантирует, что объект удален и аппаратные ресурсы освобождаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="520a2-138">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>

        > [!WARNING]
        > <span data-ttu-id="520a2-139">Адрес устройства для расширителя GPIO зависит от микросхемы, используемой производителем.</span><span class="sxs-lookup"><span data-stu-id="520a2-139">The device address for the GPIO expander depends on the chip used by the manufacturer.</span></span> <span data-ttu-id="520a2-140">Расширители GPIO, оснащенные PCF8574, используют адрес `0x27` , а те, кто использует микросхемы PCF8574A `0x3F` .</span><span class="sxs-lookup"><span data-stu-id="520a2-140">GPIO expanders equipped with a PCF8574 use the address `0x27`, while those using PCF8574A chips use `0x3F`.</span></span> <span data-ttu-id="520a2-141">Обратитесь к документации ЖК-дисплея.</span><span class="sxs-lookup"><span data-stu-id="520a2-141">Consult your LCD's documentation.</span></span>

    - <span data-ttu-id="520a2-142">Другое `using` объявление создает экземпляр `Pcf8574` и передает его в `I2cDevice` конструктор.</span><span class="sxs-lookup"><span data-stu-id="520a2-142">Another `using` declaration creates an instance of `Pcf8574` and passes the `I2cDevice` into the constructor.</span></span> <span data-ttu-id="520a2-143">Этот экземпляр представляет расширитель GPIO.</span><span class="sxs-lookup"><span data-stu-id="520a2-143">This instance represents the GPIO expander.</span></span>
    - <span data-ttu-id="520a2-144">Другое `using` объявление создает экземпляр `Lcd2004` для представления отображения.</span><span class="sxs-lookup"><span data-stu-id="520a2-144">Another `using` declaration creates an instance of `Lcd2004` to represent the display.</span></span> <span data-ttu-id="520a2-145">В конструктор передается несколько параметров, описывающих параметры, используемые для взаимодействия с расширительом GPIO.</span><span class="sxs-lookup"><span data-stu-id="520a2-145">Several parameters are passed to the constructor describing the settings to use to communicate with the GPIO expander.</span></span> <span data-ttu-id="520a2-146">Расширитель GPIO передается в качестве `controller` параметра.</span><span class="sxs-lookup"><span data-stu-id="520a2-146">The GPIO expander is passed as the `controller` parameter.</span></span>
    - <span data-ttu-id="520a2-147">`while`Цикл выполняется бессрочно.</span><span class="sxs-lookup"><span data-stu-id="520a2-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="520a2-148">Каждая итерация:</span><span class="sxs-lookup"><span data-stu-id="520a2-148">Each iteration:</span></span>
        1. <span data-ttu-id="520a2-149">Очищает экран.</span><span class="sxs-lookup"><span data-stu-id="520a2-149">Clears the display.</span></span>
        1. <span data-ttu-id="520a2-150">Устанавливает позицию курсора в первую позицию в текущей строке.</span><span class="sxs-lookup"><span data-stu-id="520a2-150">Sets the cursor position to the first position on the current line.</span></span>
        1. <span data-ttu-id="520a2-151">Записывает текущее время на экран в текущей позиции курсора.</span><span class="sxs-lookup"><span data-stu-id="520a2-151">Writes the current time to the display at the current cursor position.</span></span>
        1. <span data-ttu-id="520a2-152">Выполняет итерацию счетчика текущей строки.</span><span class="sxs-lookup"><span data-stu-id="520a2-152">Iterates the current line counter.</span></span>
        1. <span data-ttu-id="520a2-153">Спящий режим 1000 мс.</span><span class="sxs-lookup"><span data-stu-id="520a2-153">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="520a2-154">Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="520a2-154">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./LcdTutorial
    ```

    <span data-ttu-id="520a2-155">Обратите внимание на отображение символа ЖК-дисплея, так как текущее время отображается в каждой строке.</span><span class="sxs-lookup"><span data-stu-id="520a2-155">Observe the LCD character display as the current time displays on each line.</span></span>

    > [!TIP]
    > <span data-ttu-id="520a2-156">Если дисплей горит, но текст не отображается, попробуйте настроить контрастность на обратной стороне экрана.</span><span class="sxs-lookup"><span data-stu-id="520a2-156">If the display is lit but you don't see any text, try adjusting the contrast dial on the back of the display.</span></span>

1. <span data-ttu-id="520a2-157">Завершите программу, нажав клавиши <kbd>CTRL + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="520a2-157">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="520a2-158">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="520a2-158">Congratulations!</span></span> <span data-ttu-id="520a2-159">Вы выделили текст на ЖК-мониторе, используя I2C и расширитель GPIO!</span><span class="sxs-lookup"><span data-stu-id="520a2-159">You've displayed text on an LCD using a I2C and a GPIO expander!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="520a2-160">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="520a2-160">Get the source code</span></span>

<span data-ttu-id="520a2-161">Источник этого руководства [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="520a2-161">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="520a2-162">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="520a2-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="520a2-163">Научитесь использовать общего назначения ввода-вывода для мигания индикатора</span><span class="sxs-lookup"><span data-stu-id="520a2-163">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
