---
description: 'Дополнительные сведения о: Кновнассембляттрибуте'
title: Атрибут KnownAssemblyAttribute
ms.date: 03/30/2017
ms.assetid: b3bc7f31-95ff-46e1-8308-d206ec426f6e
ms.openlocfilehash: e528f547d67b77bd088288a4d079cea903318611
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793250"
---
# <a name="knownassemblyattribute"></a><span data-ttu-id="1e418-103">Атрибут KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="1e418-103">KnownAssemblyAttribute</span></span>

<span data-ttu-id="1e418-104">В этом образце показано, как можно настроить процессы сериализации и десериализации с помощью класса <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="1e418-104">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="1e418-105">В этом образце показано, как динамически добавлять известные типы во время сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="1e418-105">This sample shows how to dynamically add known types during serialization and deserialization.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="1e418-106">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="1e418-106">Sample Details</span></span>  

 <span data-ttu-id="1e418-107">Этот образец состоит из четырех проектов.</span><span class="sxs-lookup"><span data-stu-id="1e418-107">This sample is composed of four projects.</span></span> <span data-ttu-id="1e418-108">Один из них соответствует службе, которая будет размещаться службами IIS и определяет следующий контракт службы.</span><span class="sxs-lookup"><span data-stu-id="1e418-108">One of them corresponds to the service, to be hosted by IIS, which defines the following service contract.</span></span>  
  
```csharp
// Definition of a service contract.  
[ServiceContract(Namespace = "http://Microsoft.Samples.KAA")]  
[KnownAssembly("Types")]  
public interface IDataContractCalculator  
 {  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
  
    [OperationContract]  
    List<ComplexNumber> CombineLists(List<ComplexNumber> list1, List<ComplexNumber> list2);  
}  
```  
  
 <span data-ttu-id="1e418-109">Контракт службы реализован, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1e418-109">The service contract is implemented as shown in the following example.</span></span>  
  
```csharp
// Service class that implements the service contract.  
 public class DataContractCalculatorService : IDataContractCalculator  
 {  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real, n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real, n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
  
        return new ComplexNumber(real1 + real2, imaginary1 + imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real, -1 * n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
  
        return new ComplexNumber(numerator.Real / denominator.Real, numerator.Imaginary);  
    }  
  
    public List<ComplexNumber> CombineLists(List<ComplexNumber> list1, List<ComplexNumber> list2)  
    {  
        List<ComplexNumber> result  = new List<ComplexNumber>();  
        result.AddRange(list1);  
        result.AddRange(list2);  
  
        return result;  
    }  
}  
```  
  
 <span data-ttu-id="1e418-110">Другой проект соответствует клиенту, который сообщается с сервером и вызывает предоставляемые им методы.</span><span class="sxs-lookup"><span data-stu-id="1e418-110">Another project corresponds to the client, which communicates with the server and invokes the methods that it exposes.</span></span> <span data-ttu-id="1e418-111">Определение клиента показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1e418-111">The definition of the client is shown in the following example.</span></span>  
  
