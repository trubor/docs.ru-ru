---
title: Инфраструктура как код
description: Применение инфраструктуры в качестве кода (IaC) с собственными приложениями в облаке
ms.date: 05/13/2020
ms.openlocfilehash: 5a7cd3a0b4906b1a4aec9e1015d6128867ae9963
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255448"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="f8a2f-103">Инфраструктура как код</span><span class="sxs-lookup"><span data-stu-id="f8a2f-103">Infrastructure as code</span></span>

<span data-ttu-id="f8a2f-104">Облачные системы используют микрослужбы, контейнеры и современные архитектурные системы для достижения максимальной скорости и гибкости.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="f8a2f-105">Они предоставляют автоматизированные этапы сборки и выпуска для обеспечения единообразия и качества кода.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="f8a2f-106">Но это лишь часть истории.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-106">But, that's only part of the story.</span></span> <span data-ttu-id="f8a2f-107">Как подготавливать облачные среды, в которых работают эти системы?</span><span class="sxs-lookup"><span data-stu-id="f8a2f-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="f8a2f-108">Современные облачные приложения включают в себя широко распространенную методику [инфраструктуры как кода](/azure/devops/learn/what-is-infrastructure-as-code)или `IaC` .</span><span class="sxs-lookup"><span data-stu-id="f8a2f-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="f8a2f-109">С помощью IaC вы Автоматизируйте подготовку платформы.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="f8a2f-110">По сути, вы применяете методики проектирования программного обеспечения, такие как тестирование и управление версиями, в DevOps.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="f8a2f-111">Ваша инфраструктура и развертывания являются автоматизированными, постоянными и повторяемыми.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="f8a2f-112">Как и при непрерывной доставке, автоматизирована традиционная модель ручных развертываний, а инфраструктура как код (IaC) используется для управления средой приложений.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="f8a2f-113">Такие средства, как Azure Resource Manager (ARM), terraform и интерфейс командной строки Azure (CLI), позволяют декларативно создать скрипт для требуемой облачной инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="f8a2f-114">Шаблоны Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="f8a2f-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="f8a2f-115">ARM означает [Azure Resource Manager](/azure/azure-resource-manager/management/overview).</span><span class="sxs-lookup"><span data-stu-id="f8a2f-115">ARM stands for [Azure Resource Manager](/azure/azure-resource-manager/management/overview).</span></span> <span data-ttu-id="f8a2f-116">Это подсистема подготовки API, встроенная в Azure и предоставляемая в виде службы API.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="f8a2f-117">ARM позволяет развертывать, обновлять, удалять и администрировать ресурсы, содержащиеся в группе ресурсов Azure, в одной координированной операции.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="f8a2f-118">Вы предоставляете модулю шаблон на основе JSON, который указывает необходимые ресурсы и их конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="f8a2f-119">ARM автоматически управляет развертыванием в правильном порядке соблюдения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="f8a2f-120">Подсистема гарантирует идемпотентности.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-120">The engine ensures idempotency.</span></span> <span data-ttu-id="f8a2f-121">Если нужный ресурс уже существует в той же конфигурации, подготовка будет проигнорирована.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="f8a2f-122">Шаблоны Azure Resource Manager — это язык на основе JSON для определения различных ресурсов в Azure.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="f8a2f-123">Основная схема выглядит примерно так, как показано на рис. 10-14.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-123">The basic schema looks something like Figure 10-14.</span></span>

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

<span data-ttu-id="f8a2f-124">**Рис. 10-14** . схема для шаблона диспетчер ресурсов</span><span class="sxs-lookup"><span data-stu-id="f8a2f-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="f8a2f-125">В этом шаблоне можно определить контейнер хранилища в разделе ресурсов следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f8a2f-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

<span data-ttu-id="f8a2f-126">**Рис. 10-15** . пример учетной записи хранения, определенной в шаблоне диспетчер ресурсов</span><span class="sxs-lookup"><span data-stu-id="f8a2f-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="f8a2f-127">Шаблон ARM может быть параметризован с помощью динамической среды и сведений о конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="f8a2f-128">Это позволит использовать его повторно для определения различных сред, таких как разработка, контроль качества или рабочая среда.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="f8a2f-129">Как правило, шаблон создает все ресурсы в одной группе ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="f8a2f-130">При необходимости можно определить несколько групп ресурсов в одном шаблоне диспетчер ресурсов.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="f8a2f-131">Вы можете удалить все ресурсы в среде, удалив саму группу ресурсов.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="f8a2f-132">Анализ затрат также может выполняться на уровне группы ресурсов, что позволяет быстро учитывать объем данных каждой среды.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="f8a2f-133">Существует множество примеров шаблонов ARM, доступных в проекте шаблонов быстрого запуска [Azure](https://github.com/Azure/azure-quickstart-templates) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-133">There are many examples of ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="f8a2f-134">Они могут помочь ускорить создание нового шаблона или изменение существующего.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="f8a2f-135">Шаблоны диспетчер ресурсов могут выполняться множеством способов.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="f8a2f-136">Возможно, самый простой способ — просто вставить их в портал Azure.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="f8a2f-137">Для экспериментальных развертываний этот метод может быть быстрым.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="f8a2f-138">Они также могут выполняться как часть процесса сборки или выпуска в Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="f8a2f-139">Существуют задачи, которые будут использовать подключения к Azure для запуска шаблонов.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="f8a2f-140">Изменения шаблонов диспетчер ресурсов применяются постепенно, то есть для добавления нового ресурса необходимо просто добавить его в шаблон.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="f8a2f-141">Средства будут согласовывать различия между текущими ресурсами и теми, которые определены в шаблоне.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="f8a2f-142">Ресурсы будут созданы или изменены так, чтобы они совпадали с тем, что определено в шаблоне.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="f8a2f-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="f8a2f-143">Terraform</span></span>

