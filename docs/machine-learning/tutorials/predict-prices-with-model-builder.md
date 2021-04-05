---
title: Учебник. Прогнозирование цен с помощью регрессии с использованием Model Builder
description: В этом учебнике показано, как создать модель регрессии с помощью построителя моделей ML.NET, чтобы прогнозировать цены, в частности плату за проезд в такси по Нью-Йорку.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: c34586014b5617f7712a4b708cb2e4a4814da684
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874762"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="2295c-103">Учебник. Прогнозирование цен с помощью регрессии с использованием Model Builder</span><span class="sxs-lookup"><span data-stu-id="2295c-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="2295c-104">Узнайте, как с помощью построителя моделей ML.NET создать модель регрессии для прогнозирования цен.</span><span class="sxs-lookup"><span data-stu-id="2295c-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="2295c-105">Консольное приложение .NET, разрабатываемое в этом учебнике, прогнозирует плату за проезд в такси по Нью-Йорку на основе исторических данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="2295c-106">Шаблон прогнозирования цен, имеющийся в построителе моделей, можно использовать для любых сценариев, предполагающих прогнозирование числовых значений.</span><span class="sxs-lookup"><span data-stu-id="2295c-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="2295c-107">Примерами могут служить прогнозирование цен на недвижимость, спроса и продаж.</span><span class="sxs-lookup"><span data-stu-id="2295c-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="2295c-108">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="2295c-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2295c-109">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="2295c-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="2295c-110">Выбор сценария</span><span class="sxs-lookup"><span data-stu-id="2295c-110">Choose a scenario</span></span>
> - <span data-ttu-id="2295c-111">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="2295c-111">Load the data</span></span>
> - <span data-ttu-id="2295c-112">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="2295c-112">Train the model</span></span>
> - <span data-ttu-id="2295c-113">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="2295c-113">Evaluate the model</span></span>
> - <span data-ttu-id="2295c-114">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="2295c-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="2295c-115">Построитель моделей в настоящее время находится на этапе предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="2295c-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="2295c-116">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="2295c-116">Pre-requisites</span></span>