```csharp  
 // Client implementation code.  
 class Client  
 {  
    static void Main()  
    {  
        // Create a channel.  
         EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc/IDataContractCalculator");  
        BasicHttpBinding binding = new BasicHttpBinding();  
        ChannelFactory<IDataContractCalculator> factory = new ChannelFactory<IDataContractCalculator>(binding, address);  
        IDataContractCalculator channel = factory.CreateChannel();  
  
        // Call the Add service operation.  
         ComplexNumber value1 = new ComplexNumber(1, 2);  
        ComplexNumber value2 = new ComplexNumberWithMagnitude(3, 4);  
        ComplexNumber result = channel.Add(value1, value2);  
        Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Subtract service operation.  
         value1 = new ComplexNumber(1, 2);  
        value2 = new ComplexNumber(3, 4);  
        result = channel.Subtract(value1, value2);  
        Console.WriteLine("Subtract({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Multiply service operation.  
         value1 = new ComplexNumber(2, 3);  
        value2 = new ComplexNumber(4, 7);  
        result = channel.Multiply(value1, value2);  
        Console.WriteLine("Multiply({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the Divide service operation.  
         value1 = new ComplexNumber(3, 7);  
        value2 = new ComplexNumber(5, -2);  
        result = channel.Divide(value1, value2);  
        Console.WriteLine("Divide({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
            value1.Real, value1.Imaginary, value2.Real, value2.Imaginary, result.Real, result.Imaginary);  
        if (result is ComplexNumberWithMagnitude)  
        {  
            Console.WriteLine("Magnitude: {0}", ((ComplexNumberWithMagnitude)result).Magnitude);  
        }  
        else  
         {  
            Console.WriteLine("No magnitude was sent from the service");  
        }  
        Console.WriteLine();  
  
        // Call the CombineLists service operation.  
         List<ComplexNumber> list1 = new List<ComplexNumber>();  
        List<ComplexNumber> list2 = new List<ComplexNumber>();  
        list1.Add(new ComplexNumber(1, 1));  
        list1.Add(new ComplexNumber(2, 2));  
        list1.Add(new ComplexNumberWithMagnitude(3, 3));  
        list1.Add(new ComplexNumberWithMagnitude(4, 4));  
        List<ComplexNumber> listResult = channel.CombineLists(list1, list2);  
        Console.WriteLine("Lists combined:");  
        foreach (ComplexNumber n in listResult)  
        {  
            Console.WriteLine("{0} + {1}i", n.Real, n.Imaginary);  
        }  
        Console.WriteLine();  
  
        // Close the channel  
         ((IChannel)channel).Close();  
  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="1e418-112">Определение контракта службы помечено атрибутом `KnownAssembly`.</span><span class="sxs-lookup"><span data-stu-id="1e418-112">The definition of the service contract is marked with the `KnownAssembly` attribute.</span></span> <span data-ttu-id="1e418-113">Этот атрибут содержит имя библиотеки типов, каждый из которых становится известным во время выполнения как службе, так и клиенту.</span><span class="sxs-lookup"><span data-stu-id="1e418-113">This attribute contains the name of a library of types, which all become known at runtime by both the service and the client.</span></span>  
  
 <span data-ttu-id="1e418-114">Атрибут `KnownAssembly` реализует интерфейс `IContractBehavior` для того, чтобы определить сериализатор `DataContractSerializer` с арбитром `DataContractResolver` для каждого из поведений операции.</span><span class="sxs-lookup"><span data-stu-id="1e418-114">The `KnownAssembly` attribute implements `IContractBehavior` in order to define a `DataContractSerializer` with a `DataContractResolver` defined for each of the operation behaviors.</span></span> <span data-ttu-id="1e418-115">Арбитр `DataContractResolver` исследует сборку после ее создания и создает словарь с сопоставлениями типов и имен, который используется при сериализации и десериализации различных типов.</span><span class="sxs-lookup"><span data-stu-id="1e418-115">The `DataContractResolver` reflects over the assembly when it is created, and creates the dictionary with the mapping between types and names to be used when serializing and deserializing the different types.</span></span> <span data-ttu-id="1e418-116">Таким образом, типы `ResolveType` и `ResolveName` должны искать необходимые данные в этом словаре.</span><span class="sxs-lookup"><span data-stu-id="1e418-116">In that way, the `ResolveType` and `ResolveName` types must look up the data required in the dictionary.</span></span>  
  
 <span data-ttu-id="1e418-117">Арбитр `DataContractResolver`, определенный для этого образца, показан в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="1e418-117">The `DataContractResolver` defined for this sample is shown in the following example.</span></span>  
  
```csharp
public class MyDataContractResolver : DataContractResolver  
    {  
       Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();  
       Assembly assembly;  
  
       public MyDataContractResolver(string assemblyName)  
       {  
           this.KnownTypes = new List<Type>();  
  
           assembly = Assembly.Load(new AssemblyName(assemblyName));  
           foreach (Type type in assembly.GetTypes())  
           {  
               bool knownTypeFound = false;  
               System.Attribute[] attrs = System.Attribute.GetCustomAttributes(type);  
               if (attrs.Length != 0)  
               {  
                   foreach (System.Attribute attr in attrs)  
                   {  
                       if (attr is KnownTypeAttribute)  
                       {  
                           Type t = ((KnownTypeAttribute)attr).Type;  
                           if (this.KnownTypes.IndexOf(t) < 0)  
                           {  
                               this.KnownTypes.Add(t);  
                           }  
                           knownTypeFound = true;  
                       }  
                   }  
               }  
               if (!knownTypeFound)  
               {  
                   string name = type.Name;  
                   string namesp = type.Namespace;  
                   if (!dictionary.ContainsKey(name))  
                   {  
                       dictionary.Add(name, new XmlDictionaryString(XmlDictionary.Empty, name, 0));  
                   }  
                   if (!dictionary.ContainsKey(namesp))  
                   {  
                       dictionary.Add(namesp, new XmlDictionaryString(XmlDictionary.Empty, namesp, 0));  
                   }  
               }  
           }  
       }  
  
       public IList<Type> KnownTypes  
       {  
           get; set;  
       }  
  
       // Used at deserialization  
        // Allows users to map xsi:type name to any Type
        public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
       {  
           XmlDictionaryString tName;  
           XmlDictionaryString tNamespace;  
  
           if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))  
           {  
               return this.assembly.GetType(tNamespace.Value + "." + tName.Value);  
           }  
           else  
            {  
               return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
           }  
       }  
  
       // Used at serialization  
        // Maps any Type to a new xsi:type representation  
        public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
       {  
           knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);  
           if (typeName == null || typeNamespace == null)  
           {  
               typeName = new XmlDictionaryString(XmlDictionary.Empty, dataContractType.Name, 0);  
               typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, dataContractType.Namespace, 0);  
           }  
       }  
   }  
