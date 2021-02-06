---
description: 'Дополнительные сведения о: объект My. Request'
title: Объект My.Request
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 0b72252e261cd033bfc35c546de5c53a4f3cfe2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640658"
---
# <a name="myrequest-object"></a><span data-ttu-id="1aa44-103">Объект My.Request</span><span class="sxs-lookup"><span data-stu-id="1aa44-103">My.Request Object</span></span>

<span data-ttu-id="1aa44-104">Возвращает объект <xref:System.Web.HttpRequest> для запрашиваемой страницы.</span><span class="sxs-lookup"><span data-stu-id="1aa44-104">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1aa44-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="1aa44-105">Remarks</span></span>  

 <span data-ttu-id="1aa44-106">Объект `My.Request` содержит сведения о текущем HTTP-запросе.</span><span class="sxs-lookup"><span data-stu-id="1aa44-106">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="1aa44-107">Объект `My.Request` доступен только для приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1aa44-107">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aa44-108">Пример</span><span class="sxs-lookup"><span data-stu-id="1aa44-108">Example</span></span>  

 <span data-ttu-id="1aa44-109">Следующий пример получает коллекцию заголовков из `My.Request` объекта и использует `My.Response` объект для записи на страницу ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1aa44-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1aa44-110">См. также</span><span class="sxs-lookup"><span data-stu-id="1aa44-110">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="1aa44-111">Объект My.Response</span><span class="sxs-lookup"><span data-stu-id="1aa44-111">My.Response Object</span></span>](my-response-object.md)
