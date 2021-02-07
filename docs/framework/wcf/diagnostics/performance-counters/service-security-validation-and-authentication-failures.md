---
description: 'Дополнительные сведения: служба: Проверка безопасности и ошибки проверки подлинности'
title: 'Служба: количество сбоев при проверке безопасности и проверке подлинности'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 8938c74e706526a02bf2ea5885951d067d6ebae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759488"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="62017-103">Служба: количество сбоев при проверке безопасности и проверке подлинности</span><span class="sxs-lookup"><span data-stu-id="62017-103">Service: Security Validation and Authentication Failures</span></span>

<span data-ttu-id="62017-104">Имя счетчика: Security Validation and Authentication Failures</span><span class="sxs-lookup"><span data-stu-id="62017-104">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="62017-105">Описание</span><span class="sxs-lookup"><span data-stu-id="62017-105">Description</span></span>  

 <span data-ttu-id="62017-106">Значение этого счетчика увеличивается всякий раз, когда сообщение отклоняется из-за проблемы безопасности, не относящейся к счетчику "Security Calls Not Authorized".</span><span class="sxs-lookup"><span data-stu-id="62017-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="62017-107">К таким проблемам относятся следующие.</span><span class="sxs-lookup"><span data-stu-id="62017-107">Such problems include:</span></span>  
  
- <span data-ttu-id="62017-108">Невозможно прочесть в этом сообщении маркер клиента.</span><span class="sxs-lookup"><span data-stu-id="62017-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="62017-109">Маркер клиента не прошел проверку подлинности (например, неправильный пароль).</span><span class="sxs-lookup"><span data-stu-id="62017-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="62017-110">Сбой при проверке подписи (например, сообщение было искажено).</span><span class="sxs-lookup"><span data-stu-id="62017-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="62017-111">Сообщение является копией предыдущего, что может свидетельствовать об атаке воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="62017-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="62017-112">Произошел сбой при расшифровке.</span><span class="sxs-lookup"><span data-stu-id="62017-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="62017-113">В сообщении отсутствуют некоторые обязательные элементы (например, отсутствует отметка времени или зашифрованный блок данных).</span><span class="sxs-lookup"><span data-stu-id="62017-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="62017-114">Во время подтверждения TLSNEGO/SPNEGO произошли ошибки.</span><span class="sxs-lookup"><span data-stu-id="62017-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
