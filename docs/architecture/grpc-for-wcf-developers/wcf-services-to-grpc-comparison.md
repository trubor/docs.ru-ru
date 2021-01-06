---
title: Сравнение WCF с gRPC-gRPC для разработчиков WCF
description: Сравнение платформ WCF и gRPC для создания распределенных приложений.
ms.date: 12/15/2020
ms.openlocfilehash: 7dd41c3d6f248bb1ef5eacb323b1443c7bc575a7
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938498"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="0f5ec-103">Сравнение WCF и gRPC</span><span class="sxs-lookup"><span data-stu-id="0f5ec-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="0f5ec-104">В предыдущей главе вы узнаете о protobuf и том, как gRPC обрабатывает сообщения.</span><span class="sxs-lookup"><span data-stu-id="0f5ec-104">The previous chapter gave you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="0f5ec-105">Прежде чем выполнять подробное преобразование из Windows Communication Foundation (WCF) в gRPC, важно понять, как функции, доступные в WCF, обрабатываются в gRPC и какие обходные пути можно использовать при отсутствии эквивалента gRPC.</span><span class="sxs-lookup"><span data-stu-id="0f5ec-105">Before you work through a detailed conversion from Windows Communication Foundation (WCF) to gRPC, it's important know how the features available in WCF are handled in gRPC and what workarounds you can use when there's no gRPC equivalent.</span></span> <span data-ttu-id="0f5ec-106">В частности, в этой главе рассматриваются следующие темы:</span><span class="sxs-lookup"><span data-stu-id="0f5ec-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="0f5ec-107">Операции и методы</span><span class="sxs-lookup"><span data-stu-id="0f5ec-107">Operations and methods</span></span>
- <span data-ttu-id="0f5ec-108">Привязки и транспорты</span><span class="sxs-lookup"><span data-stu-id="0f5ec-108">Bindings and transports</span></span>
- <span data-ttu-id="0f5ec-109">Типы RPC</span><span class="sxs-lookup"><span data-stu-id="0f5ec-109">RPC types</span></span>
- <span data-ttu-id="0f5ec-110">Метаданные</span><span class="sxs-lookup"><span data-stu-id="0f5ec-110">Metadata</span></span>
- <span data-ttu-id="0f5ec-111">Обработка ошибок</span><span class="sxs-lookup"><span data-stu-id="0f5ec-111">Error handling</span></span>
- <span data-ttu-id="0f5ec-112">WS- \* Protocols</span><span class="sxs-lookup"><span data-stu-id="0f5ec-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="0f5ec-113">Пример gRPC</span><span class="sxs-lookup"><span data-stu-id="0f5ec-113">gRPC example</span></span>

<span data-ttu-id="0f5ec-114">При создании нового проекта ASP.NET Core 5,0 gRPC из Visual Studio 2019 или командной строки для вас создается gRPC эквивалент "Hello World".</span><span class="sxs-lookup"><span data-stu-id="0f5ec-114">When you create a new ASP.NET Core 5.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="0f5ec-115">Он состоит из `greeter.proto` файла, который определяет службу и ее сообщения, а также `GreeterService.cs` файл с реализацией службы.</span><span class="sxs-lookup"><span data-stu-id="0f5ec-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message that contains the user's name.
message HelloRequest {
  string name = 1;
}

// The response message that contains the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

<span data-ttu-id="0f5ec-116">В этой главе мы рассмотрим этот пример кода при объяснении различных концепций и функций gRPC.</span><span class="sxs-lookup"><span data-stu-id="0f5ec-116">This chapter will refer to this example code when explaining different concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0f5ec-117">[Назад](protobuf-maps.md)
>[Вперед](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="0f5ec-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
