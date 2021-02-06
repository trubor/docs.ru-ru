---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Енлисттрансактионфаилуре'
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: f0645d0f7bfc2787f4bce254ea8d6e3143dc0406
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644610"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="b36f4-103">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="b36f4-103">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>

<span data-ttu-id="b36f4-104">Службе протокола WS-AT не удалось включить в список транзакцию, используя предоставленный контекст координации.</span><span class="sxs-lookup"><span data-stu-id="b36f4-104">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b36f4-105">Описание</span><span class="sxs-lookup"><span data-stu-id="b36f4-105">Description</span></span>  

 <span data-ttu-id="b36f4-106">Регистрируется, если координатору MSDTC не удалось включить в список транзакцию для заданного протокола 2pc.</span><span class="sxs-lookup"><span data-stu-id="b36f4-106">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="b36f4-107">Это может произойти, если транзакция больше не существует, включение в список уже запрещено или если уже имеется слишком много перечислений.</span><span class="sxs-lookup"><span data-stu-id="b36f4-107">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b36f4-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="b36f4-108">Troubleshooting</span></span>  

 <span data-ttu-id="b36f4-109">Проверьте строку состояния в сообщении трассировки и определите, имеются ли элементы, с которыми можно произвести какие-либо действия.</span><span class="sxs-lookup"><span data-stu-id="b36f4-109">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b36f4-110">См. также</span><span class="sxs-lookup"><span data-stu-id="b36f4-110">See also</span></span>

- [<span data-ttu-id="b36f4-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="b36f4-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="b36f4-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="b36f4-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b36f4-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="b36f4-113">Administration and Diagnostics</span></span>](../index.md)
