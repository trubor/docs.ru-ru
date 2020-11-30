---
title: Практическое руководство. Использование именованных каналов для сетевого взаимодействия между процессами
description: Ознакомьтесь с двумя примерами использования именованных каналов для межпроцессного взаимодействия между сервером канала и одним клиентом канала в сети или несколькими.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET], named pipes
- named pipes [.NET]
- pipes [.NET]
- multiple connections via named pipes
- network communications [.NET], named pipes
- impersonation [.NET], named pipes
- full duplex communication [.NET], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
ms.openlocfilehash: 421fe06ce24fe8d78c7f8306db6a32ae83da694a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734547"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="1ec5d-103">Практическое руководство. Использование именованных каналов для сетевого взаимодействия между процессами</span><span class="sxs-lookup"><span data-stu-id="1ec5d-103">How to: Use Named Pipes for Network Interprocess Communication</span></span>

<span data-ttu-id="1ec5d-104">Именованные каналы обеспечивают межпроцессное взаимодействие между сервером канала и одним или несколькими клиентами канала.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-104">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="1ec5d-105">Они предоставляют больше функциональных возможностей, чем анонимные каналы, которые обеспечивают межпроцессное взаимодействие на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-105">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="1ec5d-106">Именованные каналы поддерживают полную дуплексную связь по сети и несколько экземпляров сервера, связь на основе сообщений и олицетворение клиента, позволяющее подключающимся процессам использовать собственные наборы разрешений на удаленных серверах.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-106">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="1ec5d-107">Для реализации именованных каналов используются классы <xref:System.IO.Pipes.NamedPipeServerStream> и <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-107">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ec5d-108">Пример</span><span class="sxs-lookup"><span data-stu-id="1ec5d-108">Example</span></span>  

 <span data-ttu-id="1ec5d-109">В примере ниже показано, как создать именованный канал с помощью класса <xref:System.IO.Pipes.NamedPipeServerStream>.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-109">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="1ec5d-110">В этом примере серверный процесс создает четыре потока.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-110">In this example, the server process creates four threads.</span></span> <span data-ttu-id="1ec5d-111">Каждый поток может принимать подключение клиента.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-111">Each thread can accept a client connection.</span></span> <span data-ttu-id="1ec5d-112">Процесс подключения клиента передает серверу имя файла.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-112">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="1ec5d-113">Если клиенту имеет необходимые разрешения, серверный процесс открывает указанный файл и отправляет клиенту его содержимое.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-113">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="1ec5d-114">Пример</span><span class="sxs-lookup"><span data-stu-id="1ec5d-114">Example</span></span>  

 <span data-ttu-id="1ec5d-115">В примере ниже представлен клиентский процесс, основанный на классе <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-115">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="1ec5d-116">Клиент подключается к серверному процессу и передает серверу имя файла.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-116">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="1ec5d-117">В этом примере используется олицетворение. Это означает, что у идентификатора, от имени которого выполняется клиентское приложение, должны быть разрешения на доступ к файлу.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-117">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="1ec5d-118">Затем сервер отправляет клиенту содержимое файла.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-118">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="1ec5d-119">Полученное содержимое файла выводится в консоль.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-119">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1ec5d-120">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="1ec5d-120">Robust Programming</span></span>  

 <span data-ttu-id="1ec5d-121">Клиентский и серверный процессы в этом примере предназначены для выполнения на одном компьютере, поэтому объекту <xref:System.IO.Pipes.NamedPipeClientStream> передается имя сервера `"."`.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-121">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="1ec5d-122">Если клиентский и серверный процессы выполняются на разных компьютерах, вместо `"."` должно быть указано сетевое имя компьютера, на котором осуществляется серверный процесс.</span><span class="sxs-lookup"><span data-stu-id="1ec5d-122">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec5d-123">См. также</span><span class="sxs-lookup"><span data-stu-id="1ec5d-123">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="1ec5d-124">Каналы</span><span class="sxs-lookup"><span data-stu-id="1ec5d-124">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="1ec5d-125">Практическое руководство. Использование анонимных каналов для локального взаимодействия между процессами</span><span class="sxs-lookup"><span data-stu-id="1ec5d-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
