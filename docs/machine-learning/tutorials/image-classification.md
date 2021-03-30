---
title: Учебник. Модель классификации изображений ML.NET из TensorFlow
description: Узнайте, как передавать знания из существующей модели TensorFlow в новую модель классификации изображений ML.NET. Модель TensorFlow была обучена для классификации изображений по тысячам категорий. Модель ML.NET использует передачу обучения, чтобы классифицировать изображения по меньшему количеству более широких категорий.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: b3e5617979d1635248f87db6008d3e234bb3ffc5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104877037"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="deccc-105">Учебник. Создание модели классификации изображений ML.NET на основе предварительно обученной модели TensorFlow</span><span class="sxs-lookup"><span data-stu-id="deccc-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="deccc-106">Узнайте, как передавать знания из существующей модели TensorFlow в новую модель классификации изображений ML.NET.</span><span class="sxs-lookup"><span data-stu-id="deccc-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="deccc-107">Модель TensorFlow была обучена для классификации изображений по тысячам категорий.</span><span class="sxs-lookup"><span data-stu-id="deccc-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="deccc-108">Модель ML.NET использует часть модели TensorFlow в своем конвейере для обучения модели, классифицирующей изображения по 3-м категориям.</span><span class="sxs-lookup"><span data-stu-id="deccc-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="deccc-109">Обучение модели для [классификации изображений](https://en.wikipedia.org/wiki/Outline_of_object_recognition) с нуля предусматривает настройку нескольких миллионов параметров, а также использование огромных объемов помеченных данных обучения и вычислительных ресурсов (сотни часов работы GPU).</span><span class="sxs-lookup"><span data-stu-id="deccc-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="deccc-110">Хотя передача обучения не настолько эффективна, как обучение пользовательской модели с нуля, этот подход позволяет значительно ускорить соответствующий процесс с использованием всего нескольких тысяч изображений (а не миллионов помеченных изображений) для быстрого создания пользовательской модели (в пределах часа на компьютере без GPU).</span><span class="sxs-lookup"><span data-stu-id="deccc-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="deccc-111">В этом учебнике этот процесс еще более уменьшен: используется только десяток изображений для обучения.</span><span class="sxs-lookup"><span data-stu-id="deccc-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="deccc-112">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="deccc-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="deccc-113">Определение проблемы</span><span class="sxs-lookup"><span data-stu-id="deccc-113">Understand the problem</span></span>
> * <span data-ttu-id="deccc-114">внедрить предварительно обученную модель TensorFlow в конвейер ML.NET;</span><span class="sxs-lookup"><span data-stu-id="deccc-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="deccc-115">обучить и оценить модель ML.NET;</span><span class="sxs-lookup"><span data-stu-id="deccc-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="deccc-116">классифицировать тестовое изображение.</span><span class="sxs-lookup"><span data-stu-id="deccc-116">Classify a test image</span></span>

<span data-ttu-id="deccc-117">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="deccc-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="deccc-118">Обратите внимание на то, что по умолчанию конфигурации проекта .NET в этом руководстве предназначена для .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="deccc-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="deccc-119">Что собой представляет передача обучения?</span><span class="sxs-lookup"><span data-stu-id="deccc-119">What is transfer learning?</span></span>

<span data-ttu-id="deccc-120">Передача обучения — это процесс использования знаний, полученных при решении одной проблемы, и применения их к другой, но похожей проблеме.</span><span class="sxs-lookup"><span data-stu-id="deccc-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="deccc-121">В этом учебнике используется часть модели TensorFlow, обученной для классификации изображений по тысяче категорий, в модели ML.NET, которая классифицирует изображения по 3-м категориям.</span><span class="sxs-lookup"><span data-stu-id="deccc-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="deccc-122">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="deccc-122">Prerequisites</span></span>

