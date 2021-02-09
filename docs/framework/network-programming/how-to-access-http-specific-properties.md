---
description: 'Подробнее о следующем: Практическое руководство. Доступ к свойствам, относящимся с HTTP'
title: Практическое руководство. Доступ к свойствам, относящимся с HTTP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: a54ef247b479cf6cdec8dc28732304cf03b0b202
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729306"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="18642-103">Практическое руководство. Доступ к свойствам, относящимся с HTTP</span><span class="sxs-lookup"><span data-stu-id="18642-103">How to: Access HTTP-Specific Properties</span></span>

<span data-ttu-id="18642-104">В этом примере показано, как отключить функции HTTP **Keep-alive** и получить номер версии протокола с веб-сервера.</span><span class="sxs-lookup"><span data-stu-id="18642-104">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18642-105">Пример</span><span class="sxs-lookup"><span data-stu-id="18642-105">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="18642-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="18642-106">Compiling the Code</span></span>  

 <span data-ttu-id="18642-107">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="18642-107">This example requires:</span></span>  
  
- <span data-ttu-id="18642-108">Ссылки на пространство имен **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="18642-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18642-109">См. также</span><span class="sxs-lookup"><span data-stu-id="18642-109">See also</span></span>

- [<span data-ttu-id="18642-110">Доступ к Интернету через прокси-сервер</span><span class="sxs-lookup"><span data-stu-id="18642-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="18642-111">Использование протоколов приложений</span><span class="sxs-lookup"><span data-stu-id="18642-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="18642-112">HTTP</span><span class="sxs-lookup"><span data-stu-id="18642-112">HTTP</span></span>](http.md)
