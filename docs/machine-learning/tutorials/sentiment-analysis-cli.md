---
title: Анализ тональности с помощью интерфейса командной строки ML.NET
description: Автоматическое создание модели машинного обучения и связанного кода C# на основе примера набора данных
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 47c38bb0b66a6fc08dd319583847dd83baedcd1e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103703"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="d828d-103">Анализ тональности с помощью интерфейса командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="d828d-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="d828d-104">Узнайте, как с помощью ML.NET CLI автоматически создать модель ML.NET и базовый код C#.</span><span class="sxs-lookup"><span data-stu-id="d828d-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="d828d-105">Вы предоставите набор данных и задачу машинного обучения, которую требуется реализовать, а CLI с помощью подсистемы AutoML создаст исходный код для формирования и развертывания модели, а также модель классификации.</span><span class="sxs-lookup"><span data-stu-id="d828d-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the classification model.</span></span>

<span data-ttu-id="d828d-106">Работая с этим учебником, вы выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="d828d-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d828d-107">подготовку данных для выбранной задачи машинного обучения;</span><span class="sxs-lookup"><span data-stu-id="d828d-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="d828d-108">запуск команды mlnet classification из CLI;</span><span class="sxs-lookup"><span data-stu-id="d828d-108">Run the 'mlnet classification' command from the CLI</span></span>
> - <span data-ttu-id="d828d-109">просмотреть результаты показателей качества;</span><span class="sxs-lookup"><span data-stu-id="d828d-109">Review the quality metric results</span></span>
> - <span data-ttu-id="d828d-110">изучение созданного кода C# для использования модели в приложении;</span><span class="sxs-lookup"><span data-stu-id="d828d-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="d828d-111">анализ созданного кода C#, который использовался для обучения модели.</span><span class="sxs-lookup"><span data-stu-id="d828d-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="d828d-112">Здесь описано, как использовать средство ML.NET CLI, которое сейчас доступно в режиме предварительной версии. Этот материал может быть изменен.</span><span class="sxs-lookup"><span data-stu-id="d828d-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="d828d-113">Дополнительные сведения см. на странице [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d828d-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="d828d-114">ML.NET CLI входит в состав ML.NET, и его основной целью является упрощение изучения ML.NET для разработчиков .NET, поэтому, чтобы приступить к работе, не нужно писать код с нуля.</span><span class="sxs-lookup"><span data-stu-id="d828d-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="d828d-115">Для создания качественных моделей и исходного кода ML.NET на основе предоставляемых наборов обучающих данных средство ML.NET CLI можно запускать в любой командной строке (Windows, Mac или Linux).</span><span class="sxs-lookup"><span data-stu-id="d828d-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="d828d-116">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="d828d-116">Pre-requisites</span></span>

- <span data-ttu-id="d828d-117">[Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1) или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="d828d-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet/3.1) or later</span></span>
- <span data-ttu-id="d828d-118">(Необязательно.) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="d828d-118">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="d828d-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="d828d-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="d828d-120">Вы можете запускать проекты, написанные на C#, из Visual Studio или с помощью `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="d828d-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="d828d-121">подготавливать данные;</span><span class="sxs-lookup"><span data-stu-id="d828d-121">Prepare your data</span></span>

