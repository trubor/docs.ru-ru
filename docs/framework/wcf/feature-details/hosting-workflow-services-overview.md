---
description: См. Дополнительные сведения о размещении служб рабочих процессов
title: Общие сведения о размещении служб рабочих процессов
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: e183dfd7428c11cf20e731ab4a9975a7388b6f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743087"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="90f56-103">Общие сведения о размещении служб рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="90f56-103">Hosting Workflow Services Overview</span></span>

<span data-ttu-id="90f56-104">Для выполнения служб рабочего процесса они должны быть размещены.</span><span class="sxs-lookup"><span data-stu-id="90f56-104">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="90f56-105">Класс <xref:System.ServiceModel.WorkflowServiceHost> представляет собой готовый узел размещения рабочих процессов, поддерживающий использование нескольких экземпляров, настройку и обмен сообщениями WCF (хотя от размещаемых рабочих процессов и не требуется обмена сообщениями).</span><span class="sxs-lookup"><span data-stu-id="90f56-105">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="90f56-106">Он также реализует сохраняемость, отслеживание и контроль за экземплярами через набор поведений службы.</span><span class="sxs-lookup"><span data-stu-id="90f56-106">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="90f56-107">Как и класс WCF <xref:System.ServiceModel.ServiceHost>, класс <xref:System.ServiceModel.WorkflowServiceHost> может быть резидентным в любом управляемом приложении .NET или размещаться на веб-сервере IIS / WAS (в виде файла XAMLX).</span><span class="sxs-lookup"><span data-stu-id="90f56-107">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="90f56-108">В этом разделе описано размещение службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="90f56-108">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90f56-109">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="90f56-109">In This Section</span></span>  

 [<span data-ttu-id="90f56-110">Размещение службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="90f56-110">Hosting Workflow Services</span></span>](hosting-workflow-services.md)  
 <span data-ttu-id="90f56-111">Описывает размещение служб рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="90f56-111">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="90f56-112">Внутренние особенности размещения службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="90f56-112">Workflow Service Host Internals</span></span>](workflow-service-host-internals.md)  
 <span data-ttu-id="90f56-113">Описывает, как объект <xref:System.ServiceModel.WorkflowServiceHost> обрабатывает входящие сообщения.</span><span class="sxs-lookup"><span data-stu-id="90f56-113">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="90f56-114">Расширяемость узла службы рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="90f56-114">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)  
 <span data-ttu-id="90f56-115">Описывает способы расширения функциональности узла службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="90f56-115">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="90f56-116">Конечная точка элемента управления рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="90f56-116">Workflow Control Endpoint</span></span>](workflow-control-endpoint.md)  
 <span data-ttu-id="90f56-117">Описывает, как определить конечную точку, позволяющую создавать экземпляры рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="90f56-117">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="90f56-118">Практическое руководство. Как разместить службу рабочего процесса с помощью Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="90f56-118">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="90f56-119">Демонстрирует размещение существующей службы рабочего процесса в фабрике приложений Windows Server.</span><span class="sxs-lookup"><span data-stu-id="90f56-119">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="90f56-120">Настройка WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="90f56-120">Configuring WorkflowServiceHost</span></span>](configuring-workflowservicehost.md)  
 <span data-ttu-id="90f56-121">Описывает управление сохраняемостью, отслеживанием, простоем и поведением необработанных исключений.</span><span class="sxs-lookup"><span data-stu-id="90f56-121">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="90f56-122">Справочник</span><span class="sxs-lookup"><span data-stu-id="90f56-122">Reference</span></span>  

 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="90f56-123">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="90f56-123">Related Sections</span></span>  

 [<span data-ttu-id="90f56-124">Службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="90f56-124">Workflow Services</span></span>](workflow-services.md)
