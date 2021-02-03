---
title: Приложения-кандидаты для машинного кода в облаке
description: Узнайте, какие типы приложений пользуются преимуществами собственного облачного подхода.
author: robvet
ms.date: 01/19/2021
ms.openlocfilehash: 443a7c1a1aaef078b33f352f597b33b768d989a3
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506192"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="6f72f-103">Приложения-кандидаты для машинного кода в облаке</span><span class="sxs-lookup"><span data-stu-id="6f72f-103">Candidate apps for cloud native</span></span>

<span data-ttu-id="6f72f-104">Просмотрите приложения в портфеле.</span><span class="sxs-lookup"><span data-stu-id="6f72f-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="6f72f-105">Сколько из них соответствует архитектуре, присущей облачным архитектурам?</span><span class="sxs-lookup"><span data-stu-id="6f72f-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="6f72f-106">Все они?</span><span class="sxs-lookup"><span data-stu-id="6f72f-106">All of them?</span></span> <span data-ttu-id="6f72f-107">Возможно, некоторые?</span><span class="sxs-lookup"><span data-stu-id="6f72f-107">Perhaps some?</span></span>

<span data-ttu-id="6f72f-108">Применяя анализ затрат и преимуществ, существует хороший шанс, что большинство не будут поддерживать тег цены недорого, необходимый для работы в облаке.</span><span class="sxs-lookup"><span data-stu-id="6f72f-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="6f72f-109">Стоимость облачного машинного кода значительно превышает бизнес-ценность приложения.</span><span class="sxs-lookup"><span data-stu-id="6f72f-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="6f72f-110">Какой тип приложения может быть кандидатом для машинного кода в облаке?</span><span class="sxs-lookup"><span data-stu-id="6f72f-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="6f72f-111">Стратегическая Корпоративная система, которая должна постоянно развивать бизнес-возможности и функции</span><span class="sxs-lookup"><span data-stu-id="6f72f-111">Strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="6f72f-112">Приложение, для которого требуется высокая скорость выпуска с высокой достоверностью</span><span class="sxs-lookup"><span data-stu-id="6f72f-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="6f72f-113">Система, в которой отдельные компоненты должны выпустить *без* полного повторного развертывания всей системы.</span><span class="sxs-lookup"><span data-stu-id="6f72f-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="6f72f-114">Приложение, разработанное группами с опытом в различных технологических стеках</span><span class="sxs-lookup"><span data-stu-id="6f72f-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="6f72f-115">Приложение с компонентами, которые должны масштабироваться независимо друг от друга</span><span class="sxs-lookup"><span data-stu-id="6f72f-115">An application with components that must scale independently</span></span>

<span data-ttu-id="6f72f-116">Тогда существуют устаревшие системы.</span><span class="sxs-lookup"><span data-stu-id="6f72f-116">Then there are legacy systems.</span></span> <span data-ttu-id="6f72f-117">Хотя мы бы хотели создавать новые приложения, мы часто ответственны за модернизации устаревшие рабочие нагрузки, которые важны для бизнеса.</span><span class="sxs-lookup"><span data-stu-id="6f72f-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="6f72f-118">Со временем устаревшее приложение можно разделить на микрослужбы, контейнеры и в конечном итоге "реплатформенные" в архитектуру, собственную в облаке.</span><span class="sxs-lookup"><span data-stu-id="6f72f-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="6f72f-119">Устаревшие приложения модернизации</span><span class="sxs-lookup"><span data-stu-id="6f72f-119">Modernizing legacy apps</span></span>

