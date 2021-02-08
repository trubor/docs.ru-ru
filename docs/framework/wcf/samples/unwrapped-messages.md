---
description: 'Дополнительные сведения: распаковать сообщения'
title: Сообщения без оболочки
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 5eeb81e9035856f6c13eed3ce54b4fb98de07e5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798216"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="ceb7d-103">Сообщения без оболочки</span><span class="sxs-lookup"><span data-stu-id="ceb7d-103">Unwrapped Messages</span></span>

<span data-ttu-id="ceb7d-104">В этом образце показаны сообщения без оболочки.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-104">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="ceb7d-105">По умолчанию текст сообщения форматируется так, чтобы параметры, которые передаются операциям службы, находились в оболочке.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-105">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="ceb7d-106">В следующем образце показано заключенное в оболочку сообщение запроса `Add` для службы `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-106">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="ceb7d-107">Элемент `<Add>` в теле сообщения выступает в роли оболочки для параметров `n1` и `n2`.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-107">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="ceb7d-108">В следующем образце показано эквивалентное сообщение без оболочки.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-108">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
```  
  
 <span data-ttu-id="ceb7d-109">В этом сообщении параметры `n1` и `n2` не помещены в элемент-оболочку, а являются непосредственными дочерними элементами элемента soap body.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-109">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ceb7d-110">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ceb7d-111">В этом образце сообщение без оболочки создается путем применения атрибута <xref:System.ServiceModel.MessageContractAttribute> к типу параметра и типу возвращаемого значения операции службы, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-111">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="ceb7d-112">Для просмотра всех отправляемых и получаемых сообщений в этом образце используется трассировка.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-112">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="ceb7d-113">Кроме того, для привязки <xref:System.ServiceModel.WSHttpBinding> не были настроены параметры безопасности, чтобы сократить число заносимых в журнал сообщений.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-113">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="ceb7d-114">Результирующий журнал трассировки (К:\логс\мессаже.лог) можно просмотреть с помощью [средства Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ceb7d-114">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="ceb7d-115">Чтобы просмотреть содержимое сообщения, выберите **сообщения** в левой и правой панелях средства Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-115">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="ceb7d-116">Этот образец настроен таким образом, чтобы журналы трассировки сохранялись в папке C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-116">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="ceb7d-117">Создайте эту папку перед выполнением образца и предоставьте сетевой службе пользователя разрешение на запись в эту папку.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-117">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ceb7d-118">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="ceb7d-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ceb7d-119">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ceb7d-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ceb7d-120">Создайте каталог C:\LOGS для регистрации сообщений.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-120">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="ceb7d-121">Предоставьте сетевой службе пользователя разрешение на запись в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-121">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="ceb7d-122">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ceb7d-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ceb7d-123">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ceb7d-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ceb7d-124">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ceb7d-125">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="ceb7d-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ceb7d-126">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ceb7d-127">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="ceb7d-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
