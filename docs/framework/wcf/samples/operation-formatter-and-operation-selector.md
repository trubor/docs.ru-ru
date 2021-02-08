---
description: 'Дополнительные сведения: модуль форматирования операций и селектор операций'
title: Модуль форматирования и селектор операции
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: dedfa92ddd2f8192eef6b11d8ecde133b961d6cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793224"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="acf84-103">Модуль форматирования и селектор операции</span><span class="sxs-lookup"><span data-stu-id="acf84-103">Operation Formatter and Operation Selector</span></span>

<span data-ttu-id="acf84-104">В этом образце показано, как можно использовать точки расширяемости Windows Communication Foundation (WCF) для предоставления данных сообщений в формате, отличном от того, который требуется WCF.</span><span class="sxs-lookup"><span data-stu-id="acf84-104">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="acf84-105">По умолчанию модули форматирования WCF предполагают включение параметров метода в `soap:body` элемент.</span><span class="sxs-lookup"><span data-stu-id="acf84-105">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="acf84-106">В этом образце показано, как реализовать пользовательский модуль форматирования операций, который анализирует параметры из строки HTTP-запроса GET и вызывает методы с использованием этих данных.</span><span class="sxs-lookup"><span data-stu-id="acf84-106">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="acf84-107">Образец основан на [Начало работы](getting-started-sample.md), который реализует `ICalculator` контракт службы.</span><span class="sxs-lookup"><span data-stu-id="acf84-107">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="acf84-108">Он показывает, каким образом можно изменить сообщения Add, Subtract, Multiply и Divide, чтобы они использовали HTTP-запросы GET в качестве запросов клиента серверу и HTTP-запросы POST с сообщениями POX в качестве ответов сервера клиенту.</span><span class="sxs-lookup"><span data-stu-id="acf84-108">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="acf84-109">Для этого в образце имеются следующие элементы.</span><span class="sxs-lookup"><span data-stu-id="acf84-109">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="acf84-110">Класс `QueryStringFormatter`, который реализует интерфейсы <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> и <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> для клиента и сервера соответственно и обрабатывает данные в строке запроса.</span><span class="sxs-lookup"><span data-stu-id="acf84-110">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="acf84-111">Класс `UriOperationSelector`, который реализует интерфейс <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> на сервере для выполнения диспетчеризации операций в зависимости от имени операции в запросе GET.</span><span class="sxs-lookup"><span data-stu-id="acf84-111">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="acf84-112">Поведение конечной точки `EnableHttpGetRequestsBehavior` (и соответствующая конфигурация), которое добавляет в среду выполнения селектор нужной операции.</span><span class="sxs-lookup"><span data-stu-id="acf84-112">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="acf84-113">Показано, как включить в среду выполнения новый модуль форматирования операций.</span><span class="sxs-lookup"><span data-stu-id="acf84-113">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="acf84-114">В этом образце служба и клиент являются консольными приложениями (EXE).</span><span class="sxs-lookup"><span data-stu-id="acf84-114">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acf84-115">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="acf84-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="acf84-116">Основные понятия</span><span class="sxs-lookup"><span data-stu-id="acf84-116">Key Concepts</span></span>  

 <span data-ttu-id="acf84-117">`QueryStringFormatter` — Модуль форматирования операций — это компонент в WCF, который отвечает за преобразование сообщения в массив объектов параметров и массив объектов параметров в сообщение.</span><span class="sxs-lookup"><span data-stu-id="acf84-117">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="acf84-118">Эта задача выполняется на клиенте с помощью интерфейса <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> и на сервере с помощью интерфейса <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>.</span><span class="sxs-lookup"><span data-stu-id="acf84-118">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="acf84-119">Эти интерфейсы позволяют пользователям получать сообщения запросов и ответов из методов `Serialize` и `Deserialize`.</span><span class="sxs-lookup"><span data-stu-id="acf84-119">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="acf84-120">В этом образце класс `QueryStringFormatter` реализует оба эти интерфейса и реализуется на стороне клиента и сервера.</span><span class="sxs-lookup"><span data-stu-id="acf84-120">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="acf84-121">Запрос:</span><span class="sxs-lookup"><span data-stu-id="acf84-121">Request:</span></span>  
  
