---
title: Краткое руководство. Использование .NET для Raspberry Pi Sense HAT
description: Приступите к работе с библиотеками .NET IoT за 5 минут с помощью Sense HAT, дополнительной платы для Raspberry Pi.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 28d6650187bbf7b9ce91516f4da4d09b114c904a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259704"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a>Краткое руководство. Использование .NET для Raspberry Pi Sense HAT

Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ardware **A** ttached on **T** op) — это дополнительная плата для Raspberry Pi. Sense HAT оснащена светодиодной матрицей 8×8 RGB, джойстиком с пятью кнопками и следующими датчиками:

- Гироскоп
- Акселерометр
- Магнитометр
- температура;
- Давление
- влажность.

В этом кратком руководстве используется платформа .NET для извлечения значений датчиков c Sense HAT, ответа на команды джойстика и последующей работы со светодиодной матрицей.

## <a name="prerequisites"></a>Предварительные требования

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- Sense HAT

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a>Запуск краткого руководства

Прикрепите Sense HAT к Raspberry Pi. В командной строке Bash в Raspberry Pi (локальной или удаленной) выполните следующую команду:

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

Команда загружает и выполняет скрипт. Сценарий:

- Устанавливает пакет SDK для .NET.
- Клонирует репозиторий GitHub, включающий проект краткого руководства по Sense HAT.
- Выполняет построение проекта.
- Запускает проект.

Выходные данные консоли отображаются в виде данных датчика. На светодиодной матрице отображается желтый пиксель на поле синего цвета. Если держать джойстик в каком-то направлении, желтый пиксель переместится в этом направлении. Если нажать на центральную кнопку джойстика, фон переключится с синего на красный.

## <a name="get-the-source-code"></a>Получение исходного кода

Исходный код для этого краткого руководства [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Использование GPIO для мигания светодиодного индикатора](../tutorials/blink-led.md)
