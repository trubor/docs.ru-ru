---
description: 'Дополнительные сведения: синхронные сценарии с использованием HTTP, TCP или Named-Pipe'
title: Синхронные сценарии с использованием HTTP, TCP или именованного канала
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: fd6605be99a9419de27f000b378720adf0ae1a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635419"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="0d477-103">Синхронные сценарии с использованием HTTP, TCP или именованного канала</span><span class="sxs-lookup"><span data-stu-id="0d477-103">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>

<span data-ttu-id="0d477-104">В этом разделе описываются действия и перенаправления для различных сценариев синхронных запросов/ответов (с однопотоковым клиентом, с использованием HTTP, TCP или именованного канала).</span><span class="sxs-lookup"><span data-stu-id="0d477-104">This topic describes the activities and transfers for different synchronous request/reply scenarios, with a single-threaded client, using HTTP, TCP or named pipe.</span></span> <span data-ttu-id="0d477-105">Дополнительные сведения о многопоточных запросах см. в статье [асинхронные сценарии с использованием HTTP, TCP или именованного канала](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) .</span><span class="sxs-lookup"><span data-stu-id="0d477-105">See [Asynchronous Scenarios using HTTP, TCP, or Named-Pipe](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) for more information on multi-threaded requests.</span></span>  
  
## <a name="synchronous-requestreply-without-errors"></a><span data-ttu-id="0d477-106">Синхронный запрос/ответ без ошибок</span><span class="sxs-lookup"><span data-stu-id="0d477-106">Synchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="0d477-107">В этом разделе описываются действия и перенаправления для реального сценария синхронных запросов/ответов (с однопотоковым клиентом).</span><span class="sxs-lookup"><span data-stu-id="0d477-107">This section describes the activities and transfers for a valid synchronous request/reply scenario, with single-threaded client.</span></span>  
  
### <a name="client"></a><span data-ttu-id="0d477-108">Клиент</span><span class="sxs-lookup"><span data-stu-id="0d477-108">Client</span></span>  
  
#### <a name="establishing-communication-with-service-endpoint"></a><span data-ttu-id="0d477-109">Установка связи с конечной точкой службы</span><span class="sxs-lookup"><span data-stu-id="0d477-109">Establishing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="0d477-110">Создается и открывается клиент.</span><span class="sxs-lookup"><span data-stu-id="0d477-110">A client is constructed and opened.</span></span> <span data-ttu-id="0d477-111">Для каждого из этих шагов внешнее действие (A) передается в действие "конструировать клиент" (B) и "открыть клиент" (C) соответственно.</span><span class="sxs-lookup"><span data-stu-id="0d477-111">For each of these steps, the ambient activity (A) is transferred to a "Construct Client" (B) and "Open Client" (C) activity respectively.</span></span> <span data-ttu-id="0d477-112">Для каждого действия, которому оно перенаправляется, внешнее действие приостанавливается до момента обратного перенаправления (т. е. до выполнения кода ServiceModel).</span><span class="sxs-lookup"><span data-stu-id="0d477-112">For each activity being transferred to, the ambient activity is suspended until there is a transfer back, that is, until ServiceModel code is executed.</span></span>  
  
#### <a name="making-a-request-to-service-endpoint"></a><span data-ttu-id="0d477-113">Создание запроса для конечной точки службы</span><span class="sxs-lookup"><span data-stu-id="0d477-113">Making a Request to Service Endpoint</span></span>  

 <span data-ttu-id="0d477-114">Внешнее действие передается в действие "ProcessAction" (D).</span><span class="sxs-lookup"><span data-stu-id="0d477-114">The ambient activity is transferred to a "ProcessAction" (D) activity.</span></span> <span data-ttu-id="0d477-115">В рамках этого действия отправляется сообщение запроса и принимается сообщение ответа.</span><span class="sxs-lookup"><span data-stu-id="0d477-115">Within this activity, a request message is sent, and a response message is received.</span></span> <span data-ttu-id="0d477-116">Действие прекращается, когда управление возвращается пользовательскому коду.</span><span class="sxs-lookup"><span data-stu-id="0d477-116">The activity ends when control returns to user code.</span></span> <span data-ttu-id="0d477-117">Поскольку этот запрос является синхронным, внешнее действие приостанавливается до возврата управления.</span><span class="sxs-lookup"><span data-stu-id="0d477-117">Because this is a synchronous request, the ambient activity suspends until control returns.</span></span>  
  
#### <a name="closing-communication-with-service-endpoint"></a><span data-ttu-id="0d477-118">Закрытие связи с конечной точкой службы</span><span class="sxs-lookup"><span data-stu-id="0d477-118">Closing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="0d477-119">Действие «закрыть» (I) клиента создается из внешнего действия.</span><span class="sxs-lookup"><span data-stu-id="0d477-119">The client's close activity (I) is created from the ambient activity.</span></span> <span data-ttu-id="0d477-120">Оно идентично действиям "создать" и "открыть".</span><span class="sxs-lookup"><span data-stu-id="0d477-120">This is identical to new and open.</span></span>  
  
