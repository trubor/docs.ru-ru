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
# <a name="how-to-install-gpu-support-in-model-builder"></a>Установка поддержки GPU в Model Builder

Узнайте, как установить драйверы GPU для использования GPU с Model Builder.

## <a name="prerequisites"></a>Предварительные требования

- Расширение Model Builder для Visual Studio. Это расширение встроено в Visual Studio начиная с версии 16.6.1.
- [Расширение Visual Studio для поддержки GPU в Model Builder](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).
- По крайней мере один GPU, совместимый с CUDA. Список совместимых GPU см. в [руководстве компании NVIDIA](https://developer.nvidia.com/cuda-gpus).
- Учетная запись разработчика NVIDIA. Если ее нет, создайте [бесплатную учетную запись](https://developer.nvidia.com/developer-program).

## <a name="install-dependencies"></a>Установка зависимостей

1. Установите [CUDA версии 10.1](https://developer.nvidia.com/cuda-10.1-download-archive-update2). Убедитесь, что вы установили CUDA версии 10.1, а не другую более новую версию. Невозможно установить несколько версий CUDA одновременно.
1. Установите [cuDNN v7.6.4 для CUDA 10.1](https://developer.nvidia.com/rdp/cudnn-download). Невозможно установить несколько версий cuDNN одновременно. После загрузки ZIP-файла с cuDNN v7.6.4 и его распаковки скопируйте файл `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` в папку `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin`.

## <a name="troubleshooting"></a>Устранение неполадок

**Как узнать, какой GPU у меня установлен?**

Следуйте приведенным ниже инструкциям.

1. Щелкните правой кнопкой мыши рабочий стол.
1. Если во всплывающем окне отображается "Панель управления NVIDIA" или "Дисплей NVIDIA", то у вас GPU производства NVIDIA.
1. Щелкните "Панель управления NVIDIA" или "Дисплей NVIDIA" во всплывающем окне.
1. Просмотрите раздел "Сведения о графической карте".
1. Там должно отображаться название вашего GPU NVIDIA.

**Я не вижу панель управления NVIDIA (или ее не удается открыть), но знаю, что у меня GPU NVIDIA.**

1. Откройте диспетчер устройств.
1. Просмотрите раздел "Видеоадаптеры".
1. Установите соответствующий [драйвер](https://www.nvidia.com/drivers) для своего GPU.
