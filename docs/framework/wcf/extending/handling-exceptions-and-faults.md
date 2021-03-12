---
description: 'Дополнительные сведения: обработка исключений и ошибок'
title: Обработка исключений и сбоев
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 16ae72d54177b664bc41be6e639d0a44867df569
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605065"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="77743-103">Обработка исключений и сбоев</span><span class="sxs-lookup"><span data-stu-id="77743-103">Handling Exceptions and Faults</span></span>

<span data-ttu-id="77743-104">Исключения используются, чтобы передать сведения об ошибках локально в службе или реализации клиента.</span><span class="sxs-lookup"><span data-stu-id="77743-104">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="77743-105">С другой стороны, сбои используются, чтобы передать ошибки за пределы службы, например, от сервера клиенту или наоборот.</span><span class="sxs-lookup"><span data-stu-id="77743-105">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="77743-106">Помимо сбоев каналы транспорта часто используют механизмы, связанные с транспортом, чтобы сообщить об ошибках на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="77743-106">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="77743-107">Например, транспорт HTTP использует коды состояния, такие как «404», чтобы сообщить о несуществующем конечном URL-адресе (отсутствует конечная точка, чтобы вернуть ошибку).</span><span class="sxs-lookup"><span data-stu-id="77743-107">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="77743-108">Этот документ состоит из трех разделов, в которых содержится руководство для разработчиков пользовательских каналов.</span><span class="sxs-lookup"><span data-stu-id="77743-108">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="77743-109">В первом разделе содержится руководство о том, когда и как определять и выдавать исключения.</span><span class="sxs-lookup"><span data-stu-id="77743-109">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="77743-110">Во втором разделе содержится руководство по созданию и использованию ошибок.</span><span class="sxs-lookup"><span data-stu-id="77743-110">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="77743-111">В третьем разделе разъясняется, как предоставить данные трассировки, которые помогут пользователю созданного канала устранить неполадки в выполняемых приложениях.</span><span class="sxs-lookup"><span data-stu-id="77743-111">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="77743-112">Исключения</span><span class="sxs-lookup"><span data-stu-id="77743-112">Exceptions</span></span>  

 <span data-ttu-id="77743-113">Важно учитывать два момента при создании исключения: во-первых, его тип должен позволять пользователям написать правильный программный код, который будет соответствующим образом реагировать на исключение.</span><span class="sxs-lookup"><span data-stu-id="77743-113">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="77743-114">Во-вторых, исключение должно содержать достаточно сведений для пользователя, чтобы понять, какой произошел сбой, его последствия и возможные способы устранения.</span><span class="sxs-lookup"><span data-stu-id="77743-114">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="77743-115">Следующие разделы содержат рекомендации по типам исключений и сообщениям для каналов Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="77743-115">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="77743-116">Общие инструкции об исключениях в .NET можно также найти в документе «Правила разработки исключений».</span><span class="sxs-lookup"><span data-stu-id="77743-116">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="77743-117">Типы исключения</span><span class="sxs-lookup"><span data-stu-id="77743-117">Exception Types</span></span>  

 <span data-ttu-id="77743-118">Все исключения, создаваемые каналами, должны быть типа <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> или типа, унаследованного от <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="77743-118">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="77743-119">(Могут также создаваться такие исключения, как <xref:System.ObjectDisposedException>, но только для того, чтобы указать на неправильное использование канала вызывающим кодом.</span><span class="sxs-lookup"><span data-stu-id="77743-119">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="77743-120">Если канал используется правильно, он должен вызвать только указанные исключения.) WCF предоставляет семь типов исключений, которые являются производными от <xref:System.ServiceModel.CommunicationException> и предназначены для использования каналами.</span><span class="sxs-lookup"><span data-stu-id="77743-120">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="77743-121">Существуют другие исключения, унаследованные от <xref:System.ServiceModel.CommunicationException>, которые созданы для использования с другими частями системы.</span><span class="sxs-lookup"><span data-stu-id="77743-121">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="77743-122">Эти типы исключений приведены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="77743-122">These exception types are:</span></span>  
  
