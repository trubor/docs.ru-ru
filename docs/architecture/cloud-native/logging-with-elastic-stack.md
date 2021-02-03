---
title: Ведение журналов с использованием эластичного стека
description: Ведение журналов с помощью эластичного стека, Logstash и Kibana
ms.date: 01/19/2021
ms.openlocfilehash: ebe7eef16d3b1a73d0fd3a010a509bbaf7be3fd5
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505821"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="9524d-103">Ведение журналов с использованием эластичного стека</span><span class="sxs-lookup"><span data-stu-id="9524d-103">Logging with Elastic Stack</span></span>

<span data-ttu-id="9524d-104">Существует множество хороших средств централизованного ведения журналов, которые изменяются по затратам от бесплатных средств с открытым исходным кодом до более дорогостоящих вариантов.</span><span class="sxs-lookup"><span data-stu-id="9524d-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="9524d-105">Во многих случаях бесплатные инструменты должны быть как или более надежными, чем оплаченные предложения.</span><span class="sxs-lookup"><span data-stu-id="9524d-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="9524d-106">Одним из таких инструментов является сочетание трех компонентов с открытым исходным кодом: Эластичный Поиск, Logstash и Kibana.</span><span class="sxs-lookup"><span data-stu-id="9524d-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span>

<span data-ttu-id="9524d-107">Вместе эти средства называются стеком эластичных баз данных или ELK.</span><span class="sxs-lookup"><span data-stu-id="9524d-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="9524d-108">Эластичный стек</span><span class="sxs-lookup"><span data-stu-id="9524d-108">Elastic Stack</span></span>

<span data-ttu-id="9524d-109">Эластичный стек — это мощный вариант для сбора информации из кластера Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="9524d-109">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="9524d-110">Kubernetes поддерживает отправку журналов в конечную точку Elasticsearch, и в [большинстве случаев](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)все, что необходимо для начала работы, — задать переменные среды, как показано на рис. 7-5:</span><span class="sxs-lookup"><span data-stu-id="9524d-110">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="9524d-111">**Рис. 7-5**.</span><span class="sxs-lookup"><span data-stu-id="9524d-111">**Figure 7-5**.</span></span> <span data-ttu-id="9524d-112">Переменные конфигурации для Kubernetes</span><span class="sxs-lookup"><span data-stu-id="9524d-112">Configuration variables for Kubernetes</span></span>

<span data-ttu-id="9524d-113">Этот шаг устанавливает Elasticsearch в кластере и целевой объект, отправляя в него все журналы кластера.</span><span class="sxs-lookup"><span data-stu-id="9524d-113">This step will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="9524d-114">![Пример панели мониторинга Kibana, в которой показаны результаты запроса к журналам, полученным от Kubernetes ](./media/kibana-dashboard.png)
 **рис. 7-6**.</span><span class="sxs-lookup"><span data-stu-id="9524d-114">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="9524d-115">Пример панели мониторинга Kibana, в которой показаны результаты запроса к журналам, принимаемым из Kubernetes</span><span class="sxs-lookup"><span data-stu-id="9524d-115">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="9524d-116">Каковы преимущества эластичного стека?</span><span class="sxs-lookup"><span data-stu-id="9524d-116">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="9524d-117">Эластичный стек обеспечивает централизованное ведение журналов с экономичным, масштабируемым и облачным способом.</span><span class="sxs-lookup"><span data-stu-id="9524d-117">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="9524d-118">Его пользовательский интерфейс упрощает анализ данных, позволяя тратить время на получение ценных сведений из данных вместо борьбы с интерфейсом неуклюжим.</span><span class="sxs-lookup"><span data-stu-id="9524d-118">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="9524d-119">Он поддерживает широкий спектр входных данных, так как распределенное приложение охватывает больше и разных типов служб, поэтому вы можете продолжать работать с данными журналов и метрик в системе.</span><span class="sxs-lookup"><span data-stu-id="9524d-119">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="9524d-120">Эластичный стек также поддерживает быстрый поиск даже в больших наборах данных, что делает возможным даже для больших приложений запись подробных данных в журнал и по-прежнему иметь возможность видеть их в удобном для себя виде.</span><span class="sxs-lookup"><span data-stu-id="9524d-120">The Elastic Stack also supports fast searches even across large data sets, making it possible even for large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="9524d-121">Logstash</span><span class="sxs-lookup"><span data-stu-id="9524d-121">Logstash</span></span>