- <span data-ttu-id="acf84-122">В этом образце класс <xref:System.ComponentModel.TypeConverter> используется для преобразования параметров в сообщении запроса в строки и обратно.</span><span class="sxs-lookup"><span data-stu-id="acf84-122">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="acf84-123">Если объект для определенного типа <xref:System.ComponentModel.TypeConverter> недоступен, модуль форматирования в этом образце создает исключение.</span><span class="sxs-lookup"><span data-stu-id="acf84-123">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="acf84-124">В методе `IClientMessageFormatter.SerializeRequest` на стороне клиента модуль форматирования создает код URI для соответствующего адреса назначения и добавляет имя операции в качестве суффикса.</span><span class="sxs-lookup"><span data-stu-id="acf84-124">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="acf84-125">Это имя используется для перенаправления на соответствующую операцию на сервере.</span><span class="sxs-lookup"><span data-stu-id="acf84-125">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="acf84-126">После этого массив объектов параметров сериализуется в строку запроса кода URI с использованием имен и значений параметров, преобразованных классом <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="acf84-126">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="acf84-127">Свойства <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> и <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> задаются данному URI.</span><span class="sxs-lookup"><span data-stu-id="acf84-127">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="acf84-128">Значение <xref:System.ServiceModel.Channels.MessageProperties> доступно через свойство <xref:System.ServiceModel.Channels.Message.Properties%2A>.</span><span class="sxs-lookup"><span data-stu-id="acf84-128"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="acf84-129">В методе `IDispatchMessageFormatter.DeserializeRequest` на сервере модуль форматирования извлекает код URI `Via` в свойствах сообщения входящего запроса.</span><span class="sxs-lookup"><span data-stu-id="acf84-129">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="acf84-130">Модуль форматирования преобразует пары "имя-значение" в строке запроса URI в имена и значения параметров и подставляет эти имена и значения параметров в массив передаваемых методу параметров.</span><span class="sxs-lookup"><span data-stu-id="acf84-130">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="acf84-131">Обратите внимание, что диспетчеризация по операциям уже произошла, поэтому в данном методе суффикс имени операции игнорируется.</span><span class="sxs-lookup"><span data-stu-id="acf84-131">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="acf84-132">Ответ:</span><span class="sxs-lookup"><span data-stu-id="acf84-132">Response:</span></span>  
  
