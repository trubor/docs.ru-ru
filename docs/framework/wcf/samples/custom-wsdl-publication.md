---
description: 'Дополнительные сведения: пользовательская публикация WSDL'
title: Пользовательская публикация WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 39bb884a6c89d24fc38b89db09c848c87e663870
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752422"
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="59dbd-103">Пользовательская публикация WSDL</span><span class="sxs-lookup"><span data-stu-id="59dbd-103">Custom WSDL Publication</span></span>

<span data-ttu-id="59dbd-104">В этом примере показано, как:</span><span class="sxs-lookup"><span data-stu-id="59dbd-104">This sample demonstrates how to:</span></span>  
  
- <span data-ttu-id="59dbd-105">реализации <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> пользовательского атрибута <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> для экспорта свойств атрибута в виде заметок WSDL;</span><span class="sxs-lookup"><span data-stu-id="59dbd-105">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
- <span data-ttu-id="59dbd-106">Реализация <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> для импорта пользовательских заметок WSDL.</span><span class="sxs-lookup"><span data-stu-id="59dbd-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
- <span data-ttu-id="59dbd-107">Реализация <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> и <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> в пользовательском поведении контракта и пользовательском поведении операции соответственно для записи импортированных заметок в виде комментариев в CodeDom для импортированных контракта и операции.</span><span class="sxs-lookup"><span data-stu-id="59dbd-107">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
- <span data-ttu-id="59dbd-108">Используйте <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> для загрузки языка WSDL, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> для импорта WSDL-файла с помощью пользовательского средства импорта WSDL и <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> для создания клиентского кода Windows Communication Foundation (WCF) с аннотацией WSDL как///и комментариями "'" в C# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="59dbd-108">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate Windows Communication Foundation (WCF) client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59dbd-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="59dbd-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="59dbd-110">Служба</span><span class="sxs-lookup"><span data-stu-id="59dbd-110">Service</span></span>  

 <span data-ttu-id="59dbd-111">В этом образце служба помечена двумя пользовательскими атрибутами.</span><span class="sxs-lookup"><span data-stu-id="59dbd-111">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="59dbd-112">Первый атрибут, `WsdlDocumentationAttribute`, принимает строку в конструкторе и может применяться для предоставления интерфейса контракта или операции со строкой, описывающей их использование.</span><span class="sxs-lookup"><span data-stu-id="59dbd-112">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="59dbd-113">Второй атрибут, `WsdlParamOrReturnDocumentationAttribute`, может применяться для возврата значений или параметров, описывающих эти значения в операции.</span><span class="sxs-lookup"><span data-stu-id="59dbd-113">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="59dbd-114">В следующем примере показан контракт службы `ICalculator`, описанный с помощью этих атрибутов.</span><span class="sxs-lookup"><span data-stu-id="59dbd-114">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
