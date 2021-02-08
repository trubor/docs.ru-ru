---
description: Дополнительные сведения см. в статье как улучшить время запуска клиентских приложений WCF с помощью XmlSerializer.
title: Практическое руководство. Сокращение времени запуска клиентских приложений WCF с использованием XmlSerializer
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 8cf46cc35753934e8f4cb3abadc20c912e9efca9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793406"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="77fc4-103">Практическое руководство. Сокращение времени запуска клиентских приложений WCF с использованием XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="77fc4-103">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>

<span data-ttu-id="77fc4-104">Службы и клиентские приложения, использующие типы данных, сериализуемые с помощью сериализатора <xref:System.Xml.Serialization.XmlSerializer>, создают и компилируют код сериализации для этих типов данных во время выполнения, что может привести к снижению производительности при запуске.</span><span class="sxs-lookup"><span data-stu-id="77fc4-104">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77fc4-105">Предварительно созданный код сериализации может использоваться только в клиентских приложениях, но не в службах.</span><span class="sxs-lookup"><span data-stu-id="77fc4-105">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="77fc4-106">[Средство служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) может улучшить производительность при запуске этих приложений, создавая необходимый код сериализации из скомпилированных сборок для приложения.</span><span class="sxs-lookup"><span data-stu-id="77fc4-106">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="77fc4-107">Svcutil.exe создает код сериализации для всех типов данных, используемых в контрактах служб в скомпилированной сборке приложения, которые могут быть сериализованы с помощью <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="77fc4-107">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="77fc4-108">Контракты служб и операций, предусматривающие использование <xref:System.Xml.Serialization.XmlSerializer>, отмечены атрибутом <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="77fc4-108">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="77fc4-109">Создание кода сериализации XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="77fc4-109">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="77fc4-110">Скомпилируйте код службы или клиента в одну или несколько сборок.</span><span class="sxs-lookup"><span data-stu-id="77fc4-110">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="77fc4-111">Откройте окно командной строки SDK.</span><span class="sxs-lookup"><span data-stu-id="77fc4-111">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="77fc4-112">Из командной строки запустите средство Svcutil.exe, используя следующий формат.</span><span class="sxs-lookup"><span data-stu-id="77fc4-112">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="77fc4-113">Аргумент `assemblyPath` задает путь к сборке, содержащей типы из контракта службы.</span><span class="sxs-lookup"><span data-stu-id="77fc4-113">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="77fc4-114">Svcutil.exe создает код сериализации для всех типов данных, используемых в контрактах служб в скомпилированной сборке приложения, которые могут быть сериализованы с помощью <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="77fc4-114">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="77fc4-115">Svcutil.exe может формировать только код сериализации на C#.</span><span class="sxs-lookup"><span data-stu-id="77fc4-115">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="77fc4-116">Для каждой входной сборки создается один файл исходного кода.</span><span class="sxs-lookup"><span data-stu-id="77fc4-116">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="77fc4-117">Нельзя использовать параметр **/Language** для изменения языка созданного кода.</span><span class="sxs-lookup"><span data-stu-id="77fc4-117">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="77fc4-118">Чтобы указать путь к зависимым сборкам, используйте параметр **/Reference** .</span><span class="sxs-lookup"><span data-stu-id="77fc4-118">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="77fc4-119">Предоставьте приложению доступ к созданному коду сериализации одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="77fc4-119">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1. <span data-ttu-id="77fc4-120">Скомпилируйте созданный код сериализации в отдельную сборку с именем [*Исходная сборка*] .XmlSerializers.dll (например, MyApp.XmlSerializers.dll).</span><span class="sxs-lookup"><span data-stu-id="77fc4-120">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="77fc4-121">Приложение должно иметь возможность загрузить эту сборку, которая должна быть подписана с помощью того же ключа, что и исходная сборка.</span><span class="sxs-lookup"><span data-stu-id="77fc4-121">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="77fc4-122">В случае повторной компиляции исходной сборки необходимо заново создать сборку сериализации.</span><span class="sxs-lookup"><span data-stu-id="77fc4-122">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2. <span data-ttu-id="77fc4-123">Скомпилируйте созданный код сериализации в отдельную сборку и используйте атрибут <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> в контракте службы, в котором используется атрибут <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="77fc4-123">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="77fc4-124">Задайте свойство <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> или <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> так, чтобы оно указывало на скомпилированную сборку сериализации.</span><span class="sxs-lookup"><span data-stu-id="77fc4-124">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3. <span data-ttu-id="77fc4-125">Скомпилируйте созданный код сериализации в сборку приложения и добавьте атрибут <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> в контракт службы, в котором используется атрибут <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="77fc4-125">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="77fc4-126">Не задавайте свойства <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> или <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="77fc4-126">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="77fc4-127">По умолчанию предполагается, что сборка сериализации по умолчанию является текущей сборкой.</span><span class="sxs-lookup"><span data-stu-id="77fc4-127">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="77fc4-128">Создание кода сериализации XmlSerializer в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77fc4-128">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="77fc4-129">Создание проектов службы и клиента WCF в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77fc4-129">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="77fc4-130">Затем добавьте ссылку на службу в клиентский проект.</span><span class="sxs-lookup"><span data-stu-id="77fc4-130">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="77fc4-131">Добавьте в <xref:System.ServiceModel.XmlSerializerFormatAttribute> контракт службы в файле *Reference.CS* в проекте клиентского приложения в разделе **укзать**  ->  **Reference. svcmap**.</span><span class="sxs-lookup"><span data-stu-id="77fc4-131">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="77fc4-132">Обратите внимание, что для просмотра этих файлов необходимо показать все файлы в **Обозреватель решений** .</span><span class="sxs-lookup"><span data-stu-id="77fc4-132">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="77fc4-133">Создайте клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="77fc4-133">Build the client app.</span></span>  
  
