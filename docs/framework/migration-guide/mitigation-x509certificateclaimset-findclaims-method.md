---
title: Устранение рисков. Метод X509CertificateClaimSet.FindClaims
description: Узнайте об изменении метода X509CertificateClaimSet.FindClaims для приложений, предназначенных для .NET Framework 4.6.1.
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: ed9e345f9e48156f37f493caa78e6b3901cecf23
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253574"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="39309-103">Устранение рисков. Метод X509CertificateClaimSet.FindClaims</span><span class="sxs-lookup"><span data-stu-id="39309-103">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="39309-104">Начиная с приложений, предназначенных для .NET Framework 4.6.1, метод <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> пытается сопоставить аргумент `claimType` со всеми записями DNS в поле SAN.</span><span class="sxs-lookup"><span data-stu-id="39309-104">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="39309-105">Последствия</span><span class="sxs-lookup"><span data-stu-id="39309-105">Impact</span></span>  

 <span data-ttu-id="39309-106">Это изменение затрагивает только приложения, предназначенные для .NET Framework, начиная с версии .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="39309-106">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="39309-107">В приложениях, предназначенных для более ранних версий .NET Framework, метод <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> пытается сопоставить аргумент `claimType` только с последней записью DNS.</span><span class="sxs-lookup"><span data-stu-id="39309-107">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="39309-108">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="39309-108">Mitigation</span></span>  

 <span data-ttu-id="39309-109">Если это изменение нежелательно, его можно отключить для приложений, предназначенных для версий .NET Framework, начиная с .NET Framework 4.6.1, добавив в раздел [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) файла конфигурации приложения следующий параметр:</span><span class="sxs-lookup"><span data-stu-id="39309-109">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="39309-110">Кроме того, это поведение можно включить для приложений, предназначенных для предыдущих версий .NET Framework, но работающих под управлением .NET Framework 4.6.1 и более поздних версий. Для этого добавьте в раздел [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) файла конфигурации приложения следующий параметр:</span><span class="sxs-lookup"><span data-stu-id="39309-110">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39309-111">См. также</span><span class="sxs-lookup"><span data-stu-id="39309-111">See also</span></span>

- [<span data-ttu-id="39309-112">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="39309-112">Application compatibility</span></span>](application-compatibility.md)
