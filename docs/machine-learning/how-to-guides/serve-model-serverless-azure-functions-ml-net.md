---
title: Развертывание модели в Функциях Azure
description: Использование модели машинного обучения ML.NET для анализа тональности и прогнозирования через Интернет с помощью Функций Azure
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 74a7a5b941596ba9fffc62ef87a01763937d88c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2020
ms.locfileid: "91608781"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="36ab2-103">Развертывание модели в Функциях Azure</span><span class="sxs-lookup"><span data-stu-id="36ab2-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="36ab2-104">Сведения о развертывании предварительно обученной модели машинного обучения ML.NET для создания прогнозов по протоколу HTTP через бессерверную среду Функций Azure.</span><span class="sxs-lookup"><span data-stu-id="36ab2-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="36ab2-105">В этом примере запускается предварительная версия службы `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="36ab2-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36ab2-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="36ab2-106">Prerequisites</span></span>

- <span data-ttu-id="36ab2-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленными рабочими нагрузками "Кроссплатформенная разработка .NET Core" и "Разработка для Azure".</span><span class="sxs-lookup"><span data-stu-id="36ab2-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" and "Azure development" workloads installed.</span></span>
- <span data-ttu-id="36ab2-108">[Средства Функций Azure](/azure/azure-functions/functions-develop-vs#check-your-tools-version).</span><span class="sxs-lookup"><span data-stu-id="36ab2-108">[Azure Functions Tools](/azure/azure-functions/functions-develop-vs#check-your-tools-version)</span></span>
- <span data-ttu-id="36ab2-109">PowerShell</span><span class="sxs-lookup"><span data-stu-id="36ab2-109">PowerShell</span></span>
- <span data-ttu-id="36ab2-110">Предварительно обученная модель.</span><span class="sxs-lookup"><span data-stu-id="36ab2-110">Pre-trained model.</span></span> <span data-ttu-id="36ab2-111">Используйте [учебник по анализу тональности ML.NET](../tutorials/sentiment-analysis.md), чтобы создать собственную модель, или скачайте эту [предварительно обученную модель машинного обучения для анализа тональности](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="36ab2-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="36ab2-112">Обзор примера для Функций Azure</span><span class="sxs-lookup"><span data-stu-id="36ab2-112">Azure Functions sample overview</span></span>

<span data-ttu-id="36ab2-113">В этом примере предоставляется приложение **триггера HTTP на языке C# для Функций Azure**, которое использует предварительно обученную модель двоичной классификации для выбора положительной или отрицательной тональности текста.</span><span class="sxs-lookup"><span data-stu-id="36ab2-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="36ab2-114">Функции Azure предоставляют простой способ выполнять небольшие фрагменты кода в большом масштабе для управляемой бессерверной облачной среды.</span><span class="sxs-lookup"><span data-stu-id="36ab2-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="36ab2-115">Код для этого примера можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="36ab2-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="36ab2-116">Создание проекта в Функциях Azure</span><span class="sxs-lookup"><span data-stu-id="36ab2-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="36ab2-117">Откройте Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="36ab2-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="36ab2-118">Выберите **Файл** > **Создать** > **Проект** в меню.</span><span class="sxs-lookup"><span data-stu-id="36ab2-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="36ab2-119">В диалоговом окне **Новый проект** щелкните узел **Visual C#** , а затем — **Облако**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="36ab2-120">Выберите шаблон проекта **Функции Azure**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="36ab2-121">В текстовое поле **Имя** введите SentimentAnalysisFunctionsApp и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="36ab2-122">В диалоговом окне **Новый проект** откройте раскрывающийся список над разделом с параметрами проекта и выберите **Функции Azure v2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="36ab2-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="36ab2-123">Затем щелкните проект **Триггер HTTP** и нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="36ab2-124">Создайте каталог с именем *MLModels* в папке проекта, чтобы сохранить модель:</span><span class="sxs-lookup"><span data-stu-id="36ab2-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="36ab2-125">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новая папка**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="36ab2-126">Введите MLModels и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="36ab2-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="36ab2-127">Установите **пакет NuGet для Microsoft.ML** версии **1.3.1**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="36ab2-128">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="36ab2-129">Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.ML**, выберите из списка этот пакет и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="36ab2-130">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="36ab2-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="36ab2-131">Установите **пакет NuGet Microsoft.Azure.Functions.Extensions**:</span><span class="sxs-lookup"><span data-stu-id="36ab2-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="36ab2-132">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="36ab2-133">Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.Azure.Functions.Extensions**, выберите из списка этот пакет и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="36ab2-134">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="36ab2-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="36ab2-135">Установите **пакет NuGet Microsoft.Extensions.ML** версии **0.15.1**:</span><span class="sxs-lookup"><span data-stu-id="36ab2-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="36ab2-136">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="36ab2-137">Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.Extensions.ML**, выберите из списка этот пакет и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="36ab2-138">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="36ab2-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="36ab2-139">Установите **пакет NuGet Microsoft.NET.Sdk.Functions** версии **1.0.31**:</span><span class="sxs-lookup"><span data-stu-id="36ab2-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.31**:</span></span>

    <span data-ttu-id="36ab2-140">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="36ab2-141">Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Установленные", выполните поиск по фразе **Microsoft.NET.Sdk.Functions**, выберите из списка этот пакет, выберите в раскрывающемся списке "Версия" значение **1.0.31**, а затем нажмите кнопку **Обновить**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.31** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="36ab2-142">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="36ab2-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="36ab2-143">Добавление предварительно обученной модели в проект</span><span class="sxs-lookup"><span data-stu-id="36ab2-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="36ab2-144">Скопируйте предварительно созданную модель в папку *MLModels*.</span><span class="sxs-lookup"><span data-stu-id="36ab2-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="36ab2-145">В обозревателе решений щелкните правой кнопкой мыши файл предварительно созданной модели и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="36ab2-146">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="36ab2-147">Создание функции Azure для анализа тональности</span><span class="sxs-lookup"><span data-stu-id="36ab2-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="36ab2-148">Создайте класс для прогнозирования тональности.</span><span class="sxs-lookup"><span data-stu-id="36ab2-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="36ab2-149">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="36ab2-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="36ab2-150">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="36ab2-151">В диалоговом окне **Добавление нового элемента** выберите **Функция Azure** и измените значение поля **Имя** на *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="36ab2-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="36ab2-152">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="36ab2-153">В диалоговом окне **Новая функция Azure** щелкните **Триггер HTTP**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="36ab2-154">Затем нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="36ab2-155">В редакторе кода откроется файл *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="36ab2-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="36ab2-156">Добавьте следующий оператор `using` в начало файла *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="36ab2-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="36ab2-157">По умолчанию класс `AnalyzeSentiment` — `static`.</span><span class="sxs-lookup"><span data-stu-id="36ab2-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="36ab2-158">Удалите ключевое слово `static` из объявления класса.</span><span class="sxs-lookup"><span data-stu-id="36ab2-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="36ab2-159">Создание моделей данных</span><span class="sxs-lookup"><span data-stu-id="36ab2-159">Create data models</span></span>

<span data-ttu-id="36ab2-160">Вам потребуется создать несколько классов для входных данных и прогнозов.</span><span class="sxs-lookup"><span data-stu-id="36ab2-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="36ab2-161">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="36ab2-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="36ab2-162">Создайте каталог с именем *DataModels* в папке проекта, чтобы сохранить в нем модели данных: В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Добавить > Новая папка**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="36ab2-163">Введите DataModels и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="36ab2-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="36ab2-164">В обозревателе решений щелкните правой кнопкой мыши папку *DataModels* и выберите **Добавить > Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="36ab2-165">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="36ab2-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="36ab2-166">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="36ab2-167">Файл *SentimentData.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="36ab2-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="36ab2-168">Добавьте в начало файла *SentimentData.cs* следующий оператор using:</span><span class="sxs-lookup"><span data-stu-id="36ab2-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="36ab2-169">Удалите из файла *SentimentData.cs* существующее определение класса и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="36ab2-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="36ab2-170">В обозревателе решений щелкните правой кнопкой мыши папку *DataModels* и выберите **Добавить > Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="36ab2-171">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="36ab2-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="36ab2-172">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-172">Then, select the **Add** button.</span></span> <span data-ttu-id="36ab2-173">В редакторе кода откроется файл *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="36ab2-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="36ab2-174">Добавьте в начало файла *SentimentPrediction.cs* следующий оператор using:</span><span class="sxs-lookup"><span data-stu-id="36ab2-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="36ab2-175">Удалите из файла *SentimentPrediction.cs* существующее определение класса и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="36ab2-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="36ab2-176">`SentimentPrediction` наследует от `SentimentData`, который обеспечивает доступ к исходным данным в свойстве `SentimentText`, а также выходным данным модели.</span><span class="sxs-lookup"><span data-stu-id="36ab2-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="36ab2-177">Регистрация службы PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="36ab2-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="36ab2-178">Для формирования одного прогноза необходимо создать [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="36ab2-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="36ab2-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="36ab2-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="36ab2-180">Кроме того, необходимо создать его экземпляр везде, где он понадобится в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="36ab2-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="36ab2-181">По мере увеличения размера приложения этот процесс может стать неуправляемым.</span><span class="sxs-lookup"><span data-stu-id="36ab2-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="36ab2-182">Для улучшенной производительности и потокобезопасности используйте сочетание внедрения зависимостей и службы `PredictionEnginePool`, которое создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="36ab2-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="36ab2-183">См. дополнительные сведения о [внедрении зависимостей](https://en.wikipedia.org/wiki/Dependency_injection) по следующей ссылке.</span><span class="sxs-lookup"><span data-stu-id="36ab2-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="36ab2-184">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="36ab2-185">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="36ab2-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="36ab2-186">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="36ab2-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="36ab2-187">Добавьте в начало файла *Startup.cs* следующие операторы using:</span><span class="sxs-lookup"><span data-stu-id="36ab2-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="36ab2-188">Удалите существующий код ниже инструкций using и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="36ab2-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="36ab2-189">Определите в классе `Startup` переменные для хранения среды, в которой выполняется приложение, и путь к файлу, в котором находится модель.</span><span class="sxs-lookup"><span data-stu-id="36ab2-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="36ab2-190">Ниже показано, как создать конструктор для задания значений переменных `_environment` и `_modelPath`.</span><span class="sxs-lookup"><span data-stu-id="36ab2-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="36ab2-191">При локальном запуске приложения средой по умолчанию считается среда *Development* (Разработка).</span><span class="sxs-lookup"><span data-stu-id="36ab2-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="36ab2-192">Затем добавьте под конструктором новый метод с именем `Configure`, который будет регистрировать службу `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="36ab2-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="36ab2-193">Вкратце, этот код инициализирует объекты и службы автоматически для использования в дальнейшем по запросу приложения, вместо того чтобы вы делали это вручную.</span><span class="sxs-lookup"><span data-stu-id="36ab2-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="36ab2-194">Модели машинного обучения не являются статическими.</span><span class="sxs-lookup"><span data-stu-id="36ab2-194">Machine learning models are not static.</span></span> <span data-ttu-id="36ab2-195">По мере появления новых данных для обучения модель переобучается и развертывается повторно.</span><span class="sxs-lookup"><span data-stu-id="36ab2-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="36ab2-196">Одним из способов получения последней версии модели в приложении является повторное развертывание всего приложения.</span><span class="sxs-lookup"><span data-stu-id="36ab2-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="36ab2-197">Однако это приводит к простою приложения.</span><span class="sxs-lookup"><span data-stu-id="36ab2-197">However, this introduces application downtime.</span></span> <span data-ttu-id="36ab2-198">Служба `PredictionEnginePool` предоставляет механизм перезагрузки обновленной модели без отключения приложения.</span><span class="sxs-lookup"><span data-stu-id="36ab2-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="36ab2-199">Задайте для параметра `watchForChanges` значение `true`. В таком случае `PredictionEnginePool` запустит объект [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher), который прослушивает уведомления об изменениях файловой системы и вызывает события при изменении файла.</span><span class="sxs-lookup"><span data-stu-id="36ab2-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="36ab2-200">При наличии изменений `PredictionEnginePool` автоматически перезагружает модель.</span><span class="sxs-lookup"><span data-stu-id="36ab2-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="36ab2-201">Модель определяется параметром `modelName`, поэтому при изменении может быть перезагружено несколько моделей на одно приложение.</span><span class="sxs-lookup"><span data-stu-id="36ab2-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="36ab2-202">Кроме того, можно использовать метод `FromUri` при работе с моделями, сохраненными удаленно.</span><span class="sxs-lookup"><span data-stu-id="36ab2-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="36ab2-203">Вместо наблюдения за событиями изменения файлов `FromUri` опрашивает удаленное расположение на предмет изменений.</span><span class="sxs-lookup"><span data-stu-id="36ab2-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="36ab2-204">Интервал опроса по умолчанию равен 5 минутам.</span><span class="sxs-lookup"><span data-stu-id="36ab2-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="36ab2-205">Вы можете увеличить или уменьшить интервал опроса в зависимости от требований вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="36ab2-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="36ab2-206">В приведенном ниже примере кода `PredictionEnginePool` опрашивает модель, сохраненную по указанному универсальному коду ресурса (URI), каждую минуту.</span><span class="sxs-lookup"><span data-stu-id="36ab2-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="36ab2-207">Загрузка модели в функцию</span><span class="sxs-lookup"><span data-stu-id="36ab2-207">Load the model into the function</span></span>

