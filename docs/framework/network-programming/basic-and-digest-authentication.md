---
title: Обычная и дайджест-аутентификация
description: Узнайте, как использовать обычную и дайджест-проверку подлинности, в ходе которой приложение предоставляет имя пользователя и пароль в объекте WebRequest, который используется для запроса данных.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: e55dc58a7998824dbcfffa204008aacb815be03a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287583"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="dff96-103">Обычная и дайджест-аутентификация</span><span class="sxs-lookup"><span data-stu-id="dff96-103">Basic and Digest Authentication</span></span>

<span data-ttu-id="dff96-104">Реализация базовой аутентификации и аутентификации с использованием дайджеста в <xref:System.Net> соответствует требованиям документа RFC2617 – HTTP Authentication: Basic and Digest Authentication (RFC2617 — аутентификация HTTP: базовая аутентификация и аутентификация с использованием дайджеста), который доступен на веб-сайте [консорциума World Wide Web](https://www.w3.org).</span><span class="sxs-lookup"><span data-stu-id="dff96-104">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="dff96-105">Чтобы использовать обычную и дайджест-проверку подлинности, приложение должно предоставлять имя пользователя и пароль в свойстве <xref:System.Net.WebRequest.Credentials%2A> объекта <xref:System.Net.WebRequest>, которое используется для запроса данных из Интернета, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="dff96-105">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
> <span data-ttu-id="dff96-106">Данные, отправляемые с помощью базовой и дайджест-проверки подлинности, не шифруются, поэтому злоумышленник может их видеть.</span><span class="sxs-lookup"><span data-stu-id="dff96-106">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="dff96-107">Кроме того, базовые учетные данные аутентификации (имя пользователя и пароль) передаются в открытом виде и могут быть перехвачены.</span><span class="sxs-lookup"><span data-stu-id="dff96-107">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff96-108">См. также</span><span class="sxs-lookup"><span data-stu-id="dff96-108">See also</span></span>

- [<span data-ttu-id="dff96-109">Проверка подлинности NTLM и Kerberos</span><span class="sxs-lookup"><span data-stu-id="dff96-109">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="dff96-110">Проверка подлинности в Интернете</span><span class="sxs-lookup"><span data-stu-id="dff96-110">Internet Authentication</span></span>](internet-authentication.md)
