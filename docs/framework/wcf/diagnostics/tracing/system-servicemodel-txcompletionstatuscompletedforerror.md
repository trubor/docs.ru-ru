---
description: 'Дополнительные сведения: System. ServiceModel. Ткскомплетионстатускомплетедфореррор'
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 83cd5c258b3a60f69cc94426aed7ccc1d27f6013
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735612"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="0be50-103">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="0be50-103">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>

<span data-ttu-id="0be50-104">Заданная транзакция для заданной операции завершена в результате необработанного исключения при выполнении.</span><span class="sxs-lookup"><span data-stu-id="0be50-104">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0be50-105">Описание</span><span class="sxs-lookup"><span data-stu-id="0be50-105">Description</span></span>  

 <span data-ttu-id="0be50-106">Трассируется, если при попытке завершить текущую транзакцию возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="0be50-106">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="0be50-107">Это происходит до того, как вызвавшему объекту отправляется ответ или ошибка.</span><span class="sxs-lookup"><span data-stu-id="0be50-107">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0be50-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="0be50-108">Troubleshooting</span></span>  

 <span data-ttu-id="0be50-109">Проверьте трассируемое сообщение на предмет наличия сообщения об исключении и других элементов, с которыми можно произвести какие-либо действия.</span><span class="sxs-lookup"><span data-stu-id="0be50-109">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0be50-110">См. также</span><span class="sxs-lookup"><span data-stu-id="0be50-110">See also</span></span>

- [<span data-ttu-id="0be50-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="0be50-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="0be50-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="0be50-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0be50-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="0be50-113">Administration and Diagnostics</span></span>](../index.md)
