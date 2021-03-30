---
title: Учебник. Анализ тональности (двоичная классификация)
description: В этом руководстве показано, как создать консольное приложение Razor Pages, которое определяет тональность комментариев на веб-сайте, и предпринимает соответствующие действия. Двоичный классификатор тональности использует построитель моделей в Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: cb4f18ad9da2e57ee09598183a1226b20a1d7aec
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874619"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="d6b1d-104">Учебник. Анализ тональности комментариев на веб-сайте в веб-приложении с помощью построителя моделей ML.NET</span><span class="sxs-lookup"><span data-stu-id="d6b1d-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="d6b1d-105">Узнайте, как анализировать тональность комментариев в реальном времени в веб-приложении.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-105">Learn how to analyze sentiment from comments in real time inside a web application.</span></span>

<span data-ttu-id="d6b1d-106">В этом руководстве показано, как создать приложение ASP.NET Razor Pages, которое определяет тональность комментариев на веб-сайте в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real time.</span></span>

<span data-ttu-id="d6b1d-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d6b1d-108">Создание приложения Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6b1d-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="d6b1d-109">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="d6b1d-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="d6b1d-110">Выбор сценария</span><span class="sxs-lookup"><span data-stu-id="d6b1d-110">Choose a scenario</span></span>
> - <span data-ttu-id="d6b1d-111">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="d6b1d-111">Load the data</span></span>
> - <span data-ttu-id="d6b1d-112">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="d6b1d-112">Train the model</span></span>
> - <span data-ttu-id="d6b1d-113">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="d6b1d-113">Evaluate the model</span></span>
> - <span data-ttu-id="d6b1d-114">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="d6b1d-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="d6b1d-115">Построитель моделей в настоящее время находится на этапе предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="d6b1d-116">Исходный код для этого руководства можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples).</span><span class="sxs-lookup"><span data-stu-id="d6b1d-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="d6b1d-117">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="d6b1d-117">Pre-requisites</span></span>

