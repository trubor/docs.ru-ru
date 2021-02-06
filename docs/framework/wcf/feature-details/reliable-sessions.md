---
description: Дополнительные сведения о надежных сеансах
title: Надежные сеансы
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 86df4ccf9c1fd52d162ad7272ece5591f0ca7482
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632884"
---
# <a name="reliable-sessions"></a><span data-ttu-id="cb158-103">Надежные сеансы</span><span class="sxs-lookup"><span data-stu-id="cb158-103">Reliable Sessions</span></span>

<span data-ttu-id="cb158-104">В этом разделе описывается, что такое надежный сеанс Windows Communication Foundation (WCF), что он использует, как и когда использовать его, какие конфигурации привязки поддерживаются, а также указатели на рекомендации.</span><span class="sxs-lookup"><span data-stu-id="cb158-104">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="cb158-105">В следующей таблице собраны сведения о ключевых вопросах и связанных разделах.</span><span class="sxs-lookup"><span data-stu-id="cb158-105">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="cb158-106">WCF надежного сеанса предоставляет функции, гарантирующие передачу сообщений между конечными точками через протоколы SOAP или транспортные посредники и доставляемые только один раз и, при необходимости, в том же порядке, в котором они были отправлены.</span><span class="sxs-lookup"><span data-stu-id="cb158-106">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="cb158-107">Чтобы использовать надежный сеанс с приложением WCF, либо используйте одну из предоставляемых системой привязок в WCF, которая поддерживает надежный сеанс по умолчанию или как вариант, либо создайте собственную настраиваемую привязку, которая поддерживает этот сеанс.</span><span class="sxs-lookup"><span data-stu-id="cb158-107">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cb158-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="cb158-108">In This Section</span></span>

<span data-ttu-id="cb158-109">[Обзор надежных сеансов](reliable-sessions-overview.md) Описывает надежные сеансы, когда их использовать, различные привязки, которые поддерживают надежные сеансы и как они работают.</span><span class="sxs-lookup"><span data-stu-id="cb158-109">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="cb158-110">[Как обмениваться сообщениями в надежном сеансе](how-to-exchange-messages-within-a-reliable-session.md) Описывает, как создать надежный сеанс по протоколу HTTP с помощью пользовательской привязки, заданной в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="cb158-110">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="cb158-111">[Как защитить сообщения в надежных сеансах](how-to-secure-messages-within-reliable-sessions.md) Описывает, как защитить надежный сеанс.</span><span class="sxs-lookup"><span data-stu-id="cb158-111">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="cb158-112">[Как создать настраиваемую привязку надежного сеанса с помощью HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Описывает, как создать надежный сеанс по протоколу HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cb158-112">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="cb158-113">Рекомендации [по надежным сеансам](best-practices-for-reliable-sessions.md) Описывает некоторые рекомендации, связанные с использованием надежного сеанса.</span><span class="sxs-lookup"><span data-stu-id="cb158-113">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="cb158-114">Справочник</span><span class="sxs-lookup"><span data-stu-id="cb158-114">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="cb158-115">См. также</span><span class="sxs-lookup"><span data-stu-id="cb158-115">See also</span></span>

- [<span data-ttu-id="cb158-116">Очереди и надежные сеансы</span><span class="sxs-lookup"><span data-stu-id="cb158-116">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="cb158-117">Сеансы, экземпляры и параллелизм</span><span class="sxs-lookup"><span data-stu-id="cb158-117">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
