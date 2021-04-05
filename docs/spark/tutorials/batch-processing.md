---
title: Учебник по выполнению пакетной обработки с помощью .NET для Apache Spark
description: Узнайте, как выполнять пакетную обработку с помощью .NET для Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 28674c583466bb4873581c9d233b9a508019b045
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876946"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Учебник. Выполнение пакетной обработки с помощью .NET для Apache Spark

В этом учебнике вы узнаете, как выполнять пакетную обработку с помощью .NET для Apache Spark. Пакетная обработка — это преобразование неактивных данных. Это означает, что исходные данные уже загружены в хранилище данных.

Обычно выполняется пакетная обработка больших неструктурированных наборов данных, которые необходимо подготовить для дальнейшего анализа. Обработка журналов и хранение данных — это типичные сценарии пакетной обработки. В таких сценариях вы анализируете сведения о проектах GitHub, например количество вилок различных проектов или сведения об обновлении проектов.

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
>
> * создать и выполнить приложение .NET для Apache Spark;
> * считывать данные в DataFrame и подготовить их для анализа;
> * обрабатывать данные с помощью Spark SQL.

## <a name="prerequisites"></a>Предварительные требования

Если вы впервые используете .NET для Apache Spark, ознакомьтесь с учебником [Учебник. Начало работы с .NET для Apache Spark](get-started.md), чтобы узнать, как подготовить среду и запустить первое приложение .NET для Apache Spark.

## <a name="download-the-sample-data"></a>Скачивание примера данных

[GHTorrent](http://ghtorrent.org/) отслеживает все открытые события GitHub, например информацию о проектах, фиксации и наблюдателях, а также сохраняет события и их структуру в базах данных. Данные, собранные за разные временные периоды, доступны в виде загружаемых архивов. Так как файлы дампа очень большие, в этом учебнике используется [их сокращенная версия](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv), которую можно скачать на сайте GitHub.

> [!NOTE]
> Набор данных GHTorrent распространяется по схеме двойного лицензирования ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)). Для некоммерческих целей (в том числе для образовательных, исследовательских и личных) набор данных распространяется по [лицензии CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/).

## <a name="create-a-console-application"></a>Создание консольного приложение

1. В командной строке выполните следующие команды, чтобы создать новое консольное приложение:

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   Команда `dotnet` создаст для вас приложение `new` типа `console`. Параметр `-o` создаст каталог с именем *mySparkBatchApp*, в котором хранится приложение и используемые им файлы. Команда `cd mySparkBatchApp` изменит каталог на только что созданный каталог приложения.

1. Чтобы использовать .NET для Apache Spark в приложении, установите пакет Microsoft.Spark. В консоли выполните следующую команду:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Создание SparkSession

1. Добавьте следующие дополнительные инструкции `using` в начало файла *Program.cs* приложения *mySparkBatchApp*.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Добавьте приведенный ниже код к пространству имен проекта. *s_referenceData* будет использоваться позже в программе для фильтрации на основе даты.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Добавьте следующий код в метод Main, чтобы установить новый сеанс SparkSession. SparkSession является точкой входа для программирования Spark через API DataSet и DataFrame. Вызов объекта `spark` позволяет получить доступ к функциям Spark и DataFrame в любом месте вашей программы.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Подготовка данных

1. Считайте входной файл в `DataFrame`, который представляет собой распределенную коллекцию данных в виде именованных столбцов. Столбцы для данных можно задать с помощью <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>. Для отображения данных в DataFrame можно применять метод <xref:Microsoft.Spark.Sql.DataFrame.Show%2A>. Не забудьте изменить путь к CSV-файлу на расположение скачанных данных GitHub.

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. Используйте метод <xref:Microsoft.Spark.Sql.DataFrame.Na%2A>, чтобы удалить строки со значениями NA (NULL), и метод <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A>, чтобы удалить определенные столбцы из данных. Это позволяет избежать ошибок при попытке анализа данных со значением NULL или столбцов, не относящихся к конечному анализу.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Анализ данных

Spark SQL позволяет выполнять SQL-вызовы данных. Общепринятой практикой является объединение пользовательских функций и Spark SQL для применения пользовательской функции ко всем строкам в DataFrame.

Вы можете специально вызвать `spark.Sql`, чтобы сымитировать стандартные вызовы SQL, которые встречаются в приложениях других типов. Кроме того, можно вызвать метод <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> и <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A>, чтобы объединить и фильтровать данные, а также выполнить вычисления с ними.

Цель этого приложения — получить определенные сведения о данных проектов GitHub. Добавьте следующие фрагменты кода в программу, чтобы проанализировать данные.

1. Добавьте следующий блок кода, чтобы определить количество вилок для каждого языка. Сначала данные группируются по языку. Затем из каждого языка берется среднее число вилок.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Добавьте следующий блок кода, чтобы упорядочить среднее число вилок по убыванию. Так вы узнаете, какие языки наиболее разветвленные. То есть сначала будет отображаться наибольшее число вилок.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. В указанном ниже блоке кода показано, как давно были обновлены проекты. Вы регистрируете новую пользовательскую функцию *MyUDF* и сравниваете ее с датой (*s_referenceDate*), которая была объявлена в начале этого учебника. Дата каждого проекта сравнивается с датой ссылки. Затем с помощью Spark SQL выполняется вызов определяемой пользователем функции в каждой строке данных, чтобы проанализировать каждый проект в наборе данных.

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);
   cleanedProjects.CreateOrReplaceTempView("dateView");

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. Вызовите `spark.Stop()`, чтобы завершить SparkSession.

## <a name="use-spark-submit-to-run-your-app"></a>Использование команды spark-submit для выполнения приложения

1. Выполните следующую команду, чтобы создать приложение .NET:

   ```dotnetcli
   dotnet build
   ```

1. Запустите приложение с помощью команды `spark-submit`. Не забудьте указать в приведенной ниже команде фактический путь к JAR-файлу Microsoft Spark.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar dotnet /<path>/to/netcoreapp<version>/mySparkBatchApp.dll
   ```

## <a name="get-the-code"></a>Получение кода

[Полное решение](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) можно просмотреть на сайте GitHub.

## <a name="next-steps"></a>Дальнейшие действия

В следующем учебнике описано, как обрабатывать потоковую передачу данных с помощью .NET для Apache Spark.
> [!div class="nextstepaction"]
> [Учебник. Структурированная потоковая передача с помощью .NET для Apache Spark](streaming.md)