<span data-ttu-id="d828d-122">Мы будем работать с существующим набором данных, используемым в сценарии "Анализ тональности", который представляет собой задачу машинного обучения двоичной классификации.</span><span class="sxs-lookup"><span data-stu-id="d828d-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="d828d-123">Вы точно так же можете использовать собственный набор данных, а модель и код будут созданы автоматически.</span><span class="sxs-lookup"><span data-stu-id="d828d-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="d828d-124">Скачайте [ZIP-файл набора данных предложений с меткой тональности UCI (ссылка дана в следующем примечании)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) и распакуйте его в любую папку.</span><span class="sxs-lookup"><span data-stu-id="d828d-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d828d-125">Наборы данных в этом руководстве взяты из документа From Group to Individual Labels using Deep Features ("От групповых до индивидуальных меток с использованием функций глубокого обучения"), Котциас (Kotzias) и</span><span class="sxs-lookup"><span data-stu-id="d828d-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="d828d-126">KDD 2015, и размещены в репозитории машинного обучения UCI Д. Дуа (D. Dua) и Э. Карра Танискиду (E. Karra Taniskidou) (2017).</span><span class="sxs-lookup"><span data-stu-id="d828d-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="d828d-127">UCI Machine Learning Repository (Репозиторий машинного обучения UCI) [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="d828d-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="d828d-128">Ирвайн, Калифорния: Калифорнийский университет, Школа информационных технологий и компьютерных наук.</span><span class="sxs-lookup"><span data-stu-id="d828d-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="d828d-129">Скопируйте файл `yelp_labelled.txt` в созданную ранее папку (например, `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="d828d-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="d828d-130">Откройте предпочитаемую командную строку и перейдите к папке, куда был скопирован файл набора данных.</span><span class="sxs-lookup"><span data-stu-id="d828d-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="d828d-131">Пример:</span><span class="sxs-lookup"><span data-stu-id="d828d-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="d828d-132">Используйте любой текстовый редактор, например Visual Studio Code, чтобы открыть и проанализировать файл набора данных `yelp_labelled.txt`.</span><span class="sxs-lookup"><span data-stu-id="d828d-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="d828d-133">Вы увидите следующую структуру:</span><span class="sxs-lookup"><span data-stu-id="d828d-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="d828d-134">У файла нет заголовка.</span><span class="sxs-lookup"><span data-stu-id="d828d-134">The file has no header.</span></span> <span data-ttu-id="d828d-135">Вы будете использовать индекс столбца.</span><span class="sxs-lookup"><span data-stu-id="d828d-135">You will use the column's index.</span></span>

    - <span data-ttu-id="d828d-136">Существует только два столбца:</span><span class="sxs-lookup"><span data-stu-id="d828d-136">There are just two columns:</span></span>

        | <span data-ttu-id="d828d-137">Текст (индекс столбца — 0)</span><span class="sxs-lookup"><span data-stu-id="d828d-137">Text (Column index 0)</span></span> | <span data-ttu-id="d828d-138">Надпись (индекс столбца — 1)</span><span class="sxs-lookup"><span data-stu-id="d828d-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="d828d-139">Ого... Отличное место.</span><span class="sxs-lookup"><span data-stu-id="d828d-139">Wow... Loved this place.</span></span> | <span data-ttu-id="d828d-140">1</span><span class="sxs-lookup"><span data-stu-id="d828d-140">1</span></span> |
        | <span data-ttu-id="d828d-141">Корочка так себе.</span><span class="sxs-lookup"><span data-stu-id="d828d-141">Crust is not good.</span></span> | <span data-ttu-id="d828d-142">0</span><span class="sxs-lookup"><span data-stu-id="d828d-142">0</span></span> |
        | <span data-ttu-id="d828d-143">Невкусно, и текстура просто отвратительна.</span><span class="sxs-lookup"><span data-stu-id="d828d-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="d828d-144">0</span><span class="sxs-lookup"><span data-stu-id="d828d-144">0</span></span> |
        | <span data-ttu-id="d828d-145">…ЕЩЕ БОЛЬШЕ СТРОК ТЕКСТА…</span><span class="sxs-lookup"><span data-stu-id="d828d-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="d828d-146">…(1 или 0)…</span><span class="sxs-lookup"><span data-stu-id="d828d-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="d828d-147">Закройте файл набора данных в редакторе.</span><span class="sxs-lookup"><span data-stu-id="d828d-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="d828d-148">Теперь вы готовы использовать CLI в сценарии "Анализ тональности".</span><span class="sxs-lookup"><span data-stu-id="d828d-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d828d-149">После завершения работы с этим руководством попробуйте применить собственные наборы данных, при условии что они подходят для любой задачи машинного обучения, поддерживаемой в предварительной версии ML.NET CLI, — *"Двоичная классификация", "Классификация", "Регрессия"* и *"Рекомендация"* .</span><span class="sxs-lookup"><span data-stu-id="d828d-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Classification', 'Regression',* and *'Recommendation'*.</span></span>

## <a name="run-the-mlnet-classification-command"></a><span data-ttu-id="d828d-150">Выполнение команды mlnet classification</span><span class="sxs-lookup"><span data-stu-id="d828d-150">Run the 'mlnet classification' command</span></span>

1. <span data-ttu-id="d828d-151">Выполните следующую команду ML.NET CLI:</span><span class="sxs-lookup"><span data-stu-id="d828d-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    <span data-ttu-id="d828d-152">Эта команда запускает **`mlnet classification`команду**:</span><span class="sxs-lookup"><span data-stu-id="d828d-152">This command runs the **`mlnet classification` command**:</span></span>
    - <span data-ttu-id="d828d-153">для **задачи машинного обучения** *классификации*;</span><span class="sxs-lookup"><span data-stu-id="d828d-153">for the **ML task** of *classification*</span></span>
    - <span data-ttu-id="d828d-154">использует **файл набора данных `yelp_labelled.txt`** в качестве обучающего и тестового набора данных (CLI внутренним образом применит перекрестную проверку или разделит его на два набора данных — один для обучения и один для тестирования);</span><span class="sxs-lookup"><span data-stu-id="d828d-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="d828d-155">где **целевой столбец** (обычно называемый **меткой**), который нужно спрогнозировать представляет собой **столбец с индексом 1** (то есть второй столбец, поскольку индекс отсчитывается от нуля);</span><span class="sxs-lookup"><span data-stu-id="d828d-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="d828d-156">**не использует заголовок файла** с именами столбцов, так как у этого конкретного файла набора данных нет заголовка;</span><span class="sxs-lookup"><span data-stu-id="d828d-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="d828d-157">**целевое время изучения или обучения** в эксперименте составляет **10 секунд**.</span><span class="sxs-lookup"><span data-stu-id="d828d-157">the **targeted exploration/train time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="d828d-158">Вы увидите выходные данные CLI, аналогичные следующим:</span><span class="sxs-lookup"><span data-stu-id="d828d-158">You will see output from the CLI, similar to:</span></span>

    ![Классификация CLI ML.NET в PowerShell](./media/mlnet-cli/mlnet-classification-powershell.gif)

    <span data-ttu-id="d828d-160">В данном случае, когда у средства CLI было всего 10 секунд и небольшой набор данных, ему удалось выполнить довольно много итераций, то есть провести обучение несколько раз на основе сочетаний различных алгоритмов или конфигурации с преобразованиями различных внутренних данных и гиперпараметров алгоритма.</span><span class="sxs-lookup"><span data-stu-id="d828d-160">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="d828d-161">В итоге за 10 секунд найдена модель высшего качества с определенным алгоритмом обучения и конкретной конфигурацией.</span><span class="sxs-lookup"><span data-stu-id="d828d-161">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="d828d-162">В зависимости от времени изучения команда может выдать другой результат.</span><span class="sxs-lookup"><span data-stu-id="d828d-162">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="d828d-163">Выбор производится с учетом нескольких отображаемых метрик, таких как `Accuracy`.</span><span class="sxs-lookup"><span data-stu-id="d828d-163">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="d828d-164">**Общие сведения о метриках качества модели**</span><span class="sxs-lookup"><span data-stu-id="d828d-164">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="d828d-165">Первая и самая простая для понимания метрика оценки модели двоичной классификации — точность.</span><span class="sxs-lookup"><span data-stu-id="d828d-165">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="d828d-166">"Точность — это доля правильных прогнозов на основе тестового набора данных".</span><span class="sxs-lookup"><span data-stu-id="d828d-166">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="d828d-167">Чем ближе к 100 % (1,00), тем лучше.</span><span class="sxs-lookup"><span data-stu-id="d828d-167">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="d828d-168">Однако бывают случаи, когда оценки с помощью одной метрики точности недостаточно, особенно если метка (0 и 1 в данном случае) несбалансирована в тестовом наборе данных.</span><span class="sxs-lookup"><span data-stu-id="d828d-168">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="d828d-169">Сведения о [дополнительных метриках и **подробные сведения о метриках** ML.NET (точность, AUC, AUCPR, F1-мера, которые используются для оценки различных моделей)](../resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="d828d-169">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="d828d-170">Можно взять этот же набор данных и указать для `--max-exploration-time` несколько минут (например, три минуты или 180 секунд), и в результате вы получите модель еще лучшего качества с другой конфигурацией обучающего конвейера для этого набора данных (размером 1000 строк).</span><span class="sxs-lookup"><span data-stu-id="d828d-170">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="d828d-171">Чтобы найти готовую для работы модель высшего или хорошего качества, предназначенную для крупных наборов данных, необходимо проводить эксперименты с помощью CLI, указывая более продолжительное время изучения в зависимости от размера набора данных.</span><span class="sxs-lookup"><span data-stu-id="d828d-171">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="d828d-172">На самом деле во многих случаях может потребоваться несколько часов, особенно если речь идет о наборе данных с большим числом строк и столбцов.</span><span class="sxs-lookup"><span data-stu-id="d828d-172">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="d828d-173">В результате выполнения предыдущей команды создаются следующие активы:</span><span class="sxs-lookup"><span data-stu-id="d828d-173">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="d828d-174">готовый к использованию ZIP-файл сериализованной модели ("модели высшего качества");</span><span class="sxs-lookup"><span data-stu-id="d828d-174">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="d828d-175">код C# для запуска или оценки созданной модели (для прогнозирования в приложениях пользователей);</span><span class="sxs-lookup"><span data-stu-id="d828d-175">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="d828d-176">обучающий код C#, используемый для создания этой модели (в целях обучения);</span><span class="sxs-lookup"><span data-stu-id="d828d-176">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="d828d-177">файл журнала со всеми изученными итерациями, содержащими подробные сведения о каждом опробованном алгоритме с сочетанием его гиперпараметров и преобразований данных.</span><span class="sxs-lookup"><span data-stu-id="d828d-177">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="d828d-178">Первые два актива (ZIP-файл модели и код C# для запуска этой модели) можно использовать непосредственно в приложениях конечных пользователей (веб-приложениях и службах ASP.NET Core, классических приложениях и т. д.) для прогнозирования с помощью созданной модели машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="d828d-178">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="d828d-179">Третий актив, обучающий код, показывает, какой код ML.NET API использовало средство CLI для обучения созданной модели, поэтому можно определить, какой конкретный алгоритм обучения и гиперпараметры были выбраны средством CLI.</span><span class="sxs-lookup"><span data-stu-id="d828d-179">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="d828d-180">Эти активы ресурсы рассматриваются в следующих шагах руководства.</span><span class="sxs-lookup"><span data-stu-id="d828d-180">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="d828d-181">Изучение созданного кода C# для запуска модели прогнозирования</span><span class="sxs-lookup"><span data-stu-id="d828d-181">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="d828d-182">В Visual Studio (2017 или 2019) откройте созданное решение в папке `SampleClassification`, находящейся в исходной конечной папке (имя папки в учебнике — `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="d828d-182">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="d828d-183">Вы увидите решение, аналогичное следующему:</span><span class="sxs-lookup"><span data-stu-id="d828d-183">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="d828d-184">В этом руководстве рекомендуется использовать Visual Studio, но можно также изучить созданный код C# (два проекта) в любом текстовом редакторе и запустить созданное консольное приложение с помощью `dotnet CLI` на компьютерах с ОС macOS, Windows или Linux.</span><span class="sxs-lookup"><span data-stu-id="d828d-184">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Решение VS, созданное с помощью CLI](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - <span data-ttu-id="d828d-186">Созданную **библиотеку классов**, содержащую сериализованную модель машинного обучения (в ZiP-файле) и классы данных (модели данных), можно использовать непосредственно в приложениях конечных пользователей даже путем прямого указания на нее (или путем перемещения кода).</span><span class="sxs-lookup"><span data-stu-id="d828d-186">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="d828d-187">Созданное **консольное приложение** содержит код выполнения, который нужно проверить, после чего можно многократно использовать код оценки (код, который запускает модель машинного обучения для прогнозирования), перемещая этот простой код (всего несколько строк) в приложения конечных пользователей для прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="d828d-187">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="d828d-188">Откройте файлы классов **ModelInput.cs** и **ModelOutput.cs** в проекте библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="d828d-188">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="d828d-189">Вы увидите, что это классы данных или классы POCO, используемые для хранения данных.</span><span class="sxs-lookup"><span data-stu-id="d828d-189">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="d828d-190">Это стереотипный код, который удобно использовать, если в наборе данных десятки или даже сотни столбцов.</span><span class="sxs-lookup"><span data-stu-id="d828d-190">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="d828d-191">Класс `ModelInput` используется при чтении данных из набора данных.</span><span class="sxs-lookup"><span data-stu-id="d828d-191">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="d828d-192">Класс `ModelOutput` используется для получения результата прогнозирования (данные прогнозирования).</span><span class="sxs-lookup"><span data-stu-id="d828d-192">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="d828d-193">Откройте файл Program.cs и изучите код.</span><span class="sxs-lookup"><span data-stu-id="d828d-193">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="d828d-194">С помощью всего нескольких строк вы сможете запустить модель и создать пример прогноза.</span><span class="sxs-lookup"><span data-stu-id="d828d-194">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - В первых строках этого кода создается *один образец данных*, который в этом случае основывается на первой строке набора данных, используемого для составления прогноза. <span data-ttu-id="d828d-196">Вы также можете создать собственные жестко запрограммированные данные, обновив следующий код.</span><span class="sxs-lookup"><span data-stu-id="d828d-196">You can also create you own 'hard-coded' data by updating the code:</span></span>

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - <span data-ttu-id="d828d-197">В следующей строке кода к заданным входным данным применяется метод `ConsumeModel.Predict()`, который позволяет составить прогноз и возвращает результаты (на основе схемы ModelOutput.cs).</span><span class="sxs-lookup"><span data-stu-id="d828d-197">The next line of code uses the `ConsumeModel.Predict()` method on the specified input data to make a prediction and return the results (based on the ModelOutput.cs schema).</span></span>
    - <span data-ttu-id="d828d-198">В последних строках кода выводятся свойства образца данных (в этом случае комментарии), а также прогноз тональности и соответствующие оценки положительной (1) и отрицательной тональности (2).</span><span class="sxs-lookup"><span data-stu-id="d828d-198">The last lines of code print out the properties of the sample data (in this case the Comment) as well as the Sentiment prediction and corresponding Scores for positive sentiment (1) and negative sentiment (2).</span></span>

1. <span data-ttu-id="d828d-199">Запустите проект с помощью исходного примера данных, загруженного из первой строки набора данных, или предоставьте пример собственных настраиваемых жестко закодированных данных.</span><span class="sxs-lookup"><span data-stu-id="d828d-199">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="d828d-200">Вы должны получить прогноз, аналогичный следующему:</span><span class="sxs-lookup"><span data-stu-id="d828d-200">You should get a prediction comparable to:</span></span>

![Запуск приложения CLI ML.NET из Visual Studio](./media/mlnet-cli/mlnet-cli-console-app.png)<span data-ttu-id="d828d-202">)</span><span class="sxs-lookup"><span data-stu-id="d828d-202">)</span></span>

