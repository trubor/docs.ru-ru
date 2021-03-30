---
title: Учебник. Анализ комментариев на веб-сайте — двоичная классификация
description: В этом руководстве показано, как создать консольное приложение .NET Core, которое классифицирует мнения, выраженные в комментариях с веб-сайта, и предпринимает соответствующие действия. Двоичный классификатор тональности использует C# в Visual Studio.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3dbcb3cbd4eea2d01638bedc7123f570ff9d64d1
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874594"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Учебник. Анализ мнений пользователей в комментариях с веб-сайта с помощью двоичной классификации в ML.NET

В этом руководстве показано, как создать консольное приложение .NET Core, которое классифицирует мнения, выраженные в комментариях с веб-сайта, и предпринимает соответствующие действия. Двоичный классификатор тональности использует C# в Visual Studio 2017.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> - Создание консольного приложения
> - Подготовка данных
> - Загрузка данных
> - Сборка и обучение модели
> - Оценка модели
> - Использование модели для прогноза
> - Просмотр результатов

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis).

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2017 версии 15.6 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core"

- [Набор данных — предложения с меткой тональности UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP-файл)

## <a name="create-a-console-application"></a>Создание консольного приложения

1. Создайте **консольное приложение .NET Core** с именем SentimentAnalysis.

2. Создайте каталог с именем *Data* в проекте, чтобы сохранять файлы набора данных.

3. Установите **пакет NuGet для Microsoft.ML**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакета, а затем выберите вкладку **Обзор**. Найдите **Microsoft.ML**, выберите пакет и нажмите кнопку **Установить**. Продолжите установку, соглашаясь с условиями лицензии для выбранного пакета.

## <a name="prepare-your-data"></a>подготавливать данные;

