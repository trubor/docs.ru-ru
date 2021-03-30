---
title: Учебник. Анализ тональности отзывов с помощью модели TensorFlow
description: В этом руководстве показано, как классифицировать тональность комментариев на веб-сайте с помощью предварительно обученной модели TensorFlow. Двоичный классификатор тональности — это консольное приложение на C#, разработанное с помощью Visual Studio.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0c2cfd46375406726913a83d67c45ff922a1085b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104877011"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Учебник. Анализ тональности отзывов о фильмах с помощью предварительно обученной модели TensorFlow в ML.NET

В этом руководстве показано, как классифицировать тональность комментариев на веб-сайте с помощью предварительно обученной модели TensorFlow. Двоичный классификатор тональности — это консольное приложение на C#, разработанное с помощью Visual Studio.

Модель TensorFlow, используемая в этом руководстве, была обучена на отзывах о фильмах из базы данных IMDB. Завершив разработку приложения, вы сможете добавить текст отзыва о фильме, и приложение сообщит вам, положительный это отзыв или отрицательный.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> * Загрузить предварительно обученную модель TensorFlow.
> * Преобразовать текст комментария на веб-сайте в признаки, пригодные для модели.
> * Использование модели для прогноза

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TextClassificationTF).

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2017 версии 15.6 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".

## <a name="setup"></a>Установка

### <a name="create-the-application"></a>Создание приложения

1. Создайте **консольное приложение .NET Core** с именем TextClassificationTF.

2. Создайте каталог с именем *Data* в проекте, чтобы сохранять файлы набора данных.

3. Установите **пакет NuGet для Microsoft.ML**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакета, а затем выберите вкладку **Обзор**. Найдите **Microsoft.ML**, выберите пакет и нажмите кнопку **Установить**. Продолжите установку, соглашаясь с условиями лицензии для выбранного пакета. Повторите эти действия для пакетов **Microsoft.ML.TensorFlow**, **Microsoft.ML.SampleUtils** и **SciSharp.TensorFlow.Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Добавление модели TensorFlow в проект

> [!NOTE]
> Модель для этого руководства взята из репозитория GitHub [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/main/Microsoft.ML.TensorFlow.TestModels/sentiment_model) и сохранена в формате TensorFlow SavedModel.