1. <span data-ttu-id="d828d-203">Попробуйте изменить пример жестко закодированных данных на другие предложения с различной тональностью и посмотрите, как модель прогнозирует положительную или отрицательную тональность.</span><span class="sxs-lookup"><span data-stu-id="d828d-203">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="d828d-204">Внедрение приложений для конечных пользователей с прогнозами модели машинного обучения</span><span class="sxs-lookup"><span data-stu-id="d828d-204">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="d828d-205">Запускать модель в приложении конечного пользователя и делать прогнозы можно с помощью аналогичного кода для оценки модели машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="d828d-205">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="d828d-206">Например, этот код можно переместить прямо в классическое приложение Windows, такое как **WPF** и **WinForms**, и запустить модель так же, как в консольном приложении.</span><span class="sxs-lookup"><span data-stu-id="d828d-206">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="d828d-207">Однако способ реализации этих строк кода для запуска модели машинного обучения необходимо оптимизировать (то есть кэшировать и один раз загрузить ZIP-файл модели) и использовать одноэлементные модели, а не создавать их при каждом запросе, особенно в том случае, если приложение (веб-приложение или распределенная служба) должно быть масштабируемым, как описано в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="d828d-207">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="d828d-208">Запуск моделей ML.NET в масштабируемых веб-приложениях и службах ASP.NET Core (многопоточных приложениях)</span><span class="sxs-lookup"><span data-stu-id="d828d-208">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="d828d-209">Процесс создания объекта модели (объекта `ITransformer`, загруженного из ZIP-файла модели) и объекта `PredictionEngine` должен быть оптимизирован, особенно при запуске в масштабируемых веб-приложениях и распределенных службах.</span><span class="sxs-lookup"><span data-stu-id="d828d-209">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="d828d-210">Оптимизация первого объекта модели (`ITransformer`) не вызывает трудностей.</span><span class="sxs-lookup"><span data-stu-id="d828d-210">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="d828d-211">Так как объект `ITransformer` является потокобезопасным, его можно кэшировать как одноэлементный или статический, чтобы загружать модель всего один раз.</span><span class="sxs-lookup"><span data-stu-id="d828d-211">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="d828d-212">Для второго объекта `PredictionEngine` сделать это не так просто, поскольку объект `PredictionEngine` не является потокобезопасным и вы не можете создать его экземпляр в виде одноэлементного или статического объекта в приложении ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d828d-212">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="d828d-213">Проблема потокобезопасности и масштабируемости подробно рассматривается в этой [публикации блога](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="d828d-213">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="d828d-214">Но сейчас все стало намного проще.</span><span class="sxs-lookup"><span data-stu-id="d828d-214">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="d828d-215">Мы разработали упрощенный подход и создали отличный **пакет интеграции .NET Core** для использования в приложениях и службах ASP.NET Core. Его нужно зарегистрировать в службах внедрения зависимостей приложения и затем использовать напрямую из кода.</span><span class="sxs-lookup"><span data-stu-id="d828d-215">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="d828d-216">См. инструкции в следующих руководствах и примерах:</span><span class="sxs-lookup"><span data-stu-id="d828d-216">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="d828d-217">Учебник. Запуск моделей ML.NET в масштабируемых веб-приложениях и веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d828d-217">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
- [<span data-ttu-id="d828d-218">Пример. Масштабируемая модель ML.NET в веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d828d-218">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="d828d-219">Изучение созданного кода C#, который использовался для модели высшего качества</span><span class="sxs-lookup"><span data-stu-id="d828d-219">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="d828d-220">Для получения более глубоких знаний изучите созданный код C#, который использовался для обучения модели средством CLI.</span><span class="sxs-lookup"><span data-stu-id="d828d-220">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="d828d-221">Сейчас этот обучающий код модели создается в пользовательском классе с именем `ModelBuilder` и доступен для изучения.</span><span class="sxs-lookup"><span data-stu-id="d828d-221">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="d828d-222">Что еще более важно, можно сравнить созданный для этого конкретного сценария (модель анализа тональности) обучающий код с кодом, приведенным в следующем учебнике.</span><span class="sxs-lookup"><span data-stu-id="d828d-222">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="d828d-223">Сравните: [Учебник. Использование ML.NET для анализа тональности методом двоичной классификации](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="d828d-223">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="d828d-224">Будет интересно сравнить выбранный алгоритм и конфигурацию конвейера в этом руководстве с кодом, созданным с помощью средства CLI.</span><span class="sxs-lookup"><span data-stu-id="d828d-224">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="d828d-225">В зависимости от продолжительности поиска оптимальных моделей вы можете выбрать особый алгоритм с собственными гиперпараметрами и конфигурацией конвейера.</span><span class="sxs-lookup"><span data-stu-id="d828d-225">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="d828d-226">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="d828d-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d828d-227">подготовить данные для выбранной задачи машинного обучения (устраняемой проблемы);</span><span class="sxs-lookup"><span data-stu-id="d828d-227">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="d828d-228">запускать команду mlnet classification из средства CLI;</span><span class="sxs-lookup"><span data-stu-id="d828d-228">Run the 'mlnet classification' command in the CLI tool</span></span>
> - <span data-ttu-id="d828d-229">просмотреть результаты показателей качества;</span><span class="sxs-lookup"><span data-stu-id="d828d-229">Review the quality metric results</span></span>
> - <span data-ttu-id="d828d-230">понять созданный код C# код для запуска модели (код, используемый в приложении конечных пользователей);</span><span class="sxs-lookup"><span data-stu-id="d828d-230">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="d828d-231">изучить созданный код C#, который использовался для модели высшего качества (в целях обучения).</span><span class="sxs-lookup"><span data-stu-id="d828d-231">Explore the generated C# code that was used to train the "best quality" model (earning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="d828d-232">См. также</span><span class="sxs-lookup"><span data-stu-id="d828d-232">See also</span></span>

- [<span data-ttu-id="d828d-233">Автоматизация обучения модели с помощью интерфейса командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="d828d-233">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="d828d-234">Учебник. Запуск моделей ML.NET в масштабируемых веб-приложениях и веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d828d-234">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
- [<span data-ttu-id="d828d-235">Пример. Масштабируемая модель ML.NET в веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d828d-235">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="d828d-236">Справочное руководство по команде auto-train в ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="d828d-236">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="d828d-237">Данные телеметрии в интерфейсе командной строки ML.NET</span><span class="sxs-lookup"><span data-stu-id="d828d-237">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
