---
title: Пакеты приложений, ориентированных на облако
description: Создание архитектуры облачных приложений .NET для Azure | Пакеты облачных приложений машинного кода
ms.date: 01/19/2021
ms.openlocfilehash: d3427ddf82b65dd274ef253749a9b87864092a0a
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506140"
---
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="6335a-103">Пакеты приложений, ориентированных на облако</span><span class="sxs-lookup"><span data-stu-id="6335a-103">Cloud Native Application Bundles</span></span>

<span data-ttu-id="6335a-104">Ключевым свойством облачных приложений является то, что они используют возможности облака для ускорения разработки.</span><span class="sxs-lookup"><span data-stu-id="6335a-104">A key property of cloud-native applications is that they leverage the capabilities of the cloud to speed up development.</span></span> <span data-ttu-id="6335a-105">Такая схема часто означает, что в полном приложении используются различные виды технологий.</span><span class="sxs-lookup"><span data-stu-id="6335a-105">This design often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="6335a-106">Приложения могут поставляться в контейнерах DOCKER. Некоторые службы могут использовать функции Azure, тогда как другие могут работать непосредственно с виртуальными машинами, выделенными на больших серверах с аппаратным ускорением GPU.</span><span class="sxs-lookup"><span data-stu-id="6335a-106">Applications may be shipped in Docker containers, some services may use Azure Functions, while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="6335a-107">Ни одно из двух собственных приложений в облаке не одинаково, поэтому было сложно предоставить единый механизм для их отправки.</span><span class="sxs-lookup"><span data-stu-id="6335a-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="6335a-108">Контейнеры DOCKER могут выполняться в Kubernetes с помощью диаграммы Helm для развертывания.</span><span class="sxs-lookup"><span data-stu-id="6335a-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="6335a-109">Функции Azure можно выделить с помощью шаблонов terraform.</span><span class="sxs-lookup"><span data-stu-id="6335a-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="6335a-110">Наконец, виртуальные машины могут быть выделены с помощью terraform, но созданы с помощью Ansible.</span><span class="sxs-lookup"><span data-stu-id="6335a-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="6335a-111">Это большое разнообразие технологий, и нет возможности упаковать их вместе в разумный пакет.</span><span class="sxs-lookup"><span data-stu-id="6335a-111">This is a large variety of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="6335a-112">До настоящего момента.</span><span class="sxs-lookup"><span data-stu-id="6335a-112">Until now.</span></span>

<span data-ttu-id="6335a-113">Облачные пакеты приложений (КНАБС) являются совместными усилиями многих компаний, таких как Microsoft, Docker и HashiCorp, для разработки спецификации для упаковки распределенных приложений.</span><span class="sxs-lookup"><span data-stu-id="6335a-113">Cloud Native Application Bundles (CNABs) are a joint effort by many community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="6335a-114">Усилия были объявлены в декабре 2018, поэтому по-прежнему остается довольно много усилий, чтобы сделать работу с большим сообществом.</span><span class="sxs-lookup"><span data-stu-id="6335a-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="6335a-115">Однако уже есть [Открытая спецификация](https://github.com/deislabs/cnab-spec) и эталонная реализация, известная как [сумку](https://duffle.sh/).</span><span class="sxs-lookup"><span data-stu-id="6335a-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="6335a-116">Это средство, написанное на Go, является совместным усилиями между DOCKER и Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="6335a-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="6335a-117">КНАБС может содержать различные технологии установки.</span><span class="sxs-lookup"><span data-stu-id="6335a-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="6335a-118">Этот аспект позволяет Helm диаграммам, шаблонам terraform и Ansible модули PlayBook сосуществовать в одном пакете.</span><span class="sxs-lookup"><span data-stu-id="6335a-118">This aspect allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="6335a-119">После сборки пакеты являются автономными и переносимыми. их можно установить с USB-носителя.</span><span class="sxs-lookup"><span data-stu-id="6335a-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="6335a-120">Пакеты криптографически подписываются, чтобы убедиться, что они берутся из утвержденной им стороны.</span><span class="sxs-lookup"><span data-stu-id="6335a-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="6335a-121">Ядром КНАБ является файл с именем `bundle.json` .</span><span class="sxs-lookup"><span data-stu-id="6335a-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="6335a-122">Этот файл определяет содержимое пакета, terraform или изображения или что-либо другое.</span><span class="sxs-lookup"><span data-stu-id="6335a-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="6335a-123">На рис. 11-9 определен КНАБ, вызывающий некоторые terraform.</span><span class="sxs-lookup"><span data-stu-id="6335a-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="6335a-124">Однако обратите внимание, что он фактически определяет изображение вызова, которое используется для вызова terraform.</span><span class="sxs-lookup"><span data-stu-id="6335a-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="6335a-125">При создании пакета файл DOCKER, расположенный в каталоге *КНАБ* , встроен в образ DOCKER, который будет включен в пакет.</span><span class="sxs-lookup"><span data-stu-id="6335a-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="6335a-126">Установка terraform в контейнер DOCKER в пакете означает, что пользователям не нужно устанавливать terraform на компьютере для запуска объединения.</span><span class="sxs-lookup"><span data-stu-id="6335a-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

