---
description: Дополнительные сведения см. в статье асинхронные сценарии с использованием HTTP, TCP или Named-Pipe
title: Асинхронные сценарии с использованием HTTP, TCP или именованного канала
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 5e01866cd20d63796741a097a6d7d774ea45d3d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770954"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="b540c-103">Асинхронные сценарии с использованием HTTP, TCP или именованного канала</span><span class="sxs-lookup"><span data-stu-id="b540c-103">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>

<span data-ttu-id="b540c-104">В этом разделе описываются действия и перенаправления для различных асинхронных сценариев типа запрос-ответ (с многопотоковыми запросами с использованием HTTP, TCP или именованного канала).</span><span class="sxs-lookup"><span data-stu-id="b540c-104">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="b540c-105">Асинхронный запрос-ответ без ошибок</span><span class="sxs-lookup"><span data-stu-id="b540c-105">Asynchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="b540c-106">В этом разделе описываются действия и перенаправления для асинхронного сценария типа запрос-ответ (с многопотоковым клиентом).</span><span class="sxs-lookup"><span data-stu-id="b540c-106">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="b540c-107">Действие вызывающего завершается, когда возвращается значение `beginCall` и `endCall`.</span><span class="sxs-lookup"><span data-stu-id="b540c-107">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="b540c-108">При осуществлении обратного вызова возвращается обратный вызов.</span><span class="sxs-lookup"><span data-stu-id="b540c-108">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="b540c-109">Вызываемое действие завершится, когда возвращается значение `beginCall` и `endCall` или когда возвращается обратный вызов, если он был вызван из данного действия.</span><span class="sxs-lookup"><span data-stu-id="b540c-109">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="b540c-110">Асинхронный клиент без обратного вызова</span><span class="sxs-lookup"><span data-stu-id="b540c-110">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="b540c-111">Распространение включено для обеих сторон (с использованием HTTP)</span><span class="sxs-lookup"><span data-stu-id="b540c-111">Propagation is Enabled on Both Sides, using HTTP</span></span>  

 ![Асинхронный клиент без обратного вызова, где Пропагатеактивити имеет значение true на обеих сторонах.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 <span data-ttu-id="b540c-113">Если значение `propagateActivity=true` равно, ProcessMessage указывает, в какое действие ProcessAction нужно передавать.</span><span class="sxs-lookup"><span data-stu-id="b540c-113">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="b540c-114">Для сценариев, основанных на HTTP, для первого отправляемого сообщения вызывается действие ReceiveBytes, которое сохраняется на время существования запроса.</span><span class="sxs-lookup"><span data-stu-id="b540c-114">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="b540c-115">Распространение отключено для обеих сторон (с использованием HTTP)</span><span class="sxs-lookup"><span data-stu-id="b540c-115">Propagation is Disabled on Either Sides, using HTTP</span></span>  

 <span data-ttu-id="b540c-116">Если `propagateActivity=false` на обеих сторонах, ProcessMessage не указывает, какое действие ProcessAction нужно переместить.</span><span class="sxs-lookup"><span data-stu-id="b540c-116">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="b540c-117">Таким образом, вызывается новое временное действие ProcessAction с новым идентификатором.</span><span class="sxs-lookup"><span data-stu-id="b540c-117">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="b540c-118">Если асинхронный ответ соответствует запросу в коде ServiceModel, идентификатор действия может быть получен из локального контекста.</span><span class="sxs-lookup"><span data-stu-id="b540c-118">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="b540c-119">Фактическое действие ProcessAction может быть передано с данным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="b540c-119">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Асинхронный клиент без обратного вызова, где Пропагатеактивити имеет значение false на любой стороне.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 <span data-ttu-id="b540c-121">Для сценариев, основанных на HTTP, для первого отправляемого сообщения вызывается действие ReceiveBytes, которое сохраняется на время существования запроса.</span><span class="sxs-lookup"><span data-stu-id="b540c-121">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="b540c-122">Действие "Обработка действия" создается на асинхронном клиенте при `propagateActivity=false` вызове или вызываемом методе, а также когда ответное сообщение не содержит заголовок действия.</span><span class="sxs-lookup"><span data-stu-id="b540c-122">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="b540c-123">Распространение включено для обеих сторон (с использованием TCP или именованного канала)</span><span class="sxs-lookup"><span data-stu-id="b540c-123">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  

 ![Асинхронный клиент без обратного вызова, где Пропагатеактивити имеет значение true для обеих сторон и именованного канала/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="b540c-125">Для сценария, основанного на именованном канале или TCP, действие ReceiveBytes вызывается при открытии клиента и сохраняется на время существования подключения.</span><span class="sxs-lookup"><span data-stu-id="b540c-125">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="b540c-126">Аналогично первому изображению, если значение `propagateActivity=true` , ProcessMessage указывает, в какое действие ProcessAction нужно передавать.</span><span class="sxs-lookup"><span data-stu-id="b540c-126">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="b540c-127">Распространение отключено для обеих сторон (с использованием TCP или именованного канала)</span><span class="sxs-lookup"><span data-stu-id="b540c-127">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  

 <span data-ttu-id="b540c-128">Для сценария, основанного на именованном канале или TCP, действие ReceiveBytes вызывается при открытии клиента и сохраняется на время существования подключения.</span><span class="sxs-lookup"><span data-stu-id="b540c-128">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="b540c-129">Аналогично второму изображению, если `propagateActivity=false` с любой стороны, ProcessMessage не указывает, в какое действие ProcessAction нужно передавать.</span><span class="sxs-lookup"><span data-stu-id="b540c-129">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="b540c-130">Таким образом, вызывается новое временное действие ProcessAction с новым идентификатором.</span><span class="sxs-lookup"><span data-stu-id="b540c-130">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="b540c-131">Если асинхронный ответ соответствует запросу в коде ServiceModel, идентификатор действия может быть получен из локального контекста.</span><span class="sxs-lookup"><span data-stu-id="b540c-131">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="b540c-132">Фактическое действие ProcessAction может быть передано с данным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="b540c-132">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Асинхронный клиент без обратного вызова, где Пропагатеактивити имеет значение false на обеих сторонах и именованном канале TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="b540c-134">Асинхронный клиент с обратным вызовом</span><span class="sxs-lookup"><span data-stu-id="b540c-134">Asynchronous client with Callback</span></span>  

 <span data-ttu-id="b540c-135">В данном сценарии добавляются действия G и A’ для обратного вызова и `endCall`, а также их передачи в обратном вызове и вне его.</span><span class="sxs-lookup"><span data-stu-id="b540c-135">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="b540c-136">В этом разделе показано только использование HTTP с `propagateActivity` = `true` .</span><span class="sxs-lookup"><span data-stu-id="b540c-136">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="b540c-137">Однако дополнительные действия и передачи применяются также к другим вариантам (то есть по `propagateActivity` = `false` протоколу TCP или именованному каналу).</span><span class="sxs-lookup"><span data-stu-id="b540c-137">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="b540c-138">Обратный вызов создает новое действие (G), когда клиент вызывает пользовательский код для уведомления о готовности результатов.</span><span class="sxs-lookup"><span data-stu-id="b540c-138">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="b540c-139">Затем пользовательский код вызывает `endCall` в обратном вызове (как показано на рисунке 5) или вне обратного вызова (рисунок 6).</span><span class="sxs-lookup"><span data-stu-id="b540c-139">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="b540c-140">Так как неизвестно, какие действия пользователя `endCall` вызывают из, это действие помечено как `A’` .</span><span class="sxs-lookup"><span data-stu-id="b540c-140">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="b540c-141">Действие A’ может быть одинаковым или отличаться от действия A.</span><span class="sxs-lookup"><span data-stu-id="b540c-141">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![Показывает асинхронный клиент с обратным вызовом, ендкалл в ответном вызове.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Показывает асинхронный клиент с обратным вызовом ендкалл вне обратного вызова.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="b540c-144">Асинхронный сервер с обратным вызовом</span><span class="sxs-lookup"><span data-stu-id="b540c-144">Asynchronous Server with Callback</span></span>  

 ![Показывает асинхронный сервер с обратным вызовом.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 <span data-ttu-id="b540c-146">Стек каналов выполняет обратный вызов клиента при получении сообщения: трассировки для данной обработки выдаются в самом действии ProcessRequest.</span><span class="sxs-lookup"><span data-stu-id="b540c-146">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="b540c-147">Асинхронный запрос-ответ с ошибками</span><span class="sxs-lookup"><span data-stu-id="b540c-147">Asynchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="b540c-148">Во время `endCall` получаются сообщения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="b540c-148">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="b540c-149">В противном случае действия и передачи аналогичны предыдущим сценариям.</span><span class="sxs-lookup"><span data-stu-id="b540c-149">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="b540c-150">Асинхронная односторонняя связь с ошибками или без них</span><span class="sxs-lookup"><span data-stu-id="b540c-150">Asynchronous One-Way with or without Errors</span></span>  

 <span data-ttu-id="b540c-151">Ответ отсутствует или клиенту возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="b540c-151">No response or fault is returned to the client.</span></span>
