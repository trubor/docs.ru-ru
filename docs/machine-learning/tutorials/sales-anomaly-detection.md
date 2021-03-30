---
title: Учебник. Обнаружение аномалий в данных о продажах товаров
description: Узнайте, как создать приложение для обнаружения аномалий в данных о продажах товаров. В этом руководстве в Visual Studio 2019 с помощью C# создается консольное приложение .NET Core.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 2262f2c5e8e389a13c583073bb2002fcd5da91ee
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874658"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Учебник. Обнаружение аномалий в данных о продажах товаров с помощью ML.NET

Узнайте, как создать приложение для обнаружения аномалий в данных о продажах товаров. В этом руководстве в Visual Studio с помощью C# создается консольное приложение .NET Core.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> * Загрузка данных
> * Создание преобразования для обнаружения пиковых аномалий
> * Обнаружение пиковых аномалий с помощью преобразования
> * Создание преобразования для обнаружения аномалий в точке изменений
> * Обнаружение аномалий в точке изменений с помощью преобразования

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/ProductSalesAnomalyDetection).

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2017 версии 15.6 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".

* [Набор данных product-sales.csv](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Формат данных в `product-sales.csv` основан на наборе данных Shampoo Sales Over a Three Year Period, изначально опубликованном DataMarket и предоставленном Time Series Data Library (TSDL), за авторством Роба Нундмана (Rob Hyndman).
> Набор данных Shampoo Sales Over a Three Year Period предоставляется по стандартной открытой лицензии DataMarket.

## <a name="create-a-console-application"></a>Создание консольного приложения

1. Создайте **консольное приложение .NET Core** с именем ProductSalesAnomalyDetection.

2. Создайте каталог с именем *Data* в проекте, чтобы сохранять файлы набора данных.

3. Установите **пакет NuGet для Microsoft.ML**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор", выполните поиск по запросу **Microsoft.ML** и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов. Повторите эти действия для пакета **Microsoft.ML.TimeSeries**.

4. Добавьте следующие операторы `using` в начало файла *Program.cs*:

    [!code-csharp[AddUsings](./snippets/sales-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Скачивание данных

1. Скачайте набор данных и сохраните его в ранее созданную папку *Data*:

   * Щелкните файл [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) правой кнопкой мыши и выберите команду "Сохранить ссылку (объект) как...".

     Файл \*.csv нужно сохранить в папке *Data*. Если вы сохранили файл \*.csv в другом месте, переместите его в папку *Data*.

2. В обозревателе решений щелкните правой кнопкой мыши файл \*.csv и выберите пункт **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

В следующей таблице представлены данные из вашего файла \*.csv:

|Месяц  |ProductSales |
|-------|-------------|
|1-Jan  |    271      |
|2-Jan  |    150,9    |
|.....  |    .....    |
|1-Feb  |    199,3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Создание классов и определение путей

Далее определите структуру данных для класса ввода данных и прогнозирования.

Добавьте в проект новый класс:

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите команду **Добавить > Новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *ProductSalesData.cs*. Теперь нажмите кнопку **Добавить**.

   Файл *ProductSalesData.cs* откроется в редакторе кода.

3. Добавьте следующую инструкцию `using` в начало файла *ProductSalesData.cs*:

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Удалите из файла *ProductSalesData.cs* существующее определение класса и добавьте следующий код с двумя классами `ProductSalesData` и `ProductSalesPrediction`:

    [!code-csharp[DeclareTypes](./snippets/sales-anomaly-detection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    `ProductSalesData` — это класс входных данных. Атрибут [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) определяет столбцы в наборе данных, которые следует загрузить (по индексам).

    `ProductSalesPrediction` указывает класс данных прогноза. Для обнаружения аномалий прогноз состоит из предупреждения, указывающего на наличие аномалии, необработанной оценки и p-значения. Чем ближе p-значение к 0, тем больше вероятность возникновения аномалий.

5. Создайте два глобальных поля для хранения пути к файлу недавно скачанного набора данных и пути к файлу сохраненной модели:

    * `_dataPath` содержит путь к набору данных, используемому для обучения модели;
    * `_docsize` содержит количество записей в файле набора данных. Вы будете использовать `_docSize` для вычисления `pvalueHistoryLength`.

6. Добавьте следующий код в строку прямо перед методом `Main`, чтобы указать эти пути:

    [!code-csharp[Declare global variables](./snippets/sales-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Инициализация переменных в методе Main

1. Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную `mlContext`:

    [!code-csharp[CreateMLContext](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    [Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

### <a name="load-the-data"></a>Загрузка данных

Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView). `IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые). Данные можно загружать в объект `IDataView` из текстового файла или других источников (например, из базы данных SQL или файлов журнала).

1. Добавьте в следующую строку метода `Main()` приведенный ниже код.

    [!code-csharp[LoadData](./snippets/sales-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл. Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.

## <a name="time-series-anomaly-detection"></a>Обнаружение аномалий во временных рядах

Функция обнаружения аномалий регистрирует неожиданные или необычные события или особенности поведения. Кроме того, она подсказывает, где нужно искать проблему, и помогает ответить на вопрос "Является ли это странным?".

![Пример обнаружения аномалий с помощью ответа на вопрос"Является ли это странным?"](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

Обнаружение аномалий — это процесс обнаружения выбросов временных рядов данных, точек заданных входных временных рядов, где поведение отличается от ожидаемого или является "странным".

Обнаружение аномалий может быть полезным во многих ситуациях. Например:

При наличии автомобиля вы, возможно, захотите узнать, правильны ли показания датчика масла или возникла утечка.
Если вы отслеживаете энергопотребление, то захотите узнать, имеет ли место простой.

Существуют два вида аномалий временных рядов, которые можно обнаружить.

* **Пиковые значения** указывают временные всплески аномального поведения в системе.

* **Точки изменений** указывают начало устойчивых изменений с течением времени в системе.

В ML.NET алгоритмы обнаружения пиковых значений IID или обнаружения точек изменений IID подходят для [независимых и одинаково распределенных наборов данных](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).

В отличие от моделей в других руководствах, преобразования обнаружения аномалий временных рядов работают непосредственно с входными данными. Методу `IEstimator.Fit()` не требуются обучающие данные для создания преобразования. Для него нужна схема данных, которая предоставляется представлением данных, созданным из пустого списка `ProductSalesData`.

Вы проанализируете одни и те же данные о продажах продукта для обнаружения пиковых значений и точек изменений. Процесс создания и обучения модели одинаков для обоих видов обнаружения; основное различие заключается в используемом алгоритме обнаружения.

## <a name="spike-detection"></a>Обнаружение пиковых значений

Целью обнаружения пиковых значений является выявление внезапных, но при этом временных всплесков, которые значительно отличаются от большинства значений данных временных рядов. Важно своевременно обнаружить эти подозрительные редкие элементы, события или наблюдения, чтобы свести их влияние к минимуму. Для обнаружения разнообразных аномалий, таких как простои, кибератаки и вирусное веб-содержимое, можно использовать описанный ниже подход. На следующем рисунке представлен пример пиковых значений в наборе данных временных рядов.

![Снимок экрана с данными обнаружения двух пиков.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a>Добавьте метод CreateEmptyDataView()

Добавьте следующий метод к `Program.cs`:

[!code-csharp[CreateEmptyDataView](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEmptyDataView)]

`CreateEmptyDataView()` создает пустой объект представления данных с правильной схемой для использования в качестве входных данных для метода `IEstimator.Fit()`.

### <a name="create-the-detectspike-method"></a>Создание метода DetectSpike()

Метод `DetectSpike()`:

* Создает преобразование из средства оценки.
* Обнаруживает пиковые значения на основе исторических данных о продажах.
* Отображает результаты.

1. Создайте метод `DetectSpike()` сразу после метода `Main()`, вставив в него следующий код:

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Используйте [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator), чтобы обучить модель для обнаружения пиковых значений. Добавьте его в метод `DetectSpike()` со следующим кодом:

    [!code-csharp[AddSpikeTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddSpikeTrainer)]

1. Создайте преобразование для обнаружения пиковых значений, добавив в метод `DetectSpike()` следующую строку кода:

    [!code-csharp[TrainModel1](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel1)]

1. Добавьте указанный ниже код для преобразования данных `productSales` в следующую строку метода `DetectSpike()`:

    [!code-csharp[TransformData1](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData1)]

    Предыдущий код использует метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A), чтобы сделать прогнозы для нескольких входных строк набора данных.

1. Преобразуйте `transformedData` в строго типизированный `IEnumerable` для более удобного отображения с помощью метода [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A), используя следующий код:

    [!code-csharp[CreateEnumerable1](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable1)]

1. Создайте отображаемую строку заголовка с помощью следующего кода <xref:System.Console.WriteLine?displayProperty=nameWithType>:

    [!code-csharp[DisplayHeader1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader1)]

    В результатах обнаружения пиковых значений будут отображены следующие сведения:

    * `Alert` указывает на оповещение о пиковом значении для заданной точки данных.
    * `Score` является значением `ProductSales` для заданной точки данных в наборе данных.
    * `P-Value` — "P" означает вероятность. Чем ближе p-значение к 0, тем больше вероятность того, что точка данных аномальна.

1. Используйте следующий код, чтобы выполнить итерацию по `predictions` `IEnumerable` и отобразить результаты:

    [!code-csharp[DisplayResults1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults1)]

1. Добавьте вызов метода `DetectSpike()` в метод `Main()`.

    [!code-csharp[CallDetectSpike](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a>Результаты обнаружения пиковых значений

Результаты выполнения должны выглядеть примерно так, как показано ниже. Во время обработки отображаются сообщения. Вы можете видеть предупреждения или обработанные сообщения. Для удобства часть сообщений удалена из следующих результатов.

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a>Обнаружение точек изменений

`Change points` — это постоянные изменения в распределении значений по потоку событий временных рядов, такие как изменения уровня и тенденции. Эти постоянные изменения длятся гораздо дольше, чем `spikes`, и могут указывать на катастрофические события. `Change points` обычно не видны невооруженным глазом, но могут быть обнаружены в данных с помощью таких подходов, которые описаны в следующем методе.  На следующем рисунке представлен пример обнаружения точек изменений.

![Снимок экрана с данными обнаружения точки изменения.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a>Создание метода DetectChangepoint()

Метод `DetectChangepoint()` выполняет следующие задачи:

* Создает преобразование из средства оценки.
* Обнаруживает точки изменений на основе исторических данных о продажах.
* Отображает результаты.

1. Создайте метод `DetectChangepoint()` сразу после метода `Main()`, вставив в него следующий код:

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Создайте [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) в методе `DetectChangepoint()`, используя следующий код:

    [!code-csharp[AddChangepointTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddChangepointTrainer)]

1. Как и ранее, создайте преобразование из средства оценки, добавив следующую строку кода в метод `DetectChangePoint()`:

    [!code-csharp[TrainModel2](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel2)]

1. Используйте метод `Transform()` для преобразования данных, добавив в `DetectChangePoint()` следующий код:

    [!code-csharp[TransformData2](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData2)]

1. Как и ранее, преобразуйте `transformedData` в строго типизированный `IEnumerable` для более удобного отображения с помощью метода `CreateEnumerable()`, используя следующий код:

    [!code-csharp[CreateEnumerable2](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable2)]

1. Создайте отображаемый заголовок, добавив в следующую строку метода `DetectChangePoint()` приведенный ниже код.

    [!code-csharp[DisplayHeader2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader2)]

    В результатах обнаружения точек изменений будут отображены следующие сведения:

    * `Alert` указывает на оповещение о точке изменений для заданной точки данных.
    * `Score` является значением `ProductSales` для заданной точки данных в наборе данных.
    * `P-Value` — "P" означает вероятность. Чем ближе p-значение к 0, тем больше вероятность того, что точка данных аномальна.
    * `Martingale value` — используется для определения того, насколько "странной" является точка данных, на основе последовательности P-значений.

1. Используйте следующий код, чтобы выполнить итерацию по `predictions` `IEnumerable` и отобразить результаты:

    [!code-csharp[DisplayResults2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults2)]

1. Добавьте вызов метода `DetectChangepoint()` в метод `Main()`.

    [!code-csharp[CallDetectChangepoint](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a>Результаты обнаружения точек изменений

Результаты выполнения должны выглядеть примерно так, как показано ниже. Во время обработки отображаются сообщения. Вы можете видеть предупреждения или обработанные сообщения. Для удобства некоторые сообщения удалены из следующих результатов.

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

Поздравляем! Вы успешно создали модели машинного обучения для обнаружения аномалий в виде пиковых значений и точек изменений в данных о продажах.

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/ProductSalesAnomalyDetection).

В этом руководстве вы узнали, как:
> [!div class="checklist"]
>
> * Загрузка данных
> * Обучение модели для обнаружения пиковых аномалий
> * Обнаружение пиковых аномалий с помощью обученной модели
> * Обучение модели для обнаружения аномалий в точке изменений
> * Обнаружение аномалий в точке изменений с помощью обученной модели

## <a name="next-steps"></a>Следующие шаги

Ознакомьтесь с примерами машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример с обнаружением аномалий для сезонных данных.
> [!div class="nextstepaction"]
> [Репозиторий GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/AnomalyDetection_PhoneCalls)
