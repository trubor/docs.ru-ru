---
title: Dapr для разработчиков .NET
description: Руководство для разработчиков .NET, в котором приводятся общие сведения о среде Microsoft Distributed Apps Runtime с открытым кодом и рекомендации по ее эффективному использованию.
author: robvet
ms.date: 02/17/2021
ms.openlocfilehash: 2ab66257cca6f99074e2aa45a24869012b4976fe
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623724"
---
# <a name="dapr-for-net-developers"></a><span data-ttu-id="74b92-103">Dapr для разработчиков .NET</span><span class="sxs-lookup"><span data-stu-id="74b92-103">Dapr for .NET Developers</span></span>

![изображение обложки](./media/cover.png)

<span data-ttu-id="74b92-105">**ПРЕДВАРИТЕЛЬНЫЙ ВЫПУСК**</span><span class="sxs-lookup"><span data-stu-id="74b92-105">**PREVIEW EDITION**</span></span>

<span data-ttu-id="74b92-106">ИЗДАТЕЛЬ</span><span class="sxs-lookup"><span data-stu-id="74b92-106">PUBLISHED BY</span></span>

<span data-ttu-id="74b92-107">Отдел разработки Майкрософт, команды .NET и Azure Incubations</span><span class="sxs-lookup"><span data-stu-id="74b92-107">Microsoft Developer Division, .NET, and Azure Incubations teams</span></span>

<span data-ttu-id="74b92-108">Подразделение корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="74b92-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="74b92-109">One Microsoft Way</span></span>

<span data-ttu-id="74b92-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="74b92-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="74b92-111">&copy; Корпорация Майкрософт (Microsoft Corporation), 2021.</span><span class="sxs-lookup"><span data-stu-id="74b92-111">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="74b92-112">Все права защищены.</span><span class="sxs-lookup"><span data-stu-id="74b92-112">All rights reserved.</span></span> <span data-ttu-id="74b92-113">Запрещается полное или частичное воспроизведение или передача настоящей книги в любом виде или любыми средствами без письменного разрешения издателя.</span><span class="sxs-lookup"><span data-stu-id="74b92-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="74b92-114">Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора.</span><span class="sxs-lookup"><span data-stu-id="74b92-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="74b92-115">Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.</span><span class="sxs-lookup"><span data-stu-id="74b92-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="74b92-116">Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными.</span><span class="sxs-lookup"><span data-stu-id="74b92-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="74b92-117">Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.</span><span class="sxs-lookup"><span data-stu-id="74b92-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="74b92-118">Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="74b92-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="74b92-119">Mac и macOS являются товарными знаками Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="74b92-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="74b92-120">Логотип Docker с изображением кита является зарегистрированным товарным знаком Docker, Inc. Используется с разрешения.</span><span class="sxs-lookup"><span data-stu-id="74b92-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="74b92-121">Все другие наименования и логотипы являются собственностью своих законных владельцев.</span><span class="sxs-lookup"><span data-stu-id="74b92-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="74b92-122">Авторы:</span><span class="sxs-lookup"><span data-stu-id="74b92-122">Authors:</span></span>

