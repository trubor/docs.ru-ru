---
title: Модернизация классических приложений для Windows 10 с помощью .NET 5
description: Сведения о модернизации существующих классических приложений с помощью .NET 5
ms.date: 01/06/2021
ms.openlocfilehash: de8a451b0598b5eabd99028d377c161dace61623
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615712"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-5"></a><span data-ttu-id="affcb-103">Модернизация классических приложений для Windows 10 с помощью .NET 5</span><span class="sxs-lookup"><span data-stu-id="affcb-103">Modernizing Desktop Apps on Windows 10 with .NET 5</span></span>

![Снимок экрана, на котором показана обложка электронной книги, посвященной модернизации классических приложений.](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="affcb-105">**Редакция 1.0.1** — обновлено для соответствия .NET 5</span><span class="sxs-lookup"><span data-stu-id="affcb-105">**EDITION v1.0.1** - Updated to .NET 5</span></span>

<span data-ttu-id="affcb-106">Обновления книги и вклад сообщества см. в [журнале изменений](https://aka.ms/desktop-ebook-changelog).</span><span class="sxs-lookup"><span data-stu-id="affcb-106">Refer [changelog](https://aka.ms/desktop-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="affcb-107">ИЗДАТЕЛЬ</span><span class="sxs-lookup"><span data-stu-id="affcb-107">PUBLISHED BY</span></span>

<span data-ttu-id="affcb-108">Подразделение Microsoft Developer Division, команды разработки .NET и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="affcb-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="affcb-109">Подразделение корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="affcb-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="affcb-110">One Microsoft Way</span></span>

<span data-ttu-id="affcb-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="affcb-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="affcb-112">© Корпорация Майкрософт (Microsoft Corporation), 2021.</span><span class="sxs-lookup"><span data-stu-id="affcb-112">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="affcb-113">Все права защищены.</span><span class="sxs-lookup"><span data-stu-id="affcb-113">All rights reserved.</span></span> <span data-ttu-id="affcb-114">Запрещается полное или частичное воспроизведение или передача настоящей книги в любом виде или любыми средствами без письменного разрешения издателя.</span><span class="sxs-lookup"><span data-stu-id="affcb-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="affcb-115">Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора.</span><span class="sxs-lookup"><span data-stu-id="affcb-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="affcb-116">Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.</span><span class="sxs-lookup"><span data-stu-id="affcb-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="affcb-117">Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными.</span><span class="sxs-lookup"><span data-stu-id="affcb-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="affcb-118">Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.</span><span class="sxs-lookup"><span data-stu-id="affcb-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="affcb-119">Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="affcb-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="affcb-120">Mac и macOS являются товарными знаками Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="affcb-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="affcb-121">Все другие наименования и логотипы являются собственностью своих законных владельцев.</span><span class="sxs-lookup"><span data-stu-id="affcb-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="affcb-122">Соавторы:</span><span class="sxs-lookup"><span data-stu-id="affcb-122">Co-Authors:</span></span>

> <span data-ttu-id="affcb-123">**Олия Гавриш (Olia Gavrysh)** , руководитель программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-123">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="affcb-124">**Мигель Анхель Кастехон Домингес (Miguel Angel Castejón Dominguez)** , архитектор инновационных продуктов, Kabel</span><span class="sxs-lookup"><span data-stu-id="affcb-124">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="affcb-125">Участники и рецензенты:</span><span class="sxs-lookup"><span data-stu-id="affcb-125">Participants and reviewers:</span></span>

> <span data-ttu-id="affcb-126">**Майра Вензел (Maira Wenzel)** , старший руководитель программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-126">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="affcb-127">**Энди де Горже (Andy De Gorge)** , старший разработчик содержимого, группа разработчиков документации по .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-127">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="affcb-128">**Мигель Рамос (Miguel Ramos)** , старший руководитель программ, команда по платформе разработчиков Windows, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-128">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="affcb-129">**Адам Браден (Adam Braden)** , главный руководитель программ, команда платформы разработчиков Windows, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-129">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="affcb-130">**Рикардо Мингес Паблос (Ricardo Minguez Pablos)** , старший руководитель программ, команда Azure IoT, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-130">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="affcb-131">**Ниш Анил (Nish Anil)** , старший менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-131">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="affcb-132">**Бет Масси (Beth Massi)** , старший менеджер по маркетингу продукции, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-132">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="affcb-133">**Скотт Хантер (Scott Hunter)** , помощник главного руководителя программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="affcb-133">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="affcb-134">**Марта Фуэнтес Лара (Marta Fuentes Lara)** , Kabel</span><span class="sxs-lookup"><span data-stu-id="affcb-134">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="affcb-135">**Рауль Фернандес де Кордоба (Raúl Fernández de Córdoba)** , Kabel</span><span class="sxs-lookup"><span data-stu-id="affcb-135">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="affcb-136">**Сан Антонио Мануэль Фернáндес Кантос (Antonio Manuel Fernández Cantos)** , Kabel</span><span class="sxs-lookup"><span data-stu-id="affcb-136">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="affcb-137">Вступление</span><span class="sxs-lookup"><span data-stu-id="affcb-137">Introduction</span></span>

<span data-ttu-id="affcb-138">Эта книга посвящена стратегиям, которые можно реализовать в целях модернизации существующих классических настольных приложений и внедрения новейших возможностей среды выполнения, языка и платформы.</span><span class="sxs-lookup"><span data-stu-id="affcb-138">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="affcb-139">Вы поймете, что уникальной методики нет, так как каждое приложение имеет свои особенности, а у вас есть собственные требования и предпочтения.</span><span class="sxs-lookup"><span data-stu-id="affcb-139">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="affcb-140">Хорошо, что существуют общие подходы, которые можно применять для добавления новых функций и возможностей в приложения.</span><span class="sxs-lookup"><span data-stu-id="affcb-140">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="affcb-141">Для внедрения некоторых из них даже не потребуется вносить значительные изменения в код.</span><span class="sxs-lookup"><span data-stu-id="affcb-141">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="affcb-142">В этой книге мы расскажем о работе всех этих функций в фоновом режиме и объясним механизм их реализации.</span><span class="sxs-lookup"><span data-stu-id="affcb-142">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="affcb-143">Кроме того, вы ознакомитесь с рядом стандартных сценариев модернизации существующих классических приложений, которые помогут вам совершенствовать ваши собственные проекты.</span><span class="sxs-lookup"><span data-stu-id="affcb-143">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="affcb-144">Подход корпорации Майкрософт к модернизации существующих приложений заключается в том, чтобы предоставить вам гибкие возможности для создания собственного настраиваемого решения.</span><span class="sxs-lookup"><span data-stu-id="affcb-144">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="affcb-145">Все стратегии модернизации, описанные в этой книге, являются в основном независимыми.</span><span class="sxs-lookup"><span data-stu-id="affcb-145">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="affcb-146">Вы можете выбрать те, которые подходят для вашего приложения, и не обращать внимания на другие.</span><span class="sxs-lookup"><span data-stu-id="affcb-146">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="affcb-147">Иными словами, вы можете отобрать необходимые стратегии в нужном сочетании, которое лучше всего соответствует требованиям вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="affcb-147">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="affcb-148">Для кого предназначена эта книга</span><span class="sxs-lookup"><span data-stu-id="affcb-148">Who should use the book</span></span>

<span data-ttu-id="affcb-149">Эта книга — для разработчиков и архитекторов решений, стремящихся модернизировать существующие приложения Windows Forms и классические приложения WPF, чтобы использовать преимущества .NET и Windows 10.</span><span class="sxs-lookup"><span data-stu-id="affcb-149">This book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET and Windows 10.</span></span>

<span data-ttu-id="affcb-150">Эта книга также может оказаться полезной тем, кто принимает технические решения, например архитекторам корпоративных систем, ведущим разработчикам или руководителям, желающим получить представление о преимуществах обновления существующих классических приложений.</span><span class="sxs-lookup"><span data-stu-id="affcb-150">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="affcb-151">Как пользоваться книгой</span><span class="sxs-lookup"><span data-stu-id="affcb-151">How to use the book</span></span>

<span data-ttu-id="affcb-152">Книга отвечает на вопрос о том, зачем модернизировать существующие приложения и какие конкретно преимущества вы получите при использовании NET и MSIX для этой цели.</span><span class="sxs-lookup"><span data-stu-id="affcb-152">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="affcb-153">Содержимое книги предназначено для архитекторов и лиц, принимающих технические решения, которые хотят получить общие сведения, но не ставят перед собой задачу детального изучения вопросов реализации и технических особенностей.</span><span class="sxs-lookup"><span data-stu-id="affcb-153">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="affcb-154">В различных главах приводятся примеры фрагментов кода реализации и снимки экранов, а в главе 5 демонстрируется полный процесс миграции на примере нескольких приложений.</span><span class="sxs-lookup"><span data-stu-id="affcb-154">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="affcb-155">Темы, которые выходят за рамки этой книги</span><span class="sxs-lookup"><span data-stu-id="affcb-155">What this book doesn't cover</span></span>

<span data-ttu-id="affcb-156">В этой книге рассматривается конкретное подмножество сценариев миграции по принципу lift-and-shift, а также определяется вариант получения преимуществ модернизации без переписывания кода.</span><span class="sxs-lookup"><span data-stu-id="affcb-156">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="affcb-157">Книга не посвящена разработке на .NET современных приложений с нуля или началу работы с Windows Forms и WPF.</span><span class="sxs-lookup"><span data-stu-id="affcb-157">This book isn't about developing modern applications with .NET from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="affcb-158">Она акцентируется на обновлении существующих классических приложений с помощью новейших технологий для разработки классических приложений.</span><span class="sxs-lookup"><span data-stu-id="affcb-158">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="affcb-159">Примеры, используемые в этой книге</span><span class="sxs-lookup"><span data-stu-id="affcb-159">Samples used in this book</span></span>

<span data-ttu-id="affcb-160">Чтобы выделить необходимые этапы проведения модернизации, мы будем использовать пример приложения с именем `eShopModernizing`.</span><span class="sxs-lookup"><span data-stu-id="affcb-160">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="affcb-161">У этого приложения есть два варианта — для Windows Forms и WPF, и мы пошагово продемонстрируем модернизацию каждого из них для .NET.</span><span class="sxs-lookup"><span data-stu-id="affcb-161">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET.</span></span>

<span data-ttu-id="affcb-162">Кроме того, если вы решите пройти пошаговое руководство, вы сможете узнать результаты процесса в репозитории GitHub.</span><span class="sxs-lookup"><span data-stu-id="affcb-162">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="affcb-163">Отправить отзыв</span><span class="sxs-lookup"><span data-stu-id="affcb-163">Send your feedback</span></span>

<span data-ttu-id="affcb-164">Эта книга и примеры постоянно дополняются, поэтому мы ждем ваших отзывов.</span><span class="sxs-lookup"><span data-stu-id="affcb-164">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="affcb-165">Если у вас есть комментарии о том, как можно улучшить эту книгу, используйте раздел отзывов в нижней части любой страницы, созданный на основе [проблем GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="affcb-165">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="affcb-166">Вперед</span><span class="sxs-lookup"><span data-stu-id="affcb-166">Next</span></span>](why-modern-applications.md)
