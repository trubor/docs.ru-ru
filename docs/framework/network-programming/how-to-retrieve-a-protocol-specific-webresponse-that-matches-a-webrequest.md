---
title: Практическое руководство. Получение объекта WebResponse, соответствующего объекту WebRequest, для определенного протокола
description: Узнайте, как получить объект WebResponse, соответствующий объекту WebRequest, для определенного протокола в .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 920704bedce478ed5a4f7906379a634a3b2a4e31
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584346"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="637eb-103">Практическое руководство. Получение объекта WebResponse, соответствующего объекту WebRequest, для определенного протокола</span><span class="sxs-lookup"><span data-stu-id="637eb-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>

<span data-ttu-id="637eb-104">В этом примере показано, как получить объект WebResponse, соответствующий объекту WebRequest, для определенного протокола.</span><span class="sxs-lookup"><span data-stu-id="637eb-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="637eb-105">Пример</span><span class="sxs-lookup"><span data-stu-id="637eb-105">Example</span></span>  
  
```csharp  
HttpWebRequest req = (HttpWebRequest)WebRequest.Create("http://www.contoso.com/");
HttpWebResponse resp = (HttpWebResponse)req.GetResponse();
```  
  
```vb  
Dim req As HttpWebRequest = CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)
Dim resp As HttpWebResponse = CType(req.GetResponse(), HttpWebResponse)
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="637eb-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="637eb-106">Compiling the Code</span></span>  

 <span data-ttu-id="637eb-107">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="637eb-107">This example requires:</span></span>  
  
- <span data-ttu-id="637eb-108">Ссылки на пространство имен **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="637eb-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="637eb-109">См. также</span><span class="sxs-lookup"><span data-stu-id="637eb-109">See also</span></span>

- [<span data-ttu-id="637eb-110">Запрос данных</span><span class="sxs-lookup"><span data-stu-id="637eb-110">Requesting Data</span></span>](requesting-data.md)
