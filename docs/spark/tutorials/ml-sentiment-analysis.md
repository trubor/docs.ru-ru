---
title: Учебник по анализу тональности с помощью .NET для Apache Spark и ML.NET
description: Из этого учебника вы узнаете, как выполнить анализ тональности с помощью ML.NET с .NET для Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: a21b92f910d82cbddd2976adeb292cea5f7bc78b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876868"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="21c0d-103">Учебник. Анализ тональности с помощью .NET для Apache Spark и ML.NET</span><span class="sxs-lookup"><span data-stu-id="21c0d-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="21c0d-104">Из этого учебника вы узнаете, как выполнить анализ тональности онлайн-отзывов с помощью .NET для Apache Spark и ML.NET.</span><span class="sxs-lookup"><span data-stu-id="21c0d-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="21c0d-105">[ML.NET](http://dot.net/ml) — это бесплатная кроссплатформенная среда машинного обучения с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="21c0d-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="21c0d-106">Вы можете использовать .NET для Apache Spark и ML.NET для масштабирования обучения и прогнозирования алгоритмов машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="21c0d-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="21c0d-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="21c0d-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="21c0d-108">Создать модель анализа тональности с помощью построителя моделей ML.NET в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="21c0d-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="21c0d-109">Создать консольное приложение .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="21c0d-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="21c0d-110">Написать и реализовать определяемую пользователем функцию.</span><span class="sxs-lookup"><span data-stu-id="21c0d-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="21c0d-111">Запустить консольное приложение .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="21c0d-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21c0d-112">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="21c0d-112">Prerequisites</span></span>

