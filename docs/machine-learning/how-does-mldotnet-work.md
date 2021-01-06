---
title: Что такое ML.NET и принципы работы этой системы
description: ML.NET позволяет добавлять в приложения .NET возможности машинного обучения в автономном и подключенном режимах. Используя эту функцию, вы можете получать автоматические прогнозы на основе данных, доступных вашему приложению, без необходимости подключаться к сети для работы с ML.NET. В этой статье рассматриваются основы машинного обучения в ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 2c44a83b4d45c95cbe45f125523207811f6368c2
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97634070"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="27d49-105">Что такое ML.NET и принципы работы этой системы</span><span class="sxs-lookup"><span data-stu-id="27d49-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="27d49-106">ML.NET позволяет добавлять в приложения .NET возможности машинного обучения в автономном и подключенном режимах.</span><span class="sxs-lookup"><span data-stu-id="27d49-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="27d49-107">Используя эту функцию, вы сможете получать автоматические прогнозы на основе данных, доступных вашему приложению.</span><span class="sxs-lookup"><span data-stu-id="27d49-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="27d49-108">Приложения машинного обучения используют для прогнозирования закономерности, найденные в данных, не будучи явно запрограммированными.</span><span class="sxs-lookup"><span data-stu-id="27d49-108">Machine learning applications make use of patterns in the data to make predictions rather than needing to be explicitly programmed.</span></span>

<span data-ttu-id="27d49-109">В основе ML.NET лежит **модель** машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="27d49-109">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="27d49-110">Эта модель определяет шаги, которые необходимо выполнить для получения прогнозов на основе входных данных.</span><span class="sxs-lookup"><span data-stu-id="27d49-110">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="27d49-111">С помощью ML.NET вы можете обучить пользовательскую модель, указав соответствующий алгоритм, а также импортировать предварительно обученные модели TensorFlow и ONNX.</span><span class="sxs-lookup"><span data-stu-id="27d49-111">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="27d49-112">Созданную модель можно добавить в приложение и использовать ее для получения прогнозов.</span><span class="sxs-lookup"><span data-stu-id="27d49-112">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="27d49-113">ML.NET работает в Windows, Linux и macOS с .NET Core или в Windows с .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27d49-113">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="27d49-114">64-разрядная версия поддерживается на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="27d49-114">64 bit is supported on all platforms.</span></span> <span data-ttu-id="27d49-115">32-разрядная версия поддерживается в Windows, за исключением функций, связанных с TensorFlow, LightGBM и ONNX.</span><span class="sxs-lookup"><span data-stu-id="27d49-115">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="27d49-116">С помощью ML.NET можно получать прогнозы следующих типов.</span><span class="sxs-lookup"><span data-stu-id="27d49-116">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="27d49-117">Классификация/категоризация</span><span class="sxs-lookup"><span data-stu-id="27d49-117">Classification/Categorization</span></span>|<span data-ttu-id="27d49-118">Автоматическое разделение отзывов клиентов на положительные и отрицательные</span><span class="sxs-lookup"><span data-stu-id="27d49-118">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="27d49-119">Регрессия/прогноз непрерывных значений</span><span class="sxs-lookup"><span data-stu-id="27d49-119">Regression/Predict continuous values</span></span>|<span data-ttu-id="27d49-120">Прогноз цены на дома, исходя из их размера и местонахождения</span><span class="sxs-lookup"><span data-stu-id="27d49-120">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="27d49-121">Обнаружение аномалий</span><span class="sxs-lookup"><span data-stu-id="27d49-121">Anomaly Detection</span></span>|<span data-ttu-id="27d49-122">Обнаружение мошеннических банковских операций</span><span class="sxs-lookup"><span data-stu-id="27d49-122">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="27d49-123">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="27d49-123">Recommendations</span></span>|<span data-ttu-id="27d49-124">Предложение продуктов, которые онлайн-покупатели могут захотеть купить, исходя из их предыдущих покупок</span><span class="sxs-lookup"><span data-stu-id="27d49-124">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="27d49-125">Временные ряды/последовательности</span><span class="sxs-lookup"><span data-stu-id="27d49-125">Time series/sequential data</span></span>|<span data-ttu-id="27d49-126">Прогнозы погоды и объемов продаж</span><span class="sxs-lookup"><span data-stu-id="27d49-126">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="27d49-127">Классификация изображений</span><span class="sxs-lookup"><span data-stu-id="27d49-127">Image classification</span></span>|<span data-ttu-id="27d49-128">Классификация патологий на медицинских изображениях</span><span class="sxs-lookup"><span data-stu-id="27d49-128">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="27d49-129">Hello ML.NET World</span><span class="sxs-lookup"><span data-stu-id="27d49-129">Hello ML.NET World</span></span>

