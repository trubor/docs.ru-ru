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
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="4de1c-103">Учебник. Выполнение пакетной обработки с помощью .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4de1c-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="4de1c-104">В этом учебнике вы узнаете, как выполнять пакетную обработку с помощью .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="4de1c-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="4de1c-105">Пакетная обработка — это преобразование неактивных данных. Это означает, что исходные данные уже загружены в хранилище данных.</span><span class="sxs-lookup"><span data-stu-id="4de1c-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="4de1c-106">Обычно выполняется пакетная обработка больших неструктурированных наборов данных, которые необходимо подготовить для дальнейшего анализа.</span><span class="sxs-lookup"><span data-stu-id="4de1c-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="4de1c-107">Обработка журналов и хранение данных — это типичные сценарии пакетной обработки.</span><span class="sxs-lookup"><span data-stu-id="4de1c-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="4de1c-108">В таких сценариях вы анализируете сведения о проектах GitHub, например количество вилок различных проектов или сведения об обновлении проектов.</span><span class="sxs-lookup"><span data-stu-id="4de1c-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="4de1c-109">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="4de1c-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4de1c-110">создать и выполнить приложение .NET для Apache Spark;</span><span class="sxs-lookup"><span data-stu-id="4de1c-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="4de1c-111">считывать данные в DataFrame и подготовить их для анализа;</span><span class="sxs-lookup"><span data-stu-id="4de1c-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="4de1c-112">обрабатывать данные с помощью Spark SQL.</span><span class="sxs-lookup"><span data-stu-id="4de1c-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4de1c-113">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="4de1c-113">Prerequisites</span></span>

<span data-ttu-id="4de1c-114">Если вы впервые используете .NET для Apache Spark, ознакомьтесь с учебником [Учебник. Начало работы с .NET для Apache Spark](get-started.md), чтобы узнать, как подготовить среду и запустить первое приложение .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="4de1c-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="4de1c-115">Скачивание примера данных</span><span class="sxs-lookup"><span data-stu-id="4de1c-115">Download the sample data</span></span>

