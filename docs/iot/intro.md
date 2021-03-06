---
title: Разработка приложений для устройств IoT с помощью библиотек .NET IoT
description: Узнайте, как можно использовать .NET для создания приложений для устройств и сценариев Интернета вещей.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: 13460fdafbfd7ef4e047cb7537e832ae4039c614
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255435"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="5e361-103">Разработка приложений для устройств IoT с помощью библиотек .NET IoT</span><span class="sxs-lookup"><span data-stu-id="5e361-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="5e361-104">.NET работает на различных платформах и архитектурах.</span><span class="sxs-lookup"><span data-stu-id="5e361-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="5e361-105">Поддерживаются стандартные доски Интернета вещей (IoT), такие как Raspberry Pi и Хуммингбоард.</span><span class="sxs-lookup"><span data-stu-id="5e361-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="5e361-106">Приложения IoT обычно взаимодействуют со специализированным оборудованием, например датчиками, аналоговыми и цифровыми преобразователями, а также ЖК-устройствами.</span><span class="sxs-lookup"><span data-stu-id="5e361-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="5e361-107">Эти сценарии включены в библиотеках .NET IoT.</span><span class="sxs-lookup"><span data-stu-id="5e361-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="5e361-108">Видеообзор</span><span class="sxs-lookup"><span data-stu-id="5e361-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="5e361-109">Библиотеки</span><span class="sxs-lookup"><span data-stu-id="5e361-109">Libraries</span></span>

<span data-ttu-id="5e361-110">Библиотеки .NET IoT состоят из двух пакетов NuGet:</span><span class="sxs-lookup"><span data-stu-id="5e361-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- [<span data-ttu-id="5e361-111">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="5e361-111">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/)
- [<span data-ttu-id="5e361-112">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="5e361-112">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a><span data-ttu-id="5e361-113">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="5e361-113">System.Device.Gpio</span></span>

<span data-ttu-id="5e361-114">`System.Device.Gpio` поддерживает различные протоколы для взаимодействия с аппаратными креплениями низкого уровня для управления устройствами.</span><span class="sxs-lookup"><span data-stu-id="5e361-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="5e361-115">Сюда входит следующее.</span><span class="sxs-lookup"><span data-stu-id="5e361-115">These include:</span></span>

- <span data-ttu-id="5e361-116">Универсальный ввод-вывод (GPIO)</span><span class="sxs-lookup"><span data-stu-id="5e361-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="5e361-117">Канал Inter-Integrated (I2C)</span><span class="sxs-lookup"><span data-stu-id="5e361-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="5e361-118">Интерфейс Serial периферийных устройств (SPI)</span><span class="sxs-lookup"><span data-stu-id="5e361-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="5e361-119">Модуляция ширины импульса (ШИРОТы)</span><span class="sxs-lookup"><span data-stu-id="5e361-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="5e361-120">Последовательный порт</span><span class="sxs-lookup"><span data-stu-id="5e361-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="5e361-121">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="5e361-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="5e361-122">`Iot.Device.Bindings`Пакет:</span><span class="sxs-lookup"><span data-stu-id="5e361-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="5e361-123">Содержит [привязки устройств](https://github.com/dotnet/iot/blob/master/src/devices/README.md) для упрощения разработки приложений с помощью оболочки System. Device. GPIO.</span><span class="sxs-lookup"><span data-stu-id="5e361-123">Contains [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="5e361-124">Поддерживается сообществом, а дополнительные привязки постоянно добавляются.</span><span class="sxs-lookup"><span data-stu-id="5e361-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="5e361-125">К часто используемым привязкам устройств относятся:</span><span class="sxs-lookup"><span data-stu-id="5e361-125">Commonly used device bindings include:</span></span>

- [<span data-ttu-id="5e361-126">Чарактерлкд — отображение символов LCD</span><span class="sxs-lookup"><span data-stu-id="5e361-126">CharacterLcd - LCD character display</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)
- [<span data-ttu-id="5e361-127">SN74HC595-8-разрядный сдвиг регистра</span><span class="sxs-lookup"><span data-stu-id="5e361-127">SN74HC595 - 8-bit shift register</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)
- [<span data-ttu-id="5e361-128">BrickPi3</span><span class="sxs-lookup"><span data-stu-id="5e361-128">BrickPi3</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)
- [<span data-ttu-id="5e361-129">Драйвер матрицы Max7219-LED</span><span class="sxs-lookup"><span data-stu-id="5e361-129">Max7219 - LED Matrix driver</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)
- [<span data-ttu-id="5e361-130">Ргбледматрикс-матрица ИНДИКАТОРов RGB</span><span class="sxs-lookup"><span data-stu-id="5e361-130">RGBLedMatrix - RGB LED Matrix</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a><span data-ttu-id="5e361-131">Поддерживаемые операционные системы</span><span class="sxs-lookup"><span data-stu-id="5e361-131">Supported operating systems</span></span>

<span data-ttu-id="5e361-132">`System.Device.Gpio` поддерживается в большинстве версий Linux, поддерживающих ARM/ARM64 и Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="5e361-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="5e361-133">Для Raspberry Pi рекомендуется [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (прежнее название — Raspbian).</span><span class="sxs-lookup"><span data-stu-id="5e361-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="5e361-134">Поддерживаемые аппаратные платформы</span><span class="sxs-lookup"><span data-stu-id="5e361-134">Supported hardware platforms</span></span>

<span data-ttu-id="5e361-135">`System.Device.Gpio` совместима с большинством одноплатных платформ.</span><span class="sxs-lookup"><span data-stu-id="5e361-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="5e361-136">Рекомендуемые платформы — Raspberry Pi (2 и выше) и Хуммингбоард.</span><span class="sxs-lookup"><span data-stu-id="5e361-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="5e361-137">Другие платформы, совместимые с совместимостью, — это Беаглебоард и ОДРОИД.</span><span class="sxs-lookup"><span data-stu-id="5e361-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="5e361-138">Платформы PC поддерживаются посредством использования моста USB и SPI/I2C.</span><span class="sxs-lookup"><span data-stu-id="5e361-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e361-139">Платформа .NET не поддерживается на устройствах архитектуры ARMv6, включая нуль-и Raspberry Pi устройств Raspberry Pi до Raspberry Pi 2.</span><span class="sxs-lookup"><span data-stu-id="5e361-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="5e361-140">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="5e361-140">Resources</span></span>

- [<span data-ttu-id="5e361-141">Библиотеки .NET IoT на GitHub</span><span class="sxs-lookup"><span data-stu-id="5e361-141">.NET IoT Libraries on Github</span></span>](https://github.com/dotnet/iot)