- <span data-ttu-id="acf84-133">В этом образце HTTP-метод GET используется только для запросов.</span><span class="sxs-lookup"><span data-stu-id="acf84-133">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="acf84-134">Модуль форматирования делегирует отправку ответа исходному модулю форматирования, который бы использовался для создания XML-сообщения.</span><span class="sxs-lookup"><span data-stu-id="acf84-134">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="acf84-135">Одна из целей этого образца заключается в том, чтобы показать, как можно реализовать такой делегирующий модуль форматирования.</span><span class="sxs-lookup"><span data-stu-id="acf84-135">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="acf84-136">Класс UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="acf84-136">UriPathSuffixOperationSelector Class</span></span>  

 <span data-ttu-id="acf84-137">Интерфейс <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> позволяет пользователям реализовывать собственную логику определения операции, которой должно перенаправляться то или иное сообщение.</span><span class="sxs-lookup"><span data-stu-id="acf84-137">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="acf84-138">В этом образце необходимо реализовать на сервере класс `UriPathSuffixOperationSelector`, чтобы выбирать нужную операцию, поскольку имя операции включается в код URI HTTP-запроса GET, а не в заголовок действия в сообщении.</span><span class="sxs-lookup"><span data-stu-id="acf84-138">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="acf84-139">В этом образце разрешены только имена операций, указываемые с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="acf84-139">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="acf84-140">Метод `SelectOperation` принимает входящее сообщение и ищет в свойствах сообщения код URI `Via`.</span><span class="sxs-lookup"><span data-stu-id="acf84-140">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="acf84-141">Он извлекает из кода URI суффикс имени операции, ищет во внутренней таблице имя операции, которой следует перенаправить сообщение, и возвращает имя операции.</span><span class="sxs-lookup"><span data-stu-id="acf84-141">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="acf84-142">Класс EnableHttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="acf84-142">EnableHttpGetRequestsBehavior Class</span></span>  

 <span data-ttu-id="acf84-143">Компонент `UriPathSuffixOperationSelector` можно настраивать программным образом или с помощью поведения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="acf84-143">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="acf84-144">В этом образце реализовано поведение `EnableHttpGetRequestsBehavior`, которое задано в файле конфигурации приложения службы.</span><span class="sxs-lookup"><span data-stu-id="acf84-144">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="acf84-145">На сервере:</span><span class="sxs-lookup"><span data-stu-id="acf84-145">On the server:</span></span>  
  
 <span data-ttu-id="acf84-146">Свойству <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> присвоена реализация <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>.</span><span class="sxs-lookup"><span data-stu-id="acf84-146">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="acf84-147">По умолчанию WCF использует фильтр адресов точного соответствия.</span><span class="sxs-lookup"><span data-stu-id="acf84-147">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="acf84-148">Код URI входящего сообщения содержит суффикс имени операции, за которым следует строка запроса, содержащая данные параметров, поэтому поведение также изменяет фильтр адресов, чтобы он срабатывал по совпадению префикса.</span><span class="sxs-lookup"><span data-stu-id="acf84-148">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="acf84-149">Для этой цели в ней используется WCF <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> .</span><span class="sxs-lookup"><span data-stu-id="acf84-149">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="acf84-150">Установка модулей форматирования операций</span><span class="sxs-lookup"><span data-stu-id="acf84-150">Installing operation formatters</span></span>  

 <span data-ttu-id="acf84-151">Поведения операций, которые задают модули форматирования, являются уникальными.</span><span class="sxs-lookup"><span data-stu-id="acf84-151">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="acf84-152">Одно такое поведение всегда реализуется по умолчанию для каждой операции, чтобы создать нужный модуль форматирования операции.</span><span class="sxs-lookup"><span data-stu-id="acf84-152">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="acf84-153">Однако такие поведения очень похожи на поведения других операций; их невозможно идентифицировать по каким-либо другим атрибутам.</span><span class="sxs-lookup"><span data-stu-id="acf84-153">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="acf84-154">Чтобы установить поведение при замене, реализация должна найти определенные поведения модуля форматирования, которые устанавливаются загрузчиком типов WCF по умолчанию, и либо заменить его, либо добавить совместимое поведение для запуска после поведения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="acf84-154">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="acf84-155">Эти поведения модулей форматирования операций можно задать программным образом перед вызовом <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> или путем задания поведения операции, которое выполняется после поведения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="acf84-155">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="acf84-156">Однако его невозможно легко настроить с помощью поведения конечной точки (а следовательно с помощью конфигурации), поскольку модель поведений не допускает замены поведения другими поведениями или иного изменения дерева описаний.</span><span class="sxs-lookup"><span data-stu-id="acf84-156">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="acf84-157">На клиенте:</span><span class="sxs-lookup"><span data-stu-id="acf84-157">On the client:</span></span>  
  
 <span data-ttu-id="acf84-158">Реализацию <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> нужно осуществлять таким образом, чтобы этот модуль форматирования мог преобразовывать запросы в HTTP-запросы GET и делегировать создание ответов исходному модулю форматирования.</span><span class="sxs-lookup"><span data-stu-id="acf84-158">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="acf84-159">Для этого вызывается вспомогательный метод `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior`.</span><span class="sxs-lookup"><span data-stu-id="acf84-159">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="acf84-160">Это необходимо сделать до вызова метода `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="acf84-160">This must be done before calling `CreateChannel`.</span></span>  
  
```csharp  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 <span data-ttu-id="acf84-161">На сервере:</span><span class="sxs-lookup"><span data-stu-id="acf84-161">On the server:</span></span>  
  