* <span data-ttu-id="21c0d-113">Если вы никогда не разрабатывали приложение .NET для Apache Spark, начните с [учебника по началу работы](get-started.md), чтобы ознакомиться с основами.</span><span class="sxs-lookup"><span data-stu-id="21c0d-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="21c0d-114">Прежде чем продолжить работу с этим учебником, выполните все предварительные требования.</span><span class="sxs-lookup"><span data-stu-id="21c0d-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="21c0d-115">В этом учебнике используется построитель моделей ML.NET (предварительная версия) и визуальный интерфейс в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="21c0d-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="21c0d-116">Если у вас еще нет Visual Studio, вы можете бесплатно [скачать версию Visual Studio](https://visualstudio.microsoft.com/downloads/) для сообщества.</span><span class="sxs-lookup"><span data-stu-id="21c0d-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="21c0d-117">[Скачайте и установите](https://marketplace.visualstudio.com/items?itemName=MLNET.07) построитель моделей ML.NET (предварительная версия).</span><span class="sxs-lookup"><span data-stu-id="21c0d-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="21c0d-118">Скачайте файлы [yelptest.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) и [yelptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) наборов данных отзывов Yelp.</span><span class="sxs-lookup"><span data-stu-id="21c0d-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="21c0d-119">Изучение данных</span><span class="sxs-lookup"><span data-stu-id="21c0d-119">Review the data</span></span>

<span data-ttu-id="21c0d-120">Набор данных отзывов Yelp содержит онлайн-отзывы о различных службах.</span><span class="sxs-lookup"><span data-stu-id="21c0d-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="21c0d-121">Откройте файл [elptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) и обратите внимание на структуру данных.</span><span class="sxs-lookup"><span data-stu-id="21c0d-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="21c0d-122">Первый столбец содержит текст отзывов, а второй столбец — оценки тональности.</span><span class="sxs-lookup"><span data-stu-id="21c0d-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="21c0d-123">Если оценка тональности равна 1, то отзыв положительный, а если показатель тональности равен 0, то отзыв отрицательный.</span><span class="sxs-lookup"><span data-stu-id="21c0d-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="21c0d-124">В следующей таблице содержатся образцы данных.</span><span class="sxs-lookup"><span data-stu-id="21c0d-124">The following table contains sample data:</span></span>

|<span data-ttu-id="21c0d-125">ReviewText</span><span class="sxs-lookup"><span data-stu-id="21c0d-125">ReviewText</span></span>|<span data-ttu-id="21c0d-126">Тональность</span><span class="sxs-lookup"><span data-stu-id="21c0d-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="21c0d-127">Ого... Отличное место.</span><span class="sxs-lookup"><span data-stu-id="21c0d-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="21c0d-128">1</span><span class="sxs-lookup"><span data-stu-id="21c0d-128">1</span></span>|
|<span data-ttu-id="21c0d-129">Корочка так себе.</span><span class="sxs-lookup"><span data-stu-id="21c0d-129">Crust is not good.</span></span>|    <span data-ttu-id="21c0d-130">0</span><span class="sxs-lookup"><span data-stu-id="21c0d-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="21c0d-131">Создание моделей машинного обучения</span><span class="sxs-lookup"><span data-stu-id="21c0d-131">Build your machine learning model</span></span>

1. <span data-ttu-id="21c0d-132">Откройте Visual Studio и создайте консольное приложение на языке C# (.NET Core).</span><span class="sxs-lookup"><span data-stu-id="21c0d-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="21c0d-133">Назовите проект *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="21c0d-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="21c0d-134">В **обозревателе решений** щелкните правой кнопкой мыши проект *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="21c0d-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="21c0d-135">Затем выберите **Добавить > Машинное обучение**.</span><span class="sxs-lookup"><span data-stu-id="21c0d-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="21c0d-136">В построителе моделей ML.NET щелкните плитку сценария **Анализ тональности**.</span><span class="sxs-lookup"><span data-stu-id="21c0d-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="21c0d-137">На странице **Добавление данных** загрузите файл набора данных *yelptrain.csv*.</span><span class="sxs-lookup"><span data-stu-id="21c0d-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="21c0d-138">Щелкните *Тональность* в раскрывающемся меню **Columns to Predict** (Прогнозируемые столбцы).</span><span class="sxs-lookup"><span data-stu-id="21c0d-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="21c0d-139">На странице **Обучение** задайте для времени обучения значение *60 секунд* и выберите **Начать обучение**.</span><span class="sxs-lookup"><span data-stu-id="21c0d-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="21c0d-140">Обратите внимание на состояние обучения в разделе **Ход выполнения**.</span><span class="sxs-lookup"><span data-stu-id="21c0d-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="21c0d-141">Когда построитель моделей завершит обучение, **оцените** результаты обучения.</span><span class="sxs-lookup"><span data-stu-id="21c0d-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="21c0d-142">Можно ввести фразы в текстовое поле ниже **Try your model** (Испытайте модель) и щелкнуть **Прогноз**, чтобы увидеть выходные данные.</span><span class="sxs-lookup"><span data-stu-id="21c0d-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="21c0d-143">Щелкните **Код**, а затем выберите **Добавить проекты**, чтобы добавить модель машинного обучения в решение.</span><span class="sxs-lookup"><span data-stu-id="21c0d-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="21c0d-144">Обратите внимание, что в решения добавляются два проекта: **MLSparkModelML.ConsoleApp** и **MLSparkModelML.Model**.</span><span class="sxs-lookup"><span data-stu-id="21c0d-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="21c0d-145">Дважды щелкните проект C# *MLSpark* и обратите внимание, что добавлена следующая ссылка на проект.</span><span class="sxs-lookup"><span data-stu-id="21c0d-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="21c0d-146">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="21c0d-146">Create a console app</span></span>

<span data-ttu-id="21c0d-147">Построитель моделей создает консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="21c0d-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="21c0d-148">Щелкните правой кнопкой мыши проект **MLSparkModelML.Console** в обозревателе решений и выберите **Управление пакетами NuGet...**</span><span class="sxs-lookup"><span data-stu-id="21c0d-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="21c0d-149">Найдите **Microsoft.Spark** и установите пакет.</span><span class="sxs-lookup"><span data-stu-id="21c0d-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="21c0d-150">Построитель моделей автоматически устанавливает **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="21c0d-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="21c0d-151">Создание SparkSession</span><span class="sxs-lookup"><span data-stu-id="21c0d-151">Create a SparkSession</span></span>

1. <span data-ttu-id="21c0d-152">Откройте файл *Program.cs* для **MLSparkModelML.ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="21c0d-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="21c0d-153">Этот файл автоматически создается построителем моделей.</span><span class="sxs-lookup"><span data-stu-id="21c0d-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="21c0d-154">Удалите операторы `using`, содержимое метода Main() и область `CreateSingleDataSample`.</span><span class="sxs-lookup"><span data-stu-id="21c0d-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="21c0d-155">Добавьте следующие новые операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="21c0d-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="21c0d-156">Измените `DATA_FILEPATH` на путь к файлу *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="21c0d-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="21c0d-157">Добавьте приведенный ниже код в метод `Main`, чтобы создать новый экземпляр `SparkSession`.</span><span class="sxs-lookup"><span data-stu-id="21c0d-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="21c0d-158">Сеанс Spark является точкой входа для программирования Spark через API DataSet и DataFrame.</span><span class="sxs-lookup"><span data-stu-id="21c0d-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="21c0d-159">Вызов созданного выше объекта *spark* позволяет получить доступ к функциям Spark и DataFrame в любом месте вашей программы.</span><span class="sxs-lookup"><span data-stu-id="21c0d-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="21c0d-160">Создание кадра данных и вывод в консоли</span><span class="sxs-lookup"><span data-stu-id="21c0d-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="21c0d-161">Прочтите данные отзывов Yelp из файла *yelptest.csv* в качестве `DataFrame`.</span><span class="sxs-lookup"><span data-stu-id="21c0d-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="21c0d-162">Включите параметры `header` и `inferSchema`.</span><span class="sxs-lookup"><span data-stu-id="21c0d-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="21c0d-163">Параметр `header` считывает первую строку *yelptest.csv* в качестве имен столбцов вместо данных.</span><span class="sxs-lookup"><span data-stu-id="21c0d-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="21c0d-164">Параметр `inferSchema` выводит типы столбцов на основе данных.</span><span class="sxs-lookup"><span data-stu-id="21c0d-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="21c0d-165">Регистрация определяемой пользователем функции</span><span class="sxs-lookup"><span data-stu-id="21c0d-165">Register a user-defined function</span></span>

<span data-ttu-id="21c0d-166">Для выполнения вычислений и анализа данных в приложениях Spark можно использовать *определяемые пользователем функции*.</span><span class="sxs-lookup"><span data-stu-id="21c0d-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="21c0d-167">В этом учебнике для оценки каждого отзыва Yelp используйте ML.NET с определяемой пользователем функцией.</span><span class="sxs-lookup"><span data-stu-id="21c0d-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="21c0d-168">Добавьте следующий код в метод `Main`, чтобы зарегистрировать определяемую пользователем функцию с именем `MLudf`.</span><span class="sxs-lookup"><span data-stu-id="21c0d-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="21c0d-169">Эта определяемая пользователем функция принимает в качестве входных данных строку отзыва Yelp и выводит значение true или false для положительной или отрицательной тональности соответственно.</span><span class="sxs-lookup"><span data-stu-id="21c0d-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="21c0d-170">В ней используется метод *Predict()* , который вы определите позже.</span><span class="sxs-lookup"><span data-stu-id="21c0d-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="21c0d-171">Использование Spark SQL для вызова определяемой пользователем функции</span><span class="sxs-lookup"><span data-stu-id="21c0d-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="21c0d-172">Теперь, когда вы считали данные и включили машинное обучение, используйте Spark SQL для вызова определяемой пользователем функции, которая будет выполнять анализ тональности для каждой строки в кадре данных.</span><span class="sxs-lookup"><span data-stu-id="21c0d-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="21c0d-173">Добавьте приведенный ниже код в метод `Main`:</span><span class="sxs-lookup"><span data-stu-id="21c0d-173">Add the following code to your `Main` method:</span></span>

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a><span data-ttu-id="21c0d-174">Создание метода Predict()</span><span class="sxs-lookup"><span data-stu-id="21c0d-174">Create predict() method</span></span>

<span data-ttu-id="21c0d-175">Добавьте приведенный ниже код перед методом `Main()`.</span><span class="sxs-lookup"><span data-stu-id="21c0d-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="21c0d-176">Этот код аналогичен тому, что создается построителем моделей в файле *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="21c0d-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="21c0d-177">Перемещение этого метода на консоль приводит к загрузке модели при каждом запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="21c0d-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="21c0d-178">Добавление модели в консольное приложение</span><span class="sxs-lookup"><span data-stu-id="21c0d-178">Add the model to your console app</span></span>

<span data-ttu-id="21c0d-179">В обозревателе решений скопируйте файл *MLModel.zip* из проекта **MLSparkModelML.Model** и вставьте его в проект **MLSparkModelML.ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="21c0d-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="21c0d-180">Ссылка автоматически добавляется в файл *MLSparkModelML.ConsoleApp.csproj*.</span><span class="sxs-lookup"><span data-stu-id="21c0d-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="21c0d-181">Выполнение кода</span><span class="sxs-lookup"><span data-stu-id="21c0d-181">Run your code</span></span>

<span data-ttu-id="21c0d-182">Чтобы выполнить код, используйте `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="21c0d-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="21c0d-183">Перейдите к корневой папке консольного приложения с помощью командной строки и выполните указанные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="21c0d-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="21c0d-184">Сначала очистите и опубликуйте приложение.</span><span class="sxs-lookup"><span data-stu-id="21c0d-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="21c0d-185">Затем перейдите в папку публикации консольного приложения и выполните указанную ниже команду `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="21c0d-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="21c0d-186">Не забудьте указать в команде фактический путь к JAR-файлу Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="21c0d-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2-4_2.11-1.0.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="21c0d-187">Получите код</span><span class="sxs-lookup"><span data-stu-id="21c0d-187">Get the code</span></span>

<span data-ttu-id="21c0d-188">Код в этом учебнике похож на код, используемый в примере [анализа тональности с большими данными](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment).</span><span class="sxs-lookup"><span data-stu-id="21c0d-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="21c0d-189">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="21c0d-189">Next steps</span></span>

<span data-ttu-id="21c0d-190">В следующем статье описано, как создать структурированный поток с помощью .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="21c0d-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="21c0d-191">Учебник. Структурированная потоковая передача с помощью .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="21c0d-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
