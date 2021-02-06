---
description: 'Дополнительные сведения о: использование арбитра контрактов данных'
title: Использование арбитра контрактов данных
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 89571c63b9135f164e0b687251798e3b67153b8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632299"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="df9a7-103">Использование арбитра контрактов данных</span><span class="sxs-lookup"><span data-stu-id="df9a7-103">Using a Data Contract Resolver</span></span>

<span data-ttu-id="df9a7-104">Арбитр контрактов данных позволяет динамически настраивать известные типы.</span><span class="sxs-lookup"><span data-stu-id="df9a7-104">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="df9a7-105">Известные типы необходимы для сериализации или десериализации типов, не предусмотренных контрактом данных.</span><span class="sxs-lookup"><span data-stu-id="df9a7-105">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="df9a7-106">Дополнительные сведения об известных типах см. в разделе [Data Contract известные типы](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="df9a7-106">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="df9a7-107">Известные типы обычно задаются статически.</span><span class="sxs-lookup"><span data-stu-id="df9a7-107">Known types are normally specified statically.</span></span> <span data-ttu-id="df9a7-108">Это означает, что при реализации операции необходимо знать все типы, которые могут быть переданы операции.</span><span class="sxs-lookup"><span data-stu-id="df9a7-108">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="df9a7-109">Существуют сценарии, в которых это не так, и важно иметь возможность динамического задания типов.</span><span class="sxs-lookup"><span data-stu-id="df9a7-109">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="df9a7-110">Создание арбитра контрактов данных</span><span class="sxs-lookup"><span data-stu-id="df9a7-110">Creating a Data Contract Resolver</span></span>  

 <span data-ttu-id="df9a7-111">Создание арбитра контрактов данных включает реализацию двух методов: <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> и <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="df9a7-111">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="df9a7-112">Эти методы реализуют обратные вызовы, используемые при сериализации и десериализации соответственно.</span><span class="sxs-lookup"><span data-stu-id="df9a7-112">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="df9a7-113">Метод <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> вызывается при сериализации, принимает тип контракта данных и сопоставляет его с именем `xsi:type` и пространством имен.</span><span class="sxs-lookup"><span data-stu-id="df9a7-113">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="df9a7-114">Метод <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> вызывается при десериализации, принимает имя `xsi:type` и пространство имен и сопоставляется с типом контракта данных.</span><span class="sxs-lookup"><span data-stu-id="df9a7-114">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="df9a7-115">Оба метода содержат параметр `knownTypeResolver`, который позволяет использовать в реализации арбитр известного типа по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="df9a7-115">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="df9a7-116">В следующем примере показана реализация <xref:System.Runtime.Serialization.DataContractResolver> для сопоставления с типом контракта данных с именем `Customer`, производного от типа контракта данных `Person`.</span><span class="sxs-lookup"><span data-stu-id="df9a7-116">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="df9a7-117">После определения <xref:System.Runtime.Serialization.DataContractResolver> его можно передать в конструктор <xref:System.Runtime.Serialization.DataContractSerializer>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="df9a7-117">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="df9a7-118">Можно указать <xref:System.Runtime.Serialization.DataContractResolver> в вызове метода <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> или <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="df9a7-118">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="df9a7-119">Или же можно задать его для <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="df9a7-119">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```csharp
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 <span data-ttu-id="df9a7-120">Сопоставитель контрактов данных можно задать декларативно, реализовав атрибут, применяемый к службе.</span><span class="sxs-lookup"><span data-stu-id="df9a7-120">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="df9a7-121">Дополнительные сведения см. в примере [кновнассембляттрибуте](../samples/knownassemblyattribute.md) .</span><span class="sxs-lookup"><span data-stu-id="df9a7-121">For more information, see the [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="df9a7-122">В этом примере реализуется атрибут с именем «Кновнассембли», который добавляет пользовательский сопоставитель контракта данных к поведению службы.</span><span class="sxs-lookup"><span data-stu-id="df9a7-122">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df9a7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="df9a7-123">See also</span></span>

- [<span data-ttu-id="df9a7-124">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="df9a7-124">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="df9a7-125">Пример DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="df9a7-125">DataContractSerializer Sample</span></span>](../samples/datacontractserializer-sample.md)
- [<span data-ttu-id="df9a7-126">Атрибут KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="df9a7-126">KnownAssemblyAttribute</span></span>](../samples/knownassemblyattribute.md)