```  
  
 <span data-ttu-id="1e418-118">Библиотека типов, которая используется в этом образце, показана в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="1e418-118">The library of types used in this sample is shown in the following example.</span></span>  
  
```csharp
 [DataContract]  
 public class ComplexNumber  
 {  
    [DataMember]  
    private double real;  
  
    [DataMember]  
    private double imaginary;  
  
    public ComplexNumber(double r1, double i1)  
    {  
        this.Real = r1;  
        this.Imaginary = i1;  
    }  
  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
}  
  
[DataContract]  
public class ComplexNumberWithMagnitude : ComplexNumber  
 {  
    public ComplexNumberWithMagnitude(double real, double imaginary) : base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary * Imaginary + Real * Real); }  
        set { }  
    }  
}  
```  
  
 <span data-ttu-id="1e418-119">Обратите внимание, что типу `ComplexNumber` не должен быть статически известен тип `ComplexNumberWithMagnitude`, поскольку последний станет известен во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="1e418-119">Note that `ComplexNumber` does not need to statically know the `ComplexNumberWithMagnitude` type, because it becomes known at runtime.</span></span>  
  
 <span data-ttu-id="1e418-120">После того, как образец построен и выполнен, клиент должен ожидать получения следующего вывода.</span><span class="sxs-lookup"><span data-stu-id="1e418-120">When the sample is built and executed, this is the expected output obtained in the client:</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
Lists combined:  
1 + 1i  
2 + 2i  
3 + 3i  
4 + 4i  
```  
  
#### <a name="to-set-up-run-and-build-the-sample"></a><span data-ttu-id="1e418-121">Настройка, выполнение и сборка образца</span><span class="sxs-lookup"><span data-stu-id="1e418-121">To set up, run, and build the sample</span></span>  
  
1. <span data-ttu-id="1e418-122">Щелкните правой кнопкой мыши решение **кновнассембляттрибуте** и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="1e418-122">Right-click the solution **KnownAssemblyAttribute** and select **Properties**.</span></span>  
  
2. <span data-ttu-id="1e418-123">В окне **Общие свойства** выберите **запускаемый проект** и щелкните **Несколько запускаемых проектов**.</span><span class="sxs-lookup"><span data-stu-id="1e418-123">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
3. <span data-ttu-id="1e418-124">Добавьте действие **Start** в проекты **службы** и **клиента** .</span><span class="sxs-lookup"><span data-stu-id="1e418-124">Add the **Start** action to the **Service** and **Client** projects.</span></span>  
  
4. <span data-ttu-id="1e418-125">Нажмите кнопку **ОК** и нажмите клавишу **F5** , чтобы запустить пример.</span><span class="sxs-lookup"><span data-stu-id="1e418-125">Click **OK**, and press **F5** to run the sample.</span></span>  
  
5. <span data-ttu-id="1e418-126">Если приложение выполняется неправильно, убедитесь в правильности настройки среды, выполнив следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="1e418-126">If the application does not run properly, follow these steps to make sure your environment has been properly set up:</span></span>  
  
6. <span data-ttu-id="1e418-127">Убедитесь, что выполнена [однократная настройка процедуры для Windows Communication Foundation примеров](./one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1e418-127">Ensure that you have performed the [One-Time Set Up Procedure for the Windows Communication Foundation Samples](./one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
7. <span data-ttu-id="1e418-128">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примера Windows Communication Foundation](./building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1e418-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Sample](./building-the-samples.md).</span></span>  
  
8. <span data-ttu-id="1e418-129">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](./running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1e418-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](./running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1e418-130">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1e418-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1e418-131">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="1e418-131">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1e418-132">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="1e418-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e418-133">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="1e418-133">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownAssemblyAttribute`
