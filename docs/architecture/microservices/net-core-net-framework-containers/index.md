---
title: Выбор между .NET 5 и .NET Framework для контейнеров Docker
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Выбор между .NET 5 и .NET Framework для контейнеров Docker
ms.date: 02/02/2021
ms.openlocfilehash: 5c3d4eff00399c8a6a041daaa71cf9fe5c9d854f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665163"
---
# <a name="choosing-between-net-5-and-net-framework-for-docker-containers"></a><span data-ttu-id="0e4b1-103">Выбор между .NET 5 и .NET Framework для контейнеров Docker</span><span class="sxs-lookup"><span data-stu-id="0e4b1-103">Choosing Between .NET 5 and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="0e4b1-104">Серверные контейнерные приложения Docker можно разрабатывать на двух платформах .NET: [.NET Framework и .NET 5](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="0e4b1-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET 5](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="0e4b1-105">В них используется множество одинаковых компонентов платформы .NET, а код можно использовать как в одной среде, так и в другой.</span><span class="sxs-lookup"><span data-stu-id="0e4b1-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="0e4b1-106">Но между этими двумя платформами также существуют и фундаментальные различия. Поэтому ваш выбор будет зависеть от поставленной задачи.</span><span class="sxs-lookup"><span data-stu-id="0e4b1-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="0e4b1-107">В этом разделе приводятся рекомендации по выбору каждой из платформ.</span><span class="sxs-lookup"><span data-stu-id="0e4b1-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0e4b1-108">[Назад](../container-docker-introduction/docker-containers-images-registries.md)
>[Вперед](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="0e4b1-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