> [!NOTE]
> Наборы данных в этом руководстве взяты из статьи From Group to Individual Labels using Deep Features ("Переход от групповых меток к индивидуальным при помощи глубинных признаков"), Котциас (Kotzias) и др., KDD 2015, и размещены в репозитории машинного обучения UCI Д. Дуа (D. Dua) и Э. Карра Танискиду (E. Karra Taniskidou) (2017). UCI Machine Learning Repository (Репозиторий машинного обучения UCI) [http://archive.ics.uci.edu/ml ]. Ирвайн, Калифорния: Калифорнийский университет, Школа информационных технологий и компьютерных наук.

1. Скачайте [ZIP-файл набора данных предложений с меткой тональности UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) и извлеките его содержимое.

2. Скопируйте файл `yelp_labelled.txt` в созданный каталог *Data*.

3. В обозревателе решений щелкните правой кнопкой мыши файл `yelp_labeled.txt` и выберите пункт **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

### <a name="create-classes-and-define-paths"></a>Создание классов и определение путей

1. Добавьте следующие новые операторы `using` в начало файла *Program.cs*:

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Добавьте следующий код в строку прямо над методом `Main`, чтобы создать поле для хранения недавно скачанного пути к файлу набора данных:

    [!code-csharp[Declare global variables](./snippets/sentiment-analysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Затем создайте классы для входных данных и прогнозов. Добавьте в проект новый класс:

    - В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.

    - В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentData.cs*. Теперь нажмите кнопку **Добавить**.

1. Файл *SentimentData.cs* откроется в редакторе кода. Добавьте следующий оператор `using` в начало файла *SentimentData.cs*.

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Удалите из файла *SentimentData.cs* существующее определение класса и добавьте следующий код с двумя классами `SentimentData` и `SentimentPrediction`:

    [!code-csharp[DeclareTypes](./snippets/sentiment-analysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Как вы подготовили данные

Класс входного набора данных, `SentimentData`, имеет `string` для комментариев пользователя (`SentimentText`) и `bool` (`Sentiment`) значение 1 (положительная) или 0 (отрицательная) для определения тональности. Оба поля имеют атрибуты [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29), которые описывают порядок файла данных каждого поля.  Кроме того, свойство `Sentiment` имеет атрибут[ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A), чтобы обозначить его как поле `Label`. В примере файла ниже отсутствует строка заголовка. Сам файл выглядит следующим образом:

|SentimentText                         |Тональность (метка) |
|--------------------------------------|----------|
|Официантка немного медленная.|    0     |
|Корочка так себе.                    |    0     |
|Ого... Отличное место.              |    1     |
|Обслуживание очень быстрое.              |    1     |

`SentimentPrediction` — этот класс прогноза используется после обучения модели. Он наследует от `SentimentData` таким образом, чтобы входные данные `SentimentText` могли отображаться вместе с выходными данными прогноза. Логическое значение `Prediction` является значением, которое модель прогнозирует при предоставлении новых входных данных `SentimentText`.

Класс выходных данных `SentimentPrediction` содержит два свойства, вычисляемые в модели: `Score` — необработанная оценка, вычисляемая в модели, и `Probability` — оценка, откалиброванная по вероятности того, что текст имеет положительную тональность.

В этом учебнике самым важным свойством является `Prediction`.

## <a name="load-the-data"></a>Загрузка данных

Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView). `IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые). Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).

[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для всех операций ML.NET. Инициализация `mlContext` создает новую среду ML.NET, которую могут совместно использовать объекты рабочего процесса создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

Необходимо подготовить приложение и затем загружать данные.

1. Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную mlContext:

    [!code-csharp[CreateMLContext](./snippets/sentiment-analysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Добавьте в следующую строку метода `Main()` приведенный ниже код:

    [!code-csharp[CallLoadData](./snippets/sentiment-analysis/csharp/Program.cs#CallLoadData)]

3. Создайте метод `LoadData()` сразу после метода `Main()`, вставив в него следующий код:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    Метод `LoadData()` выполняет следующие задачи:

    - загрузка данных;
    - Разделяет скачанный набор данных на наборы данных для обучения и тестирования.
    - Возвращает два набора данных — для обучения и для тестирования.

4. Добавьте следующий код в первую строку метода `LoadData()`:

    [!code-csharp[LoadData](./snippets/sentiment-analysis/csharp/Program.cs#LoadData "loading dataset")]

    Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл. Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Разделение набора данных для обучения и тестирования модели

При подготовке модели можно использовать часть набора данных для обучения, а другую часть — для проверки точности модели.

1. Чтобы разделить скачанные данные на необходимые наборы данных, добавьте код в следующей строке метода `LoadData()`:

    [!code-csharp[SplitData](./snippets/sentiment-analysis/csharp/Program.cs#SplitData "Split the Data")]

    Приведенный выше код использует метод [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A), чтобы разделить загруженный набор данных на учебный и проверочный наборы данных и возвратить их в класс <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData>. Укажите процент тестовых данных с помощью параметра `testFraction`. Значение по умолчанию — 10 %, но в этом случае лучше использовать 20 % для оценки большего объема данных.

2. Верните `splitDataView` в конце метода `LoadData()`.

    [!code-csharp[ReturnSplitData](./snippets/sentiment-analysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Сборка и обучение модели

1. В следующей строке кода в методе `Main()` добавьте приведенный ниже вызов метода `BuildAndTrainModel`:

    [!code-csharp[CallBuildAndTrainModel](./snippets/sentiment-analysis/csharp/Program.cs#CallBuildAndTrainModel)]

    Метод `BuildAndTrainModel()` выполняет следующие задачи:

    - извлечение и преобразование данных;
    - обучение модели;
    - прогноз тональности на основе тестовых данных;
    - возвращение модели.

2. Создайте метод `BuildAndTrainModel()` сразу после метода `Main()`, вставив в него следующий код:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Извлечение и преобразование данных

1. Добавьте следующую строку кода для вызова `FeaturizeText`:

    [!code-csharp[FeaturizeText](./snippets/sentiment-analysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    Метод `FeaturizeText()` в приведенном выше коде преобразует текстовый столбец (`SentimentText`) в числовой столбец типа ключа `Features`, который используется алгоритмом машинного обучения: он добавляет его как новый столбец набора данных:

    |SentimentText                         |Тональность |Функции              |
    |--------------------------------------|----------|----------------------|
    |Официантка немного медленная.|    0     |[0.76, 0.65, 0.44, …] |
    |Корочка так себе.                    |    0     |[0.98, 0.43, 0.54, …] |
    |Ого... Отличное место.              |    1     |[0.35, 0.73, 0.46, …] |
    |Обслуживание очень быстрое.              |    1     |[0.39, 0, 0.75, …]    |

### <a name="add-a-learning-algorithm"></a>Добавление алгоритма обучения

Это приложение использует алгоритм классификации, который классифицирует элементы или строки данных. Приложение классифицирует комментарии веб-сайта как положительные или отрицательные, поэтому это задача двоичной классификации.

Добавьте задачу машинного обучения к определениям преобразований данных, добавив следующее в следующей строке кода в `BuildAndTrainModel()`:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](./snippets/sentiment-analysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) — ваш алгоритм обучения классификации. Он добавляется в `estimator` и принимает `SentimentText` с присвоенными признаками (`Features`) и входные параметры `Label`, чтобы пройти обучение по историческим данным.

### <a name="train-the-model"></a>Обучение модели

Обучите модель на основе данных `splitTrainSet` и получите обученную модель, добавив в метод `BuildAndTrainModel()` следующие строки кода:

[!code-csharp[TrainModel](./snippets/sentiment-analysis/csharp/Program.cs#TrainModel "Train the model")]

Метод [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) обучает модель путем преобразования набора данных и применения обучения.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Возврат обученной модели для оценки

 Выполните возврат модели в конце метода `BuildAndTrainModel()`.

[!code-csharp[ReturnModel](./snippets/sentiment-analysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Оценка модели

После обучения модели с помощью проверочных данных производится валидация производительности модели.

1. Создайте метод `Evaluate()` сразу после `BuildAndTrainModel()`, используя следующий код:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    Метод `Evaluate()` выполняет следующие задачи:

    - загрузка тестового набора данных;
    - создание средства оценки BinaryClassification;
    - оценка модели и создание метрик;
    - отображение метрик.

2. Добавьте вызов нового метода из метода `Main()`, сразу после вызова метода `BuildAndTrainModel()`, используя следующий код:

    [!code-csharp[CallEvaluate](./snippets/sentiment-analysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Преобразуйте данные `splitTestSet`, добавив в метод `Evaluate()` следующий код:

    [!code-csharp[PredictWithTransformer](./snippets/sentiment-analysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Предыдущий код использует метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A), чтобы сделать прогнозы для нескольких входных строк тестового набора данных.

4. Оцените модель, добавив в метод `Evaluate()` следующую строку кода:

    [!code-csharp[ComputeMetrics](./snippets/sentiment-analysis/csharp/Program.cs#Evaluate "Compute Metrics")]

После получения прогноза (`predictions`) метод [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) оценивает модель, сравнивая спрогнозированные значения с фактическими метками (`Labels`) в тестовом наборе данных, а затем возвращает объект [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) как метрики эффективности модели.

### <a name="displaying-the-metrics-for-model-validation"></a>Отображение метрик для проверки модели

Воспользуйтесь приведенным ниже кодом, чтобы отобразить метрики.

[!code-csharp[DisplayMetrics](./snippets/sentiment-analysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- Метрика `Accuracy` возвращает точность модели — это доля правильных прогнозов в тестовом наборе.

- Метрика `AreaUnderRocCurve` показывает уверенность модели в правильности классификации с положительными и отрицательными классами. Значение `AreaUnderRocCurve` должно быть максимально близким к единице.

- Метрика `F1Score` содержит F1-оценку модели, который является мерой баланса между [точностью](../resources/glossary.md#precision) и [полнотой](../resources/glossary.md#recall).  Значение `F1Score` должно быть максимально близким к единице.

### <a name="predict-the-test-data-outcome"></a>Прогнозировать результаты для тестовых данных

1. Создайте метод `UseModelWithSingleItem()` сразу после метода `Evaluate()`, вставив в него следующий код:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Метод `UseModelWithSingleItem()` выполняет следующие задачи:

    - создание отдельного комментария тестовых данных;
    - прогноз тональности на основе тестовых данных;
    - объединение тестовых данных и прогнозов для создания отчетов;
    - отображение результатов прогнозирования.

2. Добавьте вызов нового метода из метода `Main()`, сразу после вызова метода `Evaluate()`, используя следующий код:

    [!code-csharp[CallUseModelWithSingleItem](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Давайте добавим следующий код в качестве первой строки в методе `UseModelWithSingleItem()`:

    [!code-csharp[CreatePredictionEngine](./snippets/sentiment-analysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным. Допустимо использовать в средах прототипов или средах с одним потоком. Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении. См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.

4. Добавьте комментарий для проверки прогнозирования обученной модели в методе `UseModelWithSingleItem()`, создав экземпляр `SentimentData`:

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Передайте данные тестового комментария в [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), добавив следующие строки кода в метод `UseModelWithSingleItem()`:

    [!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    Функция [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) создает прогноз по одной строке данных.

6. Выведите `SentimentText` и соответствующий прогноз тональности, используя следующий код:

    [!code-csharp[OutputPrediction](./snippets/sentiment-analysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Использование модели для прогнозирования

### <a name="deploy-and-predict-batch-items"></a>Развертывание и прогнозирование элементов пакета

1. Создайте метод `UseModelWithBatchItems()` сразу после метода `UseModelWithSingleItem()`, вставив в него следующий код:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Метод `UseModelWithBatchItems()` выполняет следующие задачи:

    - создание пакетных тестовых данных;
    - прогноз тональности на основе тестовых данных;
    - объединение тестовых данных и прогнозов для создания отчетов;
    - отображение результатов прогнозирования.

2. Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `UseModelWithSingleItem()`, используя следующий код:

    [!code-csharp[CallPredictModelBatchItems](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Добавьте новые комментарии, чтобы проверить прогнозы обученной модели, в метод `UseModelWithBatchItems()`:

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Предсказание тональности на основе комментариев

Использование модели для прогнозирования тональности комментариев с помощью метода [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A):

[!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Объедините и отобразите прогнозы

Создайте заголовок для результатов с помощью следующего кода:

[!code-csharp[OutputHeaders](./snippets/sentiment-analysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Так как `SentimentPrediction` наследуется от `SentimentData`, `Transform()` метод заполняет `SentimentText` прогнозируемыми полями. В ходе обработки ML.NET каждый компонент добавляет столбцы, что упрощает отображение результатов:

[!code-csharp[DisplayPredictions](./snippets/sentiment-analysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Результаты

Результаты выполнения должны выглядеть примерно так, как показано ниже. Во время обработки отображаются сообщения. Вы можете видеть предупреждения или обработанные сообщения. Для удобства они удалены из следующих результатов.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Поздравляем! Вы успешно создали модель машинного обучения для классификации и прогнозирования тональности сообщений.

Построение успешных моделей — итеративный процесс. Изначально эта модель имеет низкое качество, так как в руководстве используются небольшие наборы данных для быстрого обучения. Если вам требуется модель более высокого качества, можно попытаться улучшить ее, использовав более крупные наборы данных для обучения или выбрав другие алгоритмы обучения с разными [гиперпараметрами](../resources/glossary.md#hyperparameter) для каждого алгоритма.

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis).

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как:
> [!div class="checklist"]
>
> - Создание консольного приложения
> - Подготовка данных
> - Загрузка данных
> - Сборка и обучение модели
> - Оценка модели
> - Использование модели для прогноза
> - Просмотр результатов

Переходите к следующему руководству:
> [!div class="nextstepaction"]
> [Классификация задач](github-issue-classification.md)
