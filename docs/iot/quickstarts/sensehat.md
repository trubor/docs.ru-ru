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
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a><span data-ttu-id="fd01e-103">Краткое руководство. Использование .NET для Raspberry Pi Sense HAT</span><span class="sxs-lookup"><span data-stu-id="fd01e-103">Quickstart - Use .NET to drive a Raspberry Pi Sense HAT</span></span>

<span data-ttu-id="fd01e-104">Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ardware **A** ttached on **T** op) — это дополнительная плата для Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="fd01e-104">The Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ardware **A** ttached on **T** op) is an add-on board for Raspberry Pi.</span></span> <span data-ttu-id="fd01e-105">Sense HAT оснащена светодиодной матрицей 8×8 RGB, джойстиком с пятью кнопками и следующими датчиками:</span><span class="sxs-lookup"><span data-stu-id="fd01e-105">The Sense HAT is equipped with an 8×8 RGB LED matrix, a five-button joystick, and includes the following sensors:</span></span>

- <span data-ttu-id="fd01e-106">Гироскоп</span><span class="sxs-lookup"><span data-stu-id="fd01e-106">Gyroscope</span></span>
- <span data-ttu-id="fd01e-107">Акселерометр</span><span class="sxs-lookup"><span data-stu-id="fd01e-107">Accelerometer</span></span>
- <span data-ttu-id="fd01e-108">Магнитометр</span><span class="sxs-lookup"><span data-stu-id="fd01e-108">Magnetometer</span></span>
- <span data-ttu-id="fd01e-109">температура;</span><span class="sxs-lookup"><span data-stu-id="fd01e-109">Temperature</span></span>
- <span data-ttu-id="fd01e-110">Давление</span><span class="sxs-lookup"><span data-stu-id="fd01e-110">Barometric pressure</span></span>
- <span data-ttu-id="fd01e-111">влажность.</span><span class="sxs-lookup"><span data-stu-id="fd01e-111">Humidity</span></span>

<span data-ttu-id="fd01e-112">В этом кратком руководстве используется платформа .NET для извлечения значений датчиков c Sense HAT, ответа на команды джойстика и последующей работы со светодиодной матрицей.</span><span class="sxs-lookup"><span data-stu-id="fd01e-112">This quickstart uses .NET to retrieve sensor values from the Sense HAT, respond to joystick input, and drive the LED matrix.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fd01e-113">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="fd01e-113">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="fd01e-114">Sense HAT</span><span class="sxs-lookup"><span data-stu-id="fd01e-114">Sense HAT</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a><span data-ttu-id="fd01e-115">Запуск краткого руководства</span><span class="sxs-lookup"><span data-stu-id="fd01e-115">Run the quickstart</span></span>

<span data-ttu-id="fd01e-116">Прикрепите Sense HAT к Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="fd01e-116">Attach the Sense HAT to your Raspberry Pi.</span></span> <span data-ttu-id="fd01e-117">В командной строке Bash в Raspberry Pi (локальной или удаленной) выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fd01e-117">From a Bash prompt on the Raspberry Pi (local or remote), run the following command:</span></span>

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

<span data-ttu-id="fd01e-118">Команда загружает и выполняет скрипт.</span><span class="sxs-lookup"><span data-stu-id="fd01e-118">The command downloads and runs a script.</span></span> <span data-ttu-id="fd01e-119">Сценарий:</span><span class="sxs-lookup"><span data-stu-id="fd01e-119">The script:</span></span>

- <span data-ttu-id="fd01e-120">Устанавливает пакет SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="fd01e-120">Installs the .NET SDK.</span></span>
- <span data-ttu-id="fd01e-121">Клонирует репозиторий GitHub, включающий проект краткого руководства по Sense HAT.</span><span class="sxs-lookup"><span data-stu-id="fd01e-121">Clones a GitHub repository that includes the Sense HAT quickstart project.</span></span>
- <span data-ttu-id="fd01e-122">Выполняет построение проекта.</span><span class="sxs-lookup"><span data-stu-id="fd01e-122">Builds the project.</span></span>
- <span data-ttu-id="fd01e-123">Запускает проект.</span><span class="sxs-lookup"><span data-stu-id="fd01e-123">Runs the project.</span></span>

<span data-ttu-id="fd01e-124">Выходные данные консоли отображаются в виде данных датчика.</span><span class="sxs-lookup"><span data-stu-id="fd01e-124">Observe the console output as sensor data is displayed.</span></span> <span data-ttu-id="fd01e-125">На светодиодной матрице отображается желтый пиксель на поле синего цвета.</span><span class="sxs-lookup"><span data-stu-id="fd01e-125">The LED matrix displays a yellow pixel on a field of blue.</span></span> <span data-ttu-id="fd01e-126">Если держать джойстик в каком-то направлении, желтый пиксель переместится в этом направлении.</span><span class="sxs-lookup"><span data-stu-id="fd01e-126">Holding the joystick in any direction moves the yellow pixel in that direction.</span></span> <span data-ttu-id="fd01e-127">Если нажать на центральную кнопку джойстика, фон переключится с синего на красный.</span><span class="sxs-lookup"><span data-stu-id="fd01e-127">Clicking the center joystick button causes the background to switch from blue to red.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="fd01e-128">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="fd01e-128">Get the source code</span></span>

<span data-ttu-id="fd01e-129">Исходный код для этого краткого руководства [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span><span class="sxs-lookup"><span data-stu-id="fd01e-129">The source for this quickstart is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fd01e-130">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="fd01e-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd01e-131">Использование GPIO для мигания светодиодного индикатора</span><span class="sxs-lookup"><span data-stu-id="fd01e-131">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
