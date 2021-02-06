---
description: 'Дополнительные сведения: конечная точка: Проверка безопасности и ошибки проверки подлинности'
title: 'Конечная точка: количество сбоев при проверке безопасности и проверке подлинности'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9131eebcf85032c591ebf7f65e2b0e5f67ec60df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655426"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="a58ed-103">Конечная точка: количество сбоев при проверке безопасности и проверке подлинности</span><span class="sxs-lookup"><span data-stu-id="a58ed-103">Endpoint: Security Validation and Authentication Failures</span></span>

<span data-ttu-id="a58ed-104">Имя счетчика: Security Validation and Authentication Failures</span><span class="sxs-lookup"><span data-stu-id="a58ed-104">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="a58ed-105">Описание</span><span class="sxs-lookup"><span data-stu-id="a58ed-105">Description</span></span>  

 <span data-ttu-id="a58ed-106">Значение этого счетчика увеличивается всякий раз, когда сообщение отклоняется из-за проблемы безопасности, не относящейся к счетчику "Security Calls Not Authorized".</span><span class="sxs-lookup"><span data-stu-id="a58ed-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="a58ed-107">К таким проблемам относятся следующие.</span><span class="sxs-lookup"><span data-stu-id="a58ed-107">Such problems include:</span></span>  
  
- <span data-ttu-id="a58ed-108">Невозможно прочесть в этом сообщении маркер клиента.</span><span class="sxs-lookup"><span data-stu-id="a58ed-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="a58ed-109">Токен клиента не прошел проверку подлинности (неправильный пароль).</span><span class="sxs-lookup"><span data-stu-id="a58ed-109">Client token has failed authentication (bad password).</span></span>  
  
- <span data-ttu-id="a58ed-110">Сбой при проверке подписи (сообщение было изменено).</span><span class="sxs-lookup"><span data-stu-id="a58ed-110">Signature verification has failed (the message has been tampered).</span></span>  
  
- <span data-ttu-id="a58ed-111">Сообщение является копией предыдущего, что может свидетельствовать об атаке воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="a58ed-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="a58ed-112">Произошел сбой при расшифровке.</span><span class="sxs-lookup"><span data-stu-id="a58ed-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="a58ed-113">В сообщении отсутствуют некоторые обязательные элементы (отметка времени или зашифрованный блок данных).</span><span class="sxs-lookup"><span data-stu-id="a58ed-113">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="a58ed-114">Во время подтверждения TLSNEGO/SPNEGO произошли ошибки.</span><span class="sxs-lookup"><span data-stu-id="a58ed-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
