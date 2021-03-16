---
title: Использование Azure Key Vault для защиты секретов в рабочей среде
description: Безопасность в микрослужбах и веб-приложениях .NET. Azure Key Vault предоставляет отличный способ работы с секретами приложений, которыми полностью управляют администраторы. Администраторы даже могут назначать и отзывать значения разработки без необходимости привлекать к этому разработчиков.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 94243468b35e2db9818ae9afacd5beec0a12075e
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604623"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="c4eab-104">Защиты секретов в рабочей среде с помощью Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="c4eab-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="c4eab-105">Секреты, которые сохраняются в переменных среды или с помощью диспетчера секретов, хранятся на компьютере в локальном и незашифрованном виде.</span><span class="sxs-lookup"><span data-stu-id="c4eab-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="c4eab-106">Более безопасный способ хранения секретов — хранилище [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), которое предоставляет безопасное централизованное расположение для хранения ключей и секретов.</span><span class="sxs-lookup"><span data-stu-id="c4eab-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="c4eab-107">С помощью пакета **Azure.Extensions.AspNetCore.Configuration.Secrets** приложение ASP.NET Core может считывать сведения о конфигурации из Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="c4eab-107">The **Azure.Extensions.AspNetCore.Configuration.Secrets** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="c4eab-108">Чтобы приступить к работе с секретами из Azure Key Vault, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="c4eab-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="c4eab-109">Зарегистрируйте свое приложение как приложение Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c4eab-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="c4eab-110">(Доступом к хранилищам ключей управляет Azure AD.) Это можно сделать с помощью портала управления Azure.</span><span class="sxs-lookup"><span data-stu-id="c4eab-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.\</span></span>

   <span data-ttu-id="c4eab-111">Кроме того, если приложение должно проходить проверку подлинности на основе сертификата, а не пароля или секрета клиента, вы можете использовать командлет PowerShell [New-AzADApplication](/powershell/module/az.resources/new-azadapplication).</span><span class="sxs-lookup"><span data-stu-id="c4eab-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="c4eab-112">Для сертификата, который зарегистрирован в хранилище ключей Azure Key Vault, необходим только ваш открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="c4eab-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="c4eab-113">Приложение будет использовать закрытый ключ.</span><span class="sxs-lookup"><span data-stu-id="c4eab-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="c4eab-114">Предоставьте зарегистрированному приложению доступ к хранилищу ключей, создав новый субъект-службу.</span><span class="sxs-lookup"><span data-stu-id="c4eab-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="c4eab-115">Это можно сделать с помощью следующих команд PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c4eab-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="c4eab-116">Включите хранилище ключей как источник конфигурации в своем приложении. Для этого вызовите метод расширения AzureKeyVaultConfigurationExtensions.AddAzureKeyVault при создании экземпляра <xref:Microsoft.Extensions.Configuration.IConfigurationRoot>.</span><span class="sxs-lookup"><span data-stu-id="c4eab-116">Include the key vault as a configuration source in your application by calling the AzureKeyVaultConfigurationExtensions.AddAzureKeyVault extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span>

<span data-ttu-id="c4eab-117">Обратите внимание, что для вызова метода `AddAzureKeyVault` потребуется идентификатор приложения, которое было зарегистрировано и которому был предоставлен доступ к хранилищу ключей на предыдущих шагах.</span><span class="sxs-lookup"><span data-stu-id="c4eab-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span> <span data-ttu-id="c4eab-118">Или можно сначала выполнить команду Azure CLI: `az login`, а затем использовать перегрузку `AddAzureKeyVault`, которая принимает DefaultAzureCredential вместо клиента.</span><span class="sxs-lookup"><span data-stu-id="c4eab-118">Or you can firstly running the Azure CLI command: `az login`, then using an overload of `AddAzureKeyVault` that takes a DefaultAzureCredential in place of the client.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4eab-119">Рекомендуем зарегистрировать Azure Key Vault в качестве последнего поставщика конфигурации, чтобы можно было переопределять значения параметров конфигурации от предыдущих поставщиков.</span><span class="sxs-lookup"><span data-stu-id="c4eab-119">We recommend that you register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c4eab-120">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="c4eab-120">Additional resources</span></span>

- <span data-ttu-id="c4eab-121">**Использование Azure Key Vault для защиты секретов приложений** </span><span class="sxs-lookup"><span data-stu-id="c4eab-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/architecture/multitenant-identity](/azure/architecture/multitenant-identity)

- <span data-ttu-id="c4eab-122">**Безопасное хранение секретов приложения во время разработки** </span><span class="sxs-lookup"><span data-stu-id="c4eab-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="c4eab-123">**Настройка защиты данных** </span><span class="sxs-lookup"><span data-stu-id="c4eab-123">**Configuring data protection** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="c4eab-124">**Управление ключами для защиты данных и время существования в ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="c4eab-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

>[!div class="step-by-step"]
><span data-ttu-id="c4eab-125">[Назад](developer-app-secrets-storage.md)
>[Вперед](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="c4eab-125">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
