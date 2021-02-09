---
description: 'Подробнее о следующем: Практическое руководство. Запись сообщений в журнал (Visual Basic)'
title: Практическое руководство. Запись сообщений в журнал
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: ed455fdb2cebda908981514bef932942adf499ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797306"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="0743e-103">Практическое руководство. Запись сообщений в журнал (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0743e-103">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="0743e-104">Для записи в журнал информации о приложении можно использовать объекты `My.Application.Log` и `My.Log` .</span><span class="sxs-lookup"><span data-stu-id="0743e-104">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="0743e-105">В этом примере показано использование метода `My.Application.Log.WriteEntry` для записи в журнал данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="0743e-105">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="0743e-106">Для записи в журнал информации об исключениях используйте метод `My.Application.Log.WriteException`; см. раздел [Практическое руководство. Запись в журнал сведений об исключениях](how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="0743e-106">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="0743e-107">Пример</span><span class="sxs-lookup"><span data-stu-id="0743e-107">Example</span></span>

<span data-ttu-id="0743e-108">В этом примере используется метод `My.Application.Log.WriteEntry` для записи данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="0743e-108">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="0743e-109">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0743e-109">.NET Framework Security</span></span>

<span data-ttu-id="0743e-110">Убедитесь в том, что записываемые в журнал данные не включают конфиденциальных сведений, например паролей пользователей.</span><span class="sxs-lookup"><span data-stu-id="0743e-110">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="0743e-111">Дополнительные сведения см. в разделе [Работа с журналами приложения](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="0743e-111">For more information, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0743e-112">См. также</span><span class="sxs-lookup"><span data-stu-id="0743e-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="0743e-113">Работа с журналами приложения</span><span class="sxs-lookup"><span data-stu-id="0743e-113">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="0743e-114">Практическое руководство. Исплючения журналов</span><span class="sxs-lookup"><span data-stu-id="0743e-114">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="0743e-115">Пошаговое руководство. Определение места записи сведений для My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="0743e-115">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="0743e-116">Пошаговое руководство. Изменение места записи сведений для My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="0743e-116">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="0743e-117">Пошаговое руководство: Фильтрация вывода My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="0743e-117">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)
