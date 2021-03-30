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
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="da89b-104">Учебник. Обнаружение аномалий в данных о продажах товаров с помощью ML.NET</span><span class="sxs-lookup"><span data-stu-id="da89b-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="da89b-105">Узнайте, как создать приложение для обнаружения аномалий в данных о продажах товаров.</span><span class="sxs-lookup"><span data-stu-id="da89b-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="da89b-106">В этом руководстве в Visual Studio с помощью C# создается консольное приложение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="da89b-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="da89b-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="da89b-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="da89b-108">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="da89b-108">Load the data</span></span>
> * <span data-ttu-id="da89b-109">Создание преобразования для обнаружения пиковых аномалий</span><span class="sxs-lookup"><span data-stu-id="da89b-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="da89b-110">Обнаружение пиковых аномалий с помощью преобразования</span><span class="sxs-lookup"><span data-stu-id="da89b-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="da89b-111">Создание преобразования для обнаружения аномалий в точке изменений</span><span class="sxs-lookup"><span data-stu-id="da89b-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="da89b-112">Обнаружение аномалий в точке изменений с помощью преобразования</span><span class="sxs-lookup"><span data-stu-id="da89b-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="da89b-113">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/ProductSalesAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="da89b-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="da89b-114">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="da89b-114">Prerequisites</span></span>

