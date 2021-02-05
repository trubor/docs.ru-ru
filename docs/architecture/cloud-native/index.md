---
title: Разработка ориентированных на облако приложений .NET для Azure
description: Руководство по созданию ориентированных на облако приложений, использующих контейнеры, микрослужбы и бессерверные функции Azure.
author: ardalis
ms.date: 01/19/2021
ms.openlocfilehash: ad641517f9dc24aed9180cf6a092f4754739bceb
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506127"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="1de94-103">Разработка ориентированных на облако приложений .NET для Azure</span><span class="sxs-lookup"><span data-stu-id="1de94-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![изображение обложки](./media/cover.png)

<span data-ttu-id="1de94-105">**Выпуск 1.0.2**</span><span class="sxs-lookup"><span data-stu-id="1de94-105">**EDITION v1.0.2**</span></span>

<span data-ttu-id="1de94-106">Обновления книги и вклад сообщества см. в [журнале изменений](https://aka.ms/cn-ebook-changelog).</span><span class="sxs-lookup"><span data-stu-id="1de94-106">Refer [changelog](https://aka.ms/cn-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="1de94-107">ИЗДАТЕЛЬ</span><span class="sxs-lookup"><span data-stu-id="1de94-107">PUBLISHED BY</span></span>

<span data-ttu-id="1de94-108">Подразделение Microsoft Developer Division, команды разработки .NET и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1de94-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="1de94-109">Подразделение корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1de94-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="1de94-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="1de94-110">One Microsoft Way</span></span>

<span data-ttu-id="1de94-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="1de94-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="1de94-112">&copy; Корпорация Майкрософт (Microsoft Corporation), 2021.</span><span class="sxs-lookup"><span data-stu-id="1de94-112">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="1de94-113">Все права защищены.</span><span class="sxs-lookup"><span data-stu-id="1de94-113">All rights reserved.</span></span> <span data-ttu-id="1de94-114">Запрещается полное или частичное воспроизведение или передача настоящей книги в любом виде или любыми средствами без письменного разрешения издателя.</span><span class="sxs-lookup"><span data-stu-id="1de94-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="1de94-115">Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора.</span><span class="sxs-lookup"><span data-stu-id="1de94-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="1de94-116">Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.</span><span class="sxs-lookup"><span data-stu-id="1de94-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="1de94-117">Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными.</span><span class="sxs-lookup"><span data-stu-id="1de94-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="1de94-118">Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.</span><span class="sxs-lookup"><span data-stu-id="1de94-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="1de94-119">Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="1de94-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="1de94-120">Mac и macOS являются товарными знаками Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="1de94-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="1de94-121">Логотип Docker с изображением кита является зарегистрированным товарным знаком Docker, Inc. Используется с разрешения.</span><span class="sxs-lookup"><span data-stu-id="1de94-121">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="1de94-122">Все другие наименования и логотипы являются собственностью своих законных владельцев.</span><span class="sxs-lookup"><span data-stu-id="1de94-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="1de94-123">Авторы:</span><span class="sxs-lookup"><span data-stu-id="1de94-123">Authors:</span></span>

> <span data-ttu-id="1de94-124">**Роб Веттор (Rob Vettor)**  — главный архитектор облачных систем/IP-архитектор — [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1de94-124">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="1de94-125">**Стив Смит (Steve Smith)** , преподаватель и разработчик программного обеспечения, [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="1de94-125">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="1de94-126">Участники и рецензенты:</span><span class="sxs-lookup"><span data-stu-id="1de94-126">Participants and Reviewers:</span></span>

> <span data-ttu-id="1de94-127">**Цезарь де ла Торре (Cesar De la Torre)** , старший менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1de94-127">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="1de94-128">**Ниш Анил (Nish Anil)** , старший менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1de94-128">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="1de94-129">**Джереми Ликнесс (Jeremy Likness)** , старший менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1de94-129">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="1de94-130">**Сесил Филлип (Cecil Phillip)** , старший советник по облачной разработке, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1de94-130">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>
>
> <span data-ttu-id="1de94-131">**Самит Гош (Sumit Ghosh)** , главный консультант в Neudesic</span><span class="sxs-lookup"><span data-stu-id="1de94-131">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

<span data-ttu-id="1de94-132">Редакторы:</span><span class="sxs-lookup"><span data-stu-id="1de94-132">Editors:</span></span>

> <span data-ttu-id="1de94-133">**Майра Вензел (Maira Wenzel)** , менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1de94-133">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="1de94-134">**Дэвид Пайн** (David Pine), старший разработчик содержимого, разработка документации по .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="1de94-134">**David Pine**, Senior Content Developer, .NET docs, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="1de94-135">Версия</span><span class="sxs-lookup"><span data-stu-id="1de94-135">Version</span></span>

<span data-ttu-id="1de94-136">В это руководство включены сведения о версии **.NET 5** и множество дополнений, связанных с тем же "поколением" технологий (т. е. технологий Azure и сторонних производителей), к которому относится выпуск .NET 5.</span><span class="sxs-lookup"><span data-stu-id="1de94-136">This guide has been written to cover **.NET 5** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET 5 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="1de94-137">Кому необходимо это руководство</span><span class="sxs-lookup"><span data-stu-id="1de94-137">Who should use this guide</span></span>

<span data-ttu-id="1de94-138">Это руководство предназначено главным образом для разработчиков, руководителей отделов разработки и архитекторов, желающих научиться создавать приложения, ориентированные на облако.</span><span class="sxs-lookup"><span data-stu-id="1de94-138">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="1de94-139">Побочной аудиторией являются лица, принимающие решения технического характера, которым нужно определить, использовать ли ориентацию на облако при создании своих приложений.</span><span class="sxs-lookup"><span data-stu-id="1de94-139">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="1de94-140">Как использовать это руководство</span><span class="sxs-lookup"><span data-stu-id="1de94-140">How you can use this guide</span></span>

<span data-ttu-id="1de94-141">Это руководство начинается с определения ориентации на облако и представляет эталонное приложение, созданное с применением принципов и технологий ориентации на облако.</span><span class="sxs-lookup"><span data-stu-id="1de94-141">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="1de94-142">Помимо этих первых двух глав, оставшаяся часть книги поделена на главы, касающиеся большинства ориентированных на облако приложений.</span><span class="sxs-lookup"><span data-stu-id="1de94-142">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="1de94-143">Вы можете перейти к любой из этих глав, чтобы узнать о подходах ориентации на облако.</span><span class="sxs-lookup"><span data-stu-id="1de94-143">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="1de94-144">Данные и доступ к ним</span><span class="sxs-lookup"><span data-stu-id="1de94-144">Data and data access</span></span>
- <span data-ttu-id="1de94-145">Модели связи</span><span class="sxs-lookup"><span data-stu-id="1de94-145">Communication patterns</span></span>
- <span data-ttu-id="1de94-146">Масштабирование и масштабируемость</span><span class="sxs-lookup"><span data-stu-id="1de94-146">Scaling and scalability</span></span>
- <span data-ttu-id="1de94-147">Устойчивость приложения</span><span class="sxs-lookup"><span data-stu-id="1de94-147">Application resiliency</span></span>
- <span data-ttu-id="1de94-148">Мониторинг и работоспособность</span><span class="sxs-lookup"><span data-stu-id="1de94-148">Monitoring and health</span></span>
- <span data-ttu-id="1de94-149">Идентификация и безопасность</span><span class="sxs-lookup"><span data-stu-id="1de94-149">Identity and security</span></span>
- <span data-ttu-id="1de94-150">DevOps</span><span class="sxs-lookup"><span data-stu-id="1de94-150">DevOps</span></span>

<span data-ttu-id="1de94-151">Руководство доступно как в формате [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf), так и в Интернете.</span><span class="sxs-lookup"><span data-stu-id="1de94-151">This guide is available both in [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) form and online.</span></span> <span data-ttu-id="1de94-152">При необходимости вы можете порекомендовать этот документ членам своей команды или отправить им ссылку на его интернет-версию, чтобы они были в курсе этих аспектов.</span><span class="sxs-lookup"><span data-stu-id="1de94-152">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="1de94-153">В большинстве этих вопросов важную роль играет понимание базовых принципов и шаблонов, а также компромиссов, связанных с соответствующими решениями.</span><span class="sxs-lookup"><span data-stu-id="1de94-153">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="1de94-154">Цель этого документа заключается в том, чтобы предоставить командам и их руководителям сведения, необходимые для принятия взвешенных решений по архитектуре, разработке и размещению приложений.</span><span class="sxs-lookup"><span data-stu-id="1de94-154">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="1de94-155">Отправить отзыв</span><span class="sxs-lookup"><span data-stu-id="1de94-155">Send your feedback</span></span>

<span data-ttu-id="1de94-156">Эта книга и примеры постоянно дополняются, поэтому мы ждем ваших отзывов.</span><span class="sxs-lookup"><span data-stu-id="1de94-156">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="1de94-157">Если у вас есть комментарии о том, как можно улучшить эту книгу, используйте раздел отзывов в нижней части любой страницы, созданный на основе [проблем GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="1de94-157">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="1de94-158">Вперед</span><span class="sxs-lookup"><span data-stu-id="1de94-158">Next</span></span>](introduction.md)
