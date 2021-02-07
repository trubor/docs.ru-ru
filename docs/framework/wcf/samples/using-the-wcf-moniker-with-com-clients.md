---
description: Дополнительные сведения см. в статье Использование моникера WCF с COM-клиентами.
title: Использование моникера WCF с клиентами COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: c2888224e36a473773ef6d7fbd72dbae7420fab0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755763"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="a5d85-103">Использование моникера WCF с клиентами COM</span><span class="sxs-lookup"><span data-stu-id="a5d85-103">Using the WCF Moniker with COM Clients</span></span>

<span data-ttu-id="a5d85-104">В этом примере демонстрируется использование моникера службы Windows Communication Foundation (WCF) для интеграции веб-служб в среды разработки на основе COM, такие как Microsoft Office Visual Basic для приложений (Office VBA) или Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="a5d85-104">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="a5d85-105">Этот образец содержит клиент сервера скриптов Windows (VBS), поддерживающую библиотеку клиента (DLL) и библиотеку службы (DLL), размещенные службами IIS.</span><span class="sxs-lookup"><span data-stu-id="a5d85-105">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="a5d85-106">Служба представляет собой службу калькулятора, а клиент COM вызывает для службы математические операции (сложение, вычитание, умножение и деление).</span><span class="sxs-lookup"><span data-stu-id="a5d85-106">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="a5d85-107">Действия клиента отображаются в окнах сообщений.</span><span class="sxs-lookup"><span data-stu-id="a5d85-107">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5d85-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="a5d85-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a5d85-109">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="a5d85-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a5d85-110">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="a5d85-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a5d85-111">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="a5d85-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5d85-112">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="a5d85-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="a5d85-113">Служба реализует определенный контракт `ICalculator`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="a5d85-113">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
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
  
 <span data-ttu-id="a5d85-114">В образце показаны три альтернативных подхода к использованию моникера.</span><span class="sxs-lookup"><span data-stu-id="a5d85-114">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="a5d85-115">Типизированный контракт: контракт регистрируется как видимый для модели COM тип на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="a5d85-115">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="a5d85-116">Контракт WSDL: контракт предоставляется в виде документа WSDL.</span><span class="sxs-lookup"><span data-stu-id="a5d85-116">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="a5d85-117">Контракт обмена метаданными: контракт извлекается в среде выполнения из конечной точки обмена метаданными (MEX).</span><span class="sxs-lookup"><span data-stu-id="a5d85-117">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="a5d85-118">Типизированный контракт</span><span class="sxs-lookup"><span data-stu-id="a5d85-118">Typed Contract</span></span>  

 <span data-ttu-id="a5d85-119">Чтобы использовать моникер с типизированным контрактом, в COM следует зарегистрировать типы с правильными атрибутами для контракта службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-119">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="a5d85-120">Сначала необходимо создать клиент с помощью [средства служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a5d85-120">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="a5d85-121">Чтобы создать типизированную учетную запись-посредник, выполните следующую команду из командной строки в каталоге клиента.</span><span class="sxs-lookup"><span data-stu-id="a5d85-121">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="a5d85-122">Этот класс необходимо включить в проект, а проект следует настроить на создание во время компиляции подписанной сборки, видимой для COM.</span><span class="sxs-lookup"><span data-stu-id="a5d85-122">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="a5d85-123">В файле AssemblyInfo.cs необходимо указать следующий атрибут:</span><span class="sxs-lookup"><span data-stu-id="a5d85-123">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="a5d85-124">После создания проекта зарегистрируйте типы, видимые для модели COM, с помощью `regasm`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a5d85-124">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="a5d85-125">Создаваемую сборку следует добавить в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="a5d85-125">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="a5d85-126">Хотя это не является строго обязательным, такая операция упростит процесс поиска сборки средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="a5d85-126">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="a5d85-127">Следующая команда добавляет сборку в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="a5d85-127">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="a5d85-128">Для моникера службы требуется только регистрация типа, он не использует прокси-сервер для связи со службой.</span><span class="sxs-lookup"><span data-stu-id="a5d85-128">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="a5d85-129">Приложение клиента ComCalcClient.vbs использует функцию `GetObject` для создания прокси-сервера для службы с помощью синтаксиса моникера службы для указания адреса, привязки и контракта службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-129">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="a5d85-130">Используемые моникером параметры определяют следующее.</span><span class="sxs-lookup"><span data-stu-id="a5d85-130">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="a5d85-131">Адрес конечной точки службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-131">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="a5d85-132">Привязка, которую клиент должен использовать для подключения к этой конечной точке.</span><span class="sxs-lookup"><span data-stu-id="a5d85-132">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="a5d85-133">В этом случае используется определенная системой привязка wsHttpBinding, хотя пользовательские привязки можно определить в файлах конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="a5d85-133">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="a5d85-134">Для использования с сервером скрипт Windows пользовательская привязка определяется в файле Cscript.exe.config в том же каталоге, где находится файл Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="a5d85-134">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="a5d85-135">Тип контракта, поддерживаемый конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="a5d85-135">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="a5d85-136">Это тип, который был создан и зарегистрирован выше.</span><span class="sxs-lookup"><span data-stu-id="a5d85-136">This is the type that was generated and registered above.</span></span> <span data-ttu-id="a5d85-137">Поскольку Visual Basic скрипт не предоставляет строго типизированную среду COM, необходимо указать идентификатор контракта.</span><span class="sxs-lookup"><span data-stu-id="a5d85-137">Because Visual Basic script does not provide a strongly typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="a5d85-138">Этот глобальный уникальный идентификатор является `interfaceID` из файла CalcProxy.tlb, который можно просмотреть средствами COM, такими как программа просмотра объектов OLE/COM (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="a5d85-138">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="a5d85-139">Для строго типизированных сред, таких как Office VBA или Visual Basic 6,0, Добавление явной ссылки на библиотеку типов и последующее объявление типа прокси-объекта может использоваться вместо параметра контракта.</span><span class="sxs-lookup"><span data-stu-id="a5d85-139">For strongly typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="a5d85-140">Это также обеспечивает поддержку IntelliSense во время разработки клиентского приложения.</span><span class="sxs-lookup"><span data-stu-id="a5d85-140">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="a5d85-141">После создания экземпляра прокси-сервера с моникером службы клиентское приложение может вызывать методы для прокси, результатом чего станет вызов инфраструктурой моникера службы соответствующих операций службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-141">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 При запуске образца в окне сообщений сервера скриптов Windows отображается ответ операции. Это демонстрирует COM-клиент, выполняющий вызовы COM с помощью типизированного моникера для взаимодействия со службой WCF. <span data-ttu-id="a5d85-144">Несмотря на использование COM в клиентском приложении, взаимодействие со службой состоит только из вызовов веб-службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-144">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="a5d85-145">Контракт WSDL</span><span class="sxs-lookup"><span data-stu-id="a5d85-145">WSDL Contract</span></span>  

 <span data-ttu-id="a5d85-146">Чтобы использовать моникер с контрактом WSDL, регистрация библиотеки клиентов не требуется, однако контракт WSDL службы должен быть извлечен из нештатного механизма (например, с помощью браузера) для получения службой доступа к конечной точке WSDL.</span><span class="sxs-lookup"><span data-stu-id="a5d85-146">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="a5d85-147">После этого моникер может связываться с контрактом во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="a5d85-147">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="a5d85-148">Приложение клиента ComCalcClient.vbs использует функцию `FileSystemObject` для доступа к локально сохраненному файлу WSDL, затем снова использует функцию `GetObject`, чтобы создать для службы прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="a5d85-148">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="a5d85-149">Используемые моникером параметры определяют следующее.</span><span class="sxs-lookup"><span data-stu-id="a5d85-149">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="a5d85-150">Адрес конечной точки службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-150">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="a5d85-151">Привязка, которую должен использовать клиент для подключения к этой конечной точке, и пространство имен, в котором определяется эта привязка.</span><span class="sxs-lookup"><span data-stu-id="a5d85-151">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="a5d85-152">В этом случае используется `wsHttpBinding_ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="a5d85-152">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="a5d85-153">Язык WSDL, определяющий контракт.</span><span class="sxs-lookup"><span data-stu-id="a5d85-153">The WSDL that defines the contract.</span></span> <span data-ttu-id="a5d85-154">В данном случае это строка, считанная из файла serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="a5d85-154">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="a5d85-155">Имя и пространство имен контракта.</span><span class="sxs-lookup"><span data-stu-id="a5d85-155">The name and namespace of the contract.</span></span> <span data-ttu-id="a5d85-156">Эта идентификация требуется, поскольку WSDL может содержать не один контракт.</span><span class="sxs-lookup"><span data-stu-id="a5d85-156">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a5d85-157">По умолчанию службы WCF создают отдельные WSDL-файлы для каждого пространства имен, которое используется.</span><span class="sxs-lookup"><span data-stu-id="a5d85-157">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="a5d85-158">Они связаны с использованием конструктора импорта WSDL.</span><span class="sxs-lookup"><span data-stu-id="a5d85-158">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="a5d85-159">Поскольку моникер ожидает одного определения WSDL, в службе должно использоваться либо одно пространство имен (как показано в этом образце), либо требуется объединение отдельных файлов вручную.</span><span class="sxs-lookup"><span data-stu-id="a5d85-159">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="a5d85-160">После создания экземпляра прокси-сервера с моникером службы клиентское приложение может вызывать методы для прокси, результатом чего станет вызов инфраструктурой моникера службы соответствующих операций службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-160">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 При запуске образца в окне сообщений сервера скриптов Windows отображается ответ операции. <span data-ttu-id="a5d85-162">Это демонстрирует COM-клиент, выполняющий вызовы COM с использованием моникера с контрактом WSDL для взаимодействия со службой WCF.</span><span class="sxs-lookup"><span data-stu-id="a5d85-162">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="a5d85-163">Контракт обмена метаданными</span><span class="sxs-lookup"><span data-stu-id="a5d85-163">Metadata Exchange Contract</span></span>  

 <span data-ttu-id="a5d85-164">Чтобы использовать моникер с контрактом MEX, регистрация клиента не требуется, как и в случае с контрактом WSDL.</span><span class="sxs-lookup"><span data-stu-id="a5d85-164">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="a5d85-165">Контракт для службы извлекается во время выполнения путем внутреннего использования обмена метаданными.</span><span class="sxs-lookup"><span data-stu-id="a5d85-165">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="a5d85-166">Клиентское приложение ComCalcClient.vbs повторно использует функцию `GetObject` для создания прокси-сервера для службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-166">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="a5d85-167">Используемые моникером параметры определяют следующее.</span><span class="sxs-lookup"><span data-stu-id="a5d85-167">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="a5d85-168">Адрес конечной точки обмена метаданными службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-168">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="a5d85-169">Адрес конечной точки службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-169">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="a5d85-170">Привязка, которую должен использовать клиент для подключения к этой конечной точке, и пространство имен, в котором определяется эта привязка.</span><span class="sxs-lookup"><span data-stu-id="a5d85-170">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="a5d85-171">В этом случае используется `wsHttpBinding_ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="a5d85-171">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="a5d85-172">Имя и пространство имен контракта.</span><span class="sxs-lookup"><span data-stu-id="a5d85-172">The name and namespace of the contract.</span></span> <span data-ttu-id="a5d85-173">Эта идентификация требуется, поскольку WSDL может содержать не один контракт.</span><span class="sxs-lookup"><span data-stu-id="a5d85-173">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="a5d85-174">После создания экземпляра прокси-сервера с моникером службы клиентское приложение может вызывать методы для прокси, результатом чего станет вызов инфраструктурой моникера службы соответствующих операций службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-174">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 При запуске образца в окне сообщений сервера скриптов Windows отображается ответ операции. <span data-ttu-id="a5d85-176">Это демонстрирует COM-клиент, выполняющий вызовы COM с использованием моникера с контрактом MEX для взаимодействия со службой WCF.</span><span class="sxs-lookup"><span data-stu-id="a5d85-176">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="a5d85-177">Настройка и сборка образца</span><span class="sxs-lookup"><span data-stu-id="a5d85-177">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="a5d85-178">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5d85-178">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a5d85-179">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5d85-179">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a5d85-180">В Командная строка разработчика для Visual Studio откройте папку \client\bin\ в папке для конкретного языка.</span><span class="sxs-lookup"><span data-stu-id="a5d85-180">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a5d85-181">Если вы используете Windows Vista, Windows Server 2008, Windows 7 или Windows Server 2008 R2, убедитесь, что запущена командная строка с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="a5d85-181">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="a5d85-182">Введите, `tlbexp.exe client.dll /out:CalcProxy.tlb` чтобы экспортировать библиотеку DLL в TLB-файл.</span><span class="sxs-lookup"><span data-stu-id="a5d85-182">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="a5d85-183">Появится сообщение "Предупреждение программы экспорта библиотек типов", однако это не свидетельствует о наличии проблем, поскольку универсальный тип не требуется.</span><span class="sxs-lookup"><span data-stu-id="a5d85-183">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="a5d85-184">Введите, `regasm.exe /tlb:CalcProxy.tlb client.dll` чтобы зарегистрировать типы в com.</span><span class="sxs-lookup"><span data-stu-id="a5d85-184">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="a5d85-185">Появится сообщение "Предупреждение программы экспорта библиотек типов", однако это не свидетельствует о наличии проблем, поскольку универсальный тип не требуется.</span><span class="sxs-lookup"><span data-stu-id="a5d85-185">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="a5d85-186">Введите, `gacutil.exe /i client.dll` чтобы добавить сборку в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="a5d85-186">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a5d85-187">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="a5d85-187">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="a5d85-188">Проверьте, что доступ к службе можно получить с помощью браузера, введя следующий адрес: `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="a5d85-188">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="a5d85-189">Должна отобразиться страница подтверждения.</span><span class="sxs-lookup"><span data-stu-id="a5d85-189">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="a5d85-190">Запустите файл ComCalcClient.vbs из папки \client в языковой папке.</span><span class="sxs-lookup"><span data-stu-id="a5d85-190">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="a5d85-191">Действия клиента отображаются в окнах сообщений.</span><span class="sxs-lookup"><span data-stu-id="a5d85-191">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="a5d85-192">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a5d85-192">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a5d85-193">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="a5d85-193">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="a5d85-194">Создайте на компьютере службы виртуальный каталог с именем ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="a5d85-194">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="a5d85-195">Скрипт Setupvroot.bat, включенный в образец, можно использовать для создания каталога диска и виртуального каталога.</span><span class="sxs-lookup"><span data-stu-id="a5d85-195">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="a5d85-196">Скопируйте файлы служебной программы из каталога %SystemDrive%\Inetpub\wwwroot\servicemodelsamples в виртуальный каталог ServiceModelSamples на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-196">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="a5d85-197">Не забудьте включить файлы в каталог \bin.</span><span class="sxs-lookup"><span data-stu-id="a5d85-197">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="a5d85-198">Скопируйте на клиентский компьютер файл клиентского скрипта из папки \client в языковой папке.</span><span class="sxs-lookup"><span data-stu-id="a5d85-198">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="a5d85-199">В файле скрипта измените значение адреса определения конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="a5d85-199">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="a5d85-200">Замените любые ссылки на "localhost" в адресе полным именем домена.</span><span class="sxs-lookup"><span data-stu-id="a5d85-200">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="a5d85-201">Скопируйте файл языка WSDL на компьютер клиента.</span><span class="sxs-lookup"><span data-stu-id="a5d85-201">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="a5d85-202">В файле языка WSDL (serviceWsdl.xml) замените любые ссылки на "localhost" в адресе полным доменным именем.</span><span class="sxs-lookup"><span data-stu-id="a5d85-202">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="a5d85-203">Скопируйте в каталог на клиентском компьютере библиотеку Client.dll из папки \client\bin\ в языковой папке.</span><span class="sxs-lookup"><span data-stu-id="a5d85-203">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="a5d85-204">В командной строке перейдите в каталог назначения на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="a5d85-204">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="a5d85-205">При использовании Windows Vista или Windows Server 2008 не забудьте запустить командную строку от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="a5d85-205">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="a5d85-206">Введите, `tlbexp.exe client.dll /out:CalcProxy.tlb` чтобы экспортировать библиотеку DLL в TLB-файл.</span><span class="sxs-lookup"><span data-stu-id="a5d85-206">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="a5d85-207">Появится сообщение "Предупреждение программы экспорта библиотек типов", однако это не свидетельствует о наличии проблем, поскольку универсальный тип не требуется.</span><span class="sxs-lookup"><span data-stu-id="a5d85-207">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="a5d85-208">Введите, `regasm.exe /tlb:CalcProxy.tlb client.dll` чтобы зарегистрировать типы в com.</span><span class="sxs-lookup"><span data-stu-id="a5d85-208">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="a5d85-209">Убедитесь, что для пути задана папка, содержащая `regasm.exe` перед выполнением команды.</span><span class="sxs-lookup"><span data-stu-id="a5d85-209">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="a5d85-210">Введите, `gacutil.exe /i client.dll` чтобы добавить сборку в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="a5d85-210">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="a5d85-211">Убедитесь, что для пути задана папка, содержащая `gacutil.exe` перед выполнением команды.</span><span class="sxs-lookup"><span data-stu-id="a5d85-211">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="a5d85-212">Убедитесь, что доступ к службе с клиентского компьютера можно получить из браузера.</span><span class="sxs-lookup"><span data-stu-id="a5d85-212">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="a5d85-213">На клиентском компьютере запустите ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="a5d85-213">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a5d85-214">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="a5d85-214">To clean up after the sample</span></span>  
  
- <span data-ttu-id="a5d85-215">В целях безопасности удалите определение виртуального каталога и разрешения, предоставленные на шагах установки, по завершении работы с образцами.</span><span class="sxs-lookup"><span data-stu-id="a5d85-215">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>
