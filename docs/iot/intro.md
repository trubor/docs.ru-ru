---
title: Разработка приложений для устройств Интернета вещей с помощью библиотек .NET для Интернета вещей
description: Сведения о том, как на основе .NET создавать приложения для устройств и сценариев Интернета вещей
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: 4d8dffb28b28c999b3d1bf77a65265280a8ae7a1
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874788"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="886fd-103">Разработка приложений для устройств Интернета вещей с помощью библиотек .NET для Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="886fd-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="886fd-104">.NET работает на разных платформах и архитектурах.</span><span class="sxs-lookup"><span data-stu-id="886fd-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="886fd-105">Поддерживаются распространенные платы для Интернета вещей, например Raspberry Pi и Hummingboard.</span><span class="sxs-lookup"><span data-stu-id="886fd-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="886fd-106">Приложения для Интернета вещей обычно взаимодействуют со специализированным оборудованием, например с датчиками, аналоговыми и цифровыми преобразователями, а также ЖК-устройствами.</span><span class="sxs-lookup"><span data-stu-id="886fd-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="886fd-107">Библиотеки .NET для Интернета вещей поддерживают такие сценарии.</span><span class="sxs-lookup"><span data-stu-id="886fd-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="886fd-108">Видеообзор</span><span class="sxs-lookup"><span data-stu-id="886fd-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="886fd-109">Библиотеки</span><span class="sxs-lookup"><span data-stu-id="886fd-109">Libraries</span></span>

<span data-ttu-id="886fd-110">Библиотеки .NET для Интернета вещей состоят из двух пакетов NuGet:</span><span class="sxs-lookup"><span data-stu-id="886fd-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- [<span data-ttu-id="886fd-111">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="886fd-111">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/)
- [<span data-ttu-id="886fd-112">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="886fd-112">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a><span data-ttu-id="886fd-113">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="886fd-113">System.Device.Gpio</span></span>

<span data-ttu-id="886fd-114">`System.Device.Gpio` поддерживает множество протоколов для низкоуровневого взаимодействия с аппаратными разъемами, что позволяет управлять устройствами.</span><span class="sxs-lookup"><span data-stu-id="886fd-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="886fd-115">Сюда входит следующее:</span><span class="sxs-lookup"><span data-stu-id="886fd-115">These include:</span></span>

- <span data-ttu-id="886fd-116">интерфейс ввода-вывода общего назначения (GPIO);</span><span class="sxs-lookup"><span data-stu-id="886fd-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="886fd-117">шина для связи между интегральными схемами (I2C);</span><span class="sxs-lookup"><span data-stu-id="886fd-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="886fd-118">последовательный интерфейс для периферийных устройств (SPI);</span><span class="sxs-lookup"><span data-stu-id="886fd-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="886fd-119">широтно-импульсная модуляция (PWM);</span><span class="sxs-lookup"><span data-stu-id="886fd-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="886fd-120">последовательный порт.</span><span class="sxs-lookup"><span data-stu-id="886fd-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="886fd-121">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="886fd-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="886fd-122">Пакет `Iot.Device.Bindings` обладает следующими характеристиками:</span><span class="sxs-lookup"><span data-stu-id="886fd-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="886fd-123">Содержит [привязки устройств](https://github.com/dotnet/iot/blob/main/src/devices/README.md), которые упрощают разработку приложений и предоставляют оболочку для System.Device.Gpio.</span><span class="sxs-lookup"><span data-stu-id="886fd-123">Contains [device bindings](https://github.com/dotnet/iot/blob/main/src/devices/README.md) to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="886fd-124">Поддерживается сообществом и постоянно дополняется новыми привязками.</span><span class="sxs-lookup"><span data-stu-id="886fd-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="886fd-125">К часто используемым привязкам устройств относятся следующие:</span><span class="sxs-lookup"><span data-stu-id="886fd-125">Commonly used device bindings include:</span></span>

- [<span data-ttu-id="886fd-126">CharacterLcd — символьный ЖК-дисплей;</span><span class="sxs-lookup"><span data-stu-id="886fd-126">CharacterLcd - LCD character display</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/CharacterLcd)
- [<span data-ttu-id="886fd-127">SN74HC595 — 8-битный сдвиговый регистр;</span><span class="sxs-lookup"><span data-stu-id="886fd-127">SN74HC595 - 8-bit shift register</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/Sn74hc595)
- [<span data-ttu-id="886fd-128">BrickPi3;</span><span class="sxs-lookup"><span data-stu-id="886fd-128">BrickPi3</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/BrickPi3)
- [<span data-ttu-id="886fd-129">Max7219 — драйвер светодиодной матрицы;</span><span class="sxs-lookup"><span data-stu-id="886fd-129">Max7219 - LED Matrix driver</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/Max7219)
- [<span data-ttu-id="886fd-130">RGBLedMatrix — светодиодная матрица RGB.</span><span class="sxs-lookup"><span data-stu-id="886fd-130">RGBLedMatrix - RGB LED Matrix</span></span>](https://github.com/dotnet/iot/tree/main/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a><span data-ttu-id="886fd-131">Поддерживаемые операционные системы</span><span class="sxs-lookup"><span data-stu-id="886fd-131">Supported operating systems</span></span>

<span data-ttu-id="886fd-132">`System.Device.Gpio` поддерживается на большинстве версий Linux, которые могут работать с ARM/ARM64, а также в Windows 10 IoT Базовая.</span><span class="sxs-lookup"><span data-stu-id="886fd-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="886fd-133">Для Raspberry Pi рекомендуется использовать [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) (прежнее название — Raspbian).</span><span class="sxs-lookup"><span data-stu-id="886fd-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="886fd-134">Поддерживаемые аппаратные платформы</span><span class="sxs-lookup"><span data-stu-id="886fd-134">Supported hardware platforms</span></span>

<span data-ttu-id="886fd-135">`System.Device.Gpio` поддерживает большинство известных платформ на одной плате.</span><span class="sxs-lookup"><span data-stu-id="886fd-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="886fd-136">Рекомендуемые платформы — Raspberry Pi (версии 2 и выше) и Hummingboard.</span><span class="sxs-lookup"><span data-stu-id="886fd-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="886fd-137">Также совместимость гарантируется для BeagleBoard и ODROID.</span><span class="sxs-lookup"><span data-stu-id="886fd-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="886fd-138">Платформы для настольных компьютеров поддерживаются через мост USB на SPI/I2C.</span><span class="sxs-lookup"><span data-stu-id="886fd-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="886fd-139">Платформа .NET не поддерживается на устройствах с архитектурой ARMv6, включая устройства Raspberry Pi Zero и Raspberry Pi версий ниже Raspberry Pi 2.</span><span class="sxs-lookup"><span data-stu-id="886fd-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="886fd-140">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="886fd-140">Resources</span></span>

- [<span data-ttu-id="886fd-141">Библиотеки .NET для Интернета вещей на сайте Github</span><span class="sxs-lookup"><span data-stu-id="886fd-141">.NET IoT Libraries on Github</span></span>](https://github.com/dotnet/iot)