<span data-ttu-id="9524d-122">Первый компонент — [Logstash](https://www.elastic.co/products/logstash).</span><span class="sxs-lookup"><span data-stu-id="9524d-122">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="9524d-123">Это средство используется для сбора данных журнала из большого спектра различных источников.</span><span class="sxs-lookup"><span data-stu-id="9524d-123">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="9524d-124">Например, Logstash может считывать журналы с диска, а также отправлять сообщения из библиотек ведения журналов, например [Serilog](https://serilog.net/).</span><span class="sxs-lookup"><span data-stu-id="9524d-124">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="9524d-125">Logstash может выполнять некоторую базовую фильтрацию и расширение журналов по мере их поступления.</span><span class="sxs-lookup"><span data-stu-id="9524d-125">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="9524d-126">Например, если журналы содержат IP-адреса, Logstash можно настроить для выполнения географического поиска и получения страны или даже города происхождения сообщения.</span><span class="sxs-lookup"><span data-stu-id="9524d-126">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span>

<span data-ttu-id="9524d-127">Serilog — это библиотека ведения журналов для языков .NET, позволяющая выполнять параметризованное ведение журнала.</span><span class="sxs-lookup"><span data-stu-id="9524d-127">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="9524d-128">Вместо создания текстового сообщения журнала, включающего поля, параметры хранятся отдельно.</span><span class="sxs-lookup"><span data-stu-id="9524d-128">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="9524d-129">Эта библиотека обеспечивает более интеллектуальную фильтрацию и поиск.</span><span class="sxs-lookup"><span data-stu-id="9524d-129">This library allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="9524d-130">Пример конфигурации Serilog для записи в Logstash показан на рис. 7-7.</span><span class="sxs-lookup"><span data-stu-id="9524d-130">A sample Serilog configuration for writing to Logstash appears in Figure 7-7.</span></span>

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="9524d-131">**Рис. 7-7**.</span><span class="sxs-lookup"><span data-stu-id="9524d-131">**Figure 7-7**.</span></span> <span data-ttu-id="9524d-132">Serilog config для записи сведений журнала непосредственно в logstash по протоколу HTTP</span><span class="sxs-lookup"><span data-stu-id="9524d-132">Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="9524d-133">Logstash будет использовать конфигурацию, подобную показанной на рис. 7-8.</span><span class="sxs-lookup"><span data-stu-id="9524d-133">Logstash would use a configuration like the one shown in Figure 7-8.</span></span>

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

<span data-ttu-id="9524d-134">**Рис. 7-8**.</span><span class="sxs-lookup"><span data-stu-id="9524d-134">**Figure 7-8**.</span></span> <span data-ttu-id="9524d-135">Конфигурация Logstash для использования журналов из Serilog</span><span class="sxs-lookup"><span data-stu-id="9524d-135">A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="9524d-136">Для сценариев, в которых не требуется много операций с журналами, существует альтернатива [Logstash, известного как](https://www.elastic.co/products/beats)незначительное.</span><span class="sxs-lookup"><span data-stu-id="9524d-136">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="9524d-137">Ритм — это семейство средств, которое может собирать разнообразные данные из журналов в данные сети и сведения о времени работы.</span><span class="sxs-lookup"><span data-stu-id="9524d-137">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="9524d-138">Многие приложения будут использовать как Logstash, так и ритмы.</span><span class="sxs-lookup"><span data-stu-id="9524d-138">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="9524d-139">После того, как журналы собраны с помощью Logstash, им нужно поместить их в любое место.</span><span class="sxs-lookup"><span data-stu-id="9524d-139">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="9524d-140">Хотя Logstash поддерживает множество различных выходов, одна из самых интересных — эластичный Поиск.</span><span class="sxs-lookup"><span data-stu-id="9524d-140">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="9524d-141">Эластичный поиск</span><span class="sxs-lookup"><span data-stu-id="9524d-141">Elastic search</span></span>

<span data-ttu-id="9524d-142">Эластичный Поиск — это мощная поисковая система, которая может индексировать журналы по мере их поступления.</span><span class="sxs-lookup"><span data-stu-id="9524d-142">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="9524d-143">Он позволяет быстро выполнять запросы к журналам.</span><span class="sxs-lookup"><span data-stu-id="9524d-143">It makes running queries against the logs quick.</span></span> <span data-ttu-id="9524d-144">Эластичный Поиск может обрабатывать огромные объемы журналов, и в крайних случаях их можно масштабировать на нескольких узлах.</span><span class="sxs-lookup"><span data-stu-id="9524d-144">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span>

<span data-ttu-id="9524d-145">Сообщения журнала, которые были созданы для хранения параметров или которых были разделены с помощью обработки Logstash, можно запрашивать напрямую, так как Elasticsearch сохраняет эти сведения.</span><span class="sxs-lookup"><span data-stu-id="9524d-145">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="9524d-146">Запрос, выполняющий поиск первых 10 страниц, посещенных `jill@example.com` , отображается на рис. 7-9.</span><span class="sxs-lookup"><span data-stu-id="9524d-146">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-9.</span></span>

```json
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

<span data-ttu-id="9524d-147">**Рис. 7-9**.</span><span class="sxs-lookup"><span data-stu-id="9524d-147">**Figure 7-9**.</span></span> <span data-ttu-id="9524d-148">Запрос Elasticsearch для поиска 10 ведущих страниц, посещенных пользователем</span><span class="sxs-lookup"><span data-stu-id="9524d-148">An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="9524d-149">Визуализация информации с помощью веб-панелей мониторинга Kibana</span><span class="sxs-lookup"><span data-stu-id="9524d-149">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="9524d-150">Последним компонентом стека является Kibana.</span><span class="sxs-lookup"><span data-stu-id="9524d-150">The final component of the stack is Kibana.</span></span> <span data-ttu-id="9524d-151">Это средство используется для предоставления интерактивных визуализаций на веб-панели мониторинга.</span><span class="sxs-lookup"><span data-stu-id="9524d-151">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="9524d-152">Панели мониторинга могут создаваться даже пользователями, которые не являются техническими.</span><span class="sxs-lookup"><span data-stu-id="9524d-152">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="9524d-153">Большинство данных, находящихся в Elasticsearch индексе, могут быть добавлены на панели мониторинга Kibana.</span><span class="sxs-lookup"><span data-stu-id="9524d-153">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="9524d-154">Отдельные пользователи могут иметь разную панель мониторинга, и Kibana обеспечивает эту настройку, позволяя пользователям просматривать панели мониторинга.</span><span class="sxs-lookup"><span data-stu-id="9524d-154">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span>

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="9524d-155">Установка эластичного стека в Azure</span><span class="sxs-lookup"><span data-stu-id="9524d-155">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="9524d-156">Эластичный стек можно установить в Azure множеством способов.</span><span class="sxs-lookup"><span data-stu-id="9524d-156">The Elastic stack can be installed on Azure in many ways.</span></span> <span data-ttu-id="9524d-157">Как всегда, можно [подготавливать виртуальные машины и устанавливать эластичный стек на них напрямую](/azure/virtual-machines/linux/tutorial-elasticsearch).</span><span class="sxs-lookup"><span data-stu-id="9524d-157">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="9524d-158">Этот вариант является предпочтительным для некоторых опытных пользователей, так как он обеспечивает наивысшую степень настройки.</span><span class="sxs-lookup"><span data-stu-id="9524d-158">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="9524d-159">При развертывании на основе инфраструктуры в качестве службы вы узнаете о значительных затратах на управление, которые применяют этот путь, чтобы стать владельцем всех задач, связанных с инфраструктурой, таких как обеспечение безопасности компьютеров и обновление исправлений.</span><span class="sxs-lookup"><span data-stu-id="9524d-159">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span>

<span data-ttu-id="9524d-160">Параметр с меньшими издержками заключается в использовании одного из многих контейнеров DOCKER, для которых уже настроен эластичный стек.</span><span class="sxs-lookup"><span data-stu-id="9524d-160">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="9524d-161">Эти контейнеры можно удалить в существующий кластер Kubernetes и запустить вместе с кодом приложения.</span><span class="sxs-lookup"><span data-stu-id="9524d-161">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="9524d-162">Контейнер [себп/Elk](https://elk-docker.readthedocs.io/) — это хорошо документированный и протестированный контейнер эластичного стека.</span><span class="sxs-lookup"><span data-stu-id="9524d-162">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="9524d-163">Другой вариант — [недавно объявленное предложение Elk как услуга](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="9524d-163">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="9524d-164">Ссылки</span><span class="sxs-lookup"><span data-stu-id="9524d-164">References</span></span>

- [<span data-ttu-id="9524d-165">Установка эластичного стека в Azure</span><span class="sxs-lookup"><span data-stu-id="9524d-165">Install Elastic Stack on Azure</span></span>](/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="9524d-166">[Назад](observability-patterns.md)
>[Вперед](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="9524d-166">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
