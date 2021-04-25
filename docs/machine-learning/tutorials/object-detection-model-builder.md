---
title: Руководство. Обнаружение объектов на изображениях с помощью Model Builder
description: В этом руководстве показано, как создать модель обнаружения объектов с помощью ML.NET Model Builder и Машинного обучения Azure для обнаружения знака STOP на изображениях.
author: briacht
ms.author: brachtma
ms.date: 04/13/2021
ms.topic: tutorial
ms.custom: mlnet-tooling
ms.openlocfilehash: f628be47bbef080505355fa99630c68b327f1a60
ms.sourcegitcommit: 5ddbd1f65d0369b4cc8c8ff91c72f1b524c90221
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2021
ms.locfileid: "107514506"
---
# <a name="tutorial-detect-stop-signs-in-images-with-model-builder"></a><span data-ttu-id="88013-103">Руководство. Обнаружение знака STOP на изображениях с помощью Model Builder</span><span class="sxs-lookup"><span data-stu-id="88013-103">Tutorial: Detect stop signs in images with Model Builder</span></span>

<span data-ttu-id="88013-104">Узнайте, как с помощью ML.NET Model Builder и Машинного обучения Azure создать модель обнаружения объектов для нахождения на изображениях знака STOP.</span><span class="sxs-lookup"><span data-stu-id="88013-104">Learn how to build an object detection model using ML.NET Model Builder and Azure Machine Learning to detect and locate stop signs in images.</span></span>

<span data-ttu-id="88013-105">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="88013-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="88013-106">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="88013-106">Prepare and understand the data</span></span>
> - <span data-ttu-id="88013-107">выбрать сценарий;</span><span class="sxs-lookup"><span data-stu-id="88013-107">Choose the scenario</span></span>
> - <span data-ttu-id="88013-108">выбрать среду обучения;</span><span class="sxs-lookup"><span data-stu-id="88013-108">Choose the training environment</span></span>
> - <span data-ttu-id="88013-109">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="88013-109">Load the data</span></span>
> - <span data-ttu-id="88013-110">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="88013-110">Train the model</span></span>
> - <span data-ttu-id="88013-111">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="88013-111">Evaluate the model</span></span>
> - <span data-ttu-id="88013-112">Использование модели для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="88013-112">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="88013-113">Построитель моделей в настоящее время находится на этапе предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="88013-113">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88013-114">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="88013-114">Prerequisites</span></span>

