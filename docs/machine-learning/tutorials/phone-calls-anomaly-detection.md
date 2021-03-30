---
title: Учебник. Обнаружение аномалий в телефонных вызовах
description: Узнайте, как создать приложение для обнаружения аномалий в данных временных рядов. В этом руководстве в Visual Studio 2019 с помощью C# создается консольное приложение .NET Core.
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 52ce0a60c91ef7a82f7ef1a0709701302b9e11d9
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874775"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a>Учебник. Обнаружение аномалий во временном ряду с помощью ML.NET

Узнайте, как создать приложение для обнаружения аномалий в данных временных рядов. В этом руководстве в Visual Studio 2019 с помощью C# создается консольное приложение .NET Core.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> * Загрузка данных
> * Определение периода для временных рядов
> * Обнаружение аномалий для периодических временных рядов

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/PhoneCallsAnomalyDetection).

## <a name="prerequisites"></a>Предварительные требования

* [Visual Studio 2019 версии 16.7.8 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".

* [Набор данных phone-calls.csv](https://github.com/dotnet/machinelearning-samples/blob/main/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv).

## <a name="create-a-console-application"></a>Создание консольного приложение

1. Создайте **консольное приложение C# .NET Core** с именем PhoneCallsAnomalyDetection.

2. Создайте каталог с именем *Data* в проекте, чтобы сохранять файлы набора данных.

3. Установите **пакет NuGet для Microsoft.ML**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор", выполните поиск по запросу **Microsoft.ML** и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов. Повторите эти действия для пакета **Microsoft.ML.TimeSeries**.

4. Добавьте следующие операторы `using` в начало файла *Program.cs*:

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Скачивание данных

1. Скачайте набор данных и сохраните его в ранее созданную папку *Data*:

    Щелкните файл [*phone-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) правой кнопкой мыши и выберите команду "Сохранить ссылку (объект) как...".

     Файл \*.csv нужно сохранить в папке *Data*. Если вы сохранили файл \*.csv в другом месте, переместите его в папку *Data*.

2. В обозревателе решений щелкните правой кнопкой мыши файл \*.csv и выберите пункт **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

В следующей таблице представлены данные из вашего файла \*.csv:

| TIMESTAMP  | value |
|--------|--------------|
| 2018/9/3  | 36.69670857  |
| 2018/9/4  | 35.74160571  |
| .....  | .....  |
| 2018/10/3  | 34.49893429  |
| ...    | ....   |

Этот файл представляет временные ряды. Каждая строка в файле является точкой данных. Каждая точка данных имеет два атрибута, а именно `timestamp` и `value`, которые представляют количество телефонных вызовов в каждый день. Число телефонных вызов преобразуется в нечувствительность.

### <a name="create-classes-and-define-paths"></a>Создание классов и определение путей

Далее определите структуру данных для класса ввода данных и прогнозирования.

Добавьте в проект новый класс:

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите команду **Добавить > Новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *PhoneCallsData.cs*. Теперь нажмите кнопку **Добавить**.

   Файл *PhoneCallsData.cs* откроется в редакторе кода.

3. Добавьте следующую инструкцию `using` в начало файла *PhoneCallsData.cs*:

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Удалите из файла *PhoneCallsData.cs* существующее определение класса и добавьте следующий код с двумя классами `PhoneCallsData` и `PhoneCallsPrediction`:

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    `PhoneCallsData` — это класс входных данных. Атрибут [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) определяет столбцы в наборе данных, которые следует загрузить (по индексам). Он имеет два атрибута `timestamp` и `value`, соответствующие тем же атрибутам в файле данных.

    `PhoneCallsPrediction` указывает класс данных прогноза. Для детектора SR-CNN прогноз зависит от заданного [режима обнаружения](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode). В этом примере мы выбираем режим `AnomalyAndMargin`. Выходные данные содержат семь столбцов. В большинстве случаев `IsAnomaly`, `ExpectedValue`, `UpperBoundary` и `LowerBoundary` являются достаточно информативными. Они показывают, что точка является аномалией, ожидаемым значением точки и нижней/верхней границей точки.

5. Добавьте следующий код в строке справа выше метода `Main` для указания пути к файлу данных:

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Инициализация переменных в методе Main

1. Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную `mlContext`:

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    [Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

### <a name="load-the-data"></a>Загрузка данных

Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView). `IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые). Данные можно загружать в объект `IDataView` из текстового файла или других источников (например, из базы данных SQL или файлов журнала).

1. Добавьте в следующую строку метода `Main` приведенный ниже код.

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл. Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.

## <a name="time-series-anomaly-detection"></a>Обнаружение аномалий во временных рядах

Обнаружение аномалий во временных рядах — это процесс обнаружения выбросов временных рядов данных, точек заданных входных временных рядов, где поведение отличается от ожидаемого или является "странным". Эти аномалии, как правило, свидетельствуют о некоторых событиях, представляющих интерес в проблемной области: кибератака на учетные записи пользователей, отключение питания, ускорение RPS на сервере, утечка памяти и т. д.

Чтобы найти аномалию по временным рядам, сначала необходимо определить период ряда. Затем временные ряды можно разбить на несколько компонентов, таких как `Y = T + S + R`, где `Y` является исходным рядом, `T` является компонентом тренда, `S` является сезонным компонентом, а `R` — остаточной частью ряда. Этот шаг называется [декомпозицией](https://en.wikipedia.org/wiki/Decomposition_of_time_series). Наконец, для поиска аномалий выполняется обнаружение по остаточной части. В ML.NET алгоритм SR-CNN — это расширенный и новый алгоритм, основанный на анализе спектрального остатка (SR) и сверточной нейросети (CNN) для обнаружения аномалий во временных рядах. Дополнительные сведения об этом алгоритме см. в разделе [Служба обнаружения аномалий временных рядов в Майкрософт](https://arxiv.org/pdf/1906.03821.pdf).

В этом руководстве вы увидите, что эти процедуры можно выполнить с помощью двух функций.

## <a name="detect-period"></a>Определение периода

На первом шаге необходимо вызвать функцию `DetectSeasonality` для определения периода ряда.

### <a name="create-the-detectperiod-method"></a>Создание метода DetectPeriod

1. Создайте метод `DetectPeriod` сразу под методом `Main`, используя следующий код:

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. Для обнаружения периода используйте функцию <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A>. Добавьте его в метод `DetectPeriod` со следующим кодом:

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. Отобразите значение периода, добавив в метод `DetectPeriod` следующую строку кода:

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. Добавьте вызов метода `DetectPeriod` в метод `Main`.

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a>Результаты обнаружения периода

Запустите приложение. Результаты выполнения должны выглядеть примерно так, как показано ниже.

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a>Обнаружение аномалий

На этом шаге необходимо использовать метод <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> для поиска аномалий.

### <a name="create-the-detectanomaly-method"></a>Создание метода DetectAnomaly

1. Создайте метод `DetectAnomaly` сразу под методом `DetectPeriod`, используя следующий код:

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. Настройте <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> в методе `DetectAnomaly` с помощью следующего кода:

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. Выявите аномалии с помощью алгоритма SR-CNN путем добавления следующей строки кода в метод `DetectAnomaly`:

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. Преобразуйте выходные данные в строго типизированный `IEnumerable` для более удобного отображения с помощью метода [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A), используя следующий код:

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. Создайте отображаемый заголовок, добавив в следующую строку метода `DetectAnomaly` приведенный ниже код.

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    В результатах обнаружения точек изменений будут отображены следующие сведения:

    * `Index` — индекс каждой точки.
    * `Anomaly` — указание того, обнаруживается ли каждая точка как аномалия.
    * `ExpectedValue` — оценочное значение каждой точки.
    * `LowerBoundary` — наименьшее значение, в котором каждая точка может быть не аномалией.
    * `UpperBoundary` — наибольшее значение, в котором каждая точка может быть не аномалией.

6. Используйте следующий код, чтобы выполнить итерацию по `predictions` `IEnumerable` и отобразить результаты:

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. Добавьте вызов метода `DetectAnomaly` в метод `Main`.

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a>Результаты обнаружения аномалий

Запустите приложение. Результаты выполнения должны выглядеть примерно так, как показано ниже. Во время обработки отображаются сообщения. Вы можете видеть предупреждения или обработанные сообщения. Для удобства некоторые сообщения удалены из следующих результатов.

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detected anomaly
...
```

Поздравляем! Вы успешно создали модели машинного обучения для обнаружения периодов и аномалий в периодических рядах.

Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/PhoneCallsAnomalyDetection).

В этом руководстве вы узнали, как:
> [!div class="checklist"]
>
> * Загрузка данных
> * Определение периода в данных временных рядов
> * Обнаружение аномалий в данных временных рядов

## <a name="next-steps"></a>Следующие шаги

Ознакомьтесь с примерами машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример с обнаружением аномалий для энергопотребления.
> [!div class="nextstepaction"]
> [Репозиторий GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