* <span data-ttu-id="da89b-115">[Visual Studio 2017 версии 15.6 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="da89b-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="da89b-116">Набор данных product-sales.csv</span><span class="sxs-lookup"><span data-stu-id="da89b-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="da89b-117">Формат данных в `product-sales.csv` основан на наборе данных Shampoo Sales Over a Three Year Period, изначально опубликованном DataMarket и предоставленном Time Series Data Library (TSDL), за авторством Роба Нундмана (Rob Hyndman).</span><span class="sxs-lookup"><span data-stu-id="da89b-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="da89b-118">Набор данных Shampoo Sales Over a Three Year Period предоставляется по стандартной открытой лицензии DataMarket.</span><span class="sxs-lookup"><span data-stu-id="da89b-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="da89b-119">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="da89b-119">Create a console application</span></span>

1. <span data-ttu-id="da89b-120">Создайте **консольное приложение .NET Core** с именем ProductSalesAnomalyDetection.</span><span class="sxs-lookup"><span data-stu-id="da89b-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="da89b-121">Создайте каталог с именем *Data* в проекте, чтобы сохранять файлы набора данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="da89b-122">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="da89b-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="da89b-123">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="da89b-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="da89b-124">Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор", выполните поиск по запросу **Microsoft.ML** и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="da89b-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="da89b-125">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="da89b-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="da89b-126">Повторите эти действия для пакета **Microsoft.ML.TimeSeries**.</span><span class="sxs-lookup"><span data-stu-id="da89b-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="da89b-127">Добавьте следующие операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="da89b-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/sales-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="da89b-128">Скачивание данных</span><span class="sxs-lookup"><span data-stu-id="da89b-128">Download your data</span></span>

1. <span data-ttu-id="da89b-129">Скачайте набор данных и сохраните его в ранее созданную папку *Data*:</span><span class="sxs-lookup"><span data-stu-id="da89b-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="da89b-130">Щелкните файл [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) правой кнопкой мыши и выберите команду "Сохранить ссылку (объект) как...".</span><span class="sxs-lookup"><span data-stu-id="da89b-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/main/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="da89b-131">Файл \*.csv нужно сохранить в папке *Data*. Если вы сохранили файл \*.csv в другом месте, переместите его в папку *Data*.</span><span class="sxs-lookup"><span data-stu-id="da89b-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="da89b-132">В обозревателе решений щелкните правой кнопкой мыши файл \*.csv и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="da89b-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="da89b-133">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="da89b-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="da89b-134">В следующей таблице представлены данные из вашего файла \*.csv:</span><span class="sxs-lookup"><span data-stu-id="da89b-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="da89b-135">Месяц</span><span class="sxs-lookup"><span data-stu-id="da89b-135">Month</span></span>  |<span data-ttu-id="da89b-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="da89b-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="da89b-137">1-Jan</span><span class="sxs-lookup"><span data-stu-id="da89b-137">1-Jan</span></span>  |    <span data-ttu-id="da89b-138">271</span><span class="sxs-lookup"><span data-stu-id="da89b-138">271</span></span>      |
|<span data-ttu-id="da89b-139">2-Jan</span><span class="sxs-lookup"><span data-stu-id="da89b-139">2-Jan</span></span>  |    <span data-ttu-id="da89b-140">150,9</span><span class="sxs-lookup"><span data-stu-id="da89b-140">150.9</span></span>    |
|<span data-ttu-id="da89b-141">.....</span><span class="sxs-lookup"><span data-stu-id="da89b-141">.....</span></span>  |    <span data-ttu-id="da89b-142">.....</span><span class="sxs-lookup"><span data-stu-id="da89b-142">.....</span></span>    |
|<span data-ttu-id="da89b-143">1-Feb</span><span class="sxs-lookup"><span data-stu-id="da89b-143">1-Feb</span></span>  |    <span data-ttu-id="da89b-144">199,3</span><span class="sxs-lookup"><span data-stu-id="da89b-144">199.3</span></span>    |
|<span data-ttu-id="da89b-145">.....</span><span class="sxs-lookup"><span data-stu-id="da89b-145">.....</span></span>  |    <span data-ttu-id="da89b-146">.....</span><span class="sxs-lookup"><span data-stu-id="da89b-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="da89b-147">Создание классов и определение путей</span><span class="sxs-lookup"><span data-stu-id="da89b-147">Create classes and define paths</span></span>

<span data-ttu-id="da89b-148">Далее определите структуру данных для класса ввода данных и прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="da89b-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="da89b-149">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="da89b-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="da89b-150">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите команду **Добавить > Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="da89b-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="da89b-151">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="da89b-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="da89b-152">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="da89b-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="da89b-153">Файл *ProductSalesData.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="da89b-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="da89b-154">Добавьте следующую инструкцию `using` в начало файла *ProductSalesData.cs*:</span><span class="sxs-lookup"><span data-stu-id="da89b-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="da89b-155">Удалите из файла *ProductSalesData.cs* существующее определение класса и добавьте следующий код с двумя классами `ProductSalesData` и `ProductSalesPrediction`:</span><span class="sxs-lookup"><span data-stu-id="da89b-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/sales-anomaly-detection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="da89b-156">`ProductSalesData` — это класс входных данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="da89b-157">Атрибут [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) определяет столбцы в наборе данных, которые следует загрузить (по индексам).</span><span class="sxs-lookup"><span data-stu-id="da89b-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="da89b-158">`ProductSalesPrediction` указывает класс данных прогноза.</span><span class="sxs-lookup"><span data-stu-id="da89b-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="da89b-159">Для обнаружения аномалий прогноз состоит из предупреждения, указывающего на наличие аномалии, необработанной оценки и p-значения.</span><span class="sxs-lookup"><span data-stu-id="da89b-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="da89b-160">Чем ближе p-значение к 0, тем больше вероятность возникновения аномалий.</span><span class="sxs-lookup"><span data-stu-id="da89b-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="da89b-161">Создайте два глобальных поля для хранения пути к файлу недавно скачанного набора данных и пути к файлу сохраненной модели:</span><span class="sxs-lookup"><span data-stu-id="da89b-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="da89b-162">`_dataPath` содержит путь к набору данных, используемому для обучения модели;</span><span class="sxs-lookup"><span data-stu-id="da89b-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="da89b-163">`_docsize` содержит количество записей в файле набора данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="da89b-164">Вы будете использовать `_docSize` для вычисления `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="da89b-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="da89b-165">Добавьте следующий код в строку прямо перед методом `Main`, чтобы указать эти пути:</span><span class="sxs-lookup"><span data-stu-id="da89b-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](./snippets/sales-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="da89b-166">Инициализация переменных в методе Main</span><span class="sxs-lookup"><span data-stu-id="da89b-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="da89b-167">Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную `mlContext`:</span><span class="sxs-lookup"><span data-stu-id="da89b-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="da89b-168">[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="da89b-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="da89b-169">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="da89b-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="da89b-170">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="da89b-170">Load the data</span></span>

<span data-ttu-id="da89b-171">Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="da89b-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="da89b-172">`IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые).</span><span class="sxs-lookup"><span data-stu-id="da89b-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="da89b-173">Данные можно загружать в объект `IDataView` из текстового файла или других источников (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="da89b-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="da89b-174">Добавьте в следующую строку метода `Main()` приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="da89b-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](./snippets/sales-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="da89b-175">Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл.</span><span class="sxs-lookup"><span data-stu-id="da89b-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="da89b-176">Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="da89b-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="da89b-177">Обнаружение аномалий во временных рядах</span><span class="sxs-lookup"><span data-stu-id="da89b-177">Time series anomaly detection</span></span>

