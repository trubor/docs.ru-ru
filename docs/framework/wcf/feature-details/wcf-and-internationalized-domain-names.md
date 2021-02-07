---
description: 'Дополнительные сведения: WCF и международные доменные имена'
title: WCF и международные доменные имена
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: e7e1ad999d7de749b4f8cf4b3efd823befffba43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755997"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="38ea4-103">WCF и международные доменные имена</span><span class="sxs-lookup"><span data-stu-id="38ea4-103">WCF and Internationalized Domain Names</span></span>

<span data-ttu-id="38ea4-104">Добавлена поддержка служб WCF с интернационализированными именами домена (IDN).</span><span class="sxs-lookup"><span data-stu-id="38ea4-104">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="38ea4-105">Интернационализированное имя домена представляет собой имя домена, содержащее символы, не входящие в набор символов ASCII.</span><span class="sxs-lookup"><span data-stu-id="38ea4-105">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="38ea4-106">Данная поддержка включает в себя как возможность размещения службы WCF с именем IDN, так и возможность диалога клиента WCF с веб-службой с именем IDN.</span><span class="sxs-lookup"><span data-stu-id="38ea4-106">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="38ea4-107">System.Uri и IDN</span><span class="sxs-lookup"><span data-stu-id="38ea4-107">System.Uri and IDN</span></span>  

 <span data-ttu-id="38ea4-108">У объекта класса <xref:System.Uri> есть два свойства: <xref:System.Uri.Host%2A> и <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="38ea4-108"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="38ea4-109">Эти свойства содержат значения Unicode или Punycode в зависимости от параметров конфигурации IDN.</span><span class="sxs-lookup"><span data-stu-id="38ea4-109">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="38ea4-110">IDN активируется в файле конфигурации приложения с помощью следующего кода XML</span><span class="sxs-lookup"><span data-stu-id="38ea4-110">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="38ea4-111">\<idn>Элемент содержит атрибут Enabled, для которого можно задать одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="38ea4-111">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1. <span data-ttu-id="38ea4-112">"None"</span><span class="sxs-lookup"><span data-stu-id="38ea4-112">"None"</span></span>  
  
2. <span data-ttu-id="38ea4-113">"Аллексцептинтранет"</span><span class="sxs-lookup"><span data-stu-id="38ea4-113">"AllExceptIntranet"</span></span>  
  
3. <span data-ttu-id="38ea4-114">"All"</span><span class="sxs-lookup"><span data-stu-id="38ea4-114">"All"</span></span>  
  
 <span data-ttu-id="38ea4-115">Если для параметра IDN задано значение "нет", никакие преобразования с помощью URI. Host или URI. Днссафехост не выполняются.</span><span class="sxs-lookup"><span data-stu-id="38ea4-115">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="38ea4-116">Если для параметра IDN задано значение "ALL", URI. Узел остается в Юникоде и URI. Днссафехост преобразуется в Punycode.</span><span class="sxs-lookup"><span data-stu-id="38ea4-116">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="38ea4-117">Если для параметра IDN задано значение "Аллексцептинтранет", URI. Днссафехост преобразуется в Punycode для адресов Интернета и остается в Юникоде для адресов интрасети.</span><span class="sxs-lookup"><span data-stu-id="38ea4-117">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="38ea4-118">Этот параметр важен для верного разрешения имен DNS.</span><span class="sxs-lookup"><span data-stu-id="38ea4-118">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="38ea4-119">Обратите внимание, что он не требует настройки в Windows 8 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="38ea4-119">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="38ea4-120">Никогда не следует вводить адрес вручную с использованием Punycode.</span><span class="sxs-lookup"><span data-stu-id="38ea4-120">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="38ea4-121">WCF преобразует адрес в соответствии с примененными параметрами конфигурации.</span><span class="sxs-lookup"><span data-stu-id="38ea4-121">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="38ea4-122">При добавлении в applicationHost.exe.config символов Юникода сохраните файл в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="38ea4-122">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ea4-123">См. также</span><span class="sxs-lookup"><span data-stu-id="38ea4-123">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
