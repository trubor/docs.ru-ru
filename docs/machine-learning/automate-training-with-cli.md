---
title: Автоматизация обучения модели с помощью ML.NET CLI
description: Сведения о том, как использовать средство ML.NET CLI для автоматического обучения оптимальной модели из командной строки.
ms.date: 06/03/2020
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 0b230e4a517b6493abdb1ec975776fd286b654e3
ms.sourcegitcommit: b27645cb378d4e8137a267e5467ff31409acf6c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2021
ms.locfileid: "103231411"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="2afee-103">Автоматизация обучения модели с помощью ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="2afee-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="2afee-104">ML.NET CLI автоматизирует создание моделей для разработчиков, использующих .NET.</span><span class="sxs-lookup"><span data-stu-id="2afee-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="2afee-105">Чтобы использовать ML.NET API сам по себе (без ML.NET AutoML CLI), вам нужно выбрать алгоритм обучения (реализация алгоритма машинного обучения для конкретной задачи) и набор преобразований данных (конструирование признаков), применяемые к вашим данным.</span><span class="sxs-lookup"><span data-stu-id="2afee-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="2afee-106">Оптимальный конвейер индивидуален для каждого набора данных, а выбор оптимального алгоритма из всех возможных вариантов только усложняет задачу.</span><span class="sxs-lookup"><span data-stu-id="2afee-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="2afee-107">Кроме того, каждый алгоритм имеет набор настраиваемых гиперпараметров.</span><span class="sxs-lookup"><span data-stu-id="2afee-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="2afee-108">Таким образом, вы можете потратить недели (а иногда и месяцы) на оптимизацию модели машинного обучения, пытаясь найти лучшие сочетания конструирования признаков, алгоритмов обучения и гиперпараметров.</span><span class="sxs-lookup"><span data-stu-id="2afee-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="2afee-109">ML.NET CLI упрощает этот процесс с помощью автоматизированного машинного обучения (AutoML).</span><span class="sxs-lookup"><span data-stu-id="2afee-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="2afee-110">В этом разделе описано, как использовать средства ML.NET **CLI** и ML.NET **AutoML**, которые сейчас находятся на этапе предварительной версии. Этот материал может быть изменен.</span><span class="sxs-lookup"><span data-stu-id="2afee-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="2afee-111">Что такое интерфейс командной строки ML.NET CLI?</span><span class="sxs-lookup"><span data-stu-id="2afee-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="2afee-112">Интерфейс командной строки ML.NET — это [средство .NET Core](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="2afee-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="2afee-113">После установки вы передаете ему задачу машинного обучения и набор данных для обучения, а он создает модель ML.NET и код C# для выполнения, чтобы использовать модель в приложении.</span><span class="sxs-lookup"><span data-stu-id="2afee-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="2afee-114">Как показано на следующем рисунке, можно легко создать высококачественную модель ML.NET (ZIP-файл сериализованной модели), а также пример кода C# для запуска и оценки этой модели.</span><span class="sxs-lookup"><span data-stu-id="2afee-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="2afee-115">Кроме того, создается код C# для создания и обучения этой модели, поэтому вы можете исследовать алгоритм и параметры, используемые для созданной "оптимальной модели", и выполнять итерацию по ним.</span><span class="sxs-lookup"><span data-stu-id="2afee-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

![Ядро AutoML, работающее в программе командной строки ML.NET](media/automate-training-with-cli/cli-high-level-process.png)

<span data-ttu-id="2afee-117">Вы можете создать эти ресурсы из собственных наборов данных без самостоятельного написания кода, что также повышает производительность вашего труда, даже если вы уже знакомы с ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2afee-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="2afee-118">Сейчас ML.NET CLI поддерживает следующие задачи машинного обучения:</span><span class="sxs-lookup"><span data-stu-id="2afee-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- <span data-ttu-id="2afee-119">классификация;</span><span class="sxs-lookup"><span data-stu-id="2afee-119">classification</span></span>
- <span data-ttu-id="2afee-120">регрессия;</span><span class="sxs-lookup"><span data-stu-id="2afee-120">regression</span></span>
- <span data-ttu-id="2afee-121">рекомендация.</span><span class="sxs-lookup"><span data-stu-id="2afee-121">recommendation</span></span>
- <span data-ttu-id="2afee-122">классификация изображений.</span><span class="sxs-lookup"><span data-stu-id="2afee-122">image classification</span></span>

<span data-ttu-id="2afee-123">Пример использования (сценарий классификации):</span><span class="sxs-lookup"><span data-stu-id="2afee-123">Example of usage (classification scenario):</span></span>

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![Классификация ML.NET из командной строки](media/automate-training-with-cli/mlnet-classification-powershell.gif)

<span data-ttu-id="2afee-125">Его можно схожим образом запустить в *Windows PowerShell*, *оболочке Bash в macOS или Linux* или в *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="2afee-125">You can run it the same way on *Windows PowerShell*, *macOS/Linux bash*, or *Windows CMD*.</span></span> <span data-ttu-id="2afee-126">Однако функция табличного автозавершения (предложения параметров) не будет работать в *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="2afee-126">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="2afee-127">Созданные выходные ресурсы</span><span class="sxs-lookup"><span data-stu-id="2afee-127">Output assets generated</span></span>

