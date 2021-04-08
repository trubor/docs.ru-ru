---
title: Выбор вычислительных платформ Azure для контейнерных приложений
description: Модернизация существующих приложений .NET с помощью облака Azure и контейнеров Windows | Выбор вычислительных платформ Azure для контейнерных приложений
ms.date: 02/18/2020
ms.openlocfilehash: fcb9a0e7277f5ce31309f52aff63d579b0bb9a02
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079613"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Выбор вычислительных платформ Azure для контейнерных приложений

Как вы заметили после ознакомления с предыдущими разделами, Azure — это открытое облако, предлагающее различные варианты. Вы можете подобрать самый подходящий для ваших нужд, но вам также нужно будет выбрать продукты или технологии, которые следует использовать для контейнерных приложений.

Ниже приведены основные критерии, по которым *рекомендуется* выбирать подходящее решение.

- **Единое монолитное приложение.** Выбор службы приложений Azure
- **N-уровневое приложение.** Выберите такие оркестрации, как Служба Azure Kubernetes (AKS) или Служба приложений, если у вас одна или несколько серверных служб.
- **Микрослужбы.** Выберите AKS или Веб-приложения Azure для контейнеров.
- **Бессерверные функции и обработчики событий.** Выберите Функции Azure.
- **Широкомасштабная пакетная обработка.** Выберите пакетную службу Azure.

Однако не следует слепо следовать этой рекомендации, так как выбор продукта зависит от потребностей и характеристик конкретного приложения. Не все приложения одинаковы, даже если изначально они могут выглядеть похожими.

После углубленного анализа потребностей приложения изначальный и конечный выбранные продукты могут отличаться. Но в качестве отправной точки полезно иметь начальные рекомендации относительно того, где можно начать оценку и тестирование в зависимости от определенного приоритета.

В приведенной ниже таблице различные виды приложений сопоставлены с их возможными и рекомендуемыми сценариями размещения в Azure.

| Архитектура приложения | Виртуальные машины Azure | ACI — Экземпляры контейнеров Azure | Служба приложений Azure (с контейнерами и без них) | AKS — Служба Azure Kubernetes | Проверка | Пакетная служба Azure |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Веб-приложения (монолитные)**         | ![Возможный сценарий с использованием виртуальных машин](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Возможный сценарий с использованием ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Рекомендуемый сценарий с использованием Службы приложений](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Возможный сценарий с использованием AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **N-уровневые приложения (службы)**        | ![Возможный сценарий с использованием виртуальных машин](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Возможный сценарий с использованием ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Рекомендуемый сценарий с использованием Службы приложений](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Возможный сценарий с использованием AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Возможный сценарий с использованием Функций Azure](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Ориентированные на облако приложения (микрослужбы)**  | | ![Возможный сценарий с использованием ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Возможный сценарий с использованием ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) <br/> (С&nbsp;контейнерами) | ![Рекомендуемый сценарий с использованием AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Контейнеры&nbsp;Linux)| ![Рекомендуемый сценарий с использованием Функций Azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (На основе событий) | |
| **Пакетная обработки и задания (фоновые задачи)** | ![Возможный сценарий с использованием виртуальных машин](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Возможный сценарий с использованием ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Возможный сценарий с использованием Службы приложений](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Возможный сценарий с использованием AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Рекомендуемый сценарий с использованием Функций Azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Фоновые&nbsp;задачи) | ![Возможный сценарий с использованием пакетной службы Azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Большой масштаб) |

**Условные обозначения**

![Значок рекомендуемого сценария](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Рекомендуемый сценарий \
![Значок возможного сценария](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Возможна

### <a name="additional-resources"></a>Дополнительные ресурсы

- **Выбор вычислительной службы Azure для приложения**

    <https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree>

> [!div class="step-by-step"]
> [Назад](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Вперед](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
