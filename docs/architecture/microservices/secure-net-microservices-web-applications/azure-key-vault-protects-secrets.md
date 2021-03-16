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
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Защиты секретов в рабочей среде с помощью Azure Key Vault

Секреты, которые сохраняются в переменных среды или с помощью диспетчера секретов, хранятся на компьютере в локальном и незашифрованном виде. Более безопасный способ хранения секретов — хранилище [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), которое предоставляет безопасное централизованное расположение для хранения ключей и секретов.

С помощью пакета **Azure.Extensions.AspNetCore.Configuration.Secrets** приложение ASP.NET Core может считывать сведения о конфигурации из Azure Key Vault. Чтобы приступить к работе с секретами из Azure Key Vault, выполните следующие действия:

1. Зарегистрируйте свое приложение как приложение Azure Active Directory. (Доступом к хранилищам ключей управляет Azure AD.) Это можно сделать с помощью портала управления Azure.

   Кроме того, если приложение должно проходить проверку подлинности на основе сертификата, а не пароля или секрета клиента, вы можете использовать командлет PowerShell [New-AzADApplication](/powershell/module/az.resources/new-azadapplication). Для сертификата, который зарегистрирован в хранилище ключей Azure Key Vault, необходим только ваш открытый ключ. Приложение будет использовать закрытый ключ.

2. Предоставьте зарегистрированному приложению доступ к хранилищу ключей, создав новый субъект-службу. Это можно сделать с помощью следующих команд PowerShell:

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Включите хранилище ключей как источник конфигурации в своем приложении. Для этого вызовите метод расширения AzureKeyVaultConfigurationExtensions.AddAzureKeyVault при создании экземпляра <xref:Microsoft.Extensions.Configuration.IConfigurationRoot>.

Обратите внимание, что для вызова метода `AddAzureKeyVault` потребуется идентификатор приложения, которое было зарегистрировано и которому был предоставлен доступ к хранилищу ключей на предыдущих шагах. Или можно сначала выполнить команду Azure CLI: `az login`, а затем использовать перегрузку `AddAzureKeyVault`, которая принимает DefaultAzureCredential вместо клиента.

> [!IMPORTANT]
> Рекомендуем зарегистрировать Azure Key Vault в качестве последнего поставщика конфигурации, чтобы можно было переопределять значения параметров конфигурации от предыдущих поставщиков.

## <a name="additional-resources"></a>Дополнительные ресурсы

- **Использование Azure Key Vault для защиты секретов приложений** \
  [https://docs.microsoft.com/azure/architecture/multitenant-identity](/azure/architecture/multitenant-identity)

- **Безопасное хранение секретов приложения во время разработки** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Настройка защиты данных** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **Управление ключами для защиты данных и время существования в ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

>[!div class="step-by-step"]
>[Назад](developer-app-secrets-storage.md)
>[Вперед](../key-takeaways.md)
