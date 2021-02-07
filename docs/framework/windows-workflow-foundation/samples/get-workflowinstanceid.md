---
description: 'Дополнительные сведения о: Get WorkflowInstanceId'
title: Получение GetWorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 3be6c36e6a6996a11ad1e26414fa25f1e32399e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755321"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="7e7ef-103">Получение GetWorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="7e7ef-103">Get WorkflowInstanceId</span></span>

<span data-ttu-id="7e7ef-104">В этом образце показывается, как можно использовать пользовательское действие `GetWorkflowInstanceId` для возвращения идентификатора экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-104">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7e7ef-105">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="7e7ef-105">Demonstrates</span></span>  

 <span data-ttu-id="7e7ef-106">Разработка пользовательского действия, метод доступа к экземпляру рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-106">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7e7ef-107">Разговор</span><span class="sxs-lookup"><span data-stu-id="7e7ef-107">Discussion</span></span>  

 <span data-ttu-id="7e7ef-108">Для получения идентификатора экземпляра выполняющегося рабочего процесса необходимо написать код.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-108">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="7e7ef-109">Если необходимо написать полностью декларативный рабочий процесс, то требуется действие, возвращающее идентификатор экземпляра рабочего процесса, что позволит ссылаться на это действие в рабочем процессе в полностью декларативной манере.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-109">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="7e7ef-110">Доступ к идентификатору экземпляра требуется во многих случаях, например при ведении журнала с целью аудита или при осуществлении корреляции на уровне приложения с предоставлением идентификатора экземпляра клиенту для последующего создания ассоциации (например, при использовании этого действия в действии SendReply).</span><span class="sxs-lookup"><span data-stu-id="7e7ef-110">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="7e7ef-111">Действие `GetWorkflowInstanceId` реализуется как <xref:System.Activities.CodeActivity%601>, поскольку оно должно возвращать значение типа <xref:System.Guid> и должно иметь доступ к контексту <xref:System.Activities.CodeActivityContext> для получения идентификатора экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-111">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="7e7ef-112">Его реализация производится достаточно просто.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-112">Its implementation is fairly basic.</span></span>  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> <span data-ttu-id="7e7ef-113">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e7ef-114">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="7e7ef-114">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7e7ef-115">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e7ef-116">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="7e7ef-116">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
