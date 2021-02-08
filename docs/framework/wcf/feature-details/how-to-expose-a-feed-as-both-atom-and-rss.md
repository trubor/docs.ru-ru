---
description: Дополнительные сведения о том, как предоставить веб-канал как Atom и RSS.
title: Практическое руководство. Как предоставить доступ к каналу в форматах Atom и RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 5afe08b2c1d9fc687563e124061fe7fb59257180
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793783"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="65464-103">Практическое руководство. Как предоставить доступ к каналу в форматах Atom и RSS</span><span class="sxs-lookup"><span data-stu-id="65464-103">How to: Expose a Feed as Both Atom and RSS</span></span>

<span data-ttu-id="65464-104">Windows Communication Foundation (WCF) позволяет создать службу, предоставляющую канал синдикации.</span><span class="sxs-lookup"><span data-stu-id="65464-104">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="65464-105">В этом разделе рассматривается процесс создания службы синдикации, предоставляющей веб-канал синдикации с помощью Atom 1.0 и RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="65464-105">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="65464-106">Эта служба предоставляет одну конечную точку, которая может вернуть любой формат синдикации.</span><span class="sxs-lookup"><span data-stu-id="65464-106">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="65464-107">В целях упрощения в данном образце используется резидентная служба.</span><span class="sxs-lookup"><span data-stu-id="65464-107">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="65464-108">В рабочей среде служба такого типа размещается в IIS или WAS.</span><span class="sxs-lookup"><span data-stu-id="65464-108">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="65464-109">Дополнительные сведения о различных вариантах размещения WCF см. в разделе [Размещение](hosting.md).</span><span class="sxs-lookup"><span data-stu-id="65464-109">For more information about the different WCF hosting options, see [Hosting](hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="65464-110">Создание базовой службы синдикации</span><span class="sxs-lookup"><span data-stu-id="65464-110">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="65464-111">Определите контракт службы с помощью интерфейса, отмеченного атрибутом <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="65464-111">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="65464-112">Каждая операция, предоставляемая как веб-канал синдикации, возвращает объект <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="65464-112">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="65464-113">Обратите внимание на параметры для <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="65464-113">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="65464-114">`UriTemplate` указывает URL-адрес, используемый для вызова этой операции службы.</span><span class="sxs-lookup"><span data-stu-id="65464-114">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="65464-115">Строка для этого параметра содержит литералы и переменную в фигурных скобках ({*Format*}).</span><span class="sxs-lookup"><span data-stu-id="65464-115">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="65464-116">Эта переменная соответствует параметру `format` операции службы.</span><span class="sxs-lookup"><span data-stu-id="65464-116">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="65464-117">Для получения дополнительной информации см. <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="65464-117">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="65464-118">`BodyStyle` влияет на способ записи сообщений, отправляемых и получаемых этой операцией службы.</span><span class="sxs-lookup"><span data-stu-id="65464-118">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="65464-119"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> указывает, что данные, отправляемые и получаемые этой операцией службы, не заключаются в оболочку из XML-элементов, определенных в инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="65464-119"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="65464-120">Для получения дополнительной информации см. <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="65464-120">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="65464-121">Используйте атрибут <xref:System.ServiceModel.ServiceKnownTypeAttribute>, чтобы задать, какие типы возвращаются операциями службы в этом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="65464-121">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="65464-122">Реализуйте контракт службы.</span><span class="sxs-lookup"><span data-stu-id="65464-122">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="65464-123">Создайте объект <xref:System.ServiceModel.Syndication.SyndicationFeed>, затем добавьте автора, категорию и описание.</span><span class="sxs-lookup"><span data-stu-id="65464-123">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="65464-124">Создайте несколько объектов <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="65464-124">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="65464-125">Добавьте объекты <xref:System.ServiceModel.Syndication.SyndicationItem> в веб-канал.</span><span class="sxs-lookup"><span data-stu-id="65464-125">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="65464-126">Используйте параметр формата, чтобы был возвращен необходимый формат.</span><span class="sxs-lookup"><span data-stu-id="65464-126">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="65464-127">Размещение службы</span><span class="sxs-lookup"><span data-stu-id="65464-127">To host the service</span></span>  
  
1. <span data-ttu-id="65464-128">Создание объекта <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="65464-128">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="65464-129">Класс <xref:System.ServiceModel.Web.WebServiceHost> автоматически добавляет конечную точку по базовому адресу службы, если конечная точка не указана ни в коде, ни в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="65464-129">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="65464-130">В этом образце конечные точки не указаны, и поэтому предоставляется доступ к конечной точке по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="65464-130">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="65464-131">Откройте узел службы, загрузите веб-канал из службы, отобразите веб-канал и дождитесь нажатия клавиши ВВОД пользователем.</span><span class="sxs-lookup"><span data-stu-id="65464-131">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="65464-132">Вызов GetBlog с помощью HTTP GET</span><span class="sxs-lookup"><span data-stu-id="65464-132">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="65464-133">Откройте Internet Explorer, введите следующий URL-адрес и нажмите клавишу ВВОД: `http://localhost:8000/BlogService/GetBlog` .</span><span class="sxs-lookup"><span data-stu-id="65464-133">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="65464-134">URL-адрес содержит базовый адрес службы ( `http://localhost:8000/BlogService` ), относительный адрес конечной точки и операцию службы для вызова.</span><span class="sxs-lookup"><span data-stu-id="65464-134">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="65464-135">Вызов GetBlog() из кода</span><span class="sxs-lookup"><span data-stu-id="65464-135">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="65464-136">Создайте <xref:System.Xml.XmlReader> с базовым адресом и вызываемым методом.</span><span class="sxs-lookup"><span data-stu-id="65464-136">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="65464-137">Вызовите статический метод <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>, передав ему только что созданный объект <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="65464-137">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="65464-138">Это вызывает операцию службы и заполняет новый <xref:System.ServiceModel.Syndication.SyndicationFeed> с помощью модуля форматирования, возвращенного от операции службы.</span><span class="sxs-lookup"><span data-stu-id="65464-138">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="65464-139">Откройте объект веб-канала.</span><span class="sxs-lookup"><span data-stu-id="65464-139">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="65464-140">Пример</span><span class="sxs-lookup"><span data-stu-id="65464-140">Example</span></span>  

 <span data-ttu-id="65464-141">Ниже приведен полный код этого примера.</span><span class="sxs-lookup"><span data-stu-id="65464-141">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="65464-142">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="65464-142">Compiling the Code</span></span>  

 <span data-ttu-id="65464-143">При компиляции приведенного выше кода задайте ссылки на файлы System.ServiceModel.dll и System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="65464-143">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65464-144">См. также</span><span class="sxs-lookup"><span data-stu-id="65464-144">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
