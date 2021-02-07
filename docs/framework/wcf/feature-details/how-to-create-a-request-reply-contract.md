---
description: Дополнительные сведения о том, как создать контракт Request-Reply.
title: Практическое руководство. Создание контракта типа "запрос — ответ"
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: f5e63538a405aa451ffd3be114485604c00fa407
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734702"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="06394-103">Практическое руководство. Создание контракта типа "запрос — ответ"</span><span class="sxs-lookup"><span data-stu-id="06394-103">How to: Create a Request-Reply Contract</span></span>

<span data-ttu-id="06394-104">Контракт «запрос-ответ» указывает метод, который возвращает ответ.</span><span class="sxs-lookup"><span data-stu-id="06394-104">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="06394-105">Необходима отправка ответа и его корреляция запросу согласно условиям этого контракта.</span><span class="sxs-lookup"><span data-stu-id="06394-105">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="06394-106">Даже если метод не возвращает ответ (`void` в C# или `Sub` в Visual Basic), инфраструктура создает и отправляет вызывающему объекту пустое сообщение.</span><span class="sxs-lookup"><span data-stu-id="06394-106">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="06394-107">Чтобы запретить отправку пустого ответного сообщения, используйте для операции односторонний контракт.</span><span class="sxs-lookup"><span data-stu-id="06394-107">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="06394-108">Создание контракта типа запрос-ответ</span><span class="sxs-lookup"><span data-stu-id="06394-108">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="06394-109">Создайте интерфейс на любом языке программирования.</span><span class="sxs-lookup"><span data-stu-id="06394-109">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="06394-110">Примените атрибут <xref:System.ServiceModel.ServiceContractAttribute> к интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="06394-110">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="06394-111">Примените атрибут <xref:System.ServiceModel.OperationContractAttribute> к каждому методу, который могут вызывать клиенты.</span><span class="sxs-lookup"><span data-stu-id="06394-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="06394-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="06394-112">Optional.</span></span> <span data-ttu-id="06394-113">Установите свойство <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> в значение `true`, чтобы избежать отправки пустого ответного сообщения.</span><span class="sxs-lookup"><span data-stu-id="06394-113">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="06394-114">По умолчанию все операции используют контракты «запрос-ответ».</span><span class="sxs-lookup"><span data-stu-id="06394-114">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06394-115">Пример</span><span class="sxs-lookup"><span data-stu-id="06394-115">Example</span></span>  

 <span data-ttu-id="06394-116">В следующем примере определяется контракт для службы калькулятора, предоставляющей методы `Add` и `Subtract`.</span><span class="sxs-lookup"><span data-stu-id="06394-116">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="06394-117">Метод `Multiply` не является частью контракта, поскольку он не отмечен классом <xref:System.ServiceModel.OperationContractAttribute>, а потому недоступен клиентам.</span><span class="sxs-lookup"><span data-stu-id="06394-117">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- <span data-ttu-id="06394-118">Дополнительные сведения об указании контрактов операций см. в разделе <xref:System.ServiceModel.OperationContractAttribute> класс и <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="06394-118">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="06394-119">Применение атрибутов <xref:System.ServiceModel.ServiceContractAttribute> и <xref:System.ServiceModel.OperationContractAttribute> вызывает автоматическое создание определений контракта службы в документе WSDL после развертывания службы.</span><span class="sxs-lookup"><span data-stu-id="06394-119">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="06394-120">Документ загружается путем добавления `?wsdl` к базовому адресу HTTP для службы,</span><span class="sxs-lookup"><span data-stu-id="06394-120">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="06394-121">Например: `http://microsoft/CalculatorService?wsdl`</span><span class="sxs-lookup"><span data-stu-id="06394-121">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06394-122">См. также</span><span class="sxs-lookup"><span data-stu-id="06394-122">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="06394-123">Создание контрактов служб</span><span class="sxs-lookup"><span data-stu-id="06394-123">Designing Service Contracts</span></span>](../designing-service-contracts.md)
- [<span data-ttu-id="06394-124">Практическое руководство. Создание двухстороннего контракта</span><span class="sxs-lookup"><span data-stu-id="06394-124">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