> <span data-ttu-id="74b92-123">**Роб Веттор** (Rob Vettor) — главный архитектор облачных решений, [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-123">**Rob Vettor**, Principal Cloud Solution Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="74b92-124">**Зандер Моленкамп** (Sander Molenkamp) — главный архитектор облачных решений/Microsoft MVP, [sandermolenkamp.com](https://www.sandermolenkamp.com), [Info Support](https://www.infosupport.com/en/)</span><span class="sxs-lookup"><span data-stu-id="74b92-124">**Sander Molenkamp**, Principal Cloud Architect/Microsoft MVP - [sandermolenkamp.com](https://www.sandermolenkamp.com), [Info Support](https://www.infosupport.com/en/)</span></span>
>
> <span data-ttu-id="74b92-125">**Эдвин ван Вейк** (Edwin van Wijk), главный архитектор решений/Microsoft MVP, [defaultconstructor.com](https://defaultconstructor.com), [Info Support](https://www.infosupport.com/en/)</span><span class="sxs-lookup"><span data-stu-id="74b92-125">**Edwin van Wijk**, Principal Solution Architect/Microsoft MVP - [defaultconstructor.com](https://defaultconstructor.com), [Info Support](https://www.infosupport.com/en/)</span></span>

<span data-ttu-id="74b92-126">Участники и рецензенты:</span><span class="sxs-lookup"><span data-stu-id="74b92-126">Participants and Reviewers:</span></span>

> <span data-ttu-id="74b92-127">**Марк Руссинович** (Mark Russinovich), технический директор и технический специалист по Azure, управление по техническим вопросам Azure, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-127">**Mark Russinovich**, Azure CTO and Technical Fellow, Azure Office of CTO, Microsoft</span></span>
>
> <span data-ttu-id="74b92-128">**Ниш Анил (Nish Anil)** , старший менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-128">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="74b92-129">**Марк Фасселл** (Mark Fussell), главный руководитель программы, Azure Incubations, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-129">**Mark Fussell**, Principal Program Manager, Azure Incubations, Microsoft</span></span>
>
> <span data-ttu-id="74b92-130">**Ярон Шнайдер** (Yaron Schneider), главный разработчик, Azure Incubations, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-130">**Yaron Schneider**, Principal Software Engineer, Azure Incubations, Microsoft</span></span>
>
> <span data-ttu-id="74b92-131">**Ори Зохар** (Ori Zohar), старший руководитель программы, Azure Incubations, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-131">**Ori Zohar**, Senior Program Manager, Azure Incubations, Microsoft</span></span>

<span data-ttu-id="74b92-132">Редакторы:</span><span class="sxs-lookup"><span data-stu-id="74b92-132">Editors:</span></span>

> <span data-ttu-id="74b92-133">**Дэвид Пайн** (David Pine), старший разработчик содержимого, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-133">**David Pine**, Senior Content Developer, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="74b92-134">**Майра Вензел (Maira Wenzel)** , старший руководитель программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="74b92-134">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="74b92-135">Версия</span><span class="sxs-lookup"><span data-stu-id="74b92-135">Version</span></span>

<span data-ttu-id="74b92-136">Это руководство посвящено версии **Dapr 1.0**.</span><span class="sxs-lookup"><span data-stu-id="74b92-136">This guide has been written to cover the **Dapr 1.0** version.</span></span> <span data-ttu-id="74b92-137">Примеры .NET Core созданы на базе **.NET Core 3.1**.</span><span class="sxs-lookup"><span data-stu-id="74b92-137">.NET Core samples are based on **.NET Core 3.1**.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="74b92-138">Кому необходимо это руководство</span><span class="sxs-lookup"><span data-stu-id="74b92-138">Who should use this guide</span></span>

<span data-ttu-id="74b92-139">Это руководство предназначено главным образом для разработчиков, руководителей отделов разработки и архитекторов, желающих научиться создавать приложения, ориентированные на облако.</span><span class="sxs-lookup"><span data-stu-id="74b92-139">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="74b92-140">Побочной аудиторией являются лица, принимающие решения технического характера, которым нужно определить, использовать ли ориентацию на облако при создании своих приложений.</span><span class="sxs-lookup"><span data-stu-id="74b92-140">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="74b92-141">Как использовать это руководство</span><span class="sxs-lookup"><span data-stu-id="74b92-141">How you can use this guide</span></span>

<span data-ttu-id="74b92-142">Руководство доступно как в формате [PDF](https://aka.ms/dapr-ebook), так и в Интернете.</span><span class="sxs-lookup"><span data-stu-id="74b92-142">This guide is available both in [PDF](https://aka.ms/dapr-ebook) form and online.</span></span> <span data-ttu-id="74b92-143">При необходимости вы можете порекомендовать этот документ членам своей команды или отправить им ссылку на его интернет-версию, чтобы они были в курсе этих аспектов.</span><span class="sxs-lookup"><span data-stu-id="74b92-143">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="74b92-144">В большинстве этих вопросов важную роль играет понимание базовых принципов и шаблонов, а также компромиссов, связанных с соответствующими решениями.</span><span class="sxs-lookup"><span data-stu-id="74b92-144">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="74b92-145">Цель этого документа заключается в том, чтобы предоставить командам и их руководителям сведения, необходимые для принятия взвешенных решений по архитектуре, разработке и размещению приложений.</span><span class="sxs-lookup"><span data-stu-id="74b92-145">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="74b92-146">Отправить отзыв</span><span class="sxs-lookup"><span data-stu-id="74b92-146">Send your feedback</span></span>

<span data-ttu-id="74b92-147">Эта книга и примеры постоянно дополняются, поэтому мы ждем ваших отзывов.</span><span class="sxs-lookup"><span data-stu-id="74b92-147">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="74b92-148">Если у вас есть комментарии о том, как можно улучшить эту книгу, используйте раздел отзывов в нижней части любой страницы, созданный на основе [проблем GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="74b92-148">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="74b92-149">Вперед</span><span class="sxs-lookup"><span data-stu-id="74b92-149">Next</span></span>](foreword.md)
