---
title: Управление микрослужбами и многоконтейнерными приложениями для обеспечения высокого уровня масштабируемости и доступности
description: Сведения о развертывании приложения с помощью службы Azure Kubernetes.
ms.date: 08/06/2020
ms.openlocfilehash: ba9887c0a4837c16a60ebeb006416c0fa8c105e0
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032207"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="aaa6a-103">Развертывание в службе Azure Kubernetes (AKS)</span><span class="sxs-lookup"><span data-stu-id="aaa6a-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="aaa6a-104">Вы можете взаимодействовать с AKS, используя предпочитаемую клиентскую операционную систему (Windows, macOS или Linux) с установленным интерфейсом командной строки Azure (Azure CLI).</span><span class="sxs-lookup"><span data-stu-id="aaa6a-104">You can interact with AKS using your preferred client operating system (Windows, macOS, or Linux) with Azure command-line interface(Azure CLI) installed.</span></span> <span data-ttu-id="aaa6a-105">Дополнительные сведения см. в разделах [Документация по Azure CLI](/cli/azure/?view=azure-cli-latest) и [Руководство по установке](/cli/azure/install-azure-cli?view=azure-cli-latest) для доступных сред.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-105">For more details, refer [Azure CLI documentation](/cli/azure/?view=azure-cli-latest) and [Installation guide](/cli/azure/install-azure-cli?view=azure-cli-latest) for the available environments.</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="aaa6a-106">Создание среды AKS в Azure</span><span class="sxs-lookup"><span data-stu-id="aaa6a-106">Create the AKS environment in Azure</span></span>

<span data-ttu-id="aaa6a-107">Создать среду AKS можно несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-107">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="aaa6a-108">Это можно сделать с помощью команд Azure CLI или портала Azure.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-108">It can be done by using Azure CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="aaa6a-109">Здесь можно ознакомиться с рядом примеров использования Azure CLI для создания кластера и просмотра результатов на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-109">Here you can explore some examples using the Azure CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="aaa6a-110">На компьютере разработки также должны быть установлены Kubectl и Docker.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-110">You also need to have Kubectl and Docker in your development machine.</span></span>

## <a name="create-the-aks-cluster"></a><span data-ttu-id="aaa6a-111">Создание кластера AKS</span><span class="sxs-lookup"><span data-stu-id="aaa6a-111">Create the AKS cluster</span></span>

<span data-ttu-id="aaa6a-112">Создайте кластер AKS с помощью этой команды (должна существовать группа ресурсов):</span><span class="sxs-lookup"><span data-stu-id="aaa6a-112">Create the AKS cluster using this command (the resource group must exist):</span></span>

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> <span data-ttu-id="aaa6a-113">Значений параметров `--node-vm-size` и `--node-count` достаточно для примера приложения или приложения-разработчика.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-113">The `--node-vm-size` and `--node-count` parameter values are good enough for a sample/dev application.</span></span>

<span data-ttu-id="aaa6a-114">По завершении задания по созданию отобразится следующее:</span><span class="sxs-lookup"><span data-stu-id="aaa6a-114">After the creation job finishes, you can see:</span></span>

- <span data-ttu-id="aaa6a-115">Кластер AKS, созданный в начальной группе ресурсов</span><span class="sxs-lookup"><span data-stu-id="aaa6a-115">The AKS cluster created in the initial resource group</span></span>
- <span data-ttu-id="aaa6a-116">Новая связанная группа ресурсов, содержащая ресурсы, связанные с кластером AKS, как показано на следующих изображениях.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-116">A new, related resource group, containing the resources related to the AKS cluster, as show in the following images.</span></span>

<span data-ttu-id="aaa6a-117">Исходная группа ресурсов с кластером AKS:</span><span class="sxs-lookup"><span data-stu-id="aaa6a-117">The initial resource group, with the AKS cluster:</span></span>

![Группа ресурсов AKS в браузере.](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

<span data-ttu-id="aaa6a-119">**Рис. 4-17**.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-119">**Figure 4-17**.</span></span> <span data-ttu-id="aaa6a-120">Группа ресурсов AKS в Azure.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-120">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="aaa6a-121">Группа ресурсов кластера AKS:</span><span class="sxs-lookup"><span data-stu-id="aaa6a-121">The AKS cluster resource group:</span></span>

![Группа ресурсов Azure AKS в браузере.](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

<span data-ttu-id="aaa6a-123">**Рис. 4-18**.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-123">**Figure 4-18**.</span></span> <span data-ttu-id="aaa6a-124">Служба AKS в Azure.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-124">AKS view from Azure.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aaa6a-125">Как правило, изменять ресурсы в группе ресурсов кластера AKS не требуется.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-125">In general, you shouldn't need to modify the resources in the AKS cluster resource group.</span></span> <span data-ttu-id="aaa6a-126">Например, при удалении кластера AKS также удаляется и группа ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-126">For example, the resource group is deleted when you delete the AKS cluster.</span></span>

<span data-ttu-id="aaa6a-127">Созданный узел можно также просмотреть с помощью `Azure CLI` и `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-127">You can also view the node created using `Azure CLI` and `Kubectl`.</span></span>

<span data-ttu-id="aaa6a-128">Сначала получите учетные данные:</span><span class="sxs-lookup"><span data-stu-id="aaa6a-128">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Выходные данные указанной выше команды в консоли: Объединено "explore-docker-aks" в качестве текущего контекста в /home/miguel/.kube/config.](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

<span data-ttu-id="aaa6a-130">**Рис. 4-19**.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-130">**Figure 4-19**.</span></span> <span data-ttu-id="aaa6a-131">Результат команды `aks get-credentials`.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-131">`aks get-credentials` command result.</span></span>

<span data-ttu-id="aaa6a-132">Затем получите узлы из Kubectl:</span><span class="sxs-lookup"><span data-stu-id="aaa6a-132">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Выходные данные указанной выше команды в консоли: Список узлов с состоянием, возрастом (временем выполнения) и версией](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

<span data-ttu-id="aaa6a-134">**Рис. 4-20**.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-134">**Figure 4-20**.</span></span> <span data-ttu-id="aaa6a-135">Результат команды `kubectl get nodes`.</span><span class="sxs-lookup"><span data-stu-id="aaa6a-135">`kubectl get nodes` command result.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="aaa6a-136">[Назад](orchestrate-high-scalability-availability.md)
> [Вперед](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="aaa6a-136">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
