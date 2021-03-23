---
title: Как установить заголовки в клиентском запросе (службы WCF Data Services)
description: Узнайте, как с помощью обработчика событий Сендингрекуест добавить новый заголовок в сообщение запроса перед его отправкой в службу данных в службы данных WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: cfd2adbbf0dccafffef11b0f501db4832bc5e006
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805809"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Как установить заголовки в клиентском запросе (службы WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

При использовании клиентской библиотеки службы данных WCF для доступа к службе данных, которая поддерживает Open Data Protocol (OData), клиентская библиотека автоматически задает нужные заголовки HTTP в сообщениях запроса, отправляемых службе данных. Однако клиентская библиотека не может определить заголовки сообщений, которые необходимы в некоторых случаях, например когда службе данных требуется проверка подлинности на основе утверждений или файлы cookies. Дополнительные сведения см. в разделе [Securing WCF Data Services](securing-wcf-data-services.md#clientAuthentication). В этих случаях необходимо вручную установить заголовки сообщений в запросе перед отправкой. В примере в этом разделе показано, как обработать событие <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> и добавить новый заголовок в сообщение запроса перед его отправкой службе данных.  
  
 Пример в этом разделе использует образец службы данных Northwind и автоматически сформированные клиентские классы службы данных. Эта служба и классы данных клиента создаются при завершении [краткого руководства по службы данных WCF](quickstart-wcf-data-services.md). Вы также можете использовать [учебную службу данных Northwind](https://services.odata.org/Northwind/Northwind.svc/) , опубликованную на веб-сайте OData. Этот образец службы данных доступен только для чтения, и попытка сохранить изменения возвращает ошибку. Для примера служб данных на веб-сайте OData разрешена анонимная проверка подлинности.  
  
## <a name="example"></a>Пример  

 В следующем примере регистрируется обработчик для события <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>, после чего службе данных отправляется запрос.  
  
> [!NOTE]
> Если служба данных требует задавать заголовок сообщения вручную для каждого запроса, попробуйте зарегистрировать обработчик для события <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>, переопределив частичный метод `OnContextCreated` в контейнере сущностей, который представляет службу данных, то есть в данном примере `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Пример  

 Следующей метод обрабатывает событие <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> и добавляет заголовок проверки подлинности в запрос.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>См. также раздел

- [Защита служб WCF Data Services](securing-wcf-data-services.md)
- [Библиотека клиентов служб данных WCF](wcf-data-services-client-library.md)
