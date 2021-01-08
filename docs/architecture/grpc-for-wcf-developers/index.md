---
title: ASP.NET Core gRPC для разработчиков WCF — gRPC для разработчиков WCF
description: Введение в создание служб gRPC в ASP.NET Core 5.0 для разработчиков WCF
ms.date: 01/06/2021
ms.openlocfilehash: 26cce6bb784c08a5b59623ff5882fcf2fbb9e9ac
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970197"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="c6f60-103">ASP.NET Core gRPC для разработчиков WCF</span><span class="sxs-lookup"><span data-stu-id="c6f60-103">ASP.NET Core gRPC for WCF Developers</span></span>

![изображение обложки](./media/cover.png)

<span data-ttu-id="c6f60-105">Редакция 1.0.1 — обновлено для соответствия ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="c6f60-105">EDITION v1.0.1 - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="c6f60-106">Обновления книги и вклад сообщества см. в [журнале изменений](https://aka.ms/grpc-ebook-changelog).</span><span class="sxs-lookup"><span data-stu-id="c6f60-106">Refer [changelog](https://aka.ms/grpc-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="c6f60-107">ИЗДАТЕЛЬ</span><span class="sxs-lookup"><span data-stu-id="c6f60-107">PUBLISHED BY</span></span>

<span data-ttu-id="c6f60-108">Подразделение Microsoft Developer Division, команды разработки .NET и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c6f60-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="c6f60-109">Подразделение корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="c6f60-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="c6f60-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="c6f60-110">One Microsoft Way</span></span>

<span data-ttu-id="c6f60-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="c6f60-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="c6f60-112">© Корпорация Майкрософт (Microsoft Corporation), 2021.</span><span class="sxs-lookup"><span data-stu-id="c6f60-112">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="c6f60-113">Все права защищены.</span><span class="sxs-lookup"><span data-stu-id="c6f60-113">All rights reserved.</span></span> <span data-ttu-id="c6f60-114">Запрещается полное или частичное воспроизведение или передача настоящей книги в любом виде или любыми средствами без письменного разрешения издателя.</span><span class="sxs-lookup"><span data-stu-id="c6f60-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="c6f60-115">Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора.</span><span class="sxs-lookup"><span data-stu-id="c6f60-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="c6f60-116">Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.</span><span class="sxs-lookup"><span data-stu-id="c6f60-116">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="c6f60-117">Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными.</span><span class="sxs-lookup"><span data-stu-id="c6f60-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="c6f60-118">Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.</span><span class="sxs-lookup"><span data-stu-id="c6f60-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="c6f60-119">Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="c6f60-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="c6f60-120">Логотип Docker с изображением кита является зарегистрированным товарным знаком Docker, Inc. Используется с разрешения.</span><span class="sxs-lookup"><span data-stu-id="c6f60-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="c6f60-121">Все другие наименования и логотипы являются собственностью своих законных владельцев.</span><span class="sxs-lookup"><span data-stu-id="c6f60-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="c6f60-122">Авторы:</span><span class="sxs-lookup"><span data-stu-id="c6f60-122">Authors:</span></span>

> <span data-ttu-id="c6f60-123">**Марк Рендл (Mark Rendle)**  — главный технический директор — [Visual Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="c6f60-123">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="c6f60-124">**Миранда Стайнер (Miranda Steiner)**  — технический писатель</span><span class="sxs-lookup"><span data-stu-id="c6f60-124">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="c6f60-125">Редактор:</span><span class="sxs-lookup"><span data-stu-id="c6f60-125">Editor:</span></span>

> <span data-ttu-id="c6f60-126">**Майра Вензел (Maira Wenzel)**  — старший разработчик содержимого — корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="c6f60-126">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="c6f60-127">Вступление</span><span class="sxs-lookup"><span data-stu-id="c6f60-127">Introduction</span></span>

<span data-ttu-id="c6f60-128">gRPC — это современная платформа для создания сетевых служб и распределенных приложений.</span><span class="sxs-lookup"><span data-stu-id="c6f60-128">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="c6f60-129">Представьте себе производительность привязок NetTCP Windows Communication Foundation (WCF) с кроссплатформенным взаимодействием SOAP.</span><span class="sxs-lookup"><span data-stu-id="c6f60-129">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="c6f60-130">gRPC основывается на HTTP/2 и протоколе кодирования сообщений Protobuf для обеспечения высокой производительности и низкого потребления пропускной способности при взаимодействии приложений и служб.</span><span class="sxs-lookup"><span data-stu-id="c6f60-130">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="c6f60-131">Она поддерживает создание серверного и клиентского кода в большинстве популярных языков программирования и платформ, включая .NET, Java, Python, Node.js, Go и C++.</span><span class="sxs-lookup"><span data-stu-id="c6f60-131">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="c6f60-132">Учитывая первоклассную поддержку gRPC в ASP.NET Core 5.0 и имеющиеся средства и библиотеки gRPC для .NET Framework 4.x, это отличная альтернатива WCF для команд разработчиков, рассматривающих внедрение .NET в своих организациях.</span><span class="sxs-lookup"><span data-stu-id="c6f60-132">With the first-class support for gRPC in ASP.NET Core 5.0, alongside the existing gRPC tools and libraries for .NET Framework 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="c6f60-133">Кому необходимо это руководство</span><span class="sxs-lookup"><span data-stu-id="c6f60-133">Who should use this guide</span></span>

<span data-ttu-id="c6f60-134">Это руководство было написано для разработчиков, работающих в .NET Framework или .NET, которые ранее пользовались WCF и хотят перенести свои приложения в современную среду RPC для .NET Core 3.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="c6f60-134">This guide was written for developers working in .NET Framework or .NET who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="c6f60-135">В более общем плане, если вы переходите или рассматриваете переход на .NET 5 и при этом хотите использовать встроенные средства gRPC, это руководство также будет для вас полезным.</span><span class="sxs-lookup"><span data-stu-id="c6f60-135">More generally, if you are upgrading, or considering upgrading, to .NET 5, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="c6f60-136">Как использовать это руководство</span><span class="sxs-lookup"><span data-stu-id="c6f60-136">How you can use this guide</span></span>

<span data-ttu-id="c6f60-137">Здесь представлено краткое введение в создание служб gRPC на ASP.NET Core 5.0 с особой ссылкой на WCF как аналогичную платформу.</span><span class="sxs-lookup"><span data-stu-id="c6f60-137">This is a short introduction to building gRPC Services in ASP.NET Core 5.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="c6f60-138">В нем объясняются принципы gRPC, связывающие каждую из представленных концепций с эквивалентными функциями в WCF, и даются рекомендации по переносу существующего приложения WCF в gRPC.</span><span class="sxs-lookup"><span data-stu-id="c6f60-138">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="c6f60-139">Оно также полезно для разработчиков, имеющих опыт работы с WCF и желающих изучать gRPC для создания новых служб.</span><span class="sxs-lookup"><span data-stu-id="c6f60-139">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="c6f60-140">Вы можете использовать эти примеры приложений в качестве шаблона для собственных проектов, и вы можете свободно копировать и повторно использовать код из книги или ее примеров.</span><span class="sxs-lookup"><span data-stu-id="c6f60-140">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="c6f60-141">При необходимости вы можете порекомендовать это руководство членам своей команды, чтобы и они были в курсе всех важных аспектов.</span><span class="sxs-lookup"><span data-stu-id="c6f60-141">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="c6f60-142">Если все заинтересованные лица будут использовать общий набор терминологии и придерживаться основополагающих принципов, архитектурные модели и практики будут применяться более последовательно.</span><span class="sxs-lookup"><span data-stu-id="c6f60-142">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="c6f60-143">Ссылки</span><span class="sxs-lookup"><span data-stu-id="c6f60-143">References</span></span>

- <span data-ttu-id="c6f60-144">**Веб-сайт gRPC**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="c6f60-144">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="c6f60-145">**Выбор между .NET 5 и .NET Framework для серверных приложений**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="c6f60-145">**Choosing between .NET 5 and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="c6f60-146">Вперед</span><span class="sxs-lookup"><span data-stu-id="c6f60-146">Next</span></span>](introduction.md)
