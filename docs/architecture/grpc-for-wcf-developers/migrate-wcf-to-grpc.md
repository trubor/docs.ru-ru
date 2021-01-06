---
title: Перенос решения WCF в gRPC-gRPC для разработчиков WCF
description: Как перенести различные типы служб WCF в эквивалент в gRPC.
ms.date: 12/15/2020
ms.openlocfilehash: 3bd35cb6119368ff3db3be9ab5fabf89f2652b29
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937965"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="b6d40-103">Перенос решения WCF в gRPC</span><span class="sxs-lookup"><span data-stu-id="b6d40-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="b6d40-104">В этой главе описывается работа с проектами ASP.NET Core 5,0 gRPC и демонстрируется перенос различных типов служб Windows Communication Foundation (WCF) в эквивалент gRPC.</span><span class="sxs-lookup"><span data-stu-id="b6d40-104">This chapter will describe how to work with ASP.NET Core 5.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="b6d40-105">Создайте проект ASP.NET Core 5,0 gRPC.</span><span class="sxs-lookup"><span data-stu-id="b6d40-105">Create an ASP.NET Core 5.0 gRPC project.</span></span>
- <span data-ttu-id="b6d40-106">Простые операции запроса-ответа для gRPC унарного RPC.</span><span class="sxs-lookup"><span data-stu-id="b6d40-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="b6d40-107">Односторонние операции для gRPC потоковой передачи RPC клиента.</span><span class="sxs-lookup"><span data-stu-id="b6d40-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="b6d40-108">Службы с полным дуплексом для gRPC двунаправленной потоковой передачи RPC.</span><span class="sxs-lookup"><span data-stu-id="b6d40-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="b6d40-109">Также существует Сравнение использования служб потоковой передачи и повторяющихся полей для возврата наборов данных, и в конце главы рассматривается использование клиентских библиотек.</span><span class="sxs-lookup"><span data-stu-id="b6d40-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="b6d40-110">Пример приложения WCF представляет собой минимальную заглушку набора служб торговли акции.</span><span class="sxs-lookup"><span data-stu-id="b6d40-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="b6d40-111">В нем используется библиотека контейнеров инверсии управления (IoC) с открытым исходным кодом, именуемая Autofac для внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="b6d40-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="b6d40-112">Он включает три службы — по одному для каждого типа службы WCF.</span><span class="sxs-lookup"><span data-stu-id="b6d40-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="b6d40-113">Службы будут обсуждаться более подробно в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="b6d40-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="b6d40-114">Вы можете скачать решения из [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) на GitHub.</span><span class="sxs-lookup"><span data-stu-id="b6d40-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="b6d40-115">Службы используют фиктивные данные для сворачивания внешних зависимостей.</span><span class="sxs-lookup"><span data-stu-id="b6d40-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="b6d40-116">Примеры включают реализации WCF и gRPC для каждой службы.</span><span class="sxs-lookup"><span data-stu-id="b6d40-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b6d40-117">[Назад](ws-protocols.md)
>[Вперед](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="b6d40-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
