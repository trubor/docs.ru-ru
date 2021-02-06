---
description: 'Дополнительные сведения о: объект My. Response'
title: Объект My.Response
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 551528356040539994251cb66a905d0249f482da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640619"
---
# <a name="myresponse-object"></a><span data-ttu-id="a14b6-103">Объект My.Response</span><span class="sxs-lookup"><span data-stu-id="a14b6-103">My.Response Object</span></span>

<span data-ttu-id="a14b6-104">Возвращает <xref:System.Web.HttpResponse> объект, связанный с объектом <xref:System.Web.UI.Page> .</span><span class="sxs-lookup"><span data-stu-id="a14b6-104">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="a14b6-105">Этот объект позволяет отправлять клиенту данные HTTP-ответа и содержит сведения об этом ответе.</span><span class="sxs-lookup"><span data-stu-id="a14b6-105">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a14b6-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="a14b6-106">Remarks</span></span>  

 <span data-ttu-id="a14b6-107">`My.Response`Объект содержит текущий объект, <xref:System.Web.HttpResponse> связанный со страницей.</span><span class="sxs-lookup"><span data-stu-id="a14b6-107">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="a14b6-108">`My.Response`Объект доступен только для приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a14b6-108">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a14b6-109">Пример</span><span class="sxs-lookup"><span data-stu-id="a14b6-109">Example</span></span>  

 <span data-ttu-id="a14b6-110">Следующий пример получает коллекцию заголовков из `My.Request` объекта и использует `My.Response` объект для записи на страницу ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a14b6-110">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a14b6-111">См. также</span><span class="sxs-lookup"><span data-stu-id="a14b6-111">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="a14b6-112">Объект My.Request</span><span class="sxs-lookup"><span data-stu-id="a14b6-112">My.Request Object</span></span>](my-request-object.md)
