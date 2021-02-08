---
description: 'Дополнительные сведения: <transactionFlow>'
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 8a853beaec1837606ecb96156b8ec9381fa3e07a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773554"
---
# \<transactionFlow>

<span data-ttu-id="62c65-102">Задает поддержку потока транзакций для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="62c65-102">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="62c65-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="62c65-103">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62c65-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="62c65-104">Attributes and Elements</span></span>  

 <span data-ttu-id="62c65-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="62c65-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62c65-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="62c65-106">Attributes</span></span>  
  
|<span data-ttu-id="62c65-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="62c65-107">Attribute</span></span>|<span data-ttu-id="62c65-108">Описание</span><span class="sxs-lookup"><span data-stu-id="62c65-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62c65-109">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="62c65-109">transactionProtocol</span></span>|<span data-ttu-id="62c65-110">Задает используемый протокол транзакций.</span><span class="sxs-lookup"><span data-stu-id="62c65-110">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="62c65-111">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="62c65-111">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62c65-112">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="62c65-112">-   OleTransactions</span></span><br /><span data-ttu-id="62c65-113">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="62c65-113">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="62c65-114">Значение по умолчанию - OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="62c65-114">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="62c65-115">Это атрибут типа <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="62c65-115">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62c65-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="62c65-116">Child Elements</span></span>  

 <span data-ttu-id="62c65-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="62c65-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62c65-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="62c65-118">Parent Elements</span></span>  
  
|<span data-ttu-id="62c65-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="62c65-119">Element</span></span>|<span data-ttu-id="62c65-120">Описание</span><span class="sxs-lookup"><span data-stu-id="62c65-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="62c65-121">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="62c65-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62c65-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="62c65-122">Remarks</span></span>  

 <span data-ttu-id="62c65-123">Этот элемент позволяет включить или отключить входящий поток транзакций в параметрах привязки конечной точки, а также задать необходимый формат протокола для входящих транзакций.</span><span class="sxs-lookup"><span data-stu-id="62c65-123">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="62c65-124">Дополнительные сведения об использовании этого элемента конфигурации см. в разделе [Конфигурация транзакций ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) и [Включение потока транзакций](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="62c65-124">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="62c65-125">При использовании протокола `OleTransactions` для реализации потока транзакций от одной конечной точки к другой время ожидания транзакции может быть потеряно, если целевая конечная точка попытается запустить поток снова, используя любой протокол, отличный от `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="62c65-125">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="62c65-126">Это может привести к тому, что время ожидания для всех узлов, находящихся ниже перехода OleTransactions, окажется больше, чем ожидалось.</span><span class="sxs-lookup"><span data-stu-id="62c65-126">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c65-127">См. также</span><span class="sxs-lookup"><span data-stu-id="62c65-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="62c65-128">Конфигурация транзакции ServiceModel</span><span class="sxs-lookup"><span data-stu-id="62c65-128">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="62c65-129">Включение потока транзакций</span><span class="sxs-lookup"><span data-stu-id="62c65-129">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="62c65-130">Привязки</span><span class="sxs-lookup"><span data-stu-id="62c65-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="62c65-131">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="62c65-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="62c65-132">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="62c65-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
