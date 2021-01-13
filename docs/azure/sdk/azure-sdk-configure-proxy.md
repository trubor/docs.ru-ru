---
title: Настройка прокси-сервера при использовании пакета Azure SDK для .NET
description: Определение прокси-сервера для пакета Azure SDK для .NET с использованием переменных среды HTTP[S]_PROXY
ms.date: 12/10/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.openlocfilehash: 64d525f8a6c277a5ac383dfded828f2fd3cfd744
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700952"
---
# <a name="configure-a-proxy-server-when-using-the-azure-sdk-for-net"></a><span data-ttu-id="cd8b2-103">Настройка прокси-сервера при использовании пакета Azure SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="cd8b2-103">Configure a proxy server when using the Azure SDK for .NET</span></span>

<span data-ttu-id="cd8b2-104">Если вашей организации требуется использовать прокси-сервер для доступа к ресурсам в Интернете, для использования пакета Azure SDK для .NET необходимо настроить переменную среды со сведениями о прокси-сервере.</span><span class="sxs-lookup"><span data-stu-id="cd8b2-104">If your organization requires the use of a proxy server to access internet resources, you will need to set an environment variable with the proxy server information to use the Azure SDK for .NET.</span></span>  

## <a name="configuration-using-environment-variables"></a><span data-ttu-id="cd8b2-105">Настройка с использованием переменных среды</span><span class="sxs-lookup"><span data-stu-id="cd8b2-105">Configuration using environment variables</span></span>

<span data-ttu-id="cd8b2-106">В зависимости от того, использует ли прокси-сервер протокол HTTP или HTTPS, необходимо настраивать соответственно переменную среды `HTTP_PROXY` или `HTTPS_PROXY`.</span><span class="sxs-lookup"><span data-stu-id="cd8b2-106">Depending on if your proxy server uses HTTP or HTTPS, you will set either the environment variable `HTTP_PROXY` or `HTTPS_PROXY` respectively.</span></span> <span data-ttu-id="cd8b2-107">URL-адрес прокси сервера имеет вид `http[s]://[username:password@]<ip_address_or_hostname>:<port>/`, где комбинация `username:password` является необязательной.</span><span class="sxs-lookup"><span data-stu-id="cd8b2-107">The proxy server URL has the form `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` where the `username:password` combination is optional.</span></span> <span data-ttu-id="cd8b2-108">IP-адрес или имя узла, номер порта и учетные данные для прокси-сервера вы можете получить у администратора сети.</span><span class="sxs-lookup"><span data-stu-id="cd8b2-108">To get the IP address or hostname, port and credentials for your proxy server, consult your network administrator.</span></span>

<span data-ttu-id="cd8b2-109">В следующих примерах показано, как настроить соответствующие переменные среды в средах командной оболочки (Windows) и bash (Linux/Mac).</span><span class="sxs-lookup"><span data-stu-id="cd8b2-109">The following examples show how to set the appropriate environment variables in command shell (Windows) and bash (Linux/Mac) environments.</span></span>  <span data-ttu-id="cd8b2-110">После настройки соответствующей переменной среды пакет Azure SDK для .NET будет использовать прокси-сервер во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="cd8b2-110">Setting the appropriate environment variable will then cause the Azure SDK for .NET to use the proxy server at runtime.</span></span>

### <a name="cmd"></a>[<span data-ttu-id="cd8b2-111">cmd</span><span class="sxs-lookup"><span data-stu-id="cd8b2-111">cmd</span></span>](#tab/cmd)

```cmd
rem Non-authenticated HTTP server:
set HTTP_PROXY=http://10.10.1.10:1180

rem Authenticated HTTP server:
set HTTP_PROXY=http://username:password@10.10.1.10:1180

rem Non-authenticated HTTPS server:
set HTTPS_PROXY=http://10.10.1.10:1180

rem Authenticated HTTPS server:
set HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

### <a name="bash"></a>[<span data-ttu-id="cd8b2-112">bash</span><span class="sxs-lookup"><span data-stu-id="cd8b2-112">bash</span></span>](#tab/bash)

```bash
# Non-authenticated HTTP server:
HTTP_PROXY=http://10.10.1.10:1180

# Authenticated HTTP server:
HTTP_PROXY=http://username:password@10.10.1.10:1180

# Non-authenticated HTTPS server:
HTTPS_PROXY=http://10.10.1.10:1180

# Authenticated HTTPS server:
HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

---
