---
title: Настройка Visual Studio для разработки Azure с помощью .NET
description: Сведения в этой статье помогут вам настроить Visual Studio для разработки Azure, включая получение правильных рабочих нагрузок и подключение Visual Studio к учетной записи Azure
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 986469bd07657d968045465803047dc21d76dd62
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701037"
---
# <a name="configure-visual-studio-for-azure-development-with-net"></a><span data-ttu-id="7cdca-103">Настройка Visual Studio для разработки Azure с помощью .NET</span><span class="sxs-lookup"><span data-stu-id="7cdca-103">Configure Visual Studio for Azure development with .NET</span></span>

<span data-ttu-id="7cdca-104">Visual Studio включает инструментарий, помогающий в разработке и развертывании приложений в Azure.</span><span class="sxs-lookup"><span data-stu-id="7cdca-104">Visual Studio includes tooling to help with the development and deployment of applications on Azure.</span></span>  <span data-ttu-id="7cdca-105">Данное руководство поможет правильно настроить Visual Studio для разработки Azure.</span><span class="sxs-lookup"><span data-stu-id="7cdca-105">This guide will help you make sure that you have Visual Studio properly configured for Azure development.</span></span>

### <a name="download-visual-studio-2019"></a><span data-ttu-id="7cdca-106">Скачивание Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="7cdca-106">Download Visual Studio 2019</span></span>

<span data-ttu-id="7cdca-107">Вы можете пропустить этот шаг, если уже установили Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7cdca-107">If you already have Visual Studio 2019 installed, you can skip this step.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7cdca-108">Скачивание Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="7cdca-108">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a><span data-ttu-id="7cdca-109">Установка рабочих нагрузок Azure</span><span class="sxs-lookup"><span data-stu-id="7cdca-109">Install Azure workloads</span></span>

<span data-ttu-id="7cdca-110">Запустите **Visual Studio Installer** и проверьте, что установлены рабочие нагрузки **Разработка Azure** и **ASP.NET и веб-разработка**.</span><span class="sxs-lookup"><span data-stu-id="7cdca-110">Launch the **Visual Studio Installer** and validate that you have the workloads **Azure development** and **ASP.NET and web development** are installed.</span></span>  <span data-ttu-id="7cdca-111">Если какая-либо из этих рабочих нагрузок не установлена, выберите эти рабочие нагрузки, чтобы установить их.</span><span class="sxs-lookup"><span data-stu-id="7cdca-111">If either of these workloads is not installed, select these workloads to install them.</span></span>

![Снимок экрана Visual Studio Installer с выбранными рабочими нагрузками "Разработка Azure" и "ASP.NET и веб-разработка".](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a><span data-ttu-id="7cdca-113">Проверка подлинности Visual Studio в Azure</span><span class="sxs-lookup"><span data-stu-id="7cdca-113">Authenticate Visual Studio with Azure</span></span>

<span data-ttu-id="7cdca-114">При отладке приложений в Visual Studio может использоваться учетная запись Azure для проверки подлинности и доступа к ресурсам Azure.</span><span class="sxs-lookup"><span data-stu-id="7cdca-114">When debugging apps through Visual Studio, Visual Studio can use your Azure account to authenticate and access Azure Resources with.</span></span>  <span data-ttu-id="7cdca-115">Эта учетная запись также используется при публикации приложений непосредственно из Visual Studio в Azure.</span><span class="sxs-lookup"><span data-stu-id="7cdca-115">This account is also used when you publish apps directly from Visual Studio to Azure.</span></span>

<span data-ttu-id="7cdca-116">Чтобы проверить подлинность учетной записи Azure из Visual Studio, выберите меню **Сервис** > **Параметры**, чтобы открыть диалоговое окно **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="7cdca-116">To authenticate your Azure account from Visual Studio, select the **Tools** > **Options** menu to launch the **Options** dialog.</span></span> <span data-ttu-id="7cdca-117">Перейдите к параметрам `Azure Service Authentication` и выполните вход с помощью учетной записи Azure.</span><span class="sxs-lookup"><span data-stu-id="7cdca-117">Navigate to the `Azure Service Authentication` options and sign in using your Azure account.</span></span>

![Снимок экрана: диалоговое окно параметров Visual Studio, в котором отображается имя для входа Azure](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a><span data-ttu-id="7cdca-119">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="7cdca-119">Next steps</span></span>

<span data-ttu-id="7cdca-120">Если вы также используете [Visual Studio Code](https://code.visualstudio.com/) для разработки на .NET или на любом другом языке, необходимо также [настроить Visual Studio Code для разработки Azure](./configure-vs-code.md).</span><span class="sxs-lookup"><span data-stu-id="7cdca-120">If you also use [Visual Studio Code](https://code.visualstudio.com/) for development in .NET or any other language, you should also [configure Visual Studio Code for Azure development](./configure-vs-code.md).</span></span> <span data-ttu-id="7cdca-121">В противном случае перейдите к [установке Azure CLI](./install-azure-cli.md).</span><span class="sxs-lookup"><span data-stu-id="7cdca-121">Otherwise, proceed to [Installing the Azure CLI](./install-azure-cli.md).</span></span>
