---
description: 'Дополнительные сведения: привязка безопасности сообщений'
title: Привязка безопасности сообщений
ms.date: 03/30/2017
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
ms.openlocfilehash: 9392eb1955a4c142fc6cc5a693e14b7d765e4783
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703878"
---
# <a name="message-security-binding"></a><span data-ttu-id="773b1-103">Привязка безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="773b1-103">Message Security Binding</span></span>

<span data-ttu-id="773b1-104">Этот раздел содержит примеры, демонстрирующие привязку безопасности сообщений в службах Windows в WCF.</span><span class="sxs-lookup"><span data-stu-id="773b1-104">This section contains samples that demonstrate message security binding in Windows Services in WCF.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="773b1-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="773b1-105">In This Section</span></span>  

 [<span data-ttu-id="773b1-106">Безопасность сообщений с возможностью анонимного доступа</span><span class="sxs-lookup"><span data-stu-id="773b1-106">Message Security Anonymous</span></span>](message-security-anonymous.md)  
 <span data-ttu-id="773b1-107">В этом примере демонстрируется реализация приложения Windows Communication Foundation (WCF), использующего безопасность на уровне сообщений без проверки подлинности клиента, но требующего проверки подлинности сервера с помощью сертификата X. 509 на сервере.</span><span class="sxs-lookup"><span data-stu-id="773b1-107">This sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span>  
  
 [<span data-ttu-id="773b1-108">Сертификат безопасности сообщений</span><span class="sxs-lookup"><span data-stu-id="773b1-108">Message Security Certificate</span></span>](message-security-certificate.md)  
 <span data-ttu-id="773b1-109">В этом образце показано, как реализовать приложение, использующее протокол WS-Security и проверку подлинности с использованием сертификата X.509 v3 для клиента и требующее проверки подлинности сервера с использованием сертификата X.509 v3 сервера.</span><span class="sxs-lookup"><span data-stu-id="773b1-109">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span>  
  
 [<span data-ttu-id="773b1-110">Безопасность сообщений с использованием имени пользователя</span><span class="sxs-lookup"><span data-stu-id="773b1-110">Message Security User Name</span></span>](message-security-user-name.md)  
 <span data-ttu-id="773b1-111">В этом образце показано, как реализовать приложение, использующее протокол WS-Security и проверку подлинности имен пользователя для клиента и требующее проверки подлинности сервера с использованием сертификата X.509v3 сервера.</span><span class="sxs-lookup"><span data-stu-id="773b1-111">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span>  
  
 [<span data-ttu-id="773b1-112">Безопасность сообщений с использованием механизмов Windows</span><span class="sxs-lookup"><span data-stu-id="773b1-112">Message Security Windows</span></span>](message-security-windows.md)  
 <span data-ttu-id="773b1-113">В этом образце показывается, как настраивать привязку <xref:System.ServiceModel.WSHttpBinding> для использования безопасности на уровне сообщений с проверкой подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="773b1-113">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span>
