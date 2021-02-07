---
description: Дополнительные сведения см. в статье обработка ошибок в асинхронных действиях
title: Ошибка при обработке асинхронных действий
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: df223998737259aca01a4dc18ed9f2a911d80366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742411"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="3a36f-103">Ошибка при обработке асинхронных действий</span><span class="sxs-lookup"><span data-stu-id="3a36f-103">Error handling in asynchronous activities</span></span>

<span data-ttu-id="3a36f-104">Обеспечение обработки ошибок в <xref:System.Activities.AsyncCodeActivity> включает маршрутизацию ошибки в системе обратного вызова действия.</span><span class="sxs-lookup"><span data-stu-id="3a36f-104">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="3a36f-105">В этом разделе описывается, как возвратить ошибку, вызванную в асинхронной операции, обратно в узел, используя образец действия SendMail.</span><span class="sxs-lookup"><span data-stu-id="3a36f-105">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="3a36f-106">Возвращение ошибки, вызванной в асинхронном действии, обратно на узел</span><span class="sxs-lookup"><span data-stu-id="3a36f-106">Returning an error thrown in an asynchronous activity back to the host</span></span>  

 <span data-ttu-id="3a36f-107">Маршрутизация ошибки в асинхронной операции обратно на узел в образце действия SendMail включает следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="3a36f-107">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="3a36f-108">Добавьте свойство Exception к классу `SendMailAsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="3a36f-108">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="3a36f-109">Скопируйте вызванную ошибку в это свойство в обработчике событий `SendCompleted`.</span><span class="sxs-lookup"><span data-stu-id="3a36f-109">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="3a36f-110">Создайте исключение в обработчике событий `EndExecute`.</span><span class="sxs-lookup"><span data-stu-id="3a36f-110">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="3a36f-111">Ниже приведен конечный код.</span><span class="sxs-lookup"><span data-stu-id="3a36f-111">The resulting code is as follows.</span></span>  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;
        }  
    }  
```
