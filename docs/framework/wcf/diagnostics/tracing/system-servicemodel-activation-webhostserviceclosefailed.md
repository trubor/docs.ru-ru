---
description: 'Дополнительные сведения: System. ServiceModel. Activation. Вебхостсервицеклосефаилед'
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: fae41b72e2eb9aba76993081769afc42c0ec8975
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720453"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="a264f-103">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="a264f-103">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>

<span data-ttu-id="a264f-104">Возникает при невозможности правильного закрытия службы или при прерывании службы.</span><span class="sxs-lookup"><span data-stu-id="a264f-104">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a264f-105">Описание</span><span class="sxs-lookup"><span data-stu-id="a264f-105">Description</span></span>  

 <span data-ttu-id="a264f-106">Данный код ошибки отображается только в файле журнала.</span><span class="sxs-lookup"><span data-stu-id="a264f-106">This error code only appears in the log file.</span></span> <span data-ttu-id="a264f-107">Как правило, он указывает на наличие программной ошибки, например при попытке закрыть службу после того, как был вызван метод Abort.</span><span class="sxs-lookup"><span data-stu-id="a264f-107">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a264f-108">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="a264f-108">Troubleshooting</span></span>  

 <span data-ttu-id="a264f-109">Проверьте исходный код приложения.</span><span class="sxs-lookup"><span data-stu-id="a264f-109">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a264f-110">См. также</span><span class="sxs-lookup"><span data-stu-id="a264f-110">See also</span></span>

- [<span data-ttu-id="a264f-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="a264f-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="a264f-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="a264f-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a264f-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="a264f-113">Administration and Diagnostics</span></span>](../index.md)
