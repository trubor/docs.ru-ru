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
# <a name="what-is-net-for-apache-spark"></a>Что такое .NET для Apache Spark?

[Apache Spark](what-is-spark.md) — это подсистема распределенной обработки общего назначения для анализа больших наборов данных, в несколько терабайт или петабайт. .NET для Apache Spark предоставляет бесплатный, кроссплатформенный и с [открытым кодом](https://github.com/dotnet/spark) механизм поддержки .NET для популярной платформы больших данных с открытым кодом. Теперь вы можете включить возможности Apache Spark в приложения для работы с большими данными, используя привычные языки программирования.

## <a name="why-choose-net-for-apache-spark"></a>Преимущества .NET для Apache Spark

.NET для Apache Spark предоставляет разработчикам возможность работы с .NET и базы кода, которые открывают дверь в мир анализа больших данных. .NET для Apache Spark предоставляет высокопроизводительные интерфейсы API для работы со Spark на C# и F#. С помощью C# и F# можно получить доступ к следующим возможностям:

* DataFrame и SparkSQL для работы со структурированными данными;
* структурированная потоковая передача Spark для работы с потоковыми данными.
* Spark SQL для создания запросов с синтаксисом SQL;
* интеграция машинного обучения для быстрого обучения и прогнозирования (то есть для использования .NET для Apache Spark вместе с [ML.NET](https://dot.net/ml)).

Платформа .NET для Apache Spark совместима с .NET Standard, формальной спецификацией API-интерфейсов .NET, которые доступны во всех реализациях .NET. Это означает, что вы можете использовать .NET для Apache Spark в любом месте, где вы пишете код .NET, что позволяет использовать все знания, навыки, код и библиотеки, которые у вас уже есть.

Платформа .NET для Apache Spark работает в Windows, Linux и macOS на основе .NET Core. Она также работает в Windows на основе .NET Framework. Приложения можно развертывать во всех основных облачных средах, включая Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks и Databricks в AWS.

## <a name="net-for-apache-spark-architecture"></a>Архитектура .NET для Apache Spark

Языковая привязка C# и F# для Spark написана на новом языке взаимодействия Spark, который поддерживает удобный механизм расширения. При создании нового уровня взаимодействия Spark учитывались все передовые рекомендации по расширению языков и оптимизации возможностей взаимодействия и производительности. В долгосрочной перспективе эту расширяемость можно будет использовать для добавления в Spark поддержки других языков.

> [!div class="mx-imgBorder"]
> ![Архитектура .NET для Apache Spark](media/dotnet-spark-architecture.png)

Дополнительные сведения о поддержке взаимодействия для расширений языка Spark можно получить в [этом предложении](https://issues.apache.org/jira/browse/SPARK-26257).

## <a name="net-for-apache-spark-performance"></a>Производительность .NET для Apache Spark

По данным [сравнительного тестирования TPC-H](http://www.tpc.org/tpch/), .NET для Apache Spark в большинстве случаев работает лучше, чем Python и Scala, и вдвое быстрее Python в тех случаях, когда важна производительность определяемой пользователем функции. Постоянно ведется работа по улучшению и тестированию производительности.

Вы можете выполнить собственное сравнительное тестирование, используя предлагаемые тесты из репозитория [.NET для Apache Spark](https://github.com/dotnet/spark/tree/main/benchmark) на сайте GitHub.

## <a name="net-for-apache-spark-roadmap"></a>Программа развития .NET для Apache Spark

Узнайте о краткосрочных и долгосрочных планах, которые включены в официальную [программу развития .NET для Apache Spark](https://github.com/dotnet/spark/blob/main/ROADMAP.md).

## <a name="net-foundation"></a>.NET Foundation

Проект .NET для Apache Spark является частью [.NET Foundation](https://www.dotnetfoundation.org/).

## <a name="contributions"></a>Участие в проекте

Команда .NET для Apache Spark поощряет участие пользователей как в виде открытия проблем в GitHub и работы над ними, так и в виде использования запросов на вытягивание. Начните с поиска [существующей проблемы](https://github.com/dotnet/spark/issues). Если вы ее не нашли, [откройте новую](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Следующие шаги

Попробуйте .NET для Apache Spark в работе.
> [!div class="nextstepaction"]
> [Учебник. Начало работы с .NET для Apache Spark](./tutorials/get-started.md)
