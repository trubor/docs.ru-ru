---
title: Справочник по командам интерфейса командной строки (CLI) ML.NET
description: Обзор, примеры и справочник по командам auto-train в программе командной строки ML.NET.
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 6f07cd8b4237f8931bbc0ec97bc0bbe18c488f16
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856072"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="3ff33-103">Справочник по командам интерфейса командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="3ff33-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="3ff33-104">Команды `classification`, `regression` и `recommendation` являются основными командами, предоставляемыми программой командной строки ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3ff33-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="3ff33-105">Эти команды позволяют создать модель ML.NET хорошего качества для классификации и регрессии, а также модели рекомендации, используя автоматизированное машинное обучение (AutoML), а также пример кода на C# для выполнения и оценки модели.</span><span class="sxs-lookup"><span data-stu-id="3ff33-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="3ff33-106">Кроме того, код C# для обучения модели создается для изучения алгоритма и параметров модели.</span><span class="sxs-lookup"><span data-stu-id="3ff33-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="3ff33-107">Этот раздел относится к ML.NET CLI и ML.NET AutoML, находящимся в данный момент в предварительной версии; материалы могут быть изменены.</span><span class="sxs-lookup"><span data-stu-id="3ff33-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="3ff33-108">Обзор</span><span class="sxs-lookup"><span data-stu-id="3ff33-108">Overview</span></span>

<span data-ttu-id="3ff33-109">Пример использования:</span><span class="sxs-lookup"><span data-stu-id="3ff33-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="3ff33-110">Команды задачи `mlnet` ML (`classification`, `regression`и `recommendation`) создают следующие ресурсы:</span><span class="sxs-lookup"><span data-stu-id="3ff33-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="3ff33-111">готовый к использованию ZIP-файл сериализованной модели ("модели высшего качества");</span><span class="sxs-lookup"><span data-stu-id="3ff33-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="3ff33-112">код C# для выполнения или оценки созданной модели.</span><span class="sxs-lookup"><span data-stu-id="3ff33-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="3ff33-113">код на C# с кодом обучения, используемый для создания этой модели.</span><span class="sxs-lookup"><span data-stu-id="3ff33-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="3ff33-114">Первые два ресурса можно использовать непосредственно в приложениях конечных пользователей (веб-приложениях и службах ASP.NET Core, классических приложениях и т. д.) для прогнозирования с помощью созданной модели.</span><span class="sxs-lookup"><span data-stu-id="3ff33-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="3ff33-115">Третий актив, код обучения, показывает, какой код API ML.NET использовало средство CLI для обучения созданной модели, поэтому можно определить конкретный алгоритм обучения и параметры модели.</span><span class="sxs-lookup"><span data-stu-id="3ff33-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="3ff33-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="3ff33-116">Examples</span></span>

<span data-ttu-id="3ff33-117">Самый простой пример команды CLI для задачи классификации (ядро AutoML выведет большую часть параметров из предоставленных данных):</span><span class="sxs-lookup"><span data-stu-id="3ff33-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="3ff33-118">Другой простой пример команды интерфейса командной строки для решения задачи регрессии:</span><span class="sxs-lookup"><span data-stu-id="3ff33-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="3ff33-119">Создание и обучение модели классификации с набором данных для обучения, проверочным набором данных и дальнейшей настройкой явных аргументов:</span><span class="sxs-lookup"><span data-stu-id="3ff33-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="3ff33-120">Параметры команды</span><span class="sxs-lookup"><span data-stu-id="3ff33-120">Command options</span></span>

<span data-ttu-id="3ff33-121">Команды задачи `mlnet` ML (`classification`, `regression`и `recommendation`) обучают несколько моделей на основе предоставленного набора данных и параметров интерфейса командной строки ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3ff33-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="3ff33-122">Эти команды также выбирают оптимальную модель, сохраняют ее в виде сериализованного ZIP-файла и создают связанный код C# для оценки и обучения.</span><span class="sxs-lookup"><span data-stu-id="3ff33-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="3ff33-123">Параметры классификации</span><span class="sxs-lookup"><span data-stu-id="3ff33-123">Classification options</span></span>

<span data-ttu-id="3ff33-124">При запуске `mlnet classification` выполняется обучение модели классификации.</span><span class="sxs-lookup"><span data-stu-id="3ff33-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="3ff33-125">Выберите эту команду, если требуется, чтобы модель машинного обучения Azure категоризировала данные по 2 или более классам (например, анализ тональности).</span><span class="sxs-lookup"><span data-stu-id="3ff33-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="3ff33-126">Параметры регрессии</span><span class="sxs-lookup"><span data-stu-id="3ff33-126">Regression options</span></span>