|<span data-ttu-id="77743-123">Тип исключения</span><span class="sxs-lookup"><span data-stu-id="77743-123">Exception Type</span></span>|<span data-ttu-id="77743-124">Значение</span><span class="sxs-lookup"><span data-stu-id="77743-124">Meaning</span></span>|<span data-ttu-id="77743-125">Внутреннее содержимое исключения</span><span class="sxs-lookup"><span data-stu-id="77743-125">Inner Exception Content</span></span>|<span data-ttu-id="77743-126">Стратегия восстановления</span><span class="sxs-lookup"><span data-stu-id="77743-126">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="77743-127">Адрес конечной точки, указанный для прослушивания, уже используется.</span><span class="sxs-lookup"><span data-stu-id="77743-127">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="77743-128">Если имеется, предоставляет дополнительные сведения об ошибке транспорта, вызвавшей это исключение.</span><span class="sxs-lookup"><span data-stu-id="77743-128">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="77743-129">Например, если выбран диапазон 10.0.0.0/20 для виртуальной сети, для пространства клиентских адресов можно выбрать 10.1.0.0/24.</span><span class="sxs-lookup"><span data-stu-id="77743-129">For example.</span></span> <span data-ttu-id="77743-130"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException> или <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="77743-130"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="77743-131">Повторите попытку с другим адресом.</span><span class="sxs-lookup"><span data-stu-id="77743-131">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="77743-132">Доступ к адресу конечной точки, указанному для прослушивания, не разрешен процессом.</span><span class="sxs-lookup"><span data-stu-id="77743-132">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="77743-133">Если имеется, предоставляет дополнительные сведения об ошибке транспорта, вызвавшей это исключение.</span><span class="sxs-lookup"><span data-stu-id="77743-133">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="77743-134">Например, <xref:System.IO.PipeException> или <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="77743-134">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="77743-135">Повторите попытку с другими учетными данными.</span><span class="sxs-lookup"><span data-stu-id="77743-135">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="77743-136"><xref:System.ServiceModel.ICommunicationObject>Используемое состояние находится в состоянии Faulted (Дополнительные сведения см. в разделе [сведения об изменениях состояния](understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="77743-136">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="77743-137">Обратите внимание, когда объект с несколькими ожидающими вызовами переходит в состояние сбоя, только один вызов создает исключение, относящееся к сбою, а остальные вызовы создают исключение <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="77743-137">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="77743-138">Это исключение обычно создается потому, что приложение пропускает какое-либо исключение и пытается использовать объект с уже имеющимся сбоем, возможно находящимся не в том потоке, который перехватил исходное исключение.</span><span class="sxs-lookup"><span data-stu-id="77743-138">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="77743-139">Если имеется, предоставляет сведения о внутреннем исключении.</span><span class="sxs-lookup"><span data-stu-id="77743-139">If present provides details about the inner exception.</span></span>|<span data-ttu-id="77743-140">Создать новый объект.</span><span class="sxs-lookup"><span data-stu-id="77743-140">Create a new object.</span></span> <span data-ttu-id="77743-141">Обратите внимание, что в зависимости от причины сбоя <xref:System.ServiceModel.ICommunicationObject>, могут потребоваться другие действия для восстановления.</span><span class="sxs-lookup"><span data-stu-id="77743-141">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="77743-142"><xref:System.ServiceModel.ICommunicationObject>Использованный объект был прерван (Дополнительные сведения см. в статье [об изменениях состояния](understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="77743-142">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="77743-143">Аналогично <xref:System.ServiceModel.CommunicationObjectFaultedException> , это исключение указывает, что приложение вызывается <xref:System.ServiceModel.ICommunicationObject.Abort%2A> для объекта, возможно, из другого потока, и объект больше не может использоваться по этой причине.</span><span class="sxs-lookup"><span data-stu-id="77743-143">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, this exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="77743-144">Если имеется, предоставляет сведения о внутреннем исключении.</span><span class="sxs-lookup"><span data-stu-id="77743-144">If present provides details about the inner exception.</span></span>|<span data-ttu-id="77743-145">Создать новый объект.</span><span class="sxs-lookup"><span data-stu-id="77743-145">Create a new object.</span></span> <span data-ttu-id="77743-146">Обратите внимание, что в зависимости от причины прерывания <xref:System.ServiceModel.ICommunicationObject>, могут потребоваться другие действия для восстановления.</span><span class="sxs-lookup"><span data-stu-id="77743-146">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="77743-147">Удаленная целевая конечная точка не выполняет прослушивание.</span><span class="sxs-lookup"><span data-stu-id="77743-147">The target remote endpoint is not listening.</span></span> <span data-ttu-id="77743-148">Это может быть вызвано тем, что адреса конечной точки неверен или неразрешим, либо конечная точка недоступна.</span><span class="sxs-lookup"><span data-stu-id="77743-148">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="77743-149">Примерами являются ошибка DNS, недоступность диспетчера очередей и незапущенная служба.</span><span class="sxs-lookup"><span data-stu-id="77743-149">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="77743-150">Внутреннее исключение предоставляет сведения, как правило, из используемого транспорта.</span><span class="sxs-lookup"><span data-stu-id="77743-150">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="77743-151">Повторите попытку с другим адресом.</span><span class="sxs-lookup"><span data-stu-id="77743-151">Try a different address.</span></span> <span data-ttu-id="77743-152">Пользователь также может повторить попытку после небольшой паузы, если служба была недоступна.</span><span class="sxs-lookup"><span data-stu-id="77743-152">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="77743-153">Протоколы связи, описанные в политике конечной точки, не совпадают между конечными точками.</span><span class="sxs-lookup"><span data-stu-id="77743-153">The communication protocols, as described by the endpoint's policy, are mismatched between endpoints.</span></span> <span data-ttu-id="77743-154">Например, не совпадают типы содержимого кадрирования или превышен максимальный размер сообщения.</span><span class="sxs-lookup"><span data-stu-id="77743-154">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="77743-155">Если имеется, предоставляет дополнительную информацию о конкретной ошибке протокола.</span><span class="sxs-lookup"><span data-stu-id="77743-155">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="77743-156">Например, <xref:System.ServiceModel.QuotaExceededException> - внутреннее исключение, создаваемое когда причина ошибки превышает MaxReceivedMessageSize.</span><span class="sxs-lookup"><span data-stu-id="77743-156">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="77743-157">Восстановление: убедитесь в соответствии параметров протоколов отправителя и получателя.</span><span class="sxs-lookup"><span data-stu-id="77743-157">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="77743-158">Одним из способов сделать это является повторный импорт метаданных конечной точки службы (политика) и использование созданной привязки для повторного создания канала.</span><span class="sxs-lookup"><span data-stu-id="77743-158">One way to do this is to re-import the service endpoint's metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="77743-159">Удаленная конечная точка выполняет прослушивание, но не готова к обработке сообщений.</span><span class="sxs-lookup"><span data-stu-id="77743-159">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="77743-160">Если имеется, внутренне исключение предоставляет ошибку протокола SOAP или сведения об ошибке на транспортном уровне.</span><span class="sxs-lookup"><span data-stu-id="77743-160">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="77743-161">Восстановление: повторите операцию после небольшой паузы.</span><span class="sxs-lookup"><span data-stu-id="77743-161">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="77743-162">Не удалось завершить операцию в течение времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="77743-162">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="77743-163">Может содержать сведение о времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="77743-163">May provide details about the timeout.</span></span>|<span data-ttu-id="77743-164">Повторите операцию после небольшой паузы.</span><span class="sxs-lookup"><span data-stu-id="77743-164">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="77743-165">Определите новый тип исключения только в том случае, если данный тип соответствует конкретной стратегии восстановления, отличной от всех существующих типов исключений.</span><span class="sxs-lookup"><span data-stu-id="77743-165">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="77743-166">В случае определения нового типа исключения, он должен быть унаследован от <xref:System.ServiceModel.CommunicationException> или одного из его производных классов.</span><span class="sxs-lookup"><span data-stu-id="77743-166">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="77743-167">Сообщения об исключении</span><span class="sxs-lookup"><span data-stu-id="77743-167">Exception Messages</span></span>  

 <span data-ttu-id="77743-168">Сообщения об исключениях предназначены для пользователя, а не для программы, поэтому в них должно содержаться достаточно сведений, чтобы помочь пользователю понять и решить проблему.</span><span class="sxs-lookup"><span data-stu-id="77743-168">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="77743-169">Ниже приведены три неотъемлемые части хорошего сообщения об исключении.</span><span class="sxs-lookup"><span data-stu-id="77743-169">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="77743-170">Что произошло.</span><span class="sxs-lookup"><span data-stu-id="77743-170">What happened.</span></span> <span data-ttu-id="77743-171">Предоставьте четкое описание проблемы с помощью терминов, относящихся к интерфейсу пользователя.</span><span class="sxs-lookup"><span data-stu-id="77743-171">Provide a clear description of the problem using terms that relate to the user's experience.</span></span> <span data-ttu-id="77743-172">Например, "Недопустимый раздел конфигурации" является примером неправильного сообщения об исключении.</span><span class="sxs-lookup"><span data-stu-id="77743-172">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="77743-173">В этом случае у пользователя нет сведений о том, какой раздел и почему является неправильным.</span><span class="sxs-lookup"><span data-stu-id="77743-173">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="77743-174">Улучшенное сообщение будет иметь вид "Недопустимый раздел конфигурации \<customBinding> ".</span><span class="sxs-lookup"><span data-stu-id="77743-174">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="77743-175">Примером еще более точного сообщения может быть "Не удается добавить транспорт с именем myTransport в привязку myBinding, так как в привязке уже есть транспорт с именем myTransport".</span><span class="sxs-lookup"><span data-stu-id="77743-175">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="77743-176">Это очень конкретное сообщение с использованием терминов и имен, которые пользователь может легко найти в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="77743-176">This is a very specific message using terms and names that the user can easily identify in the application's configuration file.</span></span> <span data-ttu-id="77743-177">Однако в сообщении по-прежнему не хватает нескольких ключевых компонентов.</span><span class="sxs-lookup"><span data-stu-id="77743-177">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="77743-178">Значимость ошибки.</span><span class="sxs-lookup"><span data-stu-id="77743-178">The significance of the error.</span></span> <span data-ttu-id="77743-179">Если в сообщении четко не указано значение ошибки, у пользователя может возникнуть вопрос, является ли ошибка неустранимой, либо ее можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="77743-179">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="77743-180">Как правило, в сообщениях должно выводиться значение и значимость ошибки.</span><span class="sxs-lookup"><span data-stu-id="77743-180">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="77743-181">Предыдущий пример может быть улучшен следующим образом: «Не удалось открыть ServiceHost из-за ошибки конфигурации. Не удается добавить транспорт с имением myTransport в привязку myBinding, так как в привязке уже есть транспорт с именем myTransport».</span><span class="sxs-lookup"><span data-stu-id="77743-181">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="77743-182">Способы устранения проблемы пользователем.</span><span class="sxs-lookup"><span data-stu-id="77743-182">How the user should correct the problem.</span></span> <span data-ttu-id="77743-183">Самая важная часть сообщения - помочь пользователю устранить проблему.</span><span class="sxs-lookup"><span data-stu-id="77743-183">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="77743-184">В сообщении должны содержаться некоторые рекомендации или указания о том, что необходимо проверить или исправить, чтобы устранить проблему.</span><span class="sxs-lookup"><span data-stu-id="77743-184">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="77743-185">Например, «Не удалось открыть ServiceHost из-за ошибки конфигурации. Не удается добавить транспорт с имением myTransport в привязку myBinding, так как в привязке уже есть транспорт с именем myTransport.</span><span class="sxs-lookup"><span data-stu-id="77743-185">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="77743-186">Убедитесь в том, что в привязке есть только один транспорт».</span><span class="sxs-lookup"><span data-stu-id="77743-186">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="77743-187">Информирование об ошибках</span><span class="sxs-lookup"><span data-stu-id="77743-187">Communicating Faults</span></span>  

 <span data-ttu-id="77743-188">Протоколы SOAP 1.1 и SOAP 1.2 определяют конкретную структуру для ошибок.</span><span class="sxs-lookup"><span data-stu-id="77743-188">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="77743-189">Между двумя спецификациями существуют определенные отличия, но для создания и использования ошибок обычно применяются типы Message и MessageFault.</span><span class="sxs-lookup"><span data-stu-id="77743-189">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 ![Ошибки SOAP 1,2 и ошибка SOAP 1,1](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif)  
<span data-ttu-id="77743-191">Ошибка SOAP 1.2 (слева) и ошибка SOAP 1.1 (справа).</span><span class="sxs-lookup"><span data-stu-id="77743-191">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="77743-192">В SOAP 1,1 только элемент Fault является полным пространством имен.</span><span class="sxs-lookup"><span data-stu-id="77743-192">In SOAP 1.1, only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="77743-193">Протокол SOAP определяет сообщение об ошибке, как сообщение, содержащее элемент с ошибкой (элемент с именем `<env:Fault>`), в качестве дочернего элемента `<env:Body>`.</span><span class="sxs-lookup"><span data-stu-id="77743-193">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="77743-194">Содержимое элемента с ошибкой немного отличается в протоколах SOAP 1.1 и SOAP 1.2, как показано на рисунке 1.</span><span class="sxs-lookup"><span data-stu-id="77743-194">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="77743-195">Однако класс <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> нормализует эти различия в одной модели объекта:</span><span class="sxs-lookup"><span data-stu-id="77743-195">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```csharp
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 <span data-ttu-id="77743-196">Свойство `Code` соответствует свойству `env:Code` (или `faultCode` в SOAP 1.1) и определяет тип ошибки.</span><span class="sxs-lookup"><span data-stu-id="77743-196">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="77743-197">Протокол SOAP 1.2 определяет пять допустимых значений для `faultCode` (например, отправитель и получатель), а также определяет элемент `Subcode`, который может содержать значение дополнительного кода.</span><span class="sxs-lookup"><span data-stu-id="77743-197">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="77743-198">(Список допустимых кодов ошибок и их значения см. в [спецификации SOAP 1,2](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) .) Протокол SOAP 1,1 имеет немного другой механизм: он определяет четыре `faultCode` значения (например, клиент и сервер), которые можно расширить либо путем определения совершенно новых, либо с помощью точечной нотации для создания более конкретных `faultCodes` , например Client. Authentication.</span><span class="sxs-lookup"><span data-stu-id="77743-198">(See the [SOAP 1.2 specification](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="77743-199">При использовании типа MessageFault для программирования ошибок, значение FaultCode.Name и FaultCode.Namespace сопоставляется с именем и пространством имен `env:Code` в SOAP 1.2 или `faultCode` в SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="77743-199">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="77743-200">Значение FaultCode.SubCode сопоставляется со значением `env:Subcode` для протокола SOAP 1.2, а для SOAP 1.1 оно равно NULL.</span><span class="sxs-lookup"><span data-stu-id="77743-200">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="77743-201">Если требуется различать ошибку программными средствами, необходимо создать новые дополнительные коды ошибок (или новые коды ошибок при использовании протокола SOAP 1.1).</span><span class="sxs-lookup"><span data-stu-id="77743-201">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="77743-202">Это аналогично созданию нового типа исключения.</span><span class="sxs-lookup"><span data-stu-id="77743-202">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="77743-203">Не следует использовать запись через точку с кодами ошибок SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="77743-203">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="77743-204">( [Базовый профиль WS-I](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) также не рекомендует использовать нотацию с точкой кода ошибки.)</span><span class="sxs-lookup"><span data-stu-id="77743-204">(The [WS-I Basic Profile](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) also discourages the use of the fault code dot notation.)</span></span>  
  
```csharp
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 <span data-ttu-id="77743-205">`Reason`Свойство соответствует `env:Reason` (или `faultString` в SOAP 1,1) понятному описанию условия ошибки, аналогичного сообщению исключения.</span><span class="sxs-lookup"><span data-stu-id="77743-205">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception's message.</span></span> <span data-ttu-id="77743-206">Класс `FaultReason` (и `env:Reason/faultString`в протоколе SOAP) имеет встроенную поддержку нескольких переводов для обеспечения глобализации.</span><span class="sxs-lookup"><span data-stu-id="77743-206">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```csharp
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations
    {
       get;
    }  
  
 }  
```  
  
 <span data-ttu-id="77743-207">Содержимое сведений об ошибке предоставляется в MessageFault с помощью различных методов, включая `GetDetail` \<T> и `GetReaderAtDetailContents` ().</span><span class="sxs-lookup"><span data-stu-id="77743-207">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="77743-208">Сведения об ошибке — это непрозрачный элемент для передачи дополнительных данных об ошибке.</span><span class="sxs-lookup"><span data-stu-id="77743-208">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="77743-209">Это полезно, если существуют произвольные структурированные сведения, которые необходимо передать с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="77743-209">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="77743-210">Создание ошибок</span><span class="sxs-lookup"><span data-stu-id="77743-210">Generating Faults</span></span>  

 <span data-ttu-id="77743-211">В данном разделе объясняется процесс создания ошибки в ответ на условие ошибки, обнаруженное в канале или свойстве сообщения, созданном каналом.</span><span class="sxs-lookup"><span data-stu-id="77743-211">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="77743-212">Типичным примером является отправка обратно ошибки в ответ на сообщение запроса, содержащее недопустимые данные.</span><span class="sxs-lookup"><span data-stu-id="77743-212">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="77743-213">При создании ошибки пользовательский канал должен не отправлять ее напрямую, а вызвать исключение и позволить вышестоящему уровню решить, необходимо ли преобразовывать это исключение в ошибку и как ее отправлять.</span><span class="sxs-lookup"><span data-stu-id="77743-213">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="77743-214">Для облегчения данного преобразования канал должен предоставить реализацию `FaultConverter`, которая может преобразовать исключение, вызываемое пользовательским каналом, в соответствующую ошибку.</span><span class="sxs-lookup"><span data-stu-id="77743-214">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="77743-215">`FaultConverter` определяется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="77743-215">`FaultConverter` is defined as:</span></span>  
  
```csharp
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,
                                   out Message message);  
}  
```  
  
 <span data-ttu-id="77743-216">Каждый канал, создающий пользовательские ошибки, должен реализовать преобразователь `FaultConverter` и вернуть его из вызова в `GetProperty<FaultConverter>`.</span><span class="sxs-lookup"><span data-stu-id="77743-216">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="77743-217">Пользовательская `OnTryCreateFaultMessage` реализация должна либо преобразовать исключение в ошибку, либо передать его в объект с внутренним каналом `FaultConverter` .</span><span class="sxs-lookup"><span data-stu-id="77743-217">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel's `FaultConverter`.</span></span> <span data-ttu-id="77743-218">Если канал является транспортным, он должен либо преобразовать исключение или делегировать в кодировщик, `FaultConverter` либо значение по умолчанию, `FaultConverter` предоставленное в WCF.</span><span class="sxs-lookup"><span data-stu-id="77743-218">If the channel is a transport it must either convert the exception or delegate to the encoder's `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="77743-219">Преобразователь по умолчанию `FaultConverter` преобразует ошибки, соответствующие сообщениям об ошибках, которые указаны в WS-Addressing и SOAP.</span><span class="sxs-lookup"><span data-stu-id="77743-219">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="77743-220">Ниже приведен пример реализации `OnTryCreateFaultMessage`.</span><span class="sxs-lookup"><span data-stu-id="77743-220">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```csharp
public override bool OnTryCreateFaultMessage(Exception exception,
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,
                   out message);  
#else  
    FaultConverter inner =
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="77743-221">В этом шаблоне показано, что исключения, вызываемые между уровнями для требующих ошибок условий, должны содержать достаточно сведений для соответствующего генератора ошибок, чтобы создать правильную ошибку.</span><span class="sxs-lookup"><span data-stu-id="77743-221">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="77743-222">Разработчики пользовательских каналов могут определять типы исключений, соответствующие условиям ошибок, если такие исключения не существуют.</span><span class="sxs-lookup"><span data-stu-id="77743-222">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="77743-223">Обратите внимание, что исключения, затрагивающий разные уровни канала, должны передавать условие ошибки, а не непрозрачные данные ошибки.</span><span class="sxs-lookup"><span data-stu-id="77743-223">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="77743-224">Категории ошибок</span><span class="sxs-lookup"><span data-stu-id="77743-224">Fault Categories</span></span>  

 <span data-ttu-id="77743-225">Обычно существует три категории ошибок.</span><span class="sxs-lookup"><span data-stu-id="77743-225">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="77743-226">Ошибки, распространяющиеся на весь стек.</span><span class="sxs-lookup"><span data-stu-id="77743-226">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="77743-227">Эти ошибки встречаются на любом уровне в стеке каналов, например, InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="77743-227">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="77743-228">Ошибки, встречающиеся выше определенного уровня в стеке. Например, некоторые ошибки, относящиеся к поточной транзакции или ролям безопасности.</span><span class="sxs-lookup"><span data-stu-id="77743-228">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="77743-229">Ошибки, направленные на один уровень в стеке, например, ошибки номера последовательности WS-RM.</span><span class="sxs-lookup"><span data-stu-id="77743-229">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="77743-230">Категория 1.</span><span class="sxs-lookup"><span data-stu-id="77743-230">Category 1.</span></span> <span data-ttu-id="77743-231">Как правило, ошибки WS-Addressing и SOAP.</span><span class="sxs-lookup"><span data-stu-id="77743-231">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="77743-232">Базовый `FaultConverter` класс, предоставляемый WCF, преобразует ошибки, соответствующие сообщениям об ошибках, заданным в WS-Addressing и SOAP, поэтому нет необходимости самостоятельно выполнять преобразование этих исключений.</span><span class="sxs-lookup"><span data-stu-id="77743-232">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="77743-233">Категория 2.</span><span class="sxs-lookup"><span data-stu-id="77743-233">Category 2.</span></span> <span data-ttu-id="77743-234">Ошибки происходят, когда уровень добавляет в сообщение свойство, которое не полностью использует сведения о сообщении, относящиеся к данному уровню.</span><span class="sxs-lookup"><span data-stu-id="77743-234">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="77743-235">Ошибки могут быть обнаружены позже, когда расположенный выше уровень запрашивает свойство сообщения для дальнейшей обработки сведений о сообщении.</span><span class="sxs-lookup"><span data-stu-id="77743-235">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="77743-236">Такие каналы должны реализовать свойство `GetProperty`, заданное ранее, чтобы разрешить расположенному выше уровню отправлять обратно правильную ошибку.</span><span class="sxs-lookup"><span data-stu-id="77743-236">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="77743-237">Примером этого может служить свойство TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="77743-237">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="77743-238">Это свойство добавляется в сообщение без полной проверки всех данных в заголовке (для проверки может понадобиться обратиться к координатору распределенных транзакций (DTC).</span><span class="sxs-lookup"><span data-stu-id="77743-238">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="77743-239">Категория 3.</span><span class="sxs-lookup"><span data-stu-id="77743-239">Category 3.</span></span> <span data-ttu-id="77743-240">Ошибки создаются и отправляются только одним уровнем в процессоре.</span><span class="sxs-lookup"><span data-stu-id="77743-240">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="77743-241">Таким образом, все исключения содержатся на одном уровне.</span><span class="sxs-lookup"><span data-stu-id="77743-241">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="77743-242">Чтобы улучшить согласованность между каналами и упростить обслуживание, в пользовательском канале следует использовать приведенный ранее шаблон для создания сообщений об ошибках даже для внутренних ошибок.</span><span class="sxs-lookup"><span data-stu-id="77743-242">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="77743-243">Интерпретация полученных ошибок</span><span class="sxs-lookup"><span data-stu-id="77743-243">Interpreting Received Faults</span></span>  

 <span data-ttu-id="77743-244">В данном разделе содержится руководство по созданию соответствующего исключения при получении сообщения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="77743-244">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="77743-245">Ниже приведено дерево принятия решений для обработки сообщения на каждом из уровней стека.</span><span class="sxs-lookup"><span data-stu-id="77743-245">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="77743-246">Если слой считает, что сообщение является недопустимым, слой должен выполнить обработку "Недопустимое сообщение".</span><span class="sxs-lookup"><span data-stu-id="77743-246">If the layer considers the message to be invalid, the layer should do its 'invalid message' processing.</span></span> <span data-ttu-id="77743-247">Данная обработка зависит от уровня, но она может включать удаление сообщения, трассировку или вызов исключения, преобразуемого в ошибку.</span><span class="sxs-lookup"><span data-stu-id="77743-247">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="77743-248">Примерами являются случаи, когда безопасность получает сообщение с ненадлежащей защитой, или диспетчер ресурсов получает сообщение с неправильным порядковым номером.</span><span class="sxs-lookup"><span data-stu-id="77743-248">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="77743-249">В противном случае, если сообщение является сообщением об ошибке, которое относится к слою, а сообщение не имеет смысла за пределами взаимодействия слоя, этот слой должен обработать условие ошибки.</span><span class="sxs-lookup"><span data-stu-id="77743-249">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer's interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="77743-250">Примером этого является ошибка «отказ последовательности диспетчера ресурсов», являющаяся бессмысленной для уровней, расположенных выше канала диспетчера ресурсов. Это подразумевает сбой канала диспетчера ресурсов и вызов из незавершенных операций.</span><span class="sxs-lookup"><span data-stu-id="77743-250">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="77743-251">В противном случае сообщение должно быть возвращено из запроса() или получения().</span><span class="sxs-lookup"><span data-stu-id="77743-251">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="77743-252">Сюда также входят случаи, когда уровень распознает ошибку, но ошибка указывает на сбой запроса и не подразумевает сбой канала и вызов из незавершенных операций.</span><span class="sxs-lookup"><span data-stu-id="77743-252">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="77743-253">Чтобы упростить использование, уровень должен реализовать `GetProperty<FaultConverter>` и возвратить производный класс `FaultConverter`, который может преобразовать исключение, переопределив `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="77743-253">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="77743-254">Приведенные ниже объектные модели поддерживают преобразование сообщений в исключения.</span><span class="sxs-lookup"><span data-stu-id="77743-254">The following object model supports converting messages to exceptions:</span></span>  
  
```csharp
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,
                                 MessageFault fault,
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,
                                 MessageFault fault,
                                 out Exception exception);  
}  
```  
  
 <span data-ttu-id="77743-255">Уровень канала может реализовать `GetProperty<FaultConverter>`, чтобы поддержать преобразование сообщений об ошибках в исключения.</span><span class="sxs-lookup"><span data-stu-id="77743-255">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="77743-256">Для этого переопределите `OnTryCreateException` и проверьте сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="77743-256">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="77743-257">При подтверждении выполните преобразование, в противном случае запросите преобразование у внутреннего канала.</span><span class="sxs-lookup"><span data-stu-id="77743-257">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="77743-258">Каналы транспорта должны делегировать `FaultConverter.GetDefaultFaultConverter` получение FaultConverter для SOAP и WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="77743-258">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="77743-259">Типичная реализация выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="77743-259">A typical implementation looks like this:</span></span>  
  
```csharp
public override bool OnTryCreateException(  
                            Message message,
                            MessageFault fault,
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="77743-260">Для конкретных условий ошибки, имеющих определенные сценарии восстановления, можно задать производный класс `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="77743-260">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="77743-261">Обработка MustUnderstand</span><span class="sxs-lookup"><span data-stu-id="77743-261">MustUnderstand Processing</span></span>  

 <span data-ttu-id="77743-262">Протокол SOAP определяет общую ошибку для оповещения о том, что необходимый заголовок не был понят получателем.</span><span class="sxs-lookup"><span data-stu-id="77743-262">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="77743-263">Эта ошибка называется ошибкой `mustUnderstand`.</span><span class="sxs-lookup"><span data-stu-id="77743-263">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="77743-264">В WCF пользовательские каналы никогда не создают `mustUnderstand` ошибок.</span><span class="sxs-lookup"><span data-stu-id="77743-264">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="77743-265">Вместо этого диспетчер WCF, расположенный в верхней части стека связи WCF, проверяет, что в базовом стеке были распознаны все заголовки, помеченные как MustUnderstand = true.</span><span class="sxs-lookup"><span data-stu-id="77743-265">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUnderstand=true were understood by the underlying stack.</span></span> <span data-ttu-id="77743-266">Если какой-то из заголовков не был понят, в этой точке создается ошибка `mustUnderstand`.</span><span class="sxs-lookup"><span data-stu-id="77743-266">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="77743-267">(Пользователь может отключить обработку `mustUnderstand`, и приложение будет принимать все заголовки сообщений.</span><span class="sxs-lookup"><span data-stu-id="77743-267">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="77743-268">В этом случае приложение отвечает за выполнение `mustUnderstand` обработки.) Сформированная ошибка включает заголовок Нотундерстуд, содержащий имена всех заголовков с MustUnderstand = true, которые не были распознаны.</span><span class="sxs-lookup"><span data-stu-id="77743-268">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="77743-269">Если канал протокола отправляет пользовательский заголовок со значением MustUnderstand=true и получает ошибку `mustUnderstand`, он должен определить, вызвана ли эта ошибка отправленным заголовком.</span><span class="sxs-lookup"><span data-stu-id="77743-269">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="77743-270">Для этого можно использовать два члена в классе `MessageFault`:</span><span class="sxs-lookup"><span data-stu-id="77743-270">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="77743-271">`IsMustUnderstandFault` возвращает значение `true`, если это ошибка `mustUnderstand`.</span><span class="sxs-lookup"><span data-stu-id="77743-271">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="77743-272">`WasHeaderNotUnderstood` возвращает значение `true`, если заголовок с указанным именем и пространством имен включен в ошибку в качестве заголовка NotUnderstood.</span><span class="sxs-lookup"><span data-stu-id="77743-272">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="77743-273">В противном случае возвращается значение `false`.</span><span class="sxs-lookup"><span data-stu-id="77743-273">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="77743-274">Если канал выдает заголовок со значением MustUnderstand = true, уровень также должен реализовать шаблон API для создания исключения и преобразовать ошибки `mustUnderstand`, вызванные этим заголовком, в более полезное исключение, описанное ранее.</span><span class="sxs-lookup"><span data-stu-id="77743-274">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="77743-275">Трассировка</span><span class="sxs-lookup"><span data-stu-id="77743-275">Tracing</span></span>  

 <span data-ttu-id="77743-276">Платформа .NET Framework обеспечивает механизм для трассировки выполнения программы, который полезен для диагностики приложений в производственной среде или периодических проблем, когда нет возможности использовать отладчик для пошаговой проверки кода.</span><span class="sxs-lookup"><span data-stu-id="77743-276">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="77743-277">Основные компоненты этого механизма расположены в пространстве имен <xref:System.Diagnostics?displayProperty=nameWithType> и состоят из следующих элементов.</span><span class="sxs-lookup"><span data-stu-id="77743-277">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="77743-278"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, являющийся источником записываемых данных трассировки, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, являющийся абстрактным базовым классом для конкретных прослушивателей, которые получают подлежащие трассировке сведения из <xref:System.Diagnostics.TraceSource> и выводят их в назначение, зависящее от прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="77743-278"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="77743-279">Например, <xref:System.Diagnostics.XmlWriterTraceListener> выводит данные трассировки в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="77743-279">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="77743-280">Наконец, класс <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> позволяет пользователю управлять детализацией трассировке и обычно задается в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="77743-280">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="77743-281">Помимо основных компонентов можно использовать [средство Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) для просмотра трассировок WCF и поиска по ним.</span><span class="sxs-lookup"><span data-stu-id="77743-281">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="77743-282">Это средство предназначено специально для файлов трассировки, создаваемых WCF, и записывается с помощью <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="77743-282">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="77743-283">На следующем рисунке показаны различные компоненты, задействованные с трассировке.</span><span class="sxs-lookup"><span data-stu-id="77743-283">The following figure shows the various components involved in tracing.</span></span>  
  
 ![Компоненты трассировки](./media/wcfc-tracinginchannelsc.gif)  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="77743-285">Трассировка из пользовательского канала</span><span class="sxs-lookup"><span data-stu-id="77743-285">Tracing from a Custom Channel</span></span>  

 <span data-ttu-id="77743-286">Пользовательские каналы должны записывать сообщения трассировки, чтобы помочь с диагностикой проблем, когда невозможно применить отладчик на запущенном приложении.</span><span class="sxs-lookup"><span data-stu-id="77743-286">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="77743-287">Это предполагает две высокоуровневые задачи: создание экземпляра класса <xref:System.Diagnostics.TraceSource> и вызов его методов для записи трассировок.</span><span class="sxs-lookup"><span data-stu-id="77743-287">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="77743-288">При создании экземпляра класса <xref:System.Diagnostics.TraceSource> указываемая строка становится именем источника.</span><span class="sxs-lookup"><span data-stu-id="77743-288">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="77743-289">Данное имя используется для настройки (включения/отключения/установки уровня трассировки) источника трассировки.</span><span class="sxs-lookup"><span data-stu-id="77743-289">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="77743-290">Оно также отображается непосредственно в выводе трассировки.</span><span class="sxs-lookup"><span data-stu-id="77743-290">It also appears in the trace output itself.</span></span> <span data-ttu-id="77743-291">Пользовательские каналы должны использовать уникальное имя источника, чтобы при чтении вывода трассировки можно быть понять, откуда поступают данные трассировки.</span><span class="sxs-lookup"><span data-stu-id="77743-291">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="77743-292">Для имени источника трассировки принято использовать имя сборки, записывающей информацию.</span><span class="sxs-lookup"><span data-stu-id="77743-292">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="77743-293">Например, WCF использует System. ServiceModel в качестве источника трассировки для информации, записываемой из сборки System. ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="77743-293">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="77743-294">После создания источника трассировки вызываются его методы <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A> или <xref:System.Diagnostics.TraceSource.TraceInformation%2A>, чтобы внести записи трассировки в прослушиватели трассировки.</span><span class="sxs-lookup"><span data-stu-id="77743-294">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="77743-295">Для каждой внесенной записи трассировки необходимо классифицировать тип события как один из типов, определенный в <xref:System.Diagnostics.TraceEventType>.</span><span class="sxs-lookup"><span data-stu-id="77743-295">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="77743-296">Данная классификация и установка уровня трассировки определяют, выводится ли запись трассировки прослушивателю.</span><span class="sxs-lookup"><span data-stu-id="77743-296">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="77743-297">Например, установка в конфигурации уровней трассировки `Warning` позволяет записывать трассировки `Warning`, `Error` и `Critical`, но блокировать записи «Данные» и «Подробно».</span><span class="sxs-lookup"><span data-stu-id="77743-297">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="77743-298">Ниже приведен пример создания источника трассировки и внесения записи на уровне «Данные».</span><span class="sxs-lookup"><span data-stu-id="77743-298">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="77743-299">Настоятельно рекомендуется указать имя источника трассировки, являющееся уникальным для пользовательского канала, чтобы при считывании выходных данных трассировки было понятно, откуда они поступили.</span><span class="sxs-lookup"><span data-stu-id="77743-299">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="77743-300">Интеграция со средством просмотра трассировки</span><span class="sxs-lookup"><span data-stu-id="77743-300">Integrating with the Trace Viewer</span></span>  

 <span data-ttu-id="77743-301">Трассировки, формируемые каналом, можно выводить в формате, доступном для чтения [средством Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) , с помощью в <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> качестве прослушивателя трассировки.</span><span class="sxs-lookup"><span data-stu-id="77743-301">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="77743-302">Этим обычно не занимают разработчики каналов.</span><span class="sxs-lookup"><span data-stu-id="77743-302">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="77743-303">Вместо этого пользователь приложения (или пользователь, выполняющий устранение неполадок в приложении) должен настроить этот прослушиватель трассировки в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="77743-303">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application's configuration file.</span></span> <span data-ttu-id="77743-304">Например, следующая конфигурация выполняет вывод данных трассировки из пространства имен <xref:System.ServiceModel?displayProperty=nameWithType> и `Microsoft.Samples.Udp` в файл с именем `TraceEventsFile.e2e`:</span><span class="sxs-lookup"><span data-stu-id="77743-304">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="77743-305">Трассировка структурированных данных</span><span class="sxs-lookup"><span data-stu-id="77743-305">Tracing Structured Data</span></span>  

 <span data-ttu-id="77743-306">В классе <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> имеется метод <xref:System.Diagnostics.TraceSource.TraceData%2A>, который принимает один или несколько объектов для включения в запись трассировки.</span><span class="sxs-lookup"><span data-stu-id="77743-306"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="77743-307">Как правило, метод <xref:System.Object.ToString%2A?displayProperty=nameWithType> вызывается на каждом объекте, и результирующая строка записывается как часть записи.</span><span class="sxs-lookup"><span data-stu-id="77743-307">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="77743-308">При использовании <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> для вывода данных трассировки можно передавать класс <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> в виде объекта данных в <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="77743-308">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="77743-309">Результирующая запись трассировки содержит данные XML, предоставленные <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="77743-309">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="77743-310">Ниже приведен пример записи с данными приложения XML.</span><span class="sxs-lookup"><span data-stu-id="77743-310">Here is an example entry with XML application data:</span></span>  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 <span data-ttu-id="77743-311">Средство просмотра трассировки WCF понимает схему `TraceRecord` элемента, показанного ранее, и извлекает данные из своих дочерних элементов и отображает их в табличном формате.</span><span class="sxs-lookup"><span data-stu-id="77743-311">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="77743-312">Канал должен использовать эту схему при трассировке структурированных данных приложения, чтобы пользователи средства Svctraceviewer.exe могли считывать данные.</span><span class="sxs-lookup"><span data-stu-id="77743-312">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>