- <span data-ttu-id="acf84-162">Интерфейс <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> нужно реализовать таким образом, чтобы этот модуль форматирования мог считывать HTTP-запросы GET и делегировать создание ответов исходному модулю форматирования.</span><span class="sxs-lookup"><span data-stu-id="acf84-162">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="acf84-163">Это делается путем вызова того же вспомогательного метода `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior`, что и для клиента (см. предыдущий пример кода).</span><span class="sxs-lookup"><span data-stu-id="acf84-163">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="acf84-164">Это необходимо сделать до вызова метода <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="acf84-164">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="acf84-165">В этом образце показано, каким образом можно вручную изменить модуль форматирования перед вызовом метода <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="acf84-165">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="acf84-166">Того же результата можно достичь, создав для класса <xref:System.ServiceModel.ServiceHost> производный класс, который вызывает `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` перед открытием (примеры см. в документации по размещению).</span><span class="sxs-lookup"><span data-stu-id="acf84-166">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="acf84-167">Возможности для пользователя</span><span class="sxs-lookup"><span data-stu-id="acf84-167">User experience</span></span>  

 <span data-ttu-id="acf84-168">На сервере:</span><span class="sxs-lookup"><span data-stu-id="acf84-168">On the server:</span></span>  
  
- <span data-ttu-id="acf84-169">Серверную реализацию `ICalculator` изменять не требуется.</span><span class="sxs-lookup"><span data-stu-id="acf84-169">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="acf84-170">В файле App.config службы следует задавать пользовательскую привязку POX, которая устанавливает для атрибута `messageVersion` элемента `textMessageEncoding` значение `None`.</span><span class="sxs-lookup"><span data-stu-id="acf84-170">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- <span data-ttu-id="acf84-171">Кроме того, в файле App.config службы необходимо задать пользовательское поведение `EnableHttpGetRequestsBehavior`, добавив его в раздел расширений поведения.</span><span class="sxs-lookup"><span data-stu-id="acf84-171">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
- <span data-ttu-id="acf84-172">Перед вызовом метода <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> необходимо добавить модули форматирования операций.</span><span class="sxs-lookup"><span data-stu-id="acf84-172">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="acf84-173">На клиенте:</span><span class="sxs-lookup"><span data-stu-id="acf84-173">On the client:</span></span>  
  
- <span data-ttu-id="acf84-174">Изменять клиентскую реализацию не требуется.</span><span class="sxs-lookup"><span data-stu-id="acf84-174">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="acf84-175">В файле App.config клиента следует задать пользовательскую привязку POX, которая устанавливает для атрибута `messageVersion` элемента `textMessageEncoding` значение `None`.</span><span class="sxs-lookup"><span data-stu-id="acf84-175">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="acf84-176">Отличие от службы заключается в том, что клиент должен включить ручную адресацию, чтобы можно было изменять исходящий адрес назначения.</span><span class="sxs-lookup"><span data-stu-id="acf84-176">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- <span data-ttu-id="acf84-177">В файле App.config клиента должно быть задано то же пользовательское поведение `EnableHttpGetRequestsBehavior`, что и на сервере.</span><span class="sxs-lookup"><span data-stu-id="acf84-177">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="acf84-178">Перед вызовом метода <xref:System.ServiceModel.ChannelFactory%601.CreateChannel> необходимо добавить модули форматирования операций.</span><span class="sxs-lookup"><span data-stu-id="acf84-178">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="acf84-179">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="acf84-179">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="acf84-180">Все четыре операции (Add, Subtract, Multiply и Divide) должны выполняться успешно.</span><span class="sxs-lookup"><span data-stu-id="acf84-180">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="acf84-181">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="acf84-181">The samples may already be installed on your machine.</span></span> <span data-ttu-id="acf84-182">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="acf84-182">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="acf84-183">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="acf84-183">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="acf84-184">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="acf84-184">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="acf84-185">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="acf84-185">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="acf84-186">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="acf84-186">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="acf84-187">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="acf84-187">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="acf84-188">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="acf84-188">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
