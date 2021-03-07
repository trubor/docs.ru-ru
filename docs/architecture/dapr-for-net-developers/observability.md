---
title: Стандартный блок наблюдаемых ДАПР
description: Описание стандартного блока наблюдаемых элементов, его функций, преимуществ и способов его применения
author: edwinvw
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: c7c941625f5867ad58eee602bfc42183bee87183
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401871"
---
# <a name="the-dapr-observability-building-block"></a><span data-ttu-id="3b131-103">Стандартный блок наблюдаемых ДАПР</span><span class="sxs-lookup"><span data-stu-id="3b131-103">The Dapr observability building block</span></span>

<span data-ttu-id="3b131-104">Современные распределенные системы являются сложными.</span><span class="sxs-lookup"><span data-stu-id="3b131-104">Modern distributed systems are complex.</span></span> <span data-ttu-id="3b131-105">Начнем с небольших, слабо связанных и независимо развертываемых служб.</span><span class="sxs-lookup"><span data-stu-id="3b131-105">You start with small, loosely coupled, independently deployable services.</span></span> <span data-ttu-id="3b131-106">Эти службы перекрестно обрабатывают границы серверов.</span><span class="sxs-lookup"><span data-stu-id="3b131-106">These services cross process and server boundaries.</span></span> <span data-ttu-id="3b131-107">Затем они используют различные виды резервных служб инфраструктуры (базы данных, брокеры сообщений, хранилища ключей).</span><span class="sxs-lookup"><span data-stu-id="3b131-107">They then consume different kinds of infrastructure backing services (databases, message brokers, key vaults).</span></span> <span data-ttu-id="3b131-108">Наконец, эти разнородные части соформируют приложение.</span><span class="sxs-lookup"><span data-stu-id="3b131-108">Finally, these disparate pieces compose together to form an application.</span></span>

<span data-ttu-id="3b131-109">Так как вы будете иметь представление о том, что происходит?</span><span class="sxs-lookup"><span data-stu-id="3b131-109">With so many separate, moving parts, how do you make sense of what is going on?</span></span> <span data-ttu-id="3b131-110">К сожалению, устаревшие подходы к мониторингу не достаточно.</span><span class="sxs-lookup"><span data-stu-id="3b131-110">Unfortunately, legacy monitoring approaches from the past aren't enough.</span></span> <span data-ttu-id="3b131-111">Вместо этого система должна быть **наблюдаемой** от начала до конца.</span><span class="sxs-lookup"><span data-stu-id="3b131-111">Instead, the system must be **observable** from end-to-end.</span></span> <span data-ttu-id="3b131-112">Современные методики [наблюдения](../cloud-native/observability-patterns.md) обеспечивают наглядное представление о работоспособности приложения.</span><span class="sxs-lookup"><span data-stu-id="3b131-112">Modern [observability](../cloud-native/observability-patterns.md) practices provide visibility and insight into the health of the application at all times.</span></span> <span data-ttu-id="3b131-113">Они позволяют определить внутреннее состояние, просматривая выходные данные.</span><span class="sxs-lookup"><span data-stu-id="3b131-113">They enable you to infer the internal state by observing the output.</span></span> <span data-ttu-id="3b131-114">Наблюдаемость является обязательной для мониторинга и устранения неполадок распределенных приложений.</span><span class="sxs-lookup"><span data-stu-id="3b131-114">Observability is mandatory for monitoring and troubleshooting distributed applications.</span></span>

<span data-ttu-id="3b131-115">Сведения о системе, используемые для получения наблюдаемых сведений, называются **телеметрии**.</span><span class="sxs-lookup"><span data-stu-id="3b131-115">The system information used to gain observability is referred to as **telemetry**.</span></span> <span data-ttu-id="3b131-116">Его можно разделить на четыре основные категории:</span><span class="sxs-lookup"><span data-stu-id="3b131-116">It can be divided into four broad categories:</span></span>

1. <span data-ttu-id="3b131-117">**Распределенная трассировка** позволяет понять трафик между службами и службами, вовлеченными в распределенные транзакции.</span><span class="sxs-lookup"><span data-stu-id="3b131-117">**Distributed tracing** provides insight into the traffic between services and services involved in distributed transactions.</span></span>
1. <span data-ttu-id="3b131-118">**Метрики** позволяют понять производительность службы и ее потребление ресурсов.</span><span class="sxs-lookup"><span data-stu-id="3b131-118">**Metrics** provides insight into the performance of a service and its resource consumption.</span></span>
1. <span data-ttu-id="3b131-119">**Ведение журнала** позволяет получить представление о том, как работает код, и при возникновении ошибок.</span><span class="sxs-lookup"><span data-stu-id="3b131-119">**Logging** provides insight into how the code is executing and if errors have occurred.</span></span>
1. <span data-ttu-id="3b131-120">Конечные точки **работоспособности** позволяют получить представление о доступности службы.</span><span class="sxs-lookup"><span data-stu-id="3b131-120">**Health** endpoints provide insight into the availability of a service.</span></span>

<span data-ttu-id="3b131-121">Глубина телеметрии определяется функциями наблюдаемой платформы приложения.</span><span class="sxs-lookup"><span data-stu-id="3b131-121">The depth of telemetry is determined by the observability features of an application platform.</span></span> <span data-ttu-id="3b131-122">Рассмотрим облако Azure.</span><span class="sxs-lookup"><span data-stu-id="3b131-122">Consider the Azure cloud.</span></span> <span data-ttu-id="3b131-123">Он предоставляет широкие возможности телеметрии, включая все категории телеметрии.</span><span class="sxs-lookup"><span data-stu-id="3b131-123">It provides a rich telemetry experience that includes all of the telemetry categories.</span></span> <span data-ttu-id="3b131-124">Без какой бы то ни было конфигурации Большинство служб Azure IaaS и PaaS распространяют и публикуют данные телеметрии в службе [Application Insights Azure](/azure/azure-monitor/app/app-insights-overview) .</span><span class="sxs-lookup"><span data-stu-id="3b131-124">Without any configuration, most Azure IaaS and PaaS services propagate and publish telemetry to the [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview) service.</span></span> <span data-ttu-id="3b131-125">Application Insights представляет области ведения журнала системы, отслеживания и проблем с высокой визуальной панелью мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-125">Application Insights presents system logging, tracing, and problem areas with highly visual dashboards.</span></span> <span data-ttu-id="3b131-126">Она может даже визуализировать схему, показывающую зависимости между службами на основе их взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="3b131-126">It can even render a diagram showing the dependencies between services based on their communication.</span></span>

<span data-ttu-id="3b131-127">Но что делать, если приложение не может использовать Azure PaaS и ресурсы IaaS?</span><span class="sxs-lookup"><span data-stu-id="3b131-127">However, what if an application can't use Azure PaaS and IaaS resources?</span></span> <span data-ttu-id="3b131-128">Можно ли по-прежнему использовать широкие возможности телеметрии Application Insights?</span><span class="sxs-lookup"><span data-stu-id="3b131-128">Is it still possible to take advantage of the rich telemetry experience of Application Insights?</span></span> <span data-ttu-id="3b131-129">Ответ — Да.</span><span class="sxs-lookup"><span data-stu-id="3b131-129">The answer is yes.</span></span> <span data-ttu-id="3b131-130">Приложение, не являющееся приложением Azure, может импортировать библиотеки, добавлять конфигурацию и инструментировать код для отправки телеметрии в Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="3b131-130">A non-Azure application can import libraries, add configuration, and instrument code to emit telemetry to Azure Application Insights.</span></span> <span data-ttu-id="3b131-131">Однако этот подход **тесно связывает** приложение с Application Insights.</span><span class="sxs-lookup"><span data-stu-id="3b131-131">However, this approach **tightly couples** the application to Application Insights.</span></span> <span data-ttu-id="3b131-132">Перемещение приложения на другую платформу мониторинга может привести к дорогостоящему рефакторингу.</span><span class="sxs-lookup"><span data-stu-id="3b131-132">Moving the app to a different monitoring platform could involve expensive refactoring.</span></span> <span data-ttu-id="3b131-133">Было бы неплохо избегать тесного связывания и использования наблюдаемых данных за пределами кода?</span><span class="sxs-lookup"><span data-stu-id="3b131-133">Wouldn't it be great to avoid tight coupling and consume observability outside of the code?</span></span>

<span data-ttu-id="3b131-134">С помощью ДАПР можно.</span><span class="sxs-lookup"><span data-stu-id="3b131-134">With Dapr, you can.</span></span> <span data-ttu-id="3b131-135">Рассмотрим, как ДАПР может добавить наблюдаемые возможности в распределенные приложения.</span><span class="sxs-lookup"><span data-stu-id="3b131-135">Let's look at how Dapr can add observability to our distributed applications.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="3b131-136">Решение</span><span class="sxs-lookup"><span data-stu-id="3b131-136">What it solves</span></span>

<span data-ttu-id="3b131-137">Стандартный блок наблюдаемости ДАПР разделяет наблюдаемость из приложения.</span><span class="sxs-lookup"><span data-stu-id="3b131-137">The Dapr observability building block decouples observability from the application.</span></span> <span data-ttu-id="3b131-138">Он автоматически захватывает трафик, созданный ДАПР сидекарс и ДАПР системными службами, которые составляют плоскость управления ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-138">It automatically captures traffic generated by Dapr sidecars and Dapr system services that make up the Dapr control plane.</span></span> <span data-ttu-id="3b131-139">Блок корреляции трафика от одной операции, охватывающей несколько служб.</span><span class="sxs-lookup"><span data-stu-id="3b131-139">The block correlates traffic from a single operation that spans multiple services.</span></span> <span data-ttu-id="3b131-140">Он также предоставляет метрики производительности, использование ресурсов и работоспособность системы.</span><span class="sxs-lookup"><span data-stu-id="3b131-140">It also exposes performance metrics, resource utilization, and the health of the system.</span></span> <span data-ttu-id="3b131-141">Данные телеметрии публикуются в формате с открытым стандартом, позволяя получать информацию в серверной части мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-141">Telemetry is published in open-standard formats enabling information to be fed into your monitoring back end of choice.</span></span> <span data-ttu-id="3b131-142">Там можно выполнять визуализацию, запрос и анализ данных.</span><span class="sxs-lookup"><span data-stu-id="3b131-142">There, the information can be visualized, queried, and analyzed.</span></span>

<span data-ttu-id="3b131-143">По мере того, как ДАПР абстрагирует процесс, приложение не знает, как реализована наблюдаемость.</span><span class="sxs-lookup"><span data-stu-id="3b131-143">As Dapr abstracts away the plumbing, the application is unaware of how observability is implemented.</span></span> <span data-ttu-id="3b131-144">Нет необходимости ссылаться на библиотеки или реализовывать пользовательский код инструментирования.</span><span class="sxs-lookup"><span data-stu-id="3b131-144">There's no need to reference libraries or implement custom instrumentation code.</span></span> <span data-ttu-id="3b131-145">ДАПР позволяет разработчику сосредоточиться на построении бизнес-логики, а не на контролируемости.</span><span class="sxs-lookup"><span data-stu-id="3b131-145">Dapr allows the developer to focus on building business logic and not observability plumbing.</span></span> <span data-ttu-id="3b131-146">Наблюдаемость настраивается на уровне ДАПР и согласована между службами, даже если она создана различными командами и построена с различными технологическими стеками.</span><span class="sxs-lookup"><span data-stu-id="3b131-146">Observability is configured at the Dapr level and is consistent across services, even when created by different teams, and built with different technology stacks.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="3b131-147">Принцип работы</span><span class="sxs-lookup"><span data-stu-id="3b131-147">How it works</span></span>

