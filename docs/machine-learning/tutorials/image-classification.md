---
title: Учебник. Модель классификации изображений ML.NET из TensorFlow
description: Узнайте, как передавать знания из существующей модели TensorFlow в новую модель классификации изображений ML.NET. Модель TensorFlow была обучена для классификации изображений по тысячам категорий. Модель ML.NET использует передачу обучения, чтобы классифицировать изображения по меньшему количеству более широких категорий.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: b3e5617979d1635248f87db6008d3e234bb3ffc5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104877037"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Учебник. Создание модели классификации изображений ML.NET на основе предварительно обученной модели TensorFlow

Узнайте, как передавать знания из существующей модели TensorFlow в новую модель классификации изображений ML.NET.

Модель TensorFlow была обучена для классификации изображений по тысячам категорий. Модель ML.NET использует часть модели TensorFlow в своем конвейере для обучения модели, классифицирующей изображения по 3-м категориям.

Обучение модели для [классификации изображений](https://en.wikipedia.org/wiki/Outline_of_object_recognition) с нуля предусматривает настройку нескольких миллионов параметров, а также использование огромных объемов помеченных данных обучения и вычислительных ресурсов (сотни часов работы GPU). Хотя передача обучения не настолько эффективна, как обучение пользовательской модели с нуля, этот подход позволяет значительно ускорить соответствующий процесс с использованием всего нескольких тысяч изображений (а не миллионов помеченных изображений) для быстрого создания пользовательской модели (в пределах часа на компьютере без GPU). В этом учебнике этот процесс еще более уменьшен: используется только десяток изображений для обучения.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> * Определение проблемы
> * внедрить предварительно обученную модель TensorFlow в конвейер ML.NET;
> * обучить и оценить модель ML.NET;
> * классифицировать тестовое изображение.

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF). Обратите внимание на то, что по умолчанию конфигурации проекта .NET в этом руководстве предназначена для .NET Core 2.2.

## <a name="what-is-transfer-learning"></a>Что собой представляет передача обучения?

Передача обучения — это процесс использования знаний, полученных при решении одной проблемы, и применения их к другой, но похожей проблеме.

