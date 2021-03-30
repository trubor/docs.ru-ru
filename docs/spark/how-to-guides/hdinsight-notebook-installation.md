---
title: Установка .NET для Apache Spark в записных книжках Jupyter Notebook в кластерах Spark Azure HDInsight
description: Узнайте, как установить .NET для Apache Spark в записных книжках Jupyter Notebook Azure HDInsight.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 100991a5c6e07f9e7c21a64f53310f91d381873c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875503"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Установка .NET для Apache Spark в записных книжках Jupyter Notebook в кластерах Spark Azure HDInsight

В этой статье показано, как установить .NET для Apache Spark в записных книжках Jupyter Notebook в кластерах Spark Azure HDInsight. Вы можете развернуть .NET для Apache Spark в кластерах Azure HDInsight с помощью командной строки и портала Azure (дополнительные сведения см. в статье [Учебник. Развертывание приложения .NET для Apache Spark в Azure HDInsight](../tutorials/hdinsight-deployment.md)). Обратите внимание, что записные книжки предоставляют более интерактивный и итеративный интерфейс.

Кластеры Azure HDInsight поставляются с записными книжками Jupyter Notebook, поэтому вам нужно лишь настроить их для запуска .NET для Apache Spark. Для использования .NET для Apache Spark в записных книжках Jupyter Notebook требуется C# REPL, чтобы построчно выполнить код C# и при необходимости сохранить состояние выполнения. Средство [Try .NET](https://github.com/dotnet/try) интегрировано в качестве официальной версии .NET REPL.

Чтобы включить .NET для Apache Spark через интерфейс записных книжек Jupyter Notebook, необходимо выполнить несколько действий вручную с помощью [Ambari](/azure/hdinsight/hdinsight-hadoop-manage-ambari) и отправить [действия скрипта](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) в кластере HDInsight Spark.

> [!NOTE]
> Эта *экспериментальная* функция, и она не поддерживается командой HDInsight Spark.

## <a name="prerequisites"></a>Предварительные требования

Создайте кластер [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight), если его у вас еще нет.

