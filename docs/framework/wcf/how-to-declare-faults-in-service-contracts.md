---
description: Дополнительные сведения см. в статье как объявлять ошибки в контрактах служб.
title: Практическое руководство. Объявление сбоев в контрактах служб
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 1d83840386338747c983d8c4e9a788a452b9c4b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793263"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="d733c-103">Практическое руководство. Объявление сбоев в контрактах служб</span><span class="sxs-lookup"><span data-stu-id="d733c-103">How to: Declare Faults in Service Contracts</span></span>

<span data-ttu-id="d733c-104">В управляемом коде исключения создаются в случае возникновения ошибки.</span><span class="sxs-lookup"><span data-stu-id="d733c-104">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="d733c-105">Однако в приложениях Windows Communication Foundation (WCF) контракты служб указывают, какие сведения об ошибке возвращаются клиентам, объявляя ошибки SOAP в контракте службы.</span><span class="sxs-lookup"><span data-stu-id="d733c-105">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="d733c-106">Общие сведения о связи между исключениями и сбоями см. [в разделе Указание и обработка ошибок в контрактах и службах](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="d733c-106">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="d733c-107">Создайте контракт службы, в котором определяется ошибка SOAP</span><span class="sxs-lookup"><span data-stu-id="d733c-107">Create a service contract that specifies a SOAP fault</span></span>

1. <span data-ttu-id="d733c-108">Создайте контракт службы, который содержит как минимум одну операцию.</span><span class="sxs-lookup"><span data-stu-id="d733c-108">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="d733c-109">Пример см. в разделе [как определить контракт службы](how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d733c-109">For an example, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md).</span></span>

2. <span data-ttu-id="d733c-110">Выберите операцию, которая задает условие ошибки, о которой предполагается уведомить клиентов.</span><span class="sxs-lookup"><span data-stu-id="d733c-110">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="d733c-111">Сведения о том, какие условия ошибок по высоте возвращают ошибки SOAP клиентам, см. в разделе [Указание и обработка ошибок в контрактах и службах](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="d733c-111">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

3. <span data-ttu-id="d733c-112">Примените атрибут <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> к выбранной операции и передайте в конструктор сериализуемый тип ошибки.</span><span class="sxs-lookup"><span data-stu-id="d733c-112">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="d733c-113">Дополнительные сведения о создании и использовании сериализуемых типов см. [в разделе указание передача данных в контрактах служб](./feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d733c-113">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](./feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="d733c-114">В следующем примере показано, как указать, что операция `SampleMethod` может возвращать `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="d733c-114">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>

     [!code-csharp[FaultContractAttribute#4](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. <span data-ttu-id="d733c-115">Повторите шаги 2 и 3 для всех операций контракта, которые могут передавать клиентам условия ошибок.</span><span class="sxs-lookup"><span data-stu-id="d733c-115">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="d733c-116">Реализация операции, возвращающей заданную ошибку SOAP</span><span class="sxs-lookup"><span data-stu-id="d733c-116">Implementing an Operation to Return a Specified SOAP Fault</span></span>

 <span data-ttu-id="d733c-117">После задания операции, возвращающей конкретную ошибку SOAP (например, как в описанной выше процедуре) для передачи условия ошибки вызывающему приложения, необходимо реализовать соответствующую спецификацию.</span><span class="sxs-lookup"><span data-stu-id="d733c-117">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>

### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="d733c-118">Создайте заданную ошибку SOAP в операции</span><span class="sxs-lookup"><span data-stu-id="d733c-118">Throw the specified SOAP fault in the operation</span></span>

1. <span data-ttu-id="d733c-119">Когда в операции возникает условие ошибки, задаваемое атрибутом <xref:System.ServiceModel.FaultContractAttribute>, создайте новое исключение <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>, где заданная ошибка SOAP является параметром типа.</span><span class="sxs-lookup"><span data-stu-id="d733c-119">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="d733c-120">В следующих примерах кода демонстрируется, как создать ошибку `GreetingFault` в методе `SampleMethod`, показанном в описанной выше процедуре и в следующем разделе Code.</span><span class="sxs-lookup"><span data-stu-id="d733c-120">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>

     [!code-csharp[FaultContractAttribute#5](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a><span data-ttu-id="d733c-121">Пример</span><span class="sxs-lookup"><span data-stu-id="d733c-121">Example</span></span>

<span data-ttu-id="d733c-122">В следующем примере кода показана реализация одной операции, которая задает ошибку `GreetingFault` для операции `SampleMethod`.</span><span class="sxs-lookup"><span data-stu-id="d733c-122">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>

[!code-csharp[FaultContractAttribute#1](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a><span data-ttu-id="d733c-123">См. также</span><span class="sxs-lookup"><span data-stu-id="d733c-123">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
