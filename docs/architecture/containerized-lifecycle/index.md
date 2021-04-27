---
title: Жизненный цикл контейнерного приложения Docker на основе платформы и средств Майкрософт
description: Общий обзор процесса разработки и развертывания контейнерных приложений с помощью Docker, а также платформы и средств Microsoft.
ms.date: 01/06/2021
ms.openlocfilehash: 0b3c12800108eda84241252f32c6f54adb99e481
ms.sourcegitcommit: 02cc87f02c46e603ea5925de95af746b7ab46a35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2021
ms.locfileid: "107954735"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="6a49b-103">Жизненный цикл контейнерного приложения Docker на основе платформы и средств Майкрософт</span><span class="sxs-lookup"><span data-stu-id="6a49b-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![Обложка книги](./media/devops-book-cover-large-we.png)

<span data-ttu-id="6a49b-105">**Выпуск 5.0** — обновлен до ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="6a49b-105">**EDITION v5.0** - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="6a49b-106">Обновления книги и вклад сообщества см. в [журнале изменений](https://aka.ms/DockerLifecycleEbookChangelog).</span><span class="sxs-lookup"><span data-stu-id="6a49b-106">Refer [changelog](https://aka.ms/DockerLifecycleEbookChangelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="6a49b-107">В этом руководстве приводится общее описание процесса разработки и развертывания контейнерных приложений ASP.NET Core с помощью Docker с использованием платформы и средств Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="6a49b-107">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="6a49b-108">В этом руководстве представлено общее описание Azure DevOps для реализации конвейеров CI/CD, а также реестра контейнеров Azure (ACR) и Службы Azure Kubernetes (AKS) для развертывания.</span><span class="sxs-lookup"><span data-stu-id="6a49b-108">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="6a49b-109">Подробные сведения о разработке см. в руководстве [Микрослужбы .NET: архитектура для контейнерных приложений .NET](../microservices/index.md) и связанном с ним примере приложения [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="6a49b-109">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](../microservices/index.md) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="6a49b-110">Отправьте нам свой отзыв.</span><span class="sxs-lookup"><span data-stu-id="6a49b-110">Send us your feedback!</span></span>

<span data-ttu-id="6a49b-111">Мы создали это руководство, чтобы помочь вам разобраться в архитектуре контейнерных приложений и микрослужб в .NET.</span><span class="sxs-lookup"><span data-stu-id="6a49b-111">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="6a49b-112">Руководство и связанный с ним пример приложения будут развиваться, поэтому мы будем рады вашим отзывам!</span><span class="sxs-lookup"><span data-stu-id="6a49b-112">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="6a49b-113">Если у вас есть замечания касательно того, как можно улучшить это руководство, направляйте ваши отзывы по адресу <https://aka.ms/ebookfeedback>.</span><span class="sxs-lookup"><span data-stu-id="6a49b-113">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="6a49b-114">Благодарности</span><span class="sxs-lookup"><span data-stu-id="6a49b-114">Credits</span></span>

<span data-ttu-id="6a49b-115">Автор:</span><span class="sxs-lookup"><span data-stu-id="6a49b-115">Author:</span></span>

> <span data-ttu-id="6a49b-116">**Сезар де ла Торре (Cesar de la Torre)** , старший руководитель проекта, команда разработки .NET, корпорация Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="6a49b-116">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="6a49b-117">Редактор по приобретениям:</span><span class="sxs-lookup"><span data-stu-id="6a49b-117">Acquisitions Editor:</span></span>

> <span data-ttu-id="6a49b-118">**Джанин Патрик (Janine Patrick)**</span><span class="sxs-lookup"><span data-stu-id="6a49b-118">**Janine Patrick**</span></span>

<span data-ttu-id="6a49b-119">Редактор по разработкам:</span><span class="sxs-lookup"><span data-stu-id="6a49b-119">Developmental Editor:</span></span>

> <span data-ttu-id="6a49b-120">**Боб Рассел (Bob Russell)** , специалист по решениям в корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="6a49b-120">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="6a49b-121">**Octal Publishing, Inc.**</span><span class="sxs-lookup"><span data-stu-id="6a49b-121">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="6a49b-122">Редакционная колонка:</span><span class="sxs-lookup"><span data-stu-id="6a49b-122">Editorial Production:</span></span>

> [<span data-ttu-id="6a49b-123">Дайэнн Рассел (Dianne Russell)</span><span class="sxs-lookup"><span data-stu-id="6a49b-123">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="6a49b-124">**Octal Publishing, Inc.**</span><span class="sxs-lookup"><span data-stu-id="6a49b-124">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="6a49b-125">Выпускающий редактор:</span><span class="sxs-lookup"><span data-stu-id="6a49b-125">Copyeditor:</span></span>

> <span data-ttu-id="6a49b-126">**Боб Рассел (Bob Russell)** , специалист по решениям в корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="6a49b-126">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="6a49b-127">Участники и рецензенты:</span><span class="sxs-lookup"><span data-stu-id="6a49b-127">Participants and reviewers:</span></span>

> <span data-ttu-id="6a49b-128">**Ниш Анил (Nish Anil)** , старший менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="6a49b-128">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="6a49b-129">**Мигель Велосо** (Miguel Veloso), инженер по разработке программного обеспечения в Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="6a49b-129">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="6a49b-130">**Самит Гош (Sumit Ghosh)** , главный консультант в Neudesic</span><span class="sxs-lookup"><span data-stu-id="6a49b-130">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>
>
> <span data-ttu-id="6a49b-131">**Колин Дембовски (Colin Dembovsky)** , руководитель по применению DevOps, Cognizant Microsoft Business Group</span><span class="sxs-lookup"><span data-stu-id="6a49b-131">**Colin Dembovsky**, DevOps Practice Lead, Cognizant Microsoft Business Group</span></span>

## <a name="copyright"></a><span data-ttu-id="6a49b-132">Copyright</span><span class="sxs-lookup"><span data-stu-id="6a49b-132">Copyright</span></span>

<span data-ttu-id="6a49b-133">ИЗДАТЕЛЬ</span><span class="sxs-lookup"><span data-stu-id="6a49b-133">PUBLISHED BY</span></span>

<span data-ttu-id="6a49b-134">Подразделение Microsoft Developer Division, команды разработки .NET и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6a49b-134">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="6a49b-135">Подразделение корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="6a49b-135">A division of Microsoft Corporation</span></span>

<span data-ttu-id="6a49b-136">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="6a49b-136">One Microsoft Way</span></span>

<span data-ttu-id="6a49b-137">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="6a49b-137">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="6a49b-138">&copy; Корпорация Майкрософт (Microsoft Corporation), 2021.</span><span class="sxs-lookup"><span data-stu-id="6a49b-138">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="6a49b-139">Все права защищены.</span><span class="sxs-lookup"><span data-stu-id="6a49b-139">All rights reserved.</span></span> <span data-ttu-id="6a49b-140">Запрещается полное или частичное воспроизведение или передача настоящей книги в любом виде или любыми средствами без письменного разрешения издателя.</span><span class="sxs-lookup"><span data-stu-id="6a49b-140">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="6a49b-141">Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора.</span><span class="sxs-lookup"><span data-stu-id="6a49b-141">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="6a49b-142">Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.</span><span class="sxs-lookup"><span data-stu-id="6a49b-142">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="6a49b-143">Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными.</span><span class="sxs-lookup"><span data-stu-id="6a49b-143">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="6a49b-144">Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.</span><span class="sxs-lookup"><span data-stu-id="6a49b-144">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="6a49b-145">Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="6a49b-145">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="6a49b-146">Mac и macOS являются товарными знаками Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="6a49b-146">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="6a49b-147">Логотип Docker с изображением кита является зарегистрированным товарным знаком Docker, Inc. Используется с разрешения.</span><span class="sxs-lookup"><span data-stu-id="6a49b-147">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="6a49b-148">Все другие наименования и логотипы являются собственностью своих законных владельцев.</span><span class="sxs-lookup"><span data-stu-id="6a49b-148">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="6a49b-149">Вперед</span><span class="sxs-lookup"><span data-stu-id="6a49b-149">Next</span></span>](introduction-to-containers-and-docker.md)
