---
description: 'Дополнительные сведения о: Microsoft. Transactions. Трансактионбридже. Креатетрансактионфаилуре'
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 6b4a071b617de475b51ec50178e5205fa2e524d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803312"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="6ebdc-103">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="6ebdc-103">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>

<span data-ttu-id="6ebdc-104">Невозможно создать транзакцию.</span><span class="sxs-lookup"><span data-stu-id="6ebdc-104">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6ebdc-105">Описание</span><span class="sxs-lookup"><span data-stu-id="6ebdc-105">Description</span></span>  

 <span data-ttu-id="6ebdc-106">Данная трассировка создается, если MSDTC не может создать транзакцию.</span><span class="sxs-lookup"><span data-stu-id="6ebdc-106">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="6ebdc-107">Это может быть вызвано недостаточным объемом ресурсов, отсутствием места в журнале или другими ошибками.</span><span class="sxs-lookup"><span data-stu-id="6ebdc-107">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6ebdc-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="6ebdc-108">Troubleshooting</span></span>  

 <span data-ttu-id="6ebdc-109">Проверьте строку состояния в сообщении трассировки и определите, имеются ли элементы, с которыми можно произвести какие-либо действия.</span><span class="sxs-lookup"><span data-stu-id="6ebdc-109">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebdc-110">См. также</span><span class="sxs-lookup"><span data-stu-id="6ebdc-110">See also</span></span>

- [<span data-ttu-id="6ebdc-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="6ebdc-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="6ebdc-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="6ebdc-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6ebdc-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="6ebdc-113">Administration and Diagnostics</span></span>](../index.md)