<span data-ttu-id="3ff33-127">При запуске `mlnet regression` выполняется обучение модели регрессии.</span><span class="sxs-lookup"><span data-stu-id="3ff33-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="3ff33-128">Выберите эту команду, если требуется, чтобы модель машинного обучения Azure предсказывала числовое значение (например, прогноз цены).</span><span class="sxs-lookup"><span data-stu-id="3ff33-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet regression

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="3ff33-129">Параметры рекомендации</span><span class="sxs-lookup"><span data-stu-id="3ff33-129">Recommendation options</span></span>

<span data-ttu-id="3ff33-130">При запуске `mlnet recommendation` выполняется обучение модели рекомендации.</span><span class="sxs-lookup"><span data-stu-id="3ff33-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="3ff33-131">Выберите эту команду, если требуется, чтобы модель ML рекомендовала пользователям элементы на основе оценок (например, рекомендации продукта).</span><span class="sxs-lookup"><span data-stu-id="3ff33-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet recommendation

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="3ff33-132">Недопустимые входные параметры приводят к тому, что средство CLI выдает список допустимых входных данных и сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="3ff33-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="3ff33-133">Набор данных</span><span class="sxs-lookup"><span data-stu-id="3ff33-133">Dataset</span></span>

<span data-ttu-id="3ff33-134">`--dataset | -d` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="3ff33-135">Этот аргумент содержит путь к файлу в одном из следующих форматов:</span><span class="sxs-lookup"><span data-stu-id="3ff33-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="3ff33-136">*А. Файл полного набора данных:* Если используется этот параметр и пользователь не задает `--test-dataset` и `--validation-dataset`, внутри для проверки модели используется кросс-валидация с K-сверткой или автоматизированное разделение данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="3ff33-137">В этом случае пользователю будет достаточно указать путь к файлу набора данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="3ff33-138">*Б. Файл набора данных для обучения:* Если пользователь также предоставляет наборы данных для валидации модели (с помощью `--test-dataset` и при необходимости `--validation-dataset`), то аргумент `--dataset` указывает лишь "набор данных для обучения".</span><span class="sxs-lookup"><span data-stu-id="3ff33-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="3ff33-139">Например при использовании подхода 80–20 % для валидации качества модели и получения показателей точности "набор данных для обучения" будет содержать 80 % данных, а на "проверочный набор данных" придется 20 % данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="3ff33-140">Проверочный набор данных</span><span class="sxs-lookup"><span data-stu-id="3ff33-140">Test dataset</span></span>

<span data-ttu-id="3ff33-141">`--test-dataset | -t` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="3ff33-142">Путь к файлу набора данных теста, например при использовании подхода 80–20 % при выполнении регулярных валидаций для получения показателей точности.</span><span class="sxs-lookup"><span data-stu-id="3ff33-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="3ff33-143">При использовании `--test-dataset` параметр `--dataset` также является обязательным.</span><span class="sxs-lookup"><span data-stu-id="3ff33-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="3ff33-144">Аргумент `--test-dataset` является необязательным, если только не используется --validation-dataset.</span><span class="sxs-lookup"><span data-stu-id="3ff33-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="3ff33-145">В этом случае пользователь должен использовать три аргумента.</span><span class="sxs-lookup"><span data-stu-id="3ff33-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="3ff33-146">Набор данных для проверки</span><span class="sxs-lookup"><span data-stu-id="3ff33-146">Validation dataset</span></span>