4. <span data-ttu-id="77fc4-134">Используйте [средство служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , чтобы создать предварительно созданный файл сериализатора *. CS* с помощью команды:</span><span class="sxs-lookup"><span data-stu-id="77fc4-134">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="77fc4-135">Аргумент _ указывает путь к клиентской сборке WCF.</span><span class="sxs-lookup"><span data-stu-id="77fc4-135">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="77fc4-136">Например:</span><span class="sxs-lookup"><span data-stu-id="77fc4-136">Such as:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="77fc4-137">Будет создан файл *WCFClient.XmlSerializers.dll. CS* .</span><span class="sxs-lookup"><span data-stu-id="77fc4-137">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="77fc4-138">Скомпилируйте предварительно созданную сборку сериализации.</span><span class="sxs-lookup"><span data-stu-id="77fc4-138">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="77fc4-139">В зависимости от примера, приведенного на предыдущем шаге, команда Compile будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="77fc4-139">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="77fc4-140">Убедитесь, что созданный *WCFClient.XmlSerializers.dll* находится в том же каталоге, что и клиентское приложение, которое *WCFClient.exe* в этом случае.</span><span class="sxs-lookup"><span data-stu-id="77fc4-140">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="77fc4-141">Запустите клиентское приложение обычным образом.</span><span class="sxs-lookup"><span data-stu-id="77fc4-141">Run the client app as usual.</span></span> <span data-ttu-id="77fc4-142">Будет использоваться предварительно созданная сборка сериализации.</span><span class="sxs-lookup"><span data-stu-id="77fc4-142">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77fc4-143">Пример</span><span class="sxs-lookup"><span data-stu-id="77fc4-143">Example</span></span>  

 <span data-ttu-id="77fc4-144">Следующая команда создает типы сериализации для типов `XmlSerializer`, используемых любыми контрактами служб в сборке.</span><span class="sxs-lookup"><span data-stu-id="77fc4-144">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="77fc4-145">См. также</span><span class="sxs-lookup"><span data-stu-id="77fc4-145">See also</span></span>

- [<span data-ttu-id="77fc4-146">Служебное средство ServiceModel Metadata Utility Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="77fc4-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
