---
title: Выбор между .NET 5 и .NET Framework для контейнеров Docker
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Выбор между .NET 5 и .NET Framework для контейнеров Docker
ms.date: 01/13/2021
ms.openlocfilehash: 5c7ea1be02722fce7c5784afa89c18defbe4eeaf
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188651"
---
# <a name="choosing-between-net-and-net-framework-for-docker-containers"></a><span data-ttu-id="cb1b7-103">Выбор между .NET и .NET Framework для контейнеров Docker</span><span class="sxs-lookup"><span data-stu-id="cb1b7-103">Choosing Between .NET and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="cb1b7-104">Серверные контейнерные приложения Docker можно разрабатывать на двух платформах .NET: [.NET Framework и .NET 5](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="cb1b7-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET 5](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="cb1b7-105">В них используется множество одинаковых компонентов платформы .NET, а код можно использовать как в одной среде, так и в другой.</span><span class="sxs-lookup"><span data-stu-id="cb1b7-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="cb1b7-106">Но между этими двумя платформами также существуют и фундаментальные различия. Поэтому ваш выбор будет зависеть от поставленной задачи.</span><span class="sxs-lookup"><span data-stu-id="cb1b7-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="cb1b7-107">В этом разделе приводятся рекомендации по выбору каждой из платформ.</span><span class="sxs-lookup"><span data-stu-id="cb1b7-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cb1b7-108">[Назад](../container-docker-introduction/docker-containers-images-registries.md)
>[Вперед](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="cb1b7-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
