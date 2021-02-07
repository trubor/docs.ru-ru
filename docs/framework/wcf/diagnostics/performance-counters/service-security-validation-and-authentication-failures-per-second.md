---
description: 'Дополнительные сведения: служба: Проверка безопасности и ошибки проверки подлинности за секунду'
title: 'Служба: количество сбоев при проверке безопасности и проверке подлинности в секунду'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 8c0baedab3335031ed1737e0e4cecff7febc2944
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759527"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="495c7-103">Служба: количество сбоев при проверке безопасности и проверке подлинности в секунду</span><span class="sxs-lookup"><span data-stu-id="495c7-103">Service: Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="495c7-104">Имя счетчика: Security Validation and Authentication Failures Per Second.</span><span class="sxs-lookup"><span data-stu-id="495c7-104">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="495c7-105">Описание</span><span class="sxs-lookup"><span data-stu-id="495c7-105">Description</span></span>  

 <span data-ttu-id="495c7-106">Значение этого счетчика увеличивается всякий раз, когда сообщение отклоняется из-за проблемы безопасности, не относящейся к счетчику "Security Calls Not Authorized".</span><span class="sxs-lookup"><span data-stu-id="495c7-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="495c7-107">К таким проблемам относятся следующие.</span><span class="sxs-lookup"><span data-stu-id="495c7-107">Such problems include:</span></span>  
  
- <span data-ttu-id="495c7-108">Невозможно прочесть в этом сообщении маркер клиента.</span><span class="sxs-lookup"><span data-stu-id="495c7-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="495c7-109">Маркер клиента не прошел проверку подлинности (например, неправильный пароль).</span><span class="sxs-lookup"><span data-stu-id="495c7-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="495c7-110">Сбой при проверке подписи (например, сообщение было искажено).</span><span class="sxs-lookup"><span data-stu-id="495c7-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="495c7-111">Сообщение является копией предыдущего, что может свидетельствовать об атаке воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="495c7-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="495c7-112">Произошел сбой при расшифровке.</span><span class="sxs-lookup"><span data-stu-id="495c7-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="495c7-113">В сообщении отсутствуют некоторые обязательные элементы (например, отсутствует отметка времени или зашифрованный блок данных).</span><span class="sxs-lookup"><span data-stu-id="495c7-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="495c7-114">Во время подтверждения TLSNEGO/SPNEGO произошли ошибки.</span><span class="sxs-lookup"><span data-stu-id="495c7-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="495c7-115">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется по следующей формуле:</span><span class="sxs-lookup"><span data-stu-id="495c7-115">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="495c7-116">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="495c7-116">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
