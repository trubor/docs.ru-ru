---
description: Дополнительные сведения см. в статье доступ к службам WCF с помощью клиентского приложения Магазина Windows.
title: Доступ к службам WCF из клиентского приложения Магазина Windows
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: 6586b07e72749b0c136072474c27c264568ed3f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705412"
---
# <a name="access-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="a1c61-103">Доступ к службам WCF с помощью клиентского приложения Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="a1c61-103">Access WCF Services with a Windows Store Client App</span></span>

<span data-ttu-id="a1c61-104">В Windows 8 появился новый тип приложения - приложения Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="a1c61-104">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="a1c61-105">Эти приложения предназначены для работы с сенсорным экраном.</span><span class="sxs-lookup"><span data-stu-id="a1c61-105">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="a1c61-106">.NET Framework 4.5 позволяет приложениям Магазина Windows вызывать службы WCF.</span><span class="sxs-lookup"><span data-stu-id="a1c61-106">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="a1c61-107">Поддержка WCF в приложениях Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="a1c61-107">WCF Support in Windows Store Applications</span></span>  

 <span data-ttu-id="a1c61-108">Подмножество функций WCF доступно из приложения Магазина Windows. Дополнительную информацию см. в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="a1c61-108">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a1c61-109">Используйте API-синдикации WinRT вместо методов, доступных через службу WCF.</span><span class="sxs-lookup"><span data-stu-id="a1c61-109">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="a1c61-110">Дополнительные сведения см. в разделе [API синдикации WinRT](xref:Windows.Web.Syndication)</span><span class="sxs-lookup"><span data-stu-id="a1c61-110">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a1c61-111">Использование Добавление ссылки на службу для добавления ссылки на веб-службу в компонент среда выполнения Windows не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="a1c61-111">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn't supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="a1c61-112">Поддерживаемые привязки</span><span class="sxs-lookup"><span data-stu-id="a1c61-112">Supported Bindings</span></span>  

 <span data-ttu-id="a1c61-113">Поддерживаются следующие привязки WCF в приложениях Магазина Windows:</span><span class="sxs-lookup"><span data-stu-id="a1c61-113">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="a1c61-114">Поддерживаются следующие элементы привязки в приложениях Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="a1c61-114">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="a1c61-115">Поддерживается текстовое и двоичное кодирование.</span><span class="sxs-lookup"><span data-stu-id="a1c61-115">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="a1c61-116">Поддерживаются все режимы передачи WCF.</span><span class="sxs-lookup"><span data-stu-id="a1c61-116">All WCF transfer modes are supported.</span></span> <span data-ttu-id="a1c61-117">Дополнительные сведения см. в разделе [Streaming Message Transfer](streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="a1c61-117">For more information see, [Streaming Message Transfer](streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="a1c61-118">Добавление ссылки на службу</span><span class="sxs-lookup"><span data-stu-id="a1c61-118">Add Service Reference</span></span>  

 <span data-ttu-id="a1c61-119">Для вызова службы WCF из приложения Магазина Windows пользуйтесь функцией «Добавить ссылку на службу» среды Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a1c61-119">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="a1c61-120">Можно заметить небольшие изменения в работе функции «Добавить ссылку на службу» при работе с приложением Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="a1c61-120">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="a1c61-121">Во-первых, не создается файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a1c61-121">First no configuration file is generated.</span></span> <span data-ttu-id="a1c61-122">Приложения Магазина Windows не используют файлы конфигурации, поэтому их необходимо настраивать в коде.</span><span class="sxs-lookup"><span data-stu-id="a1c61-122">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="a1c61-123">Код конфигурации можно найти в файле References.cs, который создается функцией «Добавить ссылку на службу».</span><span class="sxs-lookup"><span data-stu-id="a1c61-123">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="a1c61-124">Чтобы просмотреть этот файл, выберите "Показать все файлы" в обозревателе решений.</span><span class="sxs-lookup"><span data-stu-id="a1c61-124">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="a1c61-125">Файл будет расположен под пунктом «Ссылки на службу», а затем в узлах Reference.svcmap в рамках проекта.</span><span class="sxs-lookup"><span data-stu-id="a1c61-125">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="a1c61-126">Все операции, созданные для служб WCF внутри приложения Магазина Windows, будут асинхронными, использующими асинхронную технологию на основе событий.</span><span class="sxs-lookup"><span data-stu-id="a1c61-126">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="a1c61-127">Дополнительные сведения см. в разделе [Async Tasks — упрощение асинхронного программирования с помощью задач](/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span><span class="sxs-lookup"><span data-stu-id="a1c61-127">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="a1c61-128">Поскольку конфигурация создается в коде, любые изменения, внесенные в файл Reference.cs, будут перезаписываться при каждом обновлении ссылки на службу.</span><span class="sxs-lookup"><span data-stu-id="a1c61-128">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="a1c61-129">Чтобы исправить эту ситуацию, код конфигурации создается внутри разделяемого метода, который вы можно реализовать в клиентском прокси-классе.</span><span class="sxs-lookup"><span data-stu-id="a1c61-129">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="a1c61-130">Разделяемый метод определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a1c61-130">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="a1c61-131">Затем можно реализовать этот разделяемый метод и изменить привязку или конечную точку в клиентском прокси-классе следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a1c61-131">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="a1c61-132">Сериализация</span><span class="sxs-lookup"><span data-stu-id="a1c61-132">Serialization</span></span>  

 <span data-ttu-id="a1c61-133">Поддерживаются следующие сериализаторы WCF в приложениях Магазина Windows:</span><span class="sxs-lookup"><span data-stu-id="a1c61-133">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="a1c61-134">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="a1c61-134">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="a1c61-135">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="a1c61-135">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="a1c61-136">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="a1c61-136">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a1c61-137">XmlDictionaryWriter.Write (DateTime) теперь записывает объект DateTime в виде строки.</span><span class="sxs-lookup"><span data-stu-id="a1c61-137">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="a1c61-138">Безопасность</span><span class="sxs-lookup"><span data-stu-id="a1c61-138">Security</span></span>  

<span data-ttu-id="a1c61-139">В приложениях Магазина Windows поддерживаются следующие режимы безопасности:</span><span class="sxs-lookup"><span data-stu-id="a1c61-139">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="a1c61-140">В приложениях Магазина Windows поддерживаются следующие типы учетных данных клиента:</span><span class="sxs-lookup"><span data-stu-id="a1c61-140">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="a1c61-141">None</span><span class="sxs-lookup"><span data-stu-id="a1c61-141">None</span></span>  
  
2. <span data-ttu-id="a1c61-142">Основные</span><span class="sxs-lookup"><span data-stu-id="a1c61-142">Basic</span></span>  
  
3. <span data-ttu-id="a1c61-143">Digest (дайджест)</span><span class="sxs-lookup"><span data-stu-id="a1c61-143">Digest</span></span>  
  
4. <span data-ttu-id="a1c61-144">Согласование</span><span class="sxs-lookup"><span data-stu-id="a1c61-144">Negotiate</span></span>  
  
5. <span data-ttu-id="a1c61-145">NTLM</span><span class="sxs-lookup"><span data-stu-id="a1c61-145">NTLM</span></span>  
  
6. <span data-ttu-id="a1c61-146">Windows</span><span class="sxs-lookup"><span data-stu-id="a1c61-146">Windows</span></span>  
  
7. <span data-ttu-id="a1c61-147">Имя пользователя (безопасность сообщений)</span><span class="sxs-lookup"><span data-stu-id="a1c61-147">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="a1c61-148">Windows (безопасность транспорта)</span><span class="sxs-lookup"><span data-stu-id="a1c61-148">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="a1c61-149">Чтобы приложения Магазина Windows могли получать и передавать учетные данные Windows по умолчанию, необходимо включить эту возможность в файле Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="a1c61-149">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="a1c61-150">Откройте этот файл и перейдите на вкладку "возможности" и выберите "учетные данные Windows по умолчанию".</span><span class="sxs-lookup"><span data-stu-id="a1c61-150">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="a1c61-151">Это позволит приложению подключаться к ресурсам интрасети, для доступа к которым требуются учетные данные домена.</span><span class="sxs-lookup"><span data-stu-id="a1c61-151">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a1c61-152">Чтобы приложения Магазина Windows могли выполнять вызовы между компьютерами, необходимо включить другую возможность, называемую "Домашняя или Рабочая сеть".</span><span class="sxs-lookup"><span data-stu-id="a1c61-152">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="a1c61-153">Этот параметр также находится в файле Package. appmanifest на вкладке возможности. Установите флажок Домашняя или Рабочая сеть.</span><span class="sxs-lookup"><span data-stu-id="a1c61-153">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="a1c61-154">Это позволит вашему приложению получать входящий и исходящий доступ к сетям доверенных мест пользователя, например домашних и рабочих.</span><span class="sxs-lookup"><span data-stu-id="a1c61-154">This gives your application inbound and outbound access to the networks of the user's trusted places like home and work.</span></span> <span data-ttu-id="a1c61-155">Важные входящие порты всегда заблокированы.</span><span class="sxs-lookup"><span data-stu-id="a1c61-155">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="a1c61-156">Для доступа к службам в Интернете необходимо также включить возможность «Интернет (клиент)».</span><span class="sxs-lookup"><span data-stu-id="a1c61-156">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="a1c61-157">Разное</span><span class="sxs-lookup"><span data-stu-id="a1c61-157">Misc</span></span>  

 <span data-ttu-id="a1c61-158">Поддерживается использование следующих классов для приложений Магазина Windows:</span><span class="sxs-lookup"><span data-stu-id="a1c61-158">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="a1c61-159">Определение контрактов службы</span><span class="sxs-lookup"><span data-stu-id="a1c61-159">Defining Service Contracts</span></span>  

 <span data-ttu-id="a1c61-160">Рекомендуется определять только асинхронные операции службы с помощью асинхронной модели на основе событий.</span><span class="sxs-lookup"><span data-stu-id="a1c61-160">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="a1c61-161">Это гарантирует, что приложения Магазина Windows сохранят высокую скорость отклика при вызове операции службы.</span><span class="sxs-lookup"><span data-stu-id="a1c61-161">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a1c61-162">Хотя исключение не возникнет, если указать синхронную операцию, настоятельно рекомендуется определять только асинхронные операции.</span><span class="sxs-lookup"><span data-stu-id="a1c61-162">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="a1c61-163">Вызов служб WCF из приложений Магазина Windows</span><span class="sxs-lookup"><span data-stu-id="a1c61-163">Calling WCF Services from Windows Store Applications</span></span>  

 <span data-ttu-id="a1c61-164">Как уже говорилось, вся настройка должна быть сделана в коде метода GetBindingForEndpoint в сформированном прокси-классе.</span><span class="sxs-lookup"><span data-stu-id="a1c61-164">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="a1c61-165">Вызов операции службы выполняется точно так же, как и вызов любого асинхронного метода, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="a1c61-165">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="a1c61-166">Обратите внимание на использование ключевого слова async при асинхронном вызове, а также ключевого слова await при вызове асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="a1c61-166">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c61-167">См. также</span><span class="sxs-lookup"><span data-stu-id="a1c61-167">See also</span></span>

- [<span data-ttu-id="a1c61-168">Программирование безопасности WCF</span><span class="sxs-lookup"><span data-stu-id="a1c61-168">Programming WCF Security</span></span>](programming-wcf-security.md)
- [<span data-ttu-id="a1c61-169">Привязки</span><span class="sxs-lookup"><span data-stu-id="a1c61-169">Bindings</span></span>](../bindings.md)
