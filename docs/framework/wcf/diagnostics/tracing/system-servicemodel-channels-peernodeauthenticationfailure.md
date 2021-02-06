---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Пирнодеаусентикатионфаилуре'
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 751202abd3e199a03fc4ee0bf1252d4a8027e0cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99634938"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="c34ca-103">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="c34ca-103">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>

<span data-ttu-id="c34ca-104">Подтверждение безопасности с потенциальным соседним узлом завершилось неуспешно.</span><span class="sxs-lookup"><span data-stu-id="c34ca-104">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c34ca-105">Описание</span><span class="sxs-lookup"><span data-stu-id="c34ca-105">Description</span></span>  

 <span data-ttu-id="c34ca-106">Эта трассировка возникает при попытке установить безопасное соединение с соседним узлом.</span><span class="sxs-lookup"><span data-stu-id="c34ca-106">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="c34ca-107">Это может произойти из-за недостаточных или неправильных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="c34ca-107">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="c34ca-108">PeerChannel распознает один тип маркеров для строгой идентификации (сертификаты X.509), что обеспечивает строгую модель удостоверения, зависящую от типа проверки подлинности и авторизации, который может быть реализован.</span><span class="sxs-lookup"><span data-stu-id="c34ca-108">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="c34ca-109">PeerChannel также обеспечивает поддержку простых приложений посредством использования паролей.</span><span class="sxs-lookup"><span data-stu-id="c34ca-109">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="c34ca-110">Пароли могут использоваться только для разрешения входа в сеанс; их нельзя использовать для проверки подлинности сообщений.</span><span class="sxs-lookup"><span data-stu-id="c34ca-110">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="c34ca-111">Это связано с тем, что симметричный маркер, общий для участников одноранговой группы, сложно (и не следует) использовать для проверки подлинности источника.</span><span class="sxs-lookup"><span data-stu-id="c34ca-111">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c34ca-112">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="c34ca-112">Troubleshooting</span></span>  

 <span data-ttu-id="c34ca-113">Обеспечьте, чтобы все соседние узлы имели соответствующие учетные данные безопасности.</span><span class="sxs-lookup"><span data-stu-id="c34ca-113">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c34ca-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c34ca-114">See also</span></span>

- [<span data-ttu-id="c34ca-115">Безопасность одноранговых каналов</span><span class="sxs-lookup"><span data-stu-id="c34ca-115">Peer Channel Security</span></span>](../../feature-details/peer-channel-security.md)
- [<span data-ttu-id="c34ca-116">Трассировка</span><span class="sxs-lookup"><span data-stu-id="c34ca-116">Tracing</span></span>](index.md)
- [<span data-ttu-id="c34ca-117">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="c34ca-117">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c34ca-118">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="c34ca-118">Administration and Diagnostics</span></span>](../index.md)
