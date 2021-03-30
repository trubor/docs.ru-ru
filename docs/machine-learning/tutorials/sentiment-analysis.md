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
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="9cec6-104">Учебник. Анализ мнений пользователей в комментариях с веб-сайта с помощью двоичной классификации в ML.NET</span><span class="sxs-lookup"><span data-stu-id="9cec6-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="9cec6-105">В этом руководстве показано, как создать консольное приложение .NET Core, которое классифицирует мнения, выраженные в комментариях с веб-сайта, и предпринимает соответствующие действия.</span><span class="sxs-lookup"><span data-stu-id="9cec6-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="9cec6-106">Двоичный классификатор тональности использует C# в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9cec6-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="9cec6-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="9cec6-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="9cec6-108">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="9cec6-108">Create a console application</span></span>
> - <span data-ttu-id="9cec6-109">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="9cec6-109">Prepare data</span></span>
> - <span data-ttu-id="9cec6-110">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="9cec6-110">Load the data</span></span>
> - <span data-ttu-id="9cec6-111">Сборка и обучение модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-111">Build and train the model</span></span>
> - <span data-ttu-id="9cec6-112">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-112">Evaluate the model</span></span>
> - <span data-ttu-id="9cec6-113">Использование модели для прогноза</span><span class="sxs-lookup"><span data-stu-id="9cec6-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="9cec6-114">Просмотр результатов</span><span class="sxs-lookup"><span data-stu-id="9cec6-114">See the results</span></span>

<span data-ttu-id="9cec6-115">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="9cec6-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9cec6-116">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="9cec6-116">Prerequisites</span></span>