<span data-ttu-id="da89b-178">Функция обнаружения аномалий регистрирует неожиданные или необычные события или особенности поведения.</span><span class="sxs-lookup"><span data-stu-id="da89b-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="da89b-179">Кроме того, она подсказывает, где нужно искать проблему, и помогает ответить на вопрос "Является ли это странным?".</span><span class="sxs-lookup"><span data-stu-id="da89b-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Пример обнаружения аномалий с помощью ответа на вопрос"Является ли это странным?"](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

<span data-ttu-id="da89b-181">Обнаружение аномалий — это процесс обнаружения выбросов временных рядов данных, точек заданных входных временных рядов, где поведение отличается от ожидаемого или является "странным".</span><span class="sxs-lookup"><span data-stu-id="da89b-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="da89b-182">Обнаружение аномалий может быть полезным во многих ситуациях.</span><span class="sxs-lookup"><span data-stu-id="da89b-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="da89b-183">Например:</span><span class="sxs-lookup"><span data-stu-id="da89b-183">For instance:</span></span>

<span data-ttu-id="da89b-184">При наличии автомобиля вы, возможно, захотите узнать, правильны ли показания датчика масла или возникла утечка.</span><span class="sxs-lookup"><span data-stu-id="da89b-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="da89b-185">Если вы отслеживаете энергопотребление, то захотите узнать, имеет ли место простой.</span><span class="sxs-lookup"><span data-stu-id="da89b-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="da89b-186">Существуют два вида аномалий временных рядов, которые можно обнаружить.</span><span class="sxs-lookup"><span data-stu-id="da89b-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="da89b-187">**Пиковые значения** указывают временные всплески аномального поведения в системе.</span><span class="sxs-lookup"><span data-stu-id="da89b-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="da89b-188">**Точки изменений** указывают начало устойчивых изменений с течением времени в системе.</span><span class="sxs-lookup"><span data-stu-id="da89b-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="da89b-189">В ML.NET алгоритмы обнаружения пиковых значений IID или обнаружения точек изменений IID подходят для [независимых и одинаково распределенных наборов данных](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="da89b-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="da89b-190">В отличие от моделей в других руководствах, преобразования обнаружения аномалий временных рядов работают непосредственно с входными данными.</span><span class="sxs-lookup"><span data-stu-id="da89b-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="da89b-191">Методу `IEstimator.Fit()` не требуются обучающие данные для создания преобразования.</span><span class="sxs-lookup"><span data-stu-id="da89b-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="da89b-192">Для него нужна схема данных, которая предоставляется представлением данных, созданным из пустого списка `ProductSalesData`.</span><span class="sxs-lookup"><span data-stu-id="da89b-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="da89b-193">Вы проанализируете одни и те же данные о продажах продукта для обнаружения пиковых значений и точек изменений.</span><span class="sxs-lookup"><span data-stu-id="da89b-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="da89b-194">Процесс создания и обучения модели одинаков для обоих видов обнаружения; основное различие заключается в используемом алгоритме обнаружения.</span><span class="sxs-lookup"><span data-stu-id="da89b-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="da89b-195">Обнаружение пиковых значений</span><span class="sxs-lookup"><span data-stu-id="da89b-195">Spike detection</span></span>

<span data-ttu-id="da89b-196">Целью обнаружения пиковых значений является выявление внезапных, но при этом временных всплесков, которые значительно отличаются от большинства значений данных временных рядов.</span><span class="sxs-lookup"><span data-stu-id="da89b-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="da89b-197">Важно своевременно обнаружить эти подозрительные редкие элементы, события или наблюдения, чтобы свести их влияние к минимуму.</span><span class="sxs-lookup"><span data-stu-id="da89b-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="da89b-198">Для обнаружения разнообразных аномалий, таких как простои, кибератаки и вирусное веб-содержимое, можно использовать описанный ниже подход.</span><span class="sxs-lookup"><span data-stu-id="da89b-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="da89b-199">На следующем рисунке представлен пример пиковых значений в наборе данных временных рядов.</span><span class="sxs-lookup"><span data-stu-id="da89b-199">The following image is an example of spikes in a time series dataset:</span></span>

![Снимок экрана с данными обнаружения двух пиков.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="da89b-201">Добавьте метод CreateEmptyDataView()</span><span class="sxs-lookup"><span data-stu-id="da89b-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="da89b-202">Добавьте следующий метод к `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="da89b-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="da89b-203">`CreateEmptyDataView()` создает пустой объект представления данных с правильной схемой для использования в качестве входных данных для метода `IEstimator.Fit()`.</span><span class="sxs-lookup"><span data-stu-id="da89b-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="da89b-204">Создание метода DetectSpike()</span><span class="sxs-lookup"><span data-stu-id="da89b-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="da89b-205">Метод `DetectSpike()`:</span><span class="sxs-lookup"><span data-stu-id="da89b-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="da89b-206">Создает преобразование из средства оценки.</span><span class="sxs-lookup"><span data-stu-id="da89b-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="da89b-207">Обнаруживает пиковые значения на основе исторических данных о продажах.</span><span class="sxs-lookup"><span data-stu-id="da89b-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="da89b-208">Отображает результаты.</span><span class="sxs-lookup"><span data-stu-id="da89b-208">Displays the results.</span></span>

1. <span data-ttu-id="da89b-209">Создайте метод `DetectSpike()` сразу после метода `Main()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="da89b-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="da89b-210">Используйте [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator), чтобы обучить модель для обнаружения пиковых значений.</span><span class="sxs-lookup"><span data-stu-id="da89b-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="da89b-211">Добавьте его в метод `DetectSpike()` со следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="da89b-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="da89b-212">Создайте преобразование для обнаружения пиковых значений, добавив в метод `DetectSpike()` следующую строку кода:</span><span class="sxs-lookup"><span data-stu-id="da89b-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel1)]

1. <span data-ttu-id="da89b-213">Добавьте указанный ниже код для преобразования данных `productSales` в следующую строку метода `DetectSpike()`:</span><span class="sxs-lookup"><span data-stu-id="da89b-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData1)]

    <span data-ttu-id="da89b-214">Предыдущий код использует метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A), чтобы сделать прогнозы для нескольких входных строк набора данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="da89b-215">Преобразуйте `transformedData` в строго типизированный `IEnumerable` для более удобного отображения с помощью метода [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A), используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="da89b-215">Convert your `transformedData` into a strongly typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="da89b-216">Создайте отображаемую строку заголовка с помощью следующего кода <xref:System.Console.WriteLine?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="da89b-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader1)]

    <span data-ttu-id="da89b-217">В результатах обнаружения пиковых значений будут отображены следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="da89b-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="da89b-218">`Alert` указывает на оповещение о пиковом значении для заданной точки данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="da89b-219">`Score` является значением `ProductSales` для заданной точки данных в наборе данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="da89b-220">`P-Value` — "P" означает вероятность.</span><span class="sxs-lookup"><span data-stu-id="da89b-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="da89b-221">Чем ближе p-значение к 0, тем больше вероятность того, что точка данных аномальна.</span><span class="sxs-lookup"><span data-stu-id="da89b-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="da89b-222">Используйте следующий код, чтобы выполнить итерацию по `predictions` `IEnumerable` и отобразить результаты:</span><span class="sxs-lookup"><span data-stu-id="da89b-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults1)]

1. <span data-ttu-id="da89b-223">Добавьте вызов метода `DetectSpike()` в метод `Main()`.</span><span class="sxs-lookup"><span data-stu-id="da89b-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="da89b-224">Результаты обнаружения пиковых значений</span><span class="sxs-lookup"><span data-stu-id="da89b-224">Spike detection results</span></span>

<span data-ttu-id="da89b-225">Результаты выполнения должны выглядеть примерно так, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="da89b-225">Your results should be similar to the following.</span></span> <span data-ttu-id="da89b-226">Во время обработки отображаются сообщения.</span><span class="sxs-lookup"><span data-stu-id="da89b-226">During processing, messages are displayed.</span></span> <span data-ttu-id="da89b-227">Вы можете видеть предупреждения или обработанные сообщения.</span><span class="sxs-lookup"><span data-stu-id="da89b-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="da89b-228">Для удобства часть сообщений удалена из следующих результатов.</span><span class="sxs-lookup"><span data-stu-id="da89b-228">Some of the messages have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="da89b-229">Обнаружение точек изменений</span><span class="sxs-lookup"><span data-stu-id="da89b-229">Change point detection</span></span>

<span data-ttu-id="da89b-230">`Change points` — это постоянные изменения в распределении значений по потоку событий временных рядов, такие как изменения уровня и тенденции.</span><span class="sxs-lookup"><span data-stu-id="da89b-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="da89b-231">Эти постоянные изменения длятся гораздо дольше, чем `spikes`, и могут указывать на катастрофические события.</span><span class="sxs-lookup"><span data-stu-id="da89b-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="da89b-232">`Change points` обычно не видны невооруженным глазом, но могут быть обнаружены в данных с помощью таких подходов, которые описаны в следующем методе.</span><span class="sxs-lookup"><span data-stu-id="da89b-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="da89b-233">На следующем рисунке представлен пример обнаружения точек изменений.</span><span class="sxs-lookup"><span data-stu-id="da89b-233">The following image is an example of a change point detection:</span></span>

![Снимок экрана с данными обнаружения точки изменения.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="da89b-235">Создание метода DetectChangepoint()</span><span class="sxs-lookup"><span data-stu-id="da89b-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="da89b-236">Метод `DetectChangepoint()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="da89b-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="da89b-237">Создает преобразование из средства оценки.</span><span class="sxs-lookup"><span data-stu-id="da89b-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="da89b-238">Обнаруживает точки изменений на основе исторических данных о продажах.</span><span class="sxs-lookup"><span data-stu-id="da89b-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="da89b-239">Отображает результаты.</span><span class="sxs-lookup"><span data-stu-id="da89b-239">Displays the results.</span></span>

1. <span data-ttu-id="da89b-240">Создайте метод `DetectChangepoint()` сразу после метода `Main()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="da89b-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="da89b-241">Создайте [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) в методе `DetectChangepoint()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="da89b-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="da89b-242">Как и ранее, создайте преобразование из средства оценки, добавив следующую строку кода в метод `DetectChangePoint()`:</span><span class="sxs-lookup"><span data-stu-id="da89b-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel2)]