```csharp  
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 <span data-ttu-id="59dbd-115">Атрибут `WsdlDocumentationAttribute` реализует интерфейсы <xref:System.ServiceModel.Description.IContractBehavior> и <xref:System.ServiceModel.Description.IOperationBehavior>, поэтому экземпляры атрибута при открытии службы добавляются к соответствующему описанию <xref:System.ServiceModel.Description.ContractDescription> или <xref:System.ServiceModel.Description.OperationDescription>.</span><span class="sxs-lookup"><span data-stu-id="59dbd-115">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="59dbd-116">Кроме того, атрибут реализует интерфейс <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span><span class="sxs-lookup"><span data-stu-id="59dbd-116">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="59dbd-117">При вызове метода <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> объект <xref:System.ServiceModel.Description.WsdlExporter>, который служит для экспорта метаданных, и объект <xref:System.ServiceModel.Description.WsdlContractConversionContext>, который содержит объекты описания службы, передаются в качестве параметров, что позволяет изменить экспортированные метаданные.</span><span class="sxs-lookup"><span data-stu-id="59dbd-117">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="59dbd-118">В этом образце в зависимости от того, какое описание (<xref:System.ServiceModel.Description.ContractDescription> или <xref:System.ServiceModel.Description.OperationDescription>) имеется у объекта контекста экспорта, комментарий извлекается из атрибута с помощью текстового свойства и добавляется в элемент заметки WSDL, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="59dbd-118">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)
{
    if (contractDescription != null)
    {
        // Inside this block it is the contract-level comment attribute.
        // This.Text returns the string for the contract attribute.
        // Set the doc element; if this isn't done first, there is no XmlElement in the
        // DocumentElement property.
        context.WsdlPortType.Documentation = string.Empty;
        // Contract comments.
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;
        XmlElement summaryElement = owner.CreateElement("summary");
        summaryElement.InnerText = this.Text;
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);
    }
    else
    {
        Operation operation = context.GetOperation(operationDescription);
        if (operation != null)
        {
            // We are dealing strictly with the operation here.
            // This.Text returns the string for the operation-level attributes.
            // Set the doc element; if this isn't done first, there is no XmlElement in the
            // DocumentElement property.
            operation.Documentation = String.Empty;

            // Operation C# triple comments.
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;
            XmlElement newSummaryElement = owner.CreateElement("summary");
            newSummaryElement.InnerText = this.Text;
            operation.DocumentationElement.AppendChild(newSummaryElement);
        }
    }
}
```  
  
 <span data-ttu-id="59dbd-119">Если экспортируется операция, в образце используется отражение, чтобы получить все значения `WsdlParamOrReturnDocumentationAttribute` параметров и возвращаемые значения, после чего эти значения добавляются в элементы заметки WSDL этой операции, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="59dbd-119">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
```csharp
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 <span data-ttu-id="59dbd-120">После этого образец обычным образом публикует метаданные с использованием следующего файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="59dbd-120">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
```xml  
<services>  
  <service
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a><span data-ttu-id="59dbd-121">Клиент Svcutil</span><span class="sxs-lookup"><span data-stu-id="59dbd-121">Svcutil client</span></span>  

 <span data-ttu-id="59dbd-122">В этом образце средство Svcutil.exe не используется.</span><span class="sxs-lookup"><span data-stu-id="59dbd-122">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="59dbd-123">Контракт предоставляется в файле generatedClient.cs, поэтому службу можно вызывать после того, как образец продемонстрирует пользовательский импорт WSDL и создание кода.</span><span class="sxs-lookup"><span data-stu-id="59dbd-123">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="59dbd-124">Чтобы использовать в этом примере приведенный ниже пользовательский импортер WSDL, можно запустить средство Svcutil.exe с параметром `/svcutilConfig`, задав путь к используемому в этом примере файлу конфигурации клиента, в котором содержится ссылка на библиотеку `WsdlDocumentation.dll`.</span><span class="sxs-lookup"><span data-stu-id="59dbd-124">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="59dbd-125">Но для загрузки `WsdlDocumentationImporter` средство Svuctil.exe должно иметь возможность находить и загружать библиотеку `WsdlDocumentation.dll`, что означает, что она либо должна быть зарегистрирована в глобальном кэше сборок, либо располагаться в одном каталоге с файлом Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="59dbd-125">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="59dbd-126">Для простых образцах, таких как этот, удобнее всего скопировать программу Svcutil.exe и файл конфигурации в один каталог с файлом `WsdlDocumentation.dll` и запускать ее оттуда.</span><span class="sxs-lookup"><span data-stu-id="59dbd-126">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="59dbd-127">Пользовательский импортер WSDL</span><span class="sxs-lookup"><span data-stu-id="59dbd-127">The Custom WSDL Importer</span></span>  

 <span data-ttu-id="59dbd-128">Пользовательский импортер <xref:System.ServiceModel.Description.IWsdlImportExtension> объекта `WsdlDocumentationImporter` также реализует интерфейсы <xref:System.ServiceModel.Description.IContractBehavior> и <xref:System.ServiceModel.Description.IOperationBehavior>, добавляемые в импортированные конечные точки службы, и интерфейсы<xref:System.ServiceModel.Description.IServiceContractGenerationExtension> и <xref:System.ServiceModel.Description.IOperationContractGenerationExtension>, вызываемые для изменения создания кода контракта или операции.</span><span class="sxs-lookup"><span data-stu-id="59dbd-128">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="59dbd-129">Сначала в методе <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> образец определяет, относится ли заметка WSDL к уровню контракта или службы, после чего он добавляет себя в качестве поведения в соответствующую область, передавая импортированный текст заметки в конструктор.</span><span class="sxs-lookup"><span data-stu-id="59dbd-129">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
