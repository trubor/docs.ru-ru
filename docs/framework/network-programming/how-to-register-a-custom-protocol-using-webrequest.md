---
description: 'Подробнее о следующем: Практическое руководство. Регистрация пользовательского протокола с помощью WebRequest'
title: Практическое руководство. Регистрация пользовательского протокола с помощью WebRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 7415017f20c0c6ed80570992e249fb8121907de2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785761"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="fe982-103">Практическое руководство. Регистрация пользовательского протокола с помощью WebRequest</span><span class="sxs-lookup"><span data-stu-id="fe982-103">How to: Register a Custom Protocol Using WebRequest</span></span>

<span data-ttu-id="fe982-104">В этом примере показано, как зарегистрировать класс для конкретного протокола, который определен в другом месте.</span><span class="sxs-lookup"><span data-stu-id="fe982-104">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="fe982-105">В этом примере `CustomWebRequestCreator` — пользовательский объект, который реализует метод **Create**, возвращающий объект `CustomWebRequest`.</span><span class="sxs-lookup"><span data-stu-id="fe982-105">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="fe982-106">В примере кода предполагается, что вы написали код `CustomWebRequest`, который реализует пользовательский протокол.</span><span class="sxs-lookup"><span data-stu-id="fe982-106">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe982-107">Пример</span><span class="sxs-lookup"><span data-stu-id="fe982-107">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe982-108">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="fe982-108">Compiling the Code</span></span>  

 <span data-ttu-id="fe982-109">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="fe982-109">This example requires:</span></span>  
  
 <span data-ttu-id="fe982-110">Ссылки на пространство имен <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="fe982-110">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe982-111">См. также</span><span class="sxs-lookup"><span data-stu-id="fe982-111">See also</span></span>

- [<span data-ttu-id="fe982-112">Программирование подключаемых протоколов</span><span class="sxs-lookup"><span data-stu-id="fe982-112">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