1. Скачайте файл [sentiment_model zip](https://github.com/dotnet/samples/blob/main/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true) и распакуйте его.

    ZIP-файл содержит:

    * `saved_model.pb`: собственно модель TensorFlow. Модель принимает целочисленный массив признаков фиксированной длины (600 символов), представляющий текст в строке отзыва IMDB, и выводит две вероятности, сумма которых равна 1: вероятность того, что указанный отзыв имеет положительную тональность, и вероятность того, что отзыв имеет отрицательную тональность.
    * `imdb_word_index.csv`: сопоставление отдельных слов с целочисленным значением. Сопоставление используется для создания входных признаков для модели TensorFlow.

2. Скопируйте содержимое самого внутреннего каталога `sentiment_model` в каталог `sentiment_model` проекта *TextClassificationTF*. Этот каталог содержит модель и дополнительные файлы поддержки, необходимые для работы с этим руководством, как показано на следующем рисунке:

   ![Содержимое каталога sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. В обозревателе решений щелкните правой кнопкой мыши каждый файл в каталоге `sentiment_model` и подкаталоге и выберите **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

### <a name="add-using-statements-and-global-variables"></a>Добавление операторов using и глобальных переменных

1. Добавьте следующие новые операторы `using` в начало файла *Program.cs*:

   [!code-csharp[AddUsings](./snippets/text-classification-tf/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Создайте две глобальные переменные прямо над методом `Main`, чтобы указать путь к сохраненному файлу модели и длину вектора признаков.

   [!code-csharp[DeclareGlobalVariables](./snippets/text-classification-tf/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath` — путь к файлу обученной модели.
    * `FeatureLength` — длина целочисленного массива признаков, который ожидается в модели.

### <a name="model-the-data"></a>Моделирование данных

Отзывы на фильмы — это текст произвольной формы. Приложение преобразует текст в формат входных данных, ожидаемый в модели, за несколько отдельных этапов.

Первый этап — разделение текста на отдельные слова и сопоставление каждого слова с кодировкой целого числа при помощи предоставленного файла сопоставления. Результатом этого преобразования является массив целых чисел переменной длины, которая соответствует числу слов в предложении.

|Свойство.| Значение|Type|
|-------------|-----------------------|------|
|ReviewText|this film is really good (это очень хороший фильм)|string|
|VariableLengthFeatures|14,22,9,66,78,... |int[]|

Затем размер массива признаков переменной длины изменяется на фиксированную длину 600. Это ожидаемая длина для модели TensorFlow.

|Свойство.| Значение|Type|
|-------------|-----------------------|------|
|ReviewText|this film is really good (это очень хороший фильм)|string|
|VariableLengthFeatures|14,22,9,66,78,... |int[]|
|Функции|14,22,9,66,78,... |int[600]|

1. Создайте класс для входных данных после метода `Main`:

    [!code-csharp[MovieReviewClass](./snippets/text-classification-tf/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    У класса входных данных `MovieReview` есть `string` (строка) для комментариев пользователей (`ReviewText`).

1. Создайте класс для признаков переменной длины после метода `Main`:

    [!code-csharp[VariableLengthFeatures](./snippets/text-classification-tf/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    Свойство `VariableLengthFeatures` имеет атрибут [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A), который указывает вектор.  Все элементы вектора должны относиться к одному типу. В наборах данных с большим количеством столбцов загрузка нескольких столбцов в виде одного вектора сокращает количество передаваемых данных при преобразовании данных.

    Этот класс используется в действии `ResizeFeatures`. Имена его свойств (в этом случае — только одного свойства) используются для указания того, какие столбцы в DataView могут использоваться в качестве _входных данных_ для пользовательского действия сопоставления.

1. Создайте класс для признаков фиксированной длины после метода `Main`:

    [!code-csharp[FixedLengthFeatures](./snippets/text-classification-tf/csharp/Program.cs#FixedLengthFeatures)]

    Этот класс используется в действии `ResizeFeatures`. Имена его свойств (в этом случае — только одного свойства) используются для указания того, какие столбцы в DataView могут использоваться в качестве _выходных данных_ для пользовательского действия сопоставления.

    Обратите внимание, что имя свойства `Features` определяется моделью TensorFlow. Это имя свойства нельзя изменить.

1. Создайте класс для прогноза после метода `Main`:

    [!code-csharp[Prediction](./snippets/text-classification-tf/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` — этот класс прогноза используется после обучения модели. `MovieReviewSentimentPrediction` имеет один массив `float` (`Prediction`) и атрибут `VectorType`.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Создание MLContext, словаря подстановки и действия для изменения размера признаков

[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для всех операций ML.NET. Инициализация `mlContext` создает новую среду ML.NET, которую могут совместно использовать объекты рабочего процесса создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

1. Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную mlContext:

   [!code-csharp[CreateMLContext](./snippets/text-classification-tf/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. Создайте словарь для кодирования слов в виде целых чисел с помощью метода [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A), чтобы загрузить данные сопоставления из файла, как показано в следующей таблице.

    |Слово     |Индекс    |
    |---------|---------|
    |kids (дети)     |  362    |
    |want (хотеть)     |  181    |
    |wrong (неправильно)    |  355    |
    |effects (эффекты)  |  302    |
    |feeling (чувство)  |  547    |

    Добавьте приведенный ниже код для создания карты подстановки.

    [!code-csharp[CreateLookupMap](./snippets/text-classification-tf/csharp/Program.cs#CreateLookupMap)]

1. Добавьте `Action`, чтобы преобразовать массив целых чисел переменной длины в массив целых чисел фиксированного размера с помощью следующих строк кода:

   [!code-csharp[ResizeFeatures](./snippets/text-classification-tf/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Загрузка предварительно обученной модели TensorFlow

1. Добавьте код для загрузки модели TensorFlow:

    [!code-csharp[LoadTensorFlowModel](./snippets/text-classification-tf/csharp/Program.cs#LoadTensorFlowModel)]

    После загрузки модели можно извлечь схему ее входных и выходных данных. Схемы отображаются только для интереса и изучения. Для работы окончательного варианта приложения этот код не требуется.

    [!code-csharp[GetModelSchema](./snippets/text-classification-tf/csharp/Program.cs#GetModelSchema)]

    Схема входных данных — это массив фиксированной длины из слов, закодированных в виде целых чисел. Схема выходных данных — это массив вероятностей с плавающей запятой, указывающий, является ли тональности обзора отрицательной или положительной. Сумма этих значений равна 1, так как вероятность положительной тональности является дополнением вероятности отрицательной тональности.

## <a name="create-the-mlnet-pipeline"></a>Создание конвейера ML.NET

1. Создайте конвейер и разделите входной текст на слова с помощью преобразования [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A), чтобы разбить текст на слова в виде следующей строки кода:

   [!code-csharp[TokenizeIntoWords](./snippets/text-classification-tf/csharp/Program.cs#TokenizeIntoWords)]

   В преобразовании [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) используются пробелы для разбиения текста или строки на слова. Оно создает новый столбец и разделяет каждую входную строку на вектор подстрок на основе определяемого пользователем разделителя.

1. Сопоставьте слова с кодировкой целых чисел, используя таблицу подстановки, приведенную выше:

    [!code-csharp[MapValue](./snippets/text-classification-tf/csharp/Program.cs#MapValue)]

1. Измените размер кодировок целых чисел переменной длины на фиксированную длину, необходимую для модели:

    [!code-csharp[CustomMapping](./snippets/text-classification-tf/csharp/Program.cs#CustomMapping)]

1. Классифицируйте входные данные с помощью загруженной модели TensorFlow:

    [!code-csharp[ScoreTensorFlowModel](./snippets/text-classification-tf/csharp/Program.cs#ScoreTensorFlowModel)]

    Имя выходных данных модели TensorFlow — `Prediction/Softmax`. Обратите внимание, что имя `Prediction/Softmax` определяется моделью TensorFlow. Это имя нельзя изменить.

1. Создайте новый столбец для прогнозирования выходных данных:

    [!code-csharp[SnippetCopyColumns](./snippets/text-classification-tf/csharp/Program.cs#SnippetCopyColumns)]

    Необходимо скопировать столбец `Prediction/Softmax` в столбец с именем, которое можно использовать как свойство в классе C# `Prediction`. В имени свойства C# нельзя использовать символ `/`.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Создание модели ML.NET из конвейера

1. Добавьте код для создания модели из конвейера:

    [!code-csharp[SnippetCreateModel](./snippets/text-classification-tf/csharp/Program.cs#SnippetCreateModel)]

    Модель ML.NET создается из цепочки средств оценки в конвейере с помощью вызова метода `Fit`. В этом случае мы не будем подбирать данные для создания модели, так как модель TensorFlow уже обучена. Мы предоставим пустой объект представления данных в соответствии с требованиями метода `Fit`.

## <a name="use-the-model-to-make-a-prediction"></a>Использование модели для прогноза

1. Добавьте метод `PredictSentiment` под методом `Main`.

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Добавьте следующий код в качестве первой строки в методе `PredictSentiment()` для создания `PredictionEngine`:

    [!code-csharp[CreatePredictionEngine](./snippets/text-classification-tf/csharp/Program.cs#CreatePredictionEngine)]

    Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным. Допустимо использовать в средах прототипов или средах с одним потоком. Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении. См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.

1. Добавьте комментарий для проверки прогнозирования обученной модели в методе `Predict()`, создав экземпляр `MovieReview`:

    [!code-csharp[CreateTestData](./snippets/text-classification-tf/csharp/Program.cs#CreateTestData)]

1. Передайте тестовые данные комментариев в `Prediction Engine`, добавив следующие строки кода в метод `PredictSentiment()`:

    [!code-csharp[Predict](./snippets/text-classification-tf/csharp/Program.cs#Predict)]

1. Функция [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) создает прогноз по одной строке данных.

    |Свойство.| Значение|Type|
    |-------------|-----------------------|------|
    |Прогноз|[0.5459937, 0.454006255]|float[]|

1. Выведите прогноз тональности, используя следующий код:

    [!code-csharp[DisplayPredictions](./snippets/text-classification-tf/csharp/Program.cs#DisplayPredictions)]

1. Добавьте вызов `PredictSentiment` в конце метода `Main`:

    [!code-csharp[CallPredictSentiment](./snippets/text-classification-tf/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Результаты

Скомпонуйте и запустите приложение.

Результаты выполнения должны выглядеть примерно так, как показано ниже. Во время обработки отображаются сообщения. Вы можете видеть предупреждения или обработанные сообщения. Для удобства эти сообщения удалены из следующих результатов.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Поздравляем! Вы успешно создали модель машинного обучения для классификации и прогнозирования тональности сообщений с помощью предварительно обученной модели `TensorFlow` в ML.NET.

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TextClassificationTF).

В этом руководстве вы узнали, как:
> [!div class="checklist"]
>
> * Загрузить предварительно обученную модель TensorFlow.
> * Преобразовать текст комментария на веб-сайте в признаки, пригодные для модели.
> * Использование модели для прогноза