```csharp
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="59dbd-130">Затем, при создании кода, система вызывает методы <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> и <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29>, передавая им сведения о соответствующем контексте.</span><span class="sxs-lookup"><span data-stu-id="59dbd-130">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="59dbd-131">Образец форматирует пользовательские заметки WSDL и вставляет их в CodeDom в виде комментариев.</span><span class="sxs-lookup"><span data-stu-id="59dbd-131">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
```csharp
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a><span data-ttu-id="59dbd-132">Клиентское приложение</span><span class="sxs-lookup"><span data-stu-id="59dbd-132">The Client Application</span></span>  

 <span data-ttu-id="59dbd-133">Клиентское приложение загружает пользовательский импортер WSDL путем указания его в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="59dbd-133">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"
  binding="wsHttpBinding"
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 <span data-ttu-id="59dbd-134">После указания пользовательского средства импорта система метаданных WCF загружает пользовательский импортер в любой <xref:System.ServiceModel.Description.WsdlImporter> , созданный для этой цели.</span><span class="sxs-lookup"><span data-stu-id="59dbd-134">Once the custom importer has been specified, the WCF metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="59dbd-135">В этом образце используется <xref:System.ServiceModel.Description.MetadataExchangeClient> для загрузки метаданных, правильно настроенный <xref:System.ServiceModel.Description.WsdlImporter> для импорта метаданных с помощью создаваемого образецом пользовательского импортера и <xref:System.ServiceModel.Description.ServiceContractGenerator> для компиляции измененных сведений контракта в клиентский код Visual Basic и C#, который можно использовать в Visual Studio для поддержки Intellisense или скомпилировать в XML-документацию.</span><span class="sxs-lookup"><span data-stu-id="59dbd-135">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
```csharp
/// From WSDL Documentation:  
///
/// <summary>The ICalculator contract performs basic calculation
/// services.</summary>
///
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Add operation adds two numbers and returns the
    /// result.</summary><returns>The result of adding the two arguments
    /// together.</returns><param name="n1">The first value to add.</param><param
    /// name="n2">The second value to add.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Subtract operation subtracts the second argument from the
    /// first.</summary><returns>The result of the second argument subtracted from the
    /// first.</returns><param name="n1">The value from which the second is
    /// subtracted.</param><param name="n2">The value that is subtracted from the
    /// first.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The
    /// result of multiplying the first and second arguments.</returns><param
    /// name="n1">The first value to multiply.</param><param name="n2">The second value
    /// to multiply.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///
    /// <summary>The Divide operation returns the value of the first argument divided
    /// by the second argument.</summary><returns>The result of dividing the first
    /// argument by the second.</returns><param name="n1">The numerator.</param><param
    /// name="n2">The denominator.</param>
    ///
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59dbd-136">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="59dbd-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="59dbd-137">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59dbd-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="59dbd-138">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59dbd-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="59dbd-139">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59dbd-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="59dbd-140">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="59dbd-140">The samples may already be installed on your machine.</span></span> <span data-ttu-id="59dbd-141">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="59dbd-141">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="59dbd-142">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="59dbd-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59dbd-143">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="59dbd-143">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