1. Перейдите на [портал Azure](https://portal.azure.com) и выберите **Создать ресурс**.

1. Создайте ресурс кластера Azure HDInsight. Во время создания кластера выберите **Spark 2.4** и **HDI 4.0**.

## <a name="install-net-for-apache-spark"></a>Установка .NET для Apache Spark

На портале Azure выберите **кластер HDInsight Spark**, созданный на предыдущем шаге.

### <a name="stop-the-livy-server"></a>Остановка работы сервера Livy

1. На портале щелкните **Обзор**, а затем выберите **Домашняя страница Ambari**. При появлении запроса введите учетные данные для входа в кластер.

   ![Выбор домашней страницы Ambari в панели мониторинга кластеров](./media/hdinsight-notebook-installation/select-ambari.png)

2. Выберите **Spark2** в меню навигации слева, а затем — **LIVY FOR SPARK2 SERVER** (LIVY для сервера SPARK2).

   ![Выбор Livy для сервера Spark2](./media/hdinsight-notebook-installation/select-livyserver.png)

3. Выберите узел **hn0…**

   ![Узлы, с выбранным именем "hno..."](./media/hdinsight-notebook-installation/select-host.png)

4. Щелкните многоточие рядом с **Livy for Spark2 Server** (Сервер Livy для Spark2), а затем выберите **Остановить**. При появлении запроса щелкните **ОК**, чтобы продолжить.

   Остановка работы сервера Livy для Spark2.
   ![Выбор знака многоточия и пункта "Остановить"](./media/hdinsight-notebook-installation/stop-server.png)

5. Повторите предыдущие шаги для узла **hn1…**

### <a name="submit-an-hdinsight-script-action"></a>Отправка действия скрипта HDInsight

1. `install-interactive-notebook.sh` — это скрипт, который устанавливает .NET для Apache Spark и вносит изменения в Apache Livy и Sparkmagic. Прежде чем отправить действия скрипта в HDInsight, необходимо создать и отправить `install-interactive-notebook.sh`.

   Создайте файл **install-interactive-notebook.sh** на локальном компьютере и вставьте содержимое [nstall-interactive-notebook.sh contentss](https://raw.githubusercontent.com/dotnet/spark/main/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).

   Отправьте скрипт в [универсальный код ресурса (URI)](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions), который доступен из кластера HDInsight. Например, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. Выполните скрипт `install-interactive-notebook.sh` в кластере с помощью [действий скриптов HDInsight](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

   Вернитесь к кластеру HDI на портале Azure и выберите **Действия скрипта** из параметров слева. Вы отправляете одно действие скрипта, чтобы развернуть .NET для Apache Spark REPL в кластере HDInsight Spark. Используйте следующие параметры:

   |Свойство.  |Описание  |
   |---------|---------|
   | Тип скрипта | Другой |
   | name | *Установка .NET для Apache Spark в интерфейс интерактивной Notebook*. |
   | URI bash-скрипта | Универсальный код ресурса (URI), по которому был отправлен файл `install-interactive-notebook.sh`. |
   | Типы узлов| Головной и рабочий. |
   | Параметры | Версия .NET для Apache Spark. Вы можете ознакомиться с [выпусками .NET для Apache Spark](https://github.com/dotnet/spark/releases). Например, если вы хотите установить Sparkdotnet версии 1.0.0, параметры будут следующими: `1.0.0`.

   Перейдите к следующему шагу, когда рядом с состоянием действия скрипта отображаются зеленые отметки.

### <a name="start-the-livy-server"></a>Запуск сервера Livy

Выполните инструкции, приведенные в разделе [Остановка работы сервера Livy](#stop-the-livy-server), чтобы **запустить** (а не **остановить**) сервер Livy для Spark2 узлов **hn0** и **hn1**.

### <a name="set-up-spark-default-configurations"></a>Настройка конфигураций по умолчанию Spark

1. На портале щелкните **Обзор**, а затем выберите **Домашняя страница Ambari**. При появлении запроса введите учетные данные для входа в кластер.

2. Выберите **Spark2** и **CONFIGS** (Конфигурации). Затем выберите группу **Custom spark2-defaults**.

   ![Вкладка конфигураций в Ambari](./media/hdinsight-notebook-installation/spark-configs.png)

3. Выберите **Добавить свойство** , чтобы добавить параметры Spark по умолчанию.

   ![Добавление свойства](./media/hdinsight-notebook-installation/add-property.png)

   Существует три отдельных свойства. Добавьте их поочередно, используя тип свойства **Текст** в режиме добавления одного свойства. Убедитесь, что до или после ключей и значений нет дополнительных пробелов.

   * **Свойство 1**.
       * Ключ:&ensp;&ensp;`spark.dotnet.shell.command`.
       * Значение: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Свойство 2**. Используйте версию .NET для Apache Spark, которая была включена в предыдущее действие скрипта.
       * Ключ:&ensp;&ensp;`spark.dotnet.packages`.
       * Значение: `["nuget: Microsoft.Spark, 1.0.0", "nuget: Microsoft.Spark.Extensions.Delta, 1.0.0"]`

   * **Свойство 3**.
       * Ключ:&ensp;&ensp;`spark.dotnet.interpreter`.
       * Значение: `try`

   Например, на следующем рисунке показан параметр для добавления свойства 1:

   ![Добавления текстового свойства](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   После добавления трех свойств выберите **SAVE** (Сохранить). Если появится экран предупреждения с рекомендациями конфигурации, выберите **PROCEED ANYWAY** (Продолжить).

4. Перезапустите затронутые компоненты.

   После добавления новых свойств необходимо перезапустить компоненты, которые были затронуты изменениями. В верхней части выберите **RESTART** (Перезапустить), а затем — **Restart All Affected** (Перезапустить все затронутые) из раскрывающегося списка.

   ![Вкладка конфигураций с выделенным пунктом "Перезапустить" > "Перезапустить все затронутые"](./media/hdinsight-notebook-installation/restart-affected.png)

   При появлении запроса выберите **CONFIRM RESTART ALL** (Подтвердить перезапуск всех), чтобы продолжить, а затем нажмите кнопку **ОК** для завершения работы.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Отправка заданий с помощью Jupyter Notebook

После завершения предыдущих шагов можно отправить задания .NET для Apache Spark с помощью записных книжек Jupyter Notebook.

1. Создайте записную книжку .NET для Apache Spark. Запустите Jupyter Notebook из кластера HDI на портале Azure.

   ![Запуск Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   Затем выберите **New** (Создать)  >  **.NET Spark (C#)** , чтобы создать записную книжку.

   ![Портативный компьютер Jupyter](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Отправьте задания с помощью .NET для Apache Spark.

   Чтобы создать кадр данных, используйте следующий фрагмент кода:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Создание DataFrame с демонстрацией выполнения команды](./media/hdinsight-notebook-installation/create-df.png)

   Используйте следующий фрагмент кода, чтобы зарегистрировать определяемую пользователем функцию (UDF) и использовать ее с кадрами данных:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Регистрация определяемой пользователем функции и ее использование](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Следующие шаги

* [Развертывание приложения .NET для Apache Spark в Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Документация по HDInsight](/azure/hdinsight/)
