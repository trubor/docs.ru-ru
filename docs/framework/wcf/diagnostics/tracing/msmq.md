---
description: 'Дополнительные сведения: MSMQ'
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 3d694fdab202cd2b3b03c377f72d93c22cbae263
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720583"
---
# <a name="msmq"></a><span data-ttu-id="8a231-103">MSMQ</span><span class="sxs-lookup"><span data-stu-id="8a231-103">MSMQ</span></span>

<span data-ttu-id="8a231-104">В приложениях MSMQ никакие дополнительные действия не передаются из очереди канала в MSMQ и обратно.</span><span class="sxs-lookup"><span data-stu-id="8a231-104">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="8a231-105">Кроме того, в рамках трассировки очереди канала во время операции Send отслеживаются идентификатор сообщения MSMQ, идентификатор сообщения SOAP (а также идентификатор действия, если он существует).</span><span class="sxs-lookup"><span data-stu-id="8a231-105">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="8a231-106">Идентификатор сообщения MSMQ, идентификатор сообщения SOAP (а также идентификатор действия, если он существует) отслеживаются в рамках трассировки очереди канала во время операции Receive.</span><span class="sxs-lookup"><span data-stu-id="8a231-106">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="8a231-107">Необходимые передачи для операции получения выполняются аналогично любому другому транспортному потоку (Receive Bytes->Process > операции).</span><span class="sxs-lookup"><span data-stu-id="8a231-107">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
