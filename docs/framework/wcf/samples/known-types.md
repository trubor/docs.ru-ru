---
description: 'Дополнительные сведения: известные типы'
title: Известные типы
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: 52aedb226b1e7396820292af3782274bd0ece847
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726329"
---
# <a name="known-types"></a><span data-ttu-id="5a09a-103">Известные типы</span><span class="sxs-lookup"><span data-stu-id="5a09a-103">Known Types</span></span>

<span data-ttu-id="5a09a-104">В данном образце демонстрируется, как задать информацию о наследованных типах в контракте данных.</span><span class="sxs-lookup"><span data-stu-id="5a09a-104">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="5a09a-105">Контракты данных позволяют передавать структурированные данные в службы и из служб.</span><span class="sxs-lookup"><span data-stu-id="5a09a-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="5a09a-106">В объектно-ориентированном программировании тип, унаследованный от другого типа, может использоваться вместо оригинального типа.</span><span class="sxs-lookup"><span data-stu-id="5a09a-106">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="5a09a-107">В объектно-ориентированном программировании отслеживаются скорее типы, а не схемы, и поэтому отношение между типами не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="5a09a-107">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="5a09a-108">Атрибут <xref:System.Runtime.Serialization.KnownTypeAttribute> позволяет включать в контракт данных информацию об унаследованных типах.</span><span class="sxs-lookup"><span data-stu-id="5a09a-108">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="5a09a-109">Если этот механизм не используется, унаследованный тип не может быть отправлен или получен там, где ожидается базовый тип.</span><span class="sxs-lookup"><span data-stu-id="5a09a-109">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a09a-110">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="5a09a-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5a09a-111">Контракт службы для службы использует комплексные числа, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="5a09a-111">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="5a09a-112">Тип <xref:System.Runtime.Serialization.DataContractAttribute> и <xref:System.Runtime.Serialization.DataMemberAttribute> применяется к классу `ComplexNumber` для указания тех полей класса, которые можно передавать между клиентом и службой.</span><span class="sxs-lookup"><span data-stu-id="5a09a-112">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="5a09a-113">Вместо `ComplexNumberWithMagnitude` можно использовать унаследованный класс `ComplexNumber`.</span><span class="sxs-lookup"><span data-stu-id="5a09a-113">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="5a09a-114">На это указывает атрибут <xref:System.Runtime.Serialization.KnownTypeAttribute> типа `ComplexNumber`.</span><span class="sxs-lookup"><span data-stu-id="5a09a-114">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
[KnownType(typeof(ComplexNumberWithMagnitude))]  
public class ComplexNumber  
{  
    [DataMember]  
    public double Real = 0.0D;  
    [DataMember]  
    public double Imaginary = 0.0D;  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
 <span data-ttu-id="5a09a-115">Тип `ComplexNumberWithMagnitude` наследуется от `ComplexNumber`, но добавляет дополнительный член данных - `Magnitude`.</span><span class="sxs-lookup"><span data-stu-id="5a09a-115">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumberWithMagnitude : ComplexNumber  
{  
    public ComplexNumberWithMagnitude(double real, double imaginary) :  
        base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary*Imaginary  + Real*Real); }  
        set { throw new NotImplementedException(); }  
    }  
}  
```  
  
 <span data-ttu-id="5a09a-116">Чтобы продемонстрировать функцию известных типов, служба реализуется таким образом, чтобы она возвращала `ComplexNumberWithMagnitude` только для сложения и вычитания.</span><span class="sxs-lookup"><span data-stu-id="5a09a-116">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="5a09a-117">(Даже несмотря на то, что контракт указывает `ComplexNumber`, это разрешается благодаря атрибуту `KnownTypeAttribute`).</span><span class="sxs-lookup"><span data-stu-id="5a09a-117">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="5a09a-118">Умножение и деление по-прежнему возвращают базовый `ComplexNumber` тип.</span><span class="sxs-lookup"><span data-stu-id="5a09a-118">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
```csharp
public class DataContractCalculatorService : IDataContractCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real,  
                                      n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real,
                                 n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        //Return the base type.  
        return new ComplexNumber(real1 + real2, imaginary1 +
                                                  imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real,
                                     -1*n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
        //Return the base type.  
        return new ComplexNumber(numerator.Real / denominator.Real,  
                                             numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="5a09a-119">На клиенте как контракт службы, так и контракт данных определяются в исходном файле generatedClient.cs, который создается [служебной программой метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) из метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="5a09a-119">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="5a09a-120">Поскольку атрибут <xref:System.Runtime.Serialization.KnownTypeAttribute> указан в контракте данных службы, клиент может получать при использовании службы классы `ComplexNumber` и `ComplexNumberWithMagnitude`.</span><span class="sxs-lookup"><span data-stu-id="5a09a-120">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="5a09a-121">Клиент определяет, получен ли `ComplexNumberWithMagnitude`, и создает соответствующие выходные данные.</span><span class="sxs-lookup"><span data-stu-id="5a09a-121">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
```csharp
// Create a client  
DataContractCalculatorClient client =
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber() { real = 1, imaginary = 2 };  
ComplexNumber value2 = new ComplexNumber() { real = 3, imaginary = 4 };  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.real, value1.imaginary, value2.real, value2.imaginary,  
    result.real, result.imaginary);  
if (result is ComplexNumberWithMagnitude)  
{  
    Console.WriteLine("Magnitude: {0}",
        ((ComplexNumberWithMagnitude)result).Magnitude);  
}  
else  
{  
    Console.WriteLine("No magnitude was sent from the service");  
}  
```  
  
 <span data-ttu-id="5a09a-122">При выполнении образца запросы и отклики операции отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="5a09a-122">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="5a09a-123">Обратите внимание, что умножение выводится для добавления или вычитания, но не для умножения или деления, по причине использованного способа реализации службы.</span><span class="sxs-lookup"><span data-stu-id="5a09a-123">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="5a09a-124">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="5a09a-124">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
    Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a09a-125">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="5a09a-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5a09a-126">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a09a-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5a09a-127">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a09a-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5a09a-128">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a09a-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5a09a-129">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5a09a-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a09a-130">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5a09a-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5a09a-131">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="5a09a-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a09a-132">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5a09a-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