В этом учебнике используется часть модели TensorFlow, обученной для классификации изображений по тысяче категорий, в модели ML.NET, которая классифицирует изображения по 3-м категориям.

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".
* [ZIP-файл каталога ресурсов руководства.](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [Модель машинного обучения Inception версии 1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Выбор типа задачи машинного обучения

### <a name="deep-learning"></a>Глубокое обучение

[Глубокое обучение](https://en.wikipedia.org/wiki/Deep_learning) — это разновидность машинного обучения, которая произвела революцию в области компьютерного зрения и распознавания речи.

Модели глубокого обучения обучаются на крупных наборах [помеченных данных](https://en.wikipedia.org/wiki/Labeled_data) с использованием [нейронных сетей](https://en.wikipedia.org/wiki/Artificial_neural_network), которые содержат множество слоев обучения. Глубокое обучение:

* лучше выполняет некоторые задачи, например в области компьютерного зрения;
* Требует огромных объемов данных для обучения.

Классификация изображений — это типичная задача Машинного обучения, которая позволяет автоматически классифицировать изображения по категориям, например:

* для определения того, содержит ли изображение человеческое лицо;
* для различения изображений котов и собак.

 Она также помогает определить тип объекта на изображении — еда, игрушка или прибор:

![Изображение с пиццей](./media/image-classification/220px-Pepperoni_pizza.jpg)
![Изображение с плюшевым мишкой](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![Изображение с тостером](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Изображения выше принадлежат Викискладу и имеют следующие атрибуты:
>
> * 220px-Pepperoni_pizza.jpg, открытый источник, <https://commons.wikimedia.org/w/index.php?curid=79505>;
> * 119px-Nalle_-_a_small_brown_teddy_bear.jpg, автор — [Jonik](https://commons.wikimedia.org/wiki/User:Jonik), автофотография, лицензия CC BY-SA 2.0, <https://commons.wikimedia.org/w/index.php?curid=48166>;
> * 193px-Broodrooster.jpg, автор — [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972), собственное фото, лицензия CC BY-SA 3.0, <https://commons.wikimedia.org/w/index.php?curid=27403>.

Модель `Inception model` обучена классифицировать изображения по тысяче категорий, но в этом учебнике вам столько категорий не нужно. Вам также нужны четко определенные категории. Перейдем к этапу передачи (`transfer`) этого процесса передачи обучения (`transfer learning`). Вы можете передать способность `Inception model` распознавать и классифицировать изображения в новые ограниченные категории своего классификатора изображений.

* еда;
* игрушка;
* прибор.

В этом учебнике используется модель глубокого обучения TensorFlow [Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), популярная модель распознавания изображений, обученная с помощью набора данных `ImageNet`. Модель TensorFlow классифицирует все изображения по тысячам классов, таких как "зонт", "жакет" и "посудомоечная машина".

Так как `Inception model` уже обучена на тысячах различных изображений, она содержит [признаки изображений](https://en.wikipedia.org/wiki/Feature_(computer_vision)), необходимые для их идентификации. Мы можем использовать эти внутренние признаки изображений в модели для обучения новой модели с гораздо меньшим числом классов.

Как показано на схеме ниже, вам нужно добавить ссылки на пакеты NuGet ML.NET в приложения .NET Core или .NET Framework. На внутреннем уровне ML.NET включает и ссылается на встроенную библиотеку `TensorFlow`, которая позволяет создавать код, загружающий существующую обученную модель `TensorFlow`.

![Схема преобразования ML.NET с использованием TensorFlow](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Многоклассовая классификация

После использования модели Inception TensorFlow для извлечения признаков, подходящих в качестве входных данных для классического алгоритма машинного обучения, мы добавим [многоклассовый классификатор](../resources/tasks.md#multiclass-classification) ML.NET.

В этом случае используется алгоритм [мультиномиальной логистической регрессии](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

Алгоритм, реализованный этим инструктором, хорошо работает в задачах с большим количеством признаков, что характерно для модели глубокого обучения, работающей с данными изображений.

### <a name="data"></a>Данные

Доступны два источника данных: файл `.tsv` и файлы образов.  Файл `tags.tsv` содержит два столбца: первый определен как `ImagePath`, а во втором указана метка `Label`, соответствующая изображению. В примере файла ниже отсутствует строка заголовка. Сам файл выглядит следующим образом:

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

Изображения для обучения и тестирования расположены в папках ресурсов, которые вы скачали в виде ZIP-файла. Эти изображения принадлежат Викискладу.
> *[Викисклад](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), бесплатный репозиторий мультимедиа.* Получено 17 октября 2018 г. в 10:48 со страниц: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
> <https://commons.wikimedia.org/wiki/Teddy_bear>

## <a name="setup"></a>Установка

### <a name="create-a-project"></a>Создание проекта

1. Создайте **консольное приложение .NET Core** с именем TransferLearningTF.

1. Установите **пакет NuGet для Microsoft.ML**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    * В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.
    * Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор" и выполните поиск **Microsoft.ML**.
    * Нажмите кнопку **Установить**.
    * Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**.
    * Нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с условиями лицензионного соглашения для указанных пакетов.
    * Повторите эти шаги для пакетов **Microsoft.ML.ImageAnalytics**, **SciSharp.TensorFlow.Redist** и **Microsoft.ML.TensorFlow**.

### <a name="download-assets"></a>Скачивание ресурсов

1. Скачайте [ZIP-файл каталога с ресурсами проекта](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip) и распакуйте его.

1. Скопируйте каталог `assets` в каталог проекта *TransferLearningTF*. Этот каталог и его подкаталоги содержат данные и файлы поддержки (за исключением модели Inception, которую вы скачаете и добавите на следующем шаге), необходимые для работы с этим руководством.

1. Скачайте [модель Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) и распакуйте ее.

1. Скопируйте содержание каталога `inception5h`, который вы распаковали, в каталог `assets/inception` проекта *TransferLearningTF*. Этот каталог содержит модель и дополнительные файлы поддержки, необходимые для работы с этим руководством, как показано на следующем рисунке:

   ![Содержание каталога Inception](./media/image-classification/inception-files.png)

1. В обозревателе решений щелкните правой кнопкой мыши каждый файл в каталоге и подкаталогах ресурсов и выберите **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

### <a name="create-classes-and-define-paths"></a>Создание классов и определение путей

1. Добавьте следующие новые операторы `using` в начало файла *Program.cs*:

    [!code-csharp[AddUsings](./snippets/image-classification/csharp/Program.cs#AddUsings)]

1. Добавьте следующий код в строке справа выше метода `Main` для указания пути к ресурсу:

    [!code-csharp[DeclareGlobalVariables](./snippets/image-classification/csharp/Program.cs#DeclareGlobalVariables)]

1. Создайте классы для входных данных и прогнозов.

    [!code-csharp[DeclareImageData](./snippets/image-classification/csharp/Program.cs#DeclareImageData)]

    `ImageData` является классом входных данных изображения и имеет следующие поля <xref:System.String>:

    * `ImagePath` содержит имя файла изображения.
    * `Label` содержит значение для метки изображения.

1. Добавьте новый класс в свой проект для `ImagePrediction`:

    [!code-csharp[DeclareImagePrediction](./snippets/image-classification/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction` является классом прогноза изображения и имеет следующие поля:

    * `Score` содержит процентное значение достоверности для конкретной классификации изображения.
    * `PredictedLabelValue` содержит значение для прогнозируемой метки классификации изображения.

    Класс `ImagePrediction` используется для прогнозирования после обучения модели. Он включает `string` (`ImagePath`) с путем к изображению. `Label` используется для применения и обучения модели. `PredictedLabelValue` используется для прогнозирования и оценки. Для оценки применяются входные обучающие данные, прогнозируемые значения и модель.

### <a name="initialize-variables-in-main"></a>Инициализация переменных в методе Main

1. Инициализируйте переменную `mlContext` с использованием нового экземпляра `MLContext`.  Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом:

    [!code-csharp[CreateMLContext](./snippets/image-classification/csharp/Program.cs#CreateMLContext)]

    [Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

### <a name="create-a-struct-for-inception-model-parameters"></a>Создание структуры для параметров модели Inception

1. Модель Inception имеет несколько параметров, которые необходимо передать. Создайте структуру, чтобы сопоставить значения параметров с понятными именами, с помощью следующего кода сразу после метода `Main()`:

    [!code-csharp[InceptionSettings](./snippets/image-classification/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Создание служебного метода для отображения данных

Поскольку вы будете отображать данные изображения и связанные прогнозы несколько раз, создайте метод программы отображения для обработки отображения изображений и результатов прогнозирования.

1. Создайте метод `DisplayResults()` сразу после структуры `InceptionSettings` с помощью следующего кода:

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Заполните текст метода `DisplayResults`:

    [!code-csharp[DisplayPredictions](./snippets/image-classification/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Создание служебного метода для TSV-файла

1. Создайте метод `ReadFromTsv()` сразу после метода `DisplayResults()`, вставив в него следующий код:

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Заполните текст метода `ReadFromTsv`:

    [!code-csharp[ReadFromTsv](./snippets/image-classification/csharp/Program.cs#ReadFromTsv)]

    Указанный ниже код анализирует файл `tags.tsv`, после чего добавляет путь к файлу к имени файла изображения для свойства `ImagePath` и загружает его и `Label` в объект `ImageData`.

### <a name="create-a-method-to-make-a-prediction"></a>Создание метода для формирования прогноза

1. Создайте метод `ClassifySingleImage()` непосредственно перед методом `DisplayResults()`, вставив в него следующий код:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Создайте объект `ImageData`, который хранит абсолютный путь и имя файла изображения для одного значения `ImagePath`. Добавьте такой код в следующие строки в методе `ClassifySingleImage()`:

    [!code-csharp[LoadImageData](./snippets/image-classification/csharp/Program.cs#LoadImageData)]

1. Создайте один прогноз, добавив следующий код в виде следующей строки в методе `ClassifySingleImage`:

    [!code-csharp[PredictSingle](./snippets/image-classification/csharp/Program.cs#PredictSingle)]

    Чтобы получить прогноз, используйте метод [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A). Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным. Допустимо использовать в средах прототипов или средах с одним потоком. Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении. См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.

1. Отобразите результат прогнозирования с помощью следующей строки кода в методе `ClassifySingleImage()`:

   [!code-csharp[DisplayPrediction](./snippets/image-classification/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Создание конвейера модели ML.NET

Конвейер модели ML.NET — это цепочка средств оценки. Обратите внимание, что во время создания конвейера выполнение не происходит. Объекты оценки создаются, но не выполняются.

1. Добавление метода для создания модели

    Этот метод является основным в учебнике. Он создает конвейер для модели и обучает конвейер для создания модели ML.NET. Он также оценивает модель по некоторым ранее неиспользуемым тестовым данным.

    Создайте метод `GenerateModel()` сразу после структуры `InceptionSettings` и непосредственно перед методом `DisplayResults()` с помощью следующего кода:

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Добавьте средства оценки для загрузки, изменения размера и извлечения пикселей из данных изображения:

    [!code-csharp[ImageTransforms](./snippets/image-classification/csharp/Program.cs#ImageTransforms)]

    Данные изображения должны обрабатываться в формате, который требуется модели TensorFlow. В этом случае изображения загружаются в память, преобразуются в соответствующий размер, а пиксели извлекаются в числовой вектор.

1. Добавьте средство оценки, чтобы загрузить модель TensorFlow и оценить ее:

    [!code-csharp[ScoreTensorFlowModel](./snippets/image-classification/csharp/Program.cs#ScoreTensorFlowModel)]

    Этот этап конвейера загружает модель TensorFlow в память, а затем обрабатывает вектор значений пикселей через сеть модели TensorFlow. Применение входных данных к модели глубокого обучения и формирование выходных данных с помощью модели называется **оценкой**. При полном использовании модели оценка делает вывод или прогноз.

    В этом случае используется вся модель TensorFlow, за исключением последнего слоя, который делает вывод. Выходные данные предпоследнего слоя помечаются как `softmax_2_preactivation`. Выходные данные этого слоя фактически являются вектором признаков, характеризующих исходные входные изображения.

    Этот вектор признаков, созданный моделью TensorFlow, будет использоваться в качестве входных данных для алгоритма обучения ML.NET.

1. Добавьте средство оценки, чтобы сопоставлять строковые метки в данных для обучения с целочисленными значениями ключа:

    [!code-csharp[MapValueToKey](./snippets/image-classification/csharp/Program.cs#MapValueToKey)]

    Для обучающего алгоритма ML.NET, добавляемого далее, метки должны быть в формате `key`, а не в виде произвольных строк. Ключ — это число, которое содержит сопоставление по принципу "один к одному" со строковым значением.

1. Добавьте алгоритм обучения ML.NET:

    [!code-csharp[AddTrainer](./snippets/image-classification/csharp/Program.cs#AddTrainer)]

1. Добавьте средство оценки для преобразования значения прогнозируемого ключа обратно в строку:

    [!code-csharp[MapKeyToValue](./snippets/image-classification/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Обучение модели

1. Загрузите данные для обучения с использованием оболочки [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)). Добавьте в следующую строку метода `GenerateModel()` приведенный ниже код:

    [!code-csharp[LoadData](./snippets/image-classification/csharp/Program.cs#LoadData "Load the data")]

    Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView). `IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые). Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).

1. Обучите модель сна основе данных, загруженных ранее:

    [!code-csharp[TrainModel](./snippets/image-classification/csharp/Program.cs#TrainModel)]

    Метод `Fit()` обучает модель путем применения набора данных для обучения к конвейеру.

## <a name="evaluate-the-accuracy-of-the-model"></a>Оценка точности модели

1. Загрузите и преобразуйте проверочные данные, добавив приведенный ниже код в следующую строку метода `GenerateModel`:

    [!code-csharp[LoadAndTransformTestData](./snippets/image-classification/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Есть несколько примеров изображений, которые можно использовать для оценки модели. Как и данные для обучения, их нужно загрузить в `IDataView`, чтобы модель могла их преобразовать.

1. Добавьте следующий код в метод `GenerateModel()` для оценки модели:

    [!code-csharp[Evaluate](./snippets/image-classification/csharp/Program.cs#Evaluate)]

    Получив прогноз, с помощью метода [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) вы сможете:

    * оценить модель (сравнивает спрогнозированные значения с тестовым набором данных `labels`);
    * получить метрики производительности модели.

1. Отобразите метрики точности модели.

    Используйте следующий код для отображения метрик, передачи результатов и выполнения действий по ним:

    [!code-csharp[DisplayMetrics](./snippets/image-classification/csharp/Program.cs#DisplayMetrics)]

    Для классификации изображений выполняется оценка следующих метрик:

    * `Log-loss` — см. раздел [Логарифмические потери](../resources/glossary.md#log-loss). Значение логарифмических потерь должно быть максимально близко к нулю.
    * `Per class Log-loss`. Значение логарифмических потерь для каждого класса должно быть максимально близко к нулю.

1. Добавьте следующий код, чтобы возвращать обученную модель:

    [!code-csharp[SaveModel](./snippets/image-classification/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Запуск приложения

1. Добавьте вызов `GenerateModel` в метод `Main` после создания класса MLContext:

    [!code-csharp[CallGenerateModel](./snippets/image-classification/csharp/Program.cs#CallGenerateModel)]

1. Добавьте такой вызов в метод `ClassifySingleImage()` в виде следующей строки кода в методе `Main`:

    [!code-csharp[CallClassifySingleImage](./snippets/image-classification/csharp/Program.cs#CallClassifySingleImage)]

1. Запустите консольное приложение (CTRL+F5). Результаты выполнения должны выглядеть примерно так, как указано ниже.  Кроме того, могут выводиться предупреждения или сообщения об обработке, но для удобства здесь мы убрали их.

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

Поздравляем! Вы успешно создали модель машинного обучения для классификации изображений, применив передачу обучения в модель `TensorFlow` в ML.NET.

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF).

В этом руководстве вы узнали, как:
> [!div class="checklist"]
>
> * Определение проблемы
> * внедрить предварительно обученную модель TensorFlow в конвейер ML.NET;
> * обучить и оценить модель ML.NET;
> * классифицировать тестовое изображение.

Ознакомьтесь с примерами Машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример классификации изображений.
> [!div class="nextstepaction"]
> [Репозиторий GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/)
