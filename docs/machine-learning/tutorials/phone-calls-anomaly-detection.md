---
title: Учебник. Обнаружение аномалий в телефонных вызовах
description: Узнайте, как создать приложение для обнаружения аномалий в данных временных рядов. В этом руководстве в Visual Studio 2019 с помощью C# создается консольное приложение .NET Core.
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7edb84ae53f1da7903cf4b3f77d215206ffbf1ef
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259828"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a><span data-ttu-id="fec70-104">Учебник. Обнаружение аномалий во временном ряду с помощью ML.NET</span><span class="sxs-lookup"><span data-stu-id="fec70-104">Tutorial: Detect anomalies in time series with ML.NET</span></span>

<span data-ttu-id="fec70-105">Узнайте, как создать приложение для обнаружения аномалий в данных временных рядов.</span><span class="sxs-lookup"><span data-stu-id="fec70-105">Learn how to build an anomaly detection application for time series data.</span></span> <span data-ttu-id="fec70-106">В этом руководстве в Visual Studio 2019 с помощью C# создается консольное приложение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fec70-106">This tutorial creates a .NET Core console application using C# in Visual Studio 2019.</span></span>

<span data-ttu-id="fec70-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="fec70-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fec70-108">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="fec70-108">Load the data</span></span>
> * <span data-ttu-id="fec70-109">Определение периода для временных рядов</span><span class="sxs-lookup"><span data-stu-id="fec70-109">Detect period for a time series</span></span>
> * <span data-ttu-id="fec70-110">Обнаружение аномалий для периодических временных рядов</span><span class="sxs-lookup"><span data-stu-id="fec70-110">Detect anomaly for a periodical time series</span></span>

<span data-ttu-id="fec70-111">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="fec70-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fec70-112">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="fec70-112">Prerequisites</span></span>

