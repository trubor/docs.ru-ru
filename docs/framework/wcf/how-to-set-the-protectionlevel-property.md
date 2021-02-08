---
description: Дополнительные сведения см. в статье как задать свойство ProtectionLevel.
title: Практическое руководство. Установка свойства ProtectionLevel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 526ed923d254f0312c9a2c6d17b7306973d88902
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779248"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="df3e0-103">Практическое руководство. Установка свойства ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="df3e0-103">How to: Set the ProtectionLevel Property</span></span>

<span data-ttu-id="df3e0-104">Уровень защиты можно задать, применив соответствующий атрибут и задав свойство.</span><span class="sxs-lookup"><span data-stu-id="df3e0-104">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="df3e0-105">Защиту на уровне службы можно задать таким образом, чтобы она влияла на все части каждого сообщения, можно также задать защиту на более детализированных уровнях - от методов до частей сообщения.</span><span class="sxs-lookup"><span data-stu-id="df3e0-105">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="df3e0-106">Дополнительные сведения о `ProtectionLevel` свойстве см. в разделе Основные сведения об [уровне защиты](understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="df3e0-106">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df3e0-107">Уровни защиты можно задавать только в коде, а не в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="df3e0-107">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="df3e0-108">Подписание всех сообщений для службы</span><span class="sxs-lookup"><span data-stu-id="df3e0-108">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="df3e0-109">Создайте интерфейс для службы.</span><span class="sxs-lookup"><span data-stu-id="df3e0-109">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="df3e0-110">Примените к службе атрибут <xref:System.ServiceModel.ServiceContractAttribute> и задайте значение <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> для свойства <xref:System.Net.Security.ProtectionLevel.Sign>, как показано в следующем примере кода (уровень по умолчанию - <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="df3e0-110">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="df3e0-111">Подписание всех частей сообщения для операции</span><span class="sxs-lookup"><span data-stu-id="df3e0-111">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="df3e0-112">Создайте интерфейс для службы и примените к нему атрибут <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="df3e0-112">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="df3e0-113">Добавьте в интерфейс объявление метода.</span><span class="sxs-lookup"><span data-stu-id="df3e0-113">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="df3e0-114">Примените к методу атрибут <xref:System.ServiceModel.OperationContractAttribute> и задайте значение <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> для свойства <xref:System.Net.Security.ProtectionLevel.Sign>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="df3e0-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="df3e0-115">Защита сообщений об ошибках</span><span class="sxs-lookup"><span data-stu-id="df3e0-115">Protecting Fault Messages</span></span>  

 <span data-ttu-id="df3e0-116">Создаваемые в службе исключения можно отправить клиенту в виде ошибок SOAP.</span><span class="sxs-lookup"><span data-stu-id="df3e0-116">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="df3e0-117">Дополнительные сведения о создании строго типизированных ошибок см. [в разделе Указание и обработка ошибок в контрактах и службах](specifying-and-handling-faults-in-contracts-and-services.md) и [инструкции: объявление ошибок в контрактах служб](how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="df3e0-117">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="df3e0-118">Защита сообщения об ошибке</span><span class="sxs-lookup"><span data-stu-id="df3e0-118">To protect a fault message</span></span>  
  
1. <span data-ttu-id="df3e0-119">Создайте тип, представляющий сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="df3e0-119">Create a type that represents the fault message.</span></span> <span data-ttu-id="df3e0-120">В следующем примере описано создание класса, именуемого `MathFault`, с двумя полями.</span><span class="sxs-lookup"><span data-stu-id="df3e0-120">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="df3e0-121">Примените к типу атрибут <xref:System.Runtime.Serialization.DataContractAttribute>, а к каждому полю, которое должно быть сериализовано, - атрибут <xref:System.Runtime.Serialization.DataMemberAttribute>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="df3e0-121">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="df3e0-122">Примените атрибут <xref:System.ServiceModel.FaultContractAttribute> к методу, который будет возвращать ошибку, и настройте параметр `detailType` к типу класса ошибки в интерфейсе, который будет возвращать ошибку,</span><span class="sxs-lookup"><span data-stu-id="df3e0-122">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="df3e0-123">Задайте для свойства <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> значение <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> в конструкторе, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="df3e0-123">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="df3e0-124">Защита частей сообщения</span><span class="sxs-lookup"><span data-stu-id="df3e0-124">Protecting Message Parts</span></span>  

 <span data-ttu-id="df3e0-125">Для защиты частей сообщения следует использовать контракт сообщения.</span><span class="sxs-lookup"><span data-stu-id="df3e0-125">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="df3e0-126">Дополнительные сведения о контрактах сообщений см. [в разделе Использование контрактов сообщений](./feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="df3e0-126">For more information about message contracts, see [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="df3e0-127">Защита тела сообщения</span><span class="sxs-lookup"><span data-stu-id="df3e0-127">To protect a message body</span></span>  
  
1. <span data-ttu-id="df3e0-128">Создайте тип, представляющий сообщение.</span><span class="sxs-lookup"><span data-stu-id="df3e0-128">Create a type that represents the message.</span></span> <span data-ttu-id="df3e0-129">В следующем примере описано создание класса `Company` двумя полями: `CompanyName` и `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="df3e0-129">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="df3e0-130">Примените атрибут <xref:System.ServiceModel.MessageContractAttribute> к классу и задайте значение <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> для свойства <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="df3e0-130">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="df3e0-131">Примените атрибут <xref:System.ServiceModel.MessageHeaderAttribute> к полю, которое будет выражено как заголовок сообщения, и задайте значение `ProtectionLevel` для свойства <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="df3e0-131">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="df3e0-132">Примените <xref:System.ServiceModel.MessageBodyMemberAttribute> к любому полю, которое будет выражаться как часть текста сообщения, и задайте `ProtectionLevel` для свойства значение <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="df3e0-132">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="df3e0-133">Пример</span><span class="sxs-lookup"><span data-stu-id="df3e0-133">Example</span></span>  

 <span data-ttu-id="df3e0-134">В следующем примере демонстрируется, как задать свойство `ProtectionLevel` нескольких классов атрибута в разных местах службы.</span><span class="sxs-lookup"><span data-stu-id="df3e0-134">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="df3e0-135">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="df3e0-135">Compiling the Code</span></span>  

 <span data-ttu-id="df3e0-136">В следующем примере кода показаны пространства имен, необходимые для компиляции примера кода.</span><span class="sxs-lookup"><span data-stu-id="df3e0-136">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="df3e0-137">См. также</span><span class="sxs-lookup"><span data-stu-id="df3e0-137">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="df3e0-138">Основные сведения об уровне защиты</span><span class="sxs-lookup"><span data-stu-id="df3e0-138">Understanding Protection Level</span></span>](understanding-protection-level.md)
