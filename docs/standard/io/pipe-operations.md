---
title: Операции с каналами в .NET
description: 'Сведения об операциях с каналами в .NET. Каналы предоставляют средства для межпроцессного взаимодействия. Существует два типа каналов: анонимные и именованные.'
ms.date: 03/30/2017
helpviewer_keywords:
- pipes [.NET]
- pipe operations [.NET]
- interprocess communication [.NET], pipes
- I/O [.NET], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: bb8804c32b9f2b54b05298779bddae117c10dcf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734807"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="88702-105">Операции с каналами в .NET</span><span class="sxs-lookup"><span data-stu-id="88702-105">Pipe Operations in .NET</span></span>

<span data-ttu-id="88702-106">Каналы предоставляют средства для межпроцессного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="88702-106">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="88702-107">Существует два типа каналов.</span><span class="sxs-lookup"><span data-stu-id="88702-107">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="88702-108">Анонимные каналы.</span><span class="sxs-lookup"><span data-stu-id="88702-108">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="88702-109">Анонимные каналы обеспечивают межпроцессное взаимодействие на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="88702-109">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="88702-110">Анонимные каналы требуют меньше ресурсов, чем именованные каналы, но предоставляют меньше возможностей.</span><span class="sxs-lookup"><span data-stu-id="88702-110">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="88702-111">Анонимные каналы являются односторонними и их нельзя использовать в сети.</span><span class="sxs-lookup"><span data-stu-id="88702-111">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="88702-112">Они поддерживают только один экземпляр сервера.</span><span class="sxs-lookup"><span data-stu-id="88702-112">They support only a single server instance.</span></span> <span data-ttu-id="88702-113">Анонимные каналы подходят для взаимодействия между потоками или между родительским и дочерним процессами, поскольку в этих сценариях дескриптор канала можно легко передать дочернему процессу при его создании.</span><span class="sxs-lookup"><span data-stu-id="88702-113">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="88702-114">В .NET анонимные каналы реализуются с помощью классов <xref:System.IO.Pipes.AnonymousPipeServerStream> и <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="88702-114">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="88702-115">См. практическое руководство по [ Использование анонимных каналов для локального взаимодействия между процессами](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="88702-115">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="88702-116">Именованные каналы.</span><span class="sxs-lookup"><span data-stu-id="88702-116">Named pipes.</span></span>  
  
     <span data-ttu-id="88702-117">Именованные каналы обеспечивают межпроцессное взаимодействие между сервером канала и одним или несколькими клиентами канала.</span><span class="sxs-lookup"><span data-stu-id="88702-117">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="88702-118">Именованные каналы могут быть односторонним или дуплексным.</span><span class="sxs-lookup"><span data-stu-id="88702-118">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="88702-119">Они поддерживают связь на основе сообщений и позволяют нескольким клиентам одновременно подключаться к одному серверному процессу через канал с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="88702-119">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="88702-120">Именованные каналы также поддерживают олицетворение, при котором подключенные процессы используют на удаленных серверах собственные разрешения доступа.</span><span class="sxs-lookup"><span data-stu-id="88702-120">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="88702-121">В .NET именованные каналы реализуются с помощью классов <xref:System.IO.Pipes.NamedPipeServerStream> и <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="88702-121">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="88702-122">См. практическое руководство по [ Использование именованных каналов для сетевого взаимодействия между процессами](how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="88702-122">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88702-123">См. также</span><span class="sxs-lookup"><span data-stu-id="88702-123">See also</span></span>

- [<span data-ttu-id="88702-124">Файловый и потоковый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="88702-124">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="88702-125">Практическое руководство. Использование анонимных каналов для локального взаимодействия между процессами</span><span class="sxs-lookup"><span data-stu-id="88702-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="88702-126">Практическое руководство. Использование именованных каналов для сетевого взаимодействия между процессами</span><span class="sxs-lookup"><span data-stu-id="88702-126">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
