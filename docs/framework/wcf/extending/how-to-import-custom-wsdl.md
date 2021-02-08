---
description: Дополнительные сведения см. в статье как импортировать пользовательский язык WSDL.
title: Практическое руководство. Импорт пользовательской информации WSDL
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: f21e5cace532bd6d20d409f297480f65bb23cbf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780743"
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="c46bb-103">Практическое руководство. Импорт пользовательской информации WSDL</span><span class="sxs-lookup"><span data-stu-id="c46bb-103">How to: Import Custom WSDL</span></span>

<span data-ttu-id="c46bb-104">В этом разделе описывается, как импортировать пользовательский код WSDL.</span><span class="sxs-lookup"><span data-stu-id="c46bb-104">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="c46bb-105">Для работы с пользовательским кодом WSDL необходимо реализовать интерфейс <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="c46bb-105">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="c46bb-106">Импорт пользовательского кода WSDL</span><span class="sxs-lookup"><span data-stu-id="c46bb-106">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="c46bb-107">Реализуйте расширение <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="c46bb-107">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="c46bb-108">Реализуйте метод <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29>, чтобы он изменял метаданные перед их импортом.</span><span class="sxs-lookup"><span data-stu-id="c46bb-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="c46bb-109">Реализуйте методы <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> и <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>, чтобы они изменяли контракты и конечные точки, импортированные из метаданных.</span><span class="sxs-lookup"><span data-stu-id="c46bb-109">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="c46bb-110">Чтобы обратиться к импортированному контракту или конечной точке, следует использовать соответствующий объект контекста (<xref:System.ServiceModel.Description.WsdlContractConversionContext> или <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span><span class="sxs-lookup"><span data-stu-id="c46bb-110">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
    ```csharp
    public class WsdlDocumentationImporter : IWsdlImportExtension
    {
        public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)
        {
            // Contract documentation
            if (context.WsdlPortType.Documentation != null)
            {
                context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));
            }
            // Operation documentation
            foreach (Operation operation in context.WsdlPortType.Operations)
            {
                if (operation.Documentation != null)
                {
                    OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);
                    if (operationDescription != null)
                    {
                        operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));
                    }
                }
            }
        }

        public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)
        {
            Console.WriteLine("BeforeImport called.");
        }

        public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)
        {
            Console.WriteLine("ImportEndpoint called.");
        }
    }
    ```
  
2. <span data-ttu-id="c46bb-111">Настройте клиентское приложение, чтобы оно использовало пользовательский импортер WSDL.</span><span class="sxs-lookup"><span data-stu-id="c46bb-111">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="c46bb-112">Обратите внимание, что при использовании средства Svcutil.exe соответствующие параметры необходимо задать в файле конфигурации этого средства (Svcutil.exe.config):</span><span class="sxs-lookup"><span data-stu-id="c46bb-112">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
    ```xml  
    <system.serviceModel>  
          <client>  
            <endpoint
              address="http://localhost:8000/Fibonacci"
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="c46bb-113">Создайте новый экземпляр <xref:System.ServiceModel.Description.WsdlImporter> (передав ему экземпляр <xref:System.ServiceModel.Description.MetadataSet>, содержащий документы WSDL, которые требуется импортировать) и вызовите метод <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span><span class="sxs-lookup"><span data-stu-id="c46bb-113">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c46bb-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c46bb-114">See also</span></span>

- [<span data-ttu-id="c46bb-115">Метаданные</span><span class="sxs-lookup"><span data-stu-id="c46bb-115">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="c46bb-116">Экспорт и импорт метаданных</span><span class="sxs-lookup"><span data-stu-id="c46bb-116">Exporting and Importing Metadata</span></span>](../feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="c46bb-117">Пользовательская публикация WSDL</span><span class="sxs-lookup"><span data-stu-id="c46bb-117">Custom WSDL Publication</span></span>](../samples/custom-wsdl-publication.md)
