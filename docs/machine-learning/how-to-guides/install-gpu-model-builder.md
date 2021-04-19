---
title: Установка поддержки GPU в Model Builder
description: Узнайте, как установить поддержку GPU в Model Builder
ms.date: 04/08/2021
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: 81f84a17429fd03506bbce30f5646941e4e80b3b
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255432"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a><span data-ttu-id="55f84-103">Установка поддержки GPU в Model Builder</span><span class="sxs-lookup"><span data-stu-id="55f84-103">How to install GPU support in Model Builder</span></span>

<span data-ttu-id="55f84-104">Узнайте, как установить драйверы GPU для использования GPU с Model Builder.</span><span class="sxs-lookup"><span data-stu-id="55f84-104">Learn how to install the GPU drivers to use your GPU with Model Builder.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55f84-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="55f84-105">Prerequisites</span></span>

- <span data-ttu-id="55f84-106">Расширение Model Builder для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55f84-106">Model Builder Visual Studio extension.</span></span> <span data-ttu-id="55f84-107">Это расширение встроено в Visual Studio начиная с версии 16.6.1.</span><span class="sxs-lookup"><span data-stu-id="55f84-107">The extension is built into Visual Studio as of version 16.6.1.</span></span>
- <span data-ttu-id="55f84-108">[Расширение Visual Studio для поддержки GPU в Model Builder](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span><span class="sxs-lookup"><span data-stu-id="55f84-108">[Model Builder Visual Studio GPU support extension](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span></span>
- <span data-ttu-id="55f84-109">По крайней мере один GPU, совместимый с CUDA.</span><span class="sxs-lookup"><span data-stu-id="55f84-109">At least one CUDA compatible GPU.</span></span> <span data-ttu-id="55f84-110">Список совместимых GPU см. в [руководстве компании NVIDIA](https://developer.nvidia.com/cuda-gpus).</span><span class="sxs-lookup"><span data-stu-id="55f84-110">For a list of compatible GPUs, see [NVIDIA's guide](https://developer.nvidia.com/cuda-gpus).</span></span>
- <span data-ttu-id="55f84-111">Учетная запись разработчика NVIDIA.</span><span class="sxs-lookup"><span data-stu-id="55f84-111">NVIDIA developer account.</span></span> <span data-ttu-id="55f84-112">Если ее нет, создайте [бесплатную учетную запись](https://developer.nvidia.com/developer-program).</span><span class="sxs-lookup"><span data-stu-id="55f84-112">If you don't have one, [create a free account](https://developer.nvidia.com/developer-program).</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="55f84-113">Установка зависимостей</span><span class="sxs-lookup"><span data-stu-id="55f84-113">Install dependencies</span></span>

1. <span data-ttu-id="55f84-114">Установите [CUDA версии 10.1](https://developer.nvidia.com/cuda-10.1-download-archive-update2).</span><span class="sxs-lookup"><span data-stu-id="55f84-114">Install [CUDA v10.1](https://developer.nvidia.com/cuda-10.1-download-archive-update2).</span></span> <span data-ttu-id="55f84-115">Убедитесь, что вы установили CUDA версии 10.1, а не другую более новую версию.</span><span class="sxs-lookup"><span data-stu-id="55f84-115">Make sure you install CUDA v10.1, not any other newer version.</span></span> <span data-ttu-id="55f84-116">Невозможно установить несколько версий CUDA одновременно.</span><span class="sxs-lookup"><span data-stu-id="55f84-116">You cannot have multiple versions of CUDA installed.</span></span>
1. <span data-ttu-id="55f84-117">Установите [cuDNN v7.6.4 для CUDA 10.1](https://developer.nvidia.com/rdp/cudnn-download).</span><span class="sxs-lookup"><span data-stu-id="55f84-117">Install [cuDNN v7.6.4 for CUDA 10.1](https://developer.nvidia.com/rdp/cudnn-download).</span></span> <span data-ttu-id="55f84-118">Невозможно установить несколько версий cuDNN одновременно.</span><span class="sxs-lookup"><span data-stu-id="55f84-118">You cannot have multiple versions of cuDNN installed.</span></span> <span data-ttu-id="55f84-119">После загрузки ZIP-файла с cuDNN v7.6.4 и его распаковки скопируйте файл `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` в папку `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin`.</span><span class="sxs-lookup"><span data-stu-id="55f84-119">After downloading cuDNN v7.6.4 zip file and unpacking it, copy `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` to `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin`.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="55f84-120">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="55f84-120">Troubleshooting</span></span>

<span data-ttu-id="55f84-121">**Как узнать, какой GPU у меня установлен?**</span><span class="sxs-lookup"><span data-stu-id="55f84-121">**How do I know what GPU I have?**</span></span>

<span data-ttu-id="55f84-122">Следуйте приведенным ниже инструкциям.</span><span class="sxs-lookup"><span data-stu-id="55f84-122">Follow instructions provided:</span></span>

1. <span data-ttu-id="55f84-123">Щелкните правой кнопкой мыши рабочий стол.</span><span class="sxs-lookup"><span data-stu-id="55f84-123">Right-click on desktop</span></span>
1. <span data-ttu-id="55f84-124">Если во всплывающем окне отображается "Панель управления NVIDIA" или "Дисплей NVIDIA", то у вас GPU производства NVIDIA.</span><span class="sxs-lookup"><span data-stu-id="55f84-124">If you see "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window, you have an NVIDIA GPU</span></span>
1. <span data-ttu-id="55f84-125">Щелкните "Панель управления NVIDIA" или "Дисплей NVIDIA" во всплывающем окне.</span><span class="sxs-lookup"><span data-stu-id="55f84-125">Click on "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window</span></span>
1. <span data-ttu-id="55f84-126">Просмотрите раздел "Сведения о графической карте".</span><span class="sxs-lookup"><span data-stu-id="55f84-126">Look at "Graphics Card Information"</span></span>
1. <span data-ttu-id="55f84-127">Там должно отображаться название вашего GPU NVIDIA.</span><span class="sxs-lookup"><span data-stu-id="55f84-127">You will see the name of your NVIDIA GPU</span></span>

<span data-ttu-id="55f84-128">**Я не вижу панель управления NVIDIA (или ее не удается открыть), но знаю, что у меня GPU NVIDIA.**</span><span class="sxs-lookup"><span data-stu-id="55f84-128">**I don't see NVIDIA Control Panel (or it fails to open) but I know I have an NVIDIA GPU.**</span></span>

1. <span data-ttu-id="55f84-129">Откройте диспетчер устройств.</span><span class="sxs-lookup"><span data-stu-id="55f84-129">Open Device Manager</span></span>
1. <span data-ttu-id="55f84-130">Просмотрите раздел "Видеоадаптеры".</span><span class="sxs-lookup"><span data-stu-id="55f84-130">Look at Display adapters</span></span>
1. <span data-ttu-id="55f84-131">Установите соответствующий [драйвер](https://www.nvidia.com/drivers) для своего GPU.</span><span class="sxs-lookup"><span data-stu-id="55f84-131">Install appropriate [driver](https://www.nvidia.com/drivers) for your GPU.</span></span>