<span data-ttu-id="6f72f-120">Бесплатная электронная книга Microsoft модернизировать. [существующие приложения .NET с контейнерами Azure Cloud и Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) предоставляют рекомендации по переносу локальных рабочих нагрузок в облако.</span><span class="sxs-lookup"><span data-stu-id="6f72f-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="6f72f-121">На рис. 1-10 показано, что для модернизации устаревших приложений не существует отдельной стратегии "один размер".</span><span class="sxs-lookup"><span data-stu-id="6f72f-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Стратегии переноса устаревших рабочих нагрузок](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="6f72f-123">**Рис. 1-10**.</span><span class="sxs-lookup"><span data-stu-id="6f72f-123">**Figure 1-10**.</span></span> <span data-ttu-id="6f72f-124">Стратегии переноса устаревших рабочих нагрузок</span><span class="sxs-lookup"><span data-stu-id="6f72f-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="6f72f-125">Монолитные приложения, которые не являются критически важными, значительно отличаются от быстрых и сменных ([готовых к облачным инфраструктурам](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) миграций.</span><span class="sxs-lookup"><span data-stu-id="6f72f-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="6f72f-126">Здесь локальная рабочая нагрузка перемещается на облачную виртуальную машину без изменений.</span><span class="sxs-lookup"><span data-stu-id="6f72f-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="6f72f-127">Этот подход использует [модель IaaS (инфраструктура как услуга)](https://azure.microsoft.com/overview/what-is-iaas/).</span><span class="sxs-lookup"><span data-stu-id="6f72f-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="6f72f-128">Azure включает несколько средств, таких как [Миграция Azure](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)и [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) , чтобы упростить такой переход.</span><span class="sxs-lookup"><span data-stu-id="6f72f-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="6f72f-129">Хотя эта стратегия может привести к снижению затрат, такие приложения, как правило, не были спроектированы для разблокировки и использования преимуществ облачных вычислений.</span><span class="sxs-lookup"><span data-stu-id="6f72f-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="6f72f-130">Монолитные приложения, которые являются критически важными для бизнеса, имеют преимущество благодаря расширенной миграции с прогнозированием и сдвигом (*оптимизированным для облака*).</span><span class="sxs-lookup"><span data-stu-id="6f72f-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="6f72f-131">Этот подход включает оптимизацию развертывания, включающую ключевые облачные службы, без изменения основной архитектуры приложения.</span><span class="sxs-lookup"><span data-stu-id="6f72f-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="6f72f-132">Например, вы можете [контейнеризовать](/virtualization/windowscontainers/about/) приложение и развернуть его в контейнере Orchestrator, например в [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), который обсуждается далее в этой книге.</span><span class="sxs-lookup"><span data-stu-id="6f72f-132">For example, you might [containerize](/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="6f72f-133">В облаке приложение может использовать другие облачные службы, такие как базы данных, очереди сообщений, мониторинг и распределенное кэширование.</span><span class="sxs-lookup"><span data-stu-id="6f72f-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="6f72f-134">Наконец, монолитные приложения, выполняющие стратегические корпоративные функции, могут получить лучшие преимущества от *облачного* подхода, темы этой книги.</span><span class="sxs-lookup"><span data-stu-id="6f72f-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="6f72f-135">Такой подход обеспечивает гибкость и скорость.</span><span class="sxs-lookup"><span data-stu-id="6f72f-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="6f72f-136">Но он поступает за счет реконструирования, перепроектирования и перезаписи кода.</span><span class="sxs-lookup"><span data-stu-id="6f72f-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="6f72f-137">Если вы и ваша команда предполагают, что подход в облаке является оптимальным, он наполнения вам, чтобы вы рационализироватье решение в Организации.</span><span class="sxs-lookup"><span data-stu-id="6f72f-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="6f72f-138">Какова именно бизнес-проблема, которую будет решать облачный подход?</span><span class="sxs-lookup"><span data-stu-id="6f72f-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="6f72f-139">Как она будет совпадать с бизнес-потребностями?</span><span class="sxs-lookup"><span data-stu-id="6f72f-139">How would it align with business needs?</span></span>

- <span data-ttu-id="6f72f-140">Быстрые выпуски функций с повышенной достоверностью?</span><span class="sxs-lookup"><span data-stu-id="6f72f-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="6f72f-141">Детализированная масштабируемость — более эффективное использование ресурсов?</span><span class="sxs-lookup"><span data-stu-id="6f72f-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="6f72f-142">Улучшена устойчивость системы?</span><span class="sxs-lookup"><span data-stu-id="6f72f-142">Improved system resiliency?</span></span>

- <span data-ttu-id="6f72f-143">Повысилась производительность системы?</span><span class="sxs-lookup"><span data-stu-id="6f72f-143">Improved system performance?</span></span>

- <span data-ttu-id="6f72f-144">Больше видимости операций?</span><span class="sxs-lookup"><span data-stu-id="6f72f-144">More visibility into operations?</span></span>

- <span data-ttu-id="6f72f-145">Смешиваете платформы разработки и хранилища данных, поступающие в лучшее средство для задания?</span><span class="sxs-lookup"><span data-stu-id="6f72f-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="6f72f-146">Поэкспериментировать с приложениями в будущем?</span><span class="sxs-lookup"><span data-stu-id="6f72f-146">Future-proof application investment?</span></span>

<span data-ttu-id="6f72f-147">Правая стратегия миграции зависит от приоритетов Организации и целевых систем.</span><span class="sxs-lookup"><span data-stu-id="6f72f-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="6f72f-148">Многие из них могут быть более экономичными для оптимизации приложений в облаке или для добавления недетализированных служб в N-уровневое приложение.</span><span class="sxs-lookup"><span data-stu-id="6f72f-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="6f72f-149">В таких случаях вы все равно можете полностью использовать облачные возможности PaaS, такие как службы приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="6f72f-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="6f72f-150">Итоги</span><span class="sxs-lookup"><span data-stu-id="6f72f-150">Summary</span></span>

<span data-ttu-id="6f72f-151">В этой главе мы предоставили облачные вычисления.</span><span class="sxs-lookup"><span data-stu-id="6f72f-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="6f72f-152">Мы предоставили определение вместе с основными возможностями, которые позволяют управлять облачными приложениями.</span><span class="sxs-lookup"><span data-stu-id="6f72f-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="6f72f-153">Мы рассматривали типы приложений, которые могут выровнять инвестиции и усилия.</span><span class="sxs-lookup"><span data-stu-id="6f72f-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="6f72f-154">С введением мы теперь рассмотрим более подробный обзор облачной машинной части.</span><span class="sxs-lookup"><span data-stu-id="6f72f-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="6f72f-155">Ссылки</span><span class="sxs-lookup"><span data-stu-id="6f72f-155">References</span></span>

- [<span data-ttu-id="6f72f-156">Облачная машинная базовая вычислительная среда</span><span class="sxs-lookup"><span data-stu-id="6f72f-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="6f72f-157">Микрослужбы .NET: архитектура контейнерных приложений .NET</span><span class="sxs-lookup"><span data-stu-id="6f72f-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="6f72f-158">Модернизация существующих приложений .NET с помощью облака Azure и контейнеров Windows</span><span class="sxs-lookup"><span data-stu-id="6f72f-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="6f72f-159">Собственные шаблоны в облаке по Корнелиа Дэвис</span><span class="sxs-lookup"><span data-stu-id="6f72f-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="6f72f-160">За пределами приложения Twelve-Factor</span><span class="sxs-lookup"><span data-stu-id="6f72f-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="6f72f-161">Что такое инфраструктура как код</span><span class="sxs-lookup"><span data-stu-id="6f72f-161">What is Infrastructure as Code</span></span>](/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="6f72f-162">Микроразвертывание Uber инженера: ежедневное развертывание с уверенностью</span><span class="sxs-lookup"><span data-stu-id="6f72f-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="6f72f-163">Как Netflix развертывает код</span><span class="sxs-lookup"><span data-stu-id="6f72f-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="6f72f-164">Элемент управления перегрузкой для масштабирования микрослужб WeChat</span><span class="sxs-lookup"><span data-stu-id="6f72f-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="6f72f-165">[Назад](definition.md)
>[Вперед](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="6f72f-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