<span data-ttu-id="2295c-117">Список необходимых условий и инструкции по установке см. в [руководстве по установке построителя моделей](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="2295c-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2295c-118">Создание консольного приложение</span><span class="sxs-lookup"><span data-stu-id="2295c-118">Create a console application</span></span>

1. <span data-ttu-id="2295c-119">Создайте **консольное приложение .NET Core C#** с именем TaxiFarePrediction.</span><span class="sxs-lookup"><span data-stu-id="2295c-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="2295c-120">Убедитесь, что флажок **Поместить решение и проект в одной папке** **снят** (VS 2019) или флажок **Создать каталог для решения** **установлен** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="2295c-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="2295c-121">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="2295c-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="2295c-122">Создайте каталог с именем *Data* в папке проекта, чтобы сохранить в нем файлы набора данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="2295c-123">Набор данных, используемый для обучения и оценки модели машинного обучения, создан на основе данных Комиссии по лицензированию перевозок автотранспортом города Нью-Йорк (TLC).</span><span class="sxs-lookup"><span data-stu-id="2295c-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="2295c-124">Скачать набор данных можно по [этой ссылке](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="2295c-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="2295c-125">При загрузке страницы щелкните правой кнопкой мыши в любом месте и выберите в меню команду **Сохранить как**.</span><span class="sxs-lookup"><span data-stu-id="2295c-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="2295c-126">В диалоговом окне **Сохранить как** сохраните файл в созданную ранее папку *Data*.</span><span class="sxs-lookup"><span data-stu-id="2295c-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="2295c-127">В **обозревателе решений** щелкните правой кнопкой мыши файл *taxi-fare-train.csv* и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="2295c-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="2295c-128">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="2295c-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="2295c-129">Каждая строка в наборе данных `taxi-fare-train.csv` содержит сведения о поездках в такси.</span><span class="sxs-lookup"><span data-stu-id="2295c-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="2295c-130">Откройте набор данных **taxi-fare-train.csv**.</span><span class="sxs-lookup"><span data-stu-id="2295c-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="2295c-131">Предоставленный набор данных содержит следующие столбцы:</span><span class="sxs-lookup"><span data-stu-id="2295c-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="2295c-132">**vendor_id:** идентификатор поставщика услуг такси — это признак.</span><span class="sxs-lookup"><span data-stu-id="2295c-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="2295c-133">**rate_code:** тип тарифа для поездки на такси — это признак.</span><span class="sxs-lookup"><span data-stu-id="2295c-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="2295c-134">**passenger_count:** число пассажиров в поездке — это признак.</span><span class="sxs-lookup"><span data-stu-id="2295c-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="2295c-135">**trip_time_in_secs:** время, затраченное на поездку.</span><span class="sxs-lookup"><span data-stu-id="2295c-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="2295c-136">Вам требуется спрогнозировать плату за одну поездку до того, как поездка будет завершена.</span><span class="sxs-lookup"><span data-stu-id="2295c-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="2295c-137">На этот момент вам неизвестна продолжительность поездки.</span><span class="sxs-lookup"><span data-stu-id="2295c-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="2295c-138">Таким образом, продолжительность поездки не является признаком и соответствующий столбец следует исключить из модели.</span><span class="sxs-lookup"><span data-stu-id="2295c-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="2295c-139">**trip_distance:** расстояние поездки — это признак.</span><span class="sxs-lookup"><span data-stu-id="2295c-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="2295c-140">**payment_type:** метод оплаты (наличные или кредитная карта) — это признак.</span><span class="sxs-lookup"><span data-stu-id="2295c-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="2295c-141">**fare_amount:** общая сумма, уплаченная за поездку на такси, — это метка.</span><span class="sxs-lookup"><span data-stu-id="2295c-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="2295c-142">`label` — это столбец, который необходимо спрогнозировать.</span><span class="sxs-lookup"><span data-stu-id="2295c-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="2295c-143">Цель задачи регрессии — прогнозирование числового значения.</span><span class="sxs-lookup"><span data-stu-id="2295c-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="2295c-144">В этом сценарии прогнозируется стоимость поездки в такси.</span><span class="sxs-lookup"><span data-stu-id="2295c-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="2295c-145">Поэтому меткой является **fare_amount**.</span><span class="sxs-lookup"><span data-stu-id="2295c-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="2295c-146">Выбранные признаки (`features`) — это входные данные, которые вы предоставляете модели для прогнозирования метки (`label`).</span><span class="sxs-lookup"><span data-stu-id="2295c-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="2295c-147">В этом случае остальные столбцы, исключая **trip_time_in_secs**, используются в качестве признаков или входных данных для прогнозирования стоимости поездки.</span><span class="sxs-lookup"><span data-stu-id="2295c-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="2295c-148">Выбор сценария</span><span class="sxs-lookup"><span data-stu-id="2295c-148">Choose a scenario</span></span>

<span data-ttu-id="2295c-149">Чтобы обучить модель, нужно выбрать один из доступных сценариев машинного обучения в построителе моделей.</span><span class="sxs-lookup"><span data-stu-id="2295c-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="2295c-150">В этом случае используется сценарий `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="2295c-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="2295c-151">В **обозревателе решений** щелкните правой кнопкой мыши проект *TaxiFarePrediction* и выберите **Добавить** > **Машинное обучение**.</span><span class="sxs-lookup"><span data-stu-id="2295c-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="2295c-152">На этапе выбора сценария выберите *Прогнозирование цен*.</span><span class="sxs-lookup"><span data-stu-id="2295c-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="2295c-153">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="2295c-153">Load the data</span></span>

<span data-ttu-id="2295c-154">Построитель моделей принимает данные из двух источников: базы данных SQL Server или локального файла в формате CSV или TSV.</span><span class="sxs-lookup"><span data-stu-id="2295c-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="2295c-155">На этапе добавления данных выберите в раскрывающемся списке источников данных пункт *Прогнозирование цен*.</span><span class="sxs-lookup"><span data-stu-id="2295c-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="2295c-156">Нажмите кнопку рядом с текстовым полем *Выберите файл* и выберите в проводнике файл *taxi-fare-test.csv* в каталоге *Data*.</span><span class="sxs-lookup"><span data-stu-id="2295c-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="2295c-157">Выберите *fare_amount* в раскрывающемся списке *Column to Predict (Label)* (Метка для прогнозирования (или столбец)).</span><span class="sxs-lookup"><span data-stu-id="2295c-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="2295c-158">Разверните раскрывающийся список *Входные столбцы (признаки)* и снимите флажок в столбце *trip_time_in_secs*, чтобы исключить его в качестве признака во время обучения.</span><span class="sxs-lookup"><span data-stu-id="2295c-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="2295c-159">Перейдите к этапу обучение средства создания модели.</span><span class="sxs-lookup"><span data-stu-id="2295c-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="2295c-160">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="2295c-160">Train the model</span></span>

<span data-ttu-id="2295c-161">Задачей машинного обучения, используемой в этом учебнике для обучения модели прогнозирования цен, является регрессия.</span><span class="sxs-lookup"><span data-stu-id="2295c-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="2295c-162">В процессе обучения построитель моделей обучает отдельные модели с помощью различных алгоритмов и параметров регрессии, определяя оптимальную модель для вашего набора данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="2295c-163">Время, требуемое для обучения модели, пропорционально объему данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="2295c-164">Построитель моделей автоматически выбирает значение по умолчанию для параметра **Time to train (seconds)** (Время обучения в секундах) в зависимости от размера источника данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="2295c-165">Оставьте значение по умолчанию для параметра *Time to train (seconds)* (Время обучения в секундах), если только вы не хотите проводить обучение более длительное время.</span><span class="sxs-lookup"><span data-stu-id="2295c-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="2295c-166">Выберите *Начать обучение*.</span><span class="sxs-lookup"><span data-stu-id="2295c-166">Select *Start Training*.</span></span>

<span data-ttu-id="2295c-167">В процессе обучения сведения о ходе выполнения отображаются в разделе `Progress` шага обучения.</span><span class="sxs-lookup"><span data-stu-id="2295c-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="2295c-168">"Состояние" — это состояние завершения процесса обучения.</span><span class="sxs-lookup"><span data-stu-id="2295c-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="2295c-169">"Наибольшая точность" — это точность модели, которая на данный момент определена построителем моделей как лучшая.</span><span class="sxs-lookup"><span data-stu-id="2295c-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="2295c-170">Точность зависит от того, насколько правильный прогноз был сделан моделью на основе тестовых данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="2295c-171">"Лучший алгоритм" — это название алгоритма, который на данный момент определен построителем моделей как лучший.</span><span class="sxs-lookup"><span data-stu-id="2295c-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="2295c-172">"Последний алгоритм" — это название алгоритма, который использовался построителем моделей для обучения модели последним.</span><span class="sxs-lookup"><span data-stu-id="2295c-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="2295c-173">По завершении обучения перейдите к шагу оценки.</span><span class="sxs-lookup"><span data-stu-id="2295c-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="2295c-174">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="2295c-174">Evaluate the model</span></span>

<span data-ttu-id="2295c-175">Результат обучения — одна модель с наивысшей точностью.</span><span class="sxs-lookup"><span data-stu-id="2295c-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="2295c-176">В шаге оценки в разделе результатов будет указан алгоритм, используемый оптимальной моделью, в поле *Лучшая модель*, а также метрики в поле *Качество лучшей модели (достоверность аппроксимации)*.</span><span class="sxs-lookup"><span data-stu-id="2295c-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="2295c-177">Кроме того, приводится сводная таблица с пятью лучшими моделями и их метриками.</span><span class="sxs-lookup"><span data-stu-id="2295c-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="2295c-178">Если вас не удовлетворяют метрики точности, самые простые способы повысить точность модели — увеличить длительность обучения или использовать больше данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="2295c-179">Если все в порядке, переходите к следующему шагу.</span><span class="sxs-lookup"><span data-stu-id="2295c-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="2295c-180">Добавление кода для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="2295c-180">Add the code to make predictions</span></span>

<span data-ttu-id="2295c-181">В результате процесса обучения создаются два проекта.</span><span class="sxs-lookup"><span data-stu-id="2295c-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="2295c-182">TaxiFarePredictionML.ConsoleApp — консольное приложение .NET Core с кодом для обучения и использования модели.</span><span class="sxs-lookup"><span data-stu-id="2295c-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="2295c-183">TaxiFarePredictionML.Model — библиотека классов .NET Standard с моделями данных, которые определяют схему входных и выходных данных модели, а также хранимую версию оптимальной модели во время обучения и вспомогательный класс с именем `ConsumeModel` для прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="2295c-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="2295c-184">На шаге добавления кода в построителе моделей выберите **Добавить проекты**, чтобы добавить автоматически созданные проекты в решение.</span><span class="sxs-lookup"><span data-stu-id="2295c-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="2295c-185">Откройте файл *Program.cs* в проекте *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="2295c-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="2295c-186">Добавьте следующее, используя оператор для ссылки на проект *TaxiFarePredictionML.Model*:</span><span class="sxs-lookup"><span data-stu-id="2295c-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="2295c-187">Чтобы сделать прогноз на основе новых данных с помощью модели, создайте новый экземпляр класса `ModelInput` внутри метода `Main` приложения.</span><span class="sxs-lookup"><span data-stu-id="2295c-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="2295c-188">Обратите внимание, что данные о суммах, уплаченных за поездку на такси, отсутствуют во входных данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="2295c-189">Это сделано для того, чтобы модель сама спрогнозировала их.</span><span class="sxs-lookup"><span data-stu-id="2295c-189">This is because the model will generate the prediction for it.</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. <span data-ttu-id="2295c-190">Используйте метод `Predict` из класса `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="2295c-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="2295c-191">Метод `Predict` загружает обученную модель, создает [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для модели и использует эту подсистему для создания прогнозов на основе новых данных.</span><span class="sxs-lookup"><span data-stu-id="2295c-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="2295c-192">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="2295c-192">Run the application.</span></span>

    <span data-ttu-id="2295c-193">Выходные данные программы должны выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="2295c-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="2295c-194">Если на созданные проекты нужно будет сослаться позднее в другом решении, их можно найти в каталоге `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="2295c-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2295c-195">Next Steps</span><span class="sxs-lookup"><span data-stu-id="2295c-195">Next Steps</span></span>

<span data-ttu-id="2295c-196">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="2295c-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2295c-197">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="2295c-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="2295c-198">Выбор сценария</span><span class="sxs-lookup"><span data-stu-id="2295c-198">Choose a scenario</span></span>
> - <span data-ttu-id="2295c-199">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="2295c-199">Load the data</span></span>
> - <span data-ttu-id="2295c-200">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="2295c-200">Train the model</span></span>
> - <span data-ttu-id="2295c-201">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="2295c-201">Evaluate the model</span></span>
> - <span data-ttu-id="2295c-202">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="2295c-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2295c-203">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="2295c-203">Additional Resources</span></span>

<span data-ttu-id="2295c-204">Дополнительные сведения см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="2295c-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="2295c-205">Сценарии для построителя моделей</span><span class="sxs-lookup"><span data-stu-id="2295c-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="2295c-206">Регрессия</span><span class="sxs-lookup"><span data-stu-id="2295c-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="2295c-207">Метрики модели регрессии</span><span class="sxs-lookup"><span data-stu-id="2295c-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="2295c-208">Набор данных о поездках на такси, предоставленный Комиссией по лицензированию перевозок автотранспортом города Нью-Йорк (TLC)</span><span class="sxs-lookup"><span data-stu-id="2295c-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