<span data-ttu-id="3ff33-147">`--validation-dataset | -v` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="3ff33-148">Путь к файлу валидационного набора данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="3ff33-149">В любом случае валидационный набор данных является необязательным.</span><span class="sxs-lookup"><span data-stu-id="3ff33-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="3ff33-150">При использовании `validation dataset` должно быть следующее поведение:</span><span class="sxs-lookup"><span data-stu-id="3ff33-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="3ff33-151">Аргументы `test-dataset` и `--dataset` также являются обязательными.</span><span class="sxs-lookup"><span data-stu-id="3ff33-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="3ff33-152">Набор данных `validation-dataset` используется для оценки ошибки прогноза для выбора модели.</span><span class="sxs-lookup"><span data-stu-id="3ff33-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="3ff33-153">`test-dataset` используется для оценки ошибки обобщения конечной выбранной модели.</span><span class="sxs-lookup"><span data-stu-id="3ff33-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="3ff33-154">В идеале проверочный набор должен храниться в "хранилище" и добавляться только в конце анализа данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="3ff33-155">Обычно при использовании `validation dataset` с `test dataset` этап валидации состоит из двух частей.</span><span class="sxs-lookup"><span data-stu-id="3ff33-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="3ff33-156">В первой части вы просто смотрите на модели и выбираете наиболее эффективный подход с использованием проверочных данных (=валидация).</span><span class="sxs-lookup"><span data-stu-id="3ff33-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="3ff33-157">Затем можно оценить точность выбранного подхода (= проверка).</span><span class="sxs-lookup"><span data-stu-id="3ff33-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="3ff33-158">Таким образом, разделение данных может быть задано как 80-10-10 или 75-15-10.</span><span class="sxs-lookup"><span data-stu-id="3ff33-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="3ff33-159">Пример:</span><span class="sxs-lookup"><span data-stu-id="3ff33-159">For example:</span></span>

- <span data-ttu-id="3ff33-160">Файл `training-dataset` должен содержать 75 % данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="3ff33-161">Файл `validation-dataset` должен содержать 15 % данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="3ff33-162">Файл `test-dataset` должен содержать 10 % данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="3ff33-163">В любом случае эти проценты выбираются с помощью интерфейса командной строки, который будет предоставлять уже разделенные файлы.</span><span class="sxs-lookup"><span data-stu-id="3ff33-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="3ff33-164">Столбец метки</span><span class="sxs-lookup"><span data-stu-id="3ff33-164">Label column</span></span>

<span data-ttu-id="3ff33-165">`--label-col` (целочисленное или строковое значение)</span><span class="sxs-lookup"><span data-stu-id="3ff33-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="3ff33-166">С помощью этого аргумента можно задать определенную цель и целевой столбца (переменную, которую требуется спрогнозировать) с помощью имени столбца, заданного в заголовке набора данных, или числового индекса столбца в файле набора данных (значения индексов столбцов начинаются с 0).</span><span class="sxs-lookup"><span data-stu-id="3ff33-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="3ff33-167">Этот аргумент используется для *классификации* и *регрессии*.</span><span class="sxs-lookup"><span data-stu-id="3ff33-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="3ff33-168">Столбец элементов</span><span class="sxs-lookup"><span data-stu-id="3ff33-168">Item column</span></span>

<span data-ttu-id="3ff33-169">`--item-col` (целочисленное или строковое значение)</span><span class="sxs-lookup"><span data-stu-id="3ff33-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="3ff33-170">В столбце элементов содержится список элементов, которые оцениваются пользователями (эти элементы рекомендуются пользователям).</span><span class="sxs-lookup"><span data-stu-id="3ff33-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="3ff33-171">Этот столбец можно задать с использованием имени столбца, заданного в заголовке набора данных, или числового индекса столбца в файле набора данных (значения индексов столбцов начинаются с 0).</span><span class="sxs-lookup"><span data-stu-id="3ff33-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="3ff33-172">Этот аргумент используется только для задачи  *рекомендации*.</span><span class="sxs-lookup"><span data-stu-id="3ff33-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="3ff33-173">Столбец оценок</span><span class="sxs-lookup"><span data-stu-id="3ff33-173">Rating column</span></span>

<span data-ttu-id="3ff33-174">`--rating-col` (целочисленное или строковое значение)</span><span class="sxs-lookup"><span data-stu-id="3ff33-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="3ff33-175">Столбец оценок содержит список оценок, присвоенных пользователями элементам.</span><span class="sxs-lookup"><span data-stu-id="3ff33-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="3ff33-176">Этот столбец можно задать с использованием имени столбца, заданного в заголовке набора данных, или числового индекса столбца в файле набора данных (значения индексов столбцов начинаются с 0).</span><span class="sxs-lookup"><span data-stu-id="3ff33-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="3ff33-177">Этот аргумент используется только для задачи  *рекомендации*.</span><span class="sxs-lookup"><span data-stu-id="3ff33-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="3ff33-178">Столбец пользователей</span><span class="sxs-lookup"><span data-stu-id="3ff33-178">User column</span></span>

