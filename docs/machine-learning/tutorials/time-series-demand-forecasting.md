---
title: Учебник. Прогнозирование спроса на прокат велосипедов (временные ряды)
description: В этом руководстве показано, как прогнозировать спрос для службы проката велосипедов с помощью одномерного анализа временных рядов и библиотеки ML.NET.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: aea264036ab4766696699980f464cca3d8229499
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875594"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Учебник. Прогнозирование спроса для службы проката велосипедов с помощью анализа временных рядов и ML.NET

Сведения о том, как прогнозировать спрос для службы проката велосипедов с помощью одномерного анализа временных рядов по данным, которые хранятся в базе данных SQL Server, с применением ML.NET.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> * Определение проблемы
> * загружать данные из базы данных;
> * создавать модели прогнозирования;
> * выполнять оценку модели прогнозирования;
> * сохранять модели прогнозирования;
> * применять модели прогнозирования.

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".

## <a name="time-series-forecasting-sample-overview"></a>Общие сведения о примере прогнозирования по временным рядам

Этот пример содержит **консольное приложение .NET Core на языке C#** , которое прогнозирует спрос для службы проката велосипедов с помощью алгоритма одномерного анализа временных рядов, называемого анализом сингулярного спектра. Код для этого примера можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand) на сайте GitHub.

## <a name="understand-the-problem"></a>Определение проблемы

Для эффективной работы крайне важную роль играет правильное управление запасами. Слишком большой запас товаров означает, что значительная его часть хранится на полках и не приносит дохода. Слишком малый запас приводит к потере продаж, а клиенты уходят к конкурентам. Это означает, что постоянно актуален вопрос об оптимальном уровне складских запасов. Анализ временных рядов помогает ответить на этот вопрос путем изучения исторических данных, выявления закономерностей и прогнозирования на их основе значений на некоторый период вперед.

Для анализа данных в этом руководстве используется метод одномерного анализа временных рядов. В ходе одномерного анализа временных рядов просматриваются значения одного численного параметра, измеряемого через определенные интервалы на протяжении некоторого периода времени, например ежемесячные данные о продажах.

