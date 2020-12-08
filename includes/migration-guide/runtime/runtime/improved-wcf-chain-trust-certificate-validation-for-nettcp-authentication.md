---
ms.openlocfilehash: f6553444e13416850a398ae5bcb6574f2a69bd2d
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96476968"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a><span data-ttu-id="30e50-101">Улучшенная проверка цепочки сертификатов WCF для проверки подлинности сертификатов в Net.Tcp</span><span class="sxs-lookup"><span data-stu-id="30e50-101">Improved WCF chain trust certificate validation for Net.Tcp certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="30e50-102">Подробнее</span><span class="sxs-lookup"><span data-stu-id="30e50-102">Details</span></span>

<span data-ttu-id="30e50-103">В .NET Framework 4.7.2 улучшена проверка цепочки сертификатов при использовании проверки подлинности сертификатов с защитой транспорта в WCF.</span><span class="sxs-lookup"><span data-stu-id="30e50-103">.NET Framework 4.7.2 improves chain trust certificate validation when using certificate authentication with transport security with WCF.</span></span> <span data-ttu-id="30e50-104">В связи с этим усовершенствованием сертификаты клиента, которые используются для проверки подлинности на сервере, необходимо настроить для проверки подлинности клиента.</span><span class="sxs-lookup"><span data-stu-id="30e50-104">With this improvement, client certificates that are used to authenticate to a server must be configured for client authentication.</span></span>  <span data-ttu-id="30e50-105">Аналогичным образом сертификаты сервера, которые используются для проверки подлинности сервера, необходимо настроить для проверки подлинности сервера.</span><span class="sxs-lookup"><span data-stu-id="30e50-105">Similarly server certificates that are for the authenticating a server must be configured for server authentication.</span></span> <span data-ttu-id="30e50-106">В результате этого изменения проверка цепочки сертификатов завершается ошибкой, если корневой сертификат отключен.</span><span class="sxs-lookup"><span data-stu-id="30e50-106">With this change, if the root certificate is disabled, the certificate chain validation fails.</span></span> <span data-ttu-id="30e50-107">Это же изменение вносилось в .NET Framework 3.5 и более поздних версий с помощью свертки безопасности Windows.</span><span class="sxs-lookup"><span data-stu-id="30e50-107">The same change was also made to .NET Framework 3.5 and later versions via Windows security roll-up.</span></span> <span data-ttu-id="30e50-108">Дополнительные сведения можно найти [здесь](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Это изменение включено по умолчанию. Его можно отключить с помощью параметра конфигурации.</span><span class="sxs-lookup"><span data-stu-id="30e50-108">You can find more information [here](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7).This change is on by default and can be turned off by a configuration setting.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="30e50-109">Предложение</span><span class="sxs-lookup"><span data-stu-id="30e50-109">Suggestion</span></span>

<ul><li><span data-ttu-id="30e50-110">Проверьте, есть ли у сертификатов сервера и клиента необходимые OID EKU.</span><span class="sxs-lookup"><span data-stu-id="30e50-110">Validate if your server and client certification has the required EKU OID.</span></span> <span data-ttu-id="30e50-111">Если нет, обновите сертификаты.</span><span class="sxs-lookup"><span data-stu-id="30e50-111">If not, update your certification.</span></span></li><li><span data-ttu-id="30e50-112">Возможно, корневой сертификат является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="30e50-112">Validate if your root certificate is invalid.</span></span> <span data-ttu-id="30e50-113">В этом случае обновите корневой сертификат.</span><span class="sxs-lookup"><span data-stu-id="30e50-113">If so, update the root certificate.</span></span></li><li><span data-ttu-id="30e50-114">Как отказаться от этого изменения? Если не удается обновить сертификат, можно временно обойти критическое изменение, используя следующий параметр конфигурации. Но при отказе от этого изменения ваша система будет уязвима для проблем с безопасностью.</span><span class="sxs-lookup"><span data-stu-id="30e50-114">How to opt out of the change: If you can't update the certificate, you can work around the breaking change temporarily with the following configuration setting,  However, opting out of the change will leave your system vulnerable to the security issue.</span></span></li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="30e50-115">name</span><span class="sxs-lookup"><span data-stu-id="30e50-115">Name</span></span>    | <span data-ttu-id="30e50-116">Значение</span><span class="sxs-lookup"><span data-stu-id="30e50-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="30e50-117">Область</span><span class="sxs-lookup"><span data-stu-id="30e50-117">Scope</span></span>   |<span data-ttu-id="30e50-118">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="30e50-118">Minor</span></span>|
|<span data-ttu-id="30e50-119">Version</span><span class="sxs-lookup"><span data-stu-id="30e50-119">Version</span></span>|<span data-ttu-id="30e50-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="30e50-120">4.7.2</span></span>|
|<span data-ttu-id="30e50-121">Type</span><span class="sxs-lookup"><span data-stu-id="30e50-121">Type</span></span>|<span data-ttu-id="30e50-122">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="30e50-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="30e50-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="30e50-123">Affected APIs</span></span>

<span data-ttu-id="30e50-124">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="30e50-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