### <a name="server"></a><span data-ttu-id="0d477-121">Сервер</span><span class="sxs-lookup"><span data-stu-id="0d477-121">Server</span></span>  
  
#### <a name="setting-up-a-service-host"></a><span data-ttu-id="0d477-122">Настройка узла службы</span><span class="sxs-lookup"><span data-stu-id="0d477-122">Setting up a Service Host</span></span>  

 <span data-ttu-id="0d477-123">Действия «создать» и «открыть» (N и O) узла ServiceHost создаются из внешнего действия (M).</span><span class="sxs-lookup"><span data-stu-id="0d477-123">The ServiceHost’s new and open activities (N and O) are created from the ambient activity (M).</span></span>  
  
 <span data-ttu-id="0d477-124">Действие прослушивания (P) создается при открывании узла ServiceHost для каждого прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="0d477-124">A listener activity (P) is created from opening a ServiceHost for each listener.</span></span> <span data-ttu-id="0d477-125">Действие прослушивания ожидает получения и обработки данных.</span><span class="sxs-lookup"><span data-stu-id="0d477-125">The listener activity waits to receive and process data.</span></span>  
  
#### <a name="receiving-data-on-the-wire"></a><span data-ttu-id="0d477-126">Получение данных по сети</span><span class="sxs-lookup"><span data-stu-id="0d477-126">Receiving Data on the Wire</span></span>  

 <span data-ttu-id="0d477-127">Когда данные поступают на канал, создается действие "Рецеивебитес", если оно еще не существует (Q) для обработки полученных данных.</span><span class="sxs-lookup"><span data-stu-id="0d477-127">When data arrives on the wire, a "ReceiveBytes" activity is created if it does not already exist (Q) to process the received data.</span></span> <span data-ttu-id="0d477-128">Это действие можно использовать повторно для нескольких сообщений в пределах одного соединения или очереди.</span><span class="sxs-lookup"><span data-stu-id="0d477-128">This activity can be reused for multiple messages within a connection or queue.</span></span>  
  
 <span data-ttu-id="0d477-129">Действие ReceiveBytes запускает действие ProcessMessage (R) при наличии достаточной информации для формирования сообщения действия SOAP.</span><span class="sxs-lookup"><span data-stu-id="0d477-129">The ReceiveBytes activity launches a ProcessMessage activity (R) if it has enough data to form a SOAP action message.</span></span>  
  
 <span data-ttu-id="0d477-130">При действии R обрабатываются заголовки сообщений и проверяется заголовок activityID.</span><span class="sxs-lookup"><span data-stu-id="0d477-130">In activity R, the message headers are processed, and the activityID header is verified.</span></span> <span data-ttu-id="0d477-131">Если этот заголовок имеется, идентификатору действия присваивается значение ProcessAction. В противном случае создается новый идентификатор.</span><span class="sxs-lookup"><span data-stu-id="0d477-131">If this header is present, the activity ID is set to the ProcessAction activity; otherwise, a new ID is created.</span></span>  
  
 <span data-ttu-id="0d477-132">При обработке вызова создается действие ProcessAction (S), и выполняется перенаправление на это действие.</span><span class="sxs-lookup"><span data-stu-id="0d477-132">ProcessAction activity (S) is created and being transferred to, when the call is processed.</span></span> <span data-ttu-id="0d477-133">Данное действие завершается при полном завершении обработки, связанной с входящим сообщением, включая выполнение пользовательского кода (T) и отправку ответного сообщения (если она предусмотрена).</span><span class="sxs-lookup"><span data-stu-id="0d477-133">This activity ends when all processing related to the incoming message is completed, including executing user code (T) and sending the response message if applicable.</span></span>  
  
