---
title: Инфраструктура как код
description: Применение инфраструктуры в качестве кода (IaC) с собственными приложениями в облаке
ms.date: 05/13/2020
ms.openlocfilehash: 91e309440cac1c40a3dfa5848d51e87c09340c74
ms.sourcegitcommit: 381b773c9962aca5f8d0b973d0653c0f4edcc4d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2021
ms.locfileid: "108013584"
---
# <a name="infrastructure-as-code"></a>Инфраструктура как код

Облачные системы используют микрослужбы, контейнеры и современные архитектурные системы для достижения максимальной скорости и гибкости. Они предоставляют автоматизированные этапы сборки и выпуска для обеспечения единообразия и качества кода. Но это лишь часть истории. Как подготавливать облачные среды, в которых работают эти системы?

Современные облачные приложения включают в себя широко распространенную методику [инфраструктуры как кода](/azure/devops/learn/what-is-infrastructure-as-code)или `IaC` .  С помощью IaC вы Автоматизируйте подготовку платформы. По сути, вы применяете методики проектирования программного обеспечения, такие как тестирование и управление версиями, в DevOps. Ваша инфраструктура и развертывания являются автоматизированными, постоянными и повторяемыми. Как и при непрерывной доставке, автоматизирована традиционная модель ручных развертываний, а инфраструктура как код (IaC) используется для управления средой приложений.

Такие средства, как Azure Resource Manager (ARM), terraform и интерфейс командной строки Azure (CLI), позволяют декларативно создать скрипт для требуемой облачной инфраструктуры.

## <a name="azure-resource-manager-templates"></a>Шаблоны Azure Resource Manager

ARM означает [Azure Resource Manager](/azure/azure-resource-manager/management/overview). Это подсистема подготовки API, встроенная в Azure и предоставляемая в виде службы API. ARM позволяет развертывать, обновлять, удалять и администрировать ресурсы, содержащиеся в группе ресурсов Azure, в одной координированной операции. Вы предоставляете модулю шаблон на основе JSON, который указывает необходимые ресурсы и их конфигурацию. ARM автоматически управляет развертыванием в правильном порядке соблюдения зависимостей. Подсистема гарантирует идемпотентности. Если нужный ресурс уже существует в той же конфигурации, подготовка будет проигнорирована.

Шаблоны Azure Resource Manager — это язык на основе JSON для определения различных ресурсов в Azure. Основная схема выглядит примерно так, как показано на рис. 10-14.

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

**Рис. 10-14** . схема для шаблона диспетчер ресурсов

В этом шаблоне можно определить контейнер хранилища в разделе ресурсов следующим образом:

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

**Рис. 10-15** . пример учетной записи хранения, определенной в шаблоне диспетчер ресурсов

Шаблон ARM может быть параметризован с помощью динамической среды и сведений о конфигурации. Это позволит использовать его повторно для определения различных сред, таких как разработка, контроль качества или рабочая среда. Как правило, шаблон создает все ресурсы в одной группе ресурсов Azure. При необходимости можно определить несколько групп ресурсов в одном шаблоне диспетчер ресурсов. Вы можете удалить все ресурсы в среде, удалив саму группу ресурсов. Анализ затрат также может выполняться на уровне группы ресурсов, что позволяет быстро учитывать объем данных каждой среды.

