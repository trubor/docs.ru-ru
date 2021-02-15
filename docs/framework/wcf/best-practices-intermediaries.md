---
description: 'Дополнительные сведения: рекомендации: посредники'
title: Рекомендации. Посредники
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 54fd367c9dd7a3b40f585d095d51042acd8b5722
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430499"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="e110b-103">Рекомендации. Посредники</span><span class="sxs-lookup"><span data-stu-id="e110b-103">Best Practices: Intermediaries</span></span>

<span data-ttu-id="e110b-104">Следует уделять особое внимание к ошибкам при вызове посредников, чтобы убедиться, что каналы на стороне службы посредника закрыты правильно.</span><span class="sxs-lookup"><span data-stu-id="e110b-104">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="e110b-105">Рассмотрим следующий сценарий.</span><span class="sxs-lookup"><span data-stu-id="e110b-105">Consider the following scenario.</span></span> <span data-ttu-id="e110b-106">Клиент вызывает метод в посреднике, который затем вызывает внутреннюю службу.</span><span class="sxs-lookup"><span data-stu-id="e110b-106">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="e110b-107">Внутренняя служба не определяет контракт ошибок, поэтому любая ошибка данной службы будет обрабатываться как нетипизированная ошибка.</span><span class="sxs-lookup"><span data-stu-id="e110b-107">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="e110b-108">Служба серверной части создает исключение, <xref:System.ApplicationException> и WCF правильно прерывает канал на стороне службы.</span><span class="sxs-lookup"><span data-stu-id="e110b-108">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="e110b-109">Затем <xref:System.ApplicationException> появляется как <xref:System.ServiceModel.FaultException>, которое пробрасывается дальше к посреднику.</span><span class="sxs-lookup"><span data-stu-id="e110b-109">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="e110b-110">Посредник повторно пробрасывает <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="e110b-110">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="e110b-111">WCF интерпретирует ее как нетипизированную ошибку из посредника и перенаправляет ее клиенту.</span><span class="sxs-lookup"><span data-stu-id="e110b-111">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="e110b-112">При получении ошибки и посредник и клиент закрывают каналы на своей стороне.</span><span class="sxs-lookup"><span data-stu-id="e110b-112">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="e110b-113">Канал на стороне службы посредника при этом остается открытым, поскольку WCF не знает, является ли ошибка неустранимой.</span><span class="sxs-lookup"><span data-stu-id="e110b-113">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="e110b-114">В этом случае рекомендуется определять, является ли ошибка от службы неустранимой, и, если да, посредник должен вызвать сбой канала на стороне службы, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="e110b-114">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e110b-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e110b-115">See also</span></span>

- [<span data-ttu-id="e110b-116">Обработка ошибок WCF</span><span class="sxs-lookup"><span data-stu-id="e110b-116">WCF Error Handling</span></span>](wcf-error-handling.md)
- [<span data-ttu-id="e110b-117">Задание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="e110b-117">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
