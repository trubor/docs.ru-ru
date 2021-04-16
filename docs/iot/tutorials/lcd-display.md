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
# <a name="display-text-on-an-lcd"></a><span data-ttu-id="4b465-103">Отображение текста на ЖК-дисплее</span><span class="sxs-lookup"><span data-stu-id="4b465-103">Display text on an LCD</span></span>

<span data-ttu-id="4b465-104">Символьные ЖК-дисплеи удобно использовать для отображения информации без внешнего монитора.</span><span class="sxs-lookup"><span data-stu-id="4b465-104">LCD character displays are useful for displaying information without the need for an external monitor.</span></span> <span data-ttu-id="4b465-105">Обычные символьные ЖК-дисплеи можно подключить напрямую к контактам GPIO, но в этом случае требуется использовать до 10 контактов GPIO.</span><span class="sxs-lookup"><span data-stu-id="4b465-105">Common LCD character displays can be connected directly to the GPIO pins, but such an approach requires the use of up to 10 GPIO pins.</span></span> <span data-ttu-id="4b465-106">В сценариях, требующих подключения к комбинации устройств, зачастую нецелесообразно выделять большую часть верхнего контактного ряда GPIO для символьного дисплея.</span><span class="sxs-lookup"><span data-stu-id="4b465-106">For scenarios that require connecting to a combination of devices, devoting so much of the GPIO header to a character display is often impractical.</span></span>

<span data-ttu-id="4b465-107">Многие производители продают символьные ЖК-дисплеи размером 20x4 со встроенным расширителем GPIO.</span><span class="sxs-lookup"><span data-stu-id="4b465-107">Many manufacturers sell 20x4 LCD character displays with an integrated GPIO expander.</span></span> <span data-ttu-id="4b465-108">Символьный дисплей напрямую подключается к расширителю GPIO, который затем подключается к устройству Raspberry Pi через последовательный протокол I2C.</span><span class="sxs-lookup"><span data-stu-id="4b465-108">The character display connects directly to the GPIO expander, which then connects to the Raspberry Pi via the Inter-Integrated Circuit (I2C) serial protocol.</span></span>

