---
description: 'Дополнительные сведения о: использование контрактов в рабочем процессе'
title: Использование контрактов в рабочих процессах
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: d1ef5a4c494643d521a5fe045ff87c0cbeb34db1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632221"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="a7eef-103">Использование контрактов в рабочих процессах</span><span class="sxs-lookup"><span data-stu-id="a7eef-103">Using Contracts in Workflow</span></span>

<span data-ttu-id="a7eef-104">При реализации службы выполняется определение числа контрактов, описывающих службу и данные, которые она отправляет и получает.</span><span class="sxs-lookup"><span data-stu-id="a7eef-104">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="a7eef-105">Данные представлены в виде контрактов данных и контрактов сообщений. службы WCF и Workflow Services используют контракт данных и определения контрактов сообщений как часть описаний служб.</span><span class="sxs-lookup"><span data-stu-id="a7eef-105">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="a7eef-106">Служба сама предоставляет метаданные (в форме WSDL) для описания операций службы.</span><span class="sxs-lookup"><span data-stu-id="a7eef-106">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="a7eef-107">В WCF контракты службы и операций определяют службу и операции, которые она поддерживает.</span><span class="sxs-lookup"><span data-stu-id="a7eef-107">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="a7eef-108">Однако в службе Workflow Service эти контракты являются частью самого бизнес-процесса, они представляются в метаданных процессом, называемым выводом контракта.</span><span class="sxs-lookup"><span data-stu-id="a7eef-108">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="a7eef-109">Вывод контракта</span><span class="sxs-lookup"><span data-stu-id="a7eef-109">Contract Inference</span></span>  

 <span data-ttu-id="a7eef-110">При размещении службы рабочего процесса с использованием <xref:System.ServiceModel.Activities.WorkflowServiceHost> просматривается определение рабочего процесса и формируется контракт на основе набора действий по отправке и получению сообщений, обнаруженных в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="a7eef-110">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="a7eef-111">В частности, для создания контракта используются следующие действия и свойства:</span><span class="sxs-lookup"><span data-stu-id="a7eef-111">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="a7eef-112"><xref:System.ServiceModel.Activities.Receive> Действие</span><span class="sxs-lookup"><span data-stu-id="a7eef-112"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="a7eef-113"><xref:System.ServiceModel.Activities.SendReply> Действие</span><span class="sxs-lookup"><span data-stu-id="a7eef-113"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="a7eef-114"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Действие</span><span class="sxs-lookup"><span data-stu-id="a7eef-114"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="a7eef-115">Конечным результатом вывода контракта является описание службы, использующее структуры данных, аналогичные структурам данных служб WCF и контрактов операций.</span><span class="sxs-lookup"><span data-stu-id="a7eef-115">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="a7eef-116">Затем эти сведения используются для предоставления WSDL для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="a7eef-116">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7eef-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a7eef-117">See also</span></span>

- [<span data-ttu-id="a7eef-118">Службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="a7eef-118">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="a7eef-119">Действия обмена сообщениями</span><span class="sxs-lookup"><span data-stu-id="a7eef-119">Messaging Activities</span></span>](messaging-activities.md)
- [<span data-ttu-id="a7eef-120">Практическое руководство. Как создать службу рабочего процесса с помощью действий обмена сообщениями</span><span class="sxs-lookup"><span data-stu-id="a7eef-120">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="a7eef-121">Практическое руководство. Создание службы рабочих процессов, использующей существующий контракт службы</span><span class="sxs-lookup"><span data-stu-id="a7eef-121">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
