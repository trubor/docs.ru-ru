---
description: Дополнительные сведения о поддержке POCO
title: Поддержка POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 8d44e7a3ebffc6c460a735587ca56990953b2d9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793185"
---
# <a name="poco-support"></a><span data-ttu-id="19ba8-103">Поддержка POCO</span><span class="sxs-lookup"><span data-stu-id="19ba8-103">POCO Support</span></span>

<span data-ttu-id="19ba8-104">В этом образце демонстрируется поддержка сериализации непомеченных типов, т. е. типов, к которым не применены атрибуты сериализации. Иногда такие типы называют типами POCO (Plain Old CLR Object).</span><span class="sxs-lookup"><span data-stu-id="19ba8-104">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="19ba8-105">Объект <xref:System.Runtime.Serialization.DataContractSerializer> выводит контракт данных для всех открытых непомеченных типов, имеющих конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="19ba8-105">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="19ba8-106">Контракты данных позволяют передавать структурированные данные в службы и из служб.</span><span class="sxs-lookup"><span data-stu-id="19ba8-106">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="19ba8-107">Дополнительные сведения о непомеченных типах см. в разделе [сериализуемые типы](../feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="19ba8-107">For more information about unmarked types, see [Serializable Types](../feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="19ba8-108">Этот образец основан на [Начало работы](getting-started-sample.md), но использует комплексные числа, а не простые числовые типы.</span><span class="sxs-lookup"><span data-stu-id="19ba8-108">This sample is based on the [Getting Started](getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="19ba8-109">Он также похож на пример [базового контракта данных](basic-data-contract.md) , за исключением того, <xref:System.Runtime.Serialization.DataContractAttribute> что <xref:System.Runtime.Serialization.DataMemberAttribute> атрибуты и не используются.</span><span class="sxs-lookup"><span data-stu-id="19ba8-109">It is also similar to the [Basic Data Contract](basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="19ba8-110">Клиентом является консольное приложение (EXE), а служба размещается в службах Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="19ba8-110">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19ba8-111">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="19ba8-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="19ba8-112">Класс `ComplexNumber` используется классом `ServiceContract`.</span><span class="sxs-lookup"><span data-stu-id="19ba8-112">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="19ba8-113">У типа `ComplexNumber` нет атрибутов <xref:System.Runtime.Serialization.DataContractAttribute> и <xref:System.Runtime.Serialization.DataMemberAttribute>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="19ba8-113">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="19ba8-114">По умолчанию все открытые свойства и поля сериализуются.</span><span class="sxs-lookup"><span data-stu-id="19ba8-114">By default, all public properties and fields are serialized.</span></span>  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="19ba8-115">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="19ba8-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="19ba8-116">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19ba8-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="19ba8-117">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19ba8-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="19ba8-118">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19ba8-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="19ba8-119">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="19ba8-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="19ba8-120">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="19ba8-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="19ba8-121">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="19ba8-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="19ba8-122">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="19ba8-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="19ba8-123">См. также</span><span class="sxs-lookup"><span data-stu-id="19ba8-123">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="19ba8-124">Сериализуемые типы</span><span class="sxs-lookup"><span data-stu-id="19ba8-124">Serializable Types</span></span>](../feature-details/serializable-types.md)
