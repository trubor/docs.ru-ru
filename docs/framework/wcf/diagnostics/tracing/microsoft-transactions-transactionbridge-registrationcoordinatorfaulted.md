---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Регистратионкурдинаторфаултед'
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: aae2d5824f4205a05e98c7ef00d27c6a844e1566
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770603"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="e36ae-103">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="e36ae-103">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>

<span data-ttu-id="e36ae-104">Служба протокола WS-AT получила ошибку от своего координатора в ответ на сообщение о регистрации.</span><span class="sxs-lookup"><span data-stu-id="e36ae-104">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e36ae-105">Описание</span><span class="sxs-lookup"><span data-stu-id="e36ae-105">Description</span></span>  

 <span data-ttu-id="e36ae-106">Трассируется, если локальному диспетчеру TransactionManager не удается выполнить регистрацию в вышестоящем диспетчере TransactionManager из-за того, что возвращена ошибка.</span><span class="sxs-lookup"><span data-stu-id="e36ae-106">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e36ae-107">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="e36ae-107">Troubleshooting</span></span>  

 <span data-ttu-id="e36ae-108">Проверьте возвращаемую ошибку в сообщении трассировки.</span><span class="sxs-lookup"><span data-stu-id="e36ae-108">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36ae-109">См. также</span><span class="sxs-lookup"><span data-stu-id="e36ae-109">See also</span></span>

- [<span data-ttu-id="e36ae-110">Трассировка</span><span class="sxs-lookup"><span data-stu-id="e36ae-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="e36ae-111">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="e36ae-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e36ae-112">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="e36ae-112">Administration and Diagnostics</span></span>](../index.md)
