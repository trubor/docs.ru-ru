---
title: Группирование подключений
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
ms.openlocfilehash: 8bd4412a4c13dd490fce3118f59b5bb1f0d3ea85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250571"
---
# <a name="connection-grouping"></a><span data-ttu-id="d2b4f-102">Группирование подключений</span><span class="sxs-lookup"><span data-stu-id="d2b4f-102">Connection Grouping</span></span>

<span data-ttu-id="d2b4f-103">При группировании подключений отдельный запрос в одном приложении связывается с определенным пулом подключений.</span><span class="sxs-lookup"><span data-stu-id="d2b4f-103">Connection grouping associates specific requests within a single application to a defined connection pool.</span></span> <span data-ttu-id="d2b4f-104">Это может быть необходимо для приложения среднего уровня, которое подключается к внутреннему серверу от имени пользователя и использует протокол проверки подлинности с поддержкой делегирования (например, Kerberos), а также для приложения среднего уровня, которое предоставляет свои собственные учетные данные, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d2b4f-104">This can be required by a middle-tier application that connects to a back-end server on behalf of a user and uses an authentication protocol that supports delegation, such as Kerberos, or by a middle-tier application that supplies its own credentials, as in the example below.</span></span> <span data-ttu-id="d2b4f-105">Допустим, пользователь переходит на внутренний веб-сайт с информацией о его заработной плате.</span><span class="sxs-lookup"><span data-stu-id="d2b4f-105">For example, suppose a user, Joe, visits an internal Web site that displays his payroll information.</span></span> <span data-ttu-id="d2b4f-106">После проверки подлинности пользователя сервер приложения среднего уровня использует его учетные данные для подключения к внутреннему серверу и извлечение сведений о его заработной плате.</span><span class="sxs-lookup"><span data-stu-id="d2b4f-106">After authenticating Joe, the middle-tier application server uses Joe's credentials to connect to the back-end server to retrieve his payroll information.</span></span> <span data-ttu-id="d2b4f-107">Далее другой пользователь переходит на этот сайт и запрашивает сведения о своей зарплате.</span><span class="sxs-lookup"><span data-stu-id="d2b4f-107">Next, Susan visits the site and requests her payroll information.</span></span> <span data-ttu-id="d2b4f-108">Поскольку приложение среднего уровня уже установило подключение от имени первого пользователя, внутренний сервер в ответе возвращает именно его данные.</span><span class="sxs-lookup"><span data-stu-id="d2b4f-108">Because the middle-tier application has already made a connection using Joe's credentials, the back-end server responds with Joe's information.</span></span> <span data-ttu-id="d2b4f-109">Тем не менее, если приложение назначает каждый запрос, отправляемый на внутренний сервер, группе подключений, формируемой по имени пользователя, то каждый пользователь будет принадлежать отдельному пулу подключений и не сможет случайно использовать одни и те же сведения для проверки подлинности совместно с другим пользователем.</span><span class="sxs-lookup"><span data-stu-id="d2b4f-109">However, if the application assigns each request sent to the back-end server to a connection group formed from the user name, then each user belongs to a separate connection pool and cannot accidentally share authentication information with another user.</span></span>  
  
 <span data-ttu-id="d2b4f-110">Чтобы назначить запрос конкретной группе подключений, необходимо присвоить имя свойству <xref:System.Net.WebRequest.ConnectionGroupName%2A> для <xref:System.Net.WebRequest>, прежде чем выполнять запрос.</span><span class="sxs-lookup"><span data-stu-id="d2b4f-110">To assign a request to a specific connection group, you must assign a name to the <xref:System.Net.WebRequest.ConnectionGroupName%2A> property of your <xref:System.Net.WebRequest> before making the request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2b4f-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d2b4f-111">See also</span></span>

- [<span data-ttu-id="d2b4f-112">Управление подключениями</span><span class="sxs-lookup"><span data-stu-id="d2b4f-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="d2b4f-113">Практическое руководство. Присвоение данных пользователя групповым подключениям</span><span class="sxs-lookup"><span data-stu-id="d2b4f-113">How to: Assign User Information to Group Connections</span></span>](how-to-assign-user-information-to-group-connections.md)
