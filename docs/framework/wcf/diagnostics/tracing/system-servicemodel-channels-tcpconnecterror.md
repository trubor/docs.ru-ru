---
description: 'Дополнительные сведения: System. ServiceModel. Channels. Ткпконнектеррор'
title: System.ServiceModel.Channels.TcpConnectError
ms.date: 03/30/2017
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
ms.openlocfilehash: e8c8e682100080e8622d0371505c9f3b9ddb84d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99634392"
---
# <a name="systemservicemodelchannelstcpconnecterror"></a><span data-ttu-id="a9440-103">System.ServiceModel.Channels.TcpConnectError</span><span class="sxs-lookup"><span data-stu-id="a9440-103">System.ServiceModel.Channels.TcpConnectError</span></span>

<span data-ttu-id="a9440-104">Ошибка операции TCP-соединения.</span><span class="sxs-lookup"><span data-stu-id="a9440-104">The TCP connect operation failed.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a9440-105">Описание</span><span class="sxs-lookup"><span data-stu-id="a9440-105">Description</span></span>  

 <span data-ttu-id="a9440-106">Данная запись-предупреждение указывает на сбой соединения с конечной точкой TCP.</span><span class="sxs-lookup"><span data-stu-id="a9440-106">This warning level trace indicates a failure to connect to a TCP endpoint.</span></span> <span data-ttu-id="a9440-107">Это может произойти, если удаленная конечная точка по данному IP-адресу и порту не отвечает.</span><span class="sxs-lookup"><span data-stu-id="a9440-107">This could happen if the remote endpoint is not responding at a given IP address and port.</span></span> <span data-ttu-id="a9440-108">Эту запись можно игнорировать, если последующие попытки соединения с другими допустимыми IP-адресами (такими как IPv4- или IPv6-адреса или другие адреса, представляющие данное имя узла) будут успешными.</span><span class="sxs-lookup"><span data-stu-id="a9440-108">This trace can be ignored if subsequent attempts to connect to other valid IP addresses (such as IPv4 or IPv6 addresses, or other IP addresses representing a given hostname) succeed.</span></span> <span data-ttu-id="a9440-109">Исключение в этой записи может содержать дополнительные сведения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="a9440-109">The exception within this trace can reveal additional information about the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9440-110">См. также</span><span class="sxs-lookup"><span data-stu-id="a9440-110">See also</span></span>

- [<span data-ttu-id="a9440-111">Трассировка</span><span class="sxs-lookup"><span data-stu-id="a9440-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="a9440-112">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="a9440-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a9440-113">Администрирование и диагностика</span><span class="sxs-lookup"><span data-stu-id="a9440-113">Administration and Diagnostics</span></span>](../index.md)
