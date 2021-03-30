---
title: Учебник. Классификация заявок на поддержку — мультиклассовая классификация
description: Узнайте, как использовать ML.NET для сценариев многоклассовой классификации, чтобы назначать задачи GitHub определенным областям.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: dfc007f72fcd67f31139bc7fcbad93dde39d88fb
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875633"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a>Учебник. Классификация заявок на поддержку с использованием мультиклассовой классификации с помощью ML.NET

В этом практическом руководстве демонстрируется создание классификатора задач GitHub для обучения модели, классифицирующей и прогнозирующей метки области для задач на GitHub, с помощью ML.NET в консольном приложении .NET Core на языке C# в Visual Studio.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> * подготавливать данные;
> * Преобразование данных
> * Обучение модели
> * Оценка модели
> * Прогнозирование с помощью обученной модели
> * Развертывание и прогнозирование с помощью загруженной модели

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/GitHubIssueClassification).

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".
* [Файл задач GitHub с разделением знаками табуляции (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Файл с тестовыми данными задач GitHub с разделением знаками табуляции (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Создание консольного приложения

### <a name="create-a-project"></a>Создание проекта

1. Откройте Visual Studio 2017. Выберите **Файл** > **Создать** > **Проект** в меню. В диалоговом окне **Новый проект** выберите узел **Visual C#** , а затем — узел **.NET Core**. Выберите шаблон проекта **Консольное приложение (.NET Core)** . В текстовое поле **Имя** введите GitHubIssueClassification, а затем нажмите кнопку **ОК**.

2. Создайте каталог с именем *Data* в папке проекта, чтобы сохранить в нем файлы с наборами данных:

    В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новая папка**. Введите имя папки Data и нажмите клавишу "ВВОД".

3. Создайте каталог с именем *Models* в папке проекта, чтобы сохранить модель:

    В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новая папка**. Введите "Models" и нажмите ВВОД.

4. Установите **пакет NuGet для Microsoft.ML**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор", выполните поиск по запросу **Microsoft.ML** и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.

### <a name="prepare-your-data"></a>подготавливать данные;

1. Скачайте наборы данных [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) и [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/main/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) и сохраните их в ранее созданную папку *Data*. Первый из этих наборов данных обучает модель машинного обучения, а второй позволяет оценить точность полученной модели.

2. В обозревателе решений щелкните правой кнопкой мыши каждый из файлов \*.tsv и выберите **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

### <a name="create-classes-and-define-paths"></a>Создание классов и определение путей

Добавьте следующие новые операторы `using` в начало файла *Program.cs*:

[!code-csharp[AddUsings](./snippets/github-issue-classification/csharp/Program.cs#AddUsings)]

Создайте три глобальных поля для хранения путей к недавно скачанным файлам и глобальные переменные для `MLContext`, `DataView` и `PredictionEngine`:

* `_trainDataPath` содержит путь к набору данных, используемому для обучения модели;
* `_testDataPath` содержит путь к набору данных, используемому для оценки модели;
* `_modelPath` содержит путь, по которому сохраняется обученная модель.
* `_mlContext` соответствует классу <xref:Microsoft.ML.MLContext>, предоставляющему контекст для обработки;
* `_trainingDataView` представляет собой интерфейс <xref:Microsoft.ML.IDataView>, используемый для обработки обучающего набора данных;
* `_predEngine` соответствует классу <xref:Microsoft.ML.PredictionEngine%602>, используемому для одиночных прогнозов;

Добавьте следующий код в строку непосредственно над методом `Main`, чтобы указать эти пути и другие переменные:

[!code-csharp[DeclareGlobalVariables](./snippets/github-issue-classification/csharp/Program.cs#DeclareGlobalVariables)]

Создайте несколько классов для входных данных и прогнозов. Добавьте в проект новый класс:

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.

1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и в поле **Имя** укажите *GitHubIssueData.cs*. Теперь нажмите кнопку **Добавить**.

    Файл *GitHubIssueData.cs* откроется в редакторе кода. Добавьте следующий оператор `using` в начало файла *GitHubIssueData.cs*:

[!code-csharp[AddUsings](./snippets/github-issue-classification/csharp/GitHubIssueData.cs#AddUsings)]

Удалите из файла *GitHubIssueData.cs* существующее определение класса и добавьте следующий код с двумя классами `GitHubIssue` и `IssuePrediction`:

[!code-csharp[DeclareGlobalVariables](./snippets/github-issue-classification/csharp/GitHubIssueData.cs#DeclareTypes)]

`label` — это столбец для прогнозирования. Определены `Features`входные данные, которые вы предоставляете модели для прогнозирования метки.

Используйте атрибут [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute), чтобы указать индексы исходных столбцов в файле набора данных.

`GitHubIssue` является классом входного набора данных и имеет следующие поля <xref:System.String>:

* Первый столбец `ID` (идентификатор задачи GitHub).
* Второй столбец `Area` (прогноз для обучения).
* Третий столбец `Title` (название задачи GitHub) является первым `feature`, используемым для прогнозирования `Area`
* Четвертый столбец `Description` является вторым `feature`, используемым для прогнозирования `Area`

Класс `IssuePrediction` используется для прогнозирования после обучения модели. Он имеет один параметр типа `string` (`Area`) и атрибут `PredictedLabel` `ColumnName`.  `PredictedLabel` используется для прогнозирования и оценки. Для оценки применяются входные обучающие данные, прогнозируемые значения и модель.

Все операции ML.NET запускаются в [классе MLContext](xref:Microsoft.ML.MLContext). Инициализация `mlContext` создает новую среду ML.NET, которую могут совместно использовать объекты рабочего процесса создания модели. По сути, он аналогичен классу `DBContext` в `Entity Framework`.

### <a name="initialize-variables-in-main"></a>Инициализация переменных в методе Main

Инициализируйте глобальную переменную `_mlContext` в новом экземпляре `MLContext` со случайным начальным значением (`seed: 0`) для получения воспроизводимых и детерминированных результатов при множестве циклов обучения.  Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом:

[!code-csharp[CreateMLContext](./snippets/github-issue-classification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Загрузка данных

ML.NET использует [класс IDataView](xref:Microsoft.ML.IDataView) как гибкий и эффективный способ описания числовых или текстовых табличных данных. `IDataView` может загружать данные из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).

Чтобы инициализировать и загрузить глобальную переменную `_trainingDataView` для ее использования в конвейере, добавьте после инициализации `mlContext` следующий код:

[!code-csharp[LoadTrainData](./snippets/github-issue-classification/csharp/Program.cs#LoadTrainData)]

Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл. Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.

Добавьте в следующую строку метода `Main` приведенный ниже код:

[!code-csharp[CallProcessData](./snippets/github-issue-classification/csharp/Program.cs#CallProcessData)]

Метод `ProcessData` выполняет следующие задачи:

* извлечение и преобразование данных;
* возвращение конвейера обработки.

Создайте метод `ProcessData` сразу после метода `Main`, вставив в него следующий код:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Извлечение компонентов и преобразование данных

Мы хотим прогнозировать метки области GitHub для `GitHubIssue`, поэтому стоит использовать метод [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) для преобразования столбца `Area` в числовой тип ключа столбца `Label` (формат, который принимают алгоритмы классификации) и добавить его как новый столбец набора данных:

[!code-csharp[MapValueToKey](./snippets/github-issue-classification/csharp/Program.cs#MapValueToKey)]

Затем вызовите `mlContext.Transforms.Text.FeaturizeText`, который преобразует столбцы текста (`Title` и `Description`) в числовой вектор для вызываемых `TitleFeaturized` и `DescriptionFeaturized` соответственно. Добавьте присвоение признаков для обоих столбцов в конвейере, используя следующий код:

[!code-csharp[FeaturizeText](./snippets/github-issue-classification/csharp/Program.cs#FeaturizeText)]

Последний шаг на этапе подготовки данных заключается в объединении всех столбцов признаков в столбце **Features** с помощью метода преобразования [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A). По умолчанию алгоритм обучения обрабатывает только признаки, представленные в столбце **Features**. Добавьте это преобразование в конвейер, используя следующий код:

[!code-csharp[Concatenate](./snippets/github-issue-classification/csharp/Program.cs#Concatenate)]

 Затем добавьте <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> для кэширования DataView, которое может ускорить обучение при многократных итерациях по данным, используя следующий код:

[!code-csharp[AppendCache](./snippets/github-issue-classification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> Используйте AppendCacheCheckpoint для небольших и средних наборов данных для ускорения обучения. НЕ используйте AppendCacheCheckpoint (удалите .AppendCacheCheckpoint()) при обработке очень больших наборов данных.

Выполните возврат конвейера в конце метода `ProcessData`.

[!code-csharp[ReturnPipeline](./snippets/github-issue-classification/csharp/Program.cs#ReturnPipeline)]

На этом этапе выполняется предварительная обработка и присвоение признаков. Дополнительные компоненты из ML.NET могут дать более точные результаты для вашей модели.

## <a name="build-and-train-the-model"></a>Сборка и обучение модели

В следующей строке кода в методе `Main` добавьте приведенный ниже вызов метода `BuildAndTrainModel`:

[!code-csharp[CallBuildAndTrainModel](./snippets/github-issue-classification/csharp/Program.cs#CallBuildAndTrainModel)]

Метод `BuildAndTrainModel` выполняет следующие задачи:

* создание класса алгоритма обучения;
* обучение модели;
* прогнозирование области на основе обучающих данных;
* возвращение модели.

Создайте метод `BuildAndTrainModel` сразу после метода `Main`, вставив в него следующий код:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>Сведения о задаче классификации

Классификацией называют задачу машинного обучения, которая использует данные для **определения** категории, типа или класса для некоторого элемента или ряда данных. Часто она имеет следующие виды:

* Двоичная: A или B.
* Многоклассовая: несколько категорий, которые прогнозируются по одной модели.

Для таких проблем используйте обучающий алгоритм многоклассовой классификации, поскольку прогноз категории проблемы может относиться к нескольким категориям (многоклассовая), а не только к двум (двоичная).

Добавьте алгоритм машинного обучения к определениям преобразований данных, добавив следующее в первой строке кода в `BuildAndTrainModel()`:

[!code-csharp[AddTrainer](./snippets/github-issue-classification/csharp/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) — ваш алгоритм обучения классификации по нескольким классам. Он добавляется в `pipeline` и принимает в качестве входных параметров `Title` и `Description` (`Features`) с присвоенными признаками, а также `Label` для обучения по историческим данным.

### <a name="train-the-model"></a>Обучение модели

Обучите модель на основе данных `splitTrainSet` и получите обученную модель, добавив в метод `BuildAndTrainModel()` следующие строки кода:

[!code-csharp[TrainModel](./snippets/github-issue-classification/csharp/Program.cs#TrainModel)]

Метод `Fit()` обучает модель путем преобразования набора данных и применения обучения.

Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий передать один экземпляр данных и осуществить прогнозирование на его основе. Добавьте следующую строку кода в метод `BuildAndTrainModel()`:

[!code-csharp[CreatePredictionEngine1](./snippets/github-issue-classification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Прогнозирование с помощью обученной модели

Добавьте задачу GitHub для тестирования прогноза обученной модели в методе `Predict`, создав экземпляр `GitHubIssue`:

[!code-csharp[CreateTestIssue1](./snippets/github-issue-classification/csharp/Program.cs#CreateTestIssue1)]

Используйте функцию [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A), которая создает прогноз по одной строке данных.

[!code-csharp[Predict](./snippets/github-issue-classification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Использование модели: результаты прогнозирования

Отобразите `GitHubIssue` и соответствующий прогноз метки `Area`, чтобы поделиться результатами и обработать их должным образом.  Создайте отображение для результатов с помощью следующего кода <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[OutputPrediction](./snippets/github-issue-classification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Возврат обученной модели для оценки

Выполните возврат модели в конце метода `BuildAndTrainModel`.

[!code-csharp[ReturnModel](./snippets/github-issue-classification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Оценка модели

Итак, вы завершили создание и обучение модели, и теперь ее можно оценить по другому набору данных, чтобы проверить ее точность и качество прогнозирования. В методе `Evaluate` передается для оценки модель, созданная в `BuildAndTrainModel`. Создайте метод `Evaluate` сразу после метода `BuildAndTrainModel` как показано в следующем коде:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

Метод `Evaluate` выполняет следующие задачи:

* загрузка тестового набора данных;
* создание средства оценки многоклассовой классификации;
* оценка модели и создание метрик;
* отображение метрик.

Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `BuildAndTrainModel`, используя следующий код:

[!code-csharp[CallEvaluate](./snippets/github-issue-classification/csharp/Program.cs#CallEvaluate)]

Как и ранее с набором данных для обучения, загрузите тестовый набор данных, добавив следующий код в метод `Evaluate`:

[!code-csharp[LoadTestDataset](./snippets/github-issue-classification/csharp/Program.cs#LoadTestDataset)]

Метод [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) вычисляет метрики качества для модели на основе указанного набора данных. Он возвращает объект <xref:Microsoft.ML.Data.MulticlassClassificationMetrics>, содержащий общие метрики, вычисляемые средствами оценки многоклассовой классификации.
Чтобы отобразить метрики для оценки качества модели, сначала их необходимо получить.
Используйте метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) для глобальной переменной `_trainedModel` машинного обучения ([ITransformer](xref:Microsoft.ML.ITransformer)) для ввода признаков и возврата прогнозов. В качестве следующей строки в методе `Evaluate` добавьте приведенный ниже код:

[!code-csharp[Evaluate](./snippets/github-issue-classification/csharp/Program.cs#Evaluate)]

Для многоклассовой классификации выполняется оценка следующих метрик:

* Микроточность — на метрику точности в равной степени влияет каждая пара "пример-класс".  Значение микроточности должно быть максимально близко к единице.

* Макроточность — на метрику точности в равной степени влияет каждый класс. Миноритарным классам назначается тот же вес, что и более крупным. Значение макроточности должно быть максимально близко к единице.

* Логарифмические потери — см. термин [логарифмические потери](../resources/glossary.md#log-loss). Значение логарифмических потерь должно быть максимально близко к нулю.

* Минимизация логарифмических потерь — находится в диапазоне [-inf, 1,00], где 1,00 — идеальный прогноз, а 0 — среднее прогнозное значение. Значение минимизации логарифмических потерь должно быть максимально близко к единице.

### <a name="displaying-the-metrics-for-model-validation"></a>Отображение метрик для проверки модели

Используйте следующий код для отображения метрик, передачи результатов и выполнения действий по ним:

[!code-csharp[DisplayMetrics](./snippets/github-issue-classification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Сохранение модели в файл

После того как модель будет готова, сохраните ее в файл, чтобы делать прогнозы позднее или в другом приложении. Добавьте следующий код в метод `Evaluate` .

[!code-csharp[SnippetCallSaveModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetCallSaveModel)]

Создайте метод `SaveModelAsFile` под методом `Evaluate`.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Добавьте приведенный ниже код в метод `SaveModelAsFile`. Этот код использует метод [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save%2A) для сериализации и хранения обученной модели в виде ZIP-файла.

[!code-csharp[SnippetSaveModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Развертывание и прогнозирование с помощью модели

Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `Evaluate`, используя следующий код:

[!code-csharp[CallPredictIssue](./snippets/github-issue-classification/csharp/Program.cs#CallPredictIssue)]

Создайте метод `PredictIssue` сразу после метода `Evaluate` (и непосредственно перед методом `SaveModelAsFile`), вставив в него следующий код:

```csharp
private static void PredictIssue()
{

}
```

Метод `PredictIssue` выполняет следующие задачи:

* загрузка сохраненной модели;
* создание одной задачи с тестовыми данными;
* прогнозирование области на основе тестовых данных;
* объединение тестовых данных и прогнозов для создания отчетов;
* отображение результатов прогнозирования.

Загрузите сохраненную модель в приложение, добавив в метод `PredictIssue` следующий код:

[!code-csharp[SnippetLoadModel](./snippets/github-issue-classification/csharp/Program.cs#SnippetLoadModel)]

Добавьте задачу GitHub для тестирования прогноза обученной модели в методе `Predict`, создав экземпляр `GitHubIssue`:

[!code-csharp[AddTestIssue](./snippets/github-issue-classification/csharp/Program.cs#AddTestIssue)]

Как и ранее, создайте экземпляр `PredictionEngine` следующим кодом:

[!code-csharp[CreatePredictionEngine](./snippets/github-issue-classification/csharp/Program.cs#CreatePredictionEngine)]

Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным. Допустимо использовать в средах прототипов или средах с одним потоком. Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении. См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.

Используйте `PredictionEngine` для прогнозирования метки области GitHub, добавив следующий код в метод прогноза `PredictIssue`:

[!code-csharp[PredictIssue](./snippets/github-issue-classification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Использование загружаемой модели для прогнозирования

Отобразите `Area`, чтобы категоризировать задачу и обработать ее должным образом. Создайте отображение для результатов с помощью следующего кода <xref:System.Console.WriteLine?displayProperty=nameWithType>:

[!code-csharp[DisplayResults](./snippets/github-issue-classification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a>Результаты

Результаты выполнения должны выглядеть примерно так, как показано ниже. В процессе работы конвейер выводит сообщения. Вы можете видеть предупреждения или обработанные сообщения. Для удобства эти сообщения удалены из следующих результатов.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Поздравляем! Вы успешно создали модель машинного обучения для классификации и прогнозирования метки области у задачи GitHub. Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/GitHubIssueClassification).

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как:
> [!div class="checklist"]
>
> * подготавливать данные;
> * Преобразование данных
> * Обучение модели
> * Оценка модели
> * Прогнозирование с помощью обученной модели
> * Развертывание и прогнозирование с помощью загруженной модели

Переходите к следующему руководству:
> [!div class="nextstepaction"]
> [Прогнозирование платы за такси](predict-prices.md)