<span data-ttu-id="6335a-127">**Рис. 10-18** . пример файла terraform</span><span class="sxs-lookup"><span data-stu-id="6335a-127">**Figure 10-18** - An example Terraform file</span></span>

<span data-ttu-id="6335a-128">`bundle.json`Также определяет набор параметров, которые передаются в terraform.</span><span class="sxs-lookup"><span data-stu-id="6335a-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="6335a-129">Параметризация пакета позволяет устанавливать в разных средах.</span><span class="sxs-lookup"><span data-stu-id="6335a-129">Parameterization of the bundle allows for installation in various different environments.</span></span>

<span data-ttu-id="6335a-130">Формат КНАБ также является гибким, что позволяет использовать его в любом облаке.</span><span class="sxs-lookup"><span data-stu-id="6335a-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="6335a-131">Его можно использовать и в локальных решениях, таких как [OpenStack](https://www.openstack.org/).</span><span class="sxs-lookup"><span data-stu-id="6335a-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="6335a-132">DevOps решения</span><span class="sxs-lookup"><span data-stu-id="6335a-132">DevOps Decisions</span></span>

<span data-ttu-id="6335a-133">В DevOps пространстве есть много замечательных средств, а также еще более потрясающие книги и документы о том, как их можно достичь.</span><span class="sxs-lookup"><span data-stu-id="6335a-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="6335a-134">Чтобы приступить к работе в DevOps, можно перейти к [проекту Phoenix](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), который следует за преобразованием вымышленной компании из Нупс в DevOps.</span><span class="sxs-lookup"><span data-stu-id="6335a-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="6335a-135">Одна из них: DevOps больше не является «полезной» при развертывании сложных облачных приложений в машинном код.</span><span class="sxs-lookup"><span data-stu-id="6335a-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="6335a-136">Это требование, и его следует планировать и перенаследовать в начале любого проекта.</span><span class="sxs-lookup"><span data-stu-id="6335a-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

## <a name="references"></a><span data-ttu-id="6335a-137">Ссылки</span><span class="sxs-lookup"><span data-stu-id="6335a-137">References</span></span>

- [<span data-ttu-id="6335a-138">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="6335a-138">Azure DevOps</span></span>](https://azure.microsoft.com/services/devops/)
- [<span data-ttu-id="6335a-139">Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="6335a-139">Azure Resource Manager</span></span>](/azure/azure-resource-manager/management/overview)
- [<span data-ttu-id="6335a-140">Terraform</span><span class="sxs-lookup"><span data-stu-id="6335a-140">Terraform</span></span>](https://www.terraform.io/)
- [<span data-ttu-id="6335a-141">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="6335a-141">Azure CLI</span></span>](/cli/azure/)

>[!div class="step-by-step"]
><span data-ttu-id="6335a-142">[Назад](infrastructure-as-code.md)
>[Вперед](summary.md)</span><span class="sxs-lookup"><span data-stu-id="6335a-142">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
