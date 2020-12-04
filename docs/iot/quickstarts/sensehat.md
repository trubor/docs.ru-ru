---
title: Краткое руководство. использование .NET для работы с Raspberry Пи (*)
description: Приступите к работе с библиотеками .NET IoT за 5 минут с помощью встроенной платы для Raspberry Pi.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 09e0c46a08e08a2021a9dffe214d3d62d6fb8ec5
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2020
ms.locfileid: "96594026"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a><span data-ttu-id="24dc7-103">Краткое руководство. использование .NET для работы с Raspberry Пи (\*)</span><span class="sxs-lookup"><span data-stu-id="24dc7-103">Quickstart - Use .NET to drive a Raspberry Pi Sense HAT</span></span>

<span data-ttu-id="24dc7-104">Датчик Raspberry Pi [Hat](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> — это надстройка для Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="24dc7-104">The Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> is an add-on board for Raspberry Pi.</span></span> <span data-ttu-id="24dc7-105">У точки зрения установлена схема ИНДИКАТОРов RGB размером 8 × 8, джойстик с пятью кнопками, а также следующие датчики:</span><span class="sxs-lookup"><span data-stu-id="24dc7-105">The Sense HAT is equipped with an 8×8 RGB LED matrix, a five-button joystick, and includes the following sensors:</span></span>

- <span data-ttu-id="24dc7-106">Гироскоп</span><span class="sxs-lookup"><span data-stu-id="24dc7-106">Gyroscope</span></span>
- <span data-ttu-id="24dc7-107">Акселерометр</span><span class="sxs-lookup"><span data-stu-id="24dc7-107">Accelerometer</span></span>
- <span data-ttu-id="24dc7-108">Магнитометр</span><span class="sxs-lookup"><span data-stu-id="24dc7-108">Magnetometer</span></span>
- <span data-ttu-id="24dc7-109">температура;</span><span class="sxs-lookup"><span data-stu-id="24dc7-109">Temperature</span></span>
- <span data-ttu-id="24dc7-110">Barometric pressure давление</span><span class="sxs-lookup"><span data-stu-id="24dc7-110">Barometric pressure</span></span>
- <span data-ttu-id="24dc7-111">влажность.</span><span class="sxs-lookup"><span data-stu-id="24dc7-111">Humidity</span></span>

<span data-ttu-id="24dc7-112">В этом кратком руководстве используется платформа .NET для извлечения значений датчиков с точки зрения, ответа на джойстик и последующей работы с матрицей индикатора.</span><span class="sxs-lookup"><span data-stu-id="24dc7-112">This quickstart uses .NET to retrieve sensor values from the Sense HAT, respond to joystick input, and drive the LED matrix.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24dc7-113">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="24dc7-113">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="24dc7-114">Сенсорная HAT</span><span class="sxs-lookup"><span data-stu-id="24dc7-114">Sense HAT</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a><span data-ttu-id="24dc7-115">Запуск краткого руководства</span><span class="sxs-lookup"><span data-stu-id="24dc7-115">Run the quickstart</span></span>

<span data-ttu-id="24dc7-116">Прикрепите к Raspberry Pi сенсорную HAT.</span><span class="sxs-lookup"><span data-stu-id="24dc7-116">Attach the Sense HAT to your Raspberry Pi.</span></span> <span data-ttu-id="24dc7-117">В командной строке Bash в Raspberry Pi (локальный или удаленный) выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="24dc7-117">From a Bash prompt on the Raspberry Pi (local or remote), run the following command:</span></span>

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

<span data-ttu-id="24dc7-118">Команда скачивает и запускает скрипт.</span><span class="sxs-lookup"><span data-stu-id="24dc7-118">The command downloads and runs a script.</span></span> <span data-ttu-id="24dc7-119">Сценарий:</span><span class="sxs-lookup"><span data-stu-id="24dc7-119">The script:</span></span>

- <span data-ttu-id="24dc7-120">Устанавливает пакет SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="24dc7-120">Installs the .NET SDK.</span></span>
- <span data-ttu-id="24dc7-121">Клонирование репозитория GitHub, включающего проект быстрого запуска на базе примеров.</span><span class="sxs-lookup"><span data-stu-id="24dc7-121">Clones a GitHub repository that includes the Sense HAT quickstart project.</span></span>
- <span data-ttu-id="24dc7-122">Выполняет построение проекта.</span><span class="sxs-lookup"><span data-stu-id="24dc7-122">Builds the project.</span></span>
- <span data-ttu-id="24dc7-123">Запускает проект.</span><span class="sxs-lookup"><span data-stu-id="24dc7-123">Runs the project.</span></span>

<span data-ttu-id="24dc7-124">Обратите внимание, что вывод консоли отображается в виде данных датчика.</span><span class="sxs-lookup"><span data-stu-id="24dc7-124">Observe the console output as sensor data is displayed.</span></span> <span data-ttu-id="24dc7-125">В матрице ИНДИКАТОРов отображается желтый пиксель на поле синего цвета.</span><span class="sxs-lookup"><span data-stu-id="24dc7-125">The LED matrix displays a yellow pixel on a field of blue.</span></span> <span data-ttu-id="24dc7-126">Удержание джойстика в любом направлении перемещает желтый пиксел в этом направлении.</span><span class="sxs-lookup"><span data-stu-id="24dc7-126">Holding the joystick in any direction moves the yellow pixel in that direction.</span></span> <span data-ttu-id="24dc7-127">Щелчок Центральной джойстика приводит к переключению фона с синего на красный.</span><span class="sxs-lookup"><span data-stu-id="24dc7-127">Clicking the center joystick button causes the background to switch from blue to red.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="24dc7-128">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="24dc7-128">Get the source code</span></span>

<span data-ttu-id="24dc7-129">Источник этого краткого руководства [доступен на сайте GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span><span class="sxs-lookup"><span data-stu-id="24dc7-129">The source for this quickstart is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span></span> <span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="next-steps"></a><span data-ttu-id="24dc7-130">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="24dc7-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="24dc7-131">Научитесь использовать общего назначения ввода-вывода для мигания индикатора</span><span class="sxs-lookup"><span data-stu-id="24dc7-131">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
