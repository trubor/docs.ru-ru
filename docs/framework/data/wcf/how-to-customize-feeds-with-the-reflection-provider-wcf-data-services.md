---
description: Дополнительные сведения см. в статье Настройка веб-каналов с помощью поставщика отражения (службы данных WCF).
title: Практическое руководство. Настройка каналов с поставщиком отражения (службы данных WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 91ac9cd3a5e882714335ce1d4ef29510d4640534
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765637"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="4b796-103">Практическое руководство. Настройка каналов с поставщиком отражения (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="4b796-103">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="4b796-104">Службы данных WCF позволяет настроить сериализацию Atom в ответе службы данных, чтобы свойства сущности могли быть сопоставлены с неиспользуемыми элементами, определенными в протоколе AtomPub.</span><span class="sxs-lookup"><span data-stu-id="4b796-104">WCF Data Services enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="4b796-105">Этот раздел показывает, как настроить атрибуты сопоставления типов сущностей в модели данных, определенной с помощью поставщика отражения.</span><span class="sxs-lookup"><span data-stu-id="4b796-105">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="4b796-106">Дополнительные сведения см. в разделе [Настройка веб-канала](feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b796-106">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="4b796-107">Модель данных для этого примера определяется в разделе [как создать службу данных с помощью поставщика отражения.](create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="4b796-107">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b796-108">Пример</span><span class="sxs-lookup"><span data-stu-id="4b796-108">Example</span></span>  

 <span data-ttu-id="4b796-109">В следующем примере оба свойства типа `Order` отображаются на существующие элементы Atom.</span><span class="sxs-lookup"><span data-stu-id="4b796-109">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="4b796-110">Свойство `Product` типа `Item` отображается на специализированный атрибут канала в отдельном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="4b796-110">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="4b796-111">Пример</span><span class="sxs-lookup"><span data-stu-id="4b796-111">Example</span></span>  

 <span data-ttu-id="4b796-112">Предыдущий пример возвращает следующий результат для URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="4b796-112">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="4b796-113">См. также</span><span class="sxs-lookup"><span data-stu-id="4b796-113">See also</span></span>

- [<span data-ttu-id="4b796-114">Поставщик отражения</span><span class="sxs-lookup"><span data-stu-id="4b796-114">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
