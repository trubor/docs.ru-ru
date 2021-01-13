---
title: Настройка Visual Studio Code для разработки Azure с помощью .NET
description: Сведения в этой статье помогут вам настроить Visual Studio Code для разработки Azure, включая установку и настройку соответствующих подключаемых модулей в VS Code
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 65ced99befe12d137062b4ea6a59a1ccd3099e0b
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701030"
---
# <a name="configure-visual-studio-code-for-azure-development"></a><span data-ttu-id="2f49f-103">Настройка Visual Studio Code для разработки Azure</span><span class="sxs-lookup"><span data-stu-id="2f49f-103">Configure Visual Studio Code for Azure development</span></span>

<span data-ttu-id="2f49f-104">Если вы используете Visual Studio Code для разработки для .NET, создания одностраничных приложений с помощью таких платформ, как Angular, React или Vue, или для написания приложений на другом языке, например Python, вам потребуется настроить Visual Studio Code для разработки Azure.</span><span class="sxs-lookup"><span data-stu-id="2f49f-104">If you are using Visual Studio Code, whether for .NET development, for building single page applications using frameworks like Angular, React or Vue, or for writing applications in another language like Python, you will want to configure Visual Studio Code for Azure development.</span></span>

### <a name="download-visual-studio-code"></a><span data-ttu-id="2f49f-105">Скачать Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2f49f-105">Download Visual Studio Code</span></span>

<span data-ttu-id="2f49f-106">Вы можете пропустить этот шаг, если уже установили Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2f49f-106">If you already have Visual Studio Code installed, you can skip this step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f49f-107">Скачать Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2f49f-107">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a><span data-ttu-id="2f49f-108">Установка пакета расширений "Средства Azure"</span><span class="sxs-lookup"><span data-stu-id="2f49f-108">Install the Azure Tools Extension Pack</span></span>

<span data-ttu-id="2f49f-109">[Пакет расширений средств Azure](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) содержит расширения для работы со Службой приложений Azure, Функциями Azure, службой хранилища Azure, Cosmos DB и виртуальными машинами Azure — все это в одном удобном пакете.</span><span class="sxs-lookup"><span data-stu-id="2f49f-109">The [Azure Tools Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) contains extensions for working with Azure App Service, Azure Functions, Azure Storage, Cosmos DB, and Azure Virtual Machines all in one convenient package.</span></span>

<span data-ttu-id="2f49f-110">Чтобы установить расширение из Visual Studio Code, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="2f49f-110">To install the extension from Visual Studio Code:</span></span>

1. <span data-ttu-id="2f49f-111">Нажмите клавиши <kbd>CTRL+SHIFT+X</kbd>, чтобы открыть окно **Расширения**.</span><span class="sxs-lookup"><span data-stu-id="2f49f-111">Press <kbd>Ctrl+Shift+X</kbd> to open the **Extensions** window.</span></span>
1. <span data-ttu-id="2f49f-112">Выполните поиск расширения *Средства Azure*.</span><span class="sxs-lookup"><span data-stu-id="2f49f-112">Search for the *Azure Tools* extension.</span></span>
1. <span data-ttu-id="2f49f-113">Нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="2f49f-113">Select the **Install** button.</span></span>

![Снимок экрана: панель расширений в Visual Studio Code, поиск пакета расширений "Средства Azure"](./media/visual-studio-code-azure-tools.png)

<span data-ttu-id="2f49f-115">Дополнительные сведения об установке расширений в Visual Studio Code см. в документе [Магазин расширений](https://code.visualstudio.com/docs/editor/extension-gallery) на веб-сайте Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2f49f-115">To learn more about installing extensions in Visual Studio Code, refer to the [Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) document on the Visual Studio Code website.</span></span>

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a><span data-ttu-id="2f49f-116">Вход в учетную запись Azure с помощью средств Azure</span><span class="sxs-lookup"><span data-stu-id="2f49f-116">Sign in to your Azure account with Azure Tools</span></span>

<span data-ttu-id="2f49f-117">На панели слева вы увидите значок Azure.</span><span class="sxs-lookup"><span data-stu-id="2f49f-117">On the left hand panel, you'll see an Azure icon.</span></span> <span data-ttu-id="2f49f-118">Выберите этот значок, после чего отобразится панель управления для служб Azure.</span><span class="sxs-lookup"><span data-stu-id="2f49f-118">Select this icon, and a control panel for Azure services will appear.</span></span> <span data-ttu-id="2f49f-119">Выберите **Войти в Azure** в любой службе, чтобы завершить процесс проверки подлинности средств Azure в Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2f49f-119">Choose **Sign in to Azure...** under any service to complete the authentication process for the Azure tools in Visual Studio Code.</span></span>

![Снимок экрана Visual Studio Code: вход в Azure для работы со средствами Azure](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a><span data-ttu-id="2f49f-121">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="2f49f-121">Next steps</span></span>

<span data-ttu-id="2f49f-122">Далее необходимо установить Azure CLI на рабочую станцию.</span><span class="sxs-lookup"><span data-stu-id="2f49f-122">Next, you will want to install the Azure CLI on your workstation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f49f-123">Установка Azure CLI</span><span class="sxs-lookup"><span data-stu-id="2f49f-123">Install the Azure CLI</span></span>](./install-azure-cli.md)