Существует множество примеров шаблонов ARM, доступных в проекте шаблонов быстрого запуска [Azure](https://github.com/Azure/azure-quickstart-templates) на сайте GitHub. Они могут помочь ускорить создание нового шаблона или изменение существующего.

Шаблоны диспетчер ресурсов могут выполняться множеством способов. Возможно, самый простой способ — просто вставить их в портал Azure. Для экспериментальных развертываний этот метод может быть быстрым. Они также могут выполняться как часть процесса сборки или выпуска в Azure DevOps. Существуют задачи, которые будут использовать подключения к Azure для запуска шаблонов. Изменения шаблонов диспетчер ресурсов применяются постепенно, то есть для добавления нового ресурса необходимо просто добавить его в шаблон. Средства будут согласовывать различия между текущими ресурсами и теми, которые определены в шаблоне. Ресурсы будут созданы или изменены так, чтобы они совпадали с тем, что определено в шаблоне.  

## <a name="terraform"></a>Terraform

Облачные приложения часто строятся как `cloud agnostic` . Это означает, что приложение не тесно привязано к конкретному поставщику облака и может быть развернуто в любом общедоступном облаке.

[Terraform](https://www.terraform.io/) — это коммерческое средство создания шаблонов, которое позволяет подготавливать облачные приложения для всех основных облачных игроков: Azure, Google Cloud Platform, AWS и аликлауд. Вместо использования JSON в качестве языка определения шаблона он использует немного более сжатый HCL (Hashicorp Configuration Language).

Пример файла terraform, который делает то же, что и предыдущий шаблон диспетчер ресурсов (рис. 10-15), показан на рис. 10-16:

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

**Рис. 10-16** . пример шаблона диспетчер ресурсов

Terraform также предоставляет интуитивно понятные сообщения об ошибках для шаблонов проблем. Также есть удобная задача проверки, которую можно использовать на этапе сборки для перехвата ошибок шаблона на раннем этапе.

Как и в случае с шаблонами диспетчер ресурсов, средства командной строки можно использовать для развертывания шаблонов terraform. Кроме того, в Azure Pipelines есть задачи, созданные сообществом, которые могут проверять и применять шаблоны terraform.

Иногда terraform и шаблоны ARM выводят значимые значения, например строку подключения к вновь созданной базе данных. Эти сведения можно записать в конвейер сборки и использовать в последующих задачах.

## <a name="azure-cli-scripts-and-tasks"></a>Azure CLI сценарии и задачи

Наконец, можно использовать [Azure CLI](/cli/azure/) , чтобы декларативно создать скрипт для облачной инфраструктуры. Сценарии Azure CLI могут быть созданы, найдены и доступны для инициализации и настройки практически любых ресурсов Azure. Интерфейс командной строки прост в использовании с добройой обученной кривой. Скрипты выполняются с помощью PowerShell или bash. Они также просты в отладке, особенно при сравнении с шаблонами ARM.

Azure CLI сценарии хорошо работают, когда необходимо удалить и повторно развернуть инфраструктуру. Обновление существующей среды может быть непростой задачей. Многие команды интерфейса командной строки не идемпотентными. Это означает, что они будут воссоздавать ресурс каждый раз при их запуске, даже если ресурс уже существует. Всегда можно добавить код, который проверяет существование каждого ресурса перед его созданием. Но при этом сценарий может стать чрезмерным и сложным в управлении.

Эти скрипты также можно внедрять в конвейеры DevOps для Azure как `Azure CLI tasks` . Выполнение конвейера вызывает скрипт.

На рис. 10-17 показан фрагмент кода YAML со списком версий Azure CLI и сведений о подписке. Обратите внимание, что команды Azure CLI включены во встроенный скрипт.

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

**Рис. 10-17** . Azure CLI сценарий

В статье понятие " [инфраструктура как код](/azure/devops/learn/what-is-infrastructure-as-code)", автор SAM Гукенхаймера описывает, как "команды, реализующие IaC, могут быстро доставлять стабильные среды и масштабировать их. Команды избегают ручной настройки сред и обеспечивают согласованность, представляя требуемое состояние своих сред с помощью кода. Развертывания инфраструктуры с IaC являются повторяемыми и предотвращают проблемы во время выполнения, вызванные отклонением конфигурации или отсутствием зависимостей. Команды DevOps могут работать вместе с единым набором практических рекомендаций и средств для быстрой и надежной доставки приложений и их поддерживающих инфраструктуры. "

>[!div class="step-by-step"]
>[Назад](feature-flags.md)
>[Вперед](application-bundles.md)
