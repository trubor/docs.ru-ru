---
title: Перенос существующих приложений ASP.NET в .NET Core
description: Бесплатное руководство по преобразованию приложений MVC ASP.NET и приложений веб-API ASP.NET в приложения ASP.NET Core.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 848f0e9533a65b59055853f1d502307abb69118c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105949"
---
# <a name="porting-existing-aspnet-apps-to-net-core"></a><span data-ttu-id="38554-103">Перенос существующих приложений ASP.NET в .NET Core</span><span class="sxs-lookup"><span data-stu-id="38554-103">Porting Existing ASP.NET Apps to .NET Core</span></span>

![изображение обложки](./media/index/porting-existing-aspnet-apps.png)

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="38554-105">ИЗДАТЕЛЬ</span><span class="sxs-lookup"><span data-stu-id="38554-105">PUBLISHED BY</span></span>

<span data-ttu-id="38554-106">Подразделение Microsoft Developer Division, команды разработки .NET и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="38554-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="38554-107">Подразделение корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="38554-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="38554-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="38554-108">One Microsoft Way</span></span>

<span data-ttu-id="38554-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="38554-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="38554-110">&copy; Корпорация Майкрософт (Microsoft Corporation), 2020.</span><span class="sxs-lookup"><span data-stu-id="38554-110">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="38554-111">Все права защищены.</span><span class="sxs-lookup"><span data-stu-id="38554-111">All rights reserved.</span></span> <span data-ttu-id="38554-112">Запрещается полное или частичное воспроизведение или передача этой книги в любом виде или любыми средствами без письменного разрешения издателя.</span><span class="sxs-lookup"><span data-stu-id="38554-112">No part of this book's contents may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="38554-113">Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора.</span><span class="sxs-lookup"><span data-stu-id="38554-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="38554-114">Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.</span><span class="sxs-lookup"><span data-stu-id="38554-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="38554-115">Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными.</span><span class="sxs-lookup"><span data-stu-id="38554-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="38554-116">Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.</span><span class="sxs-lookup"><span data-stu-id="38554-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="38554-117">Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="38554-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="38554-118">Mac и macOS являются товарными знаками Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="38554-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="38554-119">Логотип Docker с изображением кита является зарегистрированным товарным знаком Docker, Inc. Используется с разрешения.</span><span class="sxs-lookup"><span data-stu-id="38554-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="38554-120">Все другие наименования и логотипы являются собственностью своих законных владельцев.</span><span class="sxs-lookup"><span data-stu-id="38554-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="38554-121">Авторы:</span><span class="sxs-lookup"><span data-stu-id="38554-121">Authors:</span></span>