<span data-ttu-id="3b131-148">[Архитектура расширения](dapr-at-20000-feet.md#sidecar-architecture) ДАПР обеспечивает встроенные функции наблюдения.</span><span class="sxs-lookup"><span data-stu-id="3b131-148">Dapr's [sidecar architecture](dapr-at-20000-feet.md#sidecar-architecture) enables built-in observability features.</span></span> <span data-ttu-id="3b131-149">При взаимодействии служб ДАПР сидекарс перехватывает трафик и извлекает данные трассировки, метрики и ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="3b131-149">As services communicate, Dapr sidecars intercept the traffic and extract tracing, metrics, and logging information.</span></span> <span data-ttu-id="3b131-150">Данные телеметрии публикуются в формате Open Standard.</span><span class="sxs-lookup"><span data-stu-id="3b131-150">Telemetry is published in an open standards format.</span></span> <span data-ttu-id="3b131-151">По умолчанию ДАПР поддерживает [опентелеметри](https://opentelemetry.io/) и [зипкин](https://zipkin.io/).</span><span class="sxs-lookup"><span data-stu-id="3b131-151">By default, Dapr supports [OpenTelemetry](https://opentelemetry.io/) and [Zipkin](https://zipkin.io/).</span></span>

<span data-ttu-id="3b131-152">ДАПР предоставляет средства сбора данных, которые могут публиковать [данные](https://docs.dapr.io/operations/monitoring/open-telemetry-collector/) телеметрии для различных средств мониторинга серверной части.</span><span class="sxs-lookup"><span data-stu-id="3b131-152">Dapr provides [collectors](https://docs.dapr.io/operations/monitoring/open-telemetry-collector/) that can publish telemetry to different back-end monitoring tools.</span></span> <span data-ttu-id="3b131-153">Эти средства представляют данные телеметрии ДАПР для анализа и запросов.</span><span class="sxs-lookup"><span data-stu-id="3b131-153">These tools present Dapr telemetry for analysis and querying.</span></span> <span data-ttu-id="3b131-154">На рис. 9-1 показана архитектура наблюдаемых ДАПР:</span><span class="sxs-lookup"><span data-stu-id="3b131-154">Figure 9-1 shows the Dapr observability architecture:</span></span>

![Архитектура наблюдаемых ДАПР](media/observability/observability-architecture.png)

<span data-ttu-id="3b131-156">**Рис. 9-1**.</span><span class="sxs-lookup"><span data-stu-id="3b131-156">**Figure 9-1**.</span></span> <span data-ttu-id="3b131-157">Архитектура наблюдаемой ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-157">Dapr observability architecture.</span></span>

1. <span data-ttu-id="3b131-158">Служба а вызывает операцию в службе B. Вызов направляется от ДАПР расширения для службы A в расширения для службы б.</span><span class="sxs-lookup"><span data-stu-id="3b131-158">Service A calls an operation on Service B. The call is routed from a Dapr sidecar for Service A to a sidecar for Service B.</span></span>
1. <span data-ttu-id="3b131-159">Когда служба б завершает операцию, ответ отправляется обратно службе A через сидекарс ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-159">When Service B completes the operation, a response is sent back to Service A through the Dapr sidecars.</span></span> <span data-ttu-id="3b131-160">Они собирают и публикуют все доступные данные телеметрии для каждого запроса и ответа.</span><span class="sxs-lookup"><span data-stu-id="3b131-160">They gather and publish all available telemetry for every request and response.</span></span>
1. <span data-ttu-id="3b131-161">Настроенный сборщик принимает данные телеметрии и отправляет его в серверную части мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-161">The configured collector ingests the telemetry and sends it to the monitoring back end.</span></span>  

<span data-ttu-id="3b131-162">В качестве разработчика следует помнить, что добавление наблюдаемой среды отличается от настройки других стандартных блоков ДАПР, таких как публикация и подстройка или управление состоянием.</span><span class="sxs-lookup"><span data-stu-id="3b131-162">As a developer, keep in mind that adding observability is different from configuring other Dapr building blocks, like pub/sub or state management.</span></span> <span data-ttu-id="3b131-163">Вместо ссылки на стандартный блок необходимо добавить сборщик и серверную часть мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-163">Instead of referencing a building block, you add a collector and a monitoring back end.</span></span> <span data-ttu-id="3b131-164">На рис. 9-1 показано, как можно настроить несколько средств для объединения с разными серверными элементами мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-164">Figure 9-1 shows it's possible to configure multiple collectors that integrate with different monitoring back ends.</span></span>

<span data-ttu-id="3b131-165">В начале этой главы была обнаружена четыре категории телеметрии.</span><span class="sxs-lookup"><span data-stu-id="3b131-165">At the beginning of this chapter, four categories of telemetry were identified.</span></span> <span data-ttu-id="3b131-166">В следующих разделах приводятся подробные сведения о каждой категории.</span><span class="sxs-lookup"><span data-stu-id="3b131-166">The following sections will provide detail for each category.</span></span> <span data-ttu-id="3b131-167">Они включают инструкции по настройке средств для собраний, которые интегрируются с популярными серверными элементами мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-167">They'll include instruction on how to configure collectors that integrate with popular monitoring back ends.</span></span>

### <a name="distributed-tracing"></a><span data-ttu-id="3b131-168">Распределенная трассировка</span><span class="sxs-lookup"><span data-stu-id="3b131-168">Distributed tracing</span></span>

<span data-ttu-id="3b131-169">Распределенная трассировка позволяет понять трафик, который передается между службами в распределенном приложении.</span><span class="sxs-lookup"><span data-stu-id="3b131-169">Distributed tracing provides insight into the traffic that flows across services in a distributed application.</span></span> <span data-ttu-id="3b131-170">Журнал обменных сообщений запросов и ответов является ценным источником сведений для устранения неполадок.</span><span class="sxs-lookup"><span data-stu-id="3b131-170">The log of exchanged request and response messages is an invaluable source of information for troubleshooting issues.</span></span> <span data-ttu-id="3b131-171">Жесткая часть представляет собой *корреляцию сообщений* , происходящих из одной операции.</span><span class="sxs-lookup"><span data-stu-id="3b131-171">The hard part is *correlating messages* that originate from the same operation.</span></span>

<span data-ttu-id="3b131-172">ДАПР использует [контекст трассировки W3C](https://www.w3.org/TR/trace-context) для корреляции связанных сообщений.</span><span class="sxs-lookup"><span data-stu-id="3b131-172">Dapr uses the [W3C Trace Context](https://www.w3.org/TR/trace-context) to correlate related messages.</span></span> <span data-ttu-id="3b131-173">Он внедряет в запросы и ответы те же сведения о контексте, которые формируют уникальную операцию.</span><span class="sxs-lookup"><span data-stu-id="3b131-173">It injects the same context information into requests and responses that form a unique operation.</span></span> <span data-ttu-id="3b131-174">На рис. 9-2 показано, как работает корреляция.</span><span class="sxs-lookup"><span data-stu-id="3b131-174">Figure 9-2 shows how correlation works:</span></span>

![Пример контекста трассировки W3C](media/observability/w3c-trace-context.png)

<span data-ttu-id="3b131-176">**Рис. 9-2**.</span><span class="sxs-lookup"><span data-stu-id="3b131-176">**Figure 9-2**.</span></span> <span data-ttu-id="3b131-177">Пример контекста трассировки W3C.</span><span class="sxs-lookup"><span data-stu-id="3b131-177">W3C Trace Context example.</span></span>

1. <span data-ttu-id="3b131-178">Служба а вызывает операцию в службе B. Когда служба а запускает вызов, ДАПР создает уникальный контекст трассировки и внедряет его в запрос.</span><span class="sxs-lookup"><span data-stu-id="3b131-178">Service A invokes an operation on Service B. As Service A starts the call, Dapr creates a unique trace context and injects it into the request.</span></span>
1. <span data-ttu-id="3b131-179">Служба б получает запрос и вызывает операцию в службе C. ДАПР обнаруживает, что входящий запрос содержит контекст трассировки и распространяет его, добавляя его в исходящий запрос в службу C.</span><span class="sxs-lookup"><span data-stu-id="3b131-179">Service B receives the request and invokes an operation on Service C. Dapr detects that the incoming request contains a trace context and propagates it by injecting it into the outgoing request to Service C.</span></span>  
1. <span data-ttu-id="3b131-180">Служба C получает запрос и обрабатывает его.</span><span class="sxs-lookup"><span data-stu-id="3b131-180">Service C receives the request and handles it.</span></span> <span data-ttu-id="3b131-181">ДАПР обнаруживает, что входящий запрос содержит контекст трассировки и распространяет его, добавляя его в исходящий ответ обратно в службу B.</span><span class="sxs-lookup"><span data-stu-id="3b131-181">Dapr detects that the incoming request contains a trace context and propagates it by injecting it into the outgoing response back to Service B.</span></span>
1. <span data-ttu-id="3b131-182">Служба б получает ответ и обрабатывает его.</span><span class="sxs-lookup"><span data-stu-id="3b131-182">Service B receives the response and handles it.</span></span> <span data-ttu-id="3b131-183">Затем он создает новый ответ и распространяет контекст трассировки, внедряя его в исходящий ответ обратно в службу A.</span><span class="sxs-lookup"><span data-stu-id="3b131-183">It then creates a new response and propagates the trace context by injecting it into the outgoing response back to Service A.</span></span>

<span data-ttu-id="3b131-184">Набор запросов и ответов, входящих в состав, называется *трассировкой*.</span><span class="sxs-lookup"><span data-stu-id="3b131-184">A set of requests and responses that belong together is called a *trace*.</span></span> <span data-ttu-id="3b131-185">На рис. 9-3 показана трассировка:</span><span class="sxs-lookup"><span data-stu-id="3b131-185">Figure 9-3 shows a trace:</span></span>

![Трассировки и охваты](media/observability/traces-spans.png)

<span data-ttu-id="3b131-187">**Рис. 9-3**.</span><span class="sxs-lookup"><span data-stu-id="3b131-187">**Figure 9-3**.</span></span> <span data-ttu-id="3b131-188">Трассировки и охваты.</span><span class="sxs-lookup"><span data-stu-id="3b131-188">Traces and spans.</span></span>

<span data-ttu-id="3b131-189">На рисунке обратите внимание, что трассировка представляет собой уникальную транзакцию приложения, которая выполняется во многих службах.</span><span class="sxs-lookup"><span data-stu-id="3b131-189">In the figure, note how the trace represents a unique application transaction that takes place across many services.</span></span> <span data-ttu-id="3b131-190">Трассировка — это коллекция *диапазонов*.</span><span class="sxs-lookup"><span data-stu-id="3b131-190">A trace is a collection of *spans*.</span></span> <span data-ttu-id="3b131-191">Каждый диапазон представляет одну операцию или единицу работы, выполняемую в трассировке.</span><span class="sxs-lookup"><span data-stu-id="3b131-191">Each span represents a single operation or unit of work done within the trace.</span></span> <span data-ttu-id="3b131-192">Диапазоны — это запросы и ответы, которые передаются между службами, которые реализуют уникальную транзакцию.</span><span class="sxs-lookup"><span data-stu-id="3b131-192">Spans are the requests and responses that are sent between services that implement the unique transaction.</span></span>

<span data-ttu-id="3b131-193">В следующих разделах описано, как проверить данные телеметрии трассировки, опубликовав их в серверной части мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-193">The next sections discuss how to inspect tracing telemetry by publishing it to a monitoring back end.</span></span>

#### <a name="use-a-zipkin-monitoring-back-end"></a><span data-ttu-id="3b131-194">Использование серверной части Зипкин Monitoring</span><span class="sxs-lookup"><span data-stu-id="3b131-194">Use a Zipkin monitoring back end</span></span>

<span data-ttu-id="3b131-195">[Зипкин](https://zipkin.io/) — это распределенная система трассировки с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="3b131-195">[Zipkin](https://zipkin.io/) is an open-source distributed tracing system.</span></span> <span data-ttu-id="3b131-196">Он может принимать и визуализировать данные телеметрии.</span><span class="sxs-lookup"><span data-stu-id="3b131-196">It can ingest and visualize telemetry data.</span></span> <span data-ttu-id="3b131-197">ДАПР предлагает поддержку по умолчанию для Зипкин.</span><span class="sxs-lookup"><span data-stu-id="3b131-197">Dapr offers default support for Zipkin.</span></span> <span data-ttu-id="3b131-198">В следующем примере показано, как настроить Зипкин для визуализации телеметрии ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-198">The following example demonstrates how to configure Zipkin to visualize Dapr telemetry.</span></span>

##### <a name="enable-and-configure-tracing"></a><span data-ttu-id="3b131-199">Включение и Настройка трассировки</span><span class="sxs-lookup"><span data-stu-id="3b131-199">Enable and configure tracing</span></span>

<span data-ttu-id="3b131-200">Для начала трассировка должна быть включена для среды выполнения ДАПР с помощью файла конфигурации ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-200">To start, tracing must be enabled for the Dapr runtime using a Dapr configuration file.</span></span> <span data-ttu-id="3b131-201">Ниже приведен пример файла конфигурации с именем `tracing-config.yaml` .</span><span class="sxs-lookup"><span data-stu-id="3b131-201">Here's an example of a configuration file named `tracing-config.yaml`:</span></span>  

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: tracing-config
  namespace: default
spec:
  tracing:
    samplingRate: "1"
    zipkin:
      endpointAddress: "http://zipkin.default.svc.cluster.local:9411/api/v2/spans"
```

<span data-ttu-id="3b131-202">`samplingRate`Атрибут задает интервал, используемый для публикации трассировок.</span><span class="sxs-lookup"><span data-stu-id="3b131-202">The `samplingRate` attribute specifies the interval used for publishing traces.</span></span> <span data-ttu-id="3b131-203">Значение должно находиться в диапазоне `0` (трассировка отключена) и `1` (Каждая трассировка опубликована).</span><span class="sxs-lookup"><span data-stu-id="3b131-203">The value must be between `0` (tracing disabled) and `1` (every trace is published).</span></span> <span data-ttu-id="3b131-204">При значении, например, `0.5` каждая другая трассировка публикуется, значительно уменьшая опубликованный трафик.</span><span class="sxs-lookup"><span data-stu-id="3b131-204">With a value of `0.5`, for example, every other trace is published, significantly reducing published traffic.</span></span> <span data-ttu-id="3b131-205">`endpointAddress`Указывает на конечную точку на сервере зипкин, работающем в кластере Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3b131-205">The `endpointAddress` points to an endpoint on a Zipkin server running in a Kubernetes cluster.</span></span> <span data-ttu-id="3b131-206">Портом по умолчанию для Зипкин является `9411` .</span><span class="sxs-lookup"><span data-stu-id="3b131-206">The default port for Zipkin is `9411`.</span></span> <span data-ttu-id="3b131-207">Конфигурация должна быть применена к кластеру Kubernetes с помощью интерфейса командной строки Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="3b131-207">The configuration must be applied to the Kubernetes cluster using the Kubernetes CLI:</span></span>

```console
kubectl apply -f tracing-config.yaml
```

##### <a name="install-the-zipkin-server"></a><span data-ttu-id="3b131-208">Установка сервера Зипкин</span><span class="sxs-lookup"><span data-stu-id="3b131-208">Install the Zipkin server</span></span>

<span data-ttu-id="3b131-209">При установке ДАПР в режиме, размещенном в локальной среде, сервер Зипкин устанавливается автоматически, а трассировка включается в файле конфигурации по умолчанию, расположенном в `$HOME/.dapr/config.yaml` или `%USERPROFILE%\.dapr\config.yaml` в Windows.</span><span class="sxs-lookup"><span data-stu-id="3b131-209">When installing Dapr in self-hosted mode, a Zipkin server is automatically installed and tracing is enabled in the default configuration file located in `$HOME/.dapr/config.yaml` or `%USERPROFILE%\.dapr\config.yaml` on Windows.</span></span>

<span data-ttu-id="3b131-210">Однако при установке ДАПР в кластере Kubernetes Зипкин не добавляется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3b131-210">When installing Dapr on a Kubernetes cluster though, Zipkin isn't added by default.</span></span> <span data-ttu-id="3b131-211">Следующий файл манифеста Kubernetes с именем `zipkin.yaml` развертывает Стандартный сервер зипкин в кластере:</span><span class="sxs-lookup"><span data-stu-id="3b131-211">The following Kubernetes manifest file named `zipkin.yaml`, deploys a standard Zipkin server to the cluster:</span></span>

```yaml
kind: Deployment
apiVersion: apps/v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  replicas: 1
  selector:
    matchLabels:
      service: zipkin
  template:
    metadata:
      labels:
        service: zipkin
    spec:
      containers:
        - name: zipkin
          image: openzipkin/zipkin-slim
          imagePullPolicy: IfNotPresent
          ports:
            - name: http
              containerPort: 9411
              protocol: TCP

---

kind: Service
apiVersion: v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  type: NodePort
  ports:
    - port: 9411
      targetPort: 9411
      nodePort: 32411
      protocol: TCP
      name: zipkin
  selector:
    service: zipkin

```

<span data-ttu-id="3b131-212">В развертывании используется стандартный `openzipkin/zipkin-slim` образ контейнера.</span><span class="sxs-lookup"><span data-stu-id="3b131-212">The deployment uses the standard `openzipkin/zipkin-slim` container image.</span></span> <span data-ttu-id="3b131-213">Служба Зипкин предоставляет интерфейс веб-интерфейса Зипкин, который можно использовать для просмотра данных телеметрии по порту `32411` .</span><span class="sxs-lookup"><span data-stu-id="3b131-213">The Zipkin service exposes the Zipkin web front end, which you can use to view the telemetry on port `32411`.</span></span> <span data-ttu-id="3b131-214">Используйте интерфейс командной строки Kubernetes, чтобы применить файл манифеста Зипкин к кластеру Kubernetes и развернуть сервер Зипкин:</span><span class="sxs-lookup"><span data-stu-id="3b131-214">Use the Kubernetes CLI to apply the Zipkin manifest file to the Kubernetes cluster and deploy the Zipkin server:</span></span>

```console
kubectl apply -f zipkin.yaml
```

##### <a name="configure-the-services-to-use-the-tracing-configuration"></a><span data-ttu-id="3b131-215">Настройка служб для использования конфигурации трассировки</span><span class="sxs-lookup"><span data-stu-id="3b131-215">Configure the services to use the tracing configuration</span></span>

<span data-ttu-id="3b131-216">Теперь все настроено правильно, чтобы начать публикацию телеметрии.</span><span class="sxs-lookup"><span data-stu-id="3b131-216">Now everything is set up correctly to start publishing telemetry.</span></span> <span data-ttu-id="3b131-217">Каждый ДАПР расширения, развернутый в составе приложения, должен давать инструкции по выпуску телеметрии при запуске.</span><span class="sxs-lookup"><span data-stu-id="3b131-217">Every Dapr sidecar that is deployed as part of the application must be instructed to emit telemetry when started.</span></span> <span data-ttu-id="3b131-218">Для этого добавьте `dapr.io/config` заметку, которая ссылается на `tracing-config` конфигурацию для развертывания каждой службы.</span><span class="sxs-lookup"><span data-stu-id="3b131-218">To do that, add a `dapr.io/config` annotation that references the `tracing-config` configuration to the deployment of each service.</span></span> <span data-ttu-id="3b131-219">Ниже приведен пример файла манифеста службы API Ешоп Ordering, содержащего заметку:</span><span class="sxs-lookup"><span data-stu-id="3b131-219">Here's an example of the eShop ordering API service's manifest file containing the annotation:</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ordering-api
  namespace: eshop
  labels:
    app: eshop
spec:
  replicas: 1
  selector:
    matchLabels:
      app: eshop
  template:
    metadata:
      labels:
        app: simulation
      annotations:
        dapr.io/enabled: "true"
        dapr.io/app-id: "ordering-api"
        dapr.io/config: "tracing-config"
    spec:
      containers:
      - name: simulation
        image: eshop/ordering.api:linux-latest
```

##### <a name="inspect-the-telemetry-in-zipkin"></a><span data-ttu-id="3b131-220">Проверка телеметрии в Зипкин</span><span class="sxs-lookup"><span data-stu-id="3b131-220">Inspect the telemetry in Zipkin</span></span>

<span data-ttu-id="3b131-221">После запуска приложения ДАПР сидекарс выдаст данные телеметрии на сервер Зипкин.</span><span class="sxs-lookup"><span data-stu-id="3b131-221">Once the application is started, the Dapr sidecars will emit telemetry to the Zipkin server.</span></span> <span data-ttu-id="3b131-222">Чтобы проверить эту телеметрию, укажите в веб-браузере <http://localhost:32411> .</span><span class="sxs-lookup"><span data-stu-id="3b131-222">To inspect this telemetry, point a web-browser to <http://localhost:32411>.</span></span> <span data-ttu-id="3b131-223">Вы увидите веб-интерфейс Зипкин:</span><span class="sxs-lookup"><span data-stu-id="3b131-223">You'll see the Zipkin web front end:</span></span>

![Начальная страница Зипкин](media/observability/zipkin.png)

<span data-ttu-id="3b131-225">На вкладке *найти трассировку* можно выполнять запросы к трассировкам.</span><span class="sxs-lookup"><span data-stu-id="3b131-225">On the *Find a trace* tab, you can query traces.</span></span> <span data-ttu-id="3b131-226">При нажатии кнопки *выполнить запрос* без указания каких бы то ни было ограничений будут показаны все полученные *трассировки*:</span><span class="sxs-lookup"><span data-stu-id="3b131-226">Pressing the *RUN QUERY* button without specifying any restrictions will show all the ingested *traces*:</span></span>

![Список трассировок](media/observability/zipkin-traces-overview.png)

<span data-ttu-id="3b131-228">При нажатии кнопки « *Показывать* » рядом с определенной трассировкой отображаются подробные сведения об этой трассировке:</span><span class="sxs-lookup"><span data-stu-id="3b131-228">Clicking the *SHOW* button next to a specific trace, will show the details of that trace:</span></span>

![Сведения о трассировке](media/observability/zipkin-trace-details.png)

<span data-ttu-id="3b131-230">Каждый элемент на странице сведений — это диапазон, представляющий запрос, который является частью выбранной трассировки.</span><span class="sxs-lookup"><span data-stu-id="3b131-230">Each item on the details page, is a span that represents a request that is part of the selected trace.</span></span>

##### <a name="inspect-the-dependencies-between-services"></a><span data-ttu-id="3b131-231">Проверка зависимостей между службами</span><span class="sxs-lookup"><span data-stu-id="3b131-231">Inspect the dependencies between services</span></span>

<span data-ttu-id="3b131-232">Так как ДАПР сидекарс обрабатывает трафик между службами, Зипкин может использовать данные трассировки для определения зависимостей между службами.</span><span class="sxs-lookup"><span data-stu-id="3b131-232">Because Dapr sidecars handle traffic between services, Zipkin can use the trace information to determine the dependencies between the services.</span></span> <span data-ttu-id="3b131-233">Чтобы увидеть это в действии, перейдите на вкладку *зависимости* на веб-странице зипкин и нажмите кнопку с увеличительным стеклом.</span><span class="sxs-lookup"><span data-stu-id="3b131-233">To see it in action, go to the *Dependencies* tab on the Zipkin web page and select the button with the magnifying glass.</span></span> <span data-ttu-id="3b131-234">Зипкин покажет общие сведения о службах и их зависимостях:</span><span class="sxs-lookup"><span data-stu-id="3b131-234">Zipkin will show an overview of the services and their dependencies:</span></span>

![Граф зависимостей в Зипкин](media/observability/zipkin-dependencies.png)

<span data-ttu-id="3b131-236">Анимированные точки на линиях между службами представляют запросы и переходят из источника в место назначения.</span><span class="sxs-lookup"><span data-stu-id="3b131-236">The animated dots on the lines between the services represent requests and move from source to destination.</span></span> <span data-ttu-id="3b131-237">Красная точка указывает на неудачный запрос.</span><span class="sxs-lookup"><span data-stu-id="3b131-237">Red dots indicate a failed request.</span></span>

#### <a name="use-a-jaeger-or-new-relic-monitoring-back-end"></a><span data-ttu-id="3b131-238">Использование Жаежер или новой серверной части мониторинга Relic</span><span class="sxs-lookup"><span data-stu-id="3b131-238">Use a Jaeger or New Relic monitoring back end</span></span>

<span data-ttu-id="3b131-239">Помимо Зипкин, другие серверные программы мониторинга также поддерживают прием данных телеметрии с помощью формата Зипкин.</span><span class="sxs-lookup"><span data-stu-id="3b131-239">Beyond Zipkin itself, other monitoring back-end software also supports ingesting telemetry using the Zipkin format.</span></span> <span data-ttu-id="3b131-240">[Жаежер](https://www.jaegertracing.io/) — это система трассировки с открытым исходным кодом, созданная технологиями Uber.</span><span class="sxs-lookup"><span data-stu-id="3b131-240">[Jaeger](https://www.jaegertracing.io/) is an open source tracing system created by Uber Technologies.</span></span> <span data-ttu-id="3b131-241">Он используется для трассировки транзакций между распределенными службами и устранения неполадок в сложных средах микрослужб.</span><span class="sxs-lookup"><span data-stu-id="3b131-241">It's used to trace transactions between distributed services and troubleshoot complex microservices environments.</span></span> <span data-ttu-id="3b131-242">[New Relic](https://newrelic.com/) — это платформа наблюдения с *полным стеком* .</span><span class="sxs-lookup"><span data-stu-id="3b131-242">[New Relic](https://newrelic.com/) is a *full-stack* observability platform.</span></span> <span data-ttu-id="3b131-243">Он связывает релевантные данные из распределенного приложения, чтобы предоставить полную картину системы.</span><span class="sxs-lookup"><span data-stu-id="3b131-243">It links relevant data from a distributed application to provide a complete picture of your system.</span></span> <span data-ttu-id="3b131-244">Чтобы испытать их, укажите в `endpointAddress` файле конфигурации ДАПР указатель на жаежер или новый сервер Relic.</span><span class="sxs-lookup"><span data-stu-id="3b131-244">To try them out, specify an `endpointAddress` pointing to either a Jaeger or New Relic server in the Dapr configuration file.</span></span> <span data-ttu-id="3b131-245">Ниже приведен пример файла конфигурации, который настраивает ДАПР для отправки данных телеметрии на сервер Жаежер.</span><span class="sxs-lookup"><span data-stu-id="3b131-245">Here's an example of a configuration file that configures Dapr to send telemetry to a Jaeger server.</span></span> <span data-ttu-id="3b131-246">URL-адрес для Жаежер идентичен URL-адресу для Зипкин.</span><span class="sxs-lookup"><span data-stu-id="3b131-246">The URL for Jaeger is identical to the URL for the Zipkin.</span></span> <span data-ttu-id="3b131-247">Единственное отличие заключается в том, что используется порт, на котором работает сервер:</span><span class="sxs-lookup"><span data-stu-id="3b131-247">The only difference is the port on which the server runs:</span></span>

 ```yaml
 apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "http://localhost:9415/api/v2/spans"
 ```

<span data-ttu-id="3b131-248">Чтобы испытать новый Relic, укажите конечную точку нового API Relic.</span><span class="sxs-lookup"><span data-stu-id="3b131-248">To try out New Relic, specify the endpoint of the New Relic API.</span></span> <span data-ttu-id="3b131-249">Ниже приведен пример файла конфигурации для New Relic:</span><span class="sxs-lookup"><span data-stu-id="3b131-249">Here's an example of a configuration file for New Relic:</span></span>

 ```yaml
apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "https://trace-api.newrelic.com/trace/v1?Api-Key=<NR-API-KEY>&Data-Format=zipkin&Data-Format-Version=2"
 ```

<span data-ttu-id="3b131-250">Дополнительные сведения о том, как их использовать, см. на веб-сайтах Жаежер и New Relic.</span><span class="sxs-lookup"><span data-stu-id="3b131-250">Check out the Jaeger and New Relic websites for more information on how to use them.</span></span>

### <a name="metrics"></a><span data-ttu-id="3b131-251">Метрики</span><span class="sxs-lookup"><span data-stu-id="3b131-251">Metrics</span></span>

<span data-ttu-id="3b131-252">Метрики позволяют получить представление о производительности и потреблении ресурсов.</span><span class="sxs-lookup"><span data-stu-id="3b131-252">Metrics provide insight into performance and resource consumption.</span></span> <span data-ttu-id="3b131-253">Внутри ДАПР выпускается обширная коллекция метрик системы и среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="3b131-253">Under the hood, Dapr emits a wide collection of system and runtime metrics.</span></span> <span data-ttu-id="3b131-254">ДАПР использует [Prometheus](https://prometheus.io/) в качестве стандарта метрики.</span><span class="sxs-lookup"><span data-stu-id="3b131-254">Dapr uses [Prometheus](https://prometheus.io/) as a metric standard.</span></span> <span data-ttu-id="3b131-255">ДАПР сидекарс и системные службы предоставляют конечную точку метрик по порту `9090` .</span><span class="sxs-lookup"><span data-stu-id="3b131-255">Dapr sidecars and system services, expose a metrics endpoint on port `9090`.</span></span> <span data-ttu-id="3b131-256">*Prometheus отхода* вызывает эту конечную точку в предопределенном интервале для сбора метрик.</span><span class="sxs-lookup"><span data-stu-id="3b131-256">A *Prometheus scraper* calls this endpoint at a predefined interval to collect metrics.</span></span> <span data-ttu-id="3b131-257">Отходы отправляют значения метрик в серверную части мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-257">The scraper sends metric values to a monitoring back end.</span></span> <span data-ttu-id="3b131-258">На рис. 9-4 показан процесс отхода:</span><span class="sxs-lookup"><span data-stu-id="3b131-258">Figure 9-4 shows the scraping process:</span></span>

![Prometheus метрики](media/observability/prometheus-scraper.png)

<span data-ttu-id="3b131-260">**Рис. 9-4**.</span><span class="sxs-lookup"><span data-stu-id="3b131-260">**Figure 9-4**.</span></span> <span data-ttu-id="3b131-261">Prometheus метрики.</span><span class="sxs-lookup"><span data-stu-id="3b131-261">Scraping Prometheus metrics.</span></span>

<span data-ttu-id="3b131-262">На приведенном выше рисунке каждая расширения и системная служба предоставляет конечную точку метрики, которая прослушивает порт 9090.</span><span class="sxs-lookup"><span data-stu-id="3b131-262">In the above figure, each sidecar and system service exposes a metric endpoint that listens on port 9090.</span></span> <span data-ttu-id="3b131-263">Отбракованный объект метрик Prometheus фиксирует метрики каждой конечной точки и публикует их в серверной части мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-263">The Prometheus Metrics Scrapper captures metrics from each endpoint and published the information to the monitoring back end.</span></span>  

#### <a name="service-discovery"></a><span data-ttu-id="3b131-264">обнаружение служб;</span><span class="sxs-lookup"><span data-stu-id="3b131-264">Service discovery</span></span>

<span data-ttu-id="3b131-265">Может возникнуть вопрос о том, как источнику метрик будет известно, где собираются метрики.</span><span class="sxs-lookup"><span data-stu-id="3b131-265">You might wonder how the metrics scraper knows where to collect metrics.</span></span> <span data-ttu-id="3b131-266">Prometheus можно интегрировать с механизмами обнаружения, встроенными в целевые среды развертывания.</span><span class="sxs-lookup"><span data-stu-id="3b131-266">Prometheus can integrate with discovery mechanisms built into target deployment environments.</span></span> <span data-ttu-id="3b131-267">Например, при выполнении в Kubernetes Prometheus может интегрироваться с API Kubernetes, чтобы найти все доступные Kubernetes ресурсы, работающие в среде.</span><span class="sxs-lookup"><span data-stu-id="3b131-267">For example, when running in Kubernetes, Prometheus can integrate with the Kubernetes API to find all available Kubernetes resources running in the environment.</span></span>

#### <a name="metrics-list"></a><span data-ttu-id="3b131-268">Список метрик</span><span class="sxs-lookup"><span data-stu-id="3b131-268">Metrics list</span></span>

<span data-ttu-id="3b131-269">ДАПР создает большой набор метрик для системных служб ДАПР и их среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="3b131-269">Dapr generates a large set of metrics for Dapr system services and its runtime.</span></span> <span data-ttu-id="3b131-270">Некоторые примеры:</span><span class="sxs-lookup"><span data-stu-id="3b131-270">Some examples include:</span></span>

| <span data-ttu-id="3b131-271">Метрика</span><span class="sxs-lookup"><span data-stu-id="3b131-271">Metric</span></span>                                         | <span data-ttu-id="3b131-272">Источник</span><span class="sxs-lookup"><span data-stu-id="3b131-272">Source</span></span> | <span data-ttu-id="3b131-273">Описание</span><span class="sxs-lookup"><span data-stu-id="3b131-273">Description</span></span>                                                  |
| ---------------------------------------------- | :----: | ------------------------------------------------------------ |
| <span data-ttu-id="3b131-274">dapr_operator_service_created_total</span><span class="sxs-lookup"><span data-stu-id="3b131-274">dapr_operator_service_created_total</span></span>            | <span data-ttu-id="3b131-275">Система</span><span class="sxs-lookup"><span data-stu-id="3b131-275">System</span></span> | <span data-ttu-id="3b131-276">Общее число ДАПР служб, созданных службой оператора ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-276">The total number of Dapr services created by the Dapr Operator service.</span></span> |
| <span data-ttu-id="3b131-277">dapr_injector_sidecar_injection и requests_total</span><span class="sxs-lookup"><span data-stu-id="3b131-277">dapr_injector_sidecar_injection/requests_total</span></span> | <span data-ttu-id="3b131-278">Система</span><span class="sxs-lookup"><span data-stu-id="3b131-278">System</span></span> | <span data-ttu-id="3b131-279">Общее число запросов введения расширения, полученных службой Sidecar-Injector ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-279">The total number of sidecar injection requests received by the Dapr Sidecar-Injector service.</span></span> |
| <span data-ttu-id="3b131-280">dapr_placement_runtimes_total</span><span class="sxs-lookup"><span data-stu-id="3b131-280">dapr_placement_runtimes_total</span></span>                  | <span data-ttu-id="3b131-281">Система</span><span class="sxs-lookup"><span data-stu-id="3b131-281">System</span></span> | <span data-ttu-id="3b131-282">Общее число узлов, отправленных в службу размещения ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-282">The total number of hosts reported to the Dapr Placement service.</span></span> |
| <span data-ttu-id="3b131-283">dapr_sentry_cert_sign_request_received_total</span><span class="sxs-lookup"><span data-stu-id="3b131-283">dapr_sentry_cert_sign_request_received_total</span></span>   | <span data-ttu-id="3b131-284">Система</span><span class="sxs-lookup"><span data-stu-id="3b131-284">System</span></span> | <span data-ttu-id="3b131-285">Число запросов подписи сертификата (КРСС), полученных службой ДАПР Sentry.</span><span class="sxs-lookup"><span data-stu-id="3b131-285">The number of certificate signing requests (CRSs) received by the Dapr Sentry service.</span></span> |
| <span data-ttu-id="3b131-286">dapr_runtime_component_loaded</span><span class="sxs-lookup"><span data-stu-id="3b131-286">dapr_runtime_component_loaded</span></span>      | <span data-ttu-id="3b131-287">Параметры выполнения</span><span class="sxs-lookup"><span data-stu-id="3b131-287">Runtime</span></span> | <span data-ttu-id="3b131-288">Число успешно загруженных компонентов ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-288">The number of successfully loaded Dapr components.</span></span>           |
| <span data-ttu-id="3b131-289">dapr_grpc_io_server_completed_rpcs</span><span class="sxs-lookup"><span data-stu-id="3b131-289">dapr_grpc_io_server_completed_rpcs</span></span> | <span data-ttu-id="3b131-290">Параметры выполнения</span><span class="sxs-lookup"><span data-stu-id="3b131-290">Runtime</span></span> | <span data-ttu-id="3b131-291">Число вызовов gRPC по методу и состоянию.</span><span class="sxs-lookup"><span data-stu-id="3b131-291">Count of gRPC calls by method and status.</span></span>                    |
| <span data-ttu-id="3b131-292">dapr_http_server_request_count</span><span class="sxs-lookup"><span data-stu-id="3b131-292">dapr_http_server_request_count</span></span>     | <span data-ttu-id="3b131-293">Параметры выполнения</span><span class="sxs-lookup"><span data-stu-id="3b131-293">Runtime</span></span> | <span data-ttu-id="3b131-294">Количество HTTP-запросов, запущенных на HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="3b131-294">Number of HTTP requests started in an HTTP server.</span></span>           |
| <span data-ttu-id="3b131-295">dapr_http/клиент/sent_bytes</span><span class="sxs-lookup"><span data-stu-id="3b131-295">dapr_http/client/sent_bytes</span></span>        | <span data-ttu-id="3b131-296">Параметры выполнения</span><span class="sxs-lookup"><span data-stu-id="3b131-296">Runtime</span></span> | <span data-ttu-id="3b131-297">Общее число байтов, отправленных в тексте запроса (не включая заголовки) HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="3b131-297">Total bytes sent in request body (not including headers) by an HTTP client.</span></span> |

<span data-ttu-id="3b131-298">Дополнительные сведения о доступных метриках см. в [документации по метрикам ДАПР](https://docs.dapr.io/developing-applications/building-blocks/observability/metrics).</span><span class="sxs-lookup"><span data-stu-id="3b131-298">For more information on available metrics, see the [Dapr metrics documentation](https://docs.dapr.io/developing-applications/building-blocks/observability/metrics).</span></span>

#### <a name="configure-dapr-metrics"></a><span data-ttu-id="3b131-299">Настройка метрик ДАПР</span><span class="sxs-lookup"><span data-stu-id="3b131-299">Configure Dapr metrics</span></span>

<span data-ttu-id="3b131-300">Во время выполнения можно отключить конечную точку коллекции метрик, включив `--enable-metrics=false` аргумент в команду ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-300">At runtime, you can disable the metrics collection endpoint by including the `--enable-metrics=false` argument in the Dapr command.</span></span> <span data-ttu-id="3b131-301">Также можно изменить порт по умолчанию для конечной точки с помощью `--metrics-port 9090` аргумента.</span><span class="sxs-lookup"><span data-stu-id="3b131-301">Or, you can also change the default port for the endpoint with the `--metrics-port 9090` argument.</span></span>

<span data-ttu-id="3b131-302">Вы также можете использовать файл конфигурации ДАПР для статического включения или отключения сбора метрик времени выполнения:</span><span class="sxs-lookup"><span data-stu-id="3b131-302">You can also use a Dapr configuration file to statically enable or disable runtime metrics collection:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  metric:
    enabled: false
```

#### <a name="visualize-dapr-metrics"></a><span data-ttu-id="3b131-303">Визуализация метрик ДАПР</span><span class="sxs-lookup"><span data-stu-id="3b131-303">Visualize Dapr metrics</span></span>

<span data-ttu-id="3b131-304">С помощью Prometheusного средства сбора и публикации метрик в серверной части мониторинга, как вы хотите понять необработанные данные?</span><span class="sxs-lookup"><span data-stu-id="3b131-304">With the Prometheus scraper collecting and publishing metrics into the monitoring back end, how do you make sense of the raw data?</span></span> <span data-ttu-id="3b131-305">Популярное средство визуализации для анализа метрик — [Grafana](https://grafana.com/grafana/).</span><span class="sxs-lookup"><span data-stu-id="3b131-305">A popular visualization tool for analyzing metrics is [Grafana](https://grafana.com/grafana/).</span></span> <span data-ttu-id="3b131-306">С помощью Grafana можно создавать панели мониторинга из доступных метрик.</span><span class="sxs-lookup"><span data-stu-id="3b131-306">With Grafana, you can create dashboards from the available metrics.</span></span> <span data-ttu-id="3b131-307">Ниже приведен пример панели мониторинга, отображающей метрики системных служб ДАПР:</span><span class="sxs-lookup"><span data-stu-id="3b131-307">Here's an example of a dashboard displaying Dapr system services metrics:</span></span>

![Панель мониторинга Grafana, отображающая метрики системных служб ДАПР](media/observability/grafana-sample.png)

<span data-ttu-id="3b131-309">Документация по ДАПР содержит [руководство по установке Prometheus и Grafana](https://docs.dapr.io/operations/monitoring/grafana/).</span><span class="sxs-lookup"><span data-stu-id="3b131-309">The Dapr documentation includes a [tutorial for installing Prometheus and Grafana](https://docs.dapr.io/operations/monitoring/grafana/).</span></span>

### <a name="logging"></a><span data-ttu-id="3b131-310">Ведение журнала</span><span class="sxs-lookup"><span data-stu-id="3b131-310">Logging</span></span>

<span data-ttu-id="3b131-311">Ведение журнала позволяет понять, что происходит со службой во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="3b131-311">Logging provides insight into what is happening with a service at runtime.</span></span> <span data-ttu-id="3b131-312">При запуске приложения ДАПР автоматически создает записи журнала из ДАПР сидекарс и системных служб ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-312">When running an application, Dapr automatically emits log entries from Dapr sidecars and Dapr system services.</span></span> <span data-ttu-id="3b131-313">Однако записи в журнале, инструментированные в коде приложения, **не** включаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="3b131-313">However, logging entries instrumented in your application code **aren't** automatically included.</span></span> <span data-ttu-id="3b131-314">Чтобы выдать журнал из кода приложения, можно импортировать конкретный пакет SDK, например [ОПЕНТЕЛЕМЕТРИ SDK для .NET](https://opentelemetry.io/docs/net/).</span><span class="sxs-lookup"><span data-stu-id="3b131-314">To emit logging from application code, you can import a specific SDK like [OpenTelemetry SDK for .NET](https://opentelemetry.io/docs/net/).</span></span> <span data-ttu-id="3b131-315">Код приложения для ведения журнала рассматривается далее в разделе, посвященном *использованию пакета SDK для ДАПР .NET*.</span><span class="sxs-lookup"><span data-stu-id="3b131-315">Logging application code is covered later in this chapter in the section *Using the Dapr .NET SDK*.</span></span>  

#### <a name="log-entry-structure"></a><span data-ttu-id="3b131-316">Структура записи журнала</span><span class="sxs-lookup"><span data-stu-id="3b131-316">Log entry structure</span></span>

<span data-ttu-id="3b131-317">ДАПР выдает структурированное ведение журнала.</span><span class="sxs-lookup"><span data-stu-id="3b131-317">Dapr emits structured logging.</span></span> <span data-ttu-id="3b131-318">Каждая запись журнала имеет следующий формат:</span><span class="sxs-lookup"><span data-stu-id="3b131-318">Each log entry has the following format:</span></span>

| <span data-ttu-id="3b131-319">Поле</span><span class="sxs-lookup"><span data-stu-id="3b131-319">Field</span></span>    | <span data-ttu-id="3b131-320">Описание</span><span class="sxs-lookup"><span data-stu-id="3b131-320">Description</span></span>                                          | <span data-ttu-id="3b131-321">Пример</span><span class="sxs-lookup"><span data-stu-id="3b131-321">Example</span></span>                             |
| -------- | ---------------------------------------------------- | ----------------------------------- |
| <span data-ttu-id="3b131-322">time</span><span class="sxs-lookup"><span data-stu-id="3b131-322">time</span></span>     | <span data-ttu-id="3b131-323">Отформатированная метка времени ISO8601</span><span class="sxs-lookup"><span data-stu-id="3b131-323">ISO8601 formatted timestamp</span></span>                          | `2021-01-10T14:19:31.000Z`          |
| <span data-ttu-id="3b131-324">уровень</span><span class="sxs-lookup"><span data-stu-id="3b131-324">level</span></span>    | <span data-ttu-id="3b131-325">Уровень записи ( `debug` \| `info` \| `warn` \| `error` )  </span><span class="sxs-lookup"><span data-stu-id="3b131-325">Level of the entry (`debug` \| `info` \| `warn`  \| `error`)</span></span> | `info`                              |
| <span data-ttu-id="3b131-326">type</span><span class="sxs-lookup"><span data-stu-id="3b131-326">type</span></span>     | <span data-ttu-id="3b131-327">Тип журнала</span><span class="sxs-lookup"><span data-stu-id="3b131-327">Log Type</span></span>                                             | `log`                               |
| <span data-ttu-id="3b131-328">msg</span><span class="sxs-lookup"><span data-stu-id="3b131-328">msg</span></span>      | <span data-ttu-id="3b131-329">Сообщение журнала</span><span class="sxs-lookup"><span data-stu-id="3b131-329">Log Message</span></span>                                          | `metrics server started on :62408/` |
| <span data-ttu-id="3b131-330">область</span><span class="sxs-lookup"><span data-stu-id="3b131-330">scope</span></span>    | <span data-ttu-id="3b131-331">Область ведения журнала</span><span class="sxs-lookup"><span data-stu-id="3b131-331">Logging Scope</span></span>                                        | `dapr.runtime`                      |
| <span data-ttu-id="3b131-332">экземпляр</span><span class="sxs-lookup"><span data-stu-id="3b131-332">instance</span></span> | <span data-ttu-id="3b131-333">Имя узла, где выполняется ДАПР</span><span class="sxs-lookup"><span data-stu-id="3b131-333">Hostname where Dapr runs</span></span>                             | <span data-ttu-id="3b131-334">TSTSRV01</span><span class="sxs-lookup"><span data-stu-id="3b131-334">TSTSRV01</span></span>                            |
| <span data-ttu-id="3b131-335">app_id</span><span class="sxs-lookup"><span data-stu-id="3b131-335">app_id</span></span>   | <span data-ttu-id="3b131-336">Идентификатор приложения ДАПР</span><span class="sxs-lookup"><span data-stu-id="3b131-336">Dapr App ID</span></span>                                          | <span data-ttu-id="3b131-337">ordering-api</span><span class="sxs-lookup"><span data-stu-id="3b131-337">ordering-api</span></span>                        |
| <span data-ttu-id="3b131-338">ver</span><span class="sxs-lookup"><span data-stu-id="3b131-338">ver</span></span>      | <span data-ttu-id="3b131-339">Версия среды выполнения ДАПР</span><span class="sxs-lookup"><span data-stu-id="3b131-339">Dapr Runtime Version</span></span>                                 | <span data-ttu-id="3b131-340">`1.0.0`-RC. 2</span><span class="sxs-lookup"><span data-stu-id="3b131-340">`1.0.0`-rc.2</span></span>                        |

<span data-ttu-id="3b131-341">При поиске в записях журнала в сценарии устранения неполадок `time` поля и `level` особенно полезны.</span><span class="sxs-lookup"><span data-stu-id="3b131-341">When searching through logging entries in a troubleshooting scenario, the `time` and `level` fields are especially helpful.</span></span> <span data-ttu-id="3b131-342">Поле времени упорядочивает записи журнала, чтобы можно было определить конкретные периоды времени.</span><span class="sxs-lookup"><span data-stu-id="3b131-342">The time field orders log entries so that you can pinpoint specific time periods.</span></span> <span data-ttu-id="3b131-343">При устранении неполадок записи журнала на *уровне отладки* содержат дополнительные сведения о поведении кода.</span><span class="sxs-lookup"><span data-stu-id="3b131-343">When troubleshooting, log entries at the *debug level* provide more information on the behavior of the code.</span></span>

#### <a name="plain-text-versus-json-format"></a><span data-ttu-id="3b131-344">Обычный текст и формат JSON</span><span class="sxs-lookup"><span data-stu-id="3b131-344">Plain text versus JSON format</span></span>

<span data-ttu-id="3b131-345">По умолчанию ДАПР выдает структурированный журнал в обычном текстовом формате.</span><span class="sxs-lookup"><span data-stu-id="3b131-345">By default, Dapr emits structured logging in plain-text format.</span></span> <span data-ttu-id="3b131-346">Каждая запись журнала форматируется как строка, содержащая пары "ключ-значение".</span><span class="sxs-lookup"><span data-stu-id="3b131-346">Every log entry is formatted as a string containing key/value pairs.</span></span> <span data-ttu-id="3b131-347">Вот пример ведения журнала в виде обычного текста:</span><span class="sxs-lookup"><span data-stu-id="3b131-347">Here's an example of logging in plain text:</span></span>

```text
== DAPR == time="2021-01-12T16:11:39.4669323+01:00" level=info msg="starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="log level set to: info" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="metrics server started on :62408/" app_id=ordering-api instance=TSTSRV03 scope=dapr.metrics type=log ver=1.0.0-rc.2
```

<span data-ttu-id="3b131-348">В простой форме этот формат сложно проанализировать.</span><span class="sxs-lookup"><span data-stu-id="3b131-348">While simple, this format is difficult to parse.</span></span> <span data-ttu-id="3b131-349">При просмотре записей журнала с помощью средства мониторинга необходимо включить ведение журнала в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="3b131-349">If viewing log entries with a monitoring tool, you'll want to enable JSON formatted logging.</span></span> <span data-ttu-id="3b131-350">С помощью записей JSON средство мониторинга может индексировать и запрашивать отдельные поля.</span><span class="sxs-lookup"><span data-stu-id="3b131-350">With JSON entries, a monitoring tool can index and query individual fields.</span></span> <span data-ttu-id="3b131-351">Вот те же записи журнала в формате JSON:</span><span class="sxs-lookup"><span data-stu-id="3b131-351">Here's the same log entries in JSON format:</span></span>

```json
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d", "scope": "dapr.runtime", "time": "2021-01-12T16:11:39.4669323+01:00", "type": "log", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "log level set to: info", "scope": "dapr.runtime", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "metrics server started on :62408/", "scope": "dapr.metrics", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
```

<span data-ttu-id="3b131-352">Чтобы включить форматирование JSON, необходимо настроить каждый ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="3b131-352">To enable JSON formatting, you need to configure each Dapr sidecar.</span></span> <span data-ttu-id="3b131-353">В режиме автономного размещения можно указать флаг в `--log-as-json` командной строке:</span><span class="sxs-lookup"><span data-stu-id="3b131-353">In self-hosted mode, you can specify the flag `--log-as-json` on the command line:</span></span>

```console
dapr run --app-id ordering-api --log-level info --log-as-json dotnet run
```

<span data-ttu-id="3b131-354">В Kubernetes можно добавить `dapr.io/log-as-json` заметку для каждого развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="3b131-354">In Kubernetes, you can add a `dapr.io/log-as-json` annotation to each deployment for the application:</span></span>

```yaml
annotations:
   dapr.io/enabled: "true"
   dapr.io/app-id: "ordering-api"
   dapr.io/app-port: "80"
   dapr.io/config: "dapr-config"
   dapr.io/log-as-json: "true"
```

<span data-ttu-id="3b131-355">При установке ДАПР в кластере Kubernetes с помощью Helm можно включить ведение журнала в формате JSON для всех системных служб ДАПР:</span><span class="sxs-lookup"><span data-stu-id="3b131-355">When you install Dapr in a Kubernetes cluster using Helm, you can enable JSON formatted logging for all the Dapr system services:</span></span>

```console
helm repo add dapr https://dapr.github.io/helm-charts/
helm repo update
kubectl create namespace dapr-system
helm install dapr dapr/dapr --namespace dapr-system --set global.logAsJson=true
```

#### <a name="collect-logs"></a><span data-ttu-id="3b131-356">Сбор журналов</span><span class="sxs-lookup"><span data-stu-id="3b131-356">Collect logs</span></span>

<span data-ttu-id="3b131-357">Журналы, созданные ДАПР, можно поставлять в серверную части мониторинга для анализа.</span><span class="sxs-lookup"><span data-stu-id="3b131-357">The logs emitted by Dapr can be fed into a monitoring back end for analysis.</span></span> <span data-ttu-id="3b131-358">Сборщик данных журнала — это компонент, собирающий журналы из системы и отправляющий их в серверную части мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-358">A log collector is a component that collects logs from a system and sends them to a monitoring back end.</span></span> <span data-ttu-id="3b131-359">Широко распространенный сборщик журналов [.](https://www.fluentd.org/)</span><span class="sxs-lookup"><span data-stu-id="3b131-359">A popular log collector is [Fluentd](https://www.fluentd.org/).</span></span> <span data-ttu-id="3b131-360">Ознакомьтесь с [инструкциями по настройке, эластичным поиском и Kibana в Kubernetes](https://docs.dapr.io/operations/monitoring/fluentd/) в документации по ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-360">Check out the [How-To: Set up Fluentd, Elastic search and Kibana in Kubernetes](https://docs.dapr.io/operations/monitoring/fluentd/) in the Dapr documentation.</span></span> <span data-ttu-id="3b131-361">Эта статья содержит инструкции по настройке в качестве сборщика журналов и [стека Elk](https://www.elastic.co/elastic-stack) (эластичный Поиск и Kibana) в качестве серверной части мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-361">This article contains instructions for setting up Fluentd as log collector and the [ELK Stack](https://www.elastic.co/elastic-stack) (Elastic Search and Kibana) as a monitoring back end.</span></span>

### <a name="health-status"></a><span data-ttu-id="3b131-362">Состояние работоспособности</span><span class="sxs-lookup"><span data-stu-id="3b131-362">Health status</span></span>

<span data-ttu-id="3b131-363">Состояние работоспособности службы позволяет понять ее доступность.</span><span class="sxs-lookup"><span data-stu-id="3b131-363">The health status of a service provides insight into its availability.</span></span> <span data-ttu-id="3b131-364">Каждый ДАПР расширения предоставляет API работоспособности, который может использоваться средой размещения для определения работоспособности расширения.</span><span class="sxs-lookup"><span data-stu-id="3b131-364">Each Dapr sidecar exposes a health API that can be used by the hosting environment to determine the health of the sidecar.</span></span> <span data-ttu-id="3b131-365">API имеет одну операцию:</span><span class="sxs-lookup"><span data-stu-id="3b131-365">The API has one operation:</span></span>

```console
GET http://localhost:3500/v1.0/healthz
```

<span data-ttu-id="3b131-366">Операция возвращает два кода состояния HTTP:</span><span class="sxs-lookup"><span data-stu-id="3b131-366">The operation returns two HTTP status codes:</span></span>

- <span data-ttu-id="3b131-367">204: Если расширения работоспособен</span><span class="sxs-lookup"><span data-stu-id="3b131-367">204: When the sidecar is healthy</span></span>
- <span data-ttu-id="3b131-368">500: Если расширения не исправен</span><span class="sxs-lookup"><span data-stu-id="3b131-368">500: when the sidecar isn't healthy</span></span>

<span data-ttu-id="3b131-369">При работе в автономном режиме API работоспособности не вызывается автоматически.</span><span class="sxs-lookup"><span data-stu-id="3b131-369">When running in self-hosted mode, the health API isn't automatically invoked.</span></span> <span data-ttu-id="3b131-370">Вы можете вызвать API, используя код приложения или средство мониторинга работоспособности.</span><span class="sxs-lookup"><span data-stu-id="3b131-370">You can invoke the API though from application code or a health monitoring tool.</span></span>

<span data-ttu-id="3b131-371">При выполнении в Kubernetes ДАПР расширения-инжектор автоматически настраивает Kubernetes для использования API работоспособности *для выполнения проверок* *готовности и проб подготовки*.</span><span class="sxs-lookup"><span data-stu-id="3b131-371">When running in Kubernetes, the Dapr sidecar-injector automatically configures Kubernetes to use the health API for executing *liveness probes* and *readiness probes*.</span></span>

<span data-ttu-id="3b131-372">Kubernetes использует проверки Live, чтобы определить, работает ли контейнер.</span><span class="sxs-lookup"><span data-stu-id="3b131-372">Kubernetes uses liveness probes to determine whether a container is up and running.</span></span> <span data-ttu-id="3b131-373">Если зонд проверки на актуальность возвращает код ошибки, Kubernetes считает, что контейнер недоступен, и автоматически перезапускает его.</span><span class="sxs-lookup"><span data-stu-id="3b131-373">If a liveness probe returns a failure code, Kubernetes will assume the container is dead and automatically restart it.</span></span> <span data-ttu-id="3b131-374">Эта функция увеличивает общую доступность приложения.</span><span class="sxs-lookup"><span data-stu-id="3b131-374">This feature increases the overall availability of your application.</span></span>

<span data-ttu-id="3b131-375">Kubernetes использует проверки готовности, чтобы определить, готов ли контейнер к приему трафика.</span><span class="sxs-lookup"><span data-stu-id="3b131-375">Kubernetes uses readiness probes to determine whether a container is ready to start accepting traffic.</span></span> <span data-ttu-id="3b131-376">Модуль POD считается готовым, когда все его контейнеры готовы.</span><span class="sxs-lookup"><span data-stu-id="3b131-376">A pod is considered ready when all of its containers are ready.</span></span> <span data-ttu-id="3b131-377">Готовность определяет, может ли служба Kubernetes направлять трафик в модуль в сценарии балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="3b131-377">Readiness determines whether a Kubernetes service can direct traffic to a pod in a load-balancing scenario.</span></span> <span data-ttu-id="3b131-378">Модули Pod, которые не готовы, автоматически удаляются из балансировщика нагрузки.</span><span class="sxs-lookup"><span data-stu-id="3b131-378">Pods that aren't ready are automatically removed from the load-balancer.</span></span>

<span data-ttu-id="3b131-379">Проверки актуальности и готовности имеют несколько настраиваемых параметров.</span><span class="sxs-lookup"><span data-stu-id="3b131-379">Liveness and readiness probes have several configurable parameters.</span></span> <span data-ttu-id="3b131-380">Оба параметра настраиваются в разделе спецификации контейнера файла манифеста Pod.</span><span class="sxs-lookup"><span data-stu-id="3b131-380">Both are configured in the container spec section of a pod's manifest file.</span></span> <span data-ttu-id="3b131-381">По умолчанию ДАПР использует следующую конфигурацию для каждого контейнера расширения:</span><span class="sxs-lookup"><span data-stu-id="3b131-381">By default, Dapr uses the following configuration for each sidecar container:</span></span>

```yaml
livenessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold : 3
readinessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold: 3
```

 <span data-ttu-id="3b131-382">Для проб доступны следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="3b131-382">The following parameters are available for the probes:</span></span>

- <span data-ttu-id="3b131-383">`path`Указывает конечную точку API работоспособности ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-383">The `path` specifies the Dapr health API endpoint.</span></span>
- <span data-ttu-id="3b131-384">`port`Указывает порт API работоспособности ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-384">The `port` specifies the Dapr health API port.</span></span>
- <span data-ttu-id="3b131-385">`initialDelaySeconds`Указывает число секунд, в течение которых Kubernetes будет ожидать перед первым запуском проверки контейнера.</span><span class="sxs-lookup"><span data-stu-id="3b131-385">The `initialDelaySeconds`specifies the number of seconds Kubernetes will wait before it starts probing a container for the first time.</span></span>
- <span data-ttu-id="3b131-386">`periodSeconds`Указывает количество секунд, в течение которых Kubernetes будет ожидать каждой проверки.</span><span class="sxs-lookup"><span data-stu-id="3b131-386">The `periodSeconds` specifies the number of seconds Kubernetes will wait between each probe.</span></span>
- <span data-ttu-id="3b131-387">`timeoutSeconds`Указывает число секунд, в течение которых Kubernetes будет ожидать ответа от API до истечения времени ожидания. Время ожидания интерпретируется как сбой.</span><span class="sxs-lookup"><span data-stu-id="3b131-387">The `timeoutSeconds` specifies the number of seconds Kubernetes will wait on a response from the API before timing out. A timeout is interpreted as a failure.</span></span>
- <span data-ttu-id="3b131-388">`failureThreshold`Указывает число неудачно завершенного кода состояния Kubernetes, которое будет принято до рассмотрения того, что контейнер не является активным или не готов.</span><span class="sxs-lookup"><span data-stu-id="3b131-388">The `failureThreshold`specifies the number of failed status code Kubernetes will accept before considering the container not alive or not ready.</span></span>

### <a name="dapr-dashboard"></a><span data-ttu-id="3b131-389">Панель мониторинга ДАПР</span><span class="sxs-lookup"><span data-stu-id="3b131-389">Dapr dashboard</span></span>

<span data-ttu-id="3b131-390">ДАПР предлагает панель мониторинга, в которой представлены сведения о состоянии приложений, компонентов и конфигураций ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-390">Dapr offers a dashboard that presents status information on Dapr applications, components, and configurations.</span></span> <span data-ttu-id="3b131-391">Используйте интерфейс командной строки ДАПР, чтобы запустить панель мониторинга как веб-приложение на локальном компьютере через порт 8080:</span><span class="sxs-lookup"><span data-stu-id="3b131-391">Use the Dapr CLI to start the dashboard as a web-application on the local machine on port 8080:</span></span>

```console
dapr dashboard
```

<span data-ttu-id="3b131-392">Для приложения ДАПР, работающего в Kubernetes, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="3b131-392">For Dapr application running in Kubernetes, use the following command:</span></span>

```console
dapr dashboard -k
```

<span data-ttu-id="3b131-393">Откроется панель мониторинга с обзором всех служб в приложении с ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="3b131-393">The dashboard opens with an overview of all services in your application that have a Dapr sidecar.</span></span> <span data-ttu-id="3b131-394">На следующем снимке экрана показана панель мониторинга ДАПР для приложения Ешопондапр, работающего в Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="3b131-394">The following screenshot shows the Dapr dashboard for the eShopOnDapr application running in Kubernetes:</span></span>

![Страница обзора панели мониторинга ДАПР](media/observability/dapr-dashboard-overview.png)

<span data-ttu-id="3b131-396">Панель мониторинга ДАПР не имеет ценности при устранении неполадок в приложении ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-396">The Dapr dashboard is invaluable when troubleshooting a Dapr application.</span></span> <span data-ttu-id="3b131-397">В нем содержатся сведения о ДАПР сидекарс и системных службах.</span><span class="sxs-lookup"><span data-stu-id="3b131-397">It provides information about Dapr sidecars and system services.</span></span> <span data-ttu-id="3b131-398">Можно детализировать конфигурацию каждой службы, включая записи журнала.</span><span class="sxs-lookup"><span data-stu-id="3b131-398">You can drill down into the configuration of each service, including the logging entries.</span></span>

<span data-ttu-id="3b131-399">На панели мониторинга также отображаются настроенные компоненты (и их конфигурация) для приложения:</span><span class="sxs-lookup"><span data-stu-id="3b131-399">The dashboard also shows the configured components (and their configuration) for your application:</span></span>

![Страница компонентов панели мониторинга ДАПР](media/observability/dapr-dashboard-components.png)

<span data-ttu-id="3b131-401">На панели мониторинга доступен большой объем информации.</span><span class="sxs-lookup"><span data-stu-id="3b131-401">There's a large amount of information available through the dashboard.</span></span> <span data-ttu-id="3b131-402">Его можно обнаружить, запустив приложение ДАПР и просмотрев панель мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-402">You can discover it by running a Dapr application and browsing the dashboard.</span></span> <span data-ttu-id="3b131-403">Для запуска можно использовать сопутствующее приложение Ешопондапр.</span><span class="sxs-lookup"><span data-stu-id="3b131-403">You can use the accompanying eShopOnDapr application to start.</span></span>

<span data-ttu-id="3b131-404">Дополнительные сведения о командах панели мониторинга ДАПР см. в [справочнике по командам CLI панели мониторинга ДАПР в документации](https://docs.dapr.io/reference/cli/dapr-dashboard/) по ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-404">Check out the [Dapr dashboard CLI command reference](https://docs.dapr.io/reference/cli/dapr-dashboard/) in the Dapr docs for more information on the Dapr dashboard commands.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="3b131-405">Использование пакета SDK для ДАПР .NET</span><span class="sxs-lookup"><span data-stu-id="3b131-405">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="3b131-406">Пакет SDK для ДАПР .NET не содержит никаких специальных возможностей наблюдения.</span><span class="sxs-lookup"><span data-stu-id="3b131-406">The Dapr .NET SDK doesn't contain any specific observability features.</span></span> <span data-ttu-id="3b131-407">Все функции наблюдаемых элементов предлагаются на уровне ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-407">All observability features are offered at the Dapr level.</span></span>

<span data-ttu-id="3b131-408">Если вы хотите создавать данные телеметрии из кода приложения .NET, следует рассмотреть [пакет SDK для опентелеметри для .NET](https://opentelemetry.io/docs/net/).</span><span class="sxs-lookup"><span data-stu-id="3b131-408">If you want to emit telemetry from your .NET application code, you should consider the [OpenTelemetry SDK for .NET](https://opentelemetry.io/docs/net/).</span></span> <span data-ttu-id="3b131-409">Открытый проект телеметрии — это кросс-платформенный, Открытый исходный код и независимый от поставщика.</span><span class="sxs-lookup"><span data-stu-id="3b131-409">The Open Telemetry project is cross-platform, open source, and vendor agnostic.</span></span> <span data-ttu-id="3b131-410">Она предоставляет комплексную реализацию для создания, выдачи, сбора, обработки и экспорта данных телеметрии.</span><span class="sxs-lookup"><span data-stu-id="3b131-410">It provides an end-to-end implementation to generate, emit, collect, process, and export telemetry data.</span></span> <span data-ttu-id="3b131-411">Существует одна библиотека инструментирования для каждого языка, которая поддерживает автоматическое и ручное инструментирование.</span><span class="sxs-lookup"><span data-stu-id="3b131-411">There's a single instrumentation library per language that supports automatic and manual instrumentation.</span></span> <span data-ttu-id="3b131-412">Данные телеметрии публикуются с использованием стандарта Open телеметрии.</span><span class="sxs-lookup"><span data-stu-id="3b131-412">Telemetry is published using the Open Telemetry standard.</span></span> <span data-ttu-id="3b131-413">В проекте предусмотрена широкая поддержка отрасли и внедрение от поставщиков облачных услуг, поставщиков и конечных пользователей.</span><span class="sxs-lookup"><span data-stu-id="3b131-413">The project has broad industry support and adoption from cloud providers, vendors, and end users.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="3b131-414">Эталонное приложение: Ешопондапр</span><span class="sxs-lookup"><span data-stu-id="3b131-414">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="3b131-415">Наблюдаемость в сопутствующем справочном приложении Ешопондапр состоит из нескольких частей.</span><span class="sxs-lookup"><span data-stu-id="3b131-415">Observability in accompanying eShopOnDapr reference application consists of several parts.</span></span> <span data-ttu-id="3b131-416">Перехватывается данные телеметрии из всех сидекарс.</span><span class="sxs-lookup"><span data-stu-id="3b131-416">Telemetry from all of the sidecars is captured.</span></span> <span data-ttu-id="3b131-417">Кроме того, существуют другие функции наблюдения, унаследованные от предыдущего примера eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="3b131-417">Additionally, there are other observability features inherited from the earlier eShopOnContainers sample.</span></span>

### <a name="custom-health-dashboard"></a><span data-ttu-id="3b131-418">Настраиваемая панель мониторинга работоспособности</span><span class="sxs-lookup"><span data-stu-id="3b131-418">Custom health dashboard</span></span>

<span data-ttu-id="3b131-419">Проект **состояния** ешопондапр — это настраиваемая панель мониторинга работоспособности, которая позволяет получить представление о работоспособности служб ешоп.</span><span class="sxs-lookup"><span data-stu-id="3b131-419">The **WebStatus** project in eShopOnDapr is a custom health dashboard that gives insight into the health of the eShop services.</span></span> <span data-ttu-id="3b131-420">Эта панель мониторинга не использует API работоспособности ДАПР, но использует встроенный [механизм проверок работоспособности](/aspnet/core/host-and-deploy/health-checks) ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b131-420">This dashboard doesn't use the Dapr health API but uses the built-in [health checks mechanism](/aspnet/core/host-and-deploy/health-checks) of ASP.NET Core.</span></span> <span data-ttu-id="3b131-421">Панель мониторинга не только предоставляет состояние работоспособности служб, но и работоспособность зависимостей служб.</span><span class="sxs-lookup"><span data-stu-id="3b131-421">The dashboard not only provides the health status of the services, but also the health of the dependencies of the services.</span></span> <span data-ttu-id="3b131-422">Например, служба, использующая базу данных, также предоставляет состояние работоспособности этой базы данных, как показано на следующем снимке экрана:</span><span class="sxs-lookup"><span data-stu-id="3b131-422">For example, a service that uses a database also provides the health status of this database as shown in the following screenshot:</span></span>

![Настраиваемая панель мониторинга работоспособности Ешопондапр](media/observability/eshop-health-dashboard.png)

### <a name="seq-log-aggregator"></a><span data-ttu-id="3b131-424">Агрегатор журнала Seq</span><span class="sxs-lookup"><span data-stu-id="3b131-424">Seq log aggregator</span></span>

<span data-ttu-id="3b131-425">[Seq](https://datalust.co/seq) — это популярный сервер агрегатора журналов, который используется в ешопондапр для статистической обработки журналов.</span><span class="sxs-lookup"><span data-stu-id="3b131-425">[Seq](https://datalust.co/seq) is a popular log aggregator server that is used in eShopOnDapr to aggregate logs.</span></span> <span data-ttu-id="3b131-426">Seq принимает ведение журнала из служб приложений, но не из ДАПР системных служб или сидекарс.</span><span class="sxs-lookup"><span data-stu-id="3b131-426">Seq ingests logging from application services, but not from Dapr system services or sidecars.</span></span> <span data-ttu-id="3b131-427">Seq индексирует ведение журнала приложений и предлагает веб-интерфейс для анализа и запроса журналов.</span><span class="sxs-lookup"><span data-stu-id="3b131-427">Seq indexes application logging and offers a web front end for analyzing and querying the logs.</span></span> <span data-ttu-id="3b131-428">Она также предлагает функции для создания панелей мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-428">It also offers functionality for building monitoring dashboards.</span></span>

<span data-ttu-id="3b131-429">Службы приложений Ешопондапр выдают структурированный журнал с помощью библиотеки ведения журнала [SeriLog](https://serilog.net/) .</span><span class="sxs-lookup"><span data-stu-id="3b131-429">The eShopOnDapr application services emit structured logging using the [SeriLog](https://serilog.net/) logging library.</span></span> <span data-ttu-id="3b131-430">Serilog публикует события журнала в конструкции, называемой **приемником**.</span><span class="sxs-lookup"><span data-stu-id="3b131-430">Serilog publishes log events to a construct called a **sink**.</span></span> <span data-ttu-id="3b131-431">Приемник — это просто Целевая платформа, в которую Serilog записывает события ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="3b131-431">A sink is simply a target platform to which Serilog writes its logging events.</span></span> <span data-ttu-id="3b131-432">[Доступно множество приемников Serilog](https://github.com/serilog/serilog/wiki/Provided-Sinks), в том числе один для Seq.</span><span class="sxs-lookup"><span data-stu-id="3b131-432">[Many Serilog sinks are available](https://github.com/serilog/serilog/wiki/Provided-Sinks), including one for Seq.</span></span> <span data-ttu-id="3b131-433">Seq — это приемник Serilog, используемый в Ешопондапр.</span><span class="sxs-lookup"><span data-stu-id="3b131-433">Seq is the Serilog sink used in eShopOnDapr.</span></span>

### <a name="application-insights"></a><span data-ttu-id="3b131-434">Application Insights</span><span class="sxs-lookup"><span data-stu-id="3b131-434">Application Insights</span></span>

<span data-ttu-id="3b131-435">Ешопондапр Services также отправляют данные телеметрии непосредственно в Azure Application Insights с помощью пакета SDK для Microsoft Application Insights для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b131-435">eShopOnDapr services also send telemetry directly to Azure Application Insights using the Microsoft Application Insights SDK for .NET Core.</span></span> <span data-ttu-id="3b131-436">Дополнительные сведения см. в статье [Application Insights Azure для ASP.NET Core приложений](/azure/azure-monitor/app/asp-net-core) в документации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="3b131-436">For more information, see [Azure Application Insights for ASP.NET Core applications](/azure/azure-monitor/app/asp-net-core) in the Microsoft docs.</span></span>

## <a name="summary"></a><span data-ttu-id="3b131-437">Итоги</span><span class="sxs-lookup"><span data-stu-id="3b131-437">Summary</span></span>

<span data-ttu-id="3b131-438">Хорошее наблюдаемое значение очень важно при запуске распределенной системы в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="3b131-438">Good observability is crucial when running a distributed system in production.</span></span>

<span data-ttu-id="3b131-439">ДАПР предоставляет различные типы телеметрии, включая распределенную трассировку, ведение журнала, метрики и состояние работоспособности.</span><span class="sxs-lookup"><span data-stu-id="3b131-439">Dapr provides different types of telemetry, including distributed tracing, logging, metrics, and health status.</span></span>

<span data-ttu-id="3b131-440">ДАПР создает данные телеметрии только для системных служб ДАПР и сидекарс.</span><span class="sxs-lookup"><span data-stu-id="3b131-440">Dapr only produces telemetry for the Dapr system services and sidecars.</span></span> <span data-ttu-id="3b131-441">Данные телеметрии из кода приложения не включаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="3b131-441">Telemetry from your application code isn't automatically included.</span></span> <span data-ttu-id="3b131-442">Однако вы можете использовать конкретный пакет SDK, например пакет SDK для Опентелеметри для .NET, чтобы создавать данные телеметрии из кода приложения.</span><span class="sxs-lookup"><span data-stu-id="3b131-442">You can however use a specific SDK like the OpenTelemetry SDK for .NET to emit telemetry from your application code.</span></span>

<span data-ttu-id="3b131-443">Данные телеметрии ДАПР создаются в формате с открытым стандартом, поэтому его можно принять с помощью большого набора доступных средств мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-443">Dapr telemetry is produced in an open-standards based format so it can be ingested by a large set of available monitoring tools.</span></span> <span data-ttu-id="3b131-444">Примеры: Зипкин, Azure Application Insights, ELK Stack, New Relic и Grafana.</span><span class="sxs-lookup"><span data-stu-id="3b131-444">Some examples are: Zipkin, Azure Application Insights, the ELK Stack, New Relic, and Grafana.</span></span> <span data-ttu-id="3b131-445">Руководства по мониторингу приложений ДАПР с конкретными серверными элементами мониторинга см. в статье [мониторинг приложения с помощью ДАПР](https://docs.dapr.io/operations/monitoring/) в документации ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-445">See [Monitor your application with Dapr](https://docs.dapr.io/operations/monitoring/) in the Dapr documentation for tutorials on how to monitor your Dapr applications with specific monitoring back ends.</span></span>

<span data-ttu-id="3b131-446">Вам потребуются отходы телеметрии, которые принимают данные телеметрии и публикуют их в серверной части мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-446">You'll need a telemetry scraper that ingests telemetry and publishes it to the monitoring back end.</span></span>

<span data-ttu-id="3b131-447">ДАПР можно настроить для выдачи структурированного журнала.</span><span class="sxs-lookup"><span data-stu-id="3b131-447">Dapr can be configured to emit structured logging.</span></span> <span data-ttu-id="3b131-448">Структурированное ведение журнала предпочтительнее, так как оно может индексироваться средствами серверного мониторинга.</span><span class="sxs-lookup"><span data-stu-id="3b131-448">Structured logging is favored as it can be indexed by back-end monitoring tools.</span></span> <span data-ttu-id="3b131-449">Индексированное ведение журнала позволяет пользователям выполнять расширенные запросы при поиске в журнале.</span><span class="sxs-lookup"><span data-stu-id="3b131-449">Indexed logging enables users to execute rich queries when searching through the logging.</span></span>

<span data-ttu-id="3b131-450">ДАПР предлагает панель мониторинга, в которой представлены сведения о службах и конфигурации ДАПР.</span><span class="sxs-lookup"><span data-stu-id="3b131-450">Dapr offers a dashboard that presents information about the Dapr services and configuration.</span></span>

## <a name="references"></a><span data-ttu-id="3b131-451">Ссылки</span><span class="sxs-lookup"><span data-stu-id="3b131-451">References</span></span>

- [<span data-ttu-id="3b131-452">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="3b131-452">Azure Application Insights</span></span>](/azure/azure-monitor/app/app-insights-overview/)
- [<span data-ttu-id="3b131-453">Открыть телеметрию</span><span class="sxs-lookup"><span data-stu-id="3b131-453">Open Telemetry</span></span>](https://opentelemetry.io/)
- [<span data-ttu-id="3b131-454">зипкин</span><span class="sxs-lookup"><span data-stu-id="3b131-454">Zipkin</span></span>](https://zipkin.io/)
- [<span data-ttu-id="3b131-455">Контекст трассировки W3C</span><span class="sxs-lookup"><span data-stu-id="3b131-455">W3C Trace Context</span></span>](https://www.w3.org/TR/trace-context/)
- [<span data-ttu-id="3b131-456">Jaeger</span><span class="sxs-lookup"><span data-stu-id="3b131-456">Jaeger</span></span>](https://www.jaegertracing.io/)
- [<span data-ttu-id="3b131-457">New Relic</span><span class="sxs-lookup"><span data-stu-id="3b131-457">New Relic</span></span>](https://newrelic.com/)
- [<span data-ttu-id="3b131-458">Prometheus</span><span class="sxs-lookup"><span data-stu-id="3b131-458">Prometheus</span></span>](https://prometheus.io/)
- [<span data-ttu-id="3b131-459">Grafana</span><span class="sxs-lookup"><span data-stu-id="3b131-459">Grafana</span></span>](https://grafana.com/grafana/)
- [<span data-ttu-id="3b131-460">Открытие пакета SDK для телеметрии для .NET</span><span class="sxs-lookup"><span data-stu-id="3b131-460">Open Telemetry SDK for .NET</span></span>](https://opentelemetry.io/docs/net/)
- [<span data-ttu-id="3b131-461">Fluentd</span><span class="sxs-lookup"><span data-stu-id="3b131-461">Fluentd</span></span>](https://www.fluentd.org/)
- [<span data-ttu-id="3b131-462">Стек ELK</span><span class="sxs-lookup"><span data-stu-id="3b131-462">ELK stack</span></span>](https://www.elastic.co/elastic-stack)
- [<span data-ttu-id="3b131-463">Порядк</span><span class="sxs-lookup"><span data-stu-id="3b131-463">Seq</span></span>](https://datalust.co/seq)
- [<span data-ttu-id="3b131-464">Serilog</span><span class="sxs-lookup"><span data-stu-id="3b131-464">Serilog</span></span>](https://serilog.net/)

> [!div class="step-by-step"]
> <span data-ttu-id="3b131-465">[Назад](bindings.md)
> [Вперед](secrets.md)</span><span class="sxs-lookup"><span data-stu-id="3b131-465">[Previous](bindings.md)
[Next](secrets.md)</span></span>
