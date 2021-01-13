---
title: Установка Azure CLI
description: Разработчикам Azure потребуется установка Azure CLI. В этой статье описывается, зачем нужен интерфейс командной строки (CLI) и откуда его можно скачать и установить.
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 43737aaf5dfd02b8c4ffa6c213d7221cfe38162f
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700971"
---
# <a name="install-the-azure-cli"></a><span data-ttu-id="a6268-103">Установка Azure CLI</span><span class="sxs-lookup"><span data-stu-id="a6268-103">Install the Azure CLI</span></span>

<span data-ttu-id="a6268-104">В дополнение к порталу Azure в Azure также предлагается [Azure CLI](/cli/azure/), средство командной строки для создания ресурсов Azure и управления ими.</span><span class="sxs-lookup"><span data-stu-id="a6268-104">In addition to the Azure Portal, Azure also offers the [Azure CLI](/cli/azure/) as a command-line tool to create and manage Azure resources.</span></span> <span data-ttu-id="a6268-105">Azure CLI позволяет повысить степень эффективности и воспроизводимости повторяющихся задач, а также использовать скрипты для их выполнения.</span><span class="sxs-lookup"><span data-stu-id="a6268-105">The Azure CLI offers the benefits of efficiency, repeatability, and the ability to script recurring tasks.</span></span>  

<span data-ttu-id="a6268-106">На практике большинство разработчиков используют и портал Azure, и Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="a6268-106">In practice, most developers use both the Azure Portal and the Azure CLI.</span></span> <span data-ttu-id="a6268-107">Портал Azure удобен для знакомства с новыми службами и обзора всех ресурсов в учетной записи Azure, но при этом большинство разработчиков считают Azure CLI более быстрым и эффективным инструментом.</span><span class="sxs-lookup"><span data-stu-id="a6268-107">Where as the Azure Portal is useful when exploring new services and getting an overview of all of the resources in your Azure account, most developers find the Azure CLI to be faster and more efficient.</span></span>  <span data-ttu-id="a6268-108">Зачастую в Azure CLI с помощью одной команды можно выполнить задачу, требующую нескольких действий на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="a6268-108">The Azure CLI can often accomplish in a single command what takes multiple steps in the Azure Portal.</span></span>  <span data-ttu-id="a6268-109">Кроме того, команды Azure CLI можно сохранять в файл, благодаря чему гарантируется единообразное выполнение повторяющихся задач.</span><span class="sxs-lookup"><span data-stu-id="a6268-109">In addition, since Azure CLI commands can be saved to a file, developers can assure that recurrent tasks are run the same way each time.</span></span>

<span data-ttu-id="a6268-110">Azure CLI доступен для Windows, macOS и Linux.</span><span class="sxs-lookup"><span data-stu-id="a6268-110">The Azure CLI is available for Windows, macOS, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6268-111">Установка Azure CLI для Windows</span><span class="sxs-lookup"><span data-stu-id="a6268-111">Install the Azure CLI for Windows</span></span>](/cli/azure/install-azure-cli-windows?tabs=azure-cli)

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6268-112">Установка Azure CLI для macOS</span><span class="sxs-lookup"><span data-stu-id="a6268-112">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6268-113">Установка Azure CLI для Linux</span><span class="sxs-lookup"><span data-stu-id="a6268-113">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

### <a name="azure-cloud-shell"></a><span data-ttu-id="a6268-114">Azure Cloud Shell</span><span class="sxs-lookup"><span data-stu-id="a6268-114">Azure Cloud Shell</span></span>

<span data-ttu-id="a6268-115">Azure CLI также можно использовать в Azure Cloud Shell по адресу [https://shell.azure.com](https://shell.azure.com).</span><span class="sxs-lookup"><span data-stu-id="a6268-115">You can also use the Azure CLI in the Azure Cloud Shell at [https://shell.azure.com](https://shell.azure.com).</span></span>  <span data-ttu-id="a6268-116">Azure Cloud Shell представляет собой полнофункциональную браузерную оболочку для управления ресурсами Azure.</span><span class="sxs-lookup"><span data-stu-id="a6268-116">The Azure Cloud Shell is a fully functional, browser-based shell for managing Azure resources.</span></span>  <span data-ttu-id="a6268-117">Azure Cloud Shell удобно использовать в тех случаях, когда требуется среда командной строки, но работа ведется на устройстве, где нельзя установить Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="a6268-117">The Azure Cloud Shell is useful when you need a command line environment but are working on a device where you are unable to install the Azure CLI.</span></span>

![Снимок экрана: Azure Cloud Shell в браузере](media/azure-cloud-shell.png)
