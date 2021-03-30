---
title: Учебник. Создание приложения для рекомендации фильмов — матричная факторизация
description: В этом руководстве показано, как построить приложение для рекомендации фильмов с помощью ML.NET в консольном проекте .NET Core. Используется C# и Visual Studio 2019.
author: briacht
ms.date: 06/30/2020
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 9171a6ca073e6296220ebcb874258b6893b2974f
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875360"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a>Учебник. Создание приложения для рекомендации фильмов с использованием матричной факторизации и ML.NET

В этом руководстве показано, как построить приложение для рекомендации фильмов с помощью ML.NET в консольном проекте .NET Core. Используется C# и Visual Studio 2019.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> * выбрать алгоритм машинного обучения;
> * подготовить и загрузить данные;
> * создать и обучить модель;
> * оценить модель;
> * развернуть и использовать модель.

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/MovieRecommendation).

## <a name="machine-learning-workflow"></a>Рабочий процесс машинного обучения

Решение поставленной задачи, как и любой задачи в ML.NET, состоит из следующих этапов:

1. [Загрузка данных](#load-your-data)
2. [Создание и обучение модели](#build-and-train-your-model)
3. [Оценка модели](#evaluate-your-model)
4. [Использование модели](#use-your-model)

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".

## <a name="select-the-appropriate-machine-learning-task"></a>Выбор подходящей задачи машинного обучения

Есть несколько подходов к проблеме предоставления рекомендаций, например в отношении фильмов или связанных продуктов. В данном случае мы будем прогнозировать оценку (от 1 до 5), которую пользователь поставил бы определенному фильму, и рекомендуем этот фильм, если оценка выше установленного порога (чем выше оценка, тем больше вероятность того, что фильм понравится пользователю).

## <a name="create-a-console-application"></a>Создание консольного приложения

### <a name="create-a-project"></a>Создание проекта

1. Откройте Visual Studio 2017. Выберите **Файл** > **Создать** > **Проект** в меню. В диалоговом окне **Новый проект** выберите узел **Visual C#** , а затем — узел **.NET Core**. Выберите шаблон проекта **Консольное приложение (.NET Core)** . В текстовом поле **Имя** введите "MovieRecommender", а затем нажмите кнопку **OK**.

2. Создайте каталог с именем *Data* в папке проекта, чтобы сохранить в нем набор данных:

    В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новая папка**. Введите имя папки Data и нажмите клавишу "ВВОД".

3. Установите пакеты NuGet **Microsoft.ML** и **Microsoft.ML.Recommender**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите в качестве источника пакета "nuget.org", откройте вкладку **Обзор**, найдите **Microsoft.ML**, выберите пакет в списке и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов. Повторите эти действия для пакета **Microsoft.ML.Recommender**.

4. Добавьте следующие операторы `using` в начало файла *Program.cs*:

    [!code-csharp[UsingStatements](./snippets/movie-recommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a>Скачивание данных

1. Скачайте два набора данных и сохраните их в ранее созданную папку *Data*.

   * Щелкните файл [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) правой кнопкой мыши и выберите команду "Сохранить ссылку (объект) как...".
   * Щелкните файл [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) правой кнопкой мыши и выберите команду "Сохранить ссылку (объект) как...".

     Файлы \*.csv нужно сохранить в папке *Data*. Если вы сохранили файлы \*.csv в другом месте, переместите их в папку *Data*.

2. В обозревателе решений щелкните правой кнопкой мыши каждый из файлов \*.csv и выберите **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

   ![GIF пользователя, который выбирает в VS пункт "Копировать более новые".](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a>Загрузка данных

Первый шаг в процессе работы с ML.NET — подготовка и загрузка данных для обучения и тестирования модели.

Данные для оценки рекомендаций разделяются на наборы `Train` и `Test`. Данные `Train` служат для обучения модели. Данные `Test` используются для прогнозирования на основе обученной модели и оценки ее эффективности. Данные `Train` и `Test` обычно делятся в отношении 80/20.

Ниже приведен пример данных из ваших файлов \*.csv.

![Снимок экрана с окном предварительного просмотра набора данных CVS.](./media/movie-recommendation/csv-file-dataset-preview.png)

В файлах \*.csv четыре столбца:

* `userId`
* `movieId`
* `rating`
* `timestamp`

В машинном обучении столбцы, используемые для прогнозирования, называются [признаками](../resources/glossary.md#feature), а столбец с итоговым прогнозом — [меткой](../resources/glossary.md#label).

Нам нужно прогнозировать рейтинг фильмов, поэтому меткой (`Label`) является столбец rating. Остальные столбцы (`userId`, `movieId` и `timestamp`) — это признаки `Features`, используемые для прогнозирования метки `Label`.

| Функции      | Метка         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

Какие признаки (`Features`) будут использоваться для прогнозирования метки (`Label`) — решать вам. Для выбора подходящих признаков (`Features`) можно также использовать такие методы, как [важность комбинаций признаков](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).

В данном случае столбец `timestamp` следует исключить из числа признаков (`Feature`), так как метка времени не влияет на оценку фильма пользователем и поэтому не повышает точность прогноза:

| Функции      | Метка         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

Далее необходимо определить структуру данных для входного класса.

Добавьте в проект новый класс:

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите команду **Добавить > Новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите **Класс** и в поле **Имя** укажите *MovieRatingData.cs*. Теперь нажмите кнопку **Добавить**.

Файл *MovieRatingData.cs* откроется в редакторе кода. Добавьте следующий оператор `using` в начало файла *MovieRatingData.cs*:

```csharp
using Microsoft.ML.Data;
```

Создайте класс `MovieRating`, удалив из файла *MovieRatingData.cs* существующее определение класса и добавив следующий код:

[!code-csharp[MovieRatingClass](./snippets/movie-recommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

`MovieRating` — это класс входных данных. Атрибут [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) определяет столбцы в наборе данных, которые следует загрузить (по индексам). Столбцы `userId` и `movieId` — это признаки `Features` (входные данные модели для прогнозирования метки `Label`), а столбец rating — это прогнозируемая метка `Label` (выходные данные модели).

Создайте еще один класс, `MovieRatingPrediction`, который будет представлять результаты прогнозирования. Для этого добавьте следующий код после класса `MovieRating` в файле *MovieRatingData.cs*:

[!code-csharp[PredictionClass](./snippets/movie-recommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

В файле *Program.cs* замените строку `Console.WriteLine("Hello World!")` в методе `Main()` следующим кодом:

[!code-csharp[MLContext](./snippets/movie-recommendation/csharp/Program.cs#MLContext "Add MLContext")]

[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

После метода `Main()` создайте метод `LoadData()`:

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> Этот метод будет вызывать ошибку, пока вы не добавите оператор return при выполнении дальнейших инструкций.

Инициализируйте переменные, содержащие пути к данным, загрузите данные из файлов \*.csv и получите наборы данных `Train` и `Test` как объекты `IDataView`, добавив следующий код в метод `LoadData()`:

[!code-csharp[LoadData](./snippets/movie-recommendation/csharp/Program.cs#LoadData "Load data from data paths")]

Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView). `IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые). Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).

Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл. Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`. В данном случае вы указываете пути к файлам `Test` и `Train`, а также заголовок текстового файла (чтобы использовались правильные имена столбцов) и разделитель данных в виде запятой (по умолчанию разделителем является символ табуляции).

Добавьте в метод `Main()` следующий код для вызова метода `LoadData()` и получения наборов данных `Train` и `Test`:

[!code-csharp[LoadDataMain](./snippets/movie-recommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a>Создание и обучение модели

Создайте метод `BuildAndTrainModel()` сразу после метода `LoadData()`, вставив в него следующий код:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> Этот метод будет вызывать ошибку, пока вы не добавите оператор return при выполнении дальнейших инструкций.

Определите преобразования данных, добавив в метод `BuildAndTrainModel()` следующий код:

[!code-csharp[DataTransformations](./snippets/movie-recommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

Так как столбцы `userId` и `movieId` содержат индексы пользователей и фильмов, а не реальные значения, необходимо с помощью метода [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) преобразовать столбцы `userId` и `movieId` в столбцы признаков (`Feature`), содержащие числовые ключи (допустимый формат для алгоритмов рекомендаций), а затем добавить их в качестве новых столбцов наборов данных.

| userId | movieId | Метка | userIdEncoded | movieIdEncoded |
| ------------- |:-------------:| -----:|-----:|-----:|
| 1 | 1 | 4 | userKey1 | movieKey1 |
| 1 | 3 | 4 | userKey1 | movieKey2 |
| 1 | 6 | 4 | userKey1 | movieKey3 |

Выберите алгоритм машинного обучения и добавьте его к определениям преобразований данных, добавив в метод `BuildAndTrainModel()` следующие строки кода:

[!code-csharp[AddAlgorithm](./snippets/movie-recommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) — это алгоритм обучения для предоставления рекомендаций.  [Разложение матрицы](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) — стандартный подход к формированию рекомендаций при наличии данных о том, как пользователи оценивали продукты в прошлом, как в нашем случае. Есть и другие алгоритмы рекомендаций, которые используются при наличии других данных (дополнительные сведения см. в. разделе [Другие алгоритмы рекомендаций](#other-recommendation-algorithms) ниже).

В данном случае алгоритм разложения матрицы (`Matrix Factorization`) использует метод, называемый "совместная фильтрация". Он основывается на том допущении, что если мнение двух людей по какому-либо вопросу совпадает, то и по другому вопросу они будут склонны иметь одинаковое мнение.

Например, если два пользователя одинаково оценили определенный фильм, то второму из них с большой вероятностью понравится другой фильм, который посмотрел и высоко оценил первый пользователь.

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| Пользователь 1 | Посмотрел фильм и поставил отметку "Нравится" | Посмотрел фильм и поставил отметку "Нравится" | Посмотрел фильм и поставил отметку "Нравится" |
| Пользователь 2 | Посмотрел фильм и поставил отметку "Нравится" | Посмотрел фильм и поставил отметку "Нравится" | Не смотрел фильм — РЕКОМЕНДОВАТЬ |

Алгоритм разложения матрицы (`Matrix Factorization`) имеет ряд [параметров](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), о которых можно прочитать в разделе [Гиперпараметры алгоритма](#algorithm-hyperparameters) ниже.

Обучите модель на основе данных `Train` и получите обученную модель, добавив в метод `BuildAndTrainModel()` следующие строки кода:

[!code-csharp[FitModel](./snippets/movie-recommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

Метод [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) обучает модель с помощью предоставленных наборов обучающих данных. С технической точки зрения, он выполняет определения средств оценки (`Estimator`), преобразовывая данные и применяя алгоритм обучения, а затем возвращает обученную модель, то есть преобразователь (`Transformer`).

Дополнительные сведения о рабочем процессе обучения модели в ML.NET см. в статье [Что такое ML.NET и принципы работы этой системы](../how-does-mldotnet-work.md#code-workflow).

Добавьте в метод `Main()` следующую строку кода для вызова метода `BuildAndTrainModel()` и получения обученной модели:

[!code-csharp[BuildTrainModelMain](./snippets/movie-recommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a>Оценка модели

После обучения модели оцените ее эффективность с помощью тестовых данных.

Создайте метод `EvaluateModel()` сразу после метода `BuildAndTrainModel()`, вставив в него следующий код:

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

Преобразуйте данные `Test`, добавив в метод `EvaluateModel()` следующий код:

[!code-csharp[Transform](./snippets/movie-recommendation/csharp/Program.cs#Transform "Transform the test data")]

Метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) делает прогнозы для нескольких входных строк тестового набора данных.

Оцените модель, добавив в метод `EvaluateModel()` следующую строку кода:

[!code-csharp[Evaluate](./snippets/movie-recommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

После получения прогноза метод [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) оценивает модель, сравнивая спрогнозированные значения с фактическими метками (`Labels`) в тестовом наборе данных, а затем возвращает метрики эффективности модели.

Чтобы вывести метрики оценки в консоль, добавьте в метод `EvaluateModel()` следующие строки кода:

[!code-csharp[PrintMetrics](./snippets/movie-recommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

Добавьте в метод `Main()` следующую строку кода для вызова метода `EvaluateModel()`:

[!code-csharp[EvaluateModelMain](./snippets/movie-recommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

Теперь выходные данные должны выглядеть так:

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

В этих выходных данных 20 итераций. В каждой итерации мера погрешности уменьшается, приближаясь к 0.

`root of mean squared error` (RMS или RMSE) используется для измерения разницы между значениями, спрогнозированными моделью, и фактическими значениями в тестовом наборе данных. С технической точки зрения она вычисляется как квадратный корень из среднего значения квадратов погрешностей. Чем ниже это отклонение, тем лучше модель.

`R Squared` указывает, насколько хорошо данные соответствуют модели. Значение находится в диапазоне от 0 до 1. Значение 0 означает, что данные случайные или по другим причинам не могут соответствовать модели. Значение 1 означает, что модель идеально соответствует этим данным. Значение `R Squared` должно быть максимально близко к 1.

Построение успешных моделей — итеративный процесс. Изначально эта модель имеет низкое качество, так как в руководстве используются небольшие наборы данных для быстрого обучения. Если вам требуется модель более высокого качества, можно попытаться улучшить ее, использовав более крупные наборы данных для обучения или выбрав другие алгоритмы обучения с разными гиперпараметрами для каждого алгоритма. См. подробнее об [улучшении модели](#improve-your-model) в разделе ниже.

## <a name="use-your-model"></a>Использование модели

Теперь обученную модель можно использовать для прогнозирования на основе новых данных.

Создайте метод `UseModelForSinglePrediction()` сразу после метода `EvaluateModel()`, вставив в него следующий код:

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Для прогнозирования оценки используйте класс `PredictionEngine`. Добавьте в метод `UseModelForSinglePrediction()` следующий код:

[!code-csharp[PredictionEngine](./snippets/movie-recommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным. Допустимо использовать в средах прототипов или средах с одним потоком. Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении. См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.

Создайте экземпляр `MovieRating` с именем `testInput` и передайте его в PredictionEngine, добавив следующие строки кода в метод `UseModelForSinglePrediction()`:

[!code-csharp[MakeSinglePrediction](./snippets/movie-recommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

Функция [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) создает прогноз по одному столбцу данных.

Затем по значению `Score` (спрогнозированная оценка) можно определить, следует ли рекомендовать фильм с movieId 10 пользователю 6. Чем больше значение `Score`, тем выше вероятность того, что пользователю понравится определенный фильм. В данном случае допустим, что нужно рекомендовать фильмы с прогнозируемой оценкой более 3,5.

Чтобы вывести результаты, добавьте в метод `UseModelForSinglePrediction()` следующие строки кода:

[!code-csharp[PrintResults](./snippets/movie-recommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

Добавьте в метод `Main()` следующую строку кода для вызова метода `UseModelForSinglePrediction()`:

[!code-csharp[UseModelMain](./snippets/movie-recommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

Выходные данные этого метода должны выглядеть так:

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a>Сохранение модели

Чтобы модель можно было использовать для прогнозирования в приложениях для конечных пользователей, ее нужно сохранить.

Создайте метод `SaveModel()` сразу после метода `UseModelForSinglePrediction()`, вставив в него следующий код:

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Сохраните обученную модель, добавив в метод `SaveModel()` следующую строку кода:

[!code-csharp[SaveModel](./snippets/movie-recommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

Этот метод сохраняет обученную модель в ZIP-файле (в папке Data), который затем можно использовать в других приложениях .NET.

Добавьте в метод `Main()` следующую строку кода для вызова метода `SaveModel()`:

[!code-csharp[SaveModelMain](./snippets/movie-recommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a>Использование сохраненной модели

После сохранения обученной модели ее можно использовать в различных средах. Дополнительные сведения об эксплуатации модели обучения обученной машины в приложениях см. в статье [Сохранение и загрузка обученных моделей](../how-to-guides/save-load-machine-learning-models-ml-net.md).

## <a name="results"></a>Результаты

Выполнив описанные выше действия, запустите консольное приложение (CTRL+F5). Результаты выполнения одного прогноза должны выглядеть примерно так, как показано ниже. Кроме того, могут выводиться предупреждения или сообщения об обработке, но для удобства здесь мы убрали их.

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

Поздравляем! Вы успешно создали модель машинного обучения для рекомендации фильмов. Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/MovieRecommendation).

## <a name="improve-your-model"></a>Улучшение модели

Повысить эффективность модели для получения более точных прогнозов можно несколькими способами.

### <a name="data"></a>Данные

Чтобы повысить качество модели рекомендаций, можно дополнить обучающие данные для каждого пользователя и фильма.

[Перекрестная проверка](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) — это способ оценки моделей, при котором данные разделяются на части случайным образом, после чего некоторые части используются для обучения, а остальные — для тестирования. В плане качества модели такой метод лучше, чем фиксированное разделение общего набора на обучающие и тестовые данные, которое применялось в этом руководстве.

### <a name="features"></a>Функции

В этом руководстве использовались только три признака (`Features`) из набора данных (`user id`, `movie id` и `rating`).

Хотя для начала этого достаточно, на практике может потребоваться добавить дополнительные атрибуты или признаки `Features` (например, возраст, пол, географическое местоположение и другие). Добавление релевантных признаков (`Features`) может помочь повысить эффективность модели рекомендаций.

Если вы не уверены, какие признаки (`Features`) являются наиболее релевантными для конкретной задачи машинного обучения, можно использовать специальные методы, предоставляемые платформой ML.NET с целью выявления наиболее весомых признаков (`Features`): определение вклада признака и [важность комбинаций признаков](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).

### <a name="algorithm-hyperparameters"></a>Гиперпараметры алгоритма

Алгоритмы, предоставляемые платформой ML.NET по умолчанию, достаточно эффективны, однако их можно еще более улучшить, настроив их [гиперпараметры](../resources/glossary.md#hyperparameter).

В случае с разложением матрицы (`Matrix Factorization`) можно поэкспериментировать с такими гиперпараметрами, как [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) и [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank).

Например, в этом учебнике алгоритм имеет следующие параметры:

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded",
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a>Другие алгоритмы рекомендаций

Алгоритм разложения матрицы с совместной фильтрацией — лишь один из подходов к рекомендации фильмов. Зачастую данные по оценкам могут отсутствовать, то есть доступны только данные по просмотренным пользователями фильмам. В других случаях могут быть доступны дополнительные данные.

| Алгоритм       | Сценарий           | Пример  |
| ------------- |:-------------:| -----:|
| Разложение матрицы одного класса | Следует использовать при наличии только столбцов userId и movieId. Такой тип рекомендаций предназначен для сценария совместных покупок, то есть покупателям будет рекомендоваться набор продуктов исходя из их истории заказов. | [> Попробовать](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| Факторизационные машины с полями | Следует использовать для рекомендаций при наличии дополнительных признаков, помимо userId, productId и rating (таких как описание или цена продукта). Этот алгоритм также использует метод совместной фильтрации. | [> Попробовать](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a>Проблема нового пользователя

Одна из распространенных проблем при использовании совместной фильтрации — это проблема "холодного запуска", когда для нового пользователя еще нет данных, на основе которых можно было бы делать выводы. Для ее решения новому пользователю часто предлагается создать профиль и, например, оценить фильмы, которые он уже видел. Хотя такой подход требует некоторых усилий от пользователя, он позволяет получить начальные данные, на которые можно было бы опираться.

## <a name="resources"></a>Ресурсы

В этом учебнике используются данные из [набора данных MovieLens](http://files.grouplens.org/datasets/movielens/).

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как:

> [!div class="checklist"]
>
> * выбрать алгоритм машинного обучения;
> * подготовить и загрузить данные;
> * создать и обучить модель;
> * оценить модель;
> * развернуть и использовать модель.

Переходите к следующему руководству:
> [!div class="nextstepaction"]
> [Анализ тональности](sentiment-analysis.md)