<span data-ttu-id="27d49-130">В следующем фрагменте кода показано простейшее приложение ML.NET.</span><span class="sxs-lookup"><span data-stu-id="27d49-130">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="27d49-131">Код в этом примере создает модель линейной регрессии для прогнозирования цен на дома, исходя из их размера и стоимости.</span><span class="sxs-lookup"><span data-stu-id="27d49-131">This example constructs a linear regression model to predict house prices using house size and price data.</span></span>

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;

    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }

        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }

        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();

            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));

            // 3. Train model
            var model = pipeline.Fit(trainingData);

            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    }
```

## <a name="code-workflow"></a><span data-ttu-id="27d49-132">Порядок работы с кодом</span><span class="sxs-lookup"><span data-stu-id="27d49-132">Code workflow</span></span>

<span data-ttu-id="27d49-133">На представленной ниже схеме показана структура кода приложения, а также итеративный процесс разработки модели.</span><span class="sxs-lookup"><span data-stu-id="27d49-133">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="27d49-134">Сбор и загрузка обучающих данных в объект **IDataView**</span><span class="sxs-lookup"><span data-stu-id="27d49-134">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="27d49-135">Указание конвейера операций для извлечения функций и применение алгоритма машинного обучения</span><span class="sxs-lookup"><span data-stu-id="27d49-135">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="27d49-136">Обучение модели путем вызова функции **Fit()** для конвейера</span><span class="sxs-lookup"><span data-stu-id="27d49-136">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="27d49-137">Оценка модели и итерации для ее улучшения</span><span class="sxs-lookup"><span data-stu-id="27d49-137">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="27d49-138">Сохранение модели в двоичном формате для использования в приложении</span><span class="sxs-lookup"><span data-stu-id="27d49-138">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="27d49-139">Загрузка модели обратно в объект **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="27d49-139">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="27d49-140">Прогнозирование с помощью функции **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="27d49-140">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Процесс разработки приложения ML.NET, включая компоненты для создания данных, разработку конвейера, а также обучение, оценку и использование модели](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="27d49-142">Рассмотрим эти этапы более подробно.</span><span class="sxs-lookup"><span data-stu-id="27d49-142">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="27d49-143">Модель машинного обучения</span><span class="sxs-lookup"><span data-stu-id="27d49-143">Machine learning model</span></span>

<span data-ttu-id="27d49-144">Модель ML.NET — это объект, содержащий преобразования для получения прогнозов на основе предоставленных вами данных.</span><span class="sxs-lookup"><span data-stu-id="27d49-144">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="27d49-145">Basic</span><span class="sxs-lookup"><span data-stu-id="27d49-145">Basic</span></span>

<span data-ttu-id="27d49-146">Самая базовая модель — это двухмерная линейная регрессия, где одно непрерывное количество пропорционально другому, как в приведенном выше примере с ценами на дома.</span><span class="sxs-lookup"><span data-stu-id="27d49-146">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Модель линейной регрессии с параметрами смещения и веса](./media/linear-regression-model.svg)

<span data-ttu-id="27d49-148">Модель проста: $Цена = b + Размер \* w$.</span><span class="sxs-lookup"><span data-stu-id="27d49-148">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="27d49-149">Параметры $b$ и $w$ рассчитываются с помощью линии, проведенной через набор пар данных (размер, цена).</span><span class="sxs-lookup"><span data-stu-id="27d49-149">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="27d49-150">Данные, используемые для поиска параметров модели, называется **обучающими**.</span><span class="sxs-lookup"><span data-stu-id="27d49-150">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="27d49-151">Входные данные модели машинного обучения называются **компонентами**.</span><span class="sxs-lookup"><span data-stu-id="27d49-151">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="27d49-152">В этом примере $Размер$ — единственный компонент.</span><span class="sxs-lookup"><span data-stu-id="27d49-152">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="27d49-153">Эталонные значения, которые используются для обучения модели машинного обучения, называются **метками**.</span><span class="sxs-lookup"><span data-stu-id="27d49-153">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="27d49-154">В этом примере метками служат значения параметра $Цена$ в обучающем наборе данных.</span><span class="sxs-lookup"><span data-stu-id="27d49-154">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="27d49-155">Более сложная модель</span><span class="sxs-lookup"><span data-stu-id="27d49-155">More complex</span></span>

<span data-ttu-id="27d49-156">Более сложная модель классифицирует финансовые транзакции по категориям, используя текстовые описания транзакций.</span><span class="sxs-lookup"><span data-stu-id="27d49-156">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="27d49-157">Описание транзакции разбивается на набор компонентов — для этого удаляются избыточные слова и символы и подсчитывается количество слов и комбинаций символов.</span><span class="sxs-lookup"><span data-stu-id="27d49-157">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="27d49-158">Набор компонентов используется для обучения линейной модели на основе набора категорий в обучающих данных.</span><span class="sxs-lookup"><span data-stu-id="27d49-158">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="27d49-159">Чем больше новые описания похожи на те, что уже присутствуют в наборе обучающих данных, тем выше вероятность того, что соответствующим транзакциям будет присвоена та же категория.</span><span class="sxs-lookup"><span data-stu-id="27d49-159">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Модель классификации текста](./media/text-classification-model.svg)

<span data-ttu-id="27d49-161">И модель прогнозирования цен на дома, и модель классификации текста являются **линейными**.</span><span class="sxs-lookup"><span data-stu-id="27d49-161">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="27d49-162">В зависимости от характера ваших данных и решаемой задачи можно также использовать модели **дерева принятия решений**, **обобщенные аддитивные** модели и т. д.</span><span class="sxs-lookup"><span data-stu-id="27d49-162">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="27d49-163">Дополнительные сведения о моделях см. в статье [Задачи](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="27d49-163">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="27d49-164">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="27d49-164">Data preparation</span></span>

<span data-ttu-id="27d49-165">В большинстве случаев доступные данные не подходят для обучения модели машинного обучения в их исходном виде.</span><span class="sxs-lookup"><span data-stu-id="27d49-165">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="27d49-166">Необработанные данные необходимо подготовить (подвергнуть предварительной обработке), прежде чем их можно будет использовать для поиска параметров вашей модели.</span><span class="sxs-lookup"><span data-stu-id="27d49-166">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="27d49-167">Возможно, данные придется преобразовать из строковых значений в числовые,</span><span class="sxs-lookup"><span data-stu-id="27d49-167">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="27d49-168">освободить от избыточной информации,</span><span class="sxs-lookup"><span data-stu-id="27d49-168">You might have redundant information in your input data.</span></span> <span data-ttu-id="27d49-169">уменьшить или увеличить их размер,</span><span class="sxs-lookup"><span data-stu-id="27d49-169">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="27d49-170">масштабировать или нормализовать.</span><span class="sxs-lookup"><span data-stu-id="27d49-170">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="27d49-171">В [учебниках ML.NET](./tutorials/index.md) рассказывается о различных конвейерах обработки данных для текстов, изображений, числовых данных и временных рядов, которые используются для выполнения задач машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="27d49-171">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="27d49-172">См. сведения о [подготовке данных](./how-to-guides/prepare-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="27d49-172">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="27d49-173">Информацию обо всех [доступных преобразованиях](./resources/transforms.md) вы найдете в разделе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="27d49-173">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="27d49-174">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="27d49-174">Model evaluation</span></span>

<span data-ttu-id="27d49-175">Как узнать, насколько точные прогнозы будет давать обученная вами модель?</span><span class="sxs-lookup"><span data-stu-id="27d49-175">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="27d49-176">ML.NET позволяет оценить модель по новым тестовым данным.</span><span class="sxs-lookup"><span data-stu-id="27d49-176">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="27d49-177">У каждого типа задач машинного обучения имеются метрики, по которым можно оценить точность и аккуратность модели, применив ее к тестовому набору данных.</span><span class="sxs-lookup"><span data-stu-id="27d49-177">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="27d49-178">В примере с ценами на дома мы использовали задачу **Регрессия**.</span><span class="sxs-lookup"><span data-stu-id="27d49-178">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="27d49-179">Чтобы оценить модель, добавьте к исходному образцу следующий код:</span><span class="sxs-lookup"><span data-stu-id="27d49-179">To evaluate the model, add the following code to the original sample.</span></span>

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);

        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

<span data-ttu-id="27d49-180">Метрики оценки покажут, что ошибки незначительны, а корреляция между прогнозируемыми результатами и выходными данными теста высока.</span><span class="sxs-lookup"><span data-stu-id="27d49-180">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="27d49-181">Это было просто.</span><span class="sxs-lookup"><span data-stu-id="27d49-181">That was easy!</span></span> <span data-ttu-id="27d49-182">На практике для получения хороших метрик модели требуется гораздо более тщательная настройка.</span><span class="sxs-lookup"><span data-stu-id="27d49-182">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="27d49-183">Архитектура ML.NET</span><span class="sxs-lookup"><span data-stu-id="27d49-183">ML.NET architecture</span></span>

<span data-ttu-id="27d49-184">В этом разделе мы рассмотрим архитектурные шаблоны ML.NET.</span><span class="sxs-lookup"><span data-stu-id="27d49-184">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="27d49-185">Если вы опытный разработчик .NET, какие-то из этих шаблонов будут вам знакомы больше, а какие-то меньше.</span><span class="sxs-lookup"><span data-stu-id="27d49-185">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="27d49-186">Держитесь крепче, начинаем погружение!</span><span class="sxs-lookup"><span data-stu-id="27d49-186">Hold tight, while we dive in!</span></span>

<span data-ttu-id="27d49-187">Приложение ML.NET начинается с объекта <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="27d49-187">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="27d49-188">Этот одноэлементный объект содержит **каталоги**.</span><span class="sxs-lookup"><span data-stu-id="27d49-188">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="27d49-189">Каталог — это фабрика загрузки и сохранения данных, преобразований, инструкторов и компонентов операций модели.</span><span class="sxs-lookup"><span data-stu-id="27d49-189">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="27d49-190">Каждый объект каталога имеет методы для создания различных типов компонентов:</span><span class="sxs-lookup"><span data-stu-id="27d49-190">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="27d49-191">Загрузка и сохранение данных</span><span class="sxs-lookup"><span data-stu-id="27d49-191">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="27d49-192">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="27d49-192">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="27d49-193">Алгоритмы обучения</span><span class="sxs-lookup"><span data-stu-id="27d49-193">Training algorithms</span></span>|<span data-ttu-id="27d49-194">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="27d49-194">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="27d49-195">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="27d49-195">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="27d49-196">Обнаружение аномалий</span><span class="sxs-lookup"><span data-stu-id="27d49-196">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="27d49-197">Кластеризация</span><span class="sxs-lookup"><span data-stu-id="27d49-197">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="27d49-198">Прогнозирование</span><span class="sxs-lookup"><span data-stu-id="27d49-198">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="27d49-199">Ранжирование</span><span class="sxs-lookup"><span data-stu-id="27d49-199">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="27d49-200">Регрессия</span><span class="sxs-lookup"><span data-stu-id="27d49-200">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="27d49-201">Рекомендация</span><span class="sxs-lookup"><span data-stu-id="27d49-201">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="27d49-202">Добавление пакета NuGet `Microsoft.ML.Recommender`</span><span class="sxs-lookup"><span data-stu-id="27d49-202">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="27d49-203">TimeSeries</span><span class="sxs-lookup"><span data-stu-id="27d49-203">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="27d49-204">Добавление пакета NuGet `Microsoft.ML.TimeSeries`</span><span class="sxs-lookup"><span data-stu-id="27d49-204">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="27d49-205">Использование модели</span><span class="sxs-lookup"><span data-stu-id="27d49-205">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="27d49-206">Через каждую из указанных выше категорий можно перейти к соответствующим методам создания.</span><span class="sxs-lookup"><span data-stu-id="27d49-206">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="27d49-207">В Visual Studio каталоги отображаются с помощью IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="27d49-207">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![IntelliSense для инструкторов регрессии](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="27d49-209">Сборка конвейера</span><span class="sxs-lookup"><span data-stu-id="27d49-209">Build the pipeline</span></span>

<span data-ttu-id="27d49-210">В каждом каталоге есть набор методов расширения.</span><span class="sxs-lookup"><span data-stu-id="27d49-210">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="27d49-211">Посмотрим, как методы расширения используются при создании конвейера обучения.</span><span class="sxs-lookup"><span data-stu-id="27d49-211">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="27d49-212">В представленном ниже фрагменте кода `Concatenate` и `Sdca` — это методы из каталога.</span><span class="sxs-lookup"><span data-stu-id="27d49-212">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="27d49-213">Каждый из них создает объект [IEstimator](xref:Microsoft.ML.IEstimator%601), который добавляется в конвейер.</span><span class="sxs-lookup"><span data-stu-id="27d49-213">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="27d49-214">Этот этап включает только создание объектов.</span><span class="sxs-lookup"><span data-stu-id="27d49-214">At this point, the objects are created only.</span></span> <span data-ttu-id="27d49-215">Выполнение не происходит.</span><span class="sxs-lookup"><span data-stu-id="27d49-215">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="27d49-216">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="27d49-216">Train the model</span></span>

<span data-ttu-id="27d49-217">После создания объектов в конвейере данные можно использовать для обучения модели.</span><span class="sxs-lookup"><span data-stu-id="27d49-217">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="27d49-218">Вызов функции `Fit()` задействует входные обучающие данные для оценки параметров модели.</span><span class="sxs-lookup"><span data-stu-id="27d49-218">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="27d49-219">Это называется обучение модели.</span><span class="sxs-lookup"><span data-stu-id="27d49-219">This is known as training the model.</span></span> <span data-ttu-id="27d49-220">Напомним, что представленная выше модель линейной регрессии включала два параметра модели: **смещение** и **вес**.</span><span class="sxs-lookup"><span data-stu-id="27d49-220">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="27d49-221">После вызова функции `Fit()` значения этих параметров становятся известны.</span><span class="sxs-lookup"><span data-stu-id="27d49-221">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="27d49-222">В большинстве моделей параметров будет намного больше.</span><span class="sxs-lookup"><span data-stu-id="27d49-222">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="27d49-223">См. сведения об [обучении моделей](./how-to-guides/train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="27d49-223">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="27d49-224">Полученный объект модели реализует интерфейс <xref:Microsoft.ML.ITransformer>.</span><span class="sxs-lookup"><span data-stu-id="27d49-224">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="27d49-225">Это значит, что модель преобразует входные данные в прогнозы.</span><span class="sxs-lookup"><span data-stu-id="27d49-225">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="27d49-226">Использование модели</span><span class="sxs-lookup"><span data-stu-id="27d49-226">Use the model</span></span>

<span data-ttu-id="27d49-227">Входные данные можно преобразовывать в прогнозы все сразу или по очереди.</span><span class="sxs-lookup"><span data-stu-id="27d49-227">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="27d49-228">В примере с ценами на дома мы использовали оба варианта: все сразу для оценки модели и поочередно для создания нового прогноза.</span><span class="sxs-lookup"><span data-stu-id="27d49-228">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="27d49-229">Рассмотрим получение одиночных прогнозов.</span><span class="sxs-lookup"><span data-stu-id="27d49-229">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="27d49-230">Метод `CreatePredictionEngine()` принимает входной и выходной класс данных.</span><span class="sxs-lookup"><span data-stu-id="27d49-230">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="27d49-231">Имена полей и/или атрибуты кода определяют имена столбцов данных, которые используются при обучении модели и прогнозировании.</span><span class="sxs-lookup"><span data-stu-id="27d49-231">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="27d49-232">Дополнительные сведения см. в статье [Прогнозирование с помощью обученной модели](how-to-guides/machine-learning-model-predictions-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="27d49-232">For more information, see [Make predictions with a trained model](how-to-guides/machine-learning-model-predictions-ml-net.md).</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="27d49-233">Модели и схема данных</span><span class="sxs-lookup"><span data-stu-id="27d49-233">Data models and schema</span></span>

<span data-ttu-id="27d49-234">В основе конвейера машинного обучения ML.NET лежат объекты [DataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="27d49-234">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="27d49-235">Каждое преобразование в конвейере имеет входную схему (имена, типы и размеры данных, которые должны присутствовать во входных данных) и схему вывода (имена, типы и размеры данных, которые создаются после преобразования).</span><span class="sxs-lookup"><span data-stu-id="27d49-235">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span>

<span data-ttu-id="27d49-236">Если схема вывода из одного преобразования в конвейере не соответствует входной схеме, ML.NET выдает исключение.</span><span class="sxs-lookup"><span data-stu-id="27d49-236">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="27d49-237">Объект представления данных содержит столбцы и строки.</span><span class="sxs-lookup"><span data-stu-id="27d49-237">A data view object has columns and rows.</span></span> <span data-ttu-id="27d49-238">Каждый столбец содержит имя, тип и длину.</span><span class="sxs-lookup"><span data-stu-id="27d49-238">Each column has a name and a type and a length.</span></span> <span data-ttu-id="27d49-239">Например, столбцы входных данных в примере с ценами на дома — это **Size** и **Price**.</span><span class="sxs-lookup"><span data-stu-id="27d49-239">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="27d49-240">Оба имеют тип и являются скорее скалярными, а не векторными величинами.</span><span class="sxs-lookup"><span data-stu-id="27d49-240">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![Пример представления данных ML.NET с данными прогнозов по ценам на дома](./media/ml-net-dataview.png)

<span data-ttu-id="27d49-242">Все алгоритмы ML.NET ищут векторный столбец входных данных.</span><span class="sxs-lookup"><span data-stu-id="27d49-242">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="27d49-243">По умолчанию этот столбец вектора называется **Компоненты**.</span><span class="sxs-lookup"><span data-stu-id="27d49-243">By default this vector column is called **Features**.</span></span> <span data-ttu-id="27d49-244">Именно поэтому в примере с ценами на дома мы включили столбец **Размер** в новый столбец **Компоненты**.</span><span class="sxs-lookup"><span data-stu-id="27d49-244">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="27d49-245">Кроме того, после выполнения прогноза все алгоритмы создают новые столбцы.</span><span class="sxs-lookup"><span data-stu-id="27d49-245">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="27d49-246">Фиксированные имена этих новых столбцов зависят от типа алгоритма машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="27d49-246">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="27d49-247">В задаче регрессии один из новых столбцов называется **Оценка**.</span><span class="sxs-lookup"><span data-stu-id="27d49-247">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="27d49-248">Вот почему мы назвали точно так же наши данные цен.</span><span class="sxs-lookup"><span data-stu-id="27d49-248">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="27d49-249">Дополнительные сведения о выходных столбцах различных задач машинного обучения см в руководстве [Задачи машинного обучения](resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="27d49-249">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="27d49-250">Важным свойством объектов DataView является то, что они вычисляются **неактивно**.</span><span class="sxs-lookup"><span data-stu-id="27d49-250">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="27d49-251">Представления данных загружаются и используются только во время обучения и оценки модели и при прогнозировании данных.</span><span class="sxs-lookup"><span data-stu-id="27d49-251">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="27d49-252">В процессе написания и тестирования приложения ML.NET можно использовать отладчик Visual Studio, чтобы посмотреть на любой объект представления данных, вызвав метод [предварительного просмотра](xref:Microsoft.ML.DebuggerExtensions.Preview%2A).</span><span class="sxs-lookup"><span data-stu-id="27d49-252">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="27d49-253">Вы можете проверить переменную `debug` в отладчике и изучить ее содержимое.</span><span class="sxs-lookup"><span data-stu-id="27d49-253">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="27d49-254">Не используйте метод предварительного просмотра в рабочем коде, поскольку он сильно снижает производительность.</span><span class="sxs-lookup"><span data-stu-id="27d49-254">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="27d49-255">Развертывание модели</span><span class="sxs-lookup"><span data-stu-id="27d49-255">Model Deployment</span></span>

<span data-ttu-id="27d49-256">В реальных приложениях обучение и оценка модели будут отделены от прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="27d49-256">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="27d49-257">На практике эти действия часто выполняют разные группы разработчиков.</span><span class="sxs-lookup"><span data-stu-id="27d49-257">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="27d49-258">Ваша команда разработчиков модели может сохранить модель для использования в приложении прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="27d49-258">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="27d49-259">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="27d49-259">Next steps</span></span>

* <span data-ttu-id="27d49-260">Сведения о том, как создавать приложения, используя другие задачи машинного обучения и более реалистичные наборы данных, в [руководствах](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="27d49-260">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="27d49-261">Отдельные темы в [практических руководствах](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="27d49-261">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="27d49-262">Если вы полны энтузиазма, то [справочная документация по API](../../api/index.md?view=ml-dotnet) всегда к вашим услугам.</span><span class="sxs-lookup"><span data-stu-id="27d49-262">If you're super keen, you can dive straight into the [API Reference documentation](../../api/index.md?view=ml-dotnet).</span></span>