* <span data-ttu-id="fec70-113">[Visual Studio 2019 версии 16.7.8 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="fec70-113">[Visual Studio 2019 version 16.7.8 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="fec70-114">[Набор данных phone-calls.csv](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv).</span><span class="sxs-lookup"><span data-stu-id="fec70-114">[The phone-calls.csv dataset](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="fec70-115">Создание консольного приложение</span><span class="sxs-lookup"><span data-stu-id="fec70-115">Create a console application</span></span>

1. <span data-ttu-id="fec70-116">Создайте **консольное приложение C# .NET Core** с именем PhoneCallsAnomalyDetection.</span><span class="sxs-lookup"><span data-stu-id="fec70-116">Create a **C# .NET Core Console Application** called "PhoneCallsAnomalyDetection".</span></span>

2. <span data-ttu-id="fec70-117">Создайте каталог с именем *Data* в проекте, чтобы сохранять файлы набора данных.</span><span class="sxs-lookup"><span data-stu-id="fec70-117">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="fec70-118">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="fec70-118">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="fec70-119">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fec70-119">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="fec70-120">Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор", выполните поиск по запросу **Microsoft.ML** и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="fec70-120">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="fec70-121">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="fec70-121">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="fec70-122">Повторите эти действия для пакета **Microsoft.ML.TimeSeries**.</span><span class="sxs-lookup"><span data-stu-id="fec70-122">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="fec70-123">Добавьте следующие операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="fec70-123">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="fec70-124">Скачивание данных</span><span class="sxs-lookup"><span data-stu-id="fec70-124">Download your data</span></span>

1. <span data-ttu-id="fec70-125">Скачайте набор данных и сохраните его в ранее созданную папку *Data*:</span><span class="sxs-lookup"><span data-stu-id="fec70-125">Download the dataset and save it to the *Data* folder you previously created:</span></span>

    <span data-ttu-id="fec70-126">Щелкните файл [*phone-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) правой кнопкой мыши и выберите команду "Сохранить ссылку (объект) как...".</span><span class="sxs-lookup"><span data-stu-id="fec70-126">Right click on [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="fec70-127">Файл \*.csv нужно сохранить в папке *Data*. Если вы сохранили файл \*.csv в другом месте, переместите его в папку *Data*.</span><span class="sxs-lookup"><span data-stu-id="fec70-127">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="fec70-128">В обозревателе решений щелкните правой кнопкой мыши файл \*.csv и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="fec70-128">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="fec70-129">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="fec70-129">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="fec70-130">В следующей таблице представлены данные из вашего файла \*.csv:</span><span class="sxs-lookup"><span data-stu-id="fec70-130">The following table is a data preview from your \*.csv file:</span></span>

| <span data-ttu-id="fec70-131">TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="fec70-131">timestamp</span></span>  | <span data-ttu-id="fec70-132">value</span><span class="sxs-lookup"><span data-stu-id="fec70-132">value</span></span> |
|--------|--------------|
| <span data-ttu-id="fec70-133">2018/9/3</span><span class="sxs-lookup"><span data-stu-id="fec70-133">2018/9/3</span></span>  | <span data-ttu-id="fec70-134">36.69670857</span><span class="sxs-lookup"><span data-stu-id="fec70-134">36.69670857</span></span>  |
| <span data-ttu-id="fec70-135">2018/9/4</span><span class="sxs-lookup"><span data-stu-id="fec70-135">2018/9/4</span></span>  | <span data-ttu-id="fec70-136">35.74160571</span><span class="sxs-lookup"><span data-stu-id="fec70-136">35.74160571</span></span>  |
| <span data-ttu-id="fec70-137">.....</span><span class="sxs-lookup"><span data-stu-id="fec70-137">.....</span></span>  | <span data-ttu-id="fec70-138">.....</span><span class="sxs-lookup"><span data-stu-id="fec70-138">.....</span></span>  |
| <span data-ttu-id="fec70-139">2018/10/3</span><span class="sxs-lookup"><span data-stu-id="fec70-139">2018/10/3</span></span>  | <span data-ttu-id="fec70-140">34.49893429</span><span class="sxs-lookup"><span data-stu-id="fec70-140">34.49893429</span></span>  |
| <span data-ttu-id="fec70-141">...</span><span class="sxs-lookup"><span data-stu-id="fec70-141">...</span></span>    | <span data-ttu-id="fec70-142">....</span><span class="sxs-lookup"><span data-stu-id="fec70-142">....</span></span>   |

<span data-ttu-id="fec70-143">Этот файл представляет временные ряды.</span><span class="sxs-lookup"><span data-stu-id="fec70-143">This file represents a time-series.</span></span> <span data-ttu-id="fec70-144">Каждая строка в файле является точкой данных.</span><span class="sxs-lookup"><span data-stu-id="fec70-144">Each row in the file is a data point.</span></span> <span data-ttu-id="fec70-145">Каждая точка данных имеет два атрибута, а именно `timestamp` и `value`, которые представляют количество телефонных вызовов в каждый день.</span><span class="sxs-lookup"><span data-stu-id="fec70-145">Each data point has two attributes, namely, `timestamp` and `value`, to represent the number of phone calls at each day.</span></span> <span data-ttu-id="fec70-146">Число телефонных вызов преобразуется в нечувствительность.</span><span class="sxs-lookup"><span data-stu-id="fec70-146">The number of phone calls is transformed to de-sensitivity.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="fec70-147">Создание классов и определение путей</span><span class="sxs-lookup"><span data-stu-id="fec70-147">Create classes and define paths</span></span>

<span data-ttu-id="fec70-148">Далее определите структуру данных для класса ввода данных и прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="fec70-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="fec70-149">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="fec70-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="fec70-150">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите команду **Добавить > Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="fec70-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="fec70-151">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *PhoneCallsData.cs*.</span><span class="sxs-lookup"><span data-stu-id="fec70-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *PhoneCallsData.cs*.</span></span> <span data-ttu-id="fec70-152">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="fec70-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="fec70-153">Файл *PhoneCallsData.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="fec70-153">The *PhoneCallsData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="fec70-154">Добавьте следующую инструкцию `using` в начало файла *PhoneCallsData.cs*:</span><span class="sxs-lookup"><span data-stu-id="fec70-154">Add the following `using` statement to the top of *PhoneCallsData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="fec70-155">Удалите из файла *PhoneCallsData.cs* существующее определение класса и добавьте следующий код с двумя классами `PhoneCallsData` и `PhoneCallsPrediction`:</span><span class="sxs-lookup"><span data-stu-id="fec70-155">Remove the existing class definition and add the following code, which has two classes `PhoneCallsData` and `PhoneCallsPrediction`, to the *PhoneCallsData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="fec70-156">`PhoneCallsData` — это класс входных данных.</span><span class="sxs-lookup"><span data-stu-id="fec70-156">`PhoneCallsData` specifies an input data class.</span></span> <span data-ttu-id="fec70-157">Атрибут [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) определяет столбцы в наборе данных, которые следует загрузить (по индексам).</span><span class="sxs-lookup"><span data-stu-id="fec70-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="fec70-158">Он имеет два атрибута `timestamp` и `value`, соответствующие тем же атрибутам в файле данных.</span><span class="sxs-lookup"><span data-stu-id="fec70-158">It has two attributes `timestamp` and `value` that correspond to the same attributes in the data file.</span></span>

    <span data-ttu-id="fec70-159">`PhoneCallsPrediction` указывает класс данных прогноза.</span><span class="sxs-lookup"><span data-stu-id="fec70-159">`PhoneCallsPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="fec70-160">Для детектора SR-CNN прогноз зависит от заданного [режима обнаружения](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode).</span><span class="sxs-lookup"><span data-stu-id="fec70-160">For SR-CNN detector, the prediction depends on the [detect mode](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) specified.</span></span> <span data-ttu-id="fec70-161">В этом примере мы выбираем режим `AnomalyAndMargin`.</span><span class="sxs-lookup"><span data-stu-id="fec70-161">In this sample, we select the `AnomalyAndMargin` mode.</span></span> <span data-ttu-id="fec70-162">Выходные данные содержат семь столбцов.</span><span class="sxs-lookup"><span data-stu-id="fec70-162">The output contains seven columns.</span></span> <span data-ttu-id="fec70-163">В большинстве случаев `IsAnomaly`, `ExpectedValue`, `UpperBoundary` и `LowerBoundary` являются достаточно информативными.</span><span class="sxs-lookup"><span data-stu-id="fec70-163">In most cases, `IsAnomaly`, `ExpectedValue`, `UpperBoundary`, and `LowerBoundary` are informative enough.</span></span> <span data-ttu-id="fec70-164">Они показывают, что точка является аномалией, ожидаемым значением точки и нижней/верхней границей точки.</span><span class="sxs-lookup"><span data-stu-id="fec70-164">They tell you if a point is an anomaly, the expected value of the point and the lower / upper boundary region of the point.</span></span>

5. <span data-ttu-id="fec70-165">Добавьте следующий код в строке справа выше метода `Main` для указания пути к файлу данных:</span><span class="sxs-lookup"><span data-stu-id="fec70-165">Add the following code to the line right above the `Main` method to specify the path to your data file:</span></span>

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="fec70-166">Инициализация переменных в методе Main</span><span class="sxs-lookup"><span data-stu-id="fec70-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="fec70-167">Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="fec70-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="fec70-168">[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="fec70-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="fec70-169">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fec70-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="fec70-170">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="fec70-170">Load the data</span></span>

<span data-ttu-id="fec70-171">Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="fec70-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="fec70-172">`IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые).</span><span class="sxs-lookup"><span data-stu-id="fec70-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="fec70-173">Данные можно загружать в объект `IDataView` из текстового файла или других источников (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="fec70-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="fec70-174">Добавьте в следующую строку метода `Main` приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="fec70-174">Add the following code as the next line of the `Main` method:</span></span>

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="fec70-175">Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл.</span><span class="sxs-lookup"><span data-stu-id="fec70-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="fec70-176">Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="fec70-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="fec70-177">Обнаружение аномалий во временных рядах</span><span class="sxs-lookup"><span data-stu-id="fec70-177">Time series anomaly detection</span></span>

<span data-ttu-id="fec70-178">Обнаружение аномалий во временных рядах — это процесс обнаружения выбросов временных рядов данных, точек заданных входных временных рядов, где поведение отличается от ожидаемого или является "странным".</span><span class="sxs-lookup"><span data-stu-id="fec70-178">Time series anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span> <span data-ttu-id="fec70-179">Эти аномалии, как правило, свидетельствуют о некоторых событиях, представляющих интерес в проблемной области: кибератака на учетные записи пользователей, отключение питания, ускорение RPS на сервере, утечка памяти и т. д.</span><span class="sxs-lookup"><span data-stu-id="fec70-179">These anomalies are typically indicative of some events of interest in the problem domain: a cyber-attack on user accounts, power outage, bursting RPS on a server, memory leak, etc.</span></span>

<span data-ttu-id="fec70-180">Чтобы найти аномалию по временным рядам, сначала необходимо определить период ряда.</span><span class="sxs-lookup"><span data-stu-id="fec70-180">To find anomaly on time series, you should first determine the period of the series.</span></span> <span data-ttu-id="fec70-181">Затем временные ряды можно разбить на несколько компонентов, таких как `Y = T + S + R`, где `Y` является исходным рядом, `T` является компонентом тренда, `S` является сезонным компонентом, а `R` — остаточной частью ряда.</span><span class="sxs-lookup"><span data-stu-id="fec70-181">Then, the time series can be decomposed into several components as `Y = T + S + R`, where `Y` is the original series, `T` is the trend component, `S` is the seasonal component, and `R` is the residual component of the series.</span></span> <span data-ttu-id="fec70-182">Этот шаг называется [декомпозицией](https://en.wikipedia.org/wiki/Decomposition_of_time_series).</span><span class="sxs-lookup"><span data-stu-id="fec70-182">This step is called [decomposition](https://en.wikipedia.org/wiki/Decomposition_of_time_series).</span></span> <span data-ttu-id="fec70-183">Наконец, для поиска аномалий выполняется обнаружение по остаточной части.</span><span class="sxs-lookup"><span data-stu-id="fec70-183">Finally, detection is performed on the residual component to find the anomalies.</span></span> <span data-ttu-id="fec70-184">В ML.NET алгоритм SR-CNN — это расширенный и новый алгоритм, основанный на анализе спектрального остатка (SR) и сверточной нейросети (CNN) для обнаружения аномалий во временных рядах.</span><span class="sxs-lookup"><span data-stu-id="fec70-184">In ML.NET, The SR-CNN algorithm is an advanced and novel algorithm that is based on Spectral Residual (SR) and Convolutional Neural Network(CNN) to detect anomaly on time-series.</span></span> <span data-ttu-id="fec70-185">Дополнительные сведения об этом алгоритме см. в разделе [Служба обнаружения аномалий временных рядов в Майкрософт](https://arxiv.org/pdf/1906.03821.pdf).</span><span class="sxs-lookup"><span data-stu-id="fec70-185">For more information on this algorithm, see [Time-Series Anomaly Detection Service at Microsoft](https://arxiv.org/pdf/1906.03821.pdf).</span></span>

<span data-ttu-id="fec70-186">В этом руководстве вы увидите, что эти процедуры можно выполнить с помощью двух функций.</span><span class="sxs-lookup"><span data-stu-id="fec70-186">In this tutorial, you will see that these procedures can be completed using two functions.</span></span>

## <a name="detect-period"></a><span data-ttu-id="fec70-187">Определение периода</span><span class="sxs-lookup"><span data-stu-id="fec70-187">Detect Period</span></span>

<span data-ttu-id="fec70-188">На первом шаге необходимо вызвать функцию `DetectSeasonality` для определения периода ряда.</span><span class="sxs-lookup"><span data-stu-id="fec70-188">In the first step, we invoke the `DetectSeasonality` function to determine the period of the series.</span></span>

### <a name="create-the-detectperiod-method"></a><span data-ttu-id="fec70-189">Создание метода DetectPeriod</span><span class="sxs-lookup"><span data-stu-id="fec70-189">Create the DetectPeriod method</span></span>

1. <span data-ttu-id="fec70-190">Создайте метод `DetectPeriod` сразу под методом `Main`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="fec70-190">Create the `DetectPeriod` method, just below the `Main` method, using the following code:</span></span>

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. <span data-ttu-id="fec70-191">Для обнаружения периода используйте функцию <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A>.</span><span class="sxs-lookup"><span data-stu-id="fec70-191">Use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> function to detect period.</span></span> <span data-ttu-id="fec70-192">Добавьте его в метод `DetectPeriod` со следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="fec70-192">Add it to the `DetectPeriod` method with the following code:</span></span>

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. <span data-ttu-id="fec70-193">Отобразите значение периода, добавив в метод `DetectPeriod` следующую строку кода:</span><span class="sxs-lookup"><span data-stu-id="fec70-193">Display the period value by adding the following as the next line of code in the `DetectPeriod` method:</span></span>

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. <span data-ttu-id="fec70-194">Добавьте вызов метода `DetectPeriod` в метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="fec70-194">Add the following call to the `DetectPeriod` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a><span data-ttu-id="fec70-195">Результаты обнаружения периода</span><span class="sxs-lookup"><span data-stu-id="fec70-195">Period detection results</span></span>

<span data-ttu-id="fec70-196">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="fec70-196">Run the application.</span></span> <span data-ttu-id="fec70-197">Результаты выполнения должны выглядеть примерно так, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="fec70-197">Your results should be similar to the following.</span></span>

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a><span data-ttu-id="fec70-198">Обнаружение аномалий</span><span class="sxs-lookup"><span data-stu-id="fec70-198">Detect Anomaly</span></span>

<span data-ttu-id="fec70-199">На этом шаге необходимо использовать метод <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> для поиска аномалий.</span><span class="sxs-lookup"><span data-stu-id="fec70-199">In this step, you use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> method to find anomalies.</span></span>

### <a name="create-the-detectanomaly-method"></a><span data-ttu-id="fec70-200">Создание метода DetectAnomaly</span><span class="sxs-lookup"><span data-stu-id="fec70-200">Create the DetectAnomaly method</span></span>

1. <span data-ttu-id="fec70-201">Создайте метод `DetectAnomaly` сразу под методом `DetectPeriod`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="fec70-201">Create the `DetectAnomaly` method, just below the `DetectPeriod` method, using the following code:</span></span>

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. <span data-ttu-id="fec70-202">Настройте <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> в методе `DetectAnomaly` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="fec70-202">Set up <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> in the `DetectAnomaly` method with the following code:</span></span>

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. <span data-ttu-id="fec70-203">Выявите аномалии с помощью алгоритма SR-CNN путем добавления следующей строки кода в метод `DetectAnomaly`:</span><span class="sxs-lookup"><span data-stu-id="fec70-203">Detect anomaly by SR-CNN algorithm by adding the following line of code in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. <span data-ttu-id="fec70-204">Преобразуйте выходные данные в строго типизированный `IEnumerable` для более удобного отображения с помощью метода [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A), используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="fec70-204">Convert the output data view into a strongly typed `IEnumerable` for easier display using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. <span data-ttu-id="fec70-205">Создайте отображаемый заголовок, добавив в следующую строку метода `DetectAnomaly` приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="fec70-205">Create a display header with the following code as the next line in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    <span data-ttu-id="fec70-206">В результатах обнаружения точек изменений будут отображены следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="fec70-206">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="fec70-207">`Index` — индекс каждой точки.</span><span class="sxs-lookup"><span data-stu-id="fec70-207">`Index` is the index of each point.</span></span>
    * <span data-ttu-id="fec70-208">`Anomaly` — указание того, обнаруживается ли каждая точка как аномалия.</span><span class="sxs-lookup"><span data-stu-id="fec70-208">`Anomaly` is the indicator of whether each point is detected as anomaly.</span></span>
    * <span data-ttu-id="fec70-209">`ExpectedValue` — оценочное значение каждой точки.</span><span class="sxs-lookup"><span data-stu-id="fec70-209">`ExpectedValue` is the estimated value of each point.</span></span>
    * <span data-ttu-id="fec70-210">`LowerBoundary` — наименьшее значение, в котором каждая точка может быть не аномалией.</span><span class="sxs-lookup"><span data-stu-id="fec70-210">`LowerBoundary` is the lowest value each point can be to be not anomaly.</span></span>
    * <span data-ttu-id="fec70-211">`UpperBoundary` — наибольшее значение, в котором каждая точка может быть не аномалией.</span><span class="sxs-lookup"><span data-stu-id="fec70-211">`UpperBoundary` is the highest value each point can be to be not anomaly.</span></span>

6. <span data-ttu-id="fec70-212">Используйте следующий код, чтобы выполнить итерацию по `predictions` `IEnumerable` и отобразить результаты:</span><span class="sxs-lookup"><span data-stu-id="fec70-212">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. <span data-ttu-id="fec70-213">Добавьте вызов метода `DetectAnomaly` в метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="fec70-213">Add the following call to the `DetectAnomaly` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a><span data-ttu-id="fec70-214">Результаты обнаружения аномалий</span><span class="sxs-lookup"><span data-stu-id="fec70-214">Anomaly detection results</span></span>

<span data-ttu-id="fec70-215">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="fec70-215">Run the application.</span></span> <span data-ttu-id="fec70-216">Результаты выполнения должны выглядеть примерно так, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="fec70-216">Your results should be similar to the following.</span></span> <span data-ttu-id="fec70-217">Во время обработки отображаются сообщения.</span><span class="sxs-lookup"><span data-stu-id="fec70-217">During processing, messages are displayed.</span></span> <span data-ttu-id="fec70-218">Вы можете видеть предупреждения или обработанные сообщения.</span><span class="sxs-lookup"><span data-stu-id="fec70-218">You may see warnings or processing messages.</span></span> <span data-ttu-id="fec70-219">Для удобства некоторые сообщения удалены из следующих результатов.</span><span class="sxs-lookup"><span data-stu-id="fec70-219">Some messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="fec70-220">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="fec70-220">Congratulations!</span></span> <span data-ttu-id="fec70-221">Вы успешно создали модели машинного обучения для обнаружения периодов и аномалий в периодических рядах.</span><span class="sxs-lookup"><span data-stu-id="fec70-221">You've now successfully built machine learning models for detecting period and anomaly on a periodical series.</span></span>

<span data-ttu-id="fec70-222">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="fec70-222">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

<span data-ttu-id="fec70-223">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="fec70-223">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="fec70-224">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="fec70-224">Load the data</span></span>
> * <span data-ttu-id="fec70-225">Определение периода в данных временных рядов</span><span class="sxs-lookup"><span data-stu-id="fec70-225">Detect period on the time series data</span></span>
> * <span data-ttu-id="fec70-226">Обнаружение аномалий в данных временных рядов</span><span class="sxs-lookup"><span data-stu-id="fec70-226">Detect anomaly on the time series data</span></span>

## <a name="next-steps"></a><span data-ttu-id="fec70-227">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="fec70-227">Next steps</span></span>

<span data-ttu-id="fec70-228">Ознакомьтесь с примерами машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример с обнаружением аномалий для энергопотребления.</span><span class="sxs-lookup"><span data-stu-id="fec70-228">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="fec70-229">Репозиторий GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="fec70-229">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
