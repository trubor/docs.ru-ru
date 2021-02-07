---
description: 'Дополнительные сведения: Пользовательский перехватчик сообщений'
title: Пользовательский перехватчик сообщений
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 916e608e9f5bee66c5d2b56304af0255ace5b827
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752474"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="bcd3f-103">Пользовательский перехватчик сообщений</span><span class="sxs-lookup"><span data-stu-id="bcd3f-103">Custom Message Interceptor</span></span>

<span data-ttu-id="bcd3f-104">Данный образец демонстрирует использование модели расширяемости канала.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-104">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="bcd3f-105">В частности, показано, как реализовать пользовательский элемент привязки, который создает фабрики и прослушиватели каналов для перехвата всех входящих и исходящих сообщений в определенной точке стека времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-105">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="bcd3f-106">В состав образца входят клиент и сервер, которые демонстрируют использование этих пользовательских фабрик.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-106">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="bcd3f-107">В этом образце служба и клиент являются консольными программами (EXE).</span><span class="sxs-lookup"><span data-stu-id="bcd3f-107">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="bcd3f-108">Как клиент, так и служба используют общую библиотеку (DLL), которая содержит пользовательский элемент привязки и ассоциированные с ним объекты времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-108">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcd3f-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bcd3f-110">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bcd3f-111">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="bcd3f-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bcd3f-112">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bcd3f-113">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="bcd3f-114">В этом примере описывается рекомендуемая процедура создания пользовательского многоуровневого канала в Windows Communication Foundation (WCF) с помощью платформы Channel и следующих рекомендаций по WCF.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-114">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="bcd3f-115">Чтобы создать пользовательский многоуровневый канал, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-115">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="bcd3f-116">Выберите формы канала, которые будут поддерживать фабрика и прослушиватель каналов.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-116">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="bcd3f-117">Создайте фабрику и прослушиватель каналов, которые поддерживают выбранную форму канала.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-117">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="bcd3f-118">Присоедините элемент привязки, добавляющий пользовательский многоуровневый канал в стек каналов.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-118">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="bcd3f-119">Добавьте раздел расширения элементов привязки, чтобы представить новый элемент привязки системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-119">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="bcd3f-120">Формы каналов</span><span class="sxs-lookup"><span data-stu-id="bcd3f-120">Channel Shapes</span></span>  

 <span data-ttu-id="bcd3f-121">При создании пользовательского многоуровневого канала в первую очередь необходимо решить, какие формы требуются для канала.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-121">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="bcd3f-122">Данным инспектором сообщений поддерживается любая форма, поддерживаемая уровнем ниже (например, если уровень ниже может выполнить построение метода <xref:System.ServiceModel.Channels.IOutputChannel> и интерфейса <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, то также предоставляется метод <xref:System.ServiceModel.Channels.IOutputChannel> и интерфейс <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="bcd3f-122">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="bcd3f-123">Фабрика и прослушиватель каналов</span><span class="sxs-lookup"><span data-stu-id="bcd3f-123">Channel Factory and Listener Factory</span></span>  

 <span data-ttu-id="bcd3f-124">Следующий шаг создания пользовательского многоуровневого канала - реализация интерфейса <xref:System.ServiceModel.Channels.IChannelFactory> для каналов клиентов и интерфейса <xref:System.ServiceModel.Channels.IChannelListener> для каналов служб.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-124">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="bcd3f-125">Эти классы получают внутреннюю фабрику и прослушиватель и делегируют все вызовы внутренней фабрике и прослушивателю, кроме `OnCreateChannel` и `OnAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-125">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="bcd3f-126">Добавление элемента привязки</span><span class="sxs-lookup"><span data-stu-id="bcd3f-126">Adding a Binding Element</span></span>  

 <span data-ttu-id="bcd3f-127">В образце определен пользовательский элемент привязки: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-127">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="bcd3f-128">`InterceptingBindingElement` принимает в `ChannelMessageInterceptor` качестве входных данных и использует его `ChannelMessageInterceptor` для обработки сообщений, которые проходят через него.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-128">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="bcd3f-129">Только этот класс должен быть открытым.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-129">This is the only class that must be public.</span></span> <span data-ttu-id="bcd3f-130">Фабрика, прослушиватель и каналы - все они могут являться внутренними реализациями открытых интерфейсов времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-130">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="bcd3f-131">Добавление поддержки конфигурации</span><span class="sxs-lookup"><span data-stu-id="bcd3f-131">Adding Configuration Support</span></span>  

 <span data-ttu-id="bcd3f-132">Для интеграции с конфигурацией привязки библиотека определяет обработчик раздела конфигурации в качестве раздела расширения элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-132">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="bcd3f-133">Файлы конфигурации клиента и сервера должны зарегистрировать расширение элемента привязки в системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-133">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="bcd3f-134">Реализации, требующие предоставить их элементы привязки в системе конфигурации, могут наследовать от этого класса.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-134">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="bcd3f-135">Добавление политики</span><span class="sxs-lookup"><span data-stu-id="bcd3f-135">Adding Policy</span></span>  

 <span data-ttu-id="bcd3f-136">Для интеграции с системой политики `InterceptingBindingElement` реализует расширение IPolicyExportExtension, чтобы сообщить об участии в создании политики.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-136">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="bcd3f-137">Чтобы поддержать импорт политики на созданном клиенте, пользователь может зарегистрировать производный класс `InterceptingBindingElementImporter` и переопределить `CreateMessageInterceptor`(), чтобы создать принадлежащий им класс `ChannelMessageInterceptor` с разрешенной политикой.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-137">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="bcd3f-138">Пример: инспектор сообщений, допускающий удаление.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-138">Example: Droppable Message Inspector</span></span>  

 <span data-ttu-id="bcd3f-139">Включенный в пример образец реализации `ChannelMessageInspector` удаляет сообщения.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-139">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="bcd3f-140">Его можно открыть из конфигурации следующим образом:</span><span class="sxs-lookup"><span data-stu-id="bcd3f-140">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="bcd3f-141">Клиент и сервер используют заново созданный раздел конфигурации, чтобы добавить пользовательские фабрики в самый нижний уровень принадлежащих им стеков канала времени выполнения (расположенные над транспортным уровнем).</span><span class="sxs-lookup"><span data-stu-id="bcd3f-141">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="bcd3f-142">Клиент использует библиотеку `MessageInterceptor`, чтобы добавить пользовательский заголовок даже в нумерованные сообщения.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-142">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="bcd3f-143">С другой стороны, служба использует библиотеку `MessageInterceptor`, чтобы удалять любые сообщения, которые не содержат этот специальный заголовок.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-143">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="bcd3f-144">Клиент должен предоставить результат своей работы после запуска службы и последующего запуска клиента.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-144">You should see the following client output after running the service and then the client.</span></span>  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="bcd3f-145">Клиент отправляет отчет службе о 10 различных значениях скорости ветра, но только половина этих значений помечена специальным заголовком.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-145">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="bcd3f-146">Служба должна предоставить следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="bcd3f-146">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bcd3f-147">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="bcd3f-147">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bcd3f-148">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-148">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="bcd3f-149">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bcd3f-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="bcd3f-150">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bcd3f-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="bcd3f-151">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bcd3f-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="bcd3f-152">Первым запустите файл Service.exe, затем Client.exe и наблюдайте результат в обоих окнах консоли.</span><span class="sxs-lookup"><span data-stu-id="bcd3f-152">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