<span data-ttu-id="4b465-109">В этом разделе вы будете использовать .NET для отображения текста на символьном ЖК-дисплее с помощью расширителя GPIO I2C.</span><span class="sxs-lookup"><span data-stu-id="4b465-109">In this topic, you will use .NET to display text on an LCD character display using an I2C GPIO expander.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b465-110">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="4b465-110">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [<span data-ttu-id="4b465-111">Символьный ЖК-дисплей размером 20x4 с интерфейсом I2C</span><span class="sxs-lookup"><span data-stu-id="4b465-111">20x4 LCD Character Display with I2C interface</span></span>](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)
- <span data-ttu-id="4b465-112">оптоволоконные кабеля с разъемами на обоих концах;</span><span class="sxs-lookup"><span data-stu-id="4b465-112">Jumper wires</span></span>
- <span data-ttu-id="4b465-113">Монтажная плата (необязательно/рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="4b465-113">Breadboard (optional/recommended)</span></span>
- <span data-ttu-id="4b465-114">Коммутационная плата GPIO Raspberry Pi (необязательно/рекомендуется)</span><span class="sxs-lookup"><span data-stu-id="4b465-114">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> <span data-ttu-id="4b465-115">Существует множество производителей символьных ЖК-дисплеев.</span><span class="sxs-lookup"><span data-stu-id="4b465-115">There are many manufacturers of LCD character displays.</span></span> <span data-ttu-id="4b465-116">Большинство конструкций похожи, и производители не видят никакой разницы в функционале.</span><span class="sxs-lookup"><span data-stu-id="4b465-116">Most designs are identical, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="4b465-117">Для справки: это руководство было разработано для [LCD2004](https://www.sunfounder.com/lcd2004-module.html).</span><span class="sxs-lookup"><span data-stu-id="4b465-117">For reference, this tutorial was developed with the [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html).</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="4b465-118">Подготовка оборудования</span><span class="sxs-lookup"><span data-stu-id="4b465-118">Prepare the hardware</span></span>

<span data-ttu-id="4b465-119">Используйте соединительные провода, чтобы подключить четыре контакта на расширителе I2C к устройству Raspberry Pi следующим образом:</span><span class="sxs-lookup"><span data-stu-id="4b465-119">Use jumper wires to connect the four pins on the I2C GPIO expander to the Raspberry Pi as follows:</span></span>

- <span data-ttu-id="4b465-120">DGND к заземлению</span><span class="sxs-lookup"><span data-stu-id="4b465-120">GND to ground</span></span>
- <span data-ttu-id="4b465-121">VCC к 5V</span><span class="sxs-lookup"><span data-stu-id="4b465-121">VCC to 5V</span></span>
- <span data-ttu-id="4b465-122">SDA к SDA (GPIO 2)</span><span class="sxs-lookup"><span data-stu-id="4b465-122">SDA to SDA (GPIO 2)</span></span>
- <span data-ttu-id="4b465-123">SCL к SCL (GPIO 3)</span><span class="sxs-lookup"><span data-stu-id="4b465-123">SCL to SCL (GPIO 3)</span></span>

<span data-ttu-id="4b465-124">При необходимости ознакомьтесь со следующими рисунками:</span><span class="sxs-lookup"><span data-stu-id="4b465-124">Refer to the following figures as needed:</span></span>

| <span data-ttu-id="4b465-125">Интерфейс I2C (обратная сторона дисплея)</span><span class="sxs-lookup"><span data-stu-id="4b465-125">I2C interface (back of display)</span></span> | <span data-ttu-id="4b465-126">GPIO Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="4b465-126">Raspberry Pi GPIO</span></span> |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="Изображение обратной стороны символьного дисплея с расширителем I2C GPIO." lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Диаграмма, показывающая схему контактов верхнего контактного ряда GPIO Raspberry Pi. Изображение взято с Raspberry Pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="4b465-129">[Изображение взято с Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span><span class="sxs-lookup"><span data-stu-id="4b465-129">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="4b465-130">Создайте приложение</span><span class="sxs-lookup"><span data-stu-id="4b465-130">Create the app</span></span>

<span data-ttu-id="4b465-131">Выполните следующие действия в предпочитаемой среде разработки.</span><span class="sxs-lookup"><span data-stu-id="4b465-131">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="4b465-132">Создайте консольное приложение .NET с помощью [.NET CLI](../../core/tools/dotnet-new.md) или [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4b465-132">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="4b465-133">Назовите его *LcdTutorial*.</span><span class="sxs-lookup"><span data-stu-id="4b465-133">Name it *LcdTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="4b465-134">Замените содержимое *Program.cs* кодом из этого примера.</span><span class="sxs-lookup"><span data-stu-id="4b465-134">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    <span data-ttu-id="4b465-135">В приведенном выше коде:</span><span class="sxs-lookup"><span data-stu-id="4b465-135">In the preceding code:</span></span>

    - <span data-ttu-id="4b465-136">[Объявление using](../../csharp/whats-new/csharp-8.md#using-declarations) создает экземпляр `I2cDevice`, вызывая метод `I2cDevice.Create` и передавая новый класс `I2cConnectionSettings` с параметрами `busId` и `deviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="4b465-136">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in a new `I2cConnectionSettings` with the `busId` and `deviceAddress` parameters.</span></span> <span data-ttu-id="4b465-137">Класс `I2cDevice` представляет шину I2C.</span><span class="sxs-lookup"><span data-stu-id="4b465-137">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="4b465-138">Объявление `using` гарантирует, что объект удален и аппаратные ресурсы освобождены должным образом.</span><span class="sxs-lookup"><span data-stu-id="4b465-138">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>

        > [!WARNING]
        > <span data-ttu-id="4b465-139">Адрес устройства для расширителя GPIO зависит от микросхемы, используемой производителем.</span><span class="sxs-lookup"><span data-stu-id="4b465-139">The device address for the GPIO expander depends on the chip used by the manufacturer.</span></span> <span data-ttu-id="4b465-140">Расширители GPIO, оснащенные PCF8574, используют адрес `0x27`, а расширители с микросхемами PCF8574A используют `0x3F`.</span><span class="sxs-lookup"><span data-stu-id="4b465-140">GPIO expanders equipped with a PCF8574 use the address `0x27`, while those using PCF8574A chips use `0x3F`.</span></span> <span data-ttu-id="4b465-141">Обратитесь к документации по ЖК-дисплею.</span><span class="sxs-lookup"><span data-stu-id="4b465-141">Consult your LCD's documentation.</span></span>

    - <span data-ttu-id="4b465-142">Другое объявление `using` создает экземпляр `Pcf8574` и передает `I2cDevice` конструктору.</span><span class="sxs-lookup"><span data-stu-id="4b465-142">Another `using` declaration creates an instance of `Pcf8574` and passes the `I2cDevice` into the constructor.</span></span> <span data-ttu-id="4b465-143">Этот экземпляр представляет расширитель GPIO.</span><span class="sxs-lookup"><span data-stu-id="4b465-143">This instance represents the GPIO expander.</span></span>
    - <span data-ttu-id="4b465-144">Другое объявление `using` создает экземпляр `Lcd2004` для представления дисплея.</span><span class="sxs-lookup"><span data-stu-id="4b465-144">Another `using` declaration creates an instance of `Lcd2004` to represent the display.</span></span> <span data-ttu-id="4b465-145">Конструктору передается несколько параметров, описывающих настройки, которые будут использоваться для взаимодействия с расширителем GPIO.</span><span class="sxs-lookup"><span data-stu-id="4b465-145">Several parameters are passed to the constructor describing the settings to use to communicate with the GPIO expander.</span></span> <span data-ttu-id="4b465-146">Расширитель GPIO передается в качестве параметра `controller`.</span><span class="sxs-lookup"><span data-stu-id="4b465-146">The GPIO expander is passed as the `controller` parameter.</span></span>
    - <span data-ttu-id="4b465-147">Цикл `while` выполняется бесконечно.</span><span class="sxs-lookup"><span data-stu-id="4b465-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="4b465-148">Каждая итерация:</span><span class="sxs-lookup"><span data-stu-id="4b465-148">Each iteration:</span></span>
        1. <span data-ttu-id="4b465-149">Очищает экран.</span><span class="sxs-lookup"><span data-stu-id="4b465-149">Clears the display.</span></span>
        1. <span data-ttu-id="4b465-150">Устанавливает курсор в первую позицию в текущей строке.</span><span class="sxs-lookup"><span data-stu-id="4b465-150">Sets the cursor position to the first position on the current line.</span></span>
        1. <span data-ttu-id="4b465-151">Записывает текущее время для отображения в текущей позиции курсора.</span><span class="sxs-lookup"><span data-stu-id="4b465-151">Writes the current time to the display at the current cursor position.</span></span>
        1. <span data-ttu-id="4b465-152">Выполняет итерацию счетчика текущей строки.</span><span class="sxs-lookup"><span data-stu-id="4b465-152">Iterates the current line counter.</span></span>
        1. <span data-ttu-id="4b465-153">Переходит в спящий режим на 1000 мс.</span><span class="sxs-lookup"><span data-stu-id="4b465-153">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="4b465-154">Запустите приложение на устройстве Raspberry Pi, перейдя в каталог развертывания и запустив исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="4b465-154">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./LcdTutorial
    ```

    <span data-ttu-id="4b465-155">Наблюдайте за отображением текущего времени в каждой строке на символьном ЖК-дисплее.</span><span class="sxs-lookup"><span data-stu-id="4b465-155">Observe the LCD character display as the current time displays on each line.</span></span>

    > [!TIP]
    > <span data-ttu-id="4b465-156">Если дисплей светится, но текст не отображается, попробуйте настроить контрастность с помощью регулятора на обратной стороне экрана.</span><span class="sxs-lookup"><span data-stu-id="4b465-156">If the display is lit but you don't see any text, try adjusting the contrast dial on the back of the display.</span></span>

1. <span data-ttu-id="4b465-157">Завершите выполнение программы, нажав сочетание клавиш <kbd>CTRL+C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4b465-157">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="4b465-158">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="4b465-158">Congratulations!</span></span> <span data-ttu-id="4b465-159">Вы вывели текст на ЖК-монитор, используя расширитель GPIO I2C.</span><span class="sxs-lookup"><span data-stu-id="4b465-159">You've displayed text on an LCD using a I2C and a GPIO expander!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="4b465-160">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="4b465-160">Get the source code</span></span>

<span data-ttu-id="4b465-161">Исходный код для этого учебника [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial).</span><span class="sxs-lookup"><span data-stu-id="4b465-161">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4b465-162">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="4b465-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b465-163">Использование GPIO для мигания светодиодного индикатора</span><span class="sxs-lookup"><span data-stu-id="4b465-163">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
