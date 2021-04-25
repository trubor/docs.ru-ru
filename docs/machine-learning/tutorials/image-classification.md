---
title: Учебник. Модель классификации ML.NET для категоризации изображений
description: Узнайте, как обучить модель классификации категоризировать изображения с помощью предварительно обученной модели TensorFlow для обработки изображений.
ms.date: 04/13/2021
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: f510b6a21807a2ab1e2d7c878c285038bea33d42
ms.sourcegitcommit: 5ddbd1f65d0369b4cc8c8ff91c72f1b524c90221
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2021
ms.locfileid: "107514480"
---
# <a name="tutorial-train-an-mlnet-classification-model-to-categorize-images"></a><span data-ttu-id="3359f-103">Учебник. Обучение модели классификации ML.NET для категоризации изображений</span><span class="sxs-lookup"><span data-stu-id="3359f-103">Tutorial: Train an ML.NET classification model to categorize images</span></span>

<span data-ttu-id="3359f-104">Узнайте, как обучить модель классификации категоризировать изображения с помощью предварительно обученной модели TensorFlow для обработки изображений.</span><span class="sxs-lookup"><span data-stu-id="3359f-104">Learn how to train a classification model to categorize images using a pre-trained TensorFlow model for image processing.</span></span>

<span data-ttu-id="3359f-105">Модель TensorFlow была обучена для классификации изображений по тысячам категорий.</span><span class="sxs-lookup"><span data-stu-id="3359f-105">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="3359f-106">Поскольку модель TensorFlow способна распознавать на изображениях знакомые элементы, модель ML.NET может частично использовать ее в собственном конвейере для преобразования необработанных изображений в признаки или входные данные для обучения модели классификации.</span><span class="sxs-lookup"><span data-stu-id="3359f-106">Because the TensorFlow model knows how to recognize patterns in images, the ML.NET model can make use of part of it in its pipeline to convert raw images into features or inputs to train a classification model.</span></span>

<span data-ttu-id="3359f-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="3359f-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="3359f-108">Определение проблемы</span><span class="sxs-lookup"><span data-stu-id="3359f-108">Understand the problem</span></span>
> * <span data-ttu-id="3359f-109">внедрить предварительно обученную модель TensorFlow в конвейер ML.NET;</span><span class="sxs-lookup"><span data-stu-id="3359f-109">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="3359f-110">обучить и оценить модель ML.NET;</span><span class="sxs-lookup"><span data-stu-id="3359f-110">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="3359f-111">классифицировать тестовое изображение.</span><span class="sxs-lookup"><span data-stu-id="3359f-111">Classify a test image</span></span>

<span data-ttu-id="3359f-112">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="3359f-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="3359f-113">Обратите внимание на то, что по умолчанию конфигурации проекта .NET в этом руководстве предназначена для .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="3359f-113">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3359f-114">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="3359f-114">Prerequisites</span></span>

* <span data-ttu-id="3359f-115">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".</span><span class="sxs-lookup"><span data-stu-id="3359f-115">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="3359f-116">ZIP-файл каталога ресурсов руководства.</span><span class="sxs-lookup"><span data-stu-id="3359f-116">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="3359f-117">Модель машинного обучения Inception версии 1</span><span class="sxs-lookup"><span data-stu-id="3359f-117">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="3359f-118">Выбор типа задачи машинного обучения</span><span class="sxs-lookup"><span data-stu-id="3359f-118">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="3359f-119">Глубокое обучение</span><span class="sxs-lookup"><span data-stu-id="3359f-119">Deep learning</span></span>

