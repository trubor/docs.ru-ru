---
title: Учебник. Прогнозирование цен с помощью регрессии
description: В этом учебнике описано, как с помощью ML.NET создать модель регрессии для прогнозирования цен, в частности платы за проезд в такси по Нью-Йорку.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: f8f7146241368edaca31afd970af54a098d1aafa
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874645"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Учебник. Прогнозирование цен с помощью регрессии с ML.NET

В этом учебнике показано, как создать [модель регрессии](../resources/glossary.md#regression) с помощью ML.NET, чтобы прогнозировать цены, в частности плату за проезд в такси по Нью-Йорку.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> * Подготовка и анализ данных
> * Загрузка и преобразование данных
> * Выбор алгоритма обучения
> * Обучение модели
> * Оценка модели
> * Использование модели для прогнозирования

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".

## <a name="create-a-console-application"></a>Создание консольного приложения

1. Создайте **консольное приложение .NET Core** с именем TaxiFarePrediction.

1. Создайте каталог с именем *Data* в проекте для хранения набора данных и файлов модели.

1. Установите пакеты NuGet **Microsoft.ML** и **Microsoft.ML.FastTree**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите в качестве источника пакета "nuget.org", откройте вкладку **Обзор**, найдите **Microsoft.ML**, выберите пакет в списке и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов. Сделайте то же самое для пакета **Microsoft.ML.FastTree** в NuGet.

## <a name="prepare-and-understand-the-data"></a>Подготовка и анализ данных

1. Скачайте наборы данных [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/main/test/data/taxi-fare-train.csv) и [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/main/test/data/taxi-fare-test.csv), сохранив их в созданной на предыдущем шаге папке *Data*. Эти наборы данных используются для обучения модели машинного обучения и последующей оценки точности этой модели. Эти наборы данных взяты из [наборов данных NYC TLC Taxi Trip](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

1. В **обозревателе решений** щелкните правой кнопкой мыши каждый из файлов \*.csv и выберите **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

1. Откройте набор данных **taxi-fare-train.csv** и просмотрите заголовки столбцов в первой строке. Теперь изучите каждый из столбцов. Разберитесь, какие данные в них хранятся, и определите, какие столбцы являются **признаками**, а в каком содержится **метка**.

`label` — это столбец, который необходимо спрогнозировать. Определены `Features`входные данные, которые вы предоставляете модели для прогнозирования `Label`.

Предоставленный набор данных содержит следующие столбцы:

* **vendor_id:** идентификатор поставщика услуг такси — это признак.
* **rate_code:** тип тарифа для поездки на такси — это признак.
* **passenger_count:** число пассажиров в поездке — это признак.
* **trip_time_in_secs:** время, затраченное на поездку. Вам требуется спрогнозировать плату за одну поездку до того, как поездка будет завершена. На этот момент вам неизвестна продолжительность поездки. Таким образом, продолжительность поездки не является признаком и соответствующий столбец следует исключить из модели.
* **trip_distance:** расстояние поездки — это признак.
* **payment_type:** метод оплаты (наличные или кредитная карта) — это признак.
* **fare_amount:** общая сумма, уплаченная за поездку на такси, — это метка.

## <a name="create-data-classes"></a>Создание классов данных

Создайте классы для входных данных и прогнозов:

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *TaxiTrip.cs*. Теперь нажмите кнопку **Добавить**.
1. Добавьте следующие директивы `using` в новый файл.

   [!code-csharp[AddUsings](./snippets/predict-prices/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Удалите из файла *TaxiTrip.cs* существующее определение класса и добавьте следующий код с двумя классами `TaxiTrip` и `TaxiTripFarePrediction`:

[!code-csharp[DefineTaxiTrip](./snippets/predict-prices/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

Класс `TaxiTrip` содержит входные данные и определения для каждого из столбцов в этом наборе данных. Используйте атрибут <xref:Microsoft.ML.Data.LoadColumnAttribute>, чтобы указать индексы исходных столбцов в наборе данных.

Класс `TaxiTripFarePrediction` представляет результаты прогнозирования. Он содержит одно поле типа float `FareAmount`, к которому применен атрибут `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute>. Для задачи регрессии столбец **Оценка** содержит прогнозируемые значения метки.

> [!NOTE]
> Используйте тип `float` для представления значений с плавающей запятой в классах данных ввода и прогнозирования.

### <a name="define-data-and-model-paths"></a>Определение путей к данным и модели

Добавьте следующие новые операторы `using` в начало файла *Program.cs*:

[!code-csharp[AddUsings](./snippets/predict-prices/csharp/Program.cs#1 "Add necessary usings")]

Необходимо создать три поля, которые будут содержать пути к файлам с наборами данных и к файлу для сохранения модели:

* `_trainDataPath` содержит путь к файлу с набором данных, используемым для обучения модели.
* `_testDataPath` содержит путь к файлу с набором данных, используемым для оценки модели.
* `_modelPath` содержит путь к файлу для сохранения обучаемой модели.

Добавьте следующий код прямо перед методом `Main`, чтобы указать эти пути и переменную `_textLoader`:

[!code-csharp[InitializePaths](./snippets/predict-prices/csharp/Program.cs#2 "Define variables to store the data file paths")]

Все операции ML.NET запускаются в [классе MLContext](xref:Microsoft.ML.MLContext). Инициализация `mlContext` создает новую среду ML.NET, которую могут совместно использовать объекты рабочего процесса создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

### <a name="initialize-variables-in-main"></a>Инициализация переменных в методе Main

Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную `mlContext`:

[!code-csharp[CreateMLContext](./snippets/predict-prices/csharp/Program.cs#3 "Create the ML Context")]

В качестве следующей строки кода в методе `Main` добавьте приведенный ниже код, чтобы вызвать метод `Train`:

[!code-csharp[Train](./snippets/predict-prices/csharp/Program.cs#5 "Train your model")]

Метод `Train()` выполняет следующие задачи:

* загрузка данных;
* извлечение и преобразование данных;
* обучение модели;
* возвращение модели.

Метод `Train` обучает модель. Создайте этот метод сразу под `Main`, используя следующий код:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Загрузка и преобразование данных

ML.NET использует [класс IDataView](xref:Microsoft.ML.IDataView) как гибкий и эффективный способ описания числовых или текстовых табличных данных. `IDataView` может загружать данные из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала). Добавьте следующий код в первую строку метода `Train()`:

[!code-csharp[LoadTrainData](./snippets/predict-prices/csharp/Program.cs#6 "loading training dataset")]

Так как вам нужно спрогнозировать плату за такси, столбец `FareAmount` является меткой `Label`, которую вы будете прогнозировать (выходные данные модели). Используйте класс преобразования `CopyColumnsEstimator`, чтобы скопировать `FareAmount`, и добавьте следующий код:

[!code-csharp[CopyColumnsEstimator](./snippets/predict-prices/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Алгоритм, который обучает модель, принимает **числовые** признаки, поэтому значения категориальных данных (`VendorId`, `RateCode` и `PaymentType`) нужно преобразовать в числа (`VendorIdEncoded`, `RateCodeEncoded` и `PaymentTypeEncoded`). Для этого используйте класс преобразования [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer), который присваивает разные числовые значения ключа разным значениям в каждом из столбцов, и добавьте следующий код:

[!code-csharp[OneHotEncodingEstimator](./snippets/predict-prices/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Последний шаг на этапе подготовки данных заключается в объединении всех столбцов признаков в столбце **Features** с помощью класса преобразования `mlContext.Transforms.Concatenate`. По умолчанию алгоритм обучения обрабатывает только признаки, представленные в столбце **Features**. Добавьте следующий код:

[!code-csharp[ColumnConcatenatingEstimator](./snippets/predict-prices/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Выбор алгоритма обучения

Задача заключается в прогнозировании стоимости поездки в такси в Нью-Йорке. На первый взгляд может показаться, что плата зависит только от расстояния. Но службы такси в Нью-Йорке изменяют плату с учетом еще нескольких факторов, таких как наличие дополнительных пассажиров или оплата кредитной картой вместо наличных. Вы хотите спрогнозировать стоимость, которая является реальным значением, зависящим от других факторов в наборе данных. Для этого нужно выбрать задачу машинного обучения [регрессия](../resources/glossary.md#regression).

Добавьте задачу машинного обучения [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) к определениям преобразований данных, добавив в `Train()` следующую строку кода:

[!code-csharp[FastTreeRegressionTrainer](./snippets/predict-prices/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Обучение модели

Согласуйте модель с учебным `dataview` и получите обученную модель, добавив в метод `Train()` следующую строку кода:

[!code-csharp[TrainModel](./snippets/predict-prices/csharp/Program.cs#11 "Train the model")]

Метод [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) обучает модель путем преобразования набора данных и применения обучения.

Возвратите обученную модель с помощью следующей строки кода в методе `Train()`:

[!code-csharp[ReturnModel](./snippets/predict-prices/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Оценка модели

Затем оцените эффективность модели с помощью тестовых данных для контроля качества и проверки. Создайте метод `Evaluate()` сразу после `Train()`, используя следующий код:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

Метод `Evaluate` выполняет следующие задачи:

* загрузка тестового набора данных;
* создание средства оценки регрессии;
* оценка модели и создание метрик;
* отображение метрик.

Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `Train`, используя следующий код:

[!code-csharp[CallEvaluate](./snippets/predict-prices/csharp/Program.cs#14 "Call the Evaluate method")]

Загрузите тестовый набор данных с помощью метода [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A). Оцените модель с помощью этого набора данных для проверки ее качества, добавив следующий код в метод `Evaluate`:

[!code-csharp[LoadTestDataset](./snippets/predict-prices/csharp/Program.cs#15 "Load the test dataset")]

Затем преобразуйте данные `Test`, добавив следующий код для `Evaluate()`:

[!code-csharp[PredictWithTransformer](./snippets/predict-prices/csharp/Program.cs#16 "Predict using the Transformer")]

Метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) осуществляет прогнозирование для входных строк тестового набора данных.

Метод `RegressionContext.Evaluate` вычисляет метрики качества для `PredictionModel` на основе указанного набора данных. Возвращает объект <xref:Microsoft.ML.Data.RegressionMetrics>, который содержит общие метрики, вычисляемые с помощью средств оценки регрессии.

Чтобы отобразить их для оценки качества модели, сначала метрики необходимо получить. Добавьте в следующую строку метода `Evaluate` приведенный ниже код:

[!code-csharp[ComputeMetrics](./snippets/predict-prices/csharp/Program.cs#17 "Compute Metrics")]

После получения прогноза метод [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) оценивает модель, сравнивая спрогнозированные значения с фактическими метками (`Labels`) в тестовом наборе данных, а затем возвращает метрики эффективности модели.

Добавьте следующий код, чтобы оценить модель и создать для нее метрики оценки:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

Также в качестве метрики для оценки регрессионных моделей используется [коэффициент детерминации](../resources/glossary.md#coefficient-of-determination). Коэффициент детерминации может иметь значения в диапазоне от 0 до 1. Чем ближе его значение к 1, тем лучше модель. Чтобы отображать значение коэффициента детерминации, добавьте следующий код в метод `Evaluate`:

[!code-csharp[DisplayRSquared](./snippets/predict-prices/csharp/Program.cs#18 "Display the RSquared metric.")]

[Среднеквадратичное отклонение](../resources/glossary.md#root-of-mean-squared-error-rmse) является одной из метрик, используемых для оценки регрессионной модели. Чем ниже это отклонение, тем лучше модель. Чтобы отображать значение среднеквадратичного отклонения, добавьте следующий код в метод `Evaluate`:

[!code-csharp[DisplayRMS](./snippets/predict-prices/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Использование модели для прогнозирования

Создайте метод `TestSinglePrediction` сразу после метода `Evaluate`, вставив в него следующий код:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Метод `TestSinglePrediction` выполняет следующие задачи:

* создание отдельного комментария тестовых данных;
* прогнозирование суммы оплаты на основе тестовых данных;
* объединение тестовых данных и прогнозов для создания отчетов;
* отображение результатов прогнозирования.

Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `Evaluate`, используя следующий код:

[!code-csharp[CallTestSinglePrediction](./snippets/predict-prices/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

Для прогнозирования цены используйте `PredictionEngine`, добавив в `TestSinglePrediction()` следующий код:

[!code-csharp[MakePredictionEngine](./snippets/predict-prices/csharp/Program.cs#22 "Create the PredictionFunction")]

Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным. Допустимо использовать в средах прототипов или средах с одним потоком. Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении. См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.

Для этого руководства в этом классе используется один тестовый проход. Позже можно добавить другие сценарии и поэкспериментировать с этой моделью. Добавьте поездку для проверки прогнозирования стоимости обученной моделью с помощью метода `TestSinglePrediction()`, создав экземпляр `TaxiTrip`:

[!code-csharp[PredictionData](./snippets/predict-prices/csharp/Program.cs#23 "Create test data for single prediction")]

Затем спрогнозируйте стоимость на основе отдельного экземпляра данных о поездке на такси и передайте ее в `PredictionEngine`, добавив следующие строки кода в метод `TestSinglePrediction()`:

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#24 "Create a prediction of taxi fare")]

Функция [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) создает прогноз по одному экземпляру данных.

Чтобы отобразить прогнозируемую плату за указанную поездку, добавьте в метод `TestSinglePrediction` следующий код:

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#25 "Display the prediction.")]

Запустите программу, чтобы узнать прогноз платы за такси для тестового примера.

Поздравляем! Вы успешно создали модель машинного обучения для прогнозирования платы за проезд в такси, оценили ее точность и использовали ее для получения прогнозов. Исходный код для этого руководства можно найти в репозитории GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TaxiFarePrediction).

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как:

> [!div class="checklist"]
>
> * Подготовка и анализ данных
> * Создание конвейера обучения
> * Загрузка и преобразование данных
> * Выбор алгоритма обучения
> * Обучение модели
> * Оценка модели
> * Использование модели для прогнозирования

Переходите к следующему руководству.

> [!div class="nextstepaction"]
> [Кластеризация ирисов Фишера](iris-clustering.md)
