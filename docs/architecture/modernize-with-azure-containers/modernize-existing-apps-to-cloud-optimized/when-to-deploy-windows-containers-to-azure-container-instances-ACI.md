---
title: Когда следует развертывать контейнеры Windows в службе "Экземпляры контейнеров Azure" (ACI)
description: Модернизация существующих приложений .NET с помощью облака Azure и контейнеров Windows | Когда следует развертывать контейнеры Windows в службе "Экземпляры контейнеров Azure" (ACI)
ms.date: 12/21/2020
ms.openlocfilehash: 556fe7cbec7d259db9ec886b777feda9eed09116
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025137"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="c2dad-103">Когда следует развертывать контейнеры Windows в службе "Экземпляры контейнеров Azure" (ACI)</span><span class="sxs-lookup"><span data-stu-id="c2dad-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="c2dad-104">Основное предлагаемое преимущество службы "Экземпляры контейнеров Azure" заключается в том, что вы можете сразу же развернуть в ней контейнеры и вам не нужно поддерживать эту среду, обновлять или исправлять базовую операционную систему или виртуальные машины. Все это является прозрачным, и вы просто развертываете контейнеры в готовом к использованию окружении.</span><span class="sxs-lookup"><span data-stu-id="c2dad-104">The main value proposition of Azure Container Instances is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="c2dad-105">Причины и сценарии использования ACI похожи на основные сценарии применения виртуальных машин Azure с контейнерами. Основные сценарии такие:</span><span class="sxs-lookup"><span data-stu-id="c2dad-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="c2dad-106">**сценарии разработки и тестирования**;</span><span class="sxs-lookup"><span data-stu-id="c2dad-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="c2dad-107">**Автоматизация задач**</span><span class="sxs-lookup"><span data-stu-id="c2dad-107">**Task automation**</span></span>
- <span data-ttu-id="c2dad-108">**агенты CI/CD**;</span><span class="sxs-lookup"><span data-stu-id="c2dad-108">**CI/CD agents**</span></span>
- <span data-ttu-id="c2dad-109">**небольшая масштабируемая пакетная обработка**;</span><span class="sxs-lookup"><span data-stu-id="c2dad-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="c2dad-110">**простые веб-приложения**.</span><span class="sxs-lookup"><span data-stu-id="c2dad-110">**Simple web apps**</span></span>

<span data-ttu-id="c2dad-111">Простой сценарий использования веб-приложений подходит для ACI, но нужно учитывать, что, так как в ACI вы можете иметь только один экземпляр контейнера для каждого образа контейнера, вы не сможете обеспечить высокий уровень доступности и получите только ограниченную масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="c2dad-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="c2dad-112">Тем не менее, хотя ACI считается инфраструктурой, потому что она просто предоставляет отдельные экземпляры контейнеров, она предоставляет огромное преимущество по сравнению с обычными виртуальными машинами Azure с Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c2dad-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="c2dad-113">При использовании ACI вы просто развертываете контейнеры в среде самообслуживания и просто платите за эти контейнеры.</span><span class="sxs-lookup"><span data-stu-id="c2dad-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="c2dad-114">Вам не нужно поддерживать, обновлять и исправлять виртуальные машины, поэтому это гораздо лучшая платформа для большинства сценариев, в которых могут задействоваться виртуальные машины с контейнерами.</span><span class="sxs-lookup"><span data-stu-id="c2dad-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="c2dad-115">Использовать ACI очень просто: вы просто развертываете контейнер, и вам не нужно создавать среду виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="c2dad-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="c2dad-116">Служба "Экземпляры контейнеров Azure" (ACI) обладает такими основными преимуществами:</span><span class="sxs-lookup"><span data-stu-id="c2dad-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="c2dad-117">выполнение контейнеров без управления серверами;</span><span class="sxs-lookup"><span data-stu-id="c2dad-117">Run containers without managing servers</span></span>
- <span data-ttu-id="c2dad-118">повышение гибкости благодаря возможности предоставлять контейнеры по требованию;</span><span class="sxs-lookup"><span data-stu-id="c2dad-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="c2dad-119">развертывание контейнеров в облаке с непревзойденной простотой и скоростью — с помощью одной команды;</span><span class="sxs-lookup"><span data-stu-id="c2dad-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="c2dad-120">защита приложений за счет изоляции гипервизора.</span><span class="sxs-lookup"><span data-stu-id="c2dad-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="c2dad-121">Вкратце, с ACI вы можете быстро разрабатывать приложения без необходимости управлять виртуальными машинами или изучать новые средства.</span><span class="sxs-lookup"><span data-stu-id="c2dad-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="c2dad-122">Это просто ваше приложение в контейнере, выполняющемся в облаке.</span><span class="sxs-lookup"><span data-stu-id="c2dad-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="c2dad-123">[Назад](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Вперед](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="c2dad-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