<span data-ttu-id="2afee-128">Команды задачи машинного обучения в интерфейсе командной строки создают следующие ресурсы в выходной папке.</span><span class="sxs-lookup"><span data-stu-id="2afee-128">The ML task commands in the CLI generate the following assets in the output folder:</span></span>

- <span data-ttu-id="2afee-129">Готовый к использованию ZIP-файл сериализованной модели ("оптимальной модели") для выполнения прогнозов.</span><span class="sxs-lookup"><span data-stu-id="2afee-129">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="2afee-130">Решение C#, включающее в себя следующее:</span><span class="sxs-lookup"><span data-stu-id="2afee-130">C# solution with:</span></span>
  - <span data-ttu-id="2afee-131">код C# для запуска или оценки созданной модели (для прогнозирования в приложениях пользователей);</span><span class="sxs-lookup"><span data-stu-id="2afee-131">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="2afee-132">обучающий код C#, используемый для создания этой модели (в учебных целях или для переобучения модели).</span><span class="sxs-lookup"><span data-stu-id="2afee-132">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="2afee-133">Файл журнала с информацией обо всех итерациях/проходах по нескольким оцениваемым алгоритмам, включая их подробную конфигурацию или конвейер.</span><span class="sxs-lookup"><span data-stu-id="2afee-133">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="2afee-134">Первые два ресурса можно использовать непосредственно в приложениях конечных пользователей (веб-приложениях и службах ASP.NET Core, классических приложениях и т. д.) для прогнозирования с помощью созданной модели машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="2afee-134">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="2afee-135">Третий ресурс, обучающий код, показывает, какой код ML.NET API использовался средством CLI для обучения созданной модели, чтобы вы могли переобучить модель и определить, какой конкретный алгоритм обучения и гиперпараметры были выбраны средствами CLI и AutoML.</span><span class="sxs-lookup"><span data-stu-id="2afee-135">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="2afee-136">Общие сведения о качестве модели</span><span class="sxs-lookup"><span data-stu-id="2afee-136">Understanding the quality of the model</span></span>

<span data-ttu-id="2afee-137">При создании "оптимальной модели" с помощью средства CLI вы регистрируете метрики качества (такие как точность и достоверность аппроксимации), необходимые для требуемой задачи машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="2afee-137">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="2afee-138">Здесь приведены сводные данные об этих метриках, сгруппированные по задачам машинного обучения, чтобы вы могли определить качество автоматически созданной "оптимальной модели".</span><span class="sxs-lookup"><span data-stu-id="2afee-138">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-classification-models"></a><span data-ttu-id="2afee-139">Метрики моделей классификации</span><span class="sxs-lookup"><span data-stu-id="2afee-139">Metrics for Classification models</span></span>

<span data-ttu-id="2afee-140">Ниже приведено изображение со списком метрик для классификации пяти ведущих моделей в CLI:</span><span class="sxs-lookup"><span data-stu-id="2afee-140">The following image displays the classification metrics list for the top five models found by the CLI:</span></span>

![Метрики классификации для пяти основных моделей](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 <span data-ttu-id="2afee-142">Точность является популярной метрикой для проблем классификации, но она не всегда является лучшей метрикой для выбора оптимальной модели, что показано в ссылках ниже.</span><span class="sxs-lookup"><span data-stu-id="2afee-142">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="2afee-143">Бывают случаи, когда нужно оценить качество модели с помощью дополнительных метрик.</span><span class="sxs-lookup"><span data-stu-id="2afee-143">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="2afee-144">Чтобы изучить метрики, выводимые интерфейсом командной строки, см. раздел [Метрики для классификации](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="2afee-144">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="2afee-145">Метрики для моделей регрессии и рекомендаций</span><span class="sxs-lookup"><span data-stu-id="2afee-145">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="2afee-146">Модель регрессии хорошо соответствует данным, если различия между наблюдаемыми значениями и прогнозируемыми значениями модели являются незначительными и несистематическими.</span><span class="sxs-lookup"><span data-stu-id="2afee-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="2afee-147">Регрессию можно оценить с помощью определенных метрик.</span><span class="sxs-lookup"><span data-stu-id="2afee-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="2afee-148">Вы увидите аналогичный список метрик для пяти основных моделей качества в CLI, только в этом случае пять основных моделей относятся к задаче машинного обучения с регрессией:</span><span class="sxs-lookup"><span data-stu-id="2afee-148">You'll see a similar list of metrics for the top five quality models found by the CLI, except in this case, the top five are related to a regression ML task:</span></span>

![Метрики регрессии для пяти основных моделей](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="2afee-150">Чтобы изучить метрики, выводимые интерфейсом командной строки, см. раздел [Метрики для регрессии](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="2afee-150">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="2afee-151">См. также</span><span class="sxs-lookup"><span data-stu-id="2afee-151">See also</span></span>

- [<span data-ttu-id="2afee-152">Установка интерфейса командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="2afee-152">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="2afee-153">Учебник. Анализ тональности с помощью интерфейса командной строки (CLI) ML.NET</span><span class="sxs-lookup"><span data-stu-id="2afee-153">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="2afee-154">Справочник по командам интерфейса командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="2afee-154">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="2afee-155">Данные телеметрии в интерфейсе командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="2afee-155">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
