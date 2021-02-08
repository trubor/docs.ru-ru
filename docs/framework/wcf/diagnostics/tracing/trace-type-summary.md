---
description: Дополнительные сведения о типе трассировки "Сводка"
title: Сводка типов трассировок
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: ebfe9de16766494a6aebe0a8d2501954855dc4df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803221"
---
# <a name="trace-type-summary"></a><span data-ttu-id="193c3-103">Сводка типов трассировок</span><span class="sxs-lookup"><span data-stu-id="193c3-103">Trace Type Summary</span></span>

<span data-ttu-id="193c3-104">[Уровни источника](xref:System.Diagnostics.SourceLevels) определяют различные уровни трассировки: критическая, ошибка, предупреждение, информация и подробный, а также описание `ActivityTracing` флага, который переключает выходные данные границ трассировки и событий перемещения действий.</span><span class="sxs-lookup"><span data-stu-id="193c3-104">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="193c3-105">Также можно просматривать <xref:System.Diagnostics.TraceEventType> типы трассировок, которые могут быть выпущены из <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="193c3-105">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="193c3-106">В следующей таблице перечислены наиболее важные из них.</span><span class="sxs-lookup"><span data-stu-id="193c3-106">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="193c3-107">Тип трассировки</span><span class="sxs-lookup"><span data-stu-id="193c3-107">Trace Type</span></span>|<span data-ttu-id="193c3-108">Описание</span><span class="sxs-lookup"><span data-stu-id="193c3-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="193c3-109">Критический</span><span class="sxs-lookup"><span data-stu-id="193c3-109">Critical</span></span>|<span data-ttu-id="193c3-110">Неустранимая ошибка или сбой в работе приложения.</span><span class="sxs-lookup"><span data-stu-id="193c3-110">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="193c3-111">Ошибка</span><span class="sxs-lookup"><span data-stu-id="193c3-111">Error</span></span>|<span data-ttu-id="193c3-112">Устранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="193c3-112">Recoverable error.</span></span>|  
|<span data-ttu-id="193c3-113">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="193c3-113">Warning</span></span>|<span data-ttu-id="193c3-114">Информационное сообщение.</span><span class="sxs-lookup"><span data-stu-id="193c3-114">Informational message.</span></span>|  
|<span data-ttu-id="193c3-115">Сведения</span><span class="sxs-lookup"><span data-stu-id="193c3-115">Information</span></span>|<span data-ttu-id="193c3-116">Некритическая проблема.</span><span class="sxs-lookup"><span data-stu-id="193c3-116">Non-critical problem.</span></span>|  
|<span data-ttu-id="193c3-117">Подробный</span><span class="sxs-lookup"><span data-stu-id="193c3-117">Verbose</span></span>|<span data-ttu-id="193c3-118">Трассировка отладки.</span><span class="sxs-lookup"><span data-stu-id="193c3-118">Debugging trace.</span></span>|  
|<span data-ttu-id="193c3-119">Начало</span><span class="sxs-lookup"><span data-stu-id="193c3-119">Start</span></span>|<span data-ttu-id="193c3-120">Начало логического блока обработки.</span><span class="sxs-lookup"><span data-stu-id="193c3-120">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="193c3-121">Приостановить</span><span class="sxs-lookup"><span data-stu-id="193c3-121">Suspend</span></span>|<span data-ttu-id="193c3-122">Приостановка логического блока обработки. </span><span class="sxs-lookup"><span data-stu-id="193c3-122">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="193c3-123">Возобновить</span><span class="sxs-lookup"><span data-stu-id="193c3-123">Resume</span></span>|<span data-ttu-id="193c3-124">Возобновление логического блока обработки. </span><span class="sxs-lookup"><span data-stu-id="193c3-124">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="193c3-125">Стоп</span><span class="sxs-lookup"><span data-stu-id="193c3-125">Stop</span></span>|<span data-ttu-id="193c3-126">Остановка логического блока обработки. </span><span class="sxs-lookup"><span data-stu-id="193c3-126">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="193c3-127">Перенос</span><span class="sxs-lookup"><span data-stu-id="193c3-127">Transfer</span></span>|<span data-ttu-id="193c3-128">Изменение идентификации взаимосвязей.</span><span class="sxs-lookup"><span data-stu-id="193c3-128">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="193c3-129">Действие определяется как сочетание перечисленных выше типов трассировок.</span><span class="sxs-lookup"><span data-stu-id="193c3-129">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="193c3-130">Ниже приведено регулярное выражение, определяющее идеальное действие в локальной области (области источника трассировки):</span><span class="sxs-lookup"><span data-stu-id="193c3-130">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="193c3-131">Это означает, что действие должно удовлетворять следующим условиям.</span><span class="sxs-lookup"><span data-stu-id="193c3-131">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="193c3-132">Должно запускаться и останавливаться трассировками Start и Stop соответственно.</span><span class="sxs-lookup"><span data-stu-id="193c3-132">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="193c3-133">Трассировка Transfer должна непосредственно предшествовать трассировке Suspend или Resume.</span><span class="sxs-lookup"><span data-stu-id="193c3-133">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="193c3-134">Не должно содержать никаких трассировок между трассировками Suspend и Resume, если такие трассировки имеются.</span><span class="sxs-lookup"><span data-stu-id="193c3-134">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="193c3-135">Может содержать любые и в любом количестве трассировки уровня Critical/Error/Warning/Information/Verbose/Transfer при условии соблюдения предыдущих условий.</span><span class="sxs-lookup"><span data-stu-id="193c3-135">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="193c3-136">Ниже приведено регулярное выражение, определяющее идеальное действие в глобальной области,</span><span class="sxs-lookup"><span data-stu-id="193c3-136">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="193c3-137">где R - регулярное выражение для действия в локальной области.</span><span class="sxs-lookup"><span data-stu-id="193c3-137">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="193c3-138">Таким образом, получаем:</span><span class="sxs-lookup"><span data-stu-id="193c3-138">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
