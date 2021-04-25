---
title: Учебник. Обнаружение объектов с помощью модели глубокого обучения ONNX
description: В этом учебнике показано, как использовать предварительно обученную модель глубокого обучения ONNX в ML.NET для обнаружения объектов в изображениях.
author: luisquintanilla
ms.author: luquinta
ms.date: 04/13/2021
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2146772d8db28568884e485b95c4cfe8e2ebba2d
ms.sourcegitcommit: 5ddbd1f65d0369b4cc8c8ff91c72f1b524c90221
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2021
ms.locfileid: "107514493"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Учебник. Обнаружение объектов с помощью ONNX в ML.NET

Узнайте, как использовать предварительно обученную модель ONNX в ML.NET для обнаружения объектов в изображениях.

Обучение модели для обнаружения объектов с нуля предусматривает настройку нескольких миллионов параметров, а также использование больших объемов помеченных данных обучения и вычислительных ресурсов (сотни часов работы GPU). Использование предварительно обученной модели позволяет упростить процесс обучения.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> - Определение проблемы
> - Узнайте, что такое ONNX и как он работает с ML.NET
> - Общие сведения о модели
> - Повторное использование предварительно обученной модели
> - Обнаружение объектов в загруженной модели

## <a name="pre-requisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".
- [Пакет Nuget Microsoft.ML](https://www.nuget.org/packages/Microsoft.ML/)
- [Пакет Nuget Microsoft.ML.ImageAnalytics](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Пакет NuGet Microsoft.ML.OnnxTransformer](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Предварительно обученная модель Tiny YOLOv2](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny-yolov2)
- [Netron](https://github.com/lutzroeder/netron) (необязательно)

## <a name="onnx-object-detection-sample-overview"></a>Обзор примера обнаружения объектов в ONNX

В этом примере создается консольное приложение .NET Core, которое обнаруживает объекты на изображении с помощью предварительно обученной модели ONNX для глубокого обучения. Код для этого примера можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) на сайте GitHub.

## <a name="what-is-object-detection"></a>Что такое обнаружение объектов?

Обнаружение объектов — это задача в области компьютерного зрения. Несмотря на связь с классификацией изображений, обнаружение объектов выполняет классификацию изображений в более детализированном масштабе. Обнаружение объектов находит _и_ категоризует сущности на изображениях. Модели обнаружения объектов обычно обучаются с использованием глубокого обучения и нейронных сетей. Дополнительные сведения: [Сравнение глубокого и машинного обучения](/azure/machine-learning/concept-deep-learning-vs-machine-learning).

Используйте обнаружение объектов, если изображения содержат несколько объектов разных типов.

![Снимки экрана с данными классификации изображений и классификации объектов.](./media/object-detection-onnx/img-classification-obj-detection.png)

Некоторые варианты применения обнаружения объектов:

- Автомобили с автономным управлением
- Робототехника
- Обнаружение лиц
- Техника безопасности
- Подсчет объектов
- Распознавание активности

## <a name="select-a-deep-learning-model"></a>Выбор модели глубокого обучения

Глубокое обучение — это подмножество машинного обучения. Для обучения моделей глубокого обучения требуются большие объемы данных. Закономерности в данных представлены рядом слоев. Связи в данных кодируются как соединения между слоями, имеющие веса. Чем выше вес, тем сильнее связь. В совокупности этот ряд уровней и соединений называют искусственными нейронными сетями. Чем больше уровней в сети, тем глубже нейронная сеть.

Существуют различные типы нейронных сетей; наиболее распространенные — многоуровневый перцептрон (MLP), сверточная нейронная сеть (CNN) и рекуррентная нейронная сеть (RNN). Самым простым вариантом является MLP, который сопоставляет набор входных данных с набором выходов. Эта нейронная сеть хорошо подходит, когда в данных отсутствует пространственный или временный компонент. CNN использует слои свертки для обработки пространственных данных, содержащихся в данных. Хорошим вариантом использования CNN является обработка изображений, позволяющая обнаружить присутствие некой черты в определенном регионе изображения (например, есть ли нос в центре изображения). Наконец, RNN позволяет использовать сохраняемость состояния или памяти, используемых в качестве входных данных. RNN используются для анализа временных рядов, где важны упорядочение и контекст событий.

### <a name="understand-the-model"></a>Общие сведения о модели

Обнаружение объектов — это задача обработки изображений. Поэтому большинство моделей глубокого обучения, предназначенных для решения этой проблемы, относятся к CNN. Модель, используемая в этом руководстве, — Tiny YOLOv2, более компактная версия модели YOLOv2, описанной в документе ["YOLO9000: лучше, быстрее и надежнее" (Редмон, Фархади)](https://arxiv.org/pdf/1612.08242.pdf). Модель Tiny YOLOv2 обучена на наборе данных Pascal ВОК и состоит из 15 уровней, которые могут прогнозировать 20 различных классов объектов. Так как Tiny YOLOv2 является сжатой версией исходной модели YOLOv2, между скоростью и точностью есть компромисс. Различные слои, составляющие модель, можно использовать для визуализации с помощью таких средств, как Netron. Изучение модели приведет к сопоставлению соединений между всеми слоями, которые составляют нейронную сеть, где каждый слой будет содержать имя слоя вместе с размерами соответствующих входных и выходных данных. Структуры данных, используемые для описания входных и выходных данных модели, называются тензорами. Их можно рассматривать как контейнеры, в которых данные хранятся в N измерениях. В случае Tiny YOLOv2 имя входного слоя — `image`, и он ожидает `3 x 416 x 416` измерений в тензоре. Имя выходного слоя — `grid`; он создает выходной тензор из `125 x 13 x 13` измерений.

![Входной слой разбивается на скрытые слои, а затем создается выходной слой](./media/object-detection-onnx/netron-model-map-layers.png)

Модель YOLO принимает изображение `3(RGB) x 416px x 416px`. Модель принимает эти входные данные и передает их через различные слои для создания выходных данных. Выходные данные делят входное изображение на сетку `13 x 13`, при этом каждая ячейка в сетке состоит из значений `125`.

### <a name="what-is-an-onnx-model"></a>Что такое модель ONNX?

Open Neural Network Exchange (ONNX) — это формат с открытым исходным кодом для моделей ИИ. ONNX поддерживает взаимодействие между разными платформами. Это означает, что модель можно обучить в одной из многих популярных платформ машинного обучения, таких как PyTorch, преобразовать ее в формат ONNX и использовать модель ONNX в другой инфраструктуре, такой как ML.NET. Дополнительные сведения см. на [веб-сайте ONNX](https://onnx.ai/).

![Схема используемых форматов, которые поддерживает ONNX.](./media/object-detection-onnx/onnx-supported-formats.png)

Предварительно обученная модель Tiny YOLOv2 хранится в формате ONNX: сериализованном представлении слоев и полученных закономерностях этих слоев. В ML.NET взаимодействие с ONNX достигается с помощью пакетов NuGet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) и [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer). Пакет [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) содержит ряд преобразований, которые принимают изображение и кодируют его в числовые значения, которые можно использовать в качестве входных данных в конвейере прогнозирования или обучения. Пакет [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) использует среду выполнения ONNX для загрузки модели ONNX и использует ее для создания прогнозов на основе предоставленных входных данных.

![Поток данных файла ONNX в среде выполнения ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>Создание проекта .NET Core

Теперь, когда у вас есть общее представление о том, что такое ONNX и как работает Tiny YOLOv2, пришло время создать приложение.

### <a name="create-a-console-application"></a>Создание консольного приложения

1. Создайте **консольное приложение .NET Core** с именем ObjectDetection.

1. Установите **пакет NuGet для Microsoft.ML**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    - В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**.
    - Выберите nuget.org в качестве источника пакета, откройте вкладку "Обзор" и выполните поиск **Microsoft.ML**.
    - Нажмите кнопку **Установить**.
    - Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.
    - Повторите эти шаги для пакетов **Microsoft.ML.ImageAnalytics**, **Microsoft.ML.OnnxTransformer** и **Microsoft.ML.OnnxRuntime**.

### <a name="prepare-your-data-and-pre-trained-model"></a>Подготовка данных и предварительно обученной модели

1. Скачайте [ZIP-файл каталога с ресурсами проекта](https://github.com/dotnet/machinelearning-samples/raw/main/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) и распакуйте его.

1. Скопируйте каталог `assets` в каталог проекта *ObjectDetection*. Этот каталог и его подкаталоги содержат файлы изображений (за исключением модели Tiny YOLOv2, которую вы скачаете и добавите на следующем шаге), необходимые для работы с этим руководством.

1. Скачайте модель [Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) из репозитория [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny-yolov2) и распакуйте.

    Введите приведенные ниже команды в окне командной строки.

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Скопируйте извлеченный файл `model.onnx` из распакованного каталога в каталог `assets\Model` проекта *ObjectDetection* и переименуйте его в `TinyYolo2_model.onnx`. Этот каталог содержит модель, необходимую для работы с этим руководством.

1. В обозревателе решений щелкните правой кнопкой мыши каждый файл в каталоге и подкаталогах ресурсов и выберите **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

### <a name="create-classes-and-define-paths"></a>Создание классов и определение путей

Добавьте следующие новые операторы `using` в начало файла *Program.cs*:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Затем определите пути к различным ресурсам.

1. Сначала добавьте метод `GetAbsolutePath` под методом `Main` в классе `Program`.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Затем внутри метода `Main` создайте поля для хранения расположения ресурсов.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Добавьте в проект новый каталог для хранения входных данных и классов прогнозов.

В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новая папка**. Когда новая папка появится в обозревателе решений, присвойте ей имя "DataStructures".

Создайте класс входных данных в только что созданном каталоге *DataStructures*.

1. В **обозревателе решений** щелкните правой кнопкой мыши папку *DataStructures* и выберите **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *ImageNetData.cs*. Теперь нажмите кнопку **Добавить**.

    Файл *ImageNetData.cs* откроется в редакторе кода. Добавьте следующую инструкцию `using` в начало файла *ImageNetData.cs*:

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Удалите существующее определение класса и добавьте следующий код для класса `ImageNetData` в файл *ImageNetData.cs*:

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData` является классом входных данных изображения и имеет следующие поля <xref:System.String>:

    - `ImagePath` содержит путь, по которому хранится изображение.
    - `Label` содержит имя файла.

    Кроме того, `ImageNetData` содержит метод `ReadFromFile`, который загружает несколько файлов изображений, хранящихся по указанном пути `imageFolder`, и возвращает их в виде коллекции объектов `ImageNetData`.

Создайте класс прогноза в каталоге структур структуры *DataStructures*.

1. В **обозревателе решений** щелкните правой кнопкой мыши папку *DataStructures* и выберите **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *ImageNetPrediction.cs*. Теперь нажмите кнопку **Добавить**.

    Файл *ImageNetPrediction.cs* откроется в редакторе кода. Добавьте следующую инструкцию `using` в начало файла *ImageNetPrediction.cs*:

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Удалите существующее определение класса и добавьте следующий код для класса `ImageNetPrediction` в файл *ImageNetPrediction.cs*:

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction` является классом прогноза данных и имеет следующее поле `float[]`:

    - `PredictedLabel` содержит измерения, оценку объекта и вероятности класса для каждого ограничивающего прямоугольника, обнаруженного в изображении.

### <a name="initialize-variables-in-main"></a>Инициализация переменных в методе Main

[Класс MLContext](xref:Microsoft.ML.MLContext) является отправной точкой для любых операций ML.NET. В результате инициализации класса `mlContext` создается среда ML.NET, которая может использоваться всеми объектами в рамках процесса создания модели. По существу он аналогичен классу `DBContext` в Entity Framework.

Инициализируйте переменную `mlContext` новым экземпляром `MLContext`, добавив следующую строку в метод `Main` в файле *Program.cs* под полем `outputFolder`.

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>Создание средства анализа для выходных данных модели после обработки

Модель разделяет изображение на сетку `13 x 13`, где каждая ячейка сетки — это `32px x 32px`. Каждая ячейка сетки содержит 5 возможных ограничивающих прямоугольников объекта. Ограничивающий прямоугольник содержит 25 элементов:

![Пример сетки слева и ограничивающего прямоугольника справа](./media/object-detection-onnx/model-output-description.png)

- `x` — координата по оси X для центра ограничивающего прямоугольника относительно ячейки сетки, с которой он связан.
- `y` — координата по оси Y для центра ограничивающего прямоугольника относительно ячейки сетки, с которой он связан.
- `w` — ширина ограничивающего прямоугольника.
- `h` — высота ограничивающего прямоугольника.
- `o` — значение достоверности того, что объект существует в пределах ограничивающего прямоугольника, также известный как оценка объекта.
- `p1-p20` — вероятности для каждого из 20 классов, прогнозируемых моделью.

В итоге 25 элементов, описывающих каждый из пяти ограничивающих прямоугольников, составляют 125 элементов, содержащихся в каждой ячейке сетки.

Выходные данные, формируемые предварительно обученной моделью ONNX, представляют собой массив длины `21125`, представляющий тензорные элементы с `125 x 13 x 13` измерениями. Чтобы преобразовать прогнозы, созданные моделью, в тензоры, необходимо выполнить некоторые действия для постобработки. Для этого создайте набор классов для упрощения анализа выходных данных.

Добавьте в проект новый каталог для упорядочения набора классов средства анализа.

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новая папка**. Когда новая папка появится в обозревателе решений, присвойте ей имя "YoloParser".

### <a name="create-bounding-boxes-and-dimensions"></a>Создание ограничивающих прямоугольников и измерений

Выходные данные модели содержат координаты и размеры ограничивающих прямоугольников объектов в изображении. Создайте базовый класс для измерений.

1. В **обозревателе решений** щелкните правой кнопкой мыши папку *YoloParser* и выберите **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *DimensionsBase.cs*. Теперь нажмите кнопку **Добавить**.

    В редакторе кода откроется файл *DimensionsBase.cs*. Удалите все инструкции `using` и существующее определение класса.

    Добавьте следующий код для класса `DimensionsBase` в файл *DimensionsBase.cs*:

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase` имеет следующие свойства `float`:

    - `X` содержит расположение объекта вдоль оси X.
    - `Y` содержит расположение объекта вдоль оси Y.
    - `Height` содержит высоту объекта.
    - `Width` содержит ширину объекта.

Затем создайте класс для ограничивающих прямоугольников.

1. В **обозревателе решений** щелкните правой кнопкой мыши папку *YoloParser* и выберите **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *YoloBoundingBox.cs*. Теперь нажмите кнопку **Добавить**.

    В редакторе кода откроется файл *YoloBoundingBox.cs*. Добавьте следующую инструкцию `using` в начало файла *YoloBoundingBox.cs*:

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Непосредственно над существующим определением класса добавьте новое определение класса с именем `BoundingBoxDimensions`, который наследует от класса `DimensionsBase`, чтобы вместить размеры соответствующего ограничивающего прямоугольника.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Удалите существующее определение класса `YoloBoundingBox` и добавьте следующий код для класса `YoloBoundingBox` в файл *YoloBoundingBox.cs*:

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox` имеет следующие свойства:

    - `Dimensions` содержит размеры ограничивающего прямоугольника.
    - `Label` содержит класс объекта, обнаруженного в ограничивающем прямоугольнике.
    - `Confidence` содержит достоверность класса.
    - `Rect` содержит прямоугольное представление измерений ограничивающего прямоугольника.
    - `BoxColor` содержит цвет, связанный с соответствующим классом, который используется для рисования изображения.

### <a name="create-the-parser"></a>Создание средства анализа

Теперь, когда созданы классы для измерений и ограничивающих прямоугольников, пришло время создать средство анализа.

1. В **обозревателе решений** щелкните правой кнопкой мыши папку *YoloParser* и выберите **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *YoloOutputParser.cs*. Теперь нажмите кнопку **Добавить**.

    В редакторе кода откроется файл *YoloOutputParser.cs*. Добавьте следующую инструкцию `using` в начало файла *YoloOutputParser.cs*:

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    В существующем определении класса `YoloOutputParser` добавьте вложенный класс, который содержит размеры каждой ячейки в изображении. Добавьте следующий код для класса `CellDimensions`, который наследуется от класса `DimensionsBase`, в верхней части определения класса `YoloOutputParser`.

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. Добавьте в определение класса `YoloOutputParser` следующие константы и поля.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT` задает число строк в сетке, на которые делится изображение.
    - `COL_COUNT` задает число столбцов в сетке, на которые делится изображение.
    - `CHANNEL_COUNT` задает общее число значений, содержащихся в одной ячейке сетки.
    - `BOXES_PER_CELL` задает число ограничивающих прямоугольников в ячейке.
    - `BOX_INFO_FEATURE_COUNT` — число компонентов, содержащихся в поле (X, Y, высота, ширина, достоверность).
    - `CLASS_COUNT` — число прогнозов класса, содержащихся в каждом ограничивающем прямоугольнике.
    - `CELL_WIDTH` — ширина одной ячейки в сетке изображения.
    - `CELL_HEIGHT` — высота одной ячейки в сетке изображения.
    - `channelStride` — начальная координата текущей ячейки в сетке.

    Когда модель выполняет прогноз, также известный как оценка, она делит входной образ `416px x 416px` на сетку ячеек размером `13 x 13`. Каждая ячейка содержит `32px x 32px`. В каждой ячейке есть пять ограничивающих прямоугольников, каждый из которых содержит пять компонентов (X, Y, ширина, высота, достоверность). Кроме того, каждый ограничивающий прямоугольник содержит вероятность каждого из классов, которых в данном случае насчитывается 20. Таким образом, каждая ячейка содержит 125 элементов данных (пять функций + 20 вероятностей классов).

Создайте список привязок ниже `channelStride` для всех пяти ограничивающих прямоугольников:

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Привязки — это предварительно определенные коэффициенты высоты и ширины ограничивающих прямоугольников. Большинство объектов или классов, обнаруживаемых моделью, имеют схожие коэффициенты. Это полезно, когда дело доходит до создания ограничивающих прямоугольников. Вместо прогнозирования ограничивающих прямоугольников вычисляется смещение от предварительно определенных измерений, что сокращает число вычислений, необходимое для прогнозирования ограничивающего прямоугольника. Обычно эти коэффициенты привязки вычисляются на основе используемого набора данных. В этом случае, поскольку набор данных известен и значения предварительно вычислены, привязки могут быть жестко запрограммированы.

Затем определите метки или классы, которые будет прогнозировать модель. Эта модель прогнозирует 20 классов, которые являются подмножеством общего числа классов, прогнозируемых исходной моделью YOLOv2.

Добавьте список меток под `anchors`.

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

С каждым из классов связаны цвета. Назначьте цвета классов под `labels`:

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Создание вспомогательных функций

Этап постобработки включает ряд действий. Для этого можно применять несколько вспомогательных методов.

Средство анализа использует следующие вспомогательные методы:

- `Sigmoid` применяет функцию-сигмоиду, которая выводит число от 0 до 1.
- `Softmax` нормализует входной вектор в распределение вероятности.
- `GetOffset` сопоставляет элементы в выходных данных одномерной модели с соответствующей позицией в тензоре `125 x 13 x 13`.
- `ExtractBoundingBoxes` извлекает измерения ограничивающего прямоугольника с помощью метода `GetOffset` из выходных данных модели.
- `GetConfidence` извлекает значение достоверности того, что модель обнаружила объект, и использует функцию `Sigmoid`, чтобы преобразовать ее в процент.
- `MapBoundingBoxToCell` использует измерения ограничивающего прямоугольника и сопоставляет их с соответствующей ячейкой на изображении.
- `ExtractClasses` извлекает прогнозы класса для ограничивающего прямоугольника из выходных данных модели с помощью метода `GetOffset` и превращает их в распределение вероятности с помощью метода `Softmax`.
- `GetTopResult` выбирает из списка прогнозируемых классов класс с наибольшей вероятностью.
- `IntersectionOverUnion` фильтрует перекрывающиеся ограничивающие прямоугольники с более низкими вероятностями.

Добавьте код для всех вспомогательных методов под списком `classColors`.

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Определив все вспомогательные методы, можно использовать их для обработки выходных данных модели.

Под методом `IntersectionOverUnion` создайте метод `ParseOutputs` для обработки выходных данных, создаваемых моделью.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Создайте список для хранения ограничивающих прямоугольников и определите переменные внутри метода `ParseOutputs`.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Каждое изображение делится на сетку из ячеек `13 x 13`. Каждая ячейка содержит пять ограничивающих прямоугольников. Под переменной `boxes` добавьте код для обработки всех полей в каждой ячейке.

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

Внутри самого глубокого цикла вычислите начальную точку текущего поля в выходных данных одномерной модели.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Непосредственно под этим используйте метод `ExtractBoundingBoxDimensions`, чтобы получить размеры текущего ограничивающего прямоугольника.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Затем используйте метод `GetConfidence`, чтобы получить достоверность для текущего ограничивающего прямоугольника.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

После этого используйте метод `MapBoundingBoxToCell`, чтобы связать текущий ограничивающий прямоугольник с текущей обрабатываемой ячейкой.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Прежде чем выполнять дальнейшую обработку, проверьте, больше ли значение достоверности, чем предоставленный порог. Если нет, обработайте следующий ограничивающий прямоугольник.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

В противном случае продолжите обработку выходных данных. Следующим шагом является получение вероятности распределения прогнозируемых классов для текущего ограничивающего прямоугольника с помощью метода `ExtractClasses`.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Затем используйте метод `GetTopResult`, чтобы получить значение и индекс класса с наибольшей вероятностью для текущего поля и вычислить его оценку.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

Используйте `topScore`, чтобы снова оставить только ограничивающие прямоугольники выше указанного порогового значения.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Наконец, если текущий ограничивающий прямоугольник превышает пороговое значение, создайте новый объект `BoundingBox` и добавьте его в список `boxes`.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

После обработки всех ячеек в изображении возвратите список `boxes`. Добавьте следующий оператор return под внешним циклом for в методе `ParseOutputs`.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Фильтрация перекрывающихся полей

Теперь, когда все надежные ограничивающие прямоугольники были извлечены из выходных данных модели, для удаления перекрывающихся изображений необходимо провести дополнительную фильтрацию. Добавьте метод `FilterBoundingBoxes` под методом `ParseOutputs`:

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

В методе `FilterBoundingBoxes` начните с создания массива, который равен размеру обнаруженных полей, помечая все слоты как активные или готовые к обработке.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Затем отсортируйте список, содержащий ограничивающие прямоугольники, в порядке убывания.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

После этого создайте список для хранения отфильтрованных результатов.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Приступите к обработке каждого ограничивающего прямоугольника путем прохода по всем ограничивающим прямоугольникам.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Внутри этого цикла for проверьте, может ли быть обработан текущий ограничивающий прямоугольник.

```csharp
if (isActiveBoxes[i])
{

}
```

Если это так, добавьте ограничивающий прямоугольник в список результатов. Если результаты больше указанного предельного числа полей для извлечения, следует выйти из цикла. Добавьте следующий код в оператор if.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

В противном случае просмотрите соседние ограничивающие прямоугольники. Добавьте следующий код после проверки предела ограничений.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

Как и с первым полем, если смежное поле активно или готово к обработке, используйте метод `IntersectionOverUnion`, чтобы проверить, превышают ли первое и второе поля указанное пороговое значение. Добавьте следующий код в самый глубокий внутренний цикл for.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

За пределами внутреннего цикла for, который проверяет смежные ограничивающие прямоугольники, можно узнать, остались ли для обработки ограничивающие прямоугольники. В противном случае прервите внешний цикл for.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Наконец, за пределами начального цикла for метода `FilterBoundingBoxes` следует вернуть результаты:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Отлично. Теперь пришло время использовать этот код вместе с моделью для оценки.

## <a name="use-the-model-for-scoring"></a>Использование модели для оценки

Как и в случае с постобработкой, оценка проводится в несколько шагов. Чтобы помочь в этом, добавьте класс, который будет содержать логику оценки для проекта.

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *OnnxModelScorer.cs*. Теперь нажмите кнопку **Добавить**.

    Файл *OnnxModelScorer.cs* откроется в редакторе кода. Добавьте следующую инструкцию `using` в начало файла *OnnxModelScorer.cs*:

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    Добавьте в определение класса `OnnxModelScorer` следующие переменные:

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Непосредственно под ними создайте конструктор для класса `OnnxModelScorer`, который будет инициализировать ранее определенные переменные.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    После создания конструктора определите пару структур, содержащих переменные, связанные с изображением и параметрами модели. Создайте структуру с именем `ImageNetSettings`, которая будет содержать высоту и ширину, ожидаемые в качестве входных данных для модели.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    После этого создайте другую структуру с именем `TinyYoloModelSettings`, которая содержит имена входных и выходных слоев модели. Чтобы визуализировать имя входного и выходного слоев модели, можно использовать такой инструмент, как [Netron](https://github.com/lutzroeder/netron).

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Затем создайте первый набор методов, используемый для оценки. Создайте метод `LoadModel` внутри класса `OnnxModelScorer`.

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    Добавьте следующий код журнала в метод `LoadModel`.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    Конвейеры ML.NET обычно должны знать схему данных для работы при вызове метода [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit%2A). В этом случае будет использоваться процесс, аналогичный обучению. Однако, поскольку фактического обучения не происходит, допустимо использовать пустое значение [`IDataView`](xref:Microsoft.ML.IDataView). Создайте новый [`IDataView`](xref:Microsoft.ML.IDataView) для конвейера из пустого списка.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Ниже определите конвейер. Конвейер будет состоять из четырех преобразований.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages%2A) загружает изображение в виде точечного рисунка.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages%2A) изменяет масштаб изображения до указанного размера (в данном случае `416 x 416`).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels%2A) изменяет пиксельное представление изображения с точечного рисунка на числовой вектор.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel%2A) загружает модель ONNX и использует ее для оценки предоставленных данных.

    Определите конвейер в методе `LoadModel` под переменной `data`.

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Пришло время создать экземпляр модели для оценки. Вызовите метод [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit%2A) в конвейере и верните его результат для дальнейшей обработки.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

После загрузки модели ее можно использовать для создания прогнозов. Чтобы упростить этот процесс, создайте метод `PredictDataUsingModel` под методом `LoadModel`.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

Добавьте следующий код журнала в `PredictDataUsingModel`.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Затем используйте метод [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) для оценки данных.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Извлеките прогнозируемые вероятности и верните их для дополнительной обработки.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Теперь, когда оба шага настроены, объедините их в один метод. Добавьте новый метод `Score` под методом `PredictDataUsingModel`:

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Почти готово! Теперь пора все это использовать.

## <a name="detect-objects"></a>Обнаружение объектов

Теперь, когда все настройки завершены, пришло время обнаружить объекты. Начните с добавления ссылок на средство оценки и средство синтаксического анализа в классе *Program.cs*.

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Выходные данные модели оценки и синтаксического анализа

В методе `Main` класса *Program.cs* добавьте оператор try-catch.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

В блоке `try` начните реализовывать логику обнаружения объектов. Сначала загрузите данные в [`IDataView`](xref:Microsoft.ML.IDataView).

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Затем создайте экземпляр `OnnxModelScorer` и используйте его для оценки загруженных данных.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Теперь пора выполнить шаг постобработки. Создайте экземпляр `YoloOutputParser` и используйте его для обработки выходных данных модели.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

После обработки выходных данных модели настало время рисования ограничивающих прямоугольников на изображениях.

### <a name="visualize-predictions"></a>Визуализация прогнозов

После того как модель оценила изображения и обработала выходные данные, на изображении появятся ограничивающие прямоугольники. Для этого добавьте метод `DrawBoundingBox` под методом `GetAbsolutePath` в *Program.cs*.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

Сначала загрузите изображение и получите измерения Height и Width в методе `DrawBoundingBox`.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Затем создайте цикл for-each для прохода по каждому ограничивающему прямоугольнику, обнаруженному моделью.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

В цикле for-each получите размеры ограничивающего прямоугольника.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Поскольку размеры ограничивающего прямоугольника соответствуют входным данным модели `416 x 416`, масштабируйте размеры ограничивающего прямоугольника в соответствии с фактическим размером изображения.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Затем определите шаблон для текста, который будет отображаться над каждым ограничивающим прямоугольником. Текст будет содержать класс объекта внутри соответствующего ограничивающего прямоугольника, а также его достоверность.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Чтобы нарисовать что-то на изображении, преобразуйте его в объект [`Graphics`](xref:System.Drawing.Graphics).

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

Внутри блока кода `using` настройте параметры графического объекта [`Graphics`](xref:System.Drawing.Graphics).

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Ниже задайте параметры шрифта и цвета для текста и ограничивающего прямоугольника.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

Создайте и заполните прямоугольник над ограничивающей рамкой, которая будет содержать текст, с помощью метода [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle%2A). Это поможет выделить текст и улучшить удобочитаемость.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Затем нарисуйте текст и ограничивающий прямоугольник на изображении с помощью методов [`DrawString`](xref:System.Drawing.Graphics.DrawString%2A) и [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle%2A).

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

За пределами цикла for-each добавьте код для сохранения изображений в `outputDirectory`.

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Чтобы получить дополнительные данные о том, что приложение делает ожидаемые прогнозы во время выполнения, добавьте метод `LogDetectedObjects` под методом `DrawBoundingBox` в файле *Program.cs* для вывода обнаруженных объектов на консоль.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Теперь, когда у вас есть вспомогательные методы для создания визуальной обратной связи из прогнозов, добавьте цикл for для итерации по каждому из оцененных изображений.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

В цикле for получите имя файла изображения и связанных с ним ограничивающих прямоугольников.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Ниже используйте метод `DrawBoundingBox` для рисования ограничивающих прямоугольников на изображении.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Наконец, используйте метод `LogDetectedObjects` для вывода прогнозов на консоль.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

После оператора try-catch добавьте дополнительную логику, чтобы указать, что процесс завершен.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

Вот и все!

## <a name="results"></a>Результаты

Выполнив предыдущие шаги, запустите консольное приложение (CTRL+F5). Результаты выполнения должны выглядеть примерно так, как указано ниже. Кроме того, могут выводиться предупреждения или сообщения об обработке, но для удобства здесь мы убрали их.

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

Чтобы просмотреть изображения с ограничивающими рамками, перейдите в каталог `assets/images/output/`. Ниже приведен пример одного из обработанных изображений.

![Пример обработанного изображения столовой](./media/object-detection-onnx/dinning-room-table-chairs.png)

Поздравляем! Вы успешно создали модель машинного обучения для обнаружения объектов на основе предварительно обученной модели `ONNX` в ML.NET.

Исходный код для этого руководства можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx).

В этом руководстве вы узнали, как:
> [!div class="checklist"]
>
> - Определение проблемы
> - Узнайте, что такое ONNX и как он работает с ML.NET
> - Общие сведения о модели
> - Повторное использование предварительно обученной модели
> - Обнаружение объектов в загруженной модели

Ознакомьтесь с примерами машинного обучения в репозитории GitHub, чтобы подробнее изучить расширенный пример обнаружения объектов.
> [!div class="nextstepaction"]
> [Репозиторий GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