* <span data-ttu-id="deccc-123">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="deccc-123">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="deccc-124">ZIP-файл каталога ресурсов руководства.</span><span class="sxs-lookup"><span data-stu-id="deccc-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="deccc-125">Модель машинного обучения Inception версии 1</span><span class="sxs-lookup"><span data-stu-id="deccc-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="deccc-126">Выбор типа задачи машинного обучения</span><span class="sxs-lookup"><span data-stu-id="deccc-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="deccc-127">Глубокое обучение</span><span class="sxs-lookup"><span data-stu-id="deccc-127">Deep learning</span></span>

<span data-ttu-id="deccc-128">[Глубокое обучение](https://en.wikipedia.org/wiki/Deep_learning) — это разновидность машинного обучения, которая произвела революцию в области компьютерного зрения и распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="deccc-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="deccc-129">Модели глубокого обучения обучаются на крупных наборах [помеченных данных](https://en.wikipedia.org/wiki/Labeled_data) с использованием [нейронных сетей](https://en.wikipedia.org/wiki/Artificial_neural_network), которые содержат множество слоев обучения.</span><span class="sxs-lookup"><span data-stu-id="deccc-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="deccc-130">Глубокое обучение:</span><span class="sxs-lookup"><span data-stu-id="deccc-130">Deep learning:</span></span>

* <span data-ttu-id="deccc-131">лучше выполняет некоторые задачи, например в области компьютерного зрения;</span><span class="sxs-lookup"><span data-stu-id="deccc-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="deccc-132">Требует огромных объемов данных для обучения.</span><span class="sxs-lookup"><span data-stu-id="deccc-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="deccc-133">Классификация изображений — это типичная задача Машинного обучения, которая позволяет автоматически классифицировать изображения по категориям, например:</span><span class="sxs-lookup"><span data-stu-id="deccc-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="deccc-134">для определения того, содержит ли изображение человеческое лицо;</span><span class="sxs-lookup"><span data-stu-id="deccc-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="deccc-135">для различения изображений котов и собак.</span><span class="sxs-lookup"><span data-stu-id="deccc-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="deccc-136">Она также помогает определить тип объекта на изображении — еда, игрушка или прибор:</span><span class="sxs-lookup"><span data-stu-id="deccc-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="deccc-137">![Изображение с пиццей](./media/image-classification/220px-Pepperoni_pizza.jpg)
![Изображение с плюшевым мишкой](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![Изображение с тостером](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="deccc-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="deccc-138">Изображения выше принадлежат Викискладу и имеют следующие атрибуты:</span><span class="sxs-lookup"><span data-stu-id="deccc-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="deccc-139">220px-Pepperoni_pizza.jpg, открытый источник, <https://commons.wikimedia.org/w/index.php?curid=79505>;</span><span class="sxs-lookup"><span data-stu-id="deccc-139">"220px-Pepperoni_pizza.jpg" Public Domain, <https://commons.wikimedia.org/w/index.php?curid=79505>,</span></span>
> * <span data-ttu-id="deccc-140">119px-Nalle_-_a_small_brown_teddy_bear.jpg, автор — [Jonik](https://commons.wikimedia.org/wiki/User:Jonik), автофотография, лицензия CC BY-SA 2.0, <https://commons.wikimedia.org/w/index.php?curid=48166>;</span><span class="sxs-lookup"><span data-stu-id="deccc-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, <https://commons.wikimedia.org/w/index.php?curid=48166>.</span></span>
> * <span data-ttu-id="deccc-141">193px-Broodrooster.jpg, автор — [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972), собственное фото, лицензия CC BY-SA 3.0, <https://commons.wikimedia.org/w/index.php?curid=27403>.</span><span class="sxs-lookup"><span data-stu-id="deccc-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, <https://commons.wikimedia.org/w/index.php?curid=27403></span></span>

<span data-ttu-id="deccc-142">Модель `Inception model` обучена классифицировать изображения по тысяче категорий, но в этом учебнике вам столько категорий не нужно. Вам также нужны четко определенные категории.</span><span class="sxs-lookup"><span data-stu-id="deccc-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="deccc-143">Перейдем к этапу передачи (`transfer`) этого процесса передачи обучения (`transfer learning`).</span><span class="sxs-lookup"><span data-stu-id="deccc-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="deccc-144">Вы можете передать способность `Inception model` распознавать и классифицировать изображения в новые ограниченные категории своего классификатора изображений.</span><span class="sxs-lookup"><span data-stu-id="deccc-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="deccc-145">еда;</span><span class="sxs-lookup"><span data-stu-id="deccc-145">Food</span></span>
* <span data-ttu-id="deccc-146">игрушка;</span><span class="sxs-lookup"><span data-stu-id="deccc-146">Toy</span></span>
* <span data-ttu-id="deccc-147">прибор.</span><span class="sxs-lookup"><span data-stu-id="deccc-147">Appliance</span></span>

<span data-ttu-id="deccc-148">В этом учебнике используется модель глубокого обучения TensorFlow [Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), популярная модель распознавания изображений, обученная с помощью набора данных `ImageNet`.</span><span class="sxs-lookup"><span data-stu-id="deccc-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="deccc-149">Модель TensorFlow классифицирует все изображения по тысячам классов, таких как "зонт", "жакет" и "посудомоечная машина".</span><span class="sxs-lookup"><span data-stu-id="deccc-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="deccc-150">Так как `Inception model` уже обучена на тысячах различных изображений, она содержит [признаки изображений](https://en.wikipedia.org/wiki/Feature_(computer_vision)), необходимые для их идентификации.</span><span class="sxs-lookup"><span data-stu-id="deccc-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="deccc-151">Мы можем использовать эти внутренние признаки изображений в модели для обучения новой модели с гораздо меньшим числом классов.</span><span class="sxs-lookup"><span data-stu-id="deccc-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="deccc-152">Как показано на схеме ниже, вам нужно добавить ссылки на пакеты NuGet ML.NET в приложения .NET Core или .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="deccc-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="deccc-153">На внутреннем уровне ML.NET включает и ссылается на встроенную библиотеку `TensorFlow`, которая позволяет создавать код, загружающий существующую обученную модель `TensorFlow`.</span><span class="sxs-lookup"><span data-stu-id="deccc-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Схема преобразования ML.NET с использованием TensorFlow](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="deccc-155">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="deccc-155">Multiclass classification</span></span>

<span data-ttu-id="deccc-156">После использования модели Inception TensorFlow для извлечения признаков, подходящих в качестве входных данных для классического алгоритма машинного обучения, мы добавим [многоклассовый классификатор](../resources/tasks.md#multiclass-classification) ML.NET.</span><span class="sxs-lookup"><span data-stu-id="deccc-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="deccc-157">В этом случае используется алгоритм [мультиномиальной логистической регрессии](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="deccc-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="deccc-158">Алгоритм, реализованный этим инструктором, хорошо работает в задачах с большим количеством признаков, что характерно для модели глубокого обучения, работающей с данными изображений.</span><span class="sxs-lookup"><span data-stu-id="deccc-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="deccc-159">Данные</span><span class="sxs-lookup"><span data-stu-id="deccc-159">Data</span></span>

<span data-ttu-id="deccc-160">Доступны два источника данных: файл `.tsv` и файлы образов.</span><span class="sxs-lookup"><span data-stu-id="deccc-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="deccc-161">Файл `tags.tsv` содержит два столбца: первый определен как `ImagePath`, а во втором указана метка `Label`, соответствующая изображению.</span><span class="sxs-lookup"><span data-stu-id="deccc-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="deccc-162">В примере файла ниже отсутствует строка заголовка. Сам файл выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="deccc-162">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="deccc-163">Изображения для обучения и тестирования расположены в папках ресурсов, которые вы скачали в виде ZIP-файла.</span><span class="sxs-lookup"><span data-stu-id="deccc-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="deccc-164">Эти изображения принадлежат Викискладу.</span><span class="sxs-lookup"><span data-stu-id="deccc-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="deccc-165">*[Викисклад](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), бесплатный репозиторий мультимедиа.*</span><span class="sxs-lookup"><span data-stu-id="deccc-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="deccc-166">Получено 17 октября 2018 г. в 10:48 со страниц: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
> <https://commons.wikimedia.org/wiki/Teddy_bear></span><span class="sxs-lookup"><span data-stu-id="deccc-166">Retrieved 10:48, October 17, 2018 from: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
<https://commons.wikimedia.org/wiki/Teddy_bear></span></span>

## <a name="setup"></a><span data-ttu-id="deccc-167">Установка</span><span class="sxs-lookup"><span data-stu-id="deccc-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="deccc-168">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="deccc-168">Create a project</span></span>

1. <span data-ttu-id="deccc-169">Создайте **консольное приложение .NET Core** с именем TransferLearningTF.</span><span class="sxs-lookup"><span data-stu-id="deccc-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="deccc-170">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="deccc-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    * <span data-ttu-id="deccc-171">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="deccc-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="deccc-172">Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор" и выполните поиск **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="deccc-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="deccc-173">Нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="deccc-173">Select the **Install** button.</span></span>
    * <span data-ttu-id="deccc-174">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**.</span><span class="sxs-lookup"><span data-stu-id="deccc-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="deccc-175">Нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с условиями лицензионного соглашения для указанных пакетов.</span><span class="sxs-lookup"><span data-stu-id="deccc-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="deccc-176">Повторите эти шаги для пакетов **Microsoft.ML.ImageAnalytics**, **SciSharp.TensorFlow.Redist** и **Microsoft.ML.TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="deccc-176">Repeat these steps for **Microsoft.ML.ImageAnalytics**, **SciSharp.TensorFlow.Redist** and **Microsoft.ML.TensorFlow**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="deccc-177">Скачивание ресурсов</span><span class="sxs-lookup"><span data-stu-id="deccc-177">Download assets</span></span>

1. <span data-ttu-id="deccc-178">Скачайте [ZIP-файл каталога с ресурсами проекта](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip) и распакуйте его.</span><span class="sxs-lookup"><span data-stu-id="deccc-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="deccc-179">Скопируйте каталог `assets` в каталог проекта *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="deccc-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="deccc-180">Этот каталог и его подкаталоги содержат данные и файлы поддержки (за исключением модели Inception, которую вы скачаете и добавите на следующем шаге), необходимые для работы с этим руководством.</span><span class="sxs-lookup"><span data-stu-id="deccc-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="deccc-181">Скачайте [модель Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) и распакуйте ее.</span><span class="sxs-lookup"><span data-stu-id="deccc-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="deccc-182">Скопируйте содержание каталога `inception5h`, который вы распаковали, в каталог `assets/inception` проекта *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="deccc-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="deccc-183">Этот каталог содержит модель и дополнительные файлы поддержки, необходимые для работы с этим руководством, как показано на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="deccc-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Содержание каталога Inception](./media/image-classification/inception-files.png)

1. <span data-ttu-id="deccc-185">В обозревателе решений щелкните правой кнопкой мыши каждый файл в каталоге и подкаталогах ресурсов и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="deccc-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="deccc-186">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="deccc-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="deccc-187">Создание классов и определение путей</span><span class="sxs-lookup"><span data-stu-id="deccc-187">Create classes and define paths</span></span>

1. <span data-ttu-id="deccc-188">Добавьте следующие новые операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="deccc-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/image-classification/csharp/Program.cs#AddUsings)]

1. <span data-ttu-id="deccc-189">Добавьте следующий код в строке справа выше метода `Main` для указания пути к ресурсу:</span><span class="sxs-lookup"><span data-stu-id="deccc-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](./snippets/image-classification/csharp/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="deccc-190">Создайте классы для входных данных и прогнозов.</span><span class="sxs-lookup"><span data-stu-id="deccc-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](./snippets/image-classification/csharp/Program.cs#DeclareImageData)]

    <span data-ttu-id="deccc-191">`ImageData` является классом входных данных изображения и имеет следующие поля <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="deccc-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="deccc-192">`ImagePath` содержит имя файла изображения.</span><span class="sxs-lookup"><span data-stu-id="deccc-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="deccc-193">`Label` содержит значение для метки изображения.</span><span class="sxs-lookup"><span data-stu-id="deccc-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="deccc-194">Добавьте новый класс в свой проект для `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="deccc-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](./snippets/image-classification/csharp/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="deccc-195">`ImagePrediction` является классом прогноза изображения и имеет следующие поля:</span><span class="sxs-lookup"><span data-stu-id="deccc-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="deccc-196">`Score` содержит процентное значение достоверности для конкретной классификации изображения.</span><span class="sxs-lookup"><span data-stu-id="deccc-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="deccc-197">`PredictedLabelValue` содержит значение для прогнозируемой метки классификации изображения.</span><span class="sxs-lookup"><span data-stu-id="deccc-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="deccc-198">Класс `ImagePrediction` используется для прогнозирования после обучения модели.</span><span class="sxs-lookup"><span data-stu-id="deccc-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="deccc-199">Он включает `string` (`ImagePath`) с путем к изображению.</span><span class="sxs-lookup"><span data-stu-id="deccc-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="deccc-200">`Label` используется для применения и обучения модели.</span><span class="sxs-lookup"><span data-stu-id="deccc-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="deccc-201">`PredictedLabelValue` используется для прогнозирования и оценки.</span><span class="sxs-lookup"><span data-stu-id="deccc-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="deccc-202">Для оценки применяются входные обучающие данные, прогнозируемые значения и модель.</span><span class="sxs-lookup"><span data-stu-id="deccc-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="deccc-203">Инициализация переменных в методе Main</span><span class="sxs-lookup"><span data-stu-id="deccc-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="deccc-204">Инициализируйте переменную `mlContext` с использованием нового экземпляра `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="deccc-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="deccc-205">Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="deccc-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](./snippets/image-classification/csharp/Program.cs#CreateMLContext)]

    <span data-ttu-id="deccc-206">[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="deccc-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="deccc-207">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="deccc-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="deccc-208">Создание структуры для параметров модели Inception</span><span class="sxs-lookup"><span data-stu-id="deccc-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="deccc-209">Модель Inception имеет несколько параметров, которые необходимо передать.</span><span class="sxs-lookup"><span data-stu-id="deccc-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="deccc-210">Создайте структуру, чтобы сопоставить значения параметров с понятными именами, с помощью следующего кода сразу после метода `Main()`:</span><span class="sxs-lookup"><span data-stu-id="deccc-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](./snippets/image-classification/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="deccc-211">Создание служебного метода для отображения данных</span><span class="sxs-lookup"><span data-stu-id="deccc-211">Create a display utility method</span></span>

<span data-ttu-id="deccc-212">Поскольку вы будете отображать данные изображения и связанные прогнозы несколько раз, создайте метод программы отображения для обработки отображения изображений и результатов прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="deccc-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="deccc-213">Создайте метод `DisplayResults()` сразу после структуры `InceptionSettings` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="deccc-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="deccc-214">Заполните текст метода `DisplayResults`:</span><span class="sxs-lookup"><span data-stu-id="deccc-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](./snippets/image-classification/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="deccc-215">Создание служебного метода для TSV-файла</span><span class="sxs-lookup"><span data-stu-id="deccc-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="deccc-216">Создайте метод `ReadFromTsv()` сразу после метода `DisplayResults()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="deccc-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="deccc-217">Заполните текст метода `ReadFromTsv`:</span><span class="sxs-lookup"><span data-stu-id="deccc-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](./snippets/image-classification/csharp/Program.cs#ReadFromTsv)]

    <span data-ttu-id="deccc-218">Указанный ниже код анализирует файл `tags.tsv`, после чего добавляет путь к файлу к имени файла изображения для свойства `ImagePath` и загружает его и `Label` в объект `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="deccc-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="deccc-219">Создание метода для формирования прогноза</span><span class="sxs-lookup"><span data-stu-id="deccc-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="deccc-220">Создайте метод `ClassifySingleImage()` непосредственно перед методом `DisplayResults()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="deccc-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="deccc-221">Создайте объект `ImageData`, который хранит абсолютный путь и имя файла изображения для одного значения `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="deccc-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="deccc-222">Добавьте такой код в следующие строки в методе `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="deccc-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](./snippets/image-classification/csharp/Program.cs#LoadImageData)]

1. <span data-ttu-id="deccc-223">Создайте один прогноз, добавив следующий код в виде следующей строки в методе `ClassifySingleImage`:</span><span class="sxs-lookup"><span data-stu-id="deccc-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](./snippets/image-classification/csharp/Program.cs#PredictSingle)]

    <span data-ttu-id="deccc-224">Чтобы получить прогноз, используйте метод [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A).</span><span class="sxs-lookup"><span data-stu-id="deccc-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="deccc-225">Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных.</span><span class="sxs-lookup"><span data-stu-id="deccc-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="deccc-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="deccc-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="deccc-227">Допустимо использовать в средах прототипов или средах с одним потоком.</span><span class="sxs-lookup"><span data-stu-id="deccc-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="deccc-228">Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="deccc-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="deccc-229">См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="deccc-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="deccc-230">Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="deccc-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="deccc-231">Отобразите результат прогнозирования с помощью следующей строки кода в методе `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="deccc-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](./snippets/image-classification/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="deccc-232">Создание конвейера модели ML.NET</span><span class="sxs-lookup"><span data-stu-id="deccc-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="deccc-233">Конвейер модели ML.NET — это цепочка средств оценки.</span><span class="sxs-lookup"><span data-stu-id="deccc-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="deccc-234">Обратите внимание, что во время создания конвейера выполнение не происходит.</span><span class="sxs-lookup"><span data-stu-id="deccc-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="deccc-235">Объекты оценки создаются, но не выполняются.</span><span class="sxs-lookup"><span data-stu-id="deccc-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="deccc-236">Добавление метода для создания модели</span><span class="sxs-lookup"><span data-stu-id="deccc-236">Add a method to generate the model</span></span>

    <span data-ttu-id="deccc-237">Этот метод является основным в учебнике.</span><span class="sxs-lookup"><span data-stu-id="deccc-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="deccc-238">Он создает конвейер для модели и обучает конвейер для создания модели ML.NET.</span><span class="sxs-lookup"><span data-stu-id="deccc-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="deccc-239">Он также оценивает модель по некоторым ранее неиспользуемым тестовым данным.</span><span class="sxs-lookup"><span data-stu-id="deccc-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="deccc-240">Создайте метод `GenerateModel()` сразу после структуры `InceptionSettings` и непосредственно перед методом `DisplayResults()` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="deccc-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="deccc-241">Добавьте средства оценки для загрузки, изменения размера и извлечения пикселей из данных изображения:</span><span class="sxs-lookup"><span data-stu-id="deccc-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](./snippets/image-classification/csharp/Program.cs#ImageTransforms)]

    <span data-ttu-id="deccc-242">Данные изображения должны обрабатываться в формате, который требуется модели TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="deccc-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="deccc-243">В этом случае изображения загружаются в память, преобразуются в соответствующий размер, а пиксели извлекаются в числовой вектор.</span><span class="sxs-lookup"><span data-stu-id="deccc-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="deccc-244">Добавьте средство оценки, чтобы загрузить модель TensorFlow и оценить ее:</span><span class="sxs-lookup"><span data-stu-id="deccc-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](./snippets/image-classification/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="deccc-245">Этот этап конвейера загружает модель TensorFlow в память, а затем обрабатывает вектор значений пикселей через сеть модели TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="deccc-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="deccc-246">Применение входных данных к модели глубокого обучения и формирование выходных данных с помощью модели называется **оценкой**.</span><span class="sxs-lookup"><span data-stu-id="deccc-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="deccc-247">При полном использовании модели оценка делает вывод или прогноз.</span><span class="sxs-lookup"><span data-stu-id="deccc-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="deccc-248">В этом случае используется вся модель TensorFlow, за исключением последнего слоя, который делает вывод.</span><span class="sxs-lookup"><span data-stu-id="deccc-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="deccc-249">Выходные данные предпоследнего слоя помечаются как `softmax_2_preactivation`.</span><span class="sxs-lookup"><span data-stu-id="deccc-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="deccc-250">Выходные данные этого слоя фактически являются вектором признаков, характеризующих исходные входные изображения.</span><span class="sxs-lookup"><span data-stu-id="deccc-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="deccc-251">Этот вектор признаков, созданный моделью TensorFlow, будет использоваться в качестве входных данных для алгоритма обучения ML.NET.</span><span class="sxs-lookup"><span data-stu-id="deccc-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="deccc-252">Добавьте средство оценки, чтобы сопоставлять строковые метки в данных для обучения с целочисленными значениями ключа:</span><span class="sxs-lookup"><span data-stu-id="deccc-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](./snippets/image-classification/csharp/Program.cs#MapValueToKey)]

    <span data-ttu-id="deccc-253">Для обучающего алгоритма ML.NET, добавляемого далее, метки должны быть в формате `key`, а не в виде произвольных строк.</span><span class="sxs-lookup"><span data-stu-id="deccc-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="deccc-254">Ключ — это число, которое содержит сопоставление по принципу "один к одному" со строковым значением.</span><span class="sxs-lookup"><span data-stu-id="deccc-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="deccc-255">Добавьте алгоритм обучения ML.NET:</span><span class="sxs-lookup"><span data-stu-id="deccc-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](./snippets/image-classification/csharp/Program.cs#AddTrainer)]

1. <span data-ttu-id="deccc-256">Добавьте средство оценки для преобразования значения прогнозируемого ключа обратно в строку:</span><span class="sxs-lookup"><span data-stu-id="deccc-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](./snippets/image-classification/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="deccc-257">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="deccc-257">Train the model</span></span>

1. <span data-ttu-id="deccc-258">Загрузите данные для обучения с использованием оболочки [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)).</span><span class="sxs-lookup"><span data-stu-id="deccc-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="deccc-259">Добавьте в следующую строку метода `GenerateModel()` приведенный ниже код:</span><span class="sxs-lookup"><span data-stu-id="deccc-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](./snippets/image-classification/csharp/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="deccc-260">Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="deccc-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="deccc-261">`IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые).</span><span class="sxs-lookup"><span data-stu-id="deccc-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="deccc-262">Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="deccc-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="deccc-263">Обучите модель сна основе данных, загруженных ранее:</span><span class="sxs-lookup"><span data-stu-id="deccc-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](./snippets/image-classification/csharp/Program.cs#TrainModel)]

    <span data-ttu-id="deccc-264">Метод `Fit()` обучает модель путем применения набора данных для обучения к конвейеру.</span><span class="sxs-lookup"><span data-stu-id="deccc-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="deccc-265">Оценка точности модели</span><span class="sxs-lookup"><span data-stu-id="deccc-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="deccc-266">Загрузите и преобразуйте проверочные данные, добавив приведенный ниже код в следующую строку метода `GenerateModel`:</span><span class="sxs-lookup"><span data-stu-id="deccc-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](./snippets/image-classification/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="deccc-267">Есть несколько примеров изображений, которые можно использовать для оценки модели.</span><span class="sxs-lookup"><span data-stu-id="deccc-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="deccc-268">Как и данные для обучения, их нужно загрузить в `IDataView`, чтобы модель могла их преобразовать.</span><span class="sxs-lookup"><span data-stu-id="deccc-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="deccc-269">Добавьте следующий код в метод `GenerateModel()` для оценки модели:</span><span class="sxs-lookup"><span data-stu-id="deccc-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](./snippets/image-classification/csharp/Program.cs#Evaluate)]

    <span data-ttu-id="deccc-270">Получив прогноз, с помощью метода [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) вы сможете:</span><span class="sxs-lookup"><span data-stu-id="deccc-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="deccc-271">оценить модель (сравнивает спрогнозированные значения с тестовым набором данных `labels`);</span><span class="sxs-lookup"><span data-stu-id="deccc-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="deccc-272">получить метрики производительности модели.</span><span class="sxs-lookup"><span data-stu-id="deccc-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="deccc-273">Отобразите метрики точности модели.</span><span class="sxs-lookup"><span data-stu-id="deccc-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="deccc-274">Используйте следующий код для отображения метрик, передачи результатов и выполнения действий по ним:</span><span class="sxs-lookup"><span data-stu-id="deccc-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](./snippets/image-classification/csharp/Program.cs#DisplayMetrics)]

    <span data-ttu-id="deccc-275">Для классификации изображений выполняется оценка следующих метрик:</span><span class="sxs-lookup"><span data-stu-id="deccc-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="deccc-276">`Log-loss` — см. раздел [Логарифмические потери](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="deccc-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="deccc-277">Значение логарифмических потерь должно быть максимально близко к нулю.</span><span class="sxs-lookup"><span data-stu-id="deccc-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="deccc-278">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="deccc-278">`Per class Log-loss`.</span></span> <span data-ttu-id="deccc-279">Значение логарифмических потерь для каждого класса должно быть максимально близко к нулю.</span><span class="sxs-lookup"><span data-stu-id="deccc-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="deccc-280">Добавьте следующий код, чтобы возвращать обученную модель:</span><span class="sxs-lookup"><span data-stu-id="deccc-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](./snippets/image-classification/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="deccc-281">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="deccc-281">Run the application!</span></span>

1. <span data-ttu-id="deccc-282">Добавьте вызов `GenerateModel` в метод `Main` после создания класса MLContext:</span><span class="sxs-lookup"><span data-stu-id="deccc-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](./snippets/image-classification/csharp/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="deccc-283">Добавьте такой вызов в метод `ClassifySingleImage()` в виде следующей строки кода в методе `Main`:</span><span class="sxs-lookup"><span data-stu-id="deccc-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](./snippets/image-classification/csharp/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="deccc-284">Запустите консольное приложение (CTRL+F5).</span><span class="sxs-lookup"><span data-stu-id="deccc-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="deccc-285">Результаты выполнения должны выглядеть примерно так, как указано ниже.</span><span class="sxs-lookup"><span data-stu-id="deccc-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="deccc-286">Кроме того, могут выводиться предупреждения или сообщения об обработке, но для удобства здесь мы убрали их.</span><span class="sxs-lookup"><span data-stu-id="deccc-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

<span data-ttu-id="deccc-287">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="deccc-287">Congratulations!</span></span> <span data-ttu-id="deccc-288">Вы успешно создали модель машинного обучения для классификации изображений, применив передачу обучения в модель `TensorFlow` в ML.NET.</span><span class="sxs-lookup"><span data-stu-id="deccc-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="deccc-289">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="deccc-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="deccc-290">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="deccc-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="deccc-291">Определение проблемы</span><span class="sxs-lookup"><span data-stu-id="deccc-291">Understand the problem</span></span>
> * <span data-ttu-id="deccc-292">внедрить предварительно обученную модель TensorFlow в конвейер ML.NET;</span><span class="sxs-lookup"><span data-stu-id="deccc-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="deccc-293">обучить и оценить модель ML.NET;</span><span class="sxs-lookup"><span data-stu-id="deccc-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="deccc-294">классифицировать тестовое изображение.</span><span class="sxs-lookup"><span data-stu-id="deccc-294">Classify a test image</span></span>

<span data-ttu-id="deccc-295">Ознакомьтесь с примерами Машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример классификации изображений.</span><span class="sxs-lookup"><span data-stu-id="deccc-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="deccc-296">Репозиторий GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="deccc-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
