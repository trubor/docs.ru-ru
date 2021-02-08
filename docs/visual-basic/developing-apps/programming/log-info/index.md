---
description: 'Узнайте подробнее о: Запись сведений в журнал из приложения (Visual Basic)'
title: Запись сведений в журнал из приложения
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 6e0adf45c12d98c8bc6d177d85accf9bee347f75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775075"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="86147-103">Запись сведений в журнал из приложения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86147-103">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="86147-104">Этот раздел содержит сведения о том, как регистрировать в журнале информацию из приложения с помощью объектов `My.Application.Log` или `My.Log` и как расширить возможности ведения журнала в приложении.</span><span class="sxs-lookup"><span data-stu-id="86147-104">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="86147-105">Объект `Log` предоставляет методы для записи информации в прослушиватели журнала приложения, а свойство `TraceSource` объекта `Log` предоставляет подробные сведения о конфигурации.</span><span class="sxs-lookup"><span data-stu-id="86147-105">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="86147-106">Объект `Log` настраивается в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="86147-106">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="86147-107">Объект `My.Log` доступен только для приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="86147-107">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="86147-108">Для клиентских приложений следует использовать объект `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="86147-108">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="86147-109">Для получения дополнительной информации см. <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="86147-109">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="86147-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="86147-110">Tasks</span></span>  
  
|<span data-ttu-id="86147-111">Кому</span><span class="sxs-lookup"><span data-stu-id="86147-111">To</span></span>|<span data-ttu-id="86147-112">См.</span><span class="sxs-lookup"><span data-stu-id="86147-112">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="86147-113">Запись информации о событиях в журналы приложения.</span><span class="sxs-lookup"><span data-stu-id="86147-113">Write event information to the application's logs.</span></span>|[<span data-ttu-id="86147-114">Практическое руководство. Запись сообщений в журнал</span><span class="sxs-lookup"><span data-stu-id="86147-114">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)|  
|<span data-ttu-id="86147-115">Запись информации об исключениях в журналы приложения.</span><span class="sxs-lookup"><span data-stu-id="86147-115">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="86147-116">Практическое руководство. Исплючения журналов</span><span class="sxs-lookup"><span data-stu-id="86147-116">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)|  
|<span data-ttu-id="86147-117">Запись данных трассировки в журналы приложения во время запуска и завершения работы приложения.</span><span class="sxs-lookup"><span data-stu-id="86147-117">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="86147-118">Практическое руководство. Запись в журнал сообщений при запуске и завершении приложения</span><span class="sxs-lookup"><span data-stu-id="86147-118">How to: Log Messages When the Application Starts or Shuts Down</span></span>](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="86147-119">Настройка объекта `My.Application.Log` для записи информации в текстовый файл.</span><span class="sxs-lookup"><span data-stu-id="86147-119">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="86147-120">Практическое руководство. Запись сведений о событиях в текстовый файл</span><span class="sxs-lookup"><span data-stu-id="86147-120">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="86147-121">Настройка объекта `My.Application.Log` для записи информации в журнал событий.</span><span class="sxs-lookup"><span data-stu-id="86147-121">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="86147-122">Практическое руководство. Запись в журнал событий приложения</span><span class="sxs-lookup"><span data-stu-id="86147-122">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="86147-123">Изменение места, в которое объект `My.Application.Log` записывает информацию.</span><span class="sxs-lookup"><span data-stu-id="86147-123">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="86147-124">Пошаговое руководство: Изменение места записи сведений для My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="86147-124">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="86147-125">Выбор места, в которое объект `My.Application.Log` записывает информацию.</span><span class="sxs-lookup"><span data-stu-id="86147-125">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="86147-126">Пошаговое руководство: Определение места записи сведений для My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="86147-126">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="86147-127">Создание пользовательского прослушивателя журнала для `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="86147-127">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="86147-128">Пошаговое руководство: Создание пользовательских прослушивателей журнала</span><span class="sxs-lookup"><span data-stu-id="86147-128">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="86147-129">Фильтрация выходных данных журналов `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="86147-129">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="86147-130">Пошаговое руководство: Фильтрация вывода My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="86147-130">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="86147-131">См. также</span><span class="sxs-lookup"><span data-stu-id="86147-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="86147-132">Работа с журналами приложения</span><span class="sxs-lookup"><span data-stu-id="86147-132">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="86147-133">Устранение неполадок. Прослушиватели журнала</span><span class="sxs-lookup"><span data-stu-id="86147-133">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