<span data-ttu-id="4de1c-116">[GHTorrent](http://ghtorrent.org/) отслеживает все открытые события GitHub, например информацию о проектах, фиксации и наблюдателях, а также сохраняет события и их структуру в базах данных.</span><span class="sxs-lookup"><span data-stu-id="4de1c-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="4de1c-117">Данные, собранные за разные временные периоды, доступны в виде загружаемых архивов.</span><span class="sxs-lookup"><span data-stu-id="4de1c-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="4de1c-118">Так как файлы дампа очень большие, в этом учебнике используется [их сокращенная версия](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv), которую можно скачать на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="4de1c-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="4de1c-119">Набор данных GHTorrent распространяется по схеме двойного лицензирования ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span><span class="sxs-lookup"><span data-stu-id="4de1c-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="4de1c-120">Для некоммерческих целей (в том числе для образовательных, исследовательских и личных) набор данных распространяется по [лицензии CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="4de1c-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="4de1c-121">Создание консольного приложение</span><span class="sxs-lookup"><span data-stu-id="4de1c-121">Create a console application</span></span>

1. <span data-ttu-id="4de1c-122">В командной строке выполните следующие команды, чтобы создать новое консольное приложение:</span><span class="sxs-lookup"><span data-stu-id="4de1c-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="4de1c-123">Команда `dotnet` создаст для вас приложение `new` типа `console`.</span><span class="sxs-lookup"><span data-stu-id="4de1c-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="4de1c-124">Параметр `-o` создаст каталог с именем *mySparkBatchApp*, в котором хранится приложение и используемые им файлы.</span><span class="sxs-lookup"><span data-stu-id="4de1c-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="4de1c-125">Команда `cd mySparkBatchApp` изменит каталог на только что созданный каталог приложения.</span><span class="sxs-lookup"><span data-stu-id="4de1c-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="4de1c-126">Чтобы использовать .NET для Apache Spark в приложении, установите пакет Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="4de1c-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="4de1c-127">В консоли выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="4de1c-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="4de1c-128">Создание SparkSession</span><span class="sxs-lookup"><span data-stu-id="4de1c-128">Create a SparkSession</span></span>

1. <span data-ttu-id="4de1c-129">Добавьте следующие дополнительные инструкции `using` в начало файла *Program.cs* приложения *mySparkBatchApp*.</span><span class="sxs-lookup"><span data-stu-id="4de1c-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="4de1c-130">Добавьте приведенный ниже код к пространству имен проекта.</span><span class="sxs-lookup"><span data-stu-id="4de1c-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="4de1c-131">*s_referenceData* будет использоваться позже в программе для фильтрации на основе даты.</span><span class="sxs-lookup"><span data-stu-id="4de1c-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="4de1c-132">Добавьте следующий код в метод Main, чтобы установить новый сеанс SparkSession.</span><span class="sxs-lookup"><span data-stu-id="4de1c-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="4de1c-133">SparkSession является точкой входа для программирования Spark через API DataSet и DataFrame.</span><span class="sxs-lookup"><span data-stu-id="4de1c-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="4de1c-134">Вызов объекта `spark` позволяет получить доступ к функциям Spark и DataFrame в любом месте вашей программы.</span><span class="sxs-lookup"><span data-stu-id="4de1c-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="4de1c-135">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="4de1c-135">Prepare the data</span></span>

1. <span data-ttu-id="4de1c-136">Считайте входной файл в `DataFrame`, который представляет собой распределенную коллекцию данных в виде именованных столбцов.</span><span class="sxs-lookup"><span data-stu-id="4de1c-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="4de1c-137">Столбцы для данных можно задать с помощью <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span><span class="sxs-lookup"><span data-stu-id="4de1c-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="4de1c-138">Для отображения данных в DataFrame можно применять метод <xref:Microsoft.Spark.Sql.DataFrame.Show%2A>.</span><span class="sxs-lookup"><span data-stu-id="4de1c-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="4de1c-139">Не забудьте изменить путь к CSV-файлу на расположение скачанных данных GitHub.</span><span class="sxs-lookup"><span data-stu-id="4de1c-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

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

1. <span data-ttu-id="4de1c-140">Используйте метод <xref:Microsoft.Spark.Sql.DataFrame.Na%2A>, чтобы удалить строки со значениями NA (NULL), и метод <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A>, чтобы удалить определенные столбцы из данных.</span><span class="sxs-lookup"><span data-stu-id="4de1c-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="4de1c-141">Это позволяет избежать ошибок при попытке анализа данных со значением NULL или столбцов, не относящихся к конечному анализу.</span><span class="sxs-lookup"><span data-stu-id="4de1c-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="4de1c-142">Анализ данных</span><span class="sxs-lookup"><span data-stu-id="4de1c-142">Analyze the data</span></span>

<span data-ttu-id="4de1c-143">Spark SQL позволяет выполнять SQL-вызовы данных.</span><span class="sxs-lookup"><span data-stu-id="4de1c-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="4de1c-144">Общепринятой практикой является объединение пользовательских функций и Spark SQL для применения пользовательской функции ко всем строкам в DataFrame.</span><span class="sxs-lookup"><span data-stu-id="4de1c-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="4de1c-145">Вы можете специально вызвать `spark.Sql`, чтобы сымитировать стандартные вызовы SQL, которые встречаются в приложениях других типов.</span><span class="sxs-lookup"><span data-stu-id="4de1c-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="4de1c-146">Кроме того, можно вызвать метод <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> и <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A>, чтобы объединить и фильтровать данные, а также выполнить вычисления с ними.</span><span class="sxs-lookup"><span data-stu-id="4de1c-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="4de1c-147">Цель этого приложения — получить определенные сведения о данных проектов GitHub.</span><span class="sxs-lookup"><span data-stu-id="4de1c-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="4de1c-148">Добавьте следующие фрагменты кода в программу, чтобы проанализировать данные.</span><span class="sxs-lookup"><span data-stu-id="4de1c-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="4de1c-149">Добавьте следующий блок кода, чтобы определить количество вилок для каждого языка.</span><span class="sxs-lookup"><span data-stu-id="4de1c-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="4de1c-150">Сначала данные группируются по языку.</span><span class="sxs-lookup"><span data-stu-id="4de1c-150">First, the data is grouped by language.</span></span> <span data-ttu-id="4de1c-151">Затем из каждого языка берется среднее число вилок.</span><span class="sxs-lookup"><span data-stu-id="4de1c-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="4de1c-152">Добавьте следующий блок кода, чтобы упорядочить среднее число вилок по убыванию. Так вы узнаете, какие языки наиболее разветвленные.</span><span class="sxs-lookup"><span data-stu-id="4de1c-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="4de1c-153">То есть сначала будет отображаться наибольшее число вилок.</span><span class="sxs-lookup"><span data-stu-id="4de1c-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="4de1c-154">В указанном ниже блоке кода показано, как давно были обновлены проекты.</span><span class="sxs-lookup"><span data-stu-id="4de1c-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="4de1c-155">Вы регистрируете новую пользовательскую функцию *MyUDF* и сравниваете ее с датой (*s_referenceDate*), которая была объявлена в начале этого учебника.</span><span class="sxs-lookup"><span data-stu-id="4de1c-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="4de1c-156">Дата каждого проекта сравнивается с датой ссылки.</span><span class="sxs-lookup"><span data-stu-id="4de1c-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="4de1c-157">Затем с помощью Spark SQL выполняется вызов определяемой пользователем функции в каждой строке данных, чтобы проанализировать каждый проект в наборе данных.</span><span class="sxs-lookup"><span data-stu-id="4de1c-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

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

1. <span data-ttu-id="4de1c-158">Вызовите `spark.Stop()`, чтобы завершить SparkSession.</span><span class="sxs-lookup"><span data-stu-id="4de1c-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="4de1c-159">Использование команды spark-submit для выполнения приложения</span><span class="sxs-lookup"><span data-stu-id="4de1c-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="4de1c-160">Выполните следующую команду, чтобы создать приложение .NET:</span><span class="sxs-lookup"><span data-stu-id="4de1c-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="4de1c-161">Запустите приложение с помощью команды `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="4de1c-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="4de1c-162">Не забудьте указать в приведенной ниже команде фактический путь к JAR-файлу Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="4de1c-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar dotnet /<path>/to/netcoreapp<version>/mySparkBatchApp.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="4de1c-163">Получение кода</span><span class="sxs-lookup"><span data-stu-id="4de1c-163">Get the code</span></span>

<span data-ttu-id="4de1c-164">[Полное решение](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) можно просмотреть на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="4de1c-164">You can see the [full solution](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4de1c-165">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="4de1c-165">Next steps</span></span>

<span data-ttu-id="4de1c-166">В следующем учебнике описано, как обрабатывать потоковую передачу данных с помощью .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="4de1c-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4de1c-167">Учебник. Структурированная потоковая передача с помощью .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4de1c-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
