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
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Учебник. Анализ тональности с помощью .NET для Apache Spark и ML.NET

Из этого учебника вы узнаете, как выполнить анализ тональности онлайн-отзывов с помощью .NET для Apache Spark и ML.NET. [ML.NET](http://dot.net/ml) — это бесплатная кроссплатформенная среда машинного обучения с открытым исходным кодом. Вы можете использовать .NET для Apache Spark и ML.NET для масштабирования обучения и прогнозирования алгоритмов машинного обучения.

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
>
> * Создать модель анализа тональности с помощью построителя моделей ML.NET в Visual Studio.
> * Создать консольное приложение .NET для Apache Spark.
> * Написать и реализовать определяемую пользователем функцию.
> * Запустить консольное приложение .NET для Apache Spark.

## <a name="prerequisites"></a>Предварительные требования

* Если вы никогда не разрабатывали приложение .NET для Apache Spark, начните с [учебника по началу работы](get-started.md), чтобы ознакомиться с основами. Прежде чем продолжить работу с этим учебником, выполните все предварительные требования.

* В этом учебнике используется построитель моделей ML.NET (предварительная версия) и визуальный интерфейс в Visual Studio. Если у вас еще нет Visual Studio, вы можете бесплатно [скачать версию Visual Studio](https://visualstudio.microsoft.com/downloads/) для сообщества.

* [Скачайте и установите](https://marketplace.visualstudio.com/items?itemName=MLNET.07) построитель моделей ML.NET (предварительная версия).

* Скачайте файлы [yelptest.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) и [yelptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) наборов данных отзывов Yelp.

## <a name="review-the-data"></a>Изучение данных

Набор данных отзывов Yelp содержит онлайн-отзывы о различных службах. Откройте файл [elptrain.csv](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) и обратите внимание на структуру данных. Первый столбец содержит текст отзывов, а второй столбец — оценки тональности. Если оценка тональности равна 1, то отзыв положительный, а если показатель тональности равен 0, то отзыв отрицательный.

В следующей таблице содержатся образцы данных.

|ReviewText|Тональность|
|-|-|
|Ого... Отличное место.|    1|
|Корочка так себе.|    0|

## <a name="build-your-machine-learning-model"></a>Создание моделей машинного обучения

1. Откройте Visual Studio и создайте консольное приложение на языке C# (.NET Core). Назовите проект *MLSparkModel*.

1. В **обозревателе решений** щелкните правой кнопкой мыши проект *MLSparkModel*. Затем выберите **Добавить > Машинное обучение**.

1. В построителе моделей ML.NET щелкните плитку сценария **Анализ тональности**.

1. На странице **Добавление данных** загрузите файл набора данных *yelptrain.csv*.

1. Щелкните *Тональность* в раскрывающемся меню **Columns to Predict** (Прогнозируемые столбцы).

1. На странице **Обучение** задайте для времени обучения значение *60 секунд* и выберите **Начать обучение**. Обратите внимание на состояние обучения в разделе **Ход выполнения**.

1. Когда построитель моделей завершит обучение, **оцените** результаты обучения. Можно ввести фразы в текстовое поле ниже **Try your model** (Испытайте модель) и щелкнуть **Прогноз**, чтобы увидеть выходные данные.

1. Щелкните **Код**, а затем выберите **Добавить проекты**, чтобы добавить модель машинного обучения в решение.

1. Обратите внимание, что в решения добавляются два проекта: **MLSparkModelML.ConsoleApp** и **MLSparkModelML.Model**.

1. Дважды щелкните проект C# *MLSpark* и обратите внимание, что добавлена следующая ссылка на проект.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Создание консольного приложения

Построитель моделей создает консольное приложение.

1. Щелкните правой кнопкой мыши проект **MLSparkModelML.Console** в обозревателе решений и выберите **Управление пакетами NuGet...**

1. Найдите **Microsoft.Spark** и установите пакет. Построитель моделей автоматически устанавливает **Microsoft.ML**.

### <a name="create-a-sparksession"></a>Создание SparkSession

1. Откройте файл *Program.cs* для **MLSparkModelML.ConsoleApp**. Этот файл автоматически создается построителем моделей. Удалите операторы `using`, содержимое метода Main() и область `CreateSingleDataSample`.

1. Добавьте следующие новые операторы `using` в начало файла *Program.cs*:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Измените `DATA_FILEPATH` на путь к файлу *yelptest.csv*.

1. Добавьте приведенный ниже код в метод `Main`, чтобы создать новый экземпляр `SparkSession`. Сеанс Spark является точкой входа для программирования Spark через API DataSet и DataFrame.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   Вызов созданного выше объекта *spark* позволяет получить доступ к функциям Spark и DataFrame в любом месте вашей программы.

### <a name="create-a-dataframe-and-print-to-console"></a>Создание кадра данных и вывод в консоли

Прочтите данные отзывов Yelp из файла *yelptest.csv* в качестве `DataFrame`. Включите параметры `header` и `inferSchema`. Параметр `header` считывает первую строку *yelptest.csv* в качестве имен столбцов вместо данных. Параметр `inferSchema` выводит типы столбцов на основе данных.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Регистрация определяемой пользователем функции

Для выполнения вычислений и анализа данных в приложениях Spark можно использовать *определяемые пользователем функции*. В этом учебнике для оценки каждого отзыва Yelp используйте ML.NET с определяемой пользователем функцией.

Добавьте следующий код в метод `Main`, чтобы зарегистрировать определяемую пользователем функцию с именем `MLudf`.

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Эта определяемая пользователем функция принимает в качестве входных данных строку отзыва Yelp и выводит значение true или false для положительной или отрицательной тональности соответственно. В ней используется метод *Predict()* , который вы определите позже.

### <a name="use-spark-sql-to-call-the-udf"></a>Использование Spark SQL для вызова определяемой пользователем функции

Теперь, когда вы считали данные и включили машинное обучение, используйте Spark SQL для вызова определяемой пользователем функции, которая будет выполнять анализ тональности для каждой строки в кадре данных. Добавьте приведенный ниже код в метод `Main`:

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

### <a name="create-predict-method"></a>Создание метода Predict()

Добавьте приведенный ниже код перед методом `Main()`. Этот код аналогичен тому, что создается построителем моделей в файле *ConsumeModel.cs*. Перемещение этого метода на консоль приводит к загрузке модели при каждом запуске приложения.

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

## <a name="add-the-model-to-your-console-app"></a>Добавление модели в консольное приложение

В обозревателе решений скопируйте файл *MLModel.zip* из проекта **MLSparkModelML.Model** и вставьте его в проект **MLSparkModelML.ConsoleApp**. Ссылка автоматически добавляется в файл *MLSparkModelML.ConsoleApp.csproj*.

## <a name="run-your-code"></a>Выполнение кода

Чтобы выполнить код, используйте `spark-submit`. Перейдите к корневой папке консольного приложения с помощью командной строки и выполните указанные ниже команды.

Сначала очистите и опубликуйте приложение.

```dotnetcli
dotnet clean
dotnet publish
```

Затем перейдите в папку публикации консольного приложения и выполните указанную ниже команду `spark-submit`. Не забудьте указать в команде фактический путь к JAR-файлу Microsoft Spark.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2-4_2.11-1.0.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Получите код

Код в этом учебнике похож на код, используемый в примере [анализа тональности с большими данными](https://github.com/dotnet/spark/tree/main/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment).

## <a name="next-steps"></a>Следующие шаги

В следующем статье описано, как создать структурированный поток с помощью .NET для Apache Spark.
> [!div class="nextstepaction"]
> [Учебник. Структурированная потоковая передача с помощью .NET для Apache Spark](streaming.md)
