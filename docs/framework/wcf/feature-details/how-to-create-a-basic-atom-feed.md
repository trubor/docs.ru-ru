---
description: См. Дополнительные сведения о создании базового веб-канала Atom.
title: Практическое руководство. Создание базового канала Atom
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 4f4fa6e5b4e2b6935fb51cbc200e5ed9e03843ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734793"
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="ac0cc-103">Практическое руководство. Создание базового канала Atom</span><span class="sxs-lookup"><span data-stu-id="ac0cc-103">How to: Create a Basic Atom Feed</span></span>

<span data-ttu-id="ac0cc-104">Windows Communication Foundation (WCF) позволяет создать службу, предоставляющую канал синдикации.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-104">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="ac0cc-105">В этом разделе рассматривается процесс создания службы синдикации, предоставляющей веб-канал синдикации Atom.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-105">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="ac0cc-106">Создание базовой службы синдикации</span><span class="sxs-lookup"><span data-stu-id="ac0cc-106">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="ac0cc-107">Определите контракт службы с помощью интерфейса, отмеченного атрибутом <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="ac0cc-108">Каждая операция, предоставляемая как веб-канал синдикации, должна возвращать объект <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-108">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="ac0cc-109">Все операции службы, которые применяют атрибут <xref:System.ServiceModel.Web.WebGetAttribute>, сопоставляются с запросами HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-109">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="ac0cc-110">Чтобы сопоставить операцию с другим методом HTTP, используйте <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-110">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="ac0cc-111">Дополнительные сведения см. [в разделе как создать базовую веб-службу HTTP WCF](how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="ac0cc-111">For more information, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="ac0cc-112">Реализуйте контракт службы.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-112">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="ac0cc-113">Создайте объект <xref:System.ServiceModel.Syndication.SyndicationFeed>, затем добавьте автора, категорию и описание.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-113">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="ac0cc-114">Создайте несколько объектов <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-114">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="ac0cc-115">Добавьте объекты <xref:System.ServiceModel.Syndication.SyndicationItem> в веб-канал.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-115">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="ac0cc-116">Возвратите веб-канал.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-116">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="ac0cc-117">Размещение службы</span><span class="sxs-lookup"><span data-stu-id="ac0cc-117">To host the service</span></span>  
  
1. <span data-ttu-id="ac0cc-118">Создание объекта <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-118">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="ac0cc-119">Откройте узел службы, загрузите веб-канал из службы, отобразите веб-канал и дождитесь нажатия клавиши ВВОД пользователем.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-119">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="ac0cc-120">Вызов GetBlog() c HTTP GET</span><span class="sxs-lookup"><span data-stu-id="ac0cc-120">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="ac0cc-121">Откройте Internet Explorer, введите следующий URL-адрес и нажмите клавишу ВВОД: `http://localhost:8000/BlogService/GetBlog`</span><span class="sxs-lookup"><span data-stu-id="ac0cc-121">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`</span></span>  
  
     <span data-ttu-id="ac0cc-122">URL-адрес содержит базовый адрес службы ( `http://localhost:8000/BlogService` ), относительный адрес конечной точки и операцию службы для вызова.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-122">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="ac0cc-123">Вызов GetBlog() из кода</span><span class="sxs-lookup"><span data-stu-id="ac0cc-123">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="ac0cc-124">Создайте <xref:System.Xml.XmlReader> с базовым адресом и вызываемым методом.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-124">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="ac0cc-125">Вызовите статический метод <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>, передав ему только что созданный объект <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-125">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="ac0cc-126">Это вызывает операцию службы и заполняет новый <xref:System.ServiceModel.Syndication.SyndicationFeed> с помощью модуля форматирования, возвращенного от операции службы.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-126">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="ac0cc-127">Откройте объект веб-канала.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-127">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="ac0cc-128">Пример</span><span class="sxs-lookup"><span data-stu-id="ac0cc-128">Example</span></span>  

 <span data-ttu-id="ac0cc-129">Ниже приведен полный код этого примера.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-129">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac0cc-130">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="ac0cc-130">Compiling the Code</span></span>  

 <span data-ttu-id="ac0cc-131">При компиляции приведенного выше кода задайте ссылки на файлы System.ServiceModel.dll и System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="ac0cc-131">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac0cc-132">См. также</span><span class="sxs-lookup"><span data-stu-id="ac0cc-132">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