<span data-ttu-id="f8a2f-144">Облачные приложения часто строятся как `cloud agnostic` .</span><span class="sxs-lookup"><span data-stu-id="f8a2f-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="f8a2f-145">Это означает, что приложение не тесно привязано к конкретному поставщику облака и может быть развернуто в любом общедоступном облаке.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="f8a2f-146">[Terraform](https://www.terraform.io/) — это средство создания коммерческих шаблонов, которое позволяет подготавливать облачные приложения для всех основных облачных игроков: Azure, Google Cloud Platform, AWS и аликлауд.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="f8a2f-147">Вместо использования JSON в качестве языка определения шаблона он использует немного более сжатый YAML.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="f8a2f-148">Пример файла terraform, который делает то же, что и предыдущий шаблон диспетчер ресурсов (рис. 10-15), показан на рис. 10-16:</span><span class="sxs-lookup"><span data-stu-id="f8a2f-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

<span data-ttu-id="f8a2f-149">**Рис. 10-16** . пример шаблона диспетчер ресурсов</span><span class="sxs-lookup"><span data-stu-id="f8a2f-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="f8a2f-150">Terraform также предоставляет интуитивно понятные сообщения об ошибках для шаблонов проблем.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="f8a2f-151">Также есть удобная задача проверки, которую можно использовать на этапе сборки для перехвата ошибок шаблона на раннем этапе.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="f8a2f-152">Как и в случае с шаблонами диспетчер ресурсов, средства командной строки можно использовать для развертывания шаблонов terraform.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="f8a2f-153">Кроме того, в Azure Pipelines есть задачи, созданные сообществом, которые могут проверять и применять шаблоны terraform.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="f8a2f-154">Иногда terraform и шаблоны ARM выводят значимые значения, например строку подключения к вновь созданной базе данных.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="f8a2f-155">Эти сведения можно записать в конвейер сборки и использовать в последующих задачах.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="f8a2f-156">Azure CLI сценарии и задачи</span><span class="sxs-lookup"><span data-stu-id="f8a2f-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="f8a2f-157">Наконец, можно использовать [Azure CLI](/cli/azure/) , чтобы декларативно создать скрипт для облачной инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-157">Finally, you can leverage [Azure CLI](/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="f8a2f-158">Сценарии Azure CLI могут быть созданы, найдены и доступны для инициализации и настройки практически любых ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="f8a2f-159">Интерфейс командной строки прост в использовании с добройой обученной кривой.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="f8a2f-160">Скрипты выполняются с помощью PowerShell или bash.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="f8a2f-161">Они также просты в отладке, особенно при сравнении с шаблонами ARM.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="f8a2f-162">Azure CLI сценарии хорошо работают, когда необходимо удалить и повторно развернуть инфраструктуру.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="f8a2f-163">Обновление существующей среды может быть непростой задачей.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="f8a2f-164">Многие команды интерфейса командной строки не идемпотентными.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="f8a2f-165">Это означает, что они будут воссоздавать ресурс каждый раз при их запуске, даже если ресурс уже существует.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="f8a2f-166">Всегда можно добавить код, который проверяет существование каждого ресурса перед его созданием.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="f8a2f-167">Но при этом сценарий может стать чрезмерным и сложным в управлении.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="f8a2f-168">Эти скрипты также можно внедрять в конвейеры DevOps для Azure как `Azure CLI tasks` .</span><span class="sxs-lookup"><span data-stu-id="f8a2f-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="f8a2f-169">Выполнение конвейера вызывает скрипт.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="f8a2f-170">На рис. 10-17 показан фрагмент кода YAML со списком версий Azure CLI и сведений о подписке.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="f8a2f-171">Обратите внимание, что команды Azure CLI включены во встроенный скрипт.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-171">Note how Azure CLI commands are included in an inline script.</span></span>

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

<span data-ttu-id="f8a2f-172">**Рис. 10-17** . Azure CLI сценарий</span><span class="sxs-lookup"><span data-stu-id="f8a2f-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="f8a2f-173">В статье понятие " [инфраструктура как код](/azure/devops/learn/what-is-infrastructure-as-code)", автор SAM Гукенхаймера описывает, как "команды, реализующие IaC, могут быстро доставлять стабильные среды и масштабировать их.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-173">In the article, [What is Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="f8a2f-174">Команды избегают ручной настройки сред и обеспечивают согласованность, представляя требуемое состояние своих сред с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="f8a2f-175">Развертывания инфраструктуры с IaC являются повторяемыми и предотвращают проблемы во время выполнения, вызванные отклонением конфигурации или отсутствием зависимостей.</span><span class="sxs-lookup"><span data-stu-id="f8a2f-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="f8a2f-176">Команды DevOps могут работать вместе с единым набором практических рекомендаций и средств для быстрой и надежной доставки приложений и их поддерживающих инфраструктуры. "</span><span class="sxs-lookup"><span data-stu-id="f8a2f-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f8a2f-177">[Назад](feature-flags.md)
>[Вперед](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="f8a2f-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