<span data-ttu-id="88013-115">Список необходимых компонентов и инструкции по установке см. в [руководстве по установке построителя моделей](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="88013-115">For a list of prerequisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="model-builder-object-detection-overview"></a><span data-ttu-id="88013-116">Общие сведения об обнаружении объектов в Model Builder</span><span class="sxs-lookup"><span data-stu-id="88013-116">Model Builder object detection overview</span></span>

<span data-ttu-id="88013-117">Обнаружение объектов — это задача в области компьютерного зрения.</span><span class="sxs-lookup"><span data-stu-id="88013-117">Object detection is a computer vision problem.</span></span> <span data-ttu-id="88013-118">Несмотря на связь с классификацией изображений, обнаружение объектов выполняет классификацию изображений в более детализированном масштабе.</span><span class="sxs-lookup"><span data-stu-id="88013-118">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="88013-119">Обнаружение объектов находит _и_ категоризует сущности на изображениях.</span><span class="sxs-lookup"><span data-stu-id="88013-119">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="88013-120">Модели обнаружения объектов обычно обучаются с использованием глубокого обучения и нейронных сетей.</span><span class="sxs-lookup"><span data-stu-id="88013-120">Object detection models are commonly trained using deep learning and neural networks.</span></span> <span data-ttu-id="88013-121">Дополнительные сведения: [Сравнение глубокого и машинного обучения](/azure/machine-learning/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="88013-121">See [Deep learning vs machine learning](/azure/machine-learning/concept-deep-learning-vs-machine-learning) for more information.</span></span>

<span data-ttu-id="88013-122">Используйте обнаружение объектов, если изображения содержат несколько объектов разных типов.</span><span class="sxs-lookup"><span data-stu-id="88013-122">Use object detection when images contain multiple objects of different types.</span></span>

![Снимки экрана с данными классификации изображений и классификации объектов.](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="88013-124">Некоторые варианты применения обнаружения объектов:</span><span class="sxs-lookup"><span data-stu-id="88013-124">Some use cases for object detection include:</span></span>

- <span data-ttu-id="88013-125">Автомобили с автономным управлением</span><span class="sxs-lookup"><span data-stu-id="88013-125">Self-Driving Cars</span></span>
- <span data-ttu-id="88013-126">Робототехника</span><span class="sxs-lookup"><span data-stu-id="88013-126">Robotics</span></span>
- <span data-ttu-id="88013-127">Обнаружение лиц</span><span class="sxs-lookup"><span data-stu-id="88013-127">Face Detection</span></span>
- <span data-ttu-id="88013-128">Техника безопасности</span><span class="sxs-lookup"><span data-stu-id="88013-128">Workplace Safety</span></span>
- <span data-ttu-id="88013-129">Подсчет объектов</span><span class="sxs-lookup"><span data-stu-id="88013-129">Object Counting</span></span>
- <span data-ttu-id="88013-130">Распознавание активности</span><span class="sxs-lookup"><span data-stu-id="88013-130">Activity Recognition</span></span>

<span data-ttu-id="88013-131">В этом примере создается консольное приложение .NET Core на языке C#, которое определяет знак STOP на изображениях с помощью модели машинного обучения, созданной в Model Builder.</span><span class="sxs-lookup"><span data-stu-id="88013-131">This sample creates a C# .NET Core console application that detects stop signs in images using a machine learning model built with Model Builder.</span></span> <span data-ttu-id="88013-132">Исходный код примера из этого руководства можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/ObjectDetection_StopSigns) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="88013-132">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/ObjectDetection_StopSigns) GitHub repository.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="88013-133">Подготовка и анализ данных</span><span class="sxs-lookup"><span data-stu-id="88013-133">Prepare and understand the data</span></span>

<span data-ttu-id="88013-134">Набор данных Stop Sign содержит 50 изображений, скачанных с сайта [Unsplash](https://unsplash.com/), на каждом из которых есть хотя бы один знак STOP.</span><span class="sxs-lookup"><span data-stu-id="88013-134">The Stop Sign dataset consists of 50 images downloaded from [Unsplash](https://unsplash.com/), each of which contain at least one stop sign.</span></span>

<span data-ttu-id="88013-135">Первое, что нужно сделать, — добавить заметки к изображениям или нарисовать ограничивающие прямоугольники вокруг знаков STOP на каждом изображении.</span><span class="sxs-lookup"><span data-stu-id="88013-135">The first thing you need to do is annotate your images, or draw bounding boxes around the stop signs in each image.</span></span> <span data-ttu-id="88013-136">В этом руководстве показано, как добавить заметки к изображениям с помощью средства [VoTT](https://github.com/microsoft/VoTT).</span><span class="sxs-lookup"><span data-stu-id="88013-136">In this tutorial, you will annotate your images with a tool called [VoTT](https://github.com/microsoft/VoTT).</span></span>

> <span data-ttu-id="88013-137">Если вы хотите пропустить шаги по маркировке данных, вы можете [скачать эту версию набора данных](https://aka.ms/mlnet-object-detection-tutorial-assets) и перейти к [созданию консольного приложения](object-detection-model-builder.md#create-a-console-application).</span><span class="sxs-lookup"><span data-stu-id="88013-137">If you want to skip the data labeling steps below, you can [download this version of the dataset](https://aka.ms/mlnet-object-detection-tutorial-assets) and skip to [Create a console application](object-detection-model-builder.md#create-a-console-application).</span></span>

### <a name="create-a-new-vott-project"></a><span data-ttu-id="88013-138">Создание нового проекта VoTT</span><span class="sxs-lookup"><span data-stu-id="88013-138">Create a new VoTT project</span></span>

1. <span data-ttu-id="88013-139">[Скачайте набор данных](https://aka.ms/mlnet-object-detection-tutorial-dataset), содержащий 50 изображений со знаком STOP, и распакуйте его.</span><span class="sxs-lookup"><span data-stu-id="88013-139">[Download the dataset](https://aka.ms/mlnet-object-detection-tutorial-dataset) of 50 stop sign images and unzip.</span></span>
1. <span data-ttu-id="88013-140">[Скачайте VoTT](https://github.com/Microsoft/VoTT/releases) (средство расстановки тегов для визуальных объектов).</span><span class="sxs-lookup"><span data-stu-id="88013-140">[Download VoTT](https://github.com/Microsoft/VoTT/releases) (Visual Object Tagging Tool).</span></span>
1. <span data-ttu-id="88013-141">Откройте VoTT и выберите элемент **New Project** (Создать проект).</span><span class="sxs-lookup"><span data-stu-id="88013-141">Open VoTT and select **New Project**.</span></span>

    ![Начальный экран VoTT](./media/object-detection-model-builder/vott.png)

1. <span data-ttu-id="88013-143">В разделе **Project Settings** (Параметры проекта) укажите в поле **Display Name** (Отображаемое имя) значение StopSignObjDetection.</span><span class="sxs-lookup"><span data-stu-id="88013-143">In **Project Settings**, change the **Display Name** to "StopSignObjDetection".</span></span>
1. <span data-ttu-id="88013-144">Укажите в поле **Security Token** (Маркер безопасности) значение *Generate New Security Token* (Создать новый маркер безопасности).</span><span class="sxs-lookup"><span data-stu-id="88013-144">Change the **Security Token** to *Generate New Security Token*.</span></span>
1. <span data-ttu-id="88013-145">Рядом с полем **Source Connection** (Исходное подключение) щелкните элемент **Add Connection** (Добавить подключение).</span><span class="sxs-lookup"><span data-stu-id="88013-145">Next to **Source Connection**, select **Add Connection**.</span></span>
1. <span data-ttu-id="88013-146">В разделе **Connection Settings** (Параметры подключения) укажите в поле **Display Name** (Отображаемое имя) для подключения к источнику значение StopSignImages и укажите в поле **Provider** (Поставщик) значение *Local File System* (Локальная файловая система).</span><span class="sxs-lookup"><span data-stu-id="88013-146">In **Connection Settings**, change the **Display Name** for the source connection to "StopSignImages", and select *Local File System* as the **Provider**.</span></span> <span data-ttu-id="88013-147">В поле **Folder Path** (Путь к папке) укажите папку *Stop-Signs* с 50 обучающими изображениями и щелкните элемент **Save Connection** (Сохранить подключение).</span><span class="sxs-lookup"><span data-stu-id="88013-147">For the **Folder Path**, select the *Stop-Signs* folder which contains the 50 training images, and then select **Save Connection**.</span></span>

    ![Диалоговое окно New Connection (Новое подключение) в VoTT](./media/object-detection-model-builder/vott-new-connection.png)

1. <span data-ttu-id="88013-149">В разделе **Project Settings** (Параметры проекта) укажите в поле **Source Connection** (Исходное подключение) значение *StopSignImages* (только что созданное подключение).</span><span class="sxs-lookup"><span data-stu-id="88013-149">In **Project Settings**, change the **Source Connection** to *StopSignImages* (the connection you just created).</span></span>
1. <span data-ttu-id="88013-150">В поле **Target Connection** (Целевое подключение) также укажите значение *StopSignImages*.</span><span class="sxs-lookup"><span data-stu-id="88013-150">Change the **Target Connection** to *StopSignImages* as well.</span></span> <span data-ttu-id="88013-151">Теперь раздел **Параметры проекта** должен выглядеть примерно так, как показано на следующем снимке экрана:</span><span class="sxs-lookup"><span data-stu-id="88013-151">Your **Project Settings** should now look similar to this screenshot:</span></span>

    ![Диалоговое окно Project Settings (Параметры проекта) в VoTT](./media/object-detection-model-builder/vott-new-project.png)

1. <span data-ttu-id="88013-153">Щелкните элемент **Save Project** (Сохранить проект).</span><span class="sxs-lookup"><span data-stu-id="88013-153">Select **Save Project**.</span></span>

### <a name="add-tag-and-label-images"></a><span data-ttu-id="88013-154">Добавление тегов и меток к изображениям</span><span class="sxs-lookup"><span data-stu-id="88013-154">Add tag and label images</span></span>

<span data-ttu-id="88013-155">Теперь вы должны увидеть окно с изображениями для предварительного просмотра всех обучающих изображений слева, выбранным изображением для предварительного просмотра в центре и столбцом **Tags** (Теги) справа.</span><span class="sxs-lookup"><span data-stu-id="88013-155">You should now see a window with preview images of all the training images on the left, a preview of the selected image in the middle, and a **Tags** column on the right.</span></span> <span data-ttu-id="88013-156">Это экран **редактора тегов**.</span><span class="sxs-lookup"><span data-stu-id="88013-156">This screen is the **Tags editor**.</span></span>

1. <span data-ttu-id="88013-157">Чтобы добавить новый тег, щелкните значок плюса (первый) на панели инструментов **Tags** (Теги).</span><span class="sxs-lookup"><span data-stu-id="88013-157">Select the first (plus-shaped) icon in the **Tags** toolbar to add a new tag.</span></span>

    ![Значок добавления тега в VoTT](./media/object-detection-model-builder/vott-new-tag-icon.png)

1. <span data-ttu-id="88013-159">Назовите тег Stop-Sign и нажмите клавишу <kbd>ВВОД</kbd> на клавиатуре.</span><span class="sxs-lookup"><span data-stu-id="88013-159">Name the tag "Stop-Sign" and hit <kbd>Enter</kbd> on your keyboard.</span></span>

    ![Новый тег в VoTT](./media/object-detection-model-builder/vott-new-tag.png)

1. <span data-ttu-id="88013-161">Щелкните и удерживайте левую копку мыши, чтобы нарисовать прямоугольник вокруг каждого знака STOP на изображении.</span><span class="sxs-lookup"><span data-stu-id="88013-161">Click and drag to draw a rectangle around each stop sign in the image.</span></span> <span data-ttu-id="88013-162">Если курсор не позволяет нарисовать прямоугольник, попробуйте сделать это с помощью средства **Draw Rectangle** (Нарисовать прямоугольник) на панели инструментов вверху или используйте сочетание клавиш <kbd>R</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88013-162">If the cursor does not let you draw a rectangle, try selecting the **Draw Rectangle** tool from the toolbar on the top, or use the keyboard shortcut <kbd>R</kbd>.</span></span>
1. <span data-ttu-id="88013-163">Нарисовав прямоугольник, выберите тег **Stop-Sign**, созданный ранее, чтобы добавить его к ограничивающему прямоугольнику.</span><span class="sxs-lookup"><span data-stu-id="88013-163">After drawing your rectangle, select the **Stop-Sign** tag that you created in the previous steps to add the tag to the bounding box.</span></span>
1. <span data-ttu-id="88013-164">Щелкните в наборе данных следующее изображение для предварительного просмотра и повторите эту процедуру.</span><span class="sxs-lookup"><span data-stu-id="88013-164">Click on the preview image for the next image in the dataset and repeat this process.</span></span>
1. <span data-ttu-id="88013-165">Продолжайте шаги 3–4 для каждого из этих изображений.</span><span class="sxs-lookup"><span data-stu-id="88013-165">Continue steps 3-4 for every stop sign in every image.</span></span>

    ![Добавление заметок к изображениям в VoTT](./media/object-detection-model-builder/vott-annotating.gif)

### <a name="export-your-vott-json"></a><span data-ttu-id="88013-167">Экспорт JSON в VoTT</span><span class="sxs-lookup"><span data-stu-id="88013-167">Export your VoTT JSON</span></span>

<span data-ttu-id="88013-168">Промаркировав все обучающие изображения, можно экспортировать файл, который Model Builder будет использовать для обучения.</span><span class="sxs-lookup"><span data-stu-id="88013-168">Once you have labeled all of your training images, you can export the file that will be used by Model Builder for training.</span></span>

1. <span data-ttu-id="88013-169">Выберите значок с диагональной стрелкой на панели инструментов слева (четвертый), чтобы перейти в раздел **Export Settings** (Параметры экспорта).</span><span class="sxs-lookup"><span data-stu-id="88013-169">Select the fourth icon in the left toolbar (the one with the diagonal arrow in a box) to go to the **Export Settings**.</span></span>
1. <span data-ttu-id="88013-170">Оставьте в поле **Provider** (Поставщик) значение *VoTT JSON*.</span><span class="sxs-lookup"><span data-stu-id="88013-170">Leave the **Provider** as *VoTT JSON*.</span></span>
1. <span data-ttu-id="88013-171">Укажите в поле **Asset State** (Состояние ресурса) значение *Only tagged Assets* (Только ресурсы с тегами).</span><span class="sxs-lookup"><span data-stu-id="88013-171">Change the **Asset State** to *Only tagged Assets*.</span></span>
1. <span data-ttu-id="88013-172">Снимите флажок **Include Images** (Включить изображения).</span><span class="sxs-lookup"><span data-stu-id="88013-172">Uncheck **Include Images**.</span></span> <span data-ttu-id="88013-173">Иначе обучающие изображения будут скопированы в создаваемую папку экспорта, что является необязательным действием.</span><span class="sxs-lookup"><span data-stu-id="88013-173">If you include the images, then the training images will be copied to the export folder that is generated, which is not necessary.</span></span>
1. <span data-ttu-id="88013-174">Щелкните элемент **Save Export Settings** (Сохранить параметры экспорта).</span><span class="sxs-lookup"><span data-stu-id="88013-174">Select **Save Export Settings**.</span></span>

    ![Параметры экспорта VoTT](./media/object-detection-model-builder/vott-export.png)

1. <span data-ttu-id="88013-176">Вернитесь в **редактор тегов** (второй значок на панели инструментов слева в форме ленты).</span><span class="sxs-lookup"><span data-stu-id="88013-176">Go back to the **Tags editor** (the second icon in the left toolbar shaped like a ribbon).</span></span> <span data-ttu-id="88013-177">На верхней панели инструментов щелкните значок **Export Project** (Экспорт проекта) (последний значок в форме стрелки) или нажмите клавиши <kbd>CTRL</kbd>+<kbd>E</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88013-177">In the top toolbar, select the **Export Project** icon (the last icon shaped like an arrow in a box), or use the keyboard shortcut <kbd>Ctrl</kbd>+<kbd>E</kbd>.</span></span>

    ![Кнопка экспорта VoTT](./media/object-detection-model-builder/vott-export-button.png)

<span data-ttu-id="88013-179">В ходе экспорта будет создана новая папка с именем *vott-json-export* в папке *Stop-Sign-Images*, которая будет содержать файл JSON с именем *StopSignObjDetection-export*.</span><span class="sxs-lookup"><span data-stu-id="88013-179">This export will create a new folder called *vott-json-export* in your *Stop-Sign-Images* folder and will generate a JSON file named *StopSignObjDetection-export* in that new folder.</span></span> <span data-ttu-id="88013-180">Этот файл JSON будет использоваться в следующих шагах для обучения модели обнаружения объектов в Model Builder.</span><span class="sxs-lookup"><span data-stu-id="88013-180">You will use this JSON file in the next steps for training an object detection model in Model Builder.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="88013-181">Создание консольного приложение</span><span class="sxs-lookup"><span data-stu-id="88013-181">Create a console application</span></span>

1. <span data-ttu-id="88013-182">В Visual Studio создайте **консольное приложение C# .NET Core** с именем *StopSignDetection*.</span><span class="sxs-lookup"><span data-stu-id="88013-182">In Visual Studio, create a **C# .NET Core console application** called *StopSignDetection*.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="88013-183">Выбор сценария</span><span class="sxs-lookup"><span data-stu-id="88013-183">Choose a scenario</span></span>

1. <span data-ttu-id="88013-184">В **Обозревателе решений** щелкните правой кнопкой мыши проект *StopSignDetection* и выберите элементы **Добавить** > **Машинное обучение**, чтобы открыть пользовательский интерфейс Model Builder.</span><span class="sxs-lookup"><span data-stu-id="88013-184">In **Solution Explorer**, right-click the *StopSignDetection* project, and select **Add** > **Machine Learning** to open the Model Builder UI.</span></span>
1. <span data-ttu-id="88013-185">В этом примере сценарий включает обнаружение объектов.</span><span class="sxs-lookup"><span data-stu-id="88013-185">For this sample, the scenario is object detection.</span></span> <span data-ttu-id="88013-186">На этапе **Сценарий** в Model Builder выберите сценарий **Обнаружение объектов**.</span><span class="sxs-lookup"><span data-stu-id="88013-186">In the **Scenario** step of Model Builder, select the **Object Detection** scenario.</span></span>

![Мастер построителя моделей в Visual Studio](./media/object-detection-model-builder/obj-det-scenario.png)

> <span data-ttu-id="88013-188">Если вариант *Обнаружение объектов* не отображается в списке сценариев, попробуйте [обновить версию Model Builder](https://marketplace.visualstudio.com/items?itemName=MLNET.07).</span><span class="sxs-lookup"><span data-stu-id="88013-188">If you don't see *Object Detection* in the list of scenarios, you may need to [update your version of Model Builder](https://marketplace.visualstudio.com/items?itemName=MLNET.07).</span></span>

## <a name="choose-the-training-environment"></a><span data-ttu-id="88013-189">Выбор среды обучения</span><span class="sxs-lookup"><span data-stu-id="88013-189">Choose the training environment</span></span>

<span data-ttu-id="88013-190">Сейчас Model Builder поддерживает обучение моделей обнаружению объектов только с использованием Машинного обучения Azure, поэтому обучающая среда Azure выбрана по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="88013-190">Currently, Model Builder supports training object detection models with Azure Machine Learning only, so the Azure training environment is selected by default.</span></span>

![Выбор обучающей среды Azure](./media/object-detection-model-builder/obj-det-environment.png)

<span data-ttu-id="88013-192">Чтобы обучить модель с помощью Машинного обучения Azure, создайте эксперимент Машинного обучения Azure в Model Builder.</span><span class="sxs-lookup"><span data-stu-id="88013-192">To train a model using Azure ML, you must create an Azure ML experiment from Model Builder.</span></span>

<span data-ttu-id="88013-193">**Эксперимент Машинного обучения Azure** инкапсулирует конфигурацию и результаты одного или нескольких обучающих выполнений машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="88013-193">An **Azure ML experiment** is a resource that encapsulates the configuration and results for one or more machine learning training runs.</span></span>

<span data-ttu-id="88013-194">Чтобы создать эксперимент Машинного обучения Azure, необходимо сначала настроить среду в Azure.</span><span class="sxs-lookup"><span data-stu-id="88013-194">To create an Azure ML experiment, you first need to configure your environment in Azure.</span></span> <span data-ttu-id="88013-195">Для выполнения эксперимента требуется следующее:</span><span class="sxs-lookup"><span data-stu-id="88013-195">An experiment needs the following to run:</span></span>

- <span data-ttu-id="88013-196">подписка Azure;</span><span class="sxs-lookup"><span data-stu-id="88013-196">An Azure subscription</span></span>
- <span data-ttu-id="88013-197">**рабочая область** — ресурс Машинного обучения Azure, который является централизованным расположением для всех ресурсов и артефактов Машинного обучения Azure, создаваемых в ходе обучения;</span><span class="sxs-lookup"><span data-stu-id="88013-197">A **workspace**: an Azure ML resource that provides a central place for all Azure ML resources and artifacts created as part of a training run.</span></span>
- <span data-ttu-id="88013-198">**вычислительная среда Машинного обучения** — облачная виртуальная машина Linux, используемая для обучения;</span><span class="sxs-lookup"><span data-stu-id="88013-198">A **compute**: an Azure Machine Learning compute is a cloud-based Linux VM used for training.</span></span> <span data-ttu-id="88013-199">см. сведения о [вычислениях, поддерживаемых Model Builder](../resources/azure-training-concepts-model-builder.md#what-is-an-azure-machine-learning-compute).</span><span class="sxs-lookup"><span data-stu-id="88013-199">Learn more about [compute types supported by Model Builder](../resources/azure-training-concepts-model-builder.md#what-is-an-azure-machine-learning-compute).</span></span>

### <a name="set-up-an-azure-ml-workspace"></a><span data-ttu-id="88013-200">Настройка рабочей области Машинного обучения Azure</span><span class="sxs-lookup"><span data-stu-id="88013-200">Set up an Azure ML workspace</span></span>

<span data-ttu-id="88013-201">Чтобы настроить среду:</span><span class="sxs-lookup"><span data-stu-id="88013-201">To configure your environment:</span></span>

1. <span data-ttu-id="88013-202">Нажмите кнопку **Настроить рабочую область**.</span><span class="sxs-lookup"><span data-stu-id="88013-202">Select the **Set up workspace** button.</span></span>
1. <span data-ttu-id="88013-203">В диалоговом окне **Создание нового эксперимента** выберите свою подписку Azure.</span><span class="sxs-lookup"><span data-stu-id="88013-203">In the **Create new experiment** dialog, select your Azure subscription.</span></span>
1. <span data-ttu-id="88013-204">Создайте новую рабочую область Машинного обучения Azure или выберите существующую.</span><span class="sxs-lookup"><span data-stu-id="88013-204">Select an existing workspace or create a new Azure ML workspace.</span></span>

    <span data-ttu-id="88013-205">При создании новой рабочей области подготавливаются следующие ресурсы:</span><span class="sxs-lookup"><span data-stu-id="88013-205">When you create a new workspace, the following resources are provisioned:</span></span>

    - <span data-ttu-id="88013-206">Рабочая область службы "Машинное обучение Azure"</span><span class="sxs-lookup"><span data-stu-id="88013-206">Azure Machine Learning workspace</span></span>
    - <span data-ttu-id="88013-207">Хранилище Azure</span><span class="sxs-lookup"><span data-stu-id="88013-207">Azure Storage</span></span>
    - <span data-ttu-id="88013-208">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="88013-208">Azure Application Insights</span></span>
    - <span data-ttu-id="88013-209">Реестр контейнеров Azure</span><span class="sxs-lookup"><span data-stu-id="88013-209">Azure Container Registry</span></span>
    - <span data-ttu-id="88013-210">Хранилище ключей Azure;</span><span class="sxs-lookup"><span data-stu-id="88013-210">Azure Key Vault</span></span>

    <span data-ttu-id="88013-211">В результате этот процесс может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="88013-211">As a result, this process may take a few minutes.</span></span>

1. <span data-ttu-id="88013-212">Создайте новое вычисление машинного обучения Azure или выберите существующее.</span><span class="sxs-lookup"><span data-stu-id="88013-212">Select an existing compute or create a new Azure ML compute.</span></span> <span data-ttu-id="88013-213">Это может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="88013-213">This process may take a few minutes.</span></span>
1. <span data-ttu-id="88013-214">Оставьте имя эксперимента по умолчанию и щелкните элемент **Создать**.</span><span class="sxs-lookup"><span data-stu-id="88013-214">Leave the default experiment name and select **Create**.</span></span>

    ![Диалоговое окно настройки рабочей области Azure](./media/object-detection-model-builder/azure-dialog.png)

<span data-ttu-id="88013-216">Когда первый эксперимент будет создан, его имя регистрируется в рабочей области.</span><span class="sxs-lookup"><span data-stu-id="88013-216">The first experiment is created, and the experiment name is registered in the workspace.</span></span> <span data-ttu-id="88013-217">Все последующие выполнения (при использовании одного и того же имени эксперимента) регистрируются как часть одного эксперимента.</span><span class="sxs-lookup"><span data-stu-id="88013-217">Any subsequent runs (if the same experiment name is used ) are logged as part of the same experiment.</span></span> <span data-ttu-id="88013-218">В противном случае создается новый эксперимент.</span><span class="sxs-lookup"><span data-stu-id="88013-218">Otherwise, a new experiment is created.</span></span>

<span data-ttu-id="88013-219">Если вас устраивает конфигурация, нажмите кнопку **Следующий шаг** в Model Builder, чтобы перейти к шагу **Данные**.</span><span class="sxs-lookup"><span data-stu-id="88013-219">If you’re satisfied with your configuration, select the **Next step** button in Model Builder to move to the **Data** step.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="88013-220">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="88013-220">Load the data</span></span>

<span data-ttu-id="88013-221">На шаге **Данные** в Model Builder вы выберете обучающий набор данных.</span><span class="sxs-lookup"><span data-stu-id="88013-221">In the **Data** step of Model Builder, you will select your training dataset.</span></span>

><span data-ttu-id="88013-222">Сейчас Model Builder принимает только файлы JSON, создаваемые в VoTT, но команда разработки планирует включить поддержку других форматов в будущем.</span><span class="sxs-lookup"><span data-stu-id="88013-222">Model Builder currently only accepts the format of JSON generated by VoTT, but the team plans to add support for more formats in the future.</span></span> <span data-ttu-id="88013-223">Если есть формат набора данных для обнаружения объектов, который вы хотели бы использовать в Model Builder, оставьте свой отзыв на сайте [GitHub](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?assignees=&labels=&template=data_suggestion.md&title=).</span><span class="sxs-lookup"><span data-stu-id="88013-223">If there is a dataset format for object detection that you’d like to see supported in Model Builder, leave your feedback on [GitHub](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?assignees=&labels=&template=data_suggestion.md&title=).</span></span>

1. <span data-ttu-id="88013-224">Нажмите кнопку рядом с текстовым полем **Выбрать папку** и воспользуйтесь проводником, чтобы найти файл `StopSignObjDetection-export.json`, который должен быть расположен в каталоге *Stop-Signs/vott-json-export*.</span><span class="sxs-lookup"><span data-stu-id="88013-224">Select the button next to the **Select a folder** text box and use the File Explorer to find the `StopSignObjDetection-export.json` which should be located in the *Stop-Signs/vott-json-export* directory.</span></span>

    ![Шаг "Данные" в Model Builder](./media/object-detection-model-builder/obj-det-data.png)

1. <span data-ttu-id="88013-226">Если данные в разделе **Предварительная версия данных** выглядят правильно, нажмите кнопку **Следующий шаг**, чтобы перейти к шагу **Обучение**.</span><span class="sxs-lookup"><span data-stu-id="88013-226">If your data looks correct in the **Data Preview**, select **Next step** to move on to the **Train** step.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="88013-227">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="88013-227">Train the model</span></span>

<span data-ttu-id="88013-228">Следующий шаг — обучение модели.</span><span class="sxs-lookup"><span data-stu-id="88013-228">The next step is to train your model.</span></span>

<span data-ttu-id="88013-229">На экране **Обучение** в Model Builder нажмите кнопку **Начать обучение**.</span><span class="sxs-lookup"><span data-stu-id="88013-229">In the Model Builder **Train** screen, select the **Start training** button.</span></span>

<span data-ttu-id="88013-230">На этом этапе ваши данные будут отправлены в службу хранилища Azure и в Машинном обучении Azure начнется процесс обучения.</span><span class="sxs-lookup"><span data-stu-id="88013-230">At this point, your data is uploaded to Azure Storage and the training process begins in Azure ML.</span></span>

><span data-ttu-id="88013-231">Точная продолжительность обучения зависит от объема данных и выбранных вычислительных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="88013-231">The training process takes some time, and the amount of time may vary depending on the size of compute selected as well as the amount of data.</span></span> <span data-ttu-id="88013-232">Первое обучение модели в Azure может длиться чуть дольше, так как необходимо подготовить ресурсы.</span><span class="sxs-lookup"><span data-stu-id="88013-232">The first time a model is trained in Azure, you can expect a slightly longer training time because resources have to be provisioned.</span></span> <span data-ttu-id="88013-233">В этом примере с 50 изображениями обучение заняло около 16 минут.</span><span class="sxs-lookup"><span data-stu-id="88013-233">For this sample of 50 images, training took about 16 minutes.</span></span>

<span data-ttu-id="88013-234">Ход выполнения можно отслеживать на портале Машинного обучения Azure, щелкнув ссылку **Мониторинг текущего выполнения на портале Azure** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88013-234">You can track the progress of your runs in the Azure Machine Learning portal by selecting the **Monitor current run in Azure portal** link in Visual Studio.</span></span>

<span data-ttu-id="88013-235">Когда обучение завершится, нажмите кнопку **Следующий шаг**, чтобы перейти к шагу **Оценка**.</span><span class="sxs-lookup"><span data-stu-id="88013-235">Once training is complete, select the **Next step** button to move on to the **Evaluate** step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="88013-236">Оценка модели</span><span class="sxs-lookup"><span data-stu-id="88013-236">Evaluate the model</span></span>

<span data-ttu-id="88013-237">На экране оценки вы сможете просмотреть результаты процесса обучения, а также проверить точность модели.</span><span class="sxs-lookup"><span data-stu-id="88013-237">In the Evaluate screen, you get an overview of the results from the training process, including the model accuracy.</span></span>

![Шаг "Оценка" в Model Builder](./media/object-detection-model-builder/obj-det-evaluate.png)

<span data-ttu-id="88013-239">В этом случае точность составляет 100 %. Это означает, что модель, скорее всего, *переобучена* из-за слишком большого числа изображений в наборе данных.</span><span class="sxs-lookup"><span data-stu-id="88013-239">In this case, the accuracy says 100%, which means that the model is more than likely *overfit* due to too few images in the dataset.</span></span>

<span data-ttu-id="88013-240">Чтобы узнать, работает ли модель должным образом, можно воспользоваться возможностью **проверки модели**.</span><span class="sxs-lookup"><span data-stu-id="88013-240">You can use the **Try your model** experience to quickly check whether your model is performing as expected.</span></span>

<span data-ttu-id="88013-241">Щелкните элемент **Browse an image** (Обзор изображения) и укажите тестовое изображение — желательно такое, которое модель не использовала в процессе обучения.</span><span class="sxs-lookup"><span data-stu-id="88013-241">Select **Browse an image** and provide a test image, preferably one that the model did not use as part of training.</span></span>

![Проверка модели в Model Builder](./media/object-detection-model-builder/obj-det-try-model.png)

<span data-ttu-id="88013-243">Оценка, отображаемая для каждого обнаруженного ограничивающего прямоугольника, указывает на **достоверность** обнаруженного объекта.</span><span class="sxs-lookup"><span data-stu-id="88013-243">The score shown on each detected bounding box indicates the **confidence** of the detected object.</span></span> <span data-ttu-id="88013-244">Например, на снимке экрана выше оценка для ограничивающего прямоугольника вокруг знака STOP указывает на то, что модель с 99 % достоверностью распознает обнаруженный объект как знак STOP.</span><span class="sxs-lookup"><span data-stu-id="88013-244">For instance, in the screenshot above, the score on the bounding box around the stop sign indicates that the model is 99% sure that the detected object is a stop sign.</span></span>

<span data-ttu-id="88013-245">**Порог оценки**, который можно увеличить или уменьшить с помощью ползунка, позволяет добавлять и удалять обнаруженные объекты на основе их оценок.</span><span class="sxs-lookup"><span data-stu-id="88013-245">The **Score threshold**, which can be increased or decreased with the threshold slider, will add and remove detected objects based on their scores.</span></span> <span data-ttu-id="88013-246">Например, если порог равен 0,51, модель будет показывать только те объекты, которые имеют оценку достоверности 0,51 и выше.</span><span class="sxs-lookup"><span data-stu-id="88013-246">For instance, if the threshold is .51, then the model will only show objects that have a confidence score of .51 or above.</span></span> <span data-ttu-id="88013-247">По мере увеличения порога будет отображаться меньшее число обнаруженных объектов и наоборот.</span><span class="sxs-lookup"><span data-stu-id="88013-247">As you increase the threshold, you will see less detected objects, and as you decrease the threshold, you will see more detected objects.</span></span>

<span data-ttu-id="88013-248">Если вас не устраивают метрики точности, один простой способ повысить точность модели — использовать больше данных.</span><span class="sxs-lookup"><span data-stu-id="88013-248">If you're not satisfied with your accuracy metrics, one easy way to try to improve model accuracy is to use more data.</span></span> <span data-ttu-id="88013-249">В противном случае щелкните ссылку **Следующий шаг**, чтобы перейти к шагу **Код** в Model Builder.</span><span class="sxs-lookup"><span data-stu-id="88013-249">Otherwise, select the **Next step** link to move on to the **Code** step in Model Builder.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="88013-250">Добавление кода для прогнозирования</span><span class="sxs-lookup"><span data-stu-id="88013-250">Add the code to make predictions</span></span>

<span data-ttu-id="88013-251">В результате процесса обучения создаются два проекта.</span><span class="sxs-lookup"><span data-stu-id="88013-251">Two projects are created as a result of the training process.</span></span>

- <span data-ttu-id="88013-252">*StopSignDetectionML.ConsoleApp* — консольное приложение .NET Core на C# с кодом для обучения и использования модели.</span><span class="sxs-lookup"><span data-stu-id="88013-252">*StopSignDetectionML.ConsoleApp*: A C# .NET Core Console application that contains the model training code and sample consumption code.</span></span>
- <span data-ttu-id="88013-253">*StopSignDetectionML.Model* — библиотека классов .NET Standard с моделями данных, которые определяют схему входных и выходных данных модели, а также хранимую версию оптимальной модели во время обучения и вспомогательный класс с именем `ConsumeModel` для прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="88013-253">*StopSignDetectionML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training, and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="88013-254">На шаге кода в Model Builder щелкните элемент **Добавить проекты**, чтобы добавить автоматически созданные проекты в решение.</span><span class="sxs-lookup"><span data-stu-id="88013-254">In the code step of Model Builder, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="88013-255">Откройте файл *Program.cs* в проекте *StopSignDetection* и добавьте следующий оператор using в начало файла, чтобы создать ссылку на проект *StopSignDetectionML.Model*:</span><span class="sxs-lookup"><span data-stu-id="88013-255">Open the *Program.cs* file in the *StopSignDetection* project, and add the following using statement at the top of the file to reference the *StopSignDetectionML.Model* project:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L2)]

1. <span data-ttu-id="88013-256">Скачайте указанное ниже [тестовое изображение](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/test-image1.jpeg).</span><span class="sxs-lookup"><span data-stu-id="88013-256">Download the following [test image](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/test-image1.jpeg).</span></span>
1. <span data-ttu-id="88013-257">Создайте новый экземпляр класса `ModelInput` со свойством `ImageSource`, для которого задан путь к файлу тестового изображения, в методе `Main` приложения.</span><span class="sxs-lookup"><span data-stu-id="88013-257">Create a new instance of the `ModelInput` class with the `ImageSource` property set to the filepath of your test image inside the `Main` method of your application.</span></span> <span data-ttu-id="88013-258">Замените Hello World следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="88013-258">Replace the "Hello World" statement with the following code:</span></span>

    [!code-csharp [InputData](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L10-L15)]

1. <span data-ttu-id="88013-259">Используйте метод `Predict` из класса `ConsumeModel` для загрузки обученной модели, создания [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для модели и прогнозирования с использованием новых данных.</span><span class="sxs-lookup"><span data-stu-id="88013-259">Use the `Predict` method from the `ConsumeModel` class to load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model, and make predictions on new data.</span></span> <span data-ttu-id="88013-260">Добавьте следующий код под оператором `ModelInput`:</span><span class="sxs-lookup"><span data-stu-id="88013-260">Add the following code below the `ModelInput` statement:</span></span>

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L15)]

1. <span data-ttu-id="88013-261">Выведите выходные данные прогноза, включая метку, координаты и оценку, добавив следующий код:</span><span class="sxs-lookup"><span data-stu-id="88013-261">Print out the Prediction's output, including the label, coordinates, and score by adding the following code:</span></span>

    [!code-csharp [PrintResults](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L17-L18)]

1. <span data-ttu-id="88013-262">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="88013-262">Run the application.</span></span>

    <span data-ttu-id="88013-263">Выходные данные программы должны выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="88013-263">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Boxes:

    Top: 89.453415, Left: 481.95343, Right: 724.8073, Bottom: 388.32385, Label: Stop-Sign, Score: 0.99539465
    ```

<span data-ttu-id="88013-264">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="88013-264">Congratulations!</span></span> <span data-ttu-id="88013-265">Вы успешно создали модель машинного обучения для обнаружения знака STOP в изображениях с помощью Model Builder.</span><span class="sxs-lookup"><span data-stu-id="88013-265">You've successfully built a machine learning model to detect stop signs in images using Model Builder.</span></span> <span data-ttu-id="88013-266">Исходный код примера из этого руководства можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/ObjectDetection_StopSigns) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="88013-266">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/ObjectDetection_StopSigns) GitHub repository.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="88013-267">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="88013-267">Additional resources</span></span>

<span data-ttu-id="88013-268">Дополнительные сведения см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="88013-268">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="88013-269">Сценарии для построителя моделей</span><span class="sxs-lookup"><span data-stu-id="88013-269">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="88013-270">Обнаружение объектов с помощью ONNX в ML.NET</span><span class="sxs-lookup"><span data-stu-id="88013-270">Object Detection using ONNX in ML.NET</span></span>](object-detection-onnx.md)
