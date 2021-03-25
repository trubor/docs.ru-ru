---
title: Учебник. Создание приложения для рекомендации фильмов — матричная факторизация
description: В этом руководстве показано, как построить приложение для рекомендации фильмов с помощью ML.NET в консольном проекте .NET Core. Используется C# и Visual Studio 2019.
author: briacht
ms.date: 06/30/2020
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 2df774110d3355bf75a14e211555984a12cf7fa4
ms.sourcegitcommit: b27645cb378d4e8137a267e5467ff31409acf6c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2021
ms.locfileid: "103231398"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a><span data-ttu-id="65bb7-104">Учебник. Создание приложения для рекомендации фильмов с использованием матричной факторизации и ML.NET</span><span class="sxs-lookup"><span data-stu-id="65bb7-104">Tutorial: Build a movie recommender using matrix factorization with ML.NET</span></span>

<span data-ttu-id="65bb7-105">В этом руководстве показано, как построить приложение для рекомендации фильмов с помощью ML.NET в консольном проекте .NET Core.</span><span class="sxs-lookup"><span data-stu-id="65bb7-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="65bb7-106">Используется C# и Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="65bb7-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="65bb7-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="65bb7-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="65bb7-108">выбрать алгоритм машинного обучения;</span><span class="sxs-lookup"><span data-stu-id="65bb7-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="65bb7-109">подготовить и загрузить данные;</span><span class="sxs-lookup"><span data-stu-id="65bb7-109">Prepare and load your data</span></span>
> * <span data-ttu-id="65bb7-110">создать и обучить модель;</span><span class="sxs-lookup"><span data-stu-id="65bb7-110">Build and train a model</span></span>
> * <span data-ttu-id="65bb7-111">оценить модель;</span><span class="sxs-lookup"><span data-stu-id="65bb7-111">Evaluate a model</span></span>
> * <span data-ttu-id="65bb7-112">развернуть и использовать модель.</span><span class="sxs-lookup"><span data-stu-id="65bb7-112">Deploy and consume a model</span></span>

<span data-ttu-id="65bb7-113">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).</span><span class="sxs-lookup"><span data-stu-id="65bb7-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="65bb7-114">Рабочий процесс машинного обучения</span><span class="sxs-lookup"><span data-stu-id="65bb7-114">Machine learning workflow</span></span>

<span data-ttu-id="65bb7-115">Решение поставленной задачи, как и любой задачи в ML.NET, состоит из следующих этапов:</span><span class="sxs-lookup"><span data-stu-id="65bb7-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="65bb7-116">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="65bb7-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="65bb7-117">Создание и обучение модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="65bb7-118">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="65bb7-119">Использование модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="65bb7-120">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="65bb7-120">Prerequisites</span></span>

* <span data-ttu-id="65bb7-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="65bb7-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="65bb7-122">Выбор подходящей задачи машинного обучения</span><span class="sxs-lookup"><span data-stu-id="65bb7-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="65bb7-123">Есть несколько подходов к проблеме предоставления рекомендаций, например в отношении фильмов или связанных продуктов. В данном случае мы будем прогнозировать оценку (от 1 до 5), которую пользователь поставил бы определенному фильму, и рекомендуем этот фильм, если оценка выше установленного порога (чем выше оценка, тем больше вероятность того, что фильм понравится пользователю).</span><span class="sxs-lookup"><span data-stu-id="65bb7-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="65bb7-124">Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="65bb7-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="65bb7-125">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="65bb7-125">Create a project</span></span>

1. <span data-ttu-id="65bb7-126">Откройте Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="65bb7-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="65bb7-127">Выберите **Файл** > **Создать** > **Проект** в меню.</span><span class="sxs-lookup"><span data-stu-id="65bb7-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="65bb7-128">В диалоговом окне **Новый проект** выберите узел **Visual C#** , а затем — узел **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="65bb7-129">Выберите шаблон проекта **Консольное приложение (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="65bb7-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="65bb7-130">В текстовом поле **Имя** введите "MovieRecommender", а затем нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="65bb7-131">Создайте каталог с именем *Data* в папке проекта, чтобы сохранить в нем набор данных:</span><span class="sxs-lookup"><span data-stu-id="65bb7-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="65bb7-132">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новая папка**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="65bb7-133">Введите имя папки Data и нажмите клавишу "ВВОД".</span><span class="sxs-lookup"><span data-stu-id="65bb7-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="65bb7-134">Установите пакеты NuGet **Microsoft.ML** и **Microsoft.ML.Recommender**:</span><span class="sxs-lookup"><span data-stu-id="65bb7-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="65bb7-135">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="65bb7-136">Выберите в качестве источника пакета "nuget.org", откройте вкладку **Обзор**, найдите **Microsoft.ML**, выберите пакет в списке и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="65bb7-137">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="65bb7-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="65bb7-138">Повторите эти действия для пакета **Microsoft.ML.Recommender**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="65bb7-139">Добавьте следующие операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="65bb7-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](./snippets/movie-recommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="65bb7-140">Скачивание данных</span><span class="sxs-lookup"><span data-stu-id="65bb7-140">Download your data</span></span>

