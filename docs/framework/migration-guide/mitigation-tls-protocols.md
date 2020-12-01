---
title: Устранение рисков. Протоколы TLS
description: Узнайте о последствии и устранении рисков в связи с изменениями протокола TLS, начиная с .NET Framework 4.6.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 492315d43043c83d17eab330e8d589d1cffe7ad2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273871"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="79f0b-103">Устранение рисков. Протоколы TLS</span><span class="sxs-lookup"><span data-stu-id="79f0b-103">Mitigation: TLS Protocols</span></span>

<span data-ttu-id="79f0b-104">Начиная с версии .NET Framework 4.6, классы <xref:System.Net.ServicePointManager?displayProperty=nameWithType> и <xref:System.Net.Security.SslStream?displayProperty=nameWithType> могут использовать один из трех следующих протоколов: Tls1.0, Tls1.1 или Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="79f0b-104">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="79f0b-105">Протокол SSL 3.0 и шифрование RC4 не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="79f0b-105">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="79f0b-106">Последствия</span><span class="sxs-lookup"><span data-stu-id="79f0b-106">Impact</span></span>  

 <span data-ttu-id="79f0b-107">Это изменение влияет:</span><span class="sxs-lookup"><span data-stu-id="79f0b-107">This change affects:</span></span>  
  
- <span data-ttu-id="79f0b-108">на все приложения, использующие протокол SSL для связи с сервером HTTPS или сервером сокетов с помощью любого из следующих типов: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> и <xref:System.Net.Security.SslStream>;</span><span class="sxs-lookup"><span data-stu-id="79f0b-108">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="79f0b-109">на все приложения на стороне сервера, которые нельзя обновить для поддержки Tls1.0, Tls1.1 или Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="79f0b-109">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="79f0b-110">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="79f0b-110">Mitigation</span></span>  

 <span data-ttu-id="79f0b-111">Рекомендуется обновить приложения на стороне сервера для использования Tls1.0, Tls1.1 или Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="79f0b-111">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="79f0b-112">Если это невозможно, или если клиентские приложения не работают, можно использовать класс <xref:System.AppContext>, чтобы отказаться от этой функции одним из двух способов.</span><span class="sxs-lookup"><span data-stu-id="79f0b-112">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="79f0b-113">Программно с помощью фрагмента кода следующего вида:</span><span class="sxs-lookup"><span data-stu-id="79f0b-113">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="79f0b-114">Поскольку объект <xref:System.Net.ServicePointManager> инициализируется только один раз, определение этих параметров совместимости должно быть первым действием приложения.</span><span class="sxs-lookup"><span data-stu-id="79f0b-114">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="79f0b-115">путем добавления следующей строки в раздел [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) файла app.config:</span><span class="sxs-lookup"><span data-stu-id="79f0b-115">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="79f0b-116">Следует, тем не менее, заметить, что отказ от поведения по умолчанию не рекомендуется, поскольку приводит к снижению безопасности приложения.</span><span class="sxs-lookup"><span data-stu-id="79f0b-116">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f0b-117">См. также</span><span class="sxs-lookup"><span data-stu-id="79f0b-117">See also</span></span>

- [<span data-ttu-id="79f0b-118">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="79f0b-118">Application compatibility</span></span>](application-compatibility.md)