<span data-ttu-id="3ff33-179">`--user-col` (целочисленное или строковое значение)</span><span class="sxs-lookup"><span data-stu-id="3ff33-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="3ff33-180">В столбце пользователей содержится список пользователей, которые присваивают оценки элементам.</span><span class="sxs-lookup"><span data-stu-id="3ff33-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="3ff33-181">Этот столбец можно задать с использованием имени столбца, заданного в заголовке набора данных, или числового индекса столбца в файле набора данных (значения индексов столбцов начинаются с 0).</span><span class="sxs-lookup"><span data-stu-id="3ff33-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="3ff33-182">Этот аргумент используется только для задачи  *рекомендации*.</span><span class="sxs-lookup"><span data-stu-id="3ff33-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="3ff33-183">Игнорировать столбцы</span><span class="sxs-lookup"><span data-stu-id="3ff33-183">Ignore columns</span></span>

<span data-ttu-id="3ff33-184">`--ignore-columns` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="3ff33-185">С помощью этого аргумента можно игнорировать существующие столбцы в файле набора данных; они не загружаются и не используются процессами обучения.</span><span class="sxs-lookup"><span data-stu-id="3ff33-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="3ff33-186">Укажите имена столбцов, которые требуется игнорировать.</span><span class="sxs-lookup"><span data-stu-id="3ff33-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="3ff33-187">Используйте ", " (запятая с пробелом) или " " (пробел) для разделения нескольких имен столбцов.</span><span class="sxs-lookup"><span data-stu-id="3ff33-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="3ff33-188">Можно использовать кавычки для имен столбцов, содержащих пробелы (например, "Вход в систему").</span><span class="sxs-lookup"><span data-stu-id="3ff33-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="3ff33-189">Пример.</span><span class="sxs-lookup"><span data-stu-id="3ff33-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="3ff33-190">Имеет заголовок</span><span class="sxs-lookup"><span data-stu-id="3ff33-190">Has header</span></span>

<span data-ttu-id="3ff33-191">`--has-header` (логическое значение)</span><span class="sxs-lookup"><span data-stu-id="3ff33-191">`--has-header` (bool)</span></span>

<span data-ttu-id="3ff33-192">Укажите, содержат ли файлы набора данных строку заголовка.</span><span class="sxs-lookup"><span data-stu-id="3ff33-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="3ff33-193">Доступны следующие значения:</span><span class="sxs-lookup"><span data-stu-id="3ff33-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="3ff33-194">Если этот аргумент не задан пользователем, интерфейс командной строки ML.NET попытается обнаружить это свойство.</span><span class="sxs-lookup"><span data-stu-id="3ff33-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="3ff33-195">Время обучения</span><span class="sxs-lookup"><span data-stu-id="3ff33-195">Train time</span></span>

<span data-ttu-id="3ff33-196">`--train-time` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-196">`--train-time` (string)</span></span>

<span data-ttu-id="3ff33-197">По умолчанию максимальное время исследования/обучения составляет 30 минут.</span><span class="sxs-lookup"><span data-stu-id="3ff33-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="3ff33-198">Этот аргумент задает максимальное время (в секундах) для процесса изучения различных учителей и конфигураций.</span><span class="sxs-lookup"><span data-stu-id="3ff33-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="3ff33-199">Заданное время может быть превышено, если указанное время слишком мало (скажем, 2 секунды) для одной итерации.</span><span class="sxs-lookup"><span data-stu-id="3ff33-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="3ff33-200">В этом случае фактическое время — это время, необходимое для создания одной модели конфигурации в одной итерации.</span><span class="sxs-lookup"><span data-stu-id="3ff33-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="3ff33-201">Требуемое время для итераций зависит от размера набора данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="3ff33-202">Кэш</span><span class="sxs-lookup"><span data-stu-id="3ff33-202">Cache</span></span>

<span data-ttu-id="3ff33-203">`--cache` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-203">`--cache` (string)</span></span>

<span data-ttu-id="3ff33-204">При использовании кэширования весь обучающий набор данных будет загружен в память.</span><span class="sxs-lookup"><span data-stu-id="3ff33-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="3ff33-205">Для малых и средних наборов данных с помощью кэша можно существенно улучшить производительность обучения; это означает, что время обучения может быть короче, чем в ситуации, если кэш не используется.</span><span class="sxs-lookup"><span data-stu-id="3ff33-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="3ff33-206">Тем не менее на большие наборы данных загрузка всех данных в память может повлиять отрицательно, так как может возникнуть нехватка памяти.</span><span class="sxs-lookup"><span data-stu-id="3ff33-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="3ff33-207">В случае обучения с большими файлами набора данных без использования кэша ML.NET будет потоком передавать блоки данных с диска при необходимости загрузить дополнительные данные во время обучения.</span><span class="sxs-lookup"><span data-stu-id="3ff33-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="3ff33-208">Можно указать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="3ff33-208">You can specify the following values:</span></span>

