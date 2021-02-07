---
description: 'Дополнительные сведения: суррогат DataContract'
title: Суррогат DataContract
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 739471efcea1d04752f3065c7a28f55f9ff9a0f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755828"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="1144e-103">Суррогат DataContract</span><span class="sxs-lookup"><span data-stu-id="1144e-103">DataContract Surrogate</span></span>

<span data-ttu-id="1144e-104">В этом образце показано, каким образом такие процессы, как сериализация, десериализация, экспорт и импорт схемы, могут быть настроены при помощи заменяющего класса контракта данных.</span><span class="sxs-lookup"><span data-stu-id="1144e-104">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="1144e-105">В этом примере показано, как использовать суррогат в сценарии клиента и сервера, в котором данные сериализуются и передаются между клиентом Windows Communication Foundation (WCF) и службой.</span><span class="sxs-lookup"><span data-stu-id="1144e-105">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1144e-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="1144e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1144e-107">В этом образце используется следующий контракт службы.</span><span class="sxs-lookup"><span data-stu-id="1144e-107">The sample uses the following service contract:</span></span>  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 <span data-ttu-id="1144e-108">Операция `AddEmployee` позволяет пользователям добавлять данные о новых сотрудниках, а операция `GetEmployee` поддерживает поиск сотрудников по имени.</span><span class="sxs-lookup"><span data-stu-id="1144e-108">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="1144e-109">В этих операциях используется следующий тип данных.</span><span class="sxs-lookup"><span data-stu-id="1144e-109">These operations use the following data type:</span></span>  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 <span data-ttu-id="1144e-110">В типе `Employee` класс `Person` (показан в следующем образце кода) не может быть сериализован с помощью <xref:System.Runtime.Serialization.DataContractSerializer>, поскольку он не является допустимым классом контракта данных.</span><span class="sxs-lookup"><span data-stu-id="1144e-110">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="1144e-111">Можно применить атрибут <xref:System.Runtime.Serialization.DataContractAttribute> к классу `Person`, но это не всегда возможно.</span><span class="sxs-lookup"><span data-stu-id="1144e-111">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="1144e-112">Например, класс `Person` может быть определен в отдельной сборке, управлять которой невозможно.</span><span class="sxs-lookup"><span data-stu-id="1144e-112">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="1144e-113">С учетом этого ограничения одним из способов сериализации класса `Person` является его замена на другой класс, отмеченный атрибутом <xref:System.Runtime.Serialization.DataContractAttribute>, и копирование необходимых данных в новый класс.</span><span class="sxs-lookup"><span data-stu-id="1144e-113">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="1144e-114">Целью является отображение класса `Person` как DataContract в сериализаторе <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1144e-114">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="1144e-115">Обратите внимание, что это один способ сериализации классов, отличных от классов контракта данных.</span><span class="sxs-lookup"><span data-stu-id="1144e-115">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="1144e-116">В этом образце класс `Person` логически заменяется на другой класс с именем `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="1144e-116">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 <span data-ttu-id="1144e-117">Заменяющий класс контракта данных используется для обеспечения такой замены.</span><span class="sxs-lookup"><span data-stu-id="1144e-117">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="1144e-118">Заменяющий класс контракта данных является классом, который реализует <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span><span class="sxs-lookup"><span data-stu-id="1144e-118">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="1144e-119">В этом образце класс `AllowNonSerializableTypesSurrogate` реализует этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="1144e-119">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="1144e-120">В реализации интерфейса первой задачей является установка сопоставления типов из класса `Person` с классом `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="1144e-120">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="1144e-121">Используется как во время сериализации, так и во время экспорта схемы.</span><span class="sxs-lookup"><span data-stu-id="1144e-121">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="1144e-122">Такое сопоставление обеспечивается путем реализации метода <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29>.</span><span class="sxs-lookup"><span data-stu-id="1144e-122">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <span data-ttu-id="1144e-123">Метод <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> сопоставляет экземпляр класса `Person` с экземпляром класса `PersonSurrogated` во время сериализации, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="1144e-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="1144e-124">Метод <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> обеспечивает обратное сопоставление для десериализации, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="1144e-124">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetDeserializedObject(object obj,
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="1144e-125">Чтобы сопоставить контракт данных `PersonSurrogated` с существующим классом `Person` во время импорта схемы, в образце реализуется метод <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="1144e-125">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 <span data-ttu-id="1144e-126">В следующем образце кода показано завершение реализации интерфейса <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span><span class="sxs-lookup"><span data-stu-id="1144e-126">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 <span data-ttu-id="1144e-127">В этом образце заменяющий класс включается в ServiceModel с помощью атрибута `AllowNonSerializableTypesAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1144e-127">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="1144e-128">Разработчикам пришлось бы применить этот атрибут к контракту службы, как показано в контракте службы `IPersonnelDataService` выше.</span><span class="sxs-lookup"><span data-stu-id="1144e-128">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="1144e-129">Этот атрибут реализует `IContractBehavior` и настраивает заменяющий класс в операциях методов `ApplyClientBehavior` и `ApplyDispatchBehavior`.</span><span class="sxs-lookup"><span data-stu-id="1144e-129">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="1144e-130">В этом случае необходимости в атрибуте нет. В этом образце он используется в демонстрационных целях.</span><span class="sxs-lookup"><span data-stu-id="1144e-130">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="1144e-131">Пользователи могут также включить заменяющий класс вручную, добавив похожее поведение `IContractBehavior`, `IEndpointBehavior` или `IOperationBehavior` с использованием кода или конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1144e-131">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="1144e-132">Реализация `IContractBehavior` ищет операции, в которых используется DataContract, проверяя в них наличие зарегистрированного поведения `DataContractSerializerOperationBehavior`.</span><span class="sxs-lookup"><span data-stu-id="1144e-132">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="1144e-133">При его наличии она задает свойство `DataContractSurrogate` для этого поведения.</span><span class="sxs-lookup"><span data-stu-id="1144e-133">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="1144e-134">В следующем образце кода показано, как это можно сделать.</span><span class="sxs-lookup"><span data-stu-id="1144e-134">The following sample code shows how this is done.</span></span> <span data-ttu-id="1144e-135">Задание заменяющего класса для этого поведения операции позволяет ему участвовать в сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="1144e-135">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 <span data-ttu-id="1144e-136">Чтобы подключить заменяющий класс для использования при создании метаданных, необходимо выполнить дополнительные действия.</span><span class="sxs-lookup"><span data-stu-id="1144e-136">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="1144e-137">Одним из механизмов реализации этого является предоставление расширения `IWsdlExportExtension`, как показано в этом образце.</span><span class="sxs-lookup"><span data-stu-id="1144e-137">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="1144e-138">Еще одним способом является непосредственное изменение `WsdlExporter`.</span><span class="sxs-lookup"><span data-stu-id="1144e-138">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="1144e-139">`AllowNonSerializableTypesAttribute`Атрибут реализует `IWsdlExportExtension` и `IContractBehavior` .</span><span class="sxs-lookup"><span data-stu-id="1144e-139">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="1144e-140">В этом случае расширение может быть `IContractBehavior` либо `IEndpointBehavior` .</span><span class="sxs-lookup"><span data-stu-id="1144e-140">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="1144e-141">Реализация метода `IWsdlExportExtension.ExportContract` включает заменяющий класс путем его добавления в `XsdDataContractExporter`, используемый во время создания схемы для DataContract.</span><span class="sxs-lookup"><span data-stu-id="1144e-141">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="1144e-142">В следующем фрагменте кода показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="1144e-142">The following code snippet shows how to do this.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 <span data-ttu-id="1144e-143">При выполнении образца клиент вызывает операцию AddEmployee после вызова операции GetEmployee, чтобы проверить, выполнен ли первый вызов успешно.</span><span class="sxs-lookup"><span data-stu-id="1144e-143">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="1144e-144">Результат запроса операции GetEmployee отображается в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="1144e-144">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="1144e-145">Операция сотрудника должна пройти, чтобы найти сотрудника и напечатать "Found".</span><span class="sxs-lookup"><span data-stu-id="1144e-145">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1144e-146">В этом примере показано, как подключить заменяющий класс для сериализации, десериализации и создания метаданных.</span><span class="sxs-lookup"><span data-stu-id="1144e-146">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="1144e-147">В нем не показано, как подключить заменяющий класс для создания кода из метаданных.</span><span class="sxs-lookup"><span data-stu-id="1144e-147">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="1144e-148">Чтобы увидеть пример того, как суррогат можно использовать для подключения к созданию клиентского кода, см. пример [пользовательской публикации WSDL](custom-wsdl-publication.md) .</span><span class="sxs-lookup"><span data-stu-id="1144e-148">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1144e-149">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="1144e-149">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1144e-150">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1144e-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1144e-151">Чтобы построить выпуск решения на C#, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1144e-151">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1144e-152">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1144e-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1144e-153">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1144e-153">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1144e-154">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="1144e-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1144e-155">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="1144e-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1144e-156">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="1144e-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