#### <a name="closing-a-service-host"></a><span data-ttu-id="0d477-134">Закрытие узла службы</span><span class="sxs-lookup"><span data-stu-id="0d477-134">Closing a Service Host</span></span>  

 <span data-ttu-id="0d477-135">Действие "закрыть" (Z) узла ServiceHost создается из внешнего действия.</span><span class="sxs-lookup"><span data-stu-id="0d477-135">The ServiceHost’s close activity (Z) is created from the ambient activity.</span></span>  
  
 ![Диаграмма, на которой показаны Синхронные сценарии: HTTP, TCP или именованные каналы.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 <span data-ttu-id="0d477-137">В \<A: name> `A` — это символ ярлыка, описывающий действие в предыдущем тексте и в таблице 3.</span><span class="sxs-lookup"><span data-stu-id="0d477-137">In \<A: name>, `A` is a shortcut symbol that describes the activity in the previous text and in table 3.</span></span> <span data-ttu-id="0d477-138">`Name` представляет собой сокращенное имя действия.</span><span class="sxs-lookup"><span data-stu-id="0d477-138">`Name` is a shortened name of the activity.</span></span>  
  
 <span data-ttu-id="0d477-139">Если значение `propagateActivity` = `true` равно, действие обработки для клиента и службы имеют одинаковый идентификатор действия.</span><span class="sxs-lookup"><span data-stu-id="0d477-139">If `propagateActivity`=`true`, Process Action on both the client and service have the same activity ID.</span></span>  
  
## <a name="synchronous-requestreply-with-errors"></a><span data-ttu-id="0d477-140">Синхронный запрос/ответ с ошибками</span><span class="sxs-lookup"><span data-stu-id="0d477-140">Synchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="0d477-141">Единственное отличие от предыдущего сценария заключается в том, что в качестве ответного сообщения возвращается сообщение об ошибке SOAP.</span><span class="sxs-lookup"><span data-stu-id="0d477-141">The only difference with the previous scenario is that a SOAP fault message is returned as a response message.</span></span> <span data-ttu-id="0d477-142">Если `propagateActivity` = `true` значение равно, идентификатор действия сообщения запроса добавляется в сообщение об ошибке SOAP.</span><span class="sxs-lookup"><span data-stu-id="0d477-142">If `propagateActivity`=`true`, the activity ID of the request message is added to the SOAP fault message.</span></span>  
  
## <a name="synchronous-one-way-without-errors"></a><span data-ttu-id="0d477-143">Синхронная односторонняя связь без ошибок</span><span class="sxs-lookup"><span data-stu-id="0d477-143">Synchronous One-Way without Errors</span></span>  

 <span data-ttu-id="0d477-144">Единственное отличие от первого сценария заключается в том, что на сервер не возвращается сообщение.</span><span class="sxs-lookup"><span data-stu-id="0d477-144">The only difference with the first scenario is that no message is returned to the server.</span></span> <span data-ttu-id="0d477-145">Для протоколов, основанных на HTTP, на клиент все же возвращается состояние (допустимое или ошибка).</span><span class="sxs-lookup"><span data-stu-id="0d477-145">For HTTP-based protocols, a status (valid or error) is still returned to the client.</span></span> <span data-ttu-id="0d477-146">Это связано с тем, что HTTP — единственный протокол с семантикой запросов и ответов, которая является частью стека протокола WCF.</span><span class="sxs-lookup"><span data-stu-id="0d477-146">This is because HTTP is the only protocol with a request-response semantics that is part of the WCF protocol stack.</span></span> <span data-ttu-id="0d477-147">Поскольку обработка TCP скрыта от WCF, клиенту не отправляется подтверждение.</span><span class="sxs-lookup"><span data-stu-id="0d477-147">Because TCP processing is hidden from WCF, no acknowledgement is sent to the client.</span></span>  
  
## <a name="synchronous-one-way-with-errors"></a><span data-ttu-id="0d477-148">Синхронная односторонняя связь с ошибками</span><span class="sxs-lookup"><span data-stu-id="0d477-148">Synchronous One-Way with Errors</span></span>  

 <span data-ttu-id="0d477-149">Если произошла ошибка при обработке сообщения (Q или далее), клиенту не возвращается уведомление.</span><span class="sxs-lookup"><span data-stu-id="0d477-149">If an error occurs while processing the message (Q or beyond), no notification is returned to the client.</span></span> <span data-ttu-id="0d477-150">Эта логика идентична сценарию «Синхронная односторонняя связь без ошибок».</span><span class="sxs-lookup"><span data-stu-id="0d477-150">This is identical to the "Synchronous One-Way without Errors" scenario.</span></span> <span data-ttu-id="0d477-151">Если требуется получить сообщение об ошибке, использовать сценарий с односторонней связью не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="0d477-151">You should not use a One-Way scenario if you want to receive an error message.</span></span>  
  
## <a name="duplex"></a><span data-ttu-id="0d477-152">Дуплекс</span><span class="sxs-lookup"><span data-stu-id="0d477-152">Duplex</span></span>  

 <span data-ttu-id="0d477-153">Отличие от предыдущих сценариев заключается в том, что клиент выполняет роль службы, создавая действия ReceiveBytes и ProcessMessage, подобно сценариям для асинхронной связи.</span><span class="sxs-lookup"><span data-stu-id="0d477-153">The difference with the previous scenarios is that the client acts as a service, in which it creates the ReceiveBytes and ProcessMessage activities, similar to the Asynchronous scenarios.</span></span>
