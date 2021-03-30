---
title: Развертывание приложения .NET для Apache Spark в Databricks
description: Узнайте, как развернуть приложение .NET для Apache Spark в Databricks.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e751953937279a5f9f78f777bac8a5ca510a2f87
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876972"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Учебник. Развертывание приложения .NET для Apache Spark в Databricks

В этом учебнике описывается, как развернуть приложение в облаке с помощью Azure Databricks, платформу для аналитики на базе Apache Spark. Платформа настраивается одним щелчком, упрощает рабочие процессы и предоставляет интерактивную рабочую область для совместной работы.

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
>
> - создание рабочей области Azure Databricks;
> - Опубликовать приложение .NET для Apache Spark.
> - Создать задание Spark и кластер Spark.
> - Запустить приложение в кластере Spark.

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, сделайте следующее.

* Если у вас нет учетной записи, вы можете создать [бесплатную учетную запись](https://azure.microsoft.com/free/dotnet/).
* Войдите на [портале Azure](https://portal.azure.com/).
* Пройдите учебник [.NET для Apache Spark — начало работы за 10 минут](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro).

## <a name="create-an-azure-databricks-workspace"></a>Создание рабочей области Azure Databricks

> [!Note]
> Инструкции из этого руководство нельзя выполнять с **бесплатной пробной версией подписки**.
> Если у вас есть бесплатная учетная запись, перейдите к профилю и измените подписку на подписку с **оплатой по мере использования**. Дополнительные сведения см. на странице [создания бесплатной учетной записи Azure](https://azure.microsoft.com/free/dotnet/). Затем [удалите предельную сумму расходов](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit) и [запросите увеличение квоты](/azure/azure-supportability/resource-manager-core-quotas-request) на ЦП в своем регионе. При создании рабочей области Azure Databricks можно выбрать ценовую категорию **Пробная версия ("Премиум" — 14 дней бесплатно (DBU))** для предоставления рабочей области доступа к бесплатным DBU Azure Databricks уровня "Премиум" на 14 дней.

В этом разделе вы создадите рабочую область Azure Databricks с помощью портала Azure.

1. На портале Azure выберите **Создать ресурс** > **Analytics** > **Azure Databricks**.

   ![Создание ресурса Azure Databricks на портале Azure](./media/databricks-deployment/create-databricks-resource.png)

2. В разделе **службы Azure Databricks** укажите значения для создания рабочей области Databricks.

    |Свойство.  |Описание  |
    |---------|---------|
    |**Имя рабочей области**     | Укажите имя рабочей области Databricks.        |
    |**Подписка**     | Выберите подписку Azure в раскрывающемся списке.        |
    |**Группа ресурсов**     | Укажите, следует ли создать новую группу ресурсов или использовать имеющуюся. Группа ресурсов — это контейнер, содержащий связанные ресурсы для решения Azure. Дополнительные сведения см. в [обзоре группы ресурсов Azure](/azure/azure-resource-manager/resource-group-overview). |
    |**Расположение**     | Выберите предпочитаемый регион. Доступные регионы см. в статье о [доступности служб Azure по регионам](https://azure.microsoft.com/regions/services/).        |
    |**Ценовая категория**     |  Вы можете выбрать уровень **Стандартный** или **Премиум** или воспользоваться **бесплатной пробной версией**. Дополнительные сведения об этих ценовых категориях см. на [странице цен на Databricks](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Виртуальная сеть**     |   Нет       |

3. Выберите **Создать**. Создание рабочей области займет несколько минут. Во время создания рабочей области состояние развертывания можно просмотреть в области **Уведомления**.

## <a name="install-azure-databricks-tools"></a>Установка средств Azure Databricks

Для подключения к кластерам Azure Databricks и передачи файлов с локального компьютера можно использовать **интерфейс командной строки Databricks**. В кластерах Databricks доступ к файлам осуществляется через DBFS (файловая система Databricks).

1. Для работы интерфейса командной строки Databricks требуется Python 3.6 или более поздней версии. Если у вас уже установлен Python, можно перейти к следующему шагу.

   **Для Windows:**

   [Загрузка Python для Windows](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Для Linux:** Python предустановлен в большинстве дистрибутивов Linux. Выполните следующую команду, чтобы узнать, какая версия установлена:

   ```bash
   python3 --version
   ```

2. Установите интерфейс командной строки Databricks с помощью pip. В Python 3.4 и более поздних версий pip включен по умолчанию. Используйте pip3 для Python 3. Выполните следующую команду:

   ```bash
   pip3 install databricks-cli
   ```

3. После установки интерфейса командной строки Databricks откройте новую командную строку и выполните команду `databricks`. Если вы получаете **внутреннюю или внешнюю ошибку команды о том, что Databricks не распознан**, убедитесь, что открыли новую командную строку.

## <a name="set-up-azure-databricks"></a>Настройка Azure Databricks

Теперь, когда интерфейс командной строки Databricks установлен, необходимо настроить сведения о проверке подлинности.

1. В интерфейсе командной строки Databricks выполните команду `databricks configure --token`.

2. После выполнения команды конфигурации будет предложено ввести узел. Поддерживается следующий формат: `https://<Location>.azuredatabricks.net`. Например, если вы выбрали **eastus2** при создании службы Azure Databricks, узел будет `https://eastus2.azuredatabricks.net`.

3. После ввода узла вам будет предложено ввести маркер. На портале Azure выберите **Запустить рабочую область**, чтобы запустить рабочую область Azure Databricks.

   ![Запуск рабочей области Azure Databricks](./media/databricks-deployment/launch-databricks-workspace.png)

4. На домашней странице рабочей области выберите **Параметры пользователя**.

   ![Параметры пользователя рабочей области Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. На странице "Параметры пользователя" можно создать новый маркер. Скопируйте созданный маркер и вставьте его обратно в командную строку.

   ![Создание нового маркера доступа в рабочей области Azure Databricks](./media/databricks-deployment/generate-token.png)

Теперь вы можете получить доступ ко всем кластерам Azure Databricks, которые вы создаете, и отправить файлы в DBFS.

## <a name="download-worker-dependencies"></a>Загрузка зависимостей рабочей роли

> [!Note]
> Azure и AWS Databricks работают под управлением Linux. Поэтому если вы хотите развернуть приложение в Databricks, оно должно быть совместимо с .NET Standard, а для его компиляции необходимо использовать компилятор .NET Core.

1. Microsoft.Spark.Worker помогает Apache Spark запускать ваше приложение, например пользовательские функции (UDF), которые вы написали. Загрузите [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).

2. *install-worker.sh* — это скрипт, который позволяет копировать зависимые файлы .NET для Apache Spark в узлы кластера.

   Создайте новый файл с именем **install-worker.sh** на локальном компьютере и вставьте [содержимое файла install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/main/deployment/install-worker.sh), расположенного на сайте GitHub.

3. *db-init.sh* — это скрипт, который устанавливает зависимости на кластер Databricks Spark.

   Создайте новый файл с именем **db-init.sh** на локальном компьютере и вставьте [содержимое файла db-init.sh](https://github.com/dotnet/spark/blob/main/deployment/db-init.sh), расположенного на сайте GitHub.

   В только что созданном файле задайте для переменной `DOTNET_SPARK_RELEASE` значение `https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz`. Оставьте остальную часть файла *db-init.sh* без изменений.

> [!Note]
> Если вы используете Windows, убедитесь, что для окончаний строк в скриптах *install-worker.sh* и *db-init.sh* используется стиль Unix (LF). Можно изменять окончания строк в текстовых редакторах, таких как Notepad++ и Atom.

## <a name="publish-your-app"></a>Публикация приложения

Затем вы публикуете приложение *mySparkApp*, созданное в учебнике [.NET для Apache Spark — начало работы за 10 минут](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro), чтобы кластер Spark имел доступ ко всем файлам, которые необходимы для запуска приложения.

1. Для публикации *mySparkApp* выполните следующие команды:

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. Выполните следующие задачи и заархивируйте опубликованные файлы приложения, чтобы их можно было легко передать в кластер Databricks Spark.

   **В Windows:**

   Перейдите в каталог mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64. Затем щелкните правой кнопкой мыши папку **Publish** и выберите **Отправить > Сжатая ZIP-папка**. Назовите папку **publish.zip**.

   **В Linux выполните следующую команду:**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Отправка файлов

В этом разделе вы отправите в DBFS несколько файлов, чтобы в кластере было все необходимое для запуска приложения в облаке. Каждый раз при отправке файла в DBFS убеждайтесь, что вы находитесь в каталоге, где расположен этот файл на компьютере.

1. Выполните следующие команды, чтобы отправить *db-init.sh*, *install-worker.sh* и *Microsoft.Spark.Worker* в DBFS:

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz dbfs:/spark-dotnet/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz
   ```

2. Выполните следующие команды, чтобы отправить оставшиеся файлы, необходимые кластеру для запуска приложения: ZIP-папку публикации, *input.txt* и *microsoft-spark-2-4_2.11-1.0.0.jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.1\ubuntu.16.04-x64 directory
   databricks fs cp publish.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2-4_2.11-1.0.0.jar dbfs:/spark-dotnet/microsoft-spark-2-4_2.11-1.0.0.jar
   ```

## <a name="create-a-job"></a>Создание задания

Приложение выполняется на Azure Databricks с помощью задания, которое выполняет **spark-submit**. Это команда, используемая для запуска заданий .NET для Apache Spark.

1. В рабочей области Azure Databricks нажмите на значок **Задания**, а затем **+ Создать задание**.

   ![Создание задания Azure Databricks](./media/databricks-deployment/create-job.png)

2. Выберите название задания, а затем нажмите **Настройка spark-submit**.

   ![Настройка spark-submit для задания Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. Вставьте следующие параметры в конфигурацию задания. Затем выберите **Подтвердить**.

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2-4_2.11-1.0.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Создание кластера

1. Перейдите к своему заданию и выберите **Изменить**, чтобы настроить кластер задания.

2. Выберите для кластера **Spark 2.4.1**. Затем выберите **Дополнительные параметры** > **Скрипты инициализации**. Введите следующий путь к скрипту инициализации: `dbfs:/spark-dotnet/db-init.sh`.

   ![Настройка кластера Spark в Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. Выберите **Подтвердить**, чтобы подтвердить параметры кластера.

## <a name="run-your-app"></a>Запуск приложения

1. Перейдите к своему заданию и выберите **Запустить сейчас**, чтобы запустить задание в только что настроенном кластере Spark.

2. Создание кластера задания может занять несколько минут. После создания задание будет отправлено, и вы сможете просмотреть выходные данные.

3. Выберите **Кластеры** в меню слева, а затем имя и выполнение задания.

4. Выберите **Журналы драйверов**, чтобы просмотреть выходные данные задания. После выполнения приложения отображается та же таблица подсчета слов из локального запуска начального приложения, записанная на консоль стандартного потока вывода.

   ![Таблица выходных данных задания Azure Databricks](./media/databricks-deployment/table-output.png)

   Поздравляем, вы запустили свое первое приложение .NET для Apache Spark в Azure Databricks!

## <a name="clean-up-resources"></a>Очистка ресурсов

Если рабочая область Databricks больше не нужна, можно удалить ресурс Azure Databricks на портале Azure. Кроме того, можно выбрать имя группы ресурсов, чтобы открыть страницу группы ресурсов, а затем щелкнуть **Удалить группу ресурсов**.

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы развернули приложение .NET для Apache Spark в Databricks. Дополнительные сведения о Databricks см. в документации по Azure Databricks.

> [!div class="nextstepaction"]
> [Документация по Azure Databricks](/azure/azure-databricks/)