<span data-ttu-id="3359f-120">[Глубокое обучение](https://en.wikipedia.org/wiki/Deep_learning) — это разновидность машинного обучения, совершающая революцию в области компьютерного зрения, распознавания речи и других подобных сферах.</span><span class="sxs-lookup"><span data-stu-id="3359f-120">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like computer vision and speech recognition.</span></span>

<span data-ttu-id="3359f-121">Модели глубокого обучения обучаются на крупных наборах [помеченных данных](https://en.wikipedia.org/wiki/Labeled_data) с использованием [нейронных сетей](https://en.wikipedia.org/wiki/Artificial_neural_network), которые содержат множество слоев обучения.</span><span class="sxs-lookup"><span data-stu-id="3359f-121">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="3359f-122">Глубокое обучение:</span><span class="sxs-lookup"><span data-stu-id="3359f-122">Deep learning:</span></span>

* <span data-ttu-id="3359f-123">лучше решает некоторые задачи, например в области компьютерного зрения;</span><span class="sxs-lookup"><span data-stu-id="3359f-123">Performs better on some tasks like computer vision.</span></span>
* <span data-ttu-id="3359f-124">требует огромных объемов данных для обучения.</span><span class="sxs-lookup"><span data-stu-id="3359f-124">Requires huge amounts of training data.</span></span>

<span data-ttu-id="3359f-125">Классификация изображений — это конкретная задача их автоматической классификации по категориям, например:</span><span class="sxs-lookup"><span data-stu-id="3359f-125">Image classification is a specific classification task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="3359f-126">для определения того, содержит ли изображение человеческое лицо;</span><span class="sxs-lookup"><span data-stu-id="3359f-126">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="3359f-127">для различения изображений котов и собак.</span><span class="sxs-lookup"><span data-stu-id="3359f-127">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="3359f-128">Она также помогает определить тип объекта на изображении — еда, игрушка или прибор:</span><span class="sxs-lookup"><span data-stu-id="3359f-128">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="3359f-129">![Изображение с пиццей](./media/image-classification/220px-Pepperoni_pizza.jpg)
![Изображение с плюшевым мишкой](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![Изображение с тостером](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="3359f-129">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="3359f-130">Изображения выше принадлежат Викискладу и имеют следующие атрибуты:</span><span class="sxs-lookup"><span data-stu-id="3359f-130">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="3359f-131">220px-Pepperoni_pizza.jpg, открытый источник, <https://commons.wikimedia.org/w/index.php?curid=79505>;</span><span class="sxs-lookup"><span data-stu-id="3359f-131">"220px-Pepperoni_pizza.jpg" Public Domain, <https://commons.wikimedia.org/w/index.php?curid=79505>,</span></span>
> * <span data-ttu-id="3359f-132">119px-Nalle_-_a_small_brown_teddy_bear.jpg, автор — [Jonik](https://commons.wikimedia.org/wiki/User:Jonik), автофотография, лицензия CC BY-SA 2.0, <https://commons.wikimedia.org/w/index.php?curid=48166>;</span><span class="sxs-lookup"><span data-stu-id="3359f-132">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, <https://commons.wikimedia.org/w/index.php?curid=48166>.</span></span>
> * <span data-ttu-id="3359f-133">193px-Broodrooster.jpg, автор — [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972), собственное фото, лицензия CC BY-SA 3.0, <https://commons.wikimedia.org/w/index.php?curid=27403>.</span><span class="sxs-lookup"><span data-stu-id="3359f-133">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, <https://commons.wikimedia.org/w/index.php?curid=27403></span></span>

<span data-ttu-id="3359f-134">Обучение модели [классификации изображений](https://en.wikipedia.org/wiki/Outline_of_object_recognition) с нуля требует задания миллионов параметров, а также использования огромных объемов помеченных обучающих данных и вычислительных ресурсов (сотни часов работы GPU).</span><span class="sxs-lookup"><span data-stu-id="3359f-134">Training an [image classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="3359f-135">Использование предварительно обученной модели не настолько эффективно, как обучение специализированной модели с нуля, однако за счет использования лишь тысяч (а не миллионов) помеченных изображений этот подход позволяет получить требуемую модель существенно быстрее (в пределах часа) на компьютере без GPU.</span><span class="sxs-lookup"><span data-stu-id="3359f-135">While not as effective as training a custom model from scratch, using a pre-trained model allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="3359f-136">В этом учебнике этот процесс еще более уменьшен: используется только десяток изображений для обучения.</span><span class="sxs-lookup"><span data-stu-id="3359f-136">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="3359f-137">Модель `Inception model` обучена классификации изображений по тысячам категорий, но в настоящем учебнике требуется меньший, строго ограниченный набор. Вы можете применить модель `Inception model` в своем классификаторе изображений для распознавания и категоризации определенного нового набора.</span><span class="sxs-lookup"><span data-stu-id="3359f-137">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.You can use the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="3359f-138">еда;</span><span class="sxs-lookup"><span data-stu-id="3359f-138">Food</span></span>
* <span data-ttu-id="3359f-139">игрушка;</span><span class="sxs-lookup"><span data-stu-id="3359f-139">Toy</span></span>
* <span data-ttu-id="3359f-140">прибор.</span><span class="sxs-lookup"><span data-stu-id="3359f-140">Appliance</span></span>

<span data-ttu-id="3359f-141">В этом учебнике используется TensorFlow [Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), популярная модель глубокого обучения для распознавания изображений, обученная на наборе данных `ImageNet`.</span><span class="sxs-lookup"><span data-stu-id="3359f-141">This tutorial uses the TensorFlow [Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="3359f-142">Модель TensorFlow классифицирует все изображения по тысячам классов, таких как "зонт", "жакет" и "посудомоечная машина".</span><span class="sxs-lookup"><span data-stu-id="3359f-142">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="3359f-143">Так как `Inception model` предварительно обучена на тысячах различных изображений, она содержит [признаки изображений](https://en.wikipedia.org/wiki/Feature_(computer_vision)), необходимые для их идентификации.</span><span class="sxs-lookup"><span data-stu-id="3359f-143">Because the `Inception model` has already been pre-trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="3359f-144">Мы можем использовать эти внутренние признаки изображений в модели для обучения новой модели с гораздо меньшим числом классов.</span><span class="sxs-lookup"><span data-stu-id="3359f-144">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="3359f-145">Как показано на схеме ниже, вам нужно добавить ссылки на пакеты NuGet ML.NET в приложения .NET Core или .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3359f-145">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="3359f-146">На внутреннем уровне ML.NET включает и ссылается на встроенную библиотеку `TensorFlow`, которая позволяет создавать код, загружающий существующую обученную модель `TensorFlow`.</span><span class="sxs-lookup"><span data-stu-id="3359f-146">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Схема преобразования ML.NET с использованием TensorFlow](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="3359f-148">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="3359f-148">Multiclass classification</span></span>

<span data-ttu-id="3359f-149">После использования модели Inception TensorFlow для извлечения признаков, подходящих в качестве входных данных для классического алгоритма машинного обучения, мы добавим [многоклассовый классификатор](../resources/tasks.md#multiclass-classification) ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3359f-149">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="3359f-150">В этом случае используется алгоритм [мультиномиальной логистической регрессии](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="3359f-150">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="3359f-151">Алгоритм, реализованный этим инструктором, хорошо работает в задачах с большим количеством признаков, что характерно для модели глубокого обучения, работающей с данными изображений.</span><span class="sxs-lookup"><span data-stu-id="3359f-151">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

<span data-ttu-id="3359f-152">Дополнительные сведения: [Сравнение глубокого и машинного обучения](/azure/machine-learning/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="3359f-152">See [Deep learning vs. machine learning](/azure/machine-learning/concept-deep-learning-vs-machine-learning) for more information.</span></span>

### <a name="data"></a><span data-ttu-id="3359f-153">Данные</span><span class="sxs-lookup"><span data-stu-id="3359f-153">Data</span></span>

<span data-ttu-id="3359f-154">Доступны два источника данных: файл `.tsv` и файлы образов.</span><span class="sxs-lookup"><span data-stu-id="3359f-154">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="3359f-155">Файл `tags.tsv` содержит два столбца: первый определен как `ImagePath`, а во втором указана метка `Label`, соответствующая изображению.</span><span class="sxs-lookup"><span data-stu-id="3359f-155">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="3359f-156">В примере файла ниже отсутствует строка заголовка. Сам файл выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3359f-156">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="3359f-157">Изображения для обучения и тестирования расположены в папках ресурсов, которые вы скачали в виде ZIP-файла.</span><span class="sxs-lookup"><span data-stu-id="3359f-157">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="3359f-158">Эти изображения принадлежат Викискладу.</span><span class="sxs-lookup"><span data-stu-id="3359f-158">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="3359f-159">*[Викисклад](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), бесплатный репозиторий мультимедиа.*</span><span class="sxs-lookup"><span data-stu-id="3359f-159">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="3359f-160">Получено 17 октября 2018 г. в 10:48 со страниц: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
> <https://commons.wikimedia.org/wiki/Teddy_bear></span><span class="sxs-lookup"><span data-stu-id="3359f-160">Retrieved 10:48, October 17, 2018 from: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
<https://commons.wikimedia.org/wiki/Teddy_bear></span></span>

## <a name="setup"></a><span data-ttu-id="3359f-161">Установка</span><span class="sxs-lookup"><span data-stu-id="3359f-161">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="3359f-162">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="3359f-162">Create a project</span></span>

1. <span data-ttu-id="3359f-163">Создайте **консольное приложение .NET Core** с именем TransferLearningTF.</span><span class="sxs-lookup"><span data-stu-id="3359f-163">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="3359f-164">Установите **пакет NuGet для Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="3359f-164">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    * <span data-ttu-id="3359f-165">В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3359f-165">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="3359f-166">Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор" и выполните поиск **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="3359f-166">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="3359f-167">Нажмите кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="3359f-167">Select the **Install** button.</span></span>
    * <span data-ttu-id="3359f-168">Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**.</span><span class="sxs-lookup"><span data-stu-id="3359f-168">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="3359f-169">Нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с условиями лицензионного соглашения для указанных пакетов.</span><span class="sxs-lookup"><span data-stu-id="3359f-169">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="3359f-170">Повторите эти шаги для пакетов **Microsoft.ML.ImageAnalytics**, **SciSharp.TensorFlow.Redist** и **Microsoft.ML.TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="3359f-170">Repeat these steps for **Microsoft.ML.ImageAnalytics**, **SciSharp.TensorFlow.Redist** and **Microsoft.ML.TensorFlow**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="3359f-171">Скачивание ресурсов</span><span class="sxs-lookup"><span data-stu-id="3359f-171">Download assets</span></span>

1. <span data-ttu-id="3359f-172">Скачайте [ZIP-файл каталога с ресурсами проекта](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip) и распакуйте его.</span><span class="sxs-lookup"><span data-stu-id="3359f-172">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="3359f-173">Скопируйте каталог `assets` в каталог проекта *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="3359f-173">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="3359f-174">Этот каталог и его подкаталоги содержат данные и файлы поддержки (за исключением модели Inception, которую вы скачаете и добавите на следующем шаге), необходимые для работы с этим руководством.</span><span class="sxs-lookup"><span data-stu-id="3359f-174">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="3359f-175">Скачайте [модель Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) и распакуйте ее.</span><span class="sxs-lookup"><span data-stu-id="3359f-175">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="3359f-176">Скопируйте содержание каталога `inception5h`, который вы распаковали, в каталог `assets/inception` проекта *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="3359f-176">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="3359f-177">Этот каталог содержит модель и дополнительные файлы поддержки, необходимые для работы с этим руководством, как показано на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="3359f-177">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Содержание каталога Inception](./media/image-classification/inception-files.png)

1. <span data-ttu-id="3359f-179">В обозревателе решений щелкните правой кнопкой мыши каждый файл в каталоге и подкаталогах ресурсов и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="3359f-179">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="3359f-180">В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.</span><span class="sxs-lookup"><span data-stu-id="3359f-180">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="3359f-181">Создание классов и определение путей</span><span class="sxs-lookup"><span data-stu-id="3359f-181">Create classes and define paths</span></span>

1. <span data-ttu-id="3359f-182">Добавьте следующие новые операторы `using` в начало файла *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="3359f-182">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/image-classification/csharp/Program.cs#AddUsings)]

1. <span data-ttu-id="3359f-183">Добавьте следующий код в строке справа выше метода `Main` для указания пути к ресурсу:</span><span class="sxs-lookup"><span data-stu-id="3359f-183">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](./snippets/image-classification/csharp/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="3359f-184">Создайте классы для входных данных и прогнозов.</span><span class="sxs-lookup"><span data-stu-id="3359f-184">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](./snippets/image-classification/csharp/Program.cs#DeclareImageData)]

    <span data-ttu-id="3359f-185">`ImageData` является классом входных данных изображения и имеет следующие поля <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="3359f-185">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="3359f-186">`ImagePath` содержит имя файла изображения.</span><span class="sxs-lookup"><span data-stu-id="3359f-186">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="3359f-187">`Label` содержит значение для метки изображения.</span><span class="sxs-lookup"><span data-stu-id="3359f-187">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="3359f-188">Добавьте новый класс в свой проект для `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="3359f-188">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](./snippets/image-classification/csharp/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="3359f-189">`ImagePrediction` является классом прогноза изображения и имеет следующие поля:</span><span class="sxs-lookup"><span data-stu-id="3359f-189">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="3359f-190">`Score` содержит процентное значение достоверности для конкретной классификации изображения.</span><span class="sxs-lookup"><span data-stu-id="3359f-190">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="3359f-191">`PredictedLabelValue` содержит значение для прогнозируемой метки классификации изображения.</span><span class="sxs-lookup"><span data-stu-id="3359f-191">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="3359f-192">Класс `ImagePrediction` используется для прогнозирования после обучения модели.</span><span class="sxs-lookup"><span data-stu-id="3359f-192">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="3359f-193">Он включает `string` (`ImagePath`) с путем к изображению.</span><span class="sxs-lookup"><span data-stu-id="3359f-193">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="3359f-194">`Label` используется для применения и обучения модели.</span><span class="sxs-lookup"><span data-stu-id="3359f-194">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="3359f-195">`PredictedLabelValue` используется для прогнозирования и оценки.</span><span class="sxs-lookup"><span data-stu-id="3359f-195">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="3359f-196">Для оценки применяются входные обучающие данные, прогнозируемые значения и модель.</span><span class="sxs-lookup"><span data-stu-id="3359f-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="3359f-197">Инициализация переменных в методе Main</span><span class="sxs-lookup"><span data-stu-id="3359f-197">Initialize variables in Main</span></span>

1. <span data-ttu-id="3359f-198">Инициализируйте переменную `mlContext` с использованием нового экземпляра `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="3359f-198">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="3359f-199">Замените строку `Console.WriteLine("Hello World!")` в методе `Main` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="3359f-199">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](./snippets/image-classification/csharp/Program.cs#CreateMLContext)]

    <span data-ttu-id="3359f-200">[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели.</span><span class="sxs-lookup"><span data-stu-id="3359f-200">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="3359f-201">По существу он аналогичен классу `DBContext` в Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="3359f-201">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="3359f-202">Создание структуры для параметров модели Inception</span><span class="sxs-lookup"><span data-stu-id="3359f-202">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="3359f-203">Модель Inception имеет несколько параметров, которые необходимо передать.</span><span class="sxs-lookup"><span data-stu-id="3359f-203">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="3359f-204">Создайте структуру, чтобы сопоставить значения параметров с понятными именами, с помощью следующего кода сразу после метода `Main()`:</span><span class="sxs-lookup"><span data-stu-id="3359f-204">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](./snippets/image-classification/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="3359f-205">Создание служебного метода для отображения данных</span><span class="sxs-lookup"><span data-stu-id="3359f-205">Create a display utility method</span></span>

<span data-ttu-id="3359f-206">Поскольку вы будете отображать данные изображения и связанные прогнозы несколько раз, создайте метод программы отображения для обработки отображения изображений и результатов прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="3359f-206">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="3359f-207">Создайте метод `DisplayResults()` сразу после структуры `InceptionSettings` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="3359f-207">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="3359f-208">Заполните текст метода `DisplayResults`:</span><span class="sxs-lookup"><span data-stu-id="3359f-208">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](./snippets/image-classification/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="3359f-209">Создание служебного метода для TSV-файла</span><span class="sxs-lookup"><span data-stu-id="3359f-209">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="3359f-210">Создайте метод `ReadFromTsv()` сразу после метода `DisplayResults()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="3359f-210">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="3359f-211">Заполните текст метода `ReadFromTsv`:</span><span class="sxs-lookup"><span data-stu-id="3359f-211">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](./snippets/image-classification/csharp/Program.cs#ReadFromTsv)]

    <span data-ttu-id="3359f-212">Указанный ниже код анализирует файл `tags.tsv`, после чего добавляет путь к файлу к имени файла изображения для свойства `ImagePath` и загружает его и `Label` в объект `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="3359f-212">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="3359f-213">Создание метода для формирования прогноза</span><span class="sxs-lookup"><span data-stu-id="3359f-213">Create a method to make a prediction</span></span>

1. <span data-ttu-id="3359f-214">Создайте метод `ClassifySingleImage()` непосредственно перед методом `DisplayResults()`, вставив в него следующий код:</span><span class="sxs-lookup"><span data-stu-id="3359f-214">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="3359f-215">Создайте объект `ImageData`, который хранит абсолютный путь и имя файла изображения для одного значения `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="3359f-215">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="3359f-216">Добавьте такой код в следующие строки в методе `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="3359f-216">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](./snippets/image-classification/csharp/Program.cs#LoadImageData)]

1. <span data-ttu-id="3359f-217">Создайте один прогноз, добавив следующий код в виде следующей строки в методе `ClassifySingleImage`:</span><span class="sxs-lookup"><span data-stu-id="3359f-217">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](./snippets/image-classification/csharp/Program.cs#PredictSingle)]

    <span data-ttu-id="3359f-218">Чтобы получить прогноз, используйте метод [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A).</span><span class="sxs-lookup"><span data-stu-id="3359f-218">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="3359f-219">Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных.</span><span class="sxs-lookup"><span data-stu-id="3359f-219">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="3359f-220">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="3359f-220">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="3359f-221">Допустимо использовать в средах прототипов или средах с одним потоком.</span><span class="sxs-lookup"><span data-stu-id="3359f-221">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="3359f-222">Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="3359f-222">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="3359f-223">См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="3359f-223">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="3359f-224">Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="3359f-224">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="3359f-225">Отобразите результат прогнозирования с помощью следующей строки кода в методе `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="3359f-225">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](./snippets/image-classification/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="3359f-226">Создание конвейера модели ML.NET</span><span class="sxs-lookup"><span data-stu-id="3359f-226">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="3359f-227">Конвейер модели ML.NET — это цепочка средств оценки.</span><span class="sxs-lookup"><span data-stu-id="3359f-227">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="3359f-228">Обратите внимание, что во время создания конвейера выполнение не происходит.</span><span class="sxs-lookup"><span data-stu-id="3359f-228">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="3359f-229">Объекты оценки создаются, но не выполняются.</span><span class="sxs-lookup"><span data-stu-id="3359f-229">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="3359f-230">Добавление метода для создания модели</span><span class="sxs-lookup"><span data-stu-id="3359f-230">Add a method to generate the model</span></span>

    <span data-ttu-id="3359f-231">Этот метод является основным в учебнике.</span><span class="sxs-lookup"><span data-stu-id="3359f-231">This method is the heart of the tutorial.</span></span> <span data-ttu-id="3359f-232">Он создает конвейер для модели и обучает конвейер для создания модели ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3359f-232">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="3359f-233">Он также оценивает модель по некоторым ранее неиспользуемым тестовым данным.</span><span class="sxs-lookup"><span data-stu-id="3359f-233">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="3359f-234">Создайте метод `GenerateModel()` сразу после структуры `InceptionSettings` и непосредственно перед методом `DisplayResults()` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="3359f-234">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="3359f-235">Добавьте средства оценки для загрузки, изменения размера и извлечения пикселей из данных изображения:</span><span class="sxs-lookup"><span data-stu-id="3359f-235">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](./snippets/image-classification/csharp/Program.cs#ImageTransforms)]

    <span data-ttu-id="3359f-236">Данные изображения должны обрабатываться в формате, который требуется модели TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="3359f-236">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="3359f-237">В этом случае изображения загружаются в память, преобразуются в соответствующий размер, а пиксели извлекаются в числовой вектор.</span><span class="sxs-lookup"><span data-stu-id="3359f-237">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="3359f-238">Добавьте средство оценки, чтобы загрузить модель TensorFlow и оценить ее:</span><span class="sxs-lookup"><span data-stu-id="3359f-238">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](./snippets/image-classification/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="3359f-239">Этот этап конвейера загружает модель TensorFlow в память, а затем обрабатывает вектор значений пикселей через сеть модели TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="3359f-239">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="3359f-240">Применение входных данных к модели глубокого обучения и формирование выходных данных с помощью модели называется **оценкой**.</span><span class="sxs-lookup"><span data-stu-id="3359f-240">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="3359f-241">При полном использовании модели оценка делает вывод или прогноз.</span><span class="sxs-lookup"><span data-stu-id="3359f-241">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="3359f-242">В этом случае используется вся модель TensorFlow, за исключением последнего слоя, который делает вывод.</span><span class="sxs-lookup"><span data-stu-id="3359f-242">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="3359f-243">Выходные данные предпоследнего слоя помечаются как `softmax_2_preactivation`.</span><span class="sxs-lookup"><span data-stu-id="3359f-243">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="3359f-244">Выходные данные этого слоя фактически являются вектором признаков, характеризующих исходные входные изображения.</span><span class="sxs-lookup"><span data-stu-id="3359f-244">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="3359f-245">Этот вектор признаков, созданный моделью TensorFlow, будет использоваться в качестве входных данных для алгоритма обучения ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3359f-245">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="3359f-246">Добавьте средство оценки, чтобы сопоставлять строковые метки в данных для обучения с целочисленными значениями ключа:</span><span class="sxs-lookup"><span data-stu-id="3359f-246">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](./snippets/image-classification/csharp/Program.cs#MapValueToKey)]

    <span data-ttu-id="3359f-247">Для обучающего алгоритма ML.NET, добавляемого далее, метки должны быть в формате `key`, а не в виде произвольных строк.</span><span class="sxs-lookup"><span data-stu-id="3359f-247">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="3359f-248">Ключ — это число, которое содержит сопоставление по принципу "один к одному" со строковым значением.</span><span class="sxs-lookup"><span data-stu-id="3359f-248">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="3359f-249">Добавьте алгоритм обучения ML.NET:</span><span class="sxs-lookup"><span data-stu-id="3359f-249">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](./snippets/image-classification/csharp/Program.cs#AddTrainer)]

1. <span data-ttu-id="3359f-250">Добавьте средство оценки для преобразования значения прогнозируемого ключа обратно в строку:</span><span class="sxs-lookup"><span data-stu-id="3359f-250">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](./snippets/image-classification/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="3359f-251">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="3359f-251">Train the model</span></span>

1. <span data-ttu-id="3359f-252">Загрузите данные для обучения с использованием оболочки [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)).</span><span class="sxs-lookup"><span data-stu-id="3359f-252">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="3359f-253">Добавьте в следующую строку метода `GenerateModel()` приведенный ниже код:</span><span class="sxs-lookup"><span data-stu-id="3359f-253">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](./snippets/image-classification/csharp/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="3359f-254">Данные в ML.NET представлены [классом IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="3359f-254">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="3359f-255">`IDataView` позволяет гибко и полно описывать табличные данные (числовые и текстовые).</span><span class="sxs-lookup"><span data-stu-id="3359f-255">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="3359f-256">Данные можно загружать в объект `IDataView` из текстового файла или в режиме реального времени (например, из базы данных SQL или файлов журнала).</span><span class="sxs-lookup"><span data-stu-id="3359f-256">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="3359f-257">Обучите модель сна основе данных, загруженных ранее:</span><span class="sxs-lookup"><span data-stu-id="3359f-257">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](./snippets/image-classification/csharp/Program.cs#TrainModel)]

    <span data-ttu-id="3359f-258">Метод `Fit()` обучает модель путем применения набора данных для обучения к конвейеру.</span><span class="sxs-lookup"><span data-stu-id="3359f-258">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="3359f-259">Оценка точности модели</span><span class="sxs-lookup"><span data-stu-id="3359f-259">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="3359f-260">Загрузите и преобразуйте проверочные данные, добавив приведенный ниже код в следующую строку метода `GenerateModel`:</span><span class="sxs-lookup"><span data-stu-id="3359f-260">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](./snippets/image-classification/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="3359f-261">Есть несколько примеров изображений, которые можно использовать для оценки модели.</span><span class="sxs-lookup"><span data-stu-id="3359f-261">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="3359f-262">Как и данные для обучения, их нужно загрузить в `IDataView`, чтобы модель могла их преобразовать.</span><span class="sxs-lookup"><span data-stu-id="3359f-262">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="3359f-263">Добавьте следующий код в метод `GenerateModel()` для оценки модели:</span><span class="sxs-lookup"><span data-stu-id="3359f-263">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](./snippets/image-classification/csharp/Program.cs#Evaluate)]

    <span data-ttu-id="3359f-264">Получив прогноз, с помощью метода [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) вы сможете:</span><span class="sxs-lookup"><span data-stu-id="3359f-264">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="3359f-265">оценить модель (сравнивает спрогнозированные значения с тестовым набором данных `labels`);</span><span class="sxs-lookup"><span data-stu-id="3359f-265">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="3359f-266">получить метрики производительности модели.</span><span class="sxs-lookup"><span data-stu-id="3359f-266">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="3359f-267">Отобразите метрики точности модели.</span><span class="sxs-lookup"><span data-stu-id="3359f-267">Display the model accuracy metrics</span></span>

    <span data-ttu-id="3359f-268">Используйте следующий код для отображения метрик, передачи результатов и выполнения действий по ним:</span><span class="sxs-lookup"><span data-stu-id="3359f-268">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](./snippets/image-classification/csharp/Program.cs#DisplayMetrics)]

    <span data-ttu-id="3359f-269">Для классификации изображений выполняется оценка следующих метрик:</span><span class="sxs-lookup"><span data-stu-id="3359f-269">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="3359f-270">`Log-loss` — см. раздел [Логарифмические потери](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="3359f-270">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="3359f-271">Значение логарифмических потерь должно быть максимально близко к нулю.</span><span class="sxs-lookup"><span data-stu-id="3359f-271">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="3359f-272">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="3359f-272">`Per class Log-loss`.</span></span> <span data-ttu-id="3359f-273">Значение логарифмических потерь для каждого класса должно быть максимально близко к нулю.</span><span class="sxs-lookup"><span data-stu-id="3359f-273">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="3359f-274">Добавьте следующий код, чтобы возвращать обученную модель:</span><span class="sxs-lookup"><span data-stu-id="3359f-274">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](./snippets/image-classification/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="3359f-275">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="3359f-275">Run the application!</span></span>

1. <span data-ttu-id="3359f-276">Добавьте вызов `GenerateModel` в метод `Main` после создания класса MLContext:</span><span class="sxs-lookup"><span data-stu-id="3359f-276">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](./snippets/image-classification/csharp/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="3359f-277">Добавьте такой вызов в метод `ClassifySingleImage()` в виде следующей строки кода в методе `Main`:</span><span class="sxs-lookup"><span data-stu-id="3359f-277">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](./snippets/image-classification/csharp/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="3359f-278">Запустите консольное приложение (CTRL+F5).</span><span class="sxs-lookup"><span data-stu-id="3359f-278">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="3359f-279">Результаты выполнения должны выглядеть примерно так, как указано ниже.</span><span class="sxs-lookup"><span data-stu-id="3359f-279">Your results should be similar to the following output.</span></span>  <span data-ttu-id="3359f-280">Кроме того, могут выводиться предупреждения или сообщения об обработке, но для удобства здесь мы убрали их.</span><span class="sxs-lookup"><span data-stu-id="3359f-280">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="3359f-281">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="3359f-281">Congratulations!</span></span> <span data-ttu-id="3359f-282">Итак, вы завершили создание в ML.NET модели классификации изображений с использованием предварительно обученной модели обработки TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="3359f-282">You've now successfully built a classification model in ML.NET to categorize images by using a pre-trained TensorFlow for image processing.</span></span>

<span data-ttu-id="3359f-283">Исходный код для этого руководства можно найти в репозитории [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="3359f-283">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="3359f-284">В этом руководстве вы узнали, как:</span><span class="sxs-lookup"><span data-stu-id="3359f-284">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="3359f-285">Определение проблемы</span><span class="sxs-lookup"><span data-stu-id="3359f-285">Understand the problem</span></span>
> * <span data-ttu-id="3359f-286">внедрить предварительно обученную модель TensorFlow в конвейер ML.NET;</span><span class="sxs-lookup"><span data-stu-id="3359f-286">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="3359f-287">обучить и оценить модель ML.NET;</span><span class="sxs-lookup"><span data-stu-id="3359f-287">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="3359f-288">классифицировать тестовое изображение.</span><span class="sxs-lookup"><span data-stu-id="3359f-288">Classify a test image</span></span>

<span data-ttu-id="3359f-289">Ознакомьтесь с примерами Машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример классификации изображений.</span><span class="sxs-lookup"><span data-stu-id="3359f-289">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3359f-290">Репозиторий GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="3359f-290">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