В этом руководстве применяется алгоритм [Анализ сингулярного спектра (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). SSA разбивает временной ряд на набор основных компонентов. Эти компоненты можно интерпретировать как части одного сигнала: тенденции, шумы, сезонные колебания и многие другие факторы. Полученные компоненты реконструируются и применяются для прогнозирования значений на будущие периоды.

## <a name="create-console-application"></a>Создание консольного приложения

1. Создайте **консольное приложение .NET Core на C#** с именем BikeDemandForecasting.
1. Установите пакет NuGet **Microsoft.ML**.

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.
    1. Выберите nuget.org в качестве источника пакета, щелкните вкладку **Обзор** и найдите **Microsoft.ML**.
    1. Установите флажок **Включить предварительные версии**.
    1. Нажмите кнопку **Установить**.
    1. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**. Затем нажмите кнопку **Принимаю** в диалоговом окне "Принятие условий лицензионного соглашения", если вы согласны с условиями лицензионного соглашения для выбранных пакетов.
    1. Повторите эти действия для **System.Data.SqlClient** и **Microsoft.ML.TimeSeries**.

### <a name="prepare-and-understand-the-data"></a>Подготовка и анализ данных

1. Создайте каталог с именем *Data*.
1. Скачайте [файл базы данных *DailyDemand.mdf*](https://github.com/dotnet/machinelearning-samples/raw/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) и сохраните его в каталоге *Data*.

> [!NOTE]
> Данные, используемые в этом руководстве, получены из [набора данных UCI по аренде велосипедов](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset). Хади Фанаит (Hadi Fanaee-T) и Жуан Гама (Joao Gama), 'Event labeling combining ensemble detectors and background knowledge' (Маркировка событий по сочетанию множества датчиков и предварительных знаний), Progress in Artificial Intelligence (2013): стр. 1–15, Springer Berlin Heidelberg, [ссылка на веб-страницу](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Исходный набор данных содержит несколько столбцов, соответствующих сезонности и погоде. Для сокращения объема, поскольку для алгоритма в этом руководстве нужны значения только из одного числового столбца, мы уплотнили исходный набор данных, сохранив только следующие столбцы:

- **dteday**: дата наблюдения.
- **year**: закодированный год наблюдения (0 = 2011, 1 = 2012).
- **cnt**: общее число арендованных велосипедов за этот день.

Исходный набор данных сопоставляется с таблицей базы данных в базе данных SQL Server, которая имеет следующую схему.

```sql
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Ниже приводится пример этих данных.

| RentalDate | Год | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Создание классов входных и выходных данных

1. Откройте файл *Program.cs* и замените существующие инструкции `using` следующим кодом.

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. Создайте класс `ModelInput`. Добавьте приведенный ниже код в класс `Program`.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    Класс `ModelInput` содержит следующие столбцы:

    - **RentalDate**: дата наблюдения.
    - **Year**: закодированный год наблюдения (0 = 2011, 1 = 2012).
    - **TotalRentals**: общее число арендованных велосипедов за этот день.

1. Создайте класс `ModelOutput` под только что созданным классом `ModelInput`.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    Класс `ModelOutput` содержит следующие столбцы:

    - **ForecastedRentals**: прогнозируемые значения для прогнозируемого периода.
    - **LowerBoundRentals**: минимальные прогнозируемые значения для прогнозируемого периода.
    - **UpperBoundRentals**: максимальные прогнозируемые значения для прогнозируемого периода.

### <a name="define-paths-and-initialize-variables"></a>Определение путей и инициализация переменных

1. В методе `Main` определите переменные, которые будут хранить расположение данных, строку подключения и расположение для обученной модели.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Инициализируйте переменную `mlContext` новым экземпляром [`MLContext`](xref:Microsoft.ML.MLContext), добавив следующую строку в метод `Main`.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    Класс [`MLContext`](xref:Microsoft.ML.MLContext) будет стартовой точкой для любых операций ML.NET. При инициализации класса mlContext создается новая среда ML.NET, которая может использоваться всеми объектами в рабочем процессе создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

## <a name="load-the-data"></a>Загрузка данных

1. Создайте `DatabaseLoader`, который загружает записи с типом `ModelInput`.

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Определите запрос для загрузки данных из базы данных.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    Алгоритмы ML.NET предполагают, что данные имеют тип [`Single`](xref:System.Single). Следовательно, полученные из базы данных числовые значения, тип которых отличается от [`Real`](xref:System.Data.SqlDbType) (значение одиночной точности с плавающей запятой), необходимо преобразовать в [`Real`](xref:System.Data.SqlDbType).

    Столбцы `Year` и `TotalRental` в базе данных имеют целочисленные типы. С помощью встроенной функции `CAST` они приводятся к типу `Real`.

1. Создайте `DatabaseSource` для подключения к базе данных и выполните запрос.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Загрузите данные в `IDataView`.

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Набор данных содержит данные за два года. Для обучения используются только данные за первый год, а данные за второй год откладываются для сравнения фактических значений с прогнозом, созданным моделью. Отфильтруйте данные с помощью преобразования [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A).

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    Для отбора данных за первый год извлекаются те строки, у которых значение в столбце `Year` меньше 1. Для этого параметру `upperBound` присваивается значение 1. И наоборот, для данных за второй год извлекаются те строки, у которых это значение равно 1. Для этого параметру `lowerBound` присваивается значение 1.

## <a name="define-time-series-analysis-pipeline"></a>Определение конвейера анализа временных рядов

1. Определите конвейер, который использует [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) для прогнозирования значений в наборе данных временных рядов.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    `forecastingPipeline` принимает 365 точек данных за первый год и разделяет набор данных временных рядов на выборки за 30-дневные (помесячные) интервалы, как указано в параметре `seriesLength`. Каждая из этих выборок анализируется по еженедельным (7-дневным) периодам. При определении прогнозируемого значения для предстоящих периодов используются значения за предыдущие семь дней. Модель настроена на прогнозирование семи предстоящих периодов, как определено параметром `horizon`. Прогноз является лишь предположением, то есть не всегда будет на 100 % точным. Поэтому нам лучше получить диапазон значений, который определяется верхней и нижней границами для наилучшего и наихудшего сценариев. В нашем примере для определения нижней и верхней границ устанавливается уровень достоверности 95 %. Вы можете увеличить или уменьшить этот уровень достоверности. Чем выше значение уровня достоверности, тем шире диапазон между верхней и нижней границами.

1. Используйте метод [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit%2A), чтобы обучить модель и подогнать данные по ранее определенным `forecastingPipeline`.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Оценка модели

Оцените точность модели, создав прогноз данных на следующий год и сравнив их с фактическими значениями.

1. Добавьте новый служебный метод `Evaluate` под методом `Main`.

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. В методе `Evaluate` примените метод [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) с обученной моделью, чтобы спрогнозировать данные на следующий год.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Чтобы получить фактические значения из примера данных, используйте метод [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A).

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Чтобы получить прогнозируемые значения, используйте метод [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A).

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Вычислите разницу между реальными и прогнозируемыми значениями, которая обычно называется ошибкой.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Для оценки точности модели вычислите среднюю абсолютную погрешность и среднеквадратическую погрешность.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Для оценки точности используются следующие метрики.

    - **Средняя абсолютная погрешность**. Оценивает, насколько близки прогнозы к фактическому значению. Принимает значения в диапазоне от 0 до бесконечности. Чем ближе это значение к 0, тем лучше качество модели.
    - **Среднеквадратическая погрешность**. Суммирует ошибки в модели. Принимает значения в диапазоне от 0 до бесконечности. Чем ближе это значение к 0, тем лучше качество модели.

1. Выведите значения метрик на консоль.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Используйте метод `Evaluate` в методе `Main`.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Сохранение модели

Если вы довольны поведением модели, сохраните ее для использования в других приложениях.

1. В методе `Main` создайте [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602). [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) — это удобный метод для создания единичных прогнозов.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Сохраните модель в файл с именем `MLModel.zip`, которое задано ранее определенной переменной `modelPath`. Выполните метод [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint%2A), чтобы сохранить модель.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Применение модели для прогнозирования спроса

1. Добавьте новый служебный метод `Forecast` под методом `Evaluate`.

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. В методе `Forecast` вызовите метод [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict%2A), чтобы получить прогноз по прокату на следующие семь дней.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Сравните фактические и прогнозируемые значения по семи периодам.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. В цикле извлекайте выходные данные прогноза и выводите их на консоль.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Запуск приложения

1. Из метода `Main` вызовите метод `Forecast`.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Запустите приложение. Должен отобразиться результат, аналогичный приведенному ниже. Для краткости выходные данные были сжаты.

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

Сверка фактических и прогнозируемых значений показывает следующие связи:

![Сравнение фактических и прогнозируемых значений](./media/time-series-demand-forecasting/forecast.png)

Хотя прогнозируемые значения и не дают точного совпадения с реальными данными о прокате, они предоставляют достаточно узкий диапазон значений, который позволяет оптимизировать использование ресурсов организации.

Поздравляем! Вы успешно создали модель машинного обучения для прогнозирования спроса на прокат велосипедов.

Исходный код для этого руководства можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/Forecasting_BikeSharingDemand).

## <a name="next-steps"></a>Следующие шаги

- [Задачи машинного обучения в ML.NET](../resources/tasks.md)
- [Повышение уровня точности модели](../resources/improve-machine-learning-model-ml-net.md)
