---
title: Практическое руководство. Переопределение глобальных прокси-серверов
description: Следуйте инструкциям в приведенном ниже примере, чтобы переопределить выбор глобального прокси-сервера путем отправки запроса на URL-адрес. При этом выделенный фрагмент переопределяется с помощью прокси-сервера.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 8931cdc471b957447277c333ba482a0cec0e6aa5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265743"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="63bc0-103">Практическое руководство. Переопределение глобальных прокси-серверов</span><span class="sxs-lookup"><span data-stu-id="63bc0-103">How to: Override a Global Proxy Selection</span></span>

<span data-ttu-id="63bc0-104">В этом примере класс **WebRequest** отправляется на веб-сайт `www.contoso.com`, который переопределяет глобальные прокси-серверы прокси-сервером с именем `alternateproxy` на порту 80.</span><span class="sxs-lookup"><span data-stu-id="63bc0-104">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63bc0-105">Пример</span><span class="sxs-lookup"><span data-stu-id="63bc0-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63bc0-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="63bc0-106">Compiling the Code</span></span>  

 <span data-ttu-id="63bc0-107">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="63bc0-107">This example requires:</span></span>  
  
- <span data-ttu-id="63bc0-108">Директива [`using`](../../csharp/language-reference/keywords/using-directive.md) для пространства имен **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="63bc0-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bc0-109">См. также</span><span class="sxs-lookup"><span data-stu-id="63bc0-109">See also</span></span>

- [<span data-ttu-id="63bc0-110">Использование протоколов приложений</span><span class="sxs-lookup"><span data-stu-id="63bc0-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="63bc0-111">Доступ к Интернету через прокси-сервер</span><span class="sxs-lookup"><span data-stu-id="63bc0-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