> <span data-ttu-id="38554-122">**Стив Смит (Steve Smith)** , преподаватель и разработчик программного обеспечения, [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="38554-122">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="38554-123">Участники и рецензенты:</span><span class="sxs-lookup"><span data-stu-id="38554-123">Participants and Reviewers:</span></span>

> <span data-ttu-id="38554-124">**Ниш Анил (Nish Anil)** , старший менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="38554-124">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="38554-125">**Майк Русос** (Mike Rousos), главный специалист по разработке программного обеспечения, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="38554-125">**Mike Rousos**, Principal Software Engineer, .NET team, Microsoft</span></span>

> <span data-ttu-id="38554-126">**Скотт Эдди** (Scott Addie), старший разработчик содержимого, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="38554-126">**Scott Addie**, Senior Content Developer, .NET team, Microsoft</span></span>

> <span data-ttu-id="38554-127">**Дэвид Пайн** (David Pine), старший разработчик содержимого, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="38554-127">**David Pine**, Senior Content Developer, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="38554-128">Version</span><span class="sxs-lookup"><span data-stu-id="38554-128">Version</span></span>

<span data-ttu-id="38554-129">В это руководство включены сведения о версии **.NET Core 3.1** и обновлениях, связанных с тем же поколением технологий (т. е. технологий Azure и сторонних производителей), к которому относится выпуск .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="38554-129">This guide covers **.NET Core 3.1** and updates related to the same technology "wave" (that is, Azure and other third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="38554-130">Обновление .NET Core 3.1 до .NET 5.0 (следующая версия) выполняется относительно просто и определенно требует значительно меньше усилий, чем перенос приложений с .NET Framework на .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38554-130">Updating from .NET Core 3.1 to .NET 5.0 (the next version) is relatively straightforward and certainly will require substantially less effort than porting from .NET Framework to .NET Core.</span></span> <span data-ttu-id="38554-131">Миграция с .NET Framework 4.x на .NET 5.0 выполняется так же, как и миграция на .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="38554-131">Migrating from .NET Framework 4.x to .NET 5.0 will be similar to migrating to .NET Core 3.1.</span></span> <span data-ttu-id="38554-132">Дополнительные сведения см. в статье [Выбор подходящей версии .NET Core](choose-net-core-version.md).</span><span class="sxs-lookup"><span data-stu-id="38554-132">For more information, see [choosing the right .NET Core version](choose-net-core-version.md).</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="38554-133">Кому необходимо это руководство</span><span class="sxs-lookup"><span data-stu-id="38554-133">Who should use this guide</span></span>

<span data-ttu-id="38554-134">Это руководство предназначено для разработчиков, руководителей разработки и архитекторов, которые хотят перенести существующие приложения, написанные для MVC ASP.NET и веб-API ASP.NET (.NET Framework 4.x), в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38554-134">This guide's audience is developers, development leads, and architects who are interested in migrating their existing apps written for ASP.NET MVC and Web API (.NET Framework 4.x) to .NET Core.</span></span> <span data-ttu-id="38554-135">Это руководство будет полезно для разработчиков, использующих ASP.NET Web Forms, но им также нужно ознакомиться с электронной книгой [Blazor для разработчиков ASP.NET Web Forms](../blazor-for-web-forms-developers/index.md).</span><span class="sxs-lookup"><span data-stu-id="38554-135">ASP.NET Web Forms developers will benefit from this guide but should also read the [Blazor for ASP.NET Web Forms Developers](../blazor-for-web-forms-developers/index.md) e-book.</span></span>

<span data-ttu-id="38554-136">Вторичной аудиторией являются лица, ответственные за принятие технических решений, которые планируют перенести свои приложения в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38554-136">A secondary audience is technical decision-makers planning when to move their apps to .NET Core.</span></span>

<span data-ttu-id="38554-137">Целевая аудитория этой книги — разработчики .NET с крупными приложениями на базе MVC и веб-API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="38554-137">The target audience for this book is .NET developers with large, existing apps that run on ASP.NET MVC and Web API.</span></span> <span data-ttu-id="38554-138">Приложения на базе ASP.NET Web Forms не рассматриваются в этой книге, хотя сравнение .NET Framework с .NET Core в большой степени может быть релевантным.</span><span class="sxs-lookup"><span data-stu-id="38554-138">Apps built on ASP.NET Web Forms are outside of the focus of this book, though much of the information comparing .NET Framework and .NET Core may still be relevant.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="38554-139">Как использовать это руководство</span><span class="sxs-lookup"><span data-stu-id="38554-139">How you can use this guide</span></span>

<span data-ttu-id="38554-140">Вы можете читать эту книгу согласно ее организации, как делают многие читатели.</span><span class="sxs-lookup"><span data-stu-id="38554-140">You can read this book straight through, as we expect many readers to do.</span></span> <span data-ttu-id="38554-141">В начале этой книги приведены соображения по поводу того, следует ли переносить приложения.</span><span class="sxs-lookup"><span data-stu-id="38554-141">This book will provide you first with considerations for whether you should port your app at all.</span></span> <span data-ttu-id="38554-142">Далее описывается разница между архитектурой .NET Framework и .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38554-142">That content is followed by architectural differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="38554-143">После этого представлены стратегии постепенного переноса крупного решения и инструкции по переносу реального приложения.</span><span class="sxs-lookup"><span data-stu-id="38554-143">From there, you'll learn strategies for migrating a large solution over time and how to port a real app.</span></span> <span data-ttu-id="38554-144">Затем в книге приводятся сценарии развертывания, которые решают проблемы, связанные с запуском разных приложений, отображаемых для пользователей как одно приложение.</span><span class="sxs-lookup"><span data-stu-id="38554-144">Next, the book includes deployment scenarios that address the need to run different apps while appearing as a single app to users.</span></span> <span data-ttu-id="38554-145">В заключении в книге описываются два конкретных случая переноса реальных приложений с ASP.NET MVC на ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="38554-145">The book concludes with two case studies describing real apps that have migrated from ASP.NET MVC to ASP.NET Core.</span></span>

<span data-ttu-id="38554-146">Независимо от того, откуда вы начнете чтение, вы можете перейти к любой из приведенных ниже глав для подробного изучения определенных концепций:</span><span class="sxs-lookup"><span data-stu-id="38554-146">Whether or not you choose to start from the first chapter, you can reference any of these chapters to learn about specific concepts:</span></span>

- [<span data-ttu-id="38554-147">Различия архитектуры</span><span class="sxs-lookup"><span data-stu-id="38554-147">Architectural differences</span></span>](architectural-differences.md)
- [<span data-ttu-id="38554-148">Перенос крупных решений</span><span class="sxs-lookup"><span data-stu-id="38554-148">Migrate large solutions</span></span>](migrate-large-solutions.md)
- [<span data-ttu-id="38554-149">Пример миграции</span><span class="sxs-lookup"><span data-stu-id="38554-149">Sample migration</span></span>](example-migration-eshop.md)
- [<span data-ttu-id="38554-150">Сценарии развертывания</span><span class="sxs-lookup"><span data-stu-id="38554-150">Deployment scenarios</span></span>](deployment-scenarios.md)

<span data-ttu-id="38554-151">Руководство предоставляется в формате [PDF](https://aka.ms/aspnet-porting-ebook) и доступно в Интернете.</span><span class="sxs-lookup"><span data-stu-id="38554-151">This guide is available both in [PDF form](https://aka.ms/aspnet-porting-ebook) and online.</span></span> <span data-ttu-id="38554-152">При необходимости вы можете порекомендовать этот документ членам своей команды или отправить им ссылку на его веб-версию, чтобы они были в курсе этих концепций.</span><span class="sxs-lookup"><span data-stu-id="38554-152">Feel free to forward this document or links to its online version to your team to ensure a common understanding of these concepts.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="38554-153">Отправить отзыв</span><span class="sxs-lookup"><span data-stu-id="38554-153">Send your feedback</span></span>

<span data-ttu-id="38554-154">Эта книга и примеры постоянно дополняются, поэтому мы ждем ваших отзывов.</span><span class="sxs-lookup"><span data-stu-id="38554-154">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="38554-155">Если у вас есть комментарии о том, как можно улучшить эту книгу, используйте раздел отзывов в нижней части любой страницы, созданный на основе [проблем GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="38554-155">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="38554-156">Вперед</span><span class="sxs-lookup"><span data-stu-id="38554-156">Next</span></span>](introduction.md)