1. <span data-ttu-id="65bb7-141">Скачайте два набора данных и сохраните их в ранее созданную папку *Data*.</span><span class="sxs-lookup"><span data-stu-id="65bb7-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="65bb7-142">Щелкните файл [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) правой кнопкой мыши и выберите команду "Сохранить ссылку (объект) как...".</span><span class="sxs-lookup"><span data-stu-id="65bb7-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="65bb7-143">Щелкните файл [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) правой кнопкой мыши и выберите команду "Сохранить ссылку (объект) как...".</span><span class="sxs-lookup"><span data-stu-id="65bb7-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="65bb7-144">Файлы \*.csv нужно сохранить в папке *Data*. Если вы сохранили файлы \*.csv в другом месте, переместите их в папку *Data*.</span><span class="sxs-lookup"><span data-stu-id="65bb7-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="65bb7-145">В обозревателе решений щелкните правой кнопкой мыши каждый из файлов \*.csv и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="65bb7-146">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![GIF пользователя, который выбирает в VS пункт "Копировать более новые".](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a><span data-ttu-id="65bb7-148">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="65bb7-148">Load your data</span></span>

<span data-ttu-id="65bb7-149">Первый шаг в процессе работы с ML.NET — подготовка и загрузка данных для обучения и тестирования модели.</span><span class="sxs-lookup"><span data-stu-id="65bb7-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="65bb7-150">Данные для оценки рекомендаций разделяются на наборы `Train` и `Test`.</span><span class="sxs-lookup"><span data-stu-id="65bb7-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="65bb7-151">Данные `Train` служат для обучения модели.</span><span class="sxs-lookup"><span data-stu-id="65bb7-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="65bb7-152">Данные `Test` используются для прогнозирования на основе обученной модели и оценки ее эффективности.</span><span class="sxs-lookup"><span data-stu-id="65bb7-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="65bb7-153">Данные `Train` и `Test` обычно делятся в отношении 80/20.</span><span class="sxs-lookup"><span data-stu-id="65bb7-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="65bb7-154">Ниже приведен пример данных из ваших файлов \*.csv.</span><span class="sxs-lookup"><span data-stu-id="65bb7-154">Below is a preview of the data from your \*.csv files:</span></span>

![Снимок экрана с окном предварительного просмотра набора данных CVS.](./media/movie-recommendation/csv-file-dataset-preview.png)

<span data-ttu-id="65bb7-156">В файлах \*.csv четыре столбца:</span><span class="sxs-lookup"><span data-stu-id="65bb7-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="65bb7-157">В машинном обучении столбцы, используемые для прогнозирования, называются [признаками](../resources/glossary.md#feature), а столбец с итоговым прогнозом — [меткой](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="65bb7-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="65bb7-158">Нам нужно прогнозировать рейтинг фильмов, поэтому меткой (`Label`) является столбец rating.</span><span class="sxs-lookup"><span data-stu-id="65bb7-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="65bb7-159">Остальные столбцы (`userId`, `movieId` и `timestamp`) — это признаки `Features`, используемые для прогнозирования метки `Label`.</span><span class="sxs-lookup"><span data-stu-id="65bb7-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="65bb7-160">Функции</span><span class="sxs-lookup"><span data-stu-id="65bb7-160">Features</span></span>      | <span data-ttu-id="65bb7-161">Метка</span><span class="sxs-lookup"><span data-stu-id="65bb7-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="65bb7-162">Какие признаки (`Features`) будут использоваться для прогнозирования метки (`Label`) — решать вам.</span><span class="sxs-lookup"><span data-stu-id="65bb7-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="65bb7-163">Для выбора подходящих признаков (`Features`) можно также использовать такие методы, как [важность комбинаций признаков](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="65bb7-163">You can also use methods like [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="65bb7-164">В данном случае столбец `timestamp` следует исключить из числа признаков (`Feature`), так как метка времени не влияет на оценку фильма пользователем и поэтому не повышает точность прогноза:</span><span class="sxs-lookup"><span data-stu-id="65bb7-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="65bb7-165">Функции</span><span class="sxs-lookup"><span data-stu-id="65bb7-165">Features</span></span>      | <span data-ttu-id="65bb7-166">Метка</span><span class="sxs-lookup"><span data-stu-id="65bb7-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="65bb7-167">Далее необходимо определить структуру данных для входного класса.</span><span class="sxs-lookup"><span data-stu-id="65bb7-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="65bb7-168">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="65bb7-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="65bb7-169">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите команду **Добавить > Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="65bb7-170">В диалоговом окне **Добавление нового элемента** выберите **Класс** и в поле **Имя** укажите *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="65bb7-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="65bb7-171">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="65bb7-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="65bb7-172">Файл *MovieRatingData.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="65bb7-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="65bb7-173">Добавьте следующий оператор `using` в начало файла *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="65bb7-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="65bb7-174">Создайте класс `MovieRating`, удалив из файла *MovieRatingData.cs* существующее определение класса и добавив следующий код:</span><span class="sxs-lookup"><span data-stu-id="65bb7-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](./snippets/movie-recommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="65bb7-175">`MovieRating` — это класс входных данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="65bb7-176">Атрибут [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) определяет столбцы в наборе данных, которые следует загрузить (по индексам).</span><span class="sxs-lookup"><span data-stu-id="65bb7-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="65bb7-177">Столбцы `userId` и `movieId` — это признаки `Features` (входные данные модели для прогнозирования метки `Label`), а столбец rating — это прогнозируемая метка `Label` (выходные данные модели).</span><span class="sxs-lookup"><span data-stu-id="65bb7-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="65bb7-178">Создайте еще один класс, `MovieRatingPrediction`, который будет представлять результаты прогнозирования. Для этого добавьте следующий код после класса `MovieRating` в файле *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="65bb7-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](./snippets/movie-recommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="65bb7-179">В файле *Program.cs* замените строку `Console.WriteLine("Hello World!")` в методе `Main()` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="65bb7-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](./snippets/movie-recommendation/csharp/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="65bb7-180">[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="65bb7-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="65bb7-181">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="65bb7-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="65bb7-182">После метода `Main()` создайте метод `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="65bb7-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="65bb7-183">Этот метод будет вызывать ошибку, пока вы не добавите оператор return при выполнении дальнейших инструкций.</span><span class="sxs-lookup"><span data-stu-id="65bb7-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="65bb7-184">Инициализируйте переменные, содержащие пути к данным, загрузите данные из файлов \*.csv и получите наборы данных `Train` и `Test` как объекты `IDataView`, добавив следующий код в метод `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="65bb7-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](./snippets/movie-recommendation/csharp/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="65bb7-185">Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="65bb7-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="65bb7-186">`IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые).</span><span class="sxs-lookup"><span data-stu-id="65bb7-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="65bb7-187">Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="65bb7-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="65bb7-188">Метод [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) определяет схему данных и считывает файл.</span><span class="sxs-lookup"><span data-stu-id="65bb7-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="65bb7-189">Он принимает переменные, содержащие пути к данным, и возвращает объект `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="65bb7-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="65bb7-190">В данном случае вы указываете пути к файлам `Test` и `Train`, а также заголовок текстового файла (чтобы использовались правильные имена столбцов) и разделитель данных в виде запятой (по умолчанию разделителем является символ табуляции).</span><span class="sxs-lookup"><span data-stu-id="65bb7-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="65bb7-191">Добавьте в метод `Main()` следующий код для вызова метода `LoadData()` и получения наборов данных `Train` и `Test`:</span><span class="sxs-lookup"><span data-stu-id="65bb7-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](./snippets/movie-recommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="65bb7-192">Создание и обучение модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-192">Build and train your model</span></span>

<span data-ttu-id="65bb7-193">Создайте метод `BuildAndTrainModel()` сразу после метода `LoadData()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="65bb7-193">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="65bb7-194">Этот метод будет вызывать ошибку, пока вы не добавите оператор return при выполнении дальнейших инструкций.</span><span class="sxs-lookup"><span data-stu-id="65bb7-194">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="65bb7-195">Определите преобразования данных, добавив в метод `BuildAndTrainModel()` следующий код:</span><span class="sxs-lookup"><span data-stu-id="65bb7-195">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](./snippets/movie-recommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="65bb7-196">Так как столбцы `userId` и `movieId` содержат индексы пользователей и фильмов, а не реальные значения, необходимо с помощью метода [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) преобразовать столбцы `userId` и `movieId` в столбцы признаков (`Feature`), содержащие числовые ключи (допустимый формат для алгоритмов рекомендаций), а затем добавить их в качестве новых столбцов наборов данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-196">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="65bb7-197">userId</span><span class="sxs-lookup"><span data-stu-id="65bb7-197">userId</span></span> | <span data-ttu-id="65bb7-198">movieId</span><span class="sxs-lookup"><span data-stu-id="65bb7-198">movieId</span></span> | <span data-ttu-id="65bb7-199">Метка</span><span class="sxs-lookup"><span data-stu-id="65bb7-199">Label</span></span> | <span data-ttu-id="65bb7-200">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="65bb7-200">userIdEncoded</span></span> | <span data-ttu-id="65bb7-201">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="65bb7-201">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="65bb7-202">1</span><span class="sxs-lookup"><span data-stu-id="65bb7-202">1</span></span> | <span data-ttu-id="65bb7-203">1</span><span class="sxs-lookup"><span data-stu-id="65bb7-203">1</span></span> | <span data-ttu-id="65bb7-204">4</span><span class="sxs-lookup"><span data-stu-id="65bb7-204">4</span></span> | <span data-ttu-id="65bb7-205">userKey1</span><span class="sxs-lookup"><span data-stu-id="65bb7-205">userKey1</span></span> | <span data-ttu-id="65bb7-206">movieKey1</span><span class="sxs-lookup"><span data-stu-id="65bb7-206">movieKey1</span></span> |
| <span data-ttu-id="65bb7-207">1</span><span class="sxs-lookup"><span data-stu-id="65bb7-207">1</span></span> | <span data-ttu-id="65bb7-208">3</span><span class="sxs-lookup"><span data-stu-id="65bb7-208">3</span></span> | <span data-ttu-id="65bb7-209">4</span><span class="sxs-lookup"><span data-stu-id="65bb7-209">4</span></span> | <span data-ttu-id="65bb7-210">userKey1</span><span class="sxs-lookup"><span data-stu-id="65bb7-210">userKey1</span></span> | <span data-ttu-id="65bb7-211">movieKey2</span><span class="sxs-lookup"><span data-stu-id="65bb7-211">movieKey2</span></span> |
| <span data-ttu-id="65bb7-212">1</span><span class="sxs-lookup"><span data-stu-id="65bb7-212">1</span></span> | <span data-ttu-id="65bb7-213">6</span><span class="sxs-lookup"><span data-stu-id="65bb7-213">6</span></span> | <span data-ttu-id="65bb7-214">4</span><span class="sxs-lookup"><span data-stu-id="65bb7-214">4</span></span> | <span data-ttu-id="65bb7-215">userKey1</span><span class="sxs-lookup"><span data-stu-id="65bb7-215">userKey1</span></span> | <span data-ttu-id="65bb7-216">movieKey3</span><span class="sxs-lookup"><span data-stu-id="65bb7-216">movieKey3</span></span> |

<span data-ttu-id="65bb7-217">Выберите алгоритм машинного обучения и добавьте его к определениям преобразований данных, добавив в метод `BuildAndTrainModel()` следующие строки кода:</span><span class="sxs-lookup"><span data-stu-id="65bb7-217">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](./snippets/movie-recommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="65bb7-218">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) — это алгоритм обучения для предоставления рекомендаций.</span><span class="sxs-lookup"><span data-stu-id="65bb7-218">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="65bb7-219">[Разложение матрицы](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) — стандартный подход к формированию рекомендаций при наличии данных о том, как пользователи оценивали продукты в прошлом, как в нашем случае.</span><span class="sxs-lookup"><span data-stu-id="65bb7-219">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="65bb7-220">Есть и другие алгоритмы рекомендаций, которые используются при наличии других данных (дополнительные сведения см. в. разделе [Другие алгоритмы рекомендаций](#other-recommendation-algorithms) ниже).</span><span class="sxs-lookup"><span data-stu-id="65bb7-220">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="65bb7-221">В данном случае алгоритм разложения матрицы (`Matrix Factorization`) использует метод, называемый "совместная фильтрация". Он основывается на том допущении, что если мнение двух людей по какому-либо вопросу совпадает, то и по другому вопросу они будут склонны иметь одинаковое мнение.</span><span class="sxs-lookup"><span data-stu-id="65bb7-221">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="65bb7-222">Например, если два пользователя одинаково оценили определенный фильм, то второму из них с большой вероятностью понравится другой фильм, который посмотрел и высоко оценил первый пользователь.</span><span class="sxs-lookup"><span data-stu-id="65bb7-222">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="65bb7-223">Пользователь 1</span><span class="sxs-lookup"><span data-stu-id="65bb7-223">User 1</span></span> | <span data-ttu-id="65bb7-224">Посмотрел фильм и поставил отметку "Нравится"</span><span class="sxs-lookup"><span data-stu-id="65bb7-224">Watched and liked movie</span></span> | <span data-ttu-id="65bb7-225">Посмотрел фильм и поставил отметку "Нравится"</span><span class="sxs-lookup"><span data-stu-id="65bb7-225">Watched and liked movie</span></span> | <span data-ttu-id="65bb7-226">Посмотрел фильм и поставил отметку "Нравится"</span><span class="sxs-lookup"><span data-stu-id="65bb7-226">Watched and liked movie</span></span> |
| <span data-ttu-id="65bb7-227">Пользователь 2</span><span class="sxs-lookup"><span data-stu-id="65bb7-227">User 2</span></span> | <span data-ttu-id="65bb7-228">Посмотрел фильм и поставил отметку "Нравится"</span><span class="sxs-lookup"><span data-stu-id="65bb7-228">Watched and liked movie</span></span> | <span data-ttu-id="65bb7-229">Посмотрел фильм и поставил отметку "Нравится"</span><span class="sxs-lookup"><span data-stu-id="65bb7-229">Watched and liked movie</span></span> | <span data-ttu-id="65bb7-230">Не смотрел фильм — РЕКОМЕНДОВАТЬ</span><span class="sxs-lookup"><span data-stu-id="65bb7-230">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="65bb7-231">Алгоритм разложения матрицы (`Matrix Factorization`) имеет ряд [параметров](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), о которых можно прочитать в разделе [Гиперпараметры алгоритма](#algorithm-hyperparameters) ниже.</span><span class="sxs-lookup"><span data-stu-id="65bb7-231">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="65bb7-232">Обучите модель на основе данных `Train` и получите обученную модель, добавив в метод `BuildAndTrainModel()` следующие строки кода:</span><span class="sxs-lookup"><span data-stu-id="65bb7-232">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](./snippets/movie-recommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="65bb7-233">Метод [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) обучает модель с помощью предоставленных наборов обучающих данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-233">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="65bb7-234">С технической точки зрения, он выполняет определения средств оценки (`Estimator`), преобразовывая данные и применяя алгоритм обучения, а затем возвращает обученную модель, то есть преобразователь (`Transformer`).</span><span class="sxs-lookup"><span data-stu-id="65bb7-234">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="65bb7-235">Дополнительные сведения о рабочем процессе обучения модели в ML.NET см. в статье [Что такое ML.NET и принципы работы этой системы](../how-does-mldotnet-work.md#code-workflow).</span><span class="sxs-lookup"><span data-stu-id="65bb7-235">For more information on the model training workflow in ML.NET, see [What is ML.NET and how does it work?](../how-does-mldotnet-work.md#code-workflow).</span></span>

<span data-ttu-id="65bb7-236">Добавьте в метод `Main()` следующую строку кода для вызова метода `BuildAndTrainModel()` и получения обученной модели:</span><span class="sxs-lookup"><span data-stu-id="65bb7-236">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](./snippets/movie-recommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="65bb7-237">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-237">Evaluate your model</span></span>

<span data-ttu-id="65bb7-238">После обучения модели оцените ее эффективность с помощью тестовых данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-238">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="65bb7-239">Создайте метод `EvaluateModel()` сразу после метода `BuildAndTrainModel()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="65bb7-239">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="65bb7-240">Преобразуйте данные `Test`, добавив в метод `EvaluateModel()` следующий код:</span><span class="sxs-lookup"><span data-stu-id="65bb7-240">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](./snippets/movie-recommendation/csharp/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="65bb7-241">Метод [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) делает прогнозы для нескольких входных строк тестового набора данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-241">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="65bb7-242">Оцените модель, добавив в метод `EvaluateModel()` следующую строку кода:</span><span class="sxs-lookup"><span data-stu-id="65bb7-242">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](./snippets/movie-recommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="65bb7-243">После получения прогноза метод [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) оценивает модель, сравнивая спрогнозированные значения с фактическими метками (`Labels`) в тестовом наборе данных, а затем возвращает метрики эффективности модели.</span><span class="sxs-lookup"><span data-stu-id="65bb7-243">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="65bb7-244">Чтобы вывести метрики оценки в консоль, добавьте в метод `EvaluateModel()` следующие строки кода:</span><span class="sxs-lookup"><span data-stu-id="65bb7-244">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](./snippets/movie-recommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="65bb7-245">Добавьте в метод `Main()` следующую строку кода для вызова метода `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="65bb7-245">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](./snippets/movie-recommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="65bb7-246">Теперь выходные данные должны выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="65bb7-246">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="65bb7-247">В этих выходных данных 20 итераций.</span><span class="sxs-lookup"><span data-stu-id="65bb7-247">In this output, there are 20 iterations.</span></span> <span data-ttu-id="65bb7-248">В каждой итерации мера погрешности уменьшается, приближаясь к 0.</span><span class="sxs-lookup"><span data-stu-id="65bb7-248">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="65bb7-249">`root of mean squared error` (RMS или RMSE) используется для измерения разницы между значениями, спрогнозированными моделью, и фактическими значениями в тестовом наборе данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-249">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="65bb7-250">С технической точки зрения она вычисляется как квадратный корень из среднего значения квадратов погрешностей.</span><span class="sxs-lookup"><span data-stu-id="65bb7-250">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="65bb7-251">Чем ниже это отклонение, тем лучше модель.</span><span class="sxs-lookup"><span data-stu-id="65bb7-251">The lower it is, the better the model is.</span></span>

<span data-ttu-id="65bb7-252">`R Squared` указывает, насколько хорошо данные соответствуют модели.</span><span class="sxs-lookup"><span data-stu-id="65bb7-252">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="65bb7-253">Значение находится в диапазоне от 0 до 1.</span><span class="sxs-lookup"><span data-stu-id="65bb7-253">Ranges from 0 to 1.</span></span> <span data-ttu-id="65bb7-254">Значение 0 означает, что данные случайные или по другим причинам не могут соответствовать модели.</span><span class="sxs-lookup"><span data-stu-id="65bb7-254">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="65bb7-255">Значение 1 означает, что модель идеально соответствует этим данным.</span><span class="sxs-lookup"><span data-stu-id="65bb7-255">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="65bb7-256">Значение `R Squared` должно быть максимально близко к 1.</span><span class="sxs-lookup"><span data-stu-id="65bb7-256">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="65bb7-257">Построение успешных моделей — итеративный процесс.</span><span class="sxs-lookup"><span data-stu-id="65bb7-257">Building successful models is an iterative process.</span></span> <span data-ttu-id="65bb7-258">Изначально эта модель имеет низкое качество, так как в руководстве используются небольшие наборы данных для быстрого обучения.</span><span class="sxs-lookup"><span data-stu-id="65bb7-258">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="65bb7-259">Если вам требуется модель более высокого качества, можно попытаться улучшить ее, использовав более крупные наборы данных для обучения или выбрав другие алгоритмы обучения с разными гиперпараметрами для каждого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="65bb7-259">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="65bb7-260">См. подробнее об [улучшении модели](#improve-your-model) в разделе ниже.</span><span class="sxs-lookup"><span data-stu-id="65bb7-260">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="65bb7-261">Использование модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-261">Use your model</span></span>

<span data-ttu-id="65bb7-262">Теперь обученную модель можно использовать для прогнозирования на основе новых данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-262">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="65bb7-263">Создайте метод `UseModelForSinglePrediction()` сразу после метода `EvaluateModel()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="65bb7-263">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="65bb7-264">Для прогнозирования оценки используйте класс `PredictionEngine`. Добавьте в метод `UseModelForSinglePrediction()` следующий код:</span><span class="sxs-lookup"><span data-stu-id="65bb7-264">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](./snippets/movie-recommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="65bb7-265">Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-265">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="65bb7-266">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="65bb7-266">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="65bb7-267">Допустимо использовать в средах прототипов или средах с одним потоком.</span><span class="sxs-lookup"><span data-stu-id="65bb7-267">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="65bb7-268">Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="65bb7-268">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="65bb7-269">См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="65bb7-269">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="65bb7-270">Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="65bb7-270">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="65bb7-271">Создайте экземпляр `MovieRating` с именем `testInput` и передайте его в PredictionEngine, добавив следующие строки кода в метод `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="65bb7-271">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](./snippets/movie-recommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="65bb7-272">Функция [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) создает прогноз по одному столбцу данных.</span><span class="sxs-lookup"><span data-stu-id="65bb7-272">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="65bb7-273">Затем по значению `Score` (спрогнозированная оценка) можно определить, следует ли рекомендовать фильм с movieId 10 пользователю 6.</span><span class="sxs-lookup"><span data-stu-id="65bb7-273">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="65bb7-274">Чем больше значение `Score`, тем выше вероятность того, что пользователю понравится определенный фильм.</span><span class="sxs-lookup"><span data-stu-id="65bb7-274">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="65bb7-275">В данном случае допустим, что нужно рекомендовать фильмы с прогнозируемой оценкой более 3,5.</span><span class="sxs-lookup"><span data-stu-id="65bb7-275">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="65bb7-276">Чтобы вывести результаты, добавьте в метод `UseModelForSinglePrediction()` следующие строки кода:</span><span class="sxs-lookup"><span data-stu-id="65bb7-276">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](./snippets/movie-recommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="65bb7-277">Добавьте в метод `Main()` следующую строку кода для вызова метода `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="65bb7-277">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](./snippets/movie-recommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="65bb7-278">Выходные данные этого метода должны выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="65bb7-278">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="65bb7-279">Сохранение модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-279">Save your model</span></span>

<span data-ttu-id="65bb7-280">Чтобы модель можно было использовать для прогнозирования в приложениях для конечных пользователей, ее нужно сохранить.</span><span class="sxs-lookup"><span data-stu-id="65bb7-280">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="65bb7-281">Создайте метод `SaveModel()` сразу после метода `UseModelForSinglePrediction()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="65bb7-281">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="65bb7-282">Сохраните обученную модель, добавив в метод `SaveModel()` следующую строку кода:</span><span class="sxs-lookup"><span data-stu-id="65bb7-282">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](./snippets/movie-recommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="65bb7-283">Этот метод сохраняет обученную модель в ZIP-файле (в папке Data), который затем можно использовать в других приложениях .NET.</span><span class="sxs-lookup"><span data-stu-id="65bb7-283">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="65bb7-284">Добавьте в метод `Main()` следующую строку кода для вызова метода `SaveModel()`:</span><span class="sxs-lookup"><span data-stu-id="65bb7-284">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](./snippets/movie-recommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="65bb7-285">Использование сохраненной модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-285">Use your saved model</span></span>

<span data-ttu-id="65bb7-286">После сохранения обученной модели ее можно использовать в различных средах.</span><span class="sxs-lookup"><span data-stu-id="65bb7-286">Once you have saved your trained model, you can consume the model in different environments.</span></span> <span data-ttu-id="65bb7-287">Дополнительные сведения об эксплуатации модели обучения обученной машины в приложениях см. в статье [Сохранение и загрузка обученных моделей](../how-to-guides/save-load-machine-learning-models-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="65bb7-287">See [Save and load trained models](../how-to-guides/save-load-machine-learning-models-ml-net.md) to learn how to operationalize a trained machine learning model in apps.</span></span>

## <a name="results"></a><span data-ttu-id="65bb7-288">Результаты</span><span class="sxs-lookup"><span data-stu-id="65bb7-288">Results</span></span>

<span data-ttu-id="65bb7-289">Выполнив описанные выше действия, запустите консольное приложение (CTRL+F5).</span><span class="sxs-lookup"><span data-stu-id="65bb7-289">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="65bb7-290">Результаты выполнения одного прогноза должны выглядеть примерно так, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="65bb7-290">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="65bb7-291">Кроме того, могут выводиться предупреждения или сообщения об обработке, но для удобства здесь мы убрали их.</span><span class="sxs-lookup"><span data-stu-id="65bb7-291">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="65bb7-292">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="65bb7-292">Congratulations!</span></span> <span data-ttu-id="65bb7-293">Вы успешно создали модель машинного обучения для рекомендации фильмов.</span><span class="sxs-lookup"><span data-stu-id="65bb7-293">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="65bb7-294">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).</span><span class="sxs-lookup"><span data-stu-id="65bb7-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="65bb7-295">Улучшение модели</span><span class="sxs-lookup"><span data-stu-id="65bb7-295">Improve your model</span></span>

<span data-ttu-id="65bb7-296">Повысить эффективность модели для получения более точных прогнозов можно несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="65bb7-296">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="65bb7-297">Данные</span><span class="sxs-lookup"><span data-stu-id="65bb7-297">Data</span></span>

<span data-ttu-id="65bb7-298">Чтобы повысить качество модели рекомендаций, можно дополнить обучающие данные для каждого пользователя и фильма.</span><span class="sxs-lookup"><span data-stu-id="65bb7-298">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="65bb7-299">[Перекрестная проверка](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) — это способ оценки моделей, при котором данные разделяются на части случайным образом, после чего некоторые части используются для обучения, а остальные — для тестирования.</span><span class="sxs-lookup"><span data-stu-id="65bb7-299">[Cross validation](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="65bb7-300">В плане качества модели такой метод лучше, чем фиксированное разделение общего набора на обучающие и тестовые данные, которое применялось в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="65bb7-300">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="65bb7-301">Функции</span><span class="sxs-lookup"><span data-stu-id="65bb7-301">Features</span></span>

<span data-ttu-id="65bb7-302">В этом руководстве использовались только три признака (`Features`) из набора данных (`user id`, `movie id` и `rating`).</span><span class="sxs-lookup"><span data-stu-id="65bb7-302">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="65bb7-303">Хотя для начала этого достаточно, на практике может потребоваться добавить дополнительные атрибуты или признаки `Features` (например, возраст, пол, географическое местоположение и другие).</span><span class="sxs-lookup"><span data-stu-id="65bb7-303">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="65bb7-304">Добавление релевантных признаков (`Features`) может помочь повысить эффективность модели рекомендаций.</span><span class="sxs-lookup"><span data-stu-id="65bb7-304">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="65bb7-305">Если вы не уверены, какие признаки (`Features`) являются наиболее релевантными для конкретной задачи машинного обучения, можно использовать специальные методы, предоставляемые платформой ML.NET с целью выявления наиболее весомых признаков (`Features`): определение вклада признака и [важность комбинаций признаков](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="65bb7-305">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="65bb7-306">Гиперпараметры алгоритма</span><span class="sxs-lookup"><span data-stu-id="65bb7-306">Algorithm hyperparameters</span></span>

<span data-ttu-id="65bb7-307">Алгоритмы, предоставляемые платформой ML.NET по умолчанию, достаточно эффективны, однако их можно еще более улучшить, настроив их [гиперпараметры](../resources/glossary.md#hyperparameter).</span><span class="sxs-lookup"><span data-stu-id="65bb7-307">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="65bb7-308">В случае с разложением матрицы (`Matrix Factorization`) можно поэкспериментировать с такими гиперпараметрами, как [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) и [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank).</span><span class="sxs-lookup"><span data-stu-id="65bb7-308">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="65bb7-309">Например, в этом учебнике алгоритм имеет следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="65bb7-309">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="65bb7-310">Другие алгоритмы рекомендаций</span><span class="sxs-lookup"><span data-stu-id="65bb7-310">Other Recommendation Algorithms</span></span>

<span data-ttu-id="65bb7-311">Алгоритм разложения матрицы с совместной фильтрацией — лишь один из подходов к рекомендации фильмов.</span><span class="sxs-lookup"><span data-stu-id="65bb7-311">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="65bb7-312">Зачастую данные по оценкам могут отсутствовать, то есть доступны только данные по просмотренным пользователями фильмам.</span><span class="sxs-lookup"><span data-stu-id="65bb7-312">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="65bb7-313">В других случаях могут быть доступны дополнительные данные.</span><span class="sxs-lookup"><span data-stu-id="65bb7-313">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="65bb7-314">Алгоритм</span><span class="sxs-lookup"><span data-stu-id="65bb7-314">Algorithm</span></span>       | <span data-ttu-id="65bb7-315">Сценарий</span><span class="sxs-lookup"><span data-stu-id="65bb7-315">Scenario</span></span>           | <span data-ttu-id="65bb7-316">Пример</span><span class="sxs-lookup"><span data-stu-id="65bb7-316">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="65bb7-317">Разложение матрицы одного класса</span><span class="sxs-lookup"><span data-stu-id="65bb7-317">One Class Matrix Factorization</span></span> | <span data-ttu-id="65bb7-318">Следует использовать при наличии только столбцов userId и movieId.</span><span class="sxs-lookup"><span data-stu-id="65bb7-318">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="65bb7-319">Такой тип рекомендаций предназначен для сценария совместных покупок, то есть покупателям будет рекомендоваться набор продуктов исходя из их истории заказов.</span><span class="sxs-lookup"><span data-stu-id="65bb7-319">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="65bb7-320">> Попробовать</span><span class="sxs-lookup"><span data-stu-id="65bb7-320">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="65bb7-321">Факторизационные машины с полями</span><span class="sxs-lookup"><span data-stu-id="65bb7-321">Field Aware Factorization Machines</span></span> | <span data-ttu-id="65bb7-322">Следует использовать для рекомендаций при наличии дополнительных признаков, помимо userId, productId и rating (таких как описание или цена продукта).</span><span class="sxs-lookup"><span data-stu-id="65bb7-322">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="65bb7-323">Этот алгоритм также использует метод совместной фильтрации.</span><span class="sxs-lookup"><span data-stu-id="65bb7-323">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="65bb7-324">> Попробовать</span><span class="sxs-lookup"><span data-stu-id="65bb7-324">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="65bb7-325">Проблема нового пользователя</span><span class="sxs-lookup"><span data-stu-id="65bb7-325">New user scenario</span></span>

<span data-ttu-id="65bb7-326">Одна из распространенных проблем при использовании совместной фильтрации — это проблема "холодного запуска", когда для нового пользователя еще нет данных, на основе которых можно было бы делать выводы.</span><span class="sxs-lookup"><span data-stu-id="65bb7-326">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="65bb7-327">Для ее решения новому пользователю часто предлагается создать профиль и, например, оценить фильмы, которые он уже видел.</span><span class="sxs-lookup"><span data-stu-id="65bb7-327">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="65bb7-328">Хотя такой подход требует некоторых усилий от пользователя, он позволяет получить начальные данные, на которые можно было бы опираться.</span><span class="sxs-lookup"><span data-stu-id="65bb7-328">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="65bb7-329">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="65bb7-329">Resources</span></span>

<span data-ttu-id="65bb7-330">В этом учебнике используются данные из [набора данных MovieLens](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="65bb7-330">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="65bb7-331">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="65bb7-331">Next steps</span></span>

<span data-ttu-id="65bb7-332">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="65bb7-332">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="65bb7-333">выбрать алгоритм машинного обучения;</span><span class="sxs-lookup"><span data-stu-id="65bb7-333">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="65bb7-334">подготовить и загрузить данные;</span><span class="sxs-lookup"><span data-stu-id="65bb7-334">Prepare and load your data</span></span>
> * <span data-ttu-id="65bb7-335">создать и обучить модель;</span><span class="sxs-lookup"><span data-stu-id="65bb7-335">Build and train a model</span></span>
> * <span data-ttu-id="65bb7-336">оценить модель;</span><span class="sxs-lookup"><span data-stu-id="65bb7-336">Evaluate a model</span></span>
> * <span data-ttu-id="65bb7-337">развернуть и использовать модель.</span><span class="sxs-lookup"><span data-stu-id="65bb7-337">Deploy and consume a model</span></span>

<span data-ttu-id="65bb7-338">Переходите к следующему руководству:</span><span class="sxs-lookup"><span data-stu-id="65bb7-338">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="65bb7-339">Анализ тональности</span><span class="sxs-lookup"><span data-stu-id="65bb7-339">Sentiment Analysis</span></span>](sentiment-analysis.md)
