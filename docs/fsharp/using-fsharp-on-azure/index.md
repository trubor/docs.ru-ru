---
title: Использование языка F# в Azure
description: Руководство по использованию служб Azure с F#
author: sylvanc
ms.date: 07/29/2020
ms.custom: devx-track-fsharp
ms.openlocfilehash: 406de0cdef67631ddaaa13f686c9b2093ba5d2ff
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873268"
---
# <a name="using-f-on-azure"></a>Использование языка F# в Azure

F# — это великолепный язык для облачного программирования, который часто используется для создания веб-приложений, облачных служб, размещаемых в облаке микрослужб, а также для масштабируемой обработки данных.

В следующих разделах приведены ресурсы по использованию различных служб Azure с F#.

> [!NOTE]
> Если в этом наборе документации не упомянута определенная служба Azure, обратитесь к документации по Функциям Azure или платформе .NET для этой службы. Некоторые службы Azure не упоминаются здесь, так как не зависят от языка и не требуют документацию для конкретного языка.

## <a name="using-azure-virtual-machines-with-f"></a>Использование виртуальных машин Azure с F\#

Azure поддерживает широкий спектр конфигураций виртуальных машин (ВМ), см. статью [Linux и виртуальные машины Azure](https://azure.microsoft.com/services/virtual-machines/).

Чтобы установить F# на виртуальной машине для выполнения, компиляции кода и/или написания скриптов, см. статьи [Использование F# в Linux](https://fsharp.org/use/linux) и [Использование F# в Windows](https://fsharp.org/use/windows).

## <a name="using-azure-functions-with-f"></a>Использование Функций Azure с F\#

[Функции Azure](https://azure.microsoft.com/services/functions/) — это решение для легкого выполнения небольших фрагментов кода — или "функций" — в облаке. Вы можете ограничиться написанием кода, достаточного для решения поставленной задачи, не беспокоясь о полноценном приложении или инфраструктуре для его запуска. Ваши функции подключены к событиям в службе хранилища Azure и другим размещенным в облаке ресурсам. Данные передаются в функции F# через аргументы функции. Вы можете использовать любой привычный язык разработки, переложив задачи по масштабированию на Azure.

Функции Azure поддерживают F# в качестве первоклассного языка с эффективным, реактивным и масштабируемым выполнением кода F#. В [справочнике разработчика по F# для Функций Azure](/azure/azure-functions/functions-reference-fsharp) приведены ссылки на документацию по использованию языка F# с Функциями Azure.

Другие ресурсы, посвященные использованию Функций Azure и F#.

* [Масштабирование Функций Azure в F# с помощью Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Создание функции Azure в F#](https://www.mnie.me/azurefunctions)
* [Использование поставщика типов Azure с Функциями Azure](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Использование службы хранилища Azure с F\#

Служба хранилища Azure является базовым уровнем служб хранения для современных приложений, которым необходима устойчивость, доступность и масштабируемость для удовлетворения потребностей пользователей. Программы на F# могут напрямую взаимодействовать со службами хранилища Azure посредством методик, описанных в следующих статьях.

* [Начало работы с Хранилищем BLOB-объектов Azure с помощью языка F#](blob-storage.md)
* [Начало работы с Хранилищем файлов Azure с помощью языка F#](file-storage.md)
* [Начало работы с Хранилищем очередей Azure с помощью языка F#](queue-storage.md)
* [Начало работы с Хранилищем таблиц Azure с помощью языка F#](table-storage.md)

Службу хранилища Azure также можно использовать совместно с Функциями Azure посредством декларативной конфигурации вместо явных вызовов API. В статье [Триггеры и привязки Функций Azure для службы хранилища Azure](/azure/azure-functions/functions-bindings-storage) приведены примеры на F#.

## <a name="using-azure-app-service-with-f"></a>Использование Службы приложений Azure с F\#

[Служба приложений Azure](https://azure.microsoft.com/services/app-service/) — это облачная платформа для создания эффективных мобильных и веб-приложений, подключающихся к данным где угодно — в облаке или локальной среде.

* [Пример веб-API Azure на F#](https://github.com/fsprojects/azure-webapi-example)
* [Размещение F# в веб-приложении на платформе Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-on-azure-hdinsight-or-azure-databricks"></a>Использование Apache Spark с F# на платформе Azure HDInsight или Azure Databricks

[Apache Spark для Azure HDInsight](/azure/hdinsight/spark/apache-spark-overview) — это платформа обработки с открытым исходным кодом, в которой выполняются крупномасштабные приложения для анализа данных. [Azure Databricks](/azure/databricks/scenarios/what-is-azure-databricks) — это платформа аналитики на основе Apache Spark, оптимизированная для платформы облачных служб Microsoft Azure. Azure делает развертывание Apache Spark простым и экономичным. Разрабатывайте приложения Spark на языке F# с помощью [.NET для Apache Spark](../../spark/what-is-apache-spark-dotnet.md), набора привязок .NET для Apache Spark.

* [Примеры .NET для Apache Spark на языке F#](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.FSharp.Examples)
* [Установка записных книжек .NET Interactive Jupyter на платформе Azure HDInsight](../../spark/how-to-guides/hdinsight-notebook-installation.md)
* [Отправка заданий Apache Spark в Azure HDInsight](../../spark/how-to-guides/hdinsight-deploy-methods.md)
* [Отправка заданий Apache Spark в Azure Databricks](../../spark/how-to-guides/databricks-deploy-methods.md)

## <a name="using-azure-cosmos-db-with-f"></a>Использование Azure Cosmos DB с F\#

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) — это служба NoSQL для высокодоступных и глобально распределенных приложений.

Azure Cosmos DB можно использовать с F# двумя способами.

1. Путем создания Функций Azure на F#, которые реагируют на коллекции Azure Cosmos DB или вызывают изменения в них. См. раздел [Привязки Azure Cosmos DB для Функций Azure](/azure/azure-functions/functions-bindings-cosmosdb).
2. С помощью [пакета SDK .NET для Azure Cosmos DB для API SQL](/azure/cosmos-db/sql-api-sdk-dotnet). Соответствующие примеры написаны на C#.

## <a name="using-azure-event-hubs-with-f"></a>Использование Центров событий Azure с F\#

[Центры событий Azure](https://azure.microsoft.com/services/event-hubs/) обеспечивают прием телеметрии с веб-сайтов, устройств и из приложений в масштабах облака.

Центры событий Azure можно использовать с F# двумя способами.

1. Посредством создания Функций Azure на F#, активируемых событиями. См. статью [Триггеры Функций Azure для центров событий](/azure/azure-functions/functions-bindings-event-hubs).
2. Посредством [пакета SDK .NET для Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Обратите внимание, что эти примеры написаны на C#.

## <a name="using-azure-notification-hubs-with-f"></a>Использование Центров уведомлений Azure с F\#

[Концентраторы уведомлений Azure](/azure/notification-hubs/) — это многоплатформенная и масштабируемая инфраструктура, позволяющая отправлять мобильные push-уведомления из любой серверной системы (в облаке или локальной среде) для всех мобильных платформ.

Концентраторы уведомлений Azure можно использовать с F# двумя способами.

1. Посредством создания Функций Azure на F#, которые отправляют результаты в концентратор уведомлений. См. статью [Триггеры вывода Функций Azure для концентраторов уведомлений](/azure/azure-functions/functions-bindings-notification-hubs).
2. Посредством [пакета SDK .NET для Azure](/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend). Обратите внимание, что эти примеры написаны на C#.

## <a name="implementing-webhooks-on-azure-with-f"></a>Реализация веб-перехватчиков в Azure с помощью F\#

Объект [webhook](https://en.wikipedia.org/wiki/Webhook) представляет собой обратный вызов, активируемый через веб-запрос. Объекты webhook используются сайтами, например GitHub, для сигнализации о событиях.

Объекты webhook можно реализовать в F# и разместить в Azure с помощью [функции Azure в F# с привязкой webhook](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Использование веб-заданий с F\#

[Веб-задания](/azure/app-service-web/web-sites-create-web-jobs) — это программы, которые можно выполнять в веб-приложении службы приложений тремя способами: по запросу, непрерывно или по расписанию.

[Пример веб-задания на F#](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Реализация таймеров в Azure с помощью F\#

Таймер активирует функции вызова на основе расписания — один раз или регулярно.

Таймеры можно реализовать в F# и разместить в Azure с помощью [функции Azure в F# с триггером таймера](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Развертывание ресурсов Azure и управление ими с помощью скриптов F#

Виртуальные машины Azure можно программно развертывать и контролировать из скриптов F# с помощью API и пакетов Microsoft.Azure.Management. Например, см. статьи [Приступая к работе с библиотеками управления для .NET](/previous-versions/azure/dn722415(v=azure.100)) и [Использование Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Аналогичным образом из скриптов F# можно развернуть и контролировать и другие ресурсы Azure. Например, с помощью скриптов F# вы можете создавать учетные записи хранения, развертывать Облачные службы Azure, создавать экземпляры Azure Cosmos DB и программно управлять Центрами уведомлений Azure.

Использовать скрипты F# для развертывания ресурсов и управления ими в общем случае необязательно. Например, ресурсы Azure также можно развернуть прямо из описаний шаблонов JSON, которые могут быть параметризованы. В статье [Шаблоны Azure Resource Manager](/azure/azure-resource-manager/resource-manager-template-best-practices) приведены примеры, например [шаблоны быстрого запуска Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Другие источники

* [Полная документация по всем службам Azure](/azure/)
