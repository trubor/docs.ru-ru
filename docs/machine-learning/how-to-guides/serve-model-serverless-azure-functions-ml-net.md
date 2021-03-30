---
title: Развертывание модели в Функциях Azure
description: Использование модели машинного обучения ML.NET для анализа тональности и прогнозирования через Интернет с помощью Функций Azure
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 90b52aa295e224eb3744d2576b9a146e4e90dced
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875893"
---
# <a name="deploy-a-model-to-azure-functions"></a>Развертывание модели в Функциях Azure

Сведения о развертывании предварительно обученной модели машинного обучения ML.NET для создания прогнозов по протоколу HTTP через бессерверную среду Функций Azure.

> [!NOTE]
> В этом примере запускается предварительная версия службы `PredictionEnginePool`.

## <a name="prerequisites"></a>Предварительные требования

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или более поздняя версия либо Visual Studio 2017 версии 15.6 или более поздняя версия с установленными рабочими нагрузками "Кроссплатформенная разработка .NET Core" и "Разработка для Azure".
- [Средства Функций Azure](/azure/azure-functions/functions-develop-vs#check-your-tools-version).
- PowerShell
- Предварительно обученная модель. Используйте [учебник по анализу тональности ML.NET](../tutorials/sentiment-analysis.md), чтобы создать собственную модель, или скачайте эту [предварительно обученную модель машинного обучения для анализа тональности](https://github.com/dotnet/samples/blob/main/machine-learning/models/sentimentanalysis/sentiment_model.zip)

## <a name="azure-functions-sample-overview"></a>Обзор примера для Функций Azure

В этом примере предоставляется приложение **триггера HTTP на языке C# для Функций Azure**, которое использует предварительно обученную модель двоичной классификации для выбора положительной или отрицательной тональности текста. Функции Azure предоставляют простой способ выполнять небольшие фрагменты кода в большом масштабе для управляемой бессерверной облачной среды. Код для этого примера можно найти в репозитории [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) на сайте GitHub.

## <a name="create-azure-functions-project"></a>Создание проекта в Функциях Azure

1. Откройте Visual Studio 2017. Выберите **Файл** > **Создать** > **Проект** в меню. В диалоговом окне **Новый проект** щелкните узел **Visual C#** , а затем — **Облако**. Выберите шаблон проекта **Функции Azure**. В текстовое поле **Имя** введите SentimentAnalysisFunctionsApp и нажмите кнопку **ОК**.
1. В диалоговом окне **Новый проект** откройте раскрывающийся список над разделом с параметрами проекта и выберите **Функции Azure v2 (.NET Core)** . Затем щелкните проект **Триггер HTTP** и нажмите кнопку **OK**.
1. Создайте каталог с именем *MLModels* в папке проекта, чтобы сохранить модель:

    В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите **Добавить** > **Новая папка**. Введите MLModels и нажмите клавишу ВВОД.

1. Установите **пакет NuGet для Microsoft.ML** версии **1.3.1**.

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.ML**, выберите из списка этот пакет и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.

1. Установите **пакет NuGet Microsoft.Azure.Functions.Extensions**:

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.Azure.Functions.Extensions**, выберите из списка этот пакет и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.

1. Установите **пакет NuGet Microsoft.Extensions.ML** версии **0.15.1**:

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Обзор", выполните поиск по фразе **Microsoft.Extensions.ML**, выберите из списка этот пакет и нажмите кнопку **Установить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.

1. Установите **пакет NuGet Microsoft.NET.Sdk.Functions** версии **1.0.31**:

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Управление пакетами NuGet**. Выберите nuget.org в качестве источника пакетов, перейдите на вкладку "Установленные", выполните поиск по фразе **Microsoft.NET.Sdk.Functions**, выберите из списка этот пакет, выберите в раскрывающемся списке "Версия" значение **1.0.31**, а затем нажмите кнопку **Обновить**. Нажмите кнопку **ОК** в диалоговом окне **Предварительный просмотр изменений**, а затем нажмите кнопку **Принимаю** в диалоговом окне **Принятие условий лицензионного соглашения**, если вы согласны с указанными условиями лицензионного соглашения для выбранных пакетов.

## <a name="add-pre-trained-model-to-project"></a>Добавление предварительно обученной модели в проект

1. Скопируйте предварительно созданную модель в папку *MLModels*.
1. В обозревателе решений щелкните правой кнопкой мыши файл предварительно созданной модели и выберите **Свойства**. В разделе **Дополнительно** для параметра **Копировать в выходной каталог** установите значение **Копировать более позднюю версию**.

## <a name="create-azure-function-to-analyze-sentiment"></a>Создание функции Azure для анализа тональности

Создайте класс для прогнозирования тональности. Добавьте в проект новый класс:

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.

1. В диалоговом окне **Добавление нового элемента** выберите **Функция Azure** и измените значение поля **Имя** на *AnalyzeSentiment.cs*. Теперь нажмите кнопку **Добавить**.

1. В диалоговом окне **Новая функция Azure** щелкните **Триггер HTTP**. Затем нажмите кнопку **OK**.

    В редакторе кода откроется файл *AnalyzeSentiment.cs*. Добавьте следующий оператор `using` в начало файла *AnalyzeSentiment.cs*.

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    По умолчанию класс `AnalyzeSentiment` — `static`. Удалите ключевое слово `static` из объявления класса.

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a>Создание моделей данных

Вам потребуется создать несколько классов для входных данных и прогнозов. Добавьте в проект новый класс:

1. Создайте каталог с именем *DataModels* в папке проекта, чтобы сохранить в нем модели данных: В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Добавить > Новая папка**. Введите DataModels и нажмите клавишу ВВОД.
2. В обозревателе решений щелкните правой кнопкой мыши папку *DataModels* и выберите **Добавить > Новый элемент**.
3. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentData.cs*. Теперь нажмите кнопку **Добавить**.

    Файл *SentimentData.cs* откроется в редакторе кода. Добавьте в начало файла *SentimentData.cs* следующий оператор using:

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    Удалите из файла *SentimentData.cs* существующее определение класса и добавьте следующий код:

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. В обозревателе решений щелкните правой кнопкой мыши папку *DataModels* и выберите **Добавить > Новый элемент**.
5. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *SentimentPrediction.cs*. Теперь нажмите кнопку **Добавить**. В редакторе кода откроется файл *SentimentPrediction.cs*. Добавьте в начало файла *SentimentPrediction.cs* следующий оператор using:

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    Удалите из файла *SentimentPrediction.cs* существующее определение класса и добавьте следующий код:

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    `SentimentPrediction` наследует от `SentimentData`, который обеспечивает доступ к исходным данным в свойстве `SentimentText`, а также выходным данным модели.

## <a name="register-predictionenginepool-service"></a>Регистрация службы PredictionEnginePool

Для формирования одного прогноза необходимо создать [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602). [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) не является потокобезопасным. Кроме того, необходимо создать его экземпляр везде, где он понадобится в вашем приложении. По мере увеличения размера приложения этот процесс может стать неуправляемым. Для улучшенной производительности и потокобезопасности используйте сочетание внедрения зависимостей и службы `PredictionEnginePool`, которое создает [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) объектов [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) для использования во всем приложении.

См. дополнительные сведения о [внедрении зависимостей](https://en.wikipedia.org/wiki/Dependency_injection) по следующей ссылке.

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункты **Добавить** > **Новый элемент**.
1. В диалоговом окне **Добавление нового элемента** выберите **Класс** и измените значение поля **Имя** на *Startup.cs*. Теперь нажмите кнопку **Добавить**.
1. Добавьте в начало файла *Startup.cs* следующие операторы using:

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. Удалите существующий код ниже инструкций using и добавьте следующий код:

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. Определите в классе `Startup` переменные для хранения среды, в которой выполняется приложение, и путь к файлу, в котором находится модель.

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. Ниже показано, как создать конструктор для задания значений переменных `_environment` и `_modelPath`. При локальном запуске приложения средой по умолчанию считается среда *Development* (Разработка).

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. Затем добавьте под конструктором новый метод с именем `Configure`, который будет регистрировать службу `PredictionEnginePool`.

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

Вкратце, этот код инициализирует объекты и службы автоматически для использования в дальнейшем по запросу приложения, вместо того чтобы вы делали это вручную.

Модели машинного обучения не являются статическими. По мере появления новых данных для обучения модель переобучается и развертывается повторно. Одним из способов получения последней версии модели в приложении является повторное развертывание всего приложения. Однако это приводит к простою приложения. Служба `PredictionEnginePool` предоставляет механизм перезагрузки обновленной модели без отключения приложения.

Задайте для параметра `watchForChanges` значение `true`. В таком случае `PredictionEnginePool` запустит объект [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher), который прослушивает уведомления об изменениях файловой системы и вызывает события при изменении файла. При наличии изменений `PredictionEnginePool` автоматически перезагружает модель.

Модель определяется параметром `modelName`, поэтому при изменении может быть перезагружено несколько моделей на одно приложение.

> [!TIP]
> Кроме того, можно использовать метод `FromUri` при работе с моделями, сохраненными удаленно. Вместо наблюдения за событиями изменения файлов `FromUri` опрашивает удаленное расположение на предмет изменений. Интервал опроса по умолчанию равен 5 минутам. Вы можете увеличить или уменьшить интервал опроса в зависимости от требований вашего приложения. В приведенном ниже примере кода `PredictionEnginePool` опрашивает модель, сохраненную по указанному универсальному коду ресурса (URI), каждую минуту.
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/main/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a>Загрузка модели в функцию

Вставьте следующий код внутри класса *AnalyzeSentiment*:

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

Этот код назначает `PredictionEnginePool`, передав его в конструктор функции, который можно получить путем внедрения зависимостей.

## <a name="use-the-model-to-make-predictions"></a>Использование модели для прогнозирования

Замените существующую реализацию метода *запуска* в классе *AnalyzeSentiment* следующим кодом:

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

Когда метод `Run` выполняется, входящие данные из HTTP-запроса десериализуются и используются в качестве входных данных для `PredictionEnginePool`. Затем метод `Predict` вызывается для формирования прогнозов с использованием модели `SentimentAnalysisModel`, зарегистрированной в классе `Startup`, и возвращает результаты пользователю в случае успеха.

## <a name="test-locally"></a>Локальное тестирование

Завершив настройку параметров, протестируйте приложение:

1. Запуск приложения
1. Откройте PowerShell и введите код в командной строке, где PORT — это порт, через который работает приложение. Как правило, используется порт 7071.

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    В случае успешного выполнения результат должен выглядеть, как показано ниже:

    ```powershell
    Negative
    ```

Поздравляем! Вы успешно использовали модель для прогнозирования через Интернет с помощью Функций Azure.

## <a name="next-steps"></a>Следующие шаги

- [Развертывание в Azure](/azure/azure-functions/functions-develop-vs#publish-to-azure)
