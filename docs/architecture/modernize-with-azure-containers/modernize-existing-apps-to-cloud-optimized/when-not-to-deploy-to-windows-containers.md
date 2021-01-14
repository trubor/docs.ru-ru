---
title: Технологии, не поддерживающие развертывание в контейнерах Windows
description: Модернизация существующих приложений .NET с помощью облака Azure и контейнеров Windows | Технологии, не поддерживающие развертывание в контейнерах Windows
ms.date: 12/21/2020
ms.openlocfilehash: 4eea24ab8deb3719c778b45b3ddc1309277a3f50
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025177"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="2ae83-103">Технологии, не поддерживающие развертывание в контейнерах Windows</span><span class="sxs-lookup"><span data-stu-id="2ae83-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="2ae83-104">Некоторые технологии Windows не поддерживаются контейнерами Windows.</span><span class="sxs-lookup"><span data-stu-id="2ae83-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="2ae83-105">В таких случаях вам по-прежнему нужно выполнить миграцию на стандартные виртуальные машины, обычно с использованием только Windows и IIS.</span><span class="sxs-lookup"><span data-stu-id="2ae83-105">In those cases, you still need to migrate to the standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="2ae83-106">Сценарии, не поддерживающиеся в контейнерах Windows по состоянию на май 2018 года:</span><span class="sxs-lookup"><span data-stu-id="2ae83-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="2ae83-107">В настоящее время технология очередей сообщений (MSMQ) доступна только в контейнерах Windows с выпуском Windows Server версии 1803, но не с предыдущими выпусками.</span><span class="sxs-lookup"><span data-stu-id="2ae83-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="2ae83-108">Форум по запросам UserVoice</span><span class="sxs-lookup"><span data-stu-id="2ae83-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="2ae83-109">Форум обсуждения</span><span class="sxs-lookup"><span data-stu-id="2ae83-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="2ae83-110">Координатор распределенных транзакций Майкрософт (MSDTC) в настоящее время не поддерживается в контейнерах Windows.</span><span class="sxs-lookup"><span data-stu-id="2ae83-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="2ae83-111">Проблема, рассмотренная на сайте GitHub</span><span class="sxs-lookup"><span data-stu-id="2ae83-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="2ae83-112">Microsoft Office в настоящее время не поддерживает контейнеры.</span><span class="sxs-lookup"><span data-stu-id="2ae83-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="2ae83-113">Форум по запросам UserVoice</span><span class="sxs-lookup"><span data-stu-id="2ae83-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="2ae83-114">Приложения пользовательского интерфейса (клиентские приложения с визуальным пользовательским интерфейсом) не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="2ae83-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="2ae83-115">Роли инфраструктуры Windows (DNS, DHCP, DC, NTP, PRINT, файловый сервер, IAM и т. д.) не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="2ae83-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="2ae83-116">Другие неподдерживаемые сценарии и запросы от сообщества см. в разделе форума UserVoice, посвященном контейнерам Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="2ae83-116">For other nonsupported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2ae83-117">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="2ae83-117">Additional resources</span></span>

- <span data-ttu-id="2ae83-118">**Виртуальные машины и контейнеры в Azure**</span><span class="sxs-lookup"><span data-stu-id="2ae83-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="2ae83-119">[Назад](deploy-existing-net-apps-as-windows-containers.md)
> [Вперед](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="2ae83-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
