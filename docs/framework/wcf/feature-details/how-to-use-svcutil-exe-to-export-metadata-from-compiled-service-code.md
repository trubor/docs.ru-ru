---
description: Дополнительные сведения см. в статье как использовать Svcutil.exe для экспорта метаданных из скомпилированного кода службы.
title: Практическое руководство. Использование программы Svcutil.exe для экспорта метаданных из скомпилированного кода службы
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 509d987ff27f9a05ca59d6065d76f27006f3cb25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734208"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="3eaf1-103">Практическое руководство. Использование программы Svcutil.exe для экспорта метаданных из скомпилированного кода службы</span><span class="sxs-lookup"><span data-stu-id="3eaf1-103">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>

<span data-ttu-id="3eaf1-104">При помощи Svcutil.exe можно экспортировать метаданные для служб, контрактов и типов данных в скомпилированных сборках, как показано далее.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-104">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
- <span data-ttu-id="3eaf1-105">Для экспорта метаданных всех скомпилированных контрактов службы для набора сборок при помощи Svcutil.exe необходимо указать сборки как входные параметры.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-105">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="3eaf1-106">Это поведение установлено по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-106">This is the default behavior.</span></span>  
  
- <span data-ttu-id="3eaf1-107">Для экспорта метаданных скомпилированной службы для набора сборок при помощи Svcutil.exe необходимо указать сборку службы как входные параметры.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-107">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="3eaf1-108">Для указания имени конфигурации экспортируемой службы необходимо использовать параметр `/serviceName`.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-108">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="3eaf1-109">Svcutil.exe автоматически загружает файл конфигурации для указанной сборки исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-109">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
- <span data-ttu-id="3eaf1-110">Для экспорта всех типов контрактов данных внутри набора сборок используется параметр `/dataContractOnly`.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-110">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3eaf1-111">Для указания пути к файлам любых зависимых сборок используется параметр `/reference`.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-111">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="3eaf1-112">Экспорт метаданных в скомпилированные контракты службы</span><span class="sxs-lookup"><span data-stu-id="3eaf1-112">To export metadata for compiled service contracts</span></span>  
  
1. <span data-ttu-id="3eaf1-113">Скомпилируйте реализации контракта службы в одну или несколько библиотек классов.1</span><span class="sxs-lookup"><span data-stu-id="3eaf1-113">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2. <span data-ttu-id="3eaf1-114">Запустите Svcutil.exe в скомпилированных сборках.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-114">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3eaf1-115">Для указания пути к файлам любых зависимых сборок может понадобиться использование параметра `/reference`.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-115">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="3eaf1-116">Экспорт метаданных в скомпилированную службу</span><span class="sxs-lookup"><span data-stu-id="3eaf1-116">To export metadata for a compiled service</span></span>  
  
1. <span data-ttu-id="3eaf1-117">Скомпилируйте реализацию службы в исполняемую сборку.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-117">Compile your service implementation into an executable assembly.</span></span>  
  
2. <span data-ttu-id="3eaf1-118">Создайте файл конфигурации для исполняемого файла службы и добавьте конфигурацию службы.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-118">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3. <span data-ttu-id="3eaf1-119">Чтобы указать имя конфигурации службы, необходимо запустить Svcutil.exe в скомпилированном исполняемом файле службы при помощи параметра `/serviceName`.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-119">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3eaf1-120">Для указания пути к файлам любых зависимых сборок может понадобиться использование параметра `/reference`.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-120">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="3eaf1-121">Экспорт метаданных в скомпилированные контракты данных</span><span class="sxs-lookup"><span data-stu-id="3eaf1-121">To export metadata for compiled data contracts</span></span>  
  
1. <span data-ttu-id="3eaf1-122">Скомпилируйте реализации контракта данных в одну или несколько библиотек классов.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-122">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2. <span data-ttu-id="3eaf1-123">Чтобы задать генерацию только метаданных для контрактов данных, запустите Svcutil.exe в скомпилированных сборках с параметром `/dataContract`.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-123">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3eaf1-124">Для указания пути к файлам любых зависимых сборок может понадобиться использование параметра `/reference`.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-124">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="3eaf1-125">Пример</span><span class="sxs-lookup"><span data-stu-id="3eaf1-125">Example</span></span>  

 <span data-ttu-id="3eaf1-126">В следующем примере показано, как генерировать метаданные для реализации и конфигурации простой службы.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-126">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="3eaf1-127">Экспорт метаданных в контракт службы.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-127">To export metadata for the service contract.</span></span>  
  
```console  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="3eaf1-128">Экспорт метаданных в контракты данных.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-128">To export metadata for the data contracts.</span></span>  
  
```console  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="3eaf1-129">Экспорт метаданных в реализацию службы.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-129">To export metadata for the service implementation.</span></span>  
  
```console  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="3eaf1-130">`<path>` является путем к файлу Contracts.dll.</span><span class="sxs-lookup"><span data-stu-id="3eaf1-130">The `<path>` is the path to Contracts.dll.</span></span>  
  
```csharp
// The following service contract and data contracts are compiled into
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
```

```csharp
// The following service implementation is compiled into Service.exe.
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
```

```xml  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3eaf1-131">См. также</span><span class="sxs-lookup"><span data-stu-id="3eaf1-131">See also</span></span>

- [<span data-ttu-id="3eaf1-132">Служебное средство ServiceModel Metadata Utility Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="3eaf1-132">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="3eaf1-133">Экспорт и импорт метаданных</span><span class="sxs-lookup"><span data-stu-id="3eaf1-133">Exporting and Importing Metadata</span></span>](exporting-and-importing-metadata.md)
