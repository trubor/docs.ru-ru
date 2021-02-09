---
description: 'Узнайте подробнее о: Доступ к веб-службам приложения (Visual Basic)'
title: Доступ к веб-службам приложения
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: 4efd35ed7c8f4251a749b85a45242af299a51e6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797891"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="43279-103">Доступ к веб-службам приложения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43279-103">Accessing Application Web Services (Visual Basic)</span></span>

<span data-ttu-id="43279-104">Объект `My.WebServices` предоставляет экземпляр каждой веб-службы, на которую ссылается текущий проект.</span><span class="sxs-lookup"><span data-stu-id="43279-104">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="43279-105">Каждый экземпляр создается по запросу.</span><span class="sxs-lookup"><span data-stu-id="43279-105">Each instance is instantiated on demand.</span></span> <span data-ttu-id="43279-106">Доступ к этим веб-службам можно получить через свойства объекта `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="43279-106">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="43279-107">Имя свойства совпадает с именем веб-службы, к которой обращается свойство.</span><span class="sxs-lookup"><span data-stu-id="43279-107">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="43279-108">Любой класс, наследуемый от <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>, является веб-службой.</span><span class="sxs-lookup"><span data-stu-id="43279-108">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>

## <a name="tasks"></a><span data-ttu-id="43279-109">Задания</span><span class="sxs-lookup"><span data-stu-id="43279-109">Tasks</span></span>

<span data-ttu-id="43279-110">В следующей таблице перечислены возможные способы доступа к веб-службам, на которые ссылается приложение.</span><span class="sxs-lookup"><span data-stu-id="43279-110">The following table lists possible ways to access Web services referenced by an application.</span></span>

|<span data-ttu-id="43279-111">Кому</span><span class="sxs-lookup"><span data-stu-id="43279-111">To</span></span>|<span data-ttu-id="43279-112">См.</span><span class="sxs-lookup"><span data-stu-id="43279-112">See</span></span>|
|---|---|
|<span data-ttu-id="43279-113">Вызов веб-службы</span><span class="sxs-lookup"><span data-stu-id="43279-113">Call a Web service</span></span>|[<span data-ttu-id="43279-114">Объект My.WebServices</span><span class="sxs-lookup"><span data-stu-id="43279-114">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)|
|<span data-ttu-id="43279-115">Вызов веб-службы в асинхронном режиме и обработка события при его завершении</span><span class="sxs-lookup"><span data-stu-id="43279-115">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="43279-116">Практическое руководство. Асинхронный вызов веб-службы</span><span class="sxs-lookup"><span data-stu-id="43279-116">How to: Call a Web Service Asynchronously</span></span>](how-to-call-a-web-service-asynchronously.md)|

## <a name="see-also"></a><span data-ttu-id="43279-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="43279-117">See also</span></span>

- [<span data-ttu-id="43279-118">Объект My.WebServices</span><span class="sxs-lookup"><span data-stu-id="43279-118">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
