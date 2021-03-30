---
title: Учебник. Классификация цветов ириса — кластеризация k-средних
description: Сведения об использовании ML.NET при кластеризации
author: pkulikov
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 9240f365c6721baae03d8537e5e71153abf0f172
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875607"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Учебник. Категоризация цветов ириса с использованием кластеризации k-средних в ML.NET

В этом руководстве описано, как с помощью ML.NET создать [модель кластеризации](../resources/tasks.md#clustering) для [набора данных ирисов](https://en.wikipedia.org/wiki/Iris_flower_data_set).

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
>
> - Определение проблемы
> - Выбор подходящей задачи машинного обучения
> - Подготовка данных
> - Загрузка и преобразование данных
> - Выбор алгоритма обучения
> - Обучение модели
> - Использование модели для прогнозирования

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленной рабочей нагрузкой "Кроссплатформенная разработка .NET Core".

## <a name="understand-the-problem"></a>Определение проблемы

Задача — разделить ирисы на группы в зависимости от признаков цветка. Эти признаки — длина и ширина чашелистика и длина и ширина лепестка. В этом руководстве предполагается, что тип каждого цветка неизвестен. Вы научитесь структурировать набор данных по признакам и предсказывать, как экземпляр данных будет вписываться в эту структуру.

## <a name="select-the-appropriate-machine-learning-task"></a>Выбор подходящей задачи машинного обучения

Поскольку вы не знаете, к какой группе принадлежит каждый цветок, вы выбираете задачу [неконтролируемого машинного обучения](../resources/glossary.md#unsupervised-machine-learning). Чтобы разделить набор данных на группы таким образом, чтобы элементы одной группы больше походили друг на друга, чем на элементы из других групп, используйте задачу машинного обучения по [кластеризации](../resources/tasks.md#clustering).

## <a name="create-a-console-application"></a>Создание консольного приложения

1. Запустите Visual Studio. Выберите **Файл** > **Создать** > **Проект** в меню. В диалоговом окне **Новый проект** выберите узел **Visual C#** , а затем — узел **.NET Core**. Выберите шаблон проекта **Консольное приложение (.NET Core)** . В текстовом поле **Имя** введите "IrisFlowerClustering", а затем нажмите кнопку **OK**.

1. Создайте каталог с именем *Data* в папке проекта, чтобы хранить в нем наборы данных и файлы модели:

    В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новая папка**. Введите имя папки Data и нажмите клавишу "ВВОД".

1. Установите пакет NuGet для **Microsoft.ML**:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакета, откройте вкладку **Обзор**, выполните поиск по запросу **Microsoft.ML** и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.

## <a name="prepare-the-data"></a>Подготовка данных

1. Скачайте набор данных [iris.data](https://github.com/dotnet/machinelearning/blob/main/test/data/iris.data) и сохраните его в папке *Data*, созданной на предыдущем шаге. Дополнительные сведения о наборе данных ирисов см. на странице Википедии [Ирисы Фишера](https://en.wikipedia.org/wiki/Iris_flower_data_set) и на странице [Набор данных ирисов](http://archive.ics.uci.edu/ml/datasets/Iris), который является источником набора данных.

1. В **Обозревателе решений** щелкните правой кнопкой мыши файл *iris.data* и выберите **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

Файл *Iris.data* содержит пять столбцов со следующими данными:

- длина чашелистика в сантиметрах;
- ширина чашелистика в сантиметрах;
- длина лепестка в сантиметрах;
- ширина лепестка в сантиметрах;
- тип ириса.

В этом примере кластеризации мы не будем учитывать последний столбец.

## <a name="create-data-classes"></a>Создание классов данных

Создайте классы для входных данных и прогнозов:

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *IrisData.cs*. Теперь нажмите кнопку **Добавить**.
1. Добавьте следующую директиву `using` в новый файл:

   [!code-csharp[Add necessary usings](./snippets/iris-clustering/csharp/IrisData.cs#Usings)]

Удалите из файла *IrisData.cs* существующее определение класса и добавьте следующий код, который определяет классы `IrisData` и `ClusterPrediction`:

[!code-csharp[Define data classes](./snippets/iris-clustering/csharp/IrisData.cs#ClassDefinitions)]

Класс `IrisData` содержит входные данные и определения для каждого признака в наборе данных. Используйте атрибут [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute), чтобы указать индексы исходных столбцов в файле набора данных.

Класс `ClusterPrediction` представляет выходные данные модели кластеризации, примененные к экземпляру `IrisData`. Используйте атрибут [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute), чтобы привязать поля `PredictedClusterId` и `Distances` к столбцам **PredictedLabel** и **Score** соответственно. В случае задачи кластеризации эти столбцы означают следующее:

- Столбец **PredictedLabel** содержит идентификатор прогнозируемого кластера.
- Столбец **Score** содержит массив с квадратом Евклидовых расстояний до центроидов кластера. Длина массива равна числу кластеров.

> [!NOTE]
> Используйте тип `float` для представления значений с плавающей запятой в классах данных ввода и прогнозирования.

## <a name="define-data-and-model-paths"></a>Определение путей к данным и модели

Вернитесь к файлу *Program.cs* и добавьте два поля, которые будут содержать пути к файлу с наборами данных и к файлу для сохранения модели.

- `_dataPath` содержит путь к файлу с набором данных, используемым для обучения модели.
- `_modelPath` содержит путь к файлу для сохранения обучаемой модели.

Добавьте прямо перед методом `Main` следующий код, чтобы указать эти пути.

[!code-csharp[Initialize paths](./snippets/iris-clustering/csharp/Program.cs#Paths)]

Чтобы этот код компилировался, добавьте следующие директивы `using` вверху файла *Program.cs*.

[!code-csharp[Add usings for paths](./snippets/iris-clustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Создание контекста машинного обучения ML

Добавьте дополнительные директивы `using` в начало файла *Program.cs*.

[!code-csharp[Add Microsoft.ML usings](./snippets/iris-clustering/csharp/Program.cs#MLUsings)]

В методе `Main` замените строку `Console.WriteLine("Hello World!");` следующим кодом:

[!code-csharp[Create ML context](./snippets/iris-clustering/csharp/Program.cs#CreateContext)]

Класс <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> представляет среду машинного обучения и предоставляет механизмы для ведения журнала и точек входа для загрузки данных, обучения модели, прогнозирования и других задач. Концептуально это сопоставимо с использованием `DbContext` в Entity Framework.

## <a name="set-up-data-loading"></a>Настройка загрузки данных

Добавьте следующий код к методу `Main`, чтобы настроить способ загрузки данных:

[!code-csharp[Create text loader](./snippets/iris-clustering/csharp/Program.cs#CreateDataView)]

Универсальный [метод расширения `MLContext.Data.LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) выводит схему набора данных на основе предоставленного типа `IrisData` и возвращает интерфейс <xref:Microsoft.ML.IDataView>, который можно использовать в качестве входных данных для преобразования.

## <a name="create-a-learning-pipeline"></a>Создание конвейера обучения

В этом руководстве настройка конвейера обучения задач кластеризации состоит из следующих двух шагов:

- объедините загруженные столбцы в один столбец **Функции**, который используется тренером кластеризации;
- используйте тренер <xref:Microsoft.ML.Trainers.KMeansTrainer> для обучения модели с помощью алгоритма кластеризации k-means++.

Добавьте следующий код в метод `Main`:

[!code-csharp[Create pipeline](./snippets/iris-clustering/csharp/Program.cs#CreatePipeline)]

В этом коде указано, что набор данных нужно разделить на три кластера.

## <a name="train-the-model"></a>Обучение модели

Выполнив действия в предыдущих разделах, вы подготовили конвейер для обучения, но пока ничего не было сделано. Добавьте следующую строку к методу `Main`, чтобы выполнить загрузку данных и обучение модели:

[!code-csharp[Train the model](./snippets/iris-clustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Сохранение модели

На этом этапе у вас есть модель, которую можно интегрировать с любыми существующими или новыми приложениями .NET. Чтобы сохранить модель в ZIP-файл, добавьте к методу `Main` следующий код:

[!code-csharp[Save the model](./snippets/iris-clustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Использование модели для прогнозирования

Чтобы получить прогноз, используйте класс <xref:Microsoft.ML.PredictionEngine%602>, который принимает экземпляры входного типа через конвейер преобразователя и создает экземпляры выходного типа. Добавьте следующую строку к методу `Main` для создания экземпляра этого класса:

[!code-csharp[Create predictor](./snippets/iris-clustering/csharp/Program.cs#Predictor)]

Класс [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) представляет собой удобный API, позволяющий осуществить прогнозирование на основе единственного экземпляра данных. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным. Допустимо использовать в средах прототипов или средах с одним потоком. Для улучшенной производительности и потокобезопасности в рабочей среде используйте службу `PredictionEnginePool`, которая создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении. См. руководство по [использованию `PredictionEnginePool` в веб-API ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> Расширение службы `PredictionEnginePool` сейчас доступно в предварительной версии.

Создание класса `TestIrisData` для размещения тестовых экземпляров данных:

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *TestIrisData.cs*. Теперь нажмите кнопку **Добавить**.
1. Измените класс, чтобы он был статическим, как показано в следующем примере:

   [!code-csharp[Make class static](./snippets/iris-clustering/csharp/TestIrisData.cs#Static)]

В этом руководстве представлен один экземпляр данных ирисов в этом классе. Вы можете добавить другие сценарии и поэкспериментировать с этой моделью. Добавьте в класс `TestIrisData` следующий код:

[!code-csharp[Test data](./snippets/iris-clustering/csharp/TestIrisData.cs#TestData)]

Чтобы узнать, к какому кластеру принадлежит указанный элемент, вернитесь к файлу *Program.cs* и добавьте следующий код в метод `Main`:

[!code-csharp[Predict and output results](./snippets/iris-clustering/csharp/Program.cs#PredictionExample)]

Запустите программу, чтобы узнать, какой кластер содержит указанный экземпляр данных и квадрат расстояния от этого экземпляра до центроидов кластера. Результаты выполнения должны выглядеть примерно так:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Поздравляем! Вы успешно создали модель машинного обучения для кластеризации ирисов и использовали ее для прогнозирования. Исходный код для этого руководства можно найти в репозитории GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/IrisFlowerClustering).

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как:
> [!div class="checklist"]
>
> - Определение проблемы
> - Выбор подходящей задачи машинного обучения
> - Подготовка данных
> - Загрузка и преобразование данных
> - Выбор алгоритма обучения
> - Обучение модели
> - Использование модели для прогнозирования

Извлеките наш репозиторий GitHub, чтобы продолжить обучение и получить дополнительные примеры.
> [!div class="nextstepaction"]
> [Репозиторий GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/)
