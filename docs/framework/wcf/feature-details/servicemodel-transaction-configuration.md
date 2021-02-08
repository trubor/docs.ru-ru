---
description: Дополнительные сведения о конфигурации транзакций ServiceModel
title: Конфигурация транзакции ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 260e3cbe94ce0d22887554705134eef72a031981
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793471"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="d172d-103">Конфигурация транзакции ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d172d-103">ServiceModel Transaction Configuration</span></span>

<span data-ttu-id="d172d-104">Windows Communication Foundation (WCF) предоставляет три атрибута для настройки транзакций для службы: `transactionFlow` , `transactionProtocol` и `transactionTimeout` .</span><span class="sxs-lookup"><span data-stu-id="d172d-104">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="d172d-105">Настройка атрибута transactionFlow</span><span class="sxs-lookup"><span data-stu-id="d172d-105">Configuring transactionFlow</span></span>  

 <span data-ttu-id="d172d-106">Большинство предопределенных привязок WCF предоставляет `transactionFlow` `transactionProtocol` атрибуты и, чтобы можно было настроить привязку для приема входящих транзакций для определенной конечной точки с помощью определенного протокола потока транзакций.</span><span class="sxs-lookup"><span data-stu-id="d172d-106">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="d172d-107">Кроме того, вы можете использовать элемент `transactionFlow` и его атрибут `transactionProtocol` для сборки вашей собственной пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="d172d-107">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="d172d-108">Дополнительные сведения о настройке элементов конфигурации см. в разделе [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) и [Схема конфигурации WCF](../../configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="d172d-108">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="d172d-109">Атрибут `transactionFlow` задает, разрешен ли поток транзакций для конечных точек службы, использующих данную привязку.</span><span class="sxs-lookup"><span data-stu-id="d172d-109">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="d172d-110">Настройка атрибута transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="d172d-110">Configuring transactionProtocol</span></span>  

 <span data-ttu-id="d172d-111">Атрибут `transactionProtocol` задает протокол транзакций, который должен использоваться конечными точками, использующими данную привязку.</span><span class="sxs-lookup"><span data-stu-id="d172d-111">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="d172d-112">Ниже приведен пример раздела конфигурации, настраивающий указанную привязку для поддержки потока транзакций, а также для использования протокола WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="d172d-112">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="d172d-113">Настройка атрибута transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="d172d-113">Configuring transactionTimeout</span></span>  

 <span data-ttu-id="d172d-114">`transactionTimeout`Атрибут для службы WCF можно настроить в `behavior` элементе файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d172d-114">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="d172d-115">В следующем коде показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="d172d-115">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d172d-116">Атрибут `transactionTimeout` задает период времени, в течение которого созданная в службе новая транзакция должна быть завершена.</span><span class="sxs-lookup"><span data-stu-id="d172d-116">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="d172d-117">Он используется в качестве времени ожидания <xref:System.Transactions.TransactionScope> для любой операции, устанавливающей новую транзакцию; если применен атрибут <xref:System.ServiceModel.OperationBehaviorAttribute>, для свойства <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> устанавливается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="d172d-117">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="d172d-118">Время ожидания задает промежуток времени от создания транзакции до завершения фазы 1 в протоколе двухфазной фиксации.</span><span class="sxs-lookup"><span data-stu-id="d172d-118">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="d172d-119">Если этот атрибут задан в разделе конфигурации `service`, необходимо применить по меньшей мере один метод соответствующей службы с атрибутом <xref:System.ServiceModel.OperationBehaviorAttribute>, в котором для свойства <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> задано значение `true`.</span><span class="sxs-lookup"><span data-stu-id="d172d-119">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="d172d-120">Обратите внимание, что для времени ожидания всегда используется меньшее из значений этого параметра конфигурации `transactionTimeout` и любого из свойств <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="d172d-120">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d172d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d172d-121">See also</span></span>

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="d172d-122">Схема конфигурации WCF</span><span class="sxs-lookup"><span data-stu-id="d172d-122">WCF Configuration Schema</span></span>](../../configure-apps/file-schema/wcf/index.md)