1. <span data-ttu-id="da89b-243">Используйте метод `Transform()` для преобразования данных, добавив в `DetectChangePoint()` следующий код:</span><span class="sxs-lookup"><span data-stu-id="da89b-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData2)]

1. <span data-ttu-id="da89b-244">Как и ранее, преобразуйте `transformedData` в строго типизированный `IEnumerable` для более удобного отображения с помощью метода `CreateEnumerable()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="da89b-244">As you did previously, convert your `transformedData` into a strongly typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="da89b-245">Создайте отображаемый заголовок, добавив в следующую строку метода `DetectChangePoint()` приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="da89b-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader2)]

    <span data-ttu-id="da89b-246">В результатах обнаружения точек изменений будут отображены следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="da89b-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="da89b-247">`Alert` указывает на оповещение о точке изменений для заданной точки данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="da89b-248">`Score` является значением `ProductSales` для заданной точки данных в наборе данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="da89b-249">`P-Value` — "P" означает вероятность.</span><span class="sxs-lookup"><span data-stu-id="da89b-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="da89b-250">Чем ближе p-значение к 0, тем больше вероятность того, что точка данных аномальна.</span><span class="sxs-lookup"><span data-stu-id="da89b-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="da89b-251">`Martingale value` — используется для определения того, насколько "странной" является точка данных, на основе последовательности P-значений.</span><span class="sxs-lookup"><span data-stu-id="da89b-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="da89b-252">Используйте следующий код, чтобы выполнить итерацию по `predictions` `IEnumerable` и отобразить результаты:</span><span class="sxs-lookup"><span data-stu-id="da89b-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults2)]

1. <span data-ttu-id="da89b-253">Добавьте вызов метода `DetectChangepoint()` в метод `Main()`.</span><span class="sxs-lookup"><span data-stu-id="da89b-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="da89b-254">Результаты обнаружения точек изменений</span><span class="sxs-lookup"><span data-stu-id="da89b-254">Change point detection results</span></span>

<span data-ttu-id="da89b-255">Результаты выполнения должны выглядеть примерно так, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="da89b-255">Your results should be similar to the following.</span></span> <span data-ttu-id="da89b-256">Во время обработки отображаются сообщения.</span><span class="sxs-lookup"><span data-stu-id="da89b-256">During processing, messages are displayed.</span></span> <span data-ttu-id="da89b-257">Вы можете видеть предупреждения или обработанные сообщения.</span><span class="sxs-lookup"><span data-stu-id="da89b-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="da89b-258">Для удобства некоторые сообщения удалены из следующих результатов.</span><span class="sxs-lookup"><span data-stu-id="da89b-258">Some messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="da89b-259">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="da89b-259">Congratulations!</span></span> <span data-ttu-id="da89b-260">Вы успешно создали модели машинного обучения для обнаружения аномалий в виде пиковых значений и точек изменений в данных о продажах.</span><span class="sxs-lookup"><span data-stu-id="da89b-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="da89b-261">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/ProductSalesAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="da89b-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="da89b-262">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="da89b-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="da89b-263">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="da89b-263">Load the data</span></span>
> * <span data-ttu-id="da89b-264">Обучение модели для обнаружения пиковых аномалий</span><span class="sxs-lookup"><span data-stu-id="da89b-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="da89b-265">Обнаружение пиковых аномалий с помощью обученной модели</span><span class="sxs-lookup"><span data-stu-id="da89b-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="da89b-266">Обучение модели для обнаружения аномалий в точке изменений</span><span class="sxs-lookup"><span data-stu-id="da89b-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="da89b-267">Обнаружение аномалий в точке изменений с помощью обученной модели</span><span class="sxs-lookup"><span data-stu-id="da89b-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="da89b-268">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="da89b-268">Next steps</span></span>

<span data-ttu-id="da89b-269">Ознакомьтесь с примерами машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример с обнаружением аномалий для сезонных данных.</span><span class="sxs-lookup"><span data-stu-id="da89b-269">Check out the Machine Learning samples GitHub repository to explore a seasonality data anomaly detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="da89b-270">Репозиторий GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="da89b-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/AnomalyDetection_PhoneCalls)