- <span data-ttu-id="9cec6-117">[Visual Studio 2017 версии 15.6 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core"</span><span class="sxs-lookup"><span data-stu-id="9cec6-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="9cec6-118">[Набор данных — предложения с меткой тональности UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP-файл)</span><span class="sxs-lookup"><span data-stu-id="9cec6-118">[UCI Sentiment Labeled Sentences dataset](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="9cec6-119">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="9cec6-119">Create a console application</span></span>

1. <span data-ttu-id="9cec6-120">Создайте **консольное приложение .NET Core** с именем SentimentAnalysis.</span><span class="sxs-lookup"><span data-stu-id="9cec6-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="9cec6-121">Создайте каталог с именем *Data* в проекте, чтобы сохранять файлы набора данных.</span><span class="sxs-lookup"><span data-stu-id="9cec6-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="9cec6-122">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="9cec6-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="9cec6-123">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9cec6-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9cec6-124">Выберите nuget.org в качестве источника пакета, а затем выберите вкладку **Обзор**. Найдите **Microsoft.ML**, выберите пакет и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="9cec6-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="9cec6-125">Продолжите установку, соглашаясь с условиями лицензии для выбранного пакета.</span><span class="sxs-lookup"><span data-stu-id="9cec6-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="9cec6-126">подготавливать данные;</span><span class="sxs-lookup"><span data-stu-id="9cec6-126">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="9cec6-127">Наборы данных в этом руководстве взяты из статьи From Group to Individual Labels using Deep Features ("Переход от групповых меток к индивидуальным при помощи глубинных признаков"), Котциас (Kotzias) и</span><span class="sxs-lookup"><span data-stu-id="9cec6-127">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="9cec6-128">др.,</span><span class="sxs-lookup"><span data-stu-id="9cec6-128">al,.</span></span> <span data-ttu-id="9cec6-129">KDD 2015, и размещены в репозитории машинного обучения UCI Д. Дуа (D. Dua) и Э. Карра Танискиду (E. Karra Taniskidou) (2017).</span><span class="sxs-lookup"><span data-stu-id="9cec6-129">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="9cec6-130">UCI Machine Learning Repository (Репозиторий машинного обучения UCI) [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="9cec6-130">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="9cec6-131">Ирвайн, Калифорния: Калифорнийский университет, Школа информационных технологий и компьютерных наук.</span><span class="sxs-lookup"><span data-stu-id="9cec6-131">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="9cec6-132">Скачайте [ZIP-файл набора данных предложений с меткой тональности UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) и извлеките его содержимое.</span><span class="sxs-lookup"><span data-stu-id="9cec6-132">Download [UCI Sentiment Labeled Sentences dataset ZIP file](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="9cec6-133">Скопируйте файл `yelp_labelled.txt` в созданный каталог *Data*.</span><span class="sxs-lookup"><span data-stu-id="9cec6-133">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="9cec6-134">В обозревателе решений щелкните правой кнопкой мыши файл `yelp_labeled.txt` и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="9cec6-134">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="9cec6-135">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="9cec6-135">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="9cec6-136">Создание классов и определение путей</span><span class="sxs-lookup"><span data-stu-id="9cec6-136">Create classes and define paths</span></span>

1. <span data-ttu-id="9cec6-137">Добавьте следующие новые операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="9cec6-137">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="9cec6-138">Добавьте следующий код в строку прямо над методом `Main`, чтобы создать поле для хранения недавно скачанного пути к файлу набора данных:</span><span class="sxs-lookup"><span data-stu-id="9cec6-138">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](./snippets/sentiment-analysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="9cec6-139">Затем создайте классы для входных данных и прогнозов.</span><span class="sxs-lookup"><span data-stu-id="9cec6-139">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="9cec6-140">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="9cec6-140">Add a new class to your project:</span></span>

    - <span data-ttu-id="9cec6-141">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="9cec6-141">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="9cec6-142">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9cec6-142">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="9cec6-143">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="9cec6-143">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="9cec6-144">Файл *SentimentData.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="9cec6-144">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="9cec6-145">Добавьте следующий оператор `using` в начало файла *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9cec6-145">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="9cec6-146">Удалите из файла *SentimentData.cs* существующее определение класса и добавьте следующий код с двумя классами `SentimentData` и `SentimentPrediction`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-146">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/sentiment-analysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="9cec6-147">Как вы подготовили данные</span><span class="sxs-lookup"><span data-stu-id="9cec6-147">How the data was prepared</span></span>

<span data-ttu-id="9cec6-148">Класс входного набора данных, `SentimentData`, имеет `string` для комментариев пользователя (`SentimentText`) и `bool` (`Sentiment`) значение 1 (положительная) или 0 (отрицательная) для определения тональности.</span><span class="sxs-lookup"><span data-stu-id="9cec6-148">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="9cec6-149">Оба поля имеют атрибуты [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29), которые описывают порядок файла данных каждого поля.</span><span class="sxs-lookup"><span data-stu-id="9cec6-149">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="9cec6-150">Кроме того, свойство `Sentiment` имеет атрибут[ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A), чтобы обозначить его как поле `Label`.</span><span class="sxs-lookup"><span data-stu-id="9cec6-150">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="9cec6-151">В примере файла ниже отсутствует строка заголовка. Сам файл выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9cec6-151">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="9cec6-152">SentimentText</span><span class="sxs-lookup"><span data-stu-id="9cec6-152">SentimentText</span></span>                         |<span data-ttu-id="9cec6-153">Тональность (метка)</span><span class="sxs-lookup"><span data-stu-id="9cec6-153">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="9cec6-154">Официантка немного медленная.</span><span class="sxs-lookup"><span data-stu-id="9cec6-154">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="9cec6-155">0</span><span class="sxs-lookup"><span data-stu-id="9cec6-155">0</span></span>     |
|<span data-ttu-id="9cec6-156">Корочка так себе.</span><span class="sxs-lookup"><span data-stu-id="9cec6-156">Crust is not good.</span></span>                    |    <span data-ttu-id="9cec6-157">0</span><span class="sxs-lookup"><span data-stu-id="9cec6-157">0</span></span>     |
|<span data-ttu-id="9cec6-158">Ого... Отличное место.</span><span class="sxs-lookup"><span data-stu-id="9cec6-158">Wow... Loved this place.</span></span>              |    <span data-ttu-id="9cec6-159">1</span><span class="sxs-lookup"><span data-stu-id="9cec6-159">1</span></span>     |
|<span data-ttu-id="9cec6-160">Обслуживание очень быстрое.</span><span class="sxs-lookup"><span data-stu-id="9cec6-160">Service was very prompt.</span></span>              |    <span data-ttu-id="9cec6-161">1</span><span class="sxs-lookup"><span data-stu-id="9cec6-161">1</span></span>     |

<span data-ttu-id="9cec6-162">`SentimentPrediction` — этот класс прогноза используется после обучения модели.</span><span class="sxs-lookup"><span data-stu-id="9cec6-162">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="9cec6-163">Он наследует от `SentimentData` таким образом, чтобы входные данные `SentimentText` могли отображаться вместе с выходными данными прогноза.</span><span class="sxs-lookup"><span data-stu-id="9cec6-163">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="9cec6-164">Логическое значение `Prediction` является значением, которое модель прогнозирует при предоставлении новых входных данных `SentimentText`.</span><span class="sxs-lookup"><span data-stu-id="9cec6-164">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="9cec6-165">Класс выходных данных `SentimentPrediction` содержит два свойства, вычисляемые в модели: `Score` — необработанная оценка, вычисляемая в модели, и `Probability` — оценка, откалиброванная по вероятности того, что текст имеет положительную тональность.</span><span class="sxs-lookup"><span data-stu-id="9cec6-165">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="9cec6-166">В этом учебнике самым важным свойством является `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="9cec6-166">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="9cec6-167">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="9cec6-167">Load the data</span></span>

<span data-ttu-id="9cec6-168">Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="9cec6-168">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="9cec6-169">`IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые).</span><span class="sxs-lookup"><span data-stu-id="9cec6-169">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="9cec6-170">Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="9cec6-170">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="9cec6-171">[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для всех операций ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9cec6-171">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="9cec6-172">Инициализация `mlContext` создает новую среду ML.NET, которую могут совместно использовать объекты рабочего процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="9cec6-172">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="9cec6-173">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9cec6-173">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="9cec6-174">Необходимо подготовить приложение и затем загружать данные.</span><span class="sxs-lookup"><span data-stu-id="9cec6-174">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="9cec6-175">Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом, чтобы объявить и инициализировать переменную mlContext:</span><span class="sxs-lookup"><span data-stu-id="9cec6-175">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/sentiment-analysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="9cec6-176">Добавьте в следующую строку метода `Main()` приведенный ниже код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-176">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](./snippets/sentiment-analysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="9cec6-177">Создайте метод `LoadData()` сразу после метода `Main()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-177">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="9cec6-178">Метод `LoadData()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="9cec6-178">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="9cec6-179">загрузка данных;</span><span class="sxs-lookup"><span data-stu-id="9cec6-179">Loads the data.</span></span>
    - <span data-ttu-id="9cec6-180">Разделяет скачанный набор данных на наборы данных для обучения и тестирования.</span><span class="sxs-lookup"><span data-stu-id="9cec6-180">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="9cec6-181">Возвращает два набора данных — для обучения и для тестирования.</span><span class="sxs-lookup"><span data-stu-id="9cec6-181">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="9cec6-182">Добавьте следующий код в первую строку метода `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-182">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](./snippets/sentiment-analysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="9cec6-183">Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл.</span><span class="sxs-lookup"><span data-stu-id="9cec6-183">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) method defines the data schema and reads in the file.</span></span> <span data-ttu-id="9cec6-184">Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="9cec6-184">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="9cec6-185">Разделение набора данных для обучения и тестирования модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-185">Split the dataset for model training and testing</span></span>

<span data-ttu-id="9cec6-186">При подготовке модели можно использовать часть набора данных для обучения, а другую часть — для проверки точности модели.</span><span class="sxs-lookup"><span data-stu-id="9cec6-186">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="9cec6-187">Чтобы разделить скачанные данные на необходимые наборы данных, добавьте код в следующей строке метода `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-187">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](./snippets/sentiment-analysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="9cec6-188">Приведенный выше код использует метод [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A), чтобы разделить загруженный набор данных на учебный и проверочный наборы данных и возвратить их в класс <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData>.</span><span class="sxs-lookup"><span data-stu-id="9cec6-188">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> class.</span></span> <span data-ttu-id="9cec6-189">Укажите процент тестовых данных с помощью параметра `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="9cec6-189">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="9cec6-190">Значение по умолчанию — 10 %, но в этом случае лучше использовать 20 % для оценки большего объема данных.</span><span class="sxs-lookup"><span data-stu-id="9cec6-190">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="9cec6-191">Верните `splitDataView` в конце метода `LoadData()`.</span><span class="sxs-lookup"><span data-stu-id="9cec6-191">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](./snippets/sentiment-analysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="9cec6-192">Сборка и обучение модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-192">Build and train the model</span></span>

1. <span data-ttu-id="9cec6-193">В следующей строке кода в методе `Main()` добавьте приведенный ниже вызов метода `BuildAndTrainModel`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-193">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](./snippets/sentiment-analysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="9cec6-194">Метод `BuildAndTrainModel()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="9cec6-194">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="9cec6-195">извлечение и преобразование данных;</span><span class="sxs-lookup"><span data-stu-id="9cec6-195">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="9cec6-196">обучение модели;</span><span class="sxs-lookup"><span data-stu-id="9cec6-196">Trains the model.</span></span>
    - <span data-ttu-id="9cec6-197">прогноз тональности на основе тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="9cec6-197">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="9cec6-198">возвращение модели.</span><span class="sxs-lookup"><span data-stu-id="9cec6-198">Returns the model.</span></span>

2. <span data-ttu-id="9cec6-199">Создайте метод `BuildAndTrainModel()` сразу после метода `Main()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-199">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="9cec6-200">Извлечение и преобразование данных</span><span class="sxs-lookup"><span data-stu-id="9cec6-200">Extract and transform the data</span></span>

1. <span data-ttu-id="9cec6-201">Добавьте следующую строку кода для вызова `FeaturizeText`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-201">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](./snippets/sentiment-analysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="9cec6-202">Метод `FeaturizeText()` в приведенном выше коде преобразует текстовый столбец (`SentimentText`) в числовой столбец типа ключа `Features`, который используется алгоритмом машинного обучения: он добавляет его как новый столбец набора данных:</span><span class="sxs-lookup"><span data-stu-id="9cec6-202">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="9cec6-203">SentimentText</span><span class="sxs-lookup"><span data-stu-id="9cec6-203">SentimentText</span></span>                         |<span data-ttu-id="9cec6-204">Тональность</span><span class="sxs-lookup"><span data-stu-id="9cec6-204">Sentiment</span></span> |<span data-ttu-id="9cec6-205">Функции</span><span class="sxs-lookup"><span data-stu-id="9cec6-205">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="9cec6-206">Официантка немного медленная.</span><span class="sxs-lookup"><span data-stu-id="9cec6-206">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="9cec6-207">0</span><span class="sxs-lookup"><span data-stu-id="9cec6-207">0</span></span>     |<span data-ttu-id="9cec6-208">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="9cec6-208">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="9cec6-209">Корочка так себе.</span><span class="sxs-lookup"><span data-stu-id="9cec6-209">Crust is not good.</span></span>                    |    <span data-ttu-id="9cec6-210">0</span><span class="sxs-lookup"><span data-stu-id="9cec6-210">0</span></span>     |<span data-ttu-id="9cec6-211">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="9cec6-211">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="9cec6-212">Ого... Отличное место.</span><span class="sxs-lookup"><span data-stu-id="9cec6-212">Wow... Loved this place.</span></span>              |    <span data-ttu-id="9cec6-213">1</span><span class="sxs-lookup"><span data-stu-id="9cec6-213">1</span></span>     |<span data-ttu-id="9cec6-214">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="9cec6-214">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="9cec6-215">Обслуживание очень быстрое.</span><span class="sxs-lookup"><span data-stu-id="9cec6-215">Service was very prompt.</span></span>              |    <span data-ttu-id="9cec6-216">1</span><span class="sxs-lookup"><span data-stu-id="9cec6-216">1</span></span>     |<span data-ttu-id="9cec6-217">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="9cec6-217">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="9cec6-218">Добавление алгоритма обучения</span><span class="sxs-lookup"><span data-stu-id="9cec6-218">Add a learning algorithm</span></span>

<span data-ttu-id="9cec6-219">Это приложение использует алгоритм классификации, который классифицирует элементы или строки данных.</span><span class="sxs-lookup"><span data-stu-id="9cec6-219">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="9cec6-220">Приложение классифицирует комментарии веб-сайта как положительные или отрицательные, поэтому это задача двоичной классификации.</span><span class="sxs-lookup"><span data-stu-id="9cec6-220">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="9cec6-221">Добавьте задачу машинного обучения к определениям преобразований данных, добавив следующее в следующей строке кода в `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-221">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](./snippets/sentiment-analysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="9cec6-222">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) — ваш алгоритм обучения классификации.</span><span class="sxs-lookup"><span data-stu-id="9cec6-222">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="9cec6-223">Он добавляется в `estimator` и принимает `SentimentText` с присвоенными признаками (`Features`) и входные параметры `Label`, чтобы пройти обучение по историческим данным.</span><span class="sxs-lookup"><span data-stu-id="9cec6-223">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="9cec6-224">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-224">Train the model</span></span>

<span data-ttu-id="9cec6-225">Обучите модель на основе данных `splitTrainSet` и получите обученную модель, добавив в метод `BuildAndTrainModel()` следующие строки кода:</span><span class="sxs-lookup"><span data-stu-id="9cec6-225">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](./snippets/sentiment-analysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="9cec6-226">Метод [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) обучает модель путем преобразования набора данных и применения обучения.</span><span class="sxs-lookup"><span data-stu-id="9cec6-226">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="9cec6-227">Возврат обученной модели для оценки</span><span class="sxs-lookup"><span data-stu-id="9cec6-227">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="9cec6-228">Выполните возврат модели в конце метода `BuildAndTrainModel()`.</span><span class="sxs-lookup"><span data-stu-id="9cec6-228">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](./snippets/sentiment-analysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="9cec6-229">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-229">Evaluate the model</span></span>

<span data-ttu-id="9cec6-230">После обучения модели с помощью проверочных данных производится валидация производительности модели.</span><span class="sxs-lookup"><span data-stu-id="9cec6-230">After your model is trained, use your test data to validate the model's performance.</span></span>

1. <span data-ttu-id="9cec6-231">Создайте метод `Evaluate()` сразу после `BuildAndTrainModel()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-231">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="9cec6-232">Метод `Evaluate()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="9cec6-232">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="9cec6-233">загрузка тестового набора данных;</span><span class="sxs-lookup"><span data-stu-id="9cec6-233">Loads the test dataset.</span></span>
    - <span data-ttu-id="9cec6-234">создание средства оценки BinaryClassification;</span><span class="sxs-lookup"><span data-stu-id="9cec6-234">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="9cec6-235">оценка модели и создание метрик;</span><span class="sxs-lookup"><span data-stu-id="9cec6-235">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="9cec6-236">отображение метрик.</span><span class="sxs-lookup"><span data-stu-id="9cec6-236">Displays the metrics.</span></span>

2. <span data-ttu-id="9cec6-237">Добавьте вызов нового метода из метода `Main()`, сразу после вызова метода `BuildAndTrainModel()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-237">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](./snippets/sentiment-analysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="9cec6-238">Преобразуйте данные `splitTestSet`, добавив в метод `Evaluate()` следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-238">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](./snippets/sentiment-analysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="9cec6-239">Предыдущий код использует метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A), чтобы сделать прогнозы для нескольких входных строк тестового набора данных.</span><span class="sxs-lookup"><span data-stu-id="9cec6-239">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="9cec6-240">Оцените модель, добавив в метод `Evaluate()` следующую строку кода:</span><span class="sxs-lookup"><span data-stu-id="9cec6-240">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](./snippets/sentiment-analysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="9cec6-241">После получения прогноза (`predictions`) метод [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) оценивает модель, сравнивая спрогнозированные значения с фактическими метками (`Labels`) в тестовом наборе данных, а затем возвращает объект [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) как метрики эффективности модели.</span><span class="sxs-lookup"><span data-stu-id="9cec6-241">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="9cec6-242">Отображение метрик для проверки модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-242">Displaying the metrics for model validation</span></span>

<span data-ttu-id="9cec6-243">Воспользуйтесь приведенным ниже кодом, чтобы отобразить метрики.</span><span class="sxs-lookup"><span data-stu-id="9cec6-243">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](./snippets/sentiment-analysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="9cec6-244">Метрика `Accuracy` возвращает точность модели — это доля правильных прогнозов в тестовом наборе.</span><span class="sxs-lookup"><span data-stu-id="9cec6-244">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="9cec6-245">Метрика `AreaUnderRocCurve` показывает уверенность модели в правильности классификации с положительными и отрицательными классами.</span><span class="sxs-lookup"><span data-stu-id="9cec6-245">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="9cec6-246">Значение `AreaUnderRocCurve` должно быть максимально близким к единице.</span><span class="sxs-lookup"><span data-stu-id="9cec6-246">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="9cec6-247">Метрика `F1Score` содержит F1-оценку модели, который является мерой баланса между [точностью](../resources/glossary.md#precision) и [полнотой](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="9cec6-247">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="9cec6-248">Значение `F1Score` должно быть максимально близким к единице.</span><span class="sxs-lookup"><span data-stu-id="9cec6-248">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="9cec6-249">Прогнозировать результаты для тестовых данных</span><span class="sxs-lookup"><span data-stu-id="9cec6-249">Predict the test data outcome</span></span>

1. <span data-ttu-id="9cec6-250">Создайте метод `UseModelWithSingleItem()` сразу после метода `Evaluate()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-250">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="9cec6-251">Метод `UseModelWithSingleItem()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="9cec6-251">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="9cec6-252">создание отдельного комментария тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="9cec6-252">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="9cec6-253">прогноз тональности на основе тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="9cec6-253">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="9cec6-254">объединение тестовых данных и прогнозов для создания отчетов;</span><span class="sxs-lookup"><span data-stu-id="9cec6-254">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="9cec6-255">отображение результатов прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="9cec6-255">Displays the predicted results.</span></span>

2. <span data-ttu-id="9cec6-256">Добавьте вызов нового метода из метода `Main()`, сразу после вызова метода `Evaluate()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-256">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="9cec6-257">Давайте добавим следующий код в качестве первой строки в методе `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-257">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](./snippets/sentiment-analysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="9cec6-258">Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных.</span><span class="sxs-lookup"><span data-stu-id="9cec6-258">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="9cec6-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="9cec6-259">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="9cec6-260">Допустимо использовать в средах прототипов или средах с одним потоком.</span><span class="sxs-lookup"><span data-stu-id="9cec6-260">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="9cec6-261">Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="9cec6-261">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="9cec6-262">См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="9cec6-262">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="9cec6-263">Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="9cec6-263">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="9cec6-264">Добавьте комментарий для проверки прогнозирования обученной модели в методе `UseModelWithSingleItem()`, создав экземпляр `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-264">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="9cec6-265">Передайте данные тестового комментария в [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), добавив следующие строки кода в метод `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-265">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="9cec6-266">Функция [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) создает прогноз по одной строке данных.</span><span class="sxs-lookup"><span data-stu-id="9cec6-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="9cec6-267">Выведите `SentimentText` и соответствующий прогноз тональности, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](./snippets/sentiment-analysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="9cec6-268">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="9cec6-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="9cec6-269">Развертывание и прогнозирование элементов пакета</span><span class="sxs-lookup"><span data-stu-id="9cec6-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="9cec6-270">Создайте метод `UseModelWithBatchItems()` сразу после метода `UseModelWithSingleItem()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="9cec6-271">Метод `UseModelWithBatchItems()` выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="9cec6-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="9cec6-272">создание пакетных тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="9cec6-272">Creates batch test data.</span></span>
    - <span data-ttu-id="9cec6-273">прогноз тональности на основе тестовых данных;</span><span class="sxs-lookup"><span data-stu-id="9cec6-273">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="9cec6-274">объединение тестовых данных и прогнозов для создания отчетов;</span><span class="sxs-lookup"><span data-stu-id="9cec6-274">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="9cec6-275">отображение результатов прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="9cec6-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="9cec6-276">Добавьте вызов нового метода из метода `Main`, сразу после вызова метода `UseModelWithSingleItem()`, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="9cec6-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="9cec6-277">Добавьте новые комментарии, чтобы проверить прогнозы обученной модели, в метод `UseModelWithBatchItems()`:</span><span class="sxs-lookup"><span data-stu-id="9cec6-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="9cec6-278">Предсказание тональности на основе комментариев</span><span class="sxs-lookup"><span data-stu-id="9cec6-278">Predict comment sentiment</span></span>

<span data-ttu-id="9cec6-279">Использование модели для прогнозирования тональности комментариев с помощью метода [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A):</span><span class="sxs-lookup"><span data-stu-id="9cec6-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="9cec6-280">Объедините и отобразите прогнозы</span><span class="sxs-lookup"><span data-stu-id="9cec6-280">Combine and display the predictions</span></span>

<span data-ttu-id="9cec6-281">Создайте заголовок для результатов с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="9cec6-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](./snippets/sentiment-analysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="9cec6-282">Так как `SentimentPrediction` наследуется от `SentimentData`, `Transform()` метод заполняет `SentimentText` прогнозируемыми полями.</span><span class="sxs-lookup"><span data-stu-id="9cec6-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="9cec6-283">В ходе обработки ML.NET каждый компонент добавляет столбцы, что упрощает отображение результатов:</span><span class="sxs-lookup"><span data-stu-id="9cec6-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](./snippets/sentiment-analysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="9cec6-284">Результаты</span><span class="sxs-lookup"><span data-stu-id="9cec6-284">Results</span></span>

<span data-ttu-id="9cec6-285">Результаты выполнения должны выглядеть примерно так, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="9cec6-285">Your results should be similar to the following.</span></span> <span data-ttu-id="9cec6-286">Во время обработки отображаются сообщения.</span><span class="sxs-lookup"><span data-stu-id="9cec6-286">During processing, messages are displayed.</span></span> <span data-ttu-id="9cec6-287">Вы можете видеть предупреждения или обработанные сообщения.</span><span class="sxs-lookup"><span data-stu-id="9cec6-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="9cec6-288">Для удобства они удалены из следующих результатов.</span><span class="sxs-lookup"><span data-stu-id="9cec6-288">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="9cec6-289">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="9cec6-289">Congratulations!</span></span> <span data-ttu-id="9cec6-290">Вы успешно создали модель машинного обучения для классификации и прогнозирования тональности сообщений.</span><span class="sxs-lookup"><span data-stu-id="9cec6-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="9cec6-291">Построение успешных моделей — итеративный процесс.</span><span class="sxs-lookup"><span data-stu-id="9cec6-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="9cec6-292">Изначально эта модель имеет низкое качество, так как в руководстве используются небольшие наборы данных для быстрого обучения.</span><span class="sxs-lookup"><span data-stu-id="9cec6-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="9cec6-293">Если вам требуется модель более высокого качества, можно попытаться улучшить ее, использовав более крупные наборы данных для обучения или выбрав другие алгоритмы обучения с разными [гиперпараметрами](../resources/glossary.md#hyperparameter) для каждого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="9cec6-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="9cec6-294">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="9cec6-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9cec6-295">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="9cec6-295">Next steps</span></span>

<span data-ttu-id="9cec6-296">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="9cec6-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="9cec6-297">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="9cec6-297">Create a console application</span></span>
> - <span data-ttu-id="9cec6-298">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="9cec6-298">Prepare data</span></span>
> - <span data-ttu-id="9cec6-299">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="9cec6-299">Load the data</span></span>
> - <span data-ttu-id="9cec6-300">Сборка и обучение модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-300">Build and train the model</span></span>
> - <span data-ttu-id="9cec6-301">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="9cec6-301">Evaluate the model</span></span>
> - <span data-ttu-id="9cec6-302">Использование модели для прогноза</span><span class="sxs-lookup"><span data-stu-id="9cec6-302">Use the model to make a prediction</span></span>
> - <span data-ttu-id="9cec6-303">Просмотр результатов</span><span class="sxs-lookup"><span data-stu-id="9cec6-303">See the results</span></span>

<span data-ttu-id="9cec6-304">Переходите к следующему руководству:</span><span class="sxs-lookup"><span data-stu-id="9cec6-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9cec6-305">Классификация задач</span><span class="sxs-lookup"><span data-stu-id="9cec6-305">Issue Classification</span></span>](github-issue-classification.md)
