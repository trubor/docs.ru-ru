---
title: Жизненный цикл контейнерного приложения Docker на основе платформы и средств Майкрософт
description: Общий обзор процесса разработки и развертывания контейнерных приложений с помощью Docker, а также платформы и средств Microsoft.
ms.date: 01/06/2021
ms.openlocfilehash: 94c277e349bacee9b9fc7b160043005dd4135958
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970119"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="ea62c-103">Жизненный цикл контейнерного приложения Docker на основе платформы и средств Майкрософт</span><span class="sxs-lookup"><span data-stu-id="ea62c-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![Обложка книги](./media/devops-book-cover-large-we.png)

<span data-ttu-id="ea62c-105">**Выпуск 5.0** — обновлен до ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="ea62c-105">**EDITION v5.0** - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="ea62c-106">Обновления книги и вклад сообщества см. в [журнале изменений](https://aka.ms/DockerLifecycleEbookChangelog).</span><span class="sxs-lookup"><span data-stu-id="ea62c-106">Refer [changelog](https://aka.ms/DockerLifecycleEbookChangelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="ea62c-107">В этом руководстве приводится общее описание процесса разработки и развертывания контейнерных приложений ASP.NET Core с помощью Docker с использованием платформы и средств Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="ea62c-107">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="ea62c-108">В этом руководстве представлено общее описание Azure DevOps для реализации конвейеров CI/CD, а также реестра контейнеров Azure (ACR) и Службы Azure Kubernetes (AKS) для развертывания.</span><span class="sxs-lookup"><span data-stu-id="ea62c-108">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="ea62c-109">Подробные сведения о разработке см. в руководстве [Микрослужбы .NET: архитектура для контейнерных приложений .NET](../microservices/index.md) и связанном с ним примере приложения [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="ea62c-109">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](../microservices/index.md) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="ea62c-110">Отправьте нам свой отзыв.</span><span class="sxs-lookup"><span data-stu-id="ea62c-110">Send us your feedback!</span></span>

<span data-ttu-id="ea62c-111">Мы создали это руководство, чтобы помочь вам разобраться в архитектуре контейнерных приложений и микрослужб в .NET.</span><span class="sxs-lookup"><span data-stu-id="ea62c-111">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="ea62c-112">Руководство и связанный с ним пример приложения будут развиваться, поэтому мы будем рады вашим отзывам!</span><span class="sxs-lookup"><span data-stu-id="ea62c-112">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="ea62c-113">Если у вас есть замечания касательно того, как можно улучшить это руководство, направляйте ваши отзывы по адресу <https://aka.ms/ebookfeedback>.</span><span class="sxs-lookup"><span data-stu-id="ea62c-113">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="ea62c-114">Благодарности</span><span class="sxs-lookup"><span data-stu-id="ea62c-114">Credits</span></span>

<span data-ttu-id="ea62c-115">Автор:</span><span class="sxs-lookup"><span data-stu-id="ea62c-115">Author:</span></span>

> <span data-ttu-id="ea62c-116">**Сезар де ла Торре (Cesar de la Torre)** , старший руководитель проекта, команда разработки .NET, корпорация Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="ea62c-116">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="ea62c-117">Редактор по приобретениям:</span><span class="sxs-lookup"><span data-stu-id="ea62c-117">Acquisitions Editor:</span></span>

> <span data-ttu-id="ea62c-118">**Джанин Патрик (Janine Patrick)**</span><span class="sxs-lookup"><span data-stu-id="ea62c-118">**Janine Patrick**</span></span>

<span data-ttu-id="ea62c-119">Редактор по разработкам:</span><span class="sxs-lookup"><span data-stu-id="ea62c-119">Developmental Editor:</span></span>

> <span data-ttu-id="ea62c-120">**Боб Рассел (Bob Russell)** , специалист по решениям в корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="ea62c-120">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="ea62c-121">**Octal Publishing, Inc.**</span><span class="sxs-lookup"><span data-stu-id="ea62c-121">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="ea62c-122">Редакционная колонка:</span><span class="sxs-lookup"><span data-stu-id="ea62c-122">Editorial Production:</span></span>

> [<span data-ttu-id="ea62c-123">Дайэнн Рассел (Dianne Russell)</span><span class="sxs-lookup"><span data-stu-id="ea62c-123">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="ea62c-124">**Octal Publishing, Inc.**</span><span class="sxs-lookup"><span data-stu-id="ea62c-124">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="ea62c-125">Выпускающий редактор:</span><span class="sxs-lookup"><span data-stu-id="ea62c-125">Copyeditor:</span></span>

> <span data-ttu-id="ea62c-126">**Боб Рассел (Bob Russell)** , специалист по решениям в корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="ea62c-126">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="ea62c-127">Участники и рецензенты:</span><span class="sxs-lookup"><span data-stu-id="ea62c-127">Participants and reviewers:</span></span>

> <span data-ttu-id="ea62c-128">**Ниш Анил (Nish Anil)** , старший менеджер программ, команда .NET, корпорация Майкрософт</span><span class="sxs-lookup"><span data-stu-id="ea62c-128">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="ea62c-129">**Мигель Велосо** (Miguel Veloso), инженер по разработке программного обеспечения в Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="ea62c-129">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="ea62c-130">**Самит Гош (Sumit Ghosh)** , главный консультант в Neudesic</span><span class="sxs-lookup"><span data-stu-id="ea62c-130">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="ea62c-131">Copyright</span><span class="sxs-lookup"><span data-stu-id="ea62c-131">Copyright</span></span>

<span data-ttu-id="ea62c-132">ИЗДАТЕЛЬ</span><span class="sxs-lookup"><span data-stu-id="ea62c-132">PUBLISHED BY</span></span>

<span data-ttu-id="ea62c-133">Подразделение Microsoft Developer Division, команды разработки .NET и Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ea62c-133">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="ea62c-134">Подразделение корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="ea62c-134">A division of Microsoft Corporation</span></span>

<span data-ttu-id="ea62c-135">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="ea62c-135">One Microsoft Way</span></span>

<span data-ttu-id="ea62c-136">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="ea62c-136">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="ea62c-137">&copy; Корпорация Майкрософт (Microsoft Corporation), 2021.</span><span class="sxs-lookup"><span data-stu-id="ea62c-137">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="ea62c-138">Все права защищены.</span><span class="sxs-lookup"><span data-stu-id="ea62c-138">All rights reserved.</span></span> <span data-ttu-id="ea62c-139">Запрещается полное или частичное воспроизведение или передача настоящей книги в любом виде или любыми средствами без письменного разрешения издателя.</span><span class="sxs-lookup"><span data-stu-id="ea62c-139">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="ea62c-140">Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора.</span><span class="sxs-lookup"><span data-stu-id="ea62c-140">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="ea62c-141">Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.</span><span class="sxs-lookup"><span data-stu-id="ea62c-141">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="ea62c-142">Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными.</span><span class="sxs-lookup"><span data-stu-id="ea62c-142">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="ea62c-143">Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.</span><span class="sxs-lookup"><span data-stu-id="ea62c-143">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="ea62c-144">Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="ea62c-144">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="ea62c-145">Mac и macOS являются товарными знаками Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="ea62c-145">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="ea62c-146">Логотип Docker с изображением кита является зарегистрированным товарным знаком Docker, Inc. Используется с разрешения.</span><span class="sxs-lookup"><span data-stu-id="ea62c-146">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="ea62c-147">Все другие наименования и логотипы являются собственностью своих законных владельцев.</span><span class="sxs-lookup"><span data-stu-id="ea62c-147">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="ea62c-148">Вперед</span><span class="sxs-lookup"><span data-stu-id="ea62c-148">Next</span></span>](introduction-to-containers-and-docker.md)
