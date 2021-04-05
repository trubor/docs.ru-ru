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
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a>Разработка приложений для устройств Интернета вещей с помощью библиотек .NET для Интернета вещей

.NET работает на разных платформах и архитектурах. Поддерживаются распространенные платы для Интернета вещей, например Raspberry Pi и Hummingboard. Приложения для Интернета вещей обычно взаимодействуют со специализированным оборудованием, например с датчиками, аналоговыми и цифровыми преобразователями, а также ЖК-устройствами. Библиотеки .NET для Интернета вещей поддерживают такие сценарии.

## <a name="video-overview"></a>Видеообзор

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a>Библиотеки

Библиотеки .NET для Интернета вещей состоят из двух пакетов NuGet:

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/)
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a>System.Device.Gpio

`System.Device.Gpio` поддерживает множество протоколов для низкоуровневого взаимодействия с аппаратными разъемами, что позволяет управлять устройствами. Сюда входит следующее:

- интерфейс ввода-вывода общего назначения (GPIO);
- шина для связи между интегральными схемами (I2C);
- последовательный интерфейс для периферийных устройств (SPI);
- широтно-импульсная модуляция (PWM);
- последовательный порт.

### <a name="iotdevicebindings"></a>Iot.Device.Bindings

Пакет `Iot.Device.Bindings` обладает следующими характеристиками:

* Содержит [привязки устройств](https://github.com/dotnet/iot/blob/main/src/devices/README.md), которые упрощают разработку приложений и предоставляют оболочку для System.Device.Gpio.
* Поддерживается сообществом и постоянно дополняется новыми привязками.

К часто используемым привязкам устройств относятся следующие:

- [CharacterLcd — символьный ЖК-дисплей;](https://github.com/dotnet/iot/tree/main/src/devices/CharacterLcd)
- [SN74HC595 — 8-битный сдвиговый регистр;](https://github.com/dotnet/iot/tree/main/src/devices/Sn74hc595)
- [BrickPi3;](https://github.com/dotnet/iot/tree/main/src/devices/BrickPi3)
- [Max7219 — драйвер светодиодной матрицы;](https://github.com/dotnet/iot/tree/main/src/devices/Max7219)
- [RGBLedMatrix — светодиодная матрица RGB.](https://github.com/dotnet/iot/tree/main/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

`System.Device.Gpio` поддерживается на большинстве версий Linux, которые могут работать с ARM/ARM64, а также в Windows 10 IoT Базовая.

> [!TIP]
> Для Raspberry Pi рекомендуется использовать [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) (прежнее название — Raspbian).

## <a name="supported-hardware-platforms"></a>Поддерживаемые аппаратные платформы

`System.Device.Gpio` поддерживает большинство известных платформ на одной плате. Рекомендуемые платформы — Raspberry Pi (версии 2 и выше) и Hummingboard. Также совместимость гарантируется для BeagleBoard и ODROID.

Платформы для настольных компьютеров поддерживаются через мост USB на SPI/I2C.

> [!IMPORTANT]
> Платформа .NET не поддерживается на устройствах с архитектурой ARMv6, включая устройства Raspberry Pi Zero и Raspberry Pi версий ниже Raspberry Pi 2.

## <a name="resources"></a>Ресурсы

- [Библиотеки .NET для Интернета вещей на сайте Github](https://github.com/dotnet/iot)
