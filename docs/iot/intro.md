---
title: Разработка приложений для устройств IoT с помощью библиотек .NET IoT
description: Узнайте, как можно использовать .NET для создания приложений для устройств и сценариев Интернета вещей.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: c3d05ec5b05780f91404c3c27e91bcd602b0faeb
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2020
ms.locfileid: "96594029"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="2230d-103">Разработка приложений для устройств IoT с помощью библиотек .NET IoT</span><span class="sxs-lookup"><span data-stu-id="2230d-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="2230d-104">.NET работает на различных платформах и архитектурах.</span><span class="sxs-lookup"><span data-stu-id="2230d-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="2230d-105">Поддерживаются стандартные доски Интернета вещей (IoT), такие как Raspberry Pi и Хуммингбоард.</span><span class="sxs-lookup"><span data-stu-id="2230d-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="2230d-106">Приложения IoT обычно взаимодействуют со специализированным оборудованием, например датчиками, аналоговыми и цифровыми преобразователями, а также ЖК-устройствами.</span><span class="sxs-lookup"><span data-stu-id="2230d-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="2230d-107">Эти сценарии включены в библиотеках .NET IoT.</span><span class="sxs-lookup"><span data-stu-id="2230d-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="2230d-108">Видеообзор</span><span class="sxs-lookup"><span data-stu-id="2230d-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="2230d-109">Библиотеки</span><span class="sxs-lookup"><span data-stu-id="2230d-109">Libraries</span></span>

<span data-ttu-id="2230d-110">Библиотеки .NET IoT состоят из двух пакетов NuGet:</span><span class="sxs-lookup"><span data-stu-id="2230d-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- <span data-ttu-id="2230d-111">[System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="2230d-111">[System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="2230d-112">[Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="2230d-112">[Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

### <a name="systemdevicegpio"></a><span data-ttu-id="2230d-113">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="2230d-113">System.Device.Gpio</span></span>

<span data-ttu-id="2230d-114">`System.Device.Gpio` поддерживает различные протоколы для взаимодействия с аппаратными креплениями низкого уровня для управления устройствами.</span><span class="sxs-lookup"><span data-stu-id="2230d-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="2230d-115">приведенные ниже.</span><span class="sxs-lookup"><span data-stu-id="2230d-115">These include:</span></span>

- <span data-ttu-id="2230d-116">Универсальный ввод-вывод (GPIO)</span><span class="sxs-lookup"><span data-stu-id="2230d-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="2230d-117">Канал Inter-Integrated (I2C)</span><span class="sxs-lookup"><span data-stu-id="2230d-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="2230d-118">Интерфейс Serial периферийных устройств (SPI)</span><span class="sxs-lookup"><span data-stu-id="2230d-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="2230d-119">Модуляция ширины импульса (ШИРОТы)</span><span class="sxs-lookup"><span data-stu-id="2230d-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="2230d-120">Последовательный порт</span><span class="sxs-lookup"><span data-stu-id="2230d-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="2230d-121">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="2230d-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="2230d-122">`Iot.Device.Bindings`Пакет:</span><span class="sxs-lookup"><span data-stu-id="2230d-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="2230d-123">Содержит [привязки устройств](https://github.com/dotnet/iot/blob/master/src/devices/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> для упрощения разработки приложений с помощью оболочки System. Device. GPIO.</span><span class="sxs-lookup"><span data-stu-id="2230d-123">Contains [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="2230d-124">Поддерживается сообществом, а дополнительные привязки постоянно добавляются.</span><span class="sxs-lookup"><span data-stu-id="2230d-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="2230d-125">К часто используемым привязкам устройств относятся:</span><span class="sxs-lookup"><span data-stu-id="2230d-125">Commonly used device bindings include:</span></span>

- <span data-ttu-id="2230d-126">[Чарактерлкд — отображение символов LCD](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="2230d-126">[CharacterLcd - LCD character display](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="2230d-127">[SN74HC595-8-разрядный сдвиг регистра](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="2230d-127">[SN74HC595 - 8-bit shift register](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="2230d-128">[BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="2230d-128">[BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="2230d-129">[Драйвер матрицы Max7219-LED](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="2230d-129">[Max7219 - LED Matrix driver](https://github.com/dotnet/iot/tree/master/src/devices/Max7219) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="2230d-130">[Ргбледматрикс-матрица индикаторов RGB](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="2230d-130">[RGBLedMatrix - RGB LED Matrix](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="2230d-131">Поддерживаемые операционные системы</span><span class="sxs-lookup"><span data-stu-id="2230d-131">Supported operating systems</span></span>

<span data-ttu-id="2230d-132">`System.Device.Gpio` поддерживается в большинстве версий Linux, поддерживающих ARM/ARM64 и Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2230d-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="2230d-133">Для Raspberry Pi рекомендуется [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> (прежнее название — Raspbian).  </span><span class="sxs-lookup"><span data-stu-id="2230d-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  <span class="docon docon-navigate-external x-hidden-focus"></span> (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="2230d-134">Поддерживаемые аппаратные платформы</span><span class="sxs-lookup"><span data-stu-id="2230d-134">Supported hardware platforms</span></span>

<span data-ttu-id="2230d-135">`System.Device.Gpio` совместима с большинством одноплатных платформ.</span><span class="sxs-lookup"><span data-stu-id="2230d-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="2230d-136">Рекомендуемые платформы — Raspberry Pi (2 и выше) и Хуммингбоард.</span><span class="sxs-lookup"><span data-stu-id="2230d-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="2230d-137">Другие платформы, совместимые с совместимостью, — это Беаглебоард и ОДРОИД.</span><span class="sxs-lookup"><span data-stu-id="2230d-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="2230d-138">Платформы PC поддерживаются посредством использования моста USB и SPI/I2C.</span><span class="sxs-lookup"><span data-stu-id="2230d-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2230d-139">Платформа .NET не поддерживается на устройствах архитектуры ARMv6, включая нуль-и Raspberry Pi устройств Raspberry Pi до Raspberry Pi 2.</span><span class="sxs-lookup"><span data-stu-id="2230d-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="2230d-140">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="2230d-140">Resources</span></span>

- <span data-ttu-id="2230d-141">[Библиотеки .NET IOT на GitHub](https://github.com/dotnet/iot)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="2230d-141">[.NET IoT Libraries on Github](https://github.com/dotnet/iot) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