<span data-ttu-id="d6b1d-118">Список необходимых условий и инструкции по установке см. в [руководстве по установке построителя моделей](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="d6b1d-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="d6b1d-119">Создание приложения Razor Pages</span><span class="sxs-lookup"><span data-stu-id="d6b1d-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="d6b1d-120">Создайте **приложение ASP.NET Core Razor Pages**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="d6b1d-121">Откройте Visual Studio и выберите **Файл > Создать > Проект** в строке меню.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="d6b1d-122">В диалоговом окне "Новый проект" щелкните узел **Visual C#** , а затем — **Веб**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="d6b1d-123">Затем, выберите шаблон проекта **Веб-приложение ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="d6b1d-124">В текстовом поле **Имя** введите SentimentRazor.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="d6b1d-125">Убедитесь, что флажок **Поместить решение и проект в одной папке** **снят** (VS 2019) или флажок **Создать каталог для решения** **установлен** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="d6b1d-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="d6b1d-126">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="d6b1d-127">Выберите **Web Application** (Веб-приложение) в окне с разными типами проектов ASP.NET Core и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="d6b1d-128">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="d6b1d-128">Prepare and understand the data</span></span>

<span data-ttu-id="d6b1d-129">Скачайте [набор данных Wikipedia Detox](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="d6b1d-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="d6b1d-130">Щелкните открывшуюся веб-страницу правой кнопкой мыши, выберите **Сохранить как** и сохраните файл на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="d6b1d-131">Каждая строка в наборе данных *wikipedia-detox-250-line-data.tsv* содержит сообщение, оставленное пользователем Википедии.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="d6b1d-132">Первый столбец представляет тональность текста (0 — нетоксичный, 1 — токсичный), а второй столбец включает сам комментарий, оставленный пользователем.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="d6b1d-133">Столбцы разделены пробелами.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-133">The columns are separated by tabs.</span></span> <span data-ttu-id="d6b1d-134">Данные выглядят так:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-134">The data looks like the following:</span></span>

| <span data-ttu-id="d6b1d-135">Тональность</span><span class="sxs-lookup"><span data-stu-id="d6b1d-135">Sentiment</span></span> | <span data-ttu-id="d6b1d-136">SentimentText</span><span class="sxs-lookup"><span data-stu-id="d6b1d-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="d6b1d-137">1</span><span class="sxs-lookup"><span data-stu-id="d6b1d-137">1</span></span> | <span data-ttu-id="d6b1d-138">==RUDE== Мужик давай не начинай, просто загрузи обратно эту картинку.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="d6b1d-139">1</span><span class="sxs-lookup"><span data-stu-id="d6b1d-139">1</span></span> | <span data-ttu-id="d6b1d-140">==OK!</span><span class="sxs-lookup"><span data-stu-id="d6b1d-140">== OK!</span></span> <span data-ttu-id="d6b1d-141">==Я ЩАС WILD ONES WIKI ПОЛОЖУ!!!</span><span class="sxs-lookup"><span data-stu-id="d6b1d-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="d6b1d-142">0</span><span class="sxs-lookup"><span data-stu-id="d6b1d-142">0</span></span> | <span data-ttu-id="d6b1d-143">Надеюсь, это поможет.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="d6b1d-144">Выбор сценария</span><span class="sxs-lookup"><span data-stu-id="d6b1d-144">Choose a scenario</span></span>

![Мастер построителя моделей в Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="d6b1d-146">Чтобы обучить модель, нужно выбрать один из доступных сценариев машинного обучения в построителе моделей.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="d6b1d-147">В **обозревателе решений** щелкните правой кнопкой мыши проект *SentimentRazor* и выберите **Добавить** > **Машинное обучение**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="d6b1d-148">В этом примере сценарий включает анализ тональности.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="d6b1d-149">На шаге *Сценарий* средства построителя моделей выберите сценарий **Анализ тональности**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="d6b1d-150">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="d6b1d-150">Load the data</span></span>

<span data-ttu-id="d6b1d-151">Построитель моделей принимает данные из двух источников: базы данных SQL Server или локального файла в формате `csv` или `tsv`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="d6b1d-152">На этапе добавления данных выберите в раскрывающемся списке источников данных пункт **Прогнозирование цен**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="d6b1d-153">Нажмите кнопку рядом с текстовым полем **Выберите файл** и щелкните в проводнике файл *wikipedia-detox-250-line-data.tsv*.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="d6b1d-154">Выберите **Тональность** в раскрывающемся списке **Метка для прогнозирования (или столбец)** .</span><span class="sxs-lookup"><span data-stu-id="d6b1d-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="d6b1d-155">Оставьте значения по умолчанию для раскрывающегося списка **Входные столбцы (компоненты)** .</span><span class="sxs-lookup"><span data-stu-id="d6b1d-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="d6b1d-156">Щелкните ссылку **Обучение**, чтобы перейти к следующему шагу в средстве построителя моделей.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="d6b1d-157">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="d6b1d-157">Train the model</span></span>

<span data-ttu-id="d6b1d-158">Задачей машинного обучения, используемой в этом руководстве для обучения модели анализа тональности, является бинарная классификация.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="d6b1d-159">В процессе обучения построитель моделей обучает отдельные модели с помощью различных алгоритмов и параметров бинарной классификации, определяя оптимальную модель для вашего набора данных.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="d6b1d-160">Время, требуемое для обучения модели, пропорционально объему данных.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="d6b1d-161">Построитель моделей автоматически выбирает значение по умолчанию для параметра **Time to train (seconds)** (Время обучения в секундах) в зависимости от размера источника данных.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="d6b1d-162">Хотя построитель моделей задает для параметра **Время обучения (в секундах)** значение 10 секунд, увеличьте его до 30 секунд.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="d6b1d-163">Обучение в течение более длительного периода времени позволяет построителю моделей исследовать большее количество алгоритмов и комбинаций параметров, чтобы определить наилучшую модель.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="d6b1d-164">Выберите **Начать обучение**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-164">Select **Start Training**.</span></span>

    <span data-ttu-id="d6b1d-165">В процессе обучения сведения о ходе выполнения отображаются в разделе `Progress` шага обучения.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="d6b1d-166">"Состояние" — это состояние завершения процесса обучения.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="d6b1d-167">"Наибольшая точность" — это точность модели, которая на данный момент определена построителем моделей как лучшая.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="d6b1d-168">Точность зависит от того, насколько правильный прогноз был сделан моделью на основе тестовых данных.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="d6b1d-169">"Лучший алгоритм" — это название алгоритма, который на данный момент определен построителем моделей как лучший.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="d6b1d-170">"Последний алгоритм" — это название алгоритма, который использовался построителем моделей для обучения модели последним.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="d6b1d-171">По завершении обучения щелкните ссылку **Оценить**, чтобы перейти к следующему шагу.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="d6b1d-172">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="d6b1d-172">Evaluate the model</span></span>

<span data-ttu-id="d6b1d-173">Результатом шага обучения будет одна модель с наивысшей точностью.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-173">The result of the training step will be one model that has the best performance.</span></span> <span data-ttu-id="d6b1d-174">На шаге оценки инструмента построителя моделей в разделе результатов будет указан алгоритм, используемый оптимальной моделью, в поле **Лучшая модель**, а также метрики в поле **Точность лучшей модели**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-174">In the evaluate step of the Model Builder tool, the output section will contain the algorithm used by the best-performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="d6b1d-175">Кроме того, приводится сводная таблица с пятью лучшими моделями и их метриками.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-175">Additionally, a summary table containing the top five models and their metrics is shown.</span></span>

<span data-ttu-id="d6b1d-176">Если вас не удовлетворяют метрики точности, самые простые способы повысить точность модели — увеличить длительность обучения или использовать больше данных.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-176">If you're not satisfied with your accuracy metrics, some easy ways to try to improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="d6b1d-177">В противном случае щелкните ссылку **Код**, чтобы перейти к завершающему шагу в средстве построителя моделей.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="d6b1d-178">Добавление кода для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="d6b1d-178">Add the code to make predictions</span></span>

<span data-ttu-id="d6b1d-179">В результате процесса обучения создаются два проекта.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="d6b1d-180">Создание ссылки на обученную модель</span><span class="sxs-lookup"><span data-stu-id="d6b1d-180">Reference the trained model</span></span>

1. <span data-ttu-id="d6b1d-181">На шаге **Код** в построителе моделей выберите *Добавить проекты*, чтобы добавить автоматически созданные проекты в решение.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="d6b1d-182">Теперь в **обозревателе решений** должны появиться следующие проекты:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="d6b1d-183">*SentimentRazorML.ConsoleApp*: консольное приложение .NET Core с кодом прогнозирования и обучения модели.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="d6b1d-184">*SentimentRazorML.Model*: библиотека классов .NET Standard с моделями данных, которые определяют схему входных и выходных данных модели, а также хранимую версию оптимальной модели.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="d6b1d-185">В этом руководстве используется только проект *SentimentRazorML.Model*, так как прогнозы будут выполняться в веб-приложении *SentimentRazor*, а не в консоли.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="d6b1d-186">Хотя проект *SentimentRazorML.ConsoleApp* не будет использоваться для оценки, его можно применить для переобучения модели в будущем с помощью новых данных.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="d6b1d-187">Вопросы, связанные с переобучением, выходят за рамки этого руководства.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="d6b1d-188">Настройка пула PredictionEngine</span><span class="sxs-lookup"><span data-stu-id="d6b1d-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="d6b1d-189">Для формирования одного прогноза необходимо создать <xref:Microsoft.ML.PredictionEngine%602>.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-189">To make a single prediction, you have to create a <xref:Microsoft.ML.PredictionEngine%602>.</span></span> <span data-ttu-id="d6b1d-190"><xref:Microsoft.ML.PredictionEngine%602> не является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-190"><xref:Microsoft.ML.PredictionEngine%602> is not thread-safe.</span></span> <span data-ttu-id="d6b1d-191">Кроме того, необходимо создать его экземпляр везде, где он понадобится в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-191">Additionally, you have to create an instance of it everywhere it's needed within your application.</span></span> <span data-ttu-id="d6b1d-192">По мере увеличения размера приложения этот процесс может стать неуправляемым.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="d6b1d-193">Для улучшенной производительности и потокобезопасности используйте сочетание внедрения зависимостей и службы `PredictionEnginePool`, которое создает объекты <xref:Microsoft.ML.PredictionEngine%602> (<xref:Microsoft.Extensions.ObjectPool.ObjectPool%601>) для использования во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601> of <xref:Microsoft.ML.PredictionEngine%602> objects for use throughout your application.</span></span>

1. <span data-ttu-id="d6b1d-194">Установите пакет NuGet *Microsoft.Extensions.ML*:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="d6b1d-195">В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="d6b1d-196">Выберите nuget.org в качестве источника пакета.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="d6b1d-197">Откройте вкладку **Обзор** и найдите **Microsoft.Extensions.ML**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="d6b1d-198">Выберите пакет в списке и нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="d6b1d-199">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="d6b1d-200">Нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с условиями лицензионного соглашения для указанных пакетов.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="d6b1d-201">Откройте файл *Startup.cs* в проекте *SentimentRazor*.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="d6b1d-202">Добавьте следующие операторы using, ссылающиеся на пакет NuGet *Microsoft.Extensions.ML* и проект *SentimentRazorML.Model*:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="d6b1d-203">Создайте глобальную переменную для хранения расположения файла обученной модели.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="d6b1d-204">Файл модели хранится в каталоге сборки вместе с файлами сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="d6b1d-205">Чтобы упростить доступ к нему, создайте вспомогательный метод `GetAbsolutePath`, вызываемый после метода `Configure`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="d6b1d-206">Используйте метод `GetAbsolutePath` в конструкторе класса `Startup`, чтобы задать `_modelPath`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="d6b1d-207">Настройте `PredictionEnginePool` для приложения в методе `ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="d6b1d-208">Создание обработчика анализа тональности</span><span class="sxs-lookup"><span data-stu-id="d6b1d-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="d6b1d-209">Прогнозы будут отображаться на главной странице приложения.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="d6b1d-210">Поэтому вам нужно добавить метод, который принимает входные данные пользователя и использует `PredictionEnginePool` для получения прогноза.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="d6b1d-211">Откройте файл *Index.cshtml.cs*, расположенный в каталоге *Pages*, и добавьте следующие операторы using:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="d6b1d-212">Чтобы использовать службу `PredictionEnginePool`, настроенную в классе `Startup`, необходимо внедрить ее в конструктор модели для дальнейшего использования.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="d6b1d-213">Добавьте переменную для создания ссылки на `PredictionEnginePool` в классе `IndexModel`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="d6b1d-214">Создайте конструктор в классе `IndexModel` и вставьте в него службу `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="d6b1d-215">Создайте обработчик метода, который использует `PredictionEnginePool` для создания прогнозов на основе вводимых пользователем данных, полученных с веб-страницы.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="d6b1d-216">Добавьте новый метод `OnGetAnalyzeSentiment` под методом `OnGet`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="d6b1d-217">Внутри метода `OnGetAnalyzeSentiment` передайте тональность *Neutral* (Нейтрально), если входные данные пользователя пусты или имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="d6b1d-218">При наличии допустимых входных данных создайте новый экземпляр `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="d6b1d-219">Используйте `PredictionEnginePool` для прогнозирования тональности.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="d6b1d-220">Преобразуйте прогнозируемое значение `bool` в токсичное или нетоксичное с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="d6b1d-221">Наконец, передайте тональности обратно на веб-страницу.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="d6b1d-222">Настройка веб-страницы</span><span class="sxs-lookup"><span data-stu-id="d6b1d-222">Configure the web page</span></span>

<span data-ttu-id="d6b1d-223">Результаты, возвращаемые `OnGetAnalyzeSentiment`, будут динамически отображаться на веб-странице `Index`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="d6b1d-224">Откройте файл *Index.cshtml* в каталоге *Pages* и замените его содержимое следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="d6b1d-225">Затем добавьте код CSS в конец страницы *site.css* в каталоге *wwwroot\css*:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="d6b1d-226">После этого добавьте код для отправки входных данных с веб-страницы в обработчик `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="d6b1d-227">В файле *site.js*, расположенном в каталоге *wwwroot\js*, создайте функцию `getSentiment` для создания HTTP-запроса GET с входными данными пользователя к обработчику `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="d6b1d-228">Ниже добавьте еще одну функцию `updateMarker` для динамического обновления расположения маркера на веб-странице по мере прогнозирования тональности.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="d6b1d-229">Создайте функцию обработчика событий `updateSentiment` для получения входных данных от пользователя, отправьте ее в функцию `OnGetAnalyzeSentiment` с помощью функции `getSentiment` и обновите маркер с помощью функции `updateMarker`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="d6b1d-230">Наконец, зарегистрируйте обработчик событий и привяжите его к элементу `textarea` с помощью атрибута `id=Message`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="d6b1d-231">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="d6b1d-231">Run the application</span></span>

<span data-ttu-id="d6b1d-232">Теперь запустите приложение, которое должно открыться в браузере.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-232">Now that your application is set up, run the application, which should launch in your browser.</span></span>

<span data-ttu-id="d6b1d-233">Когда приложение запустится, введите *Model Builder is cool!* (Построитель моделей — это круто!)</span><span class="sxs-lookup"><span data-stu-id="d6b1d-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="d6b1d-234">в текстовом поле.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-234">into the text area.</span></span> <span data-ttu-id="d6b1d-235">Отобразится прогнозируемая тональность — *Not Toxic* (Нетоксично).</span><span class="sxs-lookup"><span data-stu-id="d6b1d-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Окно выполнения с окном прогнозируемой тональности](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="d6b1d-237">В будущем вам может потребоваться создать ссылку на проекты, созданные с помощью построителя моделей, для использования в другом решении. В таком случае их можно найти в каталоге `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="d6b1d-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d6b1d-238">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="d6b1d-238">Next steps</span></span>

<span data-ttu-id="d6b1d-239">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d6b1d-240">Создание приложения Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6b1d-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="d6b1d-241">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="d6b1d-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="d6b1d-242">Выбор сценария</span><span class="sxs-lookup"><span data-stu-id="d6b1d-242">Choose a scenario</span></span>
> - <span data-ttu-id="d6b1d-243">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="d6b1d-243">Load the data</span></span>
> - <span data-ttu-id="d6b1d-244">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="d6b1d-244">Train the model</span></span>
> - <span data-ttu-id="d6b1d-245">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="d6b1d-245">Evaluate the model</span></span>
> - <span data-ttu-id="d6b1d-246">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="d6b1d-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d6b1d-247">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="d6b1d-247">Additional Resources</span></span>

<span data-ttu-id="d6b1d-248">Дополнительные сведения см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="d6b1d-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="d6b1d-249">Сценарии для построителя моделей</span><span class="sxs-lookup"><span data-stu-id="d6b1d-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="d6b1d-250">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="d6b1d-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="d6b1d-251">Метрики модели двоичной классификации</span><span class="sxs-lookup"><span data-stu-id="d6b1d-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-binary-classification)
