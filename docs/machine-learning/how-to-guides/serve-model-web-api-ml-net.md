---
title: Развертывание модели в веб-API ASP.NET Core
description: Использование модели машинного обучения ML.NET для анализа тональности через Интернет с помощью веб-API ASP.NET Core
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 1d05bc0ac6a874d539794d81fd742d973724dbef
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874138"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="71b0a-103">Развертывание модели в веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="71b0a-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="71b0a-104">Узнайте, как использовать предварительно обученную модель машинного обучения ML.NET через интернет с помощью веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="71b0a-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="71b0a-105">Обслуживание модели через веб-API позволяет формировать прогнозы с помощью стандартных методов HTTP.</span><span class="sxs-lookup"><span data-stu-id="71b0a-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="71b0a-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="71b0a-106">Prerequisites</span></span>

- <span data-ttu-id="71b0a-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="71b0a-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="71b0a-108">PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71b0a-108">PowerShell.</span></span>
- <span data-ttu-id="71b0a-109">Предварительно обученная модель.</span><span class="sxs-lookup"><span data-stu-id="71b0a-109">Pre-trained model.</span></span> <span data-ttu-id="71b0a-110">Используйте [учебник по анализу тональности ML.NET](../tutorials/sentiment-analysis.md), чтобы создать собственную модель, или скачайте эту [предварительно обученную модель машинного обучения для анализа тональности](https://github.com/dotnet/samples/blob/main/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="71b0a-110">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/main/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="71b0a-111">Создание проекта веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="71b0a-111">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="71b0a-112">Откройте Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="71b0a-112">Open Visual Studio 2017.</span></span> <span data-ttu-id="71b0a-113">В меню выберите **Файл > Новый > Проект**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-113">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="71b0a-114">В диалоговом окне "Новый проект" щелкните узел **Visual C#** , а затем — **Веб**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-114">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="71b0a-115">Затем, выберите шаблон проекта **Веб-приложение ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-115">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="71b0a-116">В текстовое поле **Имя** введите SentimentAnalysisWebAPI и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-116">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="71b0a-117">В окне с разными типами проектов ASP.NET Core выберите **API** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-117">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="71b0a-118">Создайте каталог с именем *MLModels* в папке проекта, чтобы сохранить предварительно созданные файлы модели машинного обучения:</span><span class="sxs-lookup"><span data-stu-id="71b0a-118">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="71b0a-119">В обозревателе решений щелкните проект правой кнопкой мыши и выберите "Добавить" > "Новая папка".</span><span class="sxs-lookup"><span data-stu-id="71b0a-119">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="71b0a-120">Введите MLModels и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="71b0a-120">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="71b0a-121">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="71b0a-121">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="71b0a-122">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-122">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="71b0a-123">Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.ML**, выберите из списка этот пакет и нажмите кнопку "Установить".</span><span class="sxs-lookup"><span data-stu-id="71b0a-123">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="71b0a-124">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**. Затем нажмите кнопку **Принимаю** в диалоговом окне "Принятие условий лицензионного соглашения", если вы согласны с условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="71b0a-124">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="71b0a-125">Установите **пакет NuGet для Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="71b0a-125">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="71b0a-126">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-126">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="71b0a-127">Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.Extensions.ML**, выберите из списка этот пакет и нажмите кнопку "Установить".</span><span class="sxs-lookup"><span data-stu-id="71b0a-127">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="71b0a-128">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**. Затем нажмите кнопку **Принимаю** в диалоговом окне "Принятие условий лицензионного соглашения", если вы согласны с условиями лицензионного соглашения для выбранных пакетов.</span><span class="sxs-lookup"><span data-stu-id="71b0a-128">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="71b0a-129">Добавление модели в проект веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="71b0a-129">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="71b0a-130">Скопируйте предварительно созданную модель в каталог *MLModels*.</span><span class="sxs-lookup"><span data-stu-id="71b0a-130">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="71b0a-131">В обозревателе решений щелкните правой кнопкой мыши ZIP-файл модели и выберите пункт "Свойства".</span><span class="sxs-lookup"><span data-stu-id="71b0a-131">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="71b0a-132">В разделе "Дополнительно" для параметра "Копировать в выходной каталог" установите значение "Копировать более позднюю версию".</span><span class="sxs-lookup"><span data-stu-id="71b0a-132">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="71b0a-133">Создание моделей данных</span><span class="sxs-lookup"><span data-stu-id="71b0a-133">Create data models</span></span>

<span data-ttu-id="71b0a-134">Вам потребуется создать несколько классов для входных данных и прогнозов.</span><span class="sxs-lookup"><span data-stu-id="71b0a-134">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="71b0a-135">Добавьте в проект новый класс:</span><span class="sxs-lookup"><span data-stu-id="71b0a-135">Add a new class to your project:</span></span>

1. <span data-ttu-id="71b0a-136">Создайте каталог с именем *DataModels* в папке проекта, чтобы сохранить в нем модели данных:</span><span class="sxs-lookup"><span data-stu-id="71b0a-136">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="71b0a-137">В обозревателе решений щелкните проект правой кнопкой мыши и выберите "Добавить" > "Новая папка".</span><span class="sxs-lookup"><span data-stu-id="71b0a-137">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="71b0a-138">Введите DataModels и нажмите клавишу **ВВОД**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-138">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="71b0a-139">В обозревателе решений щелкните правой кнопкой мыши папку *DataModels* и выберите "Добавить" > "Новый элемент".</span><span class="sxs-lookup"><span data-stu-id="71b0a-139">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="71b0a-140">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="71b0a-140">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="71b0a-141">Теперь нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-141">Then, select the **Add** button.</span></span> <span data-ttu-id="71b0a-142">Файл *SentimentData.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="71b0a-142">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="71b0a-143">Добавьте в начало файла *SentimentData.cs* следующий оператор using:</span><span class="sxs-lookup"><span data-stu-id="71b0a-143">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="71b0a-144">Удалите из файла **SentimentData.cs** существующее определение класса и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="71b0a-144">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="71b0a-145">В обозревателе решений щелкните правой кнопкой мыши папку *DataModels* и выберите **Добавить > Новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-145">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="71b0a-146">В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="71b0a-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="71b0a-147">Теперь нажмите кнопку "Добавить".</span><span class="sxs-lookup"><span data-stu-id="71b0a-147">Then, select the Add button.</span></span> <span data-ttu-id="71b0a-148">В редакторе кода откроется файл *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="71b0a-148">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="71b0a-149">Добавьте в начало файла *SentimentPrediction.cs* следующий оператор using:</span><span class="sxs-lookup"><span data-stu-id="71b0a-149">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="71b0a-150">Удалите из файла *SentimentPrediction.cs* существующее определение класса и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="71b0a-150">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="71b0a-151">Тип`SentimentPrediction` наследуется от типа `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="71b0a-151">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="71b0a-152">Это упрощает просмотр исходных данных в свойстве `SentimentText`, а также выходных данных модели.</span><span class="sxs-lookup"><span data-stu-id="71b0a-152">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="71b0a-153">Регистрация класса PredictionEnginePool для использования в приложении</span><span class="sxs-lookup"><span data-stu-id="71b0a-153">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="71b0a-154">Для формирования одного прогноза необходимо создать [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="71b0a-154">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="71b0a-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="71b0a-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="71b0a-156">Кроме того, необходимо создать его экземпляр везде, где он понадобится в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="71b0a-156">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="71b0a-157">По мере увеличения размера приложения этот процесс может стать неуправляемым.</span><span class="sxs-lookup"><span data-stu-id="71b0a-157">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="71b0a-158">Для улучшенной производительности и потокобезопасности используйте сочетание внедрения зависимостей и службы `PredictionEnginePool`, которое создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="71b0a-158">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="71b0a-159">См. дополнительные сведения о [внедрении зависимостей в ASP.NET Core](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="71b0a-159">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="71b0a-160">Откройте класс *Startup.cs* и добавьте в начало файла следующий оператор using:</span><span class="sxs-lookup"><span data-stu-id="71b0a-160">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="71b0a-161">Добавьте в метод *ConfigureServices* следующий код:</span><span class="sxs-lookup"><span data-stu-id="71b0a-161">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

<span data-ttu-id="71b0a-162">Вкратце, этот код инициализирует объекты и службы автоматически для использования в дальнейшем по запросу приложения, вместо того чтобы вы делали это вручную.</span><span class="sxs-lookup"><span data-stu-id="71b0a-162">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="71b0a-163">Модели машинного обучения не являются статическими.</span><span class="sxs-lookup"><span data-stu-id="71b0a-163">Machine learning models are not static.</span></span> <span data-ttu-id="71b0a-164">По мере появления новых данных для обучения модель переобучается и развертывается повторно.</span><span class="sxs-lookup"><span data-stu-id="71b0a-164">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="71b0a-165">Одним из способов получения последней версии модели в приложении является повторное развертывание всего приложения.</span><span class="sxs-lookup"><span data-stu-id="71b0a-165">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="71b0a-166">Однако это приводит к простою приложения.</span><span class="sxs-lookup"><span data-stu-id="71b0a-166">However, this introduces application downtime.</span></span> <span data-ttu-id="71b0a-167">Служба `PredictionEnginePool` предоставляет механизм перезагрузки обновленной модели без отключения приложения.</span><span class="sxs-lookup"><span data-stu-id="71b0a-167">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="71b0a-168">Задайте для параметра `watchForChanges` значение `true`. В таком случае `PredictionEnginePool` запустит объект [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher), который прослушивает уведомления об изменениях файловой системы и вызывает события при изменении файла.</span><span class="sxs-lookup"><span data-stu-id="71b0a-168">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="71b0a-169">При наличии изменений `PredictionEnginePool` автоматически перезагружает модель.</span><span class="sxs-lookup"><span data-stu-id="71b0a-169">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="71b0a-170">Модель определяется параметром `modelName`, поэтому при изменении может быть перезагружено несколько моделей на одно приложение.</span><span class="sxs-lookup"><span data-stu-id="71b0a-170">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="71b0a-171">Кроме того, можно использовать метод `FromUri` при работе с моделями, сохраненными удаленно.</span><span class="sxs-lookup"><span data-stu-id="71b0a-171">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="71b0a-172">Вместо наблюдения за событиями изменения файлов `FromUri` опрашивает удаленное расположение на предмет изменений.</span><span class="sxs-lookup"><span data-stu-id="71b0a-172">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="71b0a-173">Интервал опроса по умолчанию равен 5 минутам.</span><span class="sxs-lookup"><span data-stu-id="71b0a-173">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="71b0a-174">Вы можете увеличить или уменьшить интервал опроса в зависимости от требований вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="71b0a-174">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="71b0a-175">В приведенном ниже примере кода `PredictionEnginePool` опрашивает модель, сохраненную по указанному универсальному коду ресурса (URI), каждую минуту.</span><span class="sxs-lookup"><span data-stu-id="71b0a-175">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/main/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="71b0a-176">Создание контроллера прогнозирования</span><span class="sxs-lookup"><span data-stu-id="71b0a-176">Create Predict controller</span></span>

<span data-ttu-id="71b0a-177">Для обработки входящих HTTP-запросов создайте контроллер.</span><span class="sxs-lookup"><span data-stu-id="71b0a-177">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="71b0a-178">В обозревателе решений щелкните правой кнопкой мыши папку *Контроллеры* и выберите **Добавить > Контроллер**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-178">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="71b0a-179">В диалоговом окне **Добавление нового элемента** щелкните **Пустой контроллер API** и нажмите **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="71b0a-179">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="71b0a-180">В запросе измените поле **Имя контроллера** на *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="71b0a-180">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="71b0a-181">Теперь нажмите кнопку "Добавить".</span><span class="sxs-lookup"><span data-stu-id="71b0a-181">Then, select the Add button.</span></span> <span data-ttu-id="71b0a-182">Файл *PredictController.cs* откроется в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="71b0a-182">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="71b0a-183">Добавьте в начало файла *PredictController.cs* следующий оператор using.</span><span class="sxs-lookup"><span data-stu-id="71b0a-183">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="71b0a-184">Удалите из файла *PredictController.cs* существующее определение класса и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="71b0a-184">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="71b0a-185">Этот код назначает класс `PredictionEnginePool`, передав его в конструктор контроллера, который можно получить путем внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="71b0a-185">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="71b0a-186">Затем метод `Post` контроллера `Predict` использует `PredictionEnginePool` для формирования прогнозов с помощью модели `SentimentAnalysisModel`, зарегистрированной в классе `Startup`, и возвращает результаты пользователю в случае успеха.</span><span class="sxs-lookup"><span data-stu-id="71b0a-186">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="71b0a-187">Тестирование веб-API на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="71b0a-187">Test web API locally</span></span>

<span data-ttu-id="71b0a-188">Завершив настройку параметров, протестируйте приложение:</span><span class="sxs-lookup"><span data-stu-id="71b0a-188">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="71b0a-189">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="71b0a-189">Run the application.</span></span>
1. <span data-ttu-id="71b0a-190">Откройте PowerShell и введите следующий код, где PORT — это порт, который прослушивается приложением.</span><span class="sxs-lookup"><span data-stu-id="71b0a-190">Open PowerShell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="71b0a-191">В случае успешного выполнения результат должен выглядеть, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="71b0a-191">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="71b0a-192">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="71b0a-192">Congratulations!</span></span> <span data-ttu-id="71b0a-193">Вы успешно использовали модель для прогнозирования через Интернет с помощью веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="71b0a-193">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="71b0a-194">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="71b0a-194">Next Steps</span></span>

- [<span data-ttu-id="71b0a-195">Развертывание в Azure</span><span class="sxs-lookup"><span data-stu-id="71b0a-195">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