<span data-ttu-id="36ab2-208">Вставьте следующий код внутри класса *AnalyzeSentiment*:</span><span class="sxs-lookup"><span data-stu-id="36ab2-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="36ab2-209">Этот код назначает `PredictionEnginePool`, передав его в конструктор функции, который можно получить путем внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="36ab2-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="36ab2-210">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="36ab2-210">Use the model to make predictions</span></span>

<span data-ttu-id="36ab2-211">Замените существующую реализацию метода *запуска* в классе *AnalyzeSentiment* следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="36ab2-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="36ab2-212">Когда метод `Run` выполняется, входящие данные из HTTP-запроса десериализуются и используются в качестве входных данных для `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="36ab2-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="36ab2-213">Затем метод `Predict` вызывается для формирования прогнозов с использованием модели `SentimentAnalysisModel`, зарегистрированной в классе `Startup`, и возвращает результаты пользователю в случае успеха.</span><span class="sxs-lookup"><span data-stu-id="36ab2-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="36ab2-214">Локальное тестирование</span><span class="sxs-lookup"><span data-stu-id="36ab2-214">Test locally</span></span>

<span data-ttu-id="36ab2-215">Завершив настройку параметров, протестируйте приложение:</span><span class="sxs-lookup"><span data-stu-id="36ab2-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="36ab2-216">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="36ab2-216">Run the application</span></span>
1. <span data-ttu-id="36ab2-217">Откройте PowerShell и введите код в командной строке, где PORT — это порт, через который работает приложение.</span><span class="sxs-lookup"><span data-stu-id="36ab2-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="36ab2-218">Как правило, используется порт 7071.</span><span class="sxs-lookup"><span data-stu-id="36ab2-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="36ab2-219">В случае успешного выполнения результат должен выглядеть, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="36ab2-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="36ab2-220">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="36ab2-220">Congratulations!</span></span> <span data-ttu-id="36ab2-221">Вы успешно использовали модель для прогнозирования через Интернет с помощью Функций Azure.</span><span class="sxs-lookup"><span data-stu-id="36ab2-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="36ab2-222">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="36ab2-222">Next Steps</span></span>

- [<span data-ttu-id="36ab2-223">Развертывание в Azure</span><span class="sxs-lookup"><span data-stu-id="36ab2-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
