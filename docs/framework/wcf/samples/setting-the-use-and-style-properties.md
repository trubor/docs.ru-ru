---
description: 'Дополнительные сведения: Задание свойств использования и стиля'
title: Определение образцов свойств use и Style
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 435ea23e4a34ec91ea764ae9435487c1e1313afd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793003"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="658a1-103">Установка свойств Use и Style</span><span class="sxs-lookup"><span data-stu-id="658a1-103">Setting the Use and Style Properties</span></span>

<span data-ttu-id="658a1-104">В этом образце кода показано, как использовать свойства Use и Style классов <xref:System.ServiceModel.XmlSerializerFormatAttribute> и <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="658a1-104">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="658a1-105">Эти свойства влияют на форматирование сообщений.</span><span class="sxs-lookup"><span data-stu-id="658a1-105">These properties affect how messages are formatted.</span></span> <span data-ttu-id="658a1-106">По умолчанию тело сообщения форматируется с использованием стиля <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="658a1-106">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="658a1-107">Эти параметры можно задать либо на уровне контракта службы, либо на уровне контракта операции.</span><span class="sxs-lookup"><span data-stu-id="658a1-107">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="658a1-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="658a1-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="658a1-109">Свойство <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> определяет форматирование метаданных WSDL службы.</span><span class="sxs-lookup"><span data-stu-id="658a1-109">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="658a1-110">Допустимые значения: <xref:System.ServiceModel.OperationFormatStyle.Document> и <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="658a1-110">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="658a1-111">Стиль RPC означает, что WSDL-представление сообщений, которыми осуществляется обмен в ходе операции, содержит такие же параметры, как при удаленном вызове процедур.</span><span class="sxs-lookup"><span data-stu-id="658a1-111">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="658a1-112">Пример приведен ниже.</span><span class="sxs-lookup"><span data-stu-id="658a1-112">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="658a1-113">При задании для стиля значения <xref:System.ServiceModel.OperationFormatStyle.Document> WSDL-представление будет содержать единственный элемент, представляющий документ, которым осуществляется обмен в ходе операции, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="658a1-113">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="658a1-114">Свойство <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> определяет формат сообщения.</span><span class="sxs-lookup"><span data-stu-id="658a1-114">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="658a1-115">Возможные значения: <xref:System.ServiceModel.OperationFormatUse.Literal> и <xref:System.ServiceModel.OperationFormatUse.Encoded>. Значение по умолчанию: <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="658a1-115">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="658a1-116">Значение Literal означает, что сообщение представляет собой литеральный экземпляр схемы в WSDL, как показано в следующем примере стиля Document/Literal.</span><span class="sxs-lookup"><span data-stu-id="658a1-116">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="658a1-117">«Encoded» (закодировано) означает, что схемы в WSDL являются абстрактными спецификациями, которые кодируются в соответствии с правилами в разделе 5 спецификации SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="658a1-117">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="658a1-118">Далее приведен пример RPC/Encoded.</span><span class="sxs-lookup"><span data-stu-id="658a1-118">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="658a1-119">Профиль WS-I Basic Profile 1.0 запрещает использование стиля <xref:System.ServiceModel.OperationFormatUse.Encoded>, поэтому его следует использовать, только когда того требуют службы, созданные по устаревшим стандартам.</span><span class="sxs-lookup"><span data-stu-id="658a1-119">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="658a1-120">Формат сообщений `Encoded` доступен только при использовании сериализатора XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="658a1-120">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="658a1-121">Для просмотра отправляемых и получаемых сообщений Этот образец основан на [трассировке и регистрации сообщений](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="658a1-121">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="658a1-122">В конфигурацию службы и исходный код внесены изменения, позволяющие использовать трассировку и журнал сообщений.</span><span class="sxs-lookup"><span data-stu-id="658a1-122">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="658a1-123">Кроме того, привязка <xref:System.ServiceModel.WSHttpBinding> настроена без использования средств безопасности, что позволяет просматривать сообщения в журнале в формате без шифрования.</span><span class="sxs-lookup"><span data-stu-id="658a1-123">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="658a1-124">Результирующие журналы трассировки (System. ServiceModel. E2E и Message. log) должны быть просмотрены с помощью [средства Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="658a1-124">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="658a1-125">В конфигурации задана следующая папка для создания трассировок: C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="658a1-125">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="658a1-126">Создайте эту папку, прежде чем выполнять код из этого образца.</span><span class="sxs-lookup"><span data-stu-id="658a1-126">Create the folder before running the sample.</span></span> <span data-ttu-id="658a1-127">Чтобы просмотреть содержимое сообщения в средстве просмотра трассировки, выберите **сообщения** в левой и правой панелях инструмента.</span><span class="sxs-lookup"><span data-stu-id="658a1-127">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="658a1-128">В следующем примере кода приведен контракт службы, в котором свойству <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> задано значение <xref:System.ServiceModel.OperationFormatUse>, и вместо формата тела сообщения по умолчанию (<xref:System.ServiceModel.OperationFormatStyle>) задан формат <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="658a1-128">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="658a1-129">Чтобы проверить различия между параметрами <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> и <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A>, измените их для службы, заново создайте клиент, выполните пример и просмотрите файл c:\logs\message.logs с помощью средства Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="658a1-129">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="658a1-130">Также обратите внимание на влияние на метаданные путем просмотра `http://localhost/ServiceModelSamples/service.svc?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="658a1-130">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="658a1-131">Метаданные служб обычно подразделяются на несколько страниц.</span><span class="sxs-lookup"><span data-stu-id="658a1-131">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="658a1-132">Главная страница WSDL содержит привязки WSDL, но `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` позволяет просматривать определения сообщений.</span><span class="sxs-lookup"><span data-stu-id="658a1-132">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="658a1-133">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="658a1-133">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="658a1-134">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="658a1-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="658a1-135">Создайте каталог C:\LOGS для регистрации сообщений.</span><span class="sxs-lookup"><span data-stu-id="658a1-135">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="658a1-136">Предоставьте сетевой службе пользователя разрешение на запись в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="658a1-136">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="658a1-137">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="658a1-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="658a1-138">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="658a1-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="658a1-139">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="658a1-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="658a1-140">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="658a1-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="658a1-141">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="658a1-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="658a1-142">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="658a1-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
