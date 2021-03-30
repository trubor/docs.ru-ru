---
title: Что такое .NET для Apache Spark?
description: Сведения о .NET для Apache Spark, бесплатной кроссплатформенной платформе аналитики больших данных с открытым кодом, которая позволяет пользоваться Spark везде, где вы пишете код .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/09/2020
ms.openlocfilehash: 1fa3ae16334176f0e3e888087078d5b98de9d869
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873202"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="34a82-103">Что такое .NET для Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="34a82-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="34a82-104">[Apache Spark](what-is-spark.md) — это подсистема распределенной обработки общего назначения для анализа больших наборов данных, в несколько терабайт или петабайт.</span><span class="sxs-lookup"><span data-stu-id="34a82-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="34a82-105">.NET для Apache Spark предоставляет бесплатный, кроссплатформенный и с [открытым кодом](https://github.com/dotnet/spark) механизм поддержки .NET для популярной платформы больших данных с открытым кодом. Теперь вы можете включить возможности Apache Spark в приложения для работы с большими данными, используя привычные языки программирования.</span><span class="sxs-lookup"><span data-stu-id="34a82-105">With .NET for Apache Spark, the free, [open-source](https://github.com/dotnet/spark), and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="34a82-106">Преимущества .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="34a82-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="34a82-107">.NET для Apache Spark предоставляет разработчикам возможность работы с .NET и базы кода, которые открывают дверь в мир анализа больших данных.</span><span class="sxs-lookup"><span data-stu-id="34a82-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="34a82-108">.NET для Apache Spark предоставляет высокопроизводительные интерфейсы API для работы со Spark на C# и F#.</span><span class="sxs-lookup"><span data-stu-id="34a82-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="34a82-109">С помощью C# и F# можно получить доступ к следующим возможностям:</span><span class="sxs-lookup"><span data-stu-id="34a82-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="34a82-110">DataFrame и SparkSQL для работы со структурированными данными;</span><span class="sxs-lookup"><span data-stu-id="34a82-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="34a82-111">структурированная потоковая передача Spark для работы с потоковыми данными.</span><span class="sxs-lookup"><span data-stu-id="34a82-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="34a82-112">Spark SQL для создания запросов с синтаксисом SQL;</span><span class="sxs-lookup"><span data-stu-id="34a82-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="34a82-113">интеграция машинного обучения для быстрого обучения и прогнозирования (то есть для использования .NET для Apache Spark вместе с [ML.NET](https://dot.net/ml)).</span><span class="sxs-lookup"><span data-stu-id="34a82-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="34a82-114">Платформа .NET для Apache Spark совместима с .NET Standard, формальной спецификацией API-интерфейсов .NET, которые доступны во всех реализациях .NET.</span><span class="sxs-lookup"><span data-stu-id="34a82-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="34a82-115">Это означает, что вы можете использовать .NET для Apache Spark в любом месте, где вы пишете код .NET, что позволяет использовать все знания, навыки, код и библиотеки, которые у вас уже есть.</span><span class="sxs-lookup"><span data-stu-id="34a82-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="34a82-116">Платформа .NET для Apache Spark работает в Windows, Linux и macOS на основе .NET Core.</span><span class="sxs-lookup"><span data-stu-id="34a82-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="34a82-117">Она также работает в Windows на основе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34a82-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="34a82-118">Приложения можно развертывать во всех основных облачных средах, включая Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks и Databricks в AWS.</span><span class="sxs-lookup"><span data-stu-id="34a82-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="34a82-119">Архитектура .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="34a82-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="34a82-120">Языковая привязка C# и F# для Spark написана на новом языке взаимодействия Spark, который поддерживает удобный механизм расширения.</span><span class="sxs-lookup"><span data-stu-id="34a82-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="34a82-121">При создании нового уровня взаимодействия Spark учитывались все передовые рекомендации по расширению языков и оптимизации возможностей взаимодействия и производительности.</span><span class="sxs-lookup"><span data-stu-id="34a82-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="34a82-122">В долгосрочной перспективе эту расширяемость можно будет использовать для добавления в Spark поддержки других языков.</span><span class="sxs-lookup"><span data-stu-id="34a82-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="34a82-123">![Архитектура .NET для Apache Spark](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="34a82-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="34a82-124">Дополнительные сведения о поддержке взаимодействия для расширений языка Spark можно получить в [этом предложении](https://issues.apache.org/jira/browse/SPARK-26257).</span><span class="sxs-lookup"><span data-stu-id="34a82-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="34a82-125">Производительность .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="34a82-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="34a82-126">По данным [сравнительного тестирования TPC-H](http://www.tpc.org/tpch/), .NET для Apache Spark в большинстве случаев работает лучше, чем Python и Scala, и вдвое быстрее Python в тех случаях, когда важна производительность определяемой пользователем функции.</span><span class="sxs-lookup"><span data-stu-id="34a82-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="34a82-127">Постоянно ведется работа по улучшению и тестированию производительности.</span><span class="sxs-lookup"><span data-stu-id="34a82-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="34a82-128">Вы можете выполнить собственное сравнительное тестирование, используя предлагаемые тесты из репозитория [.NET для Apache Spark](https://github.com/dotnet/spark/tree/main/benchmark) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="34a82-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/main/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="34a82-129">Программа развития .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="34a82-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="34a82-130">Узнайте о краткосрочных и долгосрочных планах, которые включены в официальную [программу развития .NET для Apache Spark](https://github.com/dotnet/spark/blob/main/ROADMAP.md).</span><span class="sxs-lookup"><span data-stu-id="34a82-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/main/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="34a82-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="34a82-131">.NET Foundation</span></span>

<span data-ttu-id="34a82-132">Проект .NET для Apache Spark является частью [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="34a82-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="34a82-133">Участие в проекте</span><span class="sxs-lookup"><span data-stu-id="34a82-133">Contributions</span></span>

<span data-ttu-id="34a82-134">Команда .NET для Apache Spark поощряет участие пользователей как в виде открытия проблем в GitHub и работы над ними, так и в виде использования запросов на вытягивание.</span><span class="sxs-lookup"><span data-stu-id="34a82-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="34a82-135">Начните с поиска [существующей проблемы](https://github.com/dotnet/spark/issues).</span><span class="sxs-lookup"><span data-stu-id="34a82-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="34a82-136">Если вы ее не нашли, [откройте новую](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="34a82-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="34a82-137">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="34a82-137">Next steps</span></span>

<span data-ttu-id="34a82-138">Попробуйте .NET для Apache Spark в работе.</span><span class="sxs-lookup"><span data-stu-id="34a82-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="34a82-139">Учебник. Начало работы с .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="34a82-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