<span data-ttu-id="3ff33-209">`on`. принудительно включает кэш при обучении;</span><span class="sxs-lookup"><span data-stu-id="3ff33-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="3ff33-210">`off`. принудительно отключает кэш при обучении;</span><span class="sxs-lookup"><span data-stu-id="3ff33-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="3ff33-211">`auto`. кэш будет использоваться в зависимости от эвристики AutoML.</span><span class="sxs-lookup"><span data-stu-id="3ff33-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="3ff33-212">Как правило, для небольших и средних наборов данных будет использоваться кэш; большие наборы данных не будут использовать кэш, если вы укажете `auto`.</span><span class="sxs-lookup"><span data-stu-id="3ff33-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="3ff33-213">Если вы не укажете параметр `--cache`, то для кэша `auto` будет использована конфигурация по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3ff33-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="3ff33-214">name</span><span class="sxs-lookup"><span data-stu-id="3ff33-214">Name</span></span>

<span data-ttu-id="3ff33-215">`--name` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-215">`--name` (string)</span></span>

<span data-ttu-id="3ff33-216">Имя для создаваемых выходных проекта или решения.</span><span class="sxs-lookup"><span data-stu-id="3ff33-216">The name for the created output project or solution.</span></span> <span data-ttu-id="3ff33-217">Если имя не задано, используется имя `sample-{mltask}`.</span><span class="sxs-lookup"><span data-stu-id="3ff33-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="3ff33-218">Файл модели ML.NET (ZIP-файл) получит то же имя.</span><span class="sxs-lookup"><span data-stu-id="3ff33-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="3ff33-219">Путь для создаваемых файлов</span><span class="sxs-lookup"><span data-stu-id="3ff33-219">Output path</span></span>

<span data-ttu-id="3ff33-220">`--output | -o` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-220">`--output | -o` (string)</span></span>

<span data-ttu-id="3ff33-221">Корневое расположение или папка для размещения созданных выходных данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="3ff33-222">Значением по умолчанию является текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="3ff33-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="3ff33-223">Уровень детализации</span><span class="sxs-lookup"><span data-stu-id="3ff33-223">Verbosity</span></span>

<span data-ttu-id="3ff33-224">`--verbosity | -v` (строка)</span><span class="sxs-lookup"><span data-stu-id="3ff33-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="3ff33-225">Задает уровень детализации стандартных выходных данных.</span><span class="sxs-lookup"><span data-stu-id="3ff33-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="3ff33-226">Допустимыми значениями являются:</span><span class="sxs-lookup"><span data-stu-id="3ff33-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="3ff33-227">`m[inimal]` (по умолчанию);</span><span class="sxs-lookup"><span data-stu-id="3ff33-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="3ff33-228">`diag[nostic]` (уровень ведения журнала).</span><span class="sxs-lookup"><span data-stu-id="3ff33-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="3ff33-229">По умолчанию программа командной строки должна отображать минимальные данные обратной связи (`minimal`) во время работы, например отметить, что она работает и (по возможности) сколько времени уйдет на завершение работы.</span><span class="sxs-lookup"><span data-stu-id="3ff33-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="3ff33-230">Справка</span><span class="sxs-lookup"><span data-stu-id="3ff33-230">Help</span></span>

`-h |--help`

<span data-ttu-id="3ff33-231">Выводит справку для команды с описанием каждого аргумента.</span><span class="sxs-lookup"><span data-stu-id="3ff33-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ff33-232">См. также</span><span class="sxs-lookup"><span data-stu-id="3ff33-232">See also</span></span>

- [<span data-ttu-id="3ff33-233">Установка интерфейса командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="3ff33-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="3ff33-234">Общие сведения о ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="3ff33-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="3ff33-235">Учебник. Анализ тональности с помощью интерфейса командной строки (CLI) ML.NET</span><span class="sxs-lookup"><span data-stu-id="3ff33-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="3ff33-236">Данные телеметрии в интерфейсе командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="3ff33-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
