---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 9235f1bcda7529b71aef542d3a49da08a9d4b59e
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592128"
---
<span data-ttu-id="4eac8-101">Небезопасные десериализаторы уязвимы при десериализации ненадежных данных.</span><span class="sxs-lookup"><span data-stu-id="4eac8-101">Insecure deserializers are vulnerable when deserializing untrusted data.</span></span> <span data-ttu-id="4eac8-102">Злоумышленник может изменить сериализованные данные и включить в них непредвиденные типы для внедрения объектов с вредоносными побочными эффектами.</span><span class="sxs-lookup"><span data-stu-id="4eac8-102">An attacker could modify the serialized data to include unexpected types to inject objects with malicious side effects.</span></span> <span data-ttu-id="4eac8-103">Атака против небезопасного десериализатора может, например, выполнять команды в базовой операционной системе, отсылать сообщения по сети или удалять файлы.</span><span class="sxs-lookup"><span data-stu-id="4eac8-103">An attack against an insecure deserializer could, for example, execute commands on the underlying operating system, communicate over the network, or delete files.</span></span>
