---
title: Использование записных книжек Jupyter
titleSuffix: .NET for Apache Spark
description: Использование .NET для Apache Spark в интерактивных средах, таких как Jupyter Notebook, Jupyter Lab или Visual Studio Code (VS Code)
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: 9c0e713731b5e2ad742bdd257a99f9029f244363
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536116"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a><span data-ttu-id="2432e-103">Использование .NET для Apache Spark в записных книжках Jupyter</span><span class="sxs-lookup"><span data-stu-id="2432e-103">Use .NET for Apache Spark in Jupyter Notebooks</span></span>

<span data-ttu-id="2432e-104">Из этой статьи вы узнаете, как запускать задания .NET для Apache Spark в интерактивном режиме в Jupyter Notebook и Visual Studio Code (VS Code) с помощью .NET Interactive.</span><span class="sxs-lookup"><span data-stu-id="2432e-104">In this article, you learn how to run .NET for Apache Spark jobs interactively in Jupyter Notebook and Visual Studio Code (VS Code) with .NET Interactive.</span></span>

## <a name="about-jupyter"></a><span data-ttu-id="2432e-105">Сведения о Jupyter</span><span class="sxs-lookup"><span data-stu-id="2432e-105">About Jupyter</span></span>

<span data-ttu-id="2432e-106">[Jupyter](https://jupyter.org/) — это кроссплатформенная вычислительная среда с открытым исходным кодом, которая позволяет пользователям создавать прототипы и разрабатывать приложения в интерактивном режиме.</span><span class="sxs-lookup"><span data-stu-id="2432e-106">[Jupyter](https://jupyter.org/) is an open-source, cross-platform computing environment that provides a way for users to prototype and develop applications interactively.</span></span> <span data-ttu-id="2432e-107">Для взаимодействия с Jupyter можно использовать широкий набор интерфейсов, таких как Jupyter Notebook, Jupyter Lab и VS Code.</span><span class="sxs-lookup"><span data-stu-id="2432e-107">You can interact with Jupyter through a wide variety of interfaces such as Jupyter Notebook, Jupyter Lab, and VS Code.</span></span>

<span data-ttu-id="2432e-108">В контексте .NET, [.NET Interactive](https://github.com/dotnet/interactive), глобальное средство .NET Core, предоставляет ядро для написания кода .NET (C#/F#) в интерактивных вычислительных средах, таких как Jupyter Notebook.</span><span class="sxs-lookup"><span data-stu-id="2432e-108">In the context of .NET, [.NET Interactive](https://github.com/dotnet/interactive), a .NET Core global tool, provides a kernel for writing .NET code (C#/F#) in interactive computing environments such as Jupyter Notebook.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2432e-109">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="2432e-109">Prerequisites</span></span>

- [<span data-ttu-id="2432e-110">Пакет SDK для .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="2432e-110">.NET Core 3.1 SDK</span></span>](../../core/install/index.yml)
- [<span data-ttu-id="2432e-111">Apache Spark</span><span class="sxs-lookup"><span data-stu-id="2432e-111">Apache Spark</span></span>](https://spark.apache.org/downloads.html)
- [<span data-ttu-id="2432e-112">Рабочая роль Apache Spark .NET</span><span class="sxs-lookup"><span data-stu-id="2432e-112">Apache Spark .NET Worker</span></span>](https://github.com/dotnet/spark/releases)

<span data-ttu-id="2432e-113">Дополнительные сведения о настройке среды .NET для Apache Spark см. в [руководстве по началу работы](../tutorials/get-started.md).</span><span class="sxs-lookup"><span data-stu-id="2432e-113">See the [getting started tutorial](../tutorials/get-started.md) for more information on setting up your .NET for Apache Spark environment.</span></span>

## <a name="prepare-environment"></a><span data-ttu-id="2432e-114">Подготовка среды</span><span class="sxs-lookup"><span data-stu-id="2432e-114">Prepare environment</span></span>

<span data-ttu-id="2432e-115">Для работы с записными книжками Jupyter Notebook потребуется две вещи.</span><span class="sxs-lookup"><span data-stu-id="2432e-115">To work with Jupyter Notebooks, you'll need two things.</span></span>

1. <span data-ttu-id="2432e-116">Установите [глобальное средство .NET Interactive](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md).</span><span class="sxs-lookup"><span data-stu-id="2432e-116">Install the [.NET Interactive global .NET tool](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)</span></span>
1. <span data-ttu-id="2432e-117">Скачайте пакет NuGet `Microsoft.Spark`.</span><span class="sxs-lookup"><span data-stu-id="2432e-117">Download the `Microsoft.Spark` NuGet package.</span></span>
    1. <span data-ttu-id="2432e-118">Перейдите на страницу пакета NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/).</span><span class="sxs-lookup"><span data-stu-id="2432e-118">Navigate to the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package page.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="2432e-119">По умолчанию скачивается последняя версия пакета.</span><span class="sxs-lookup"><span data-stu-id="2432e-119">By default, the latest version of the package is downloaded.</span></span> <span data-ttu-id="2432e-120">**Убедитесь, что загружаемая версия совпадает с версией рабочей роли .NET Apache Spark.**</span><span class="sxs-lookup"><span data-stu-id="2432e-120">**Make sure that the version you download is the same as your Apache Spark .NET Worker.**</span></span>

    1. <span data-ttu-id="2432e-121">В области **Сведения** выберите **Скачать пакет**, чтобы скачать последнюю версию пакета.</span><span class="sxs-lookup"><span data-stu-id="2432e-121">In the **Info** pane, select **Download package** to download the latest version of the package.</span></span> <span data-ttu-id="2432e-122">Имя пакета аналогично *microsoft.spark.[PACKAGE-VERSION].nupkg*.</span><span class="sxs-lookup"><span data-stu-id="2432e-122">The name of the package is similar to  *microsoft.spark.[PACKAGE-VERSION].nupkg*.</span></span>
    1. <span data-ttu-id="2432e-123">Распакуйте скачанный пакет.</span><span class="sxs-lookup"><span data-stu-id="2432e-123">Unzip the downloaded package.</span></span> <span data-ttu-id="2432e-124">В распакованном каталоге должен содержаться подкаталог *jars*.</span><span class="sxs-lookup"><span data-stu-id="2432e-124">The unzipped directory should contain a subdirectory called *jars*.</span></span> <span data-ttu-id="2432e-125">Запишите путь, так как он потребуется позже.</span><span class="sxs-lookup"><span data-stu-id="2432e-125">Take note of the path since it's used at a later time.</span></span>

## <a name="start-net-for-apache-spark"></a><span data-ttu-id="2432e-126">Запуск .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="2432e-126">Start .NET for Apache Spark</span></span>

<span data-ttu-id="2432e-127">Выполните следующую команду, чтобы запустить .NET для Apache Spark в режиме отладки.</span><span class="sxs-lookup"><span data-stu-id="2432e-127">Run the following command to start .NET for Apache Spark in debug mode.</span></span> <span data-ttu-id="2432e-128">Команда `spark-submit` запускает процесс и ожидает подключения от [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span><span class="sxs-lookup"><span data-stu-id="2432e-128">This `spark-submit` command starts a process and waits for connections from a [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span> <span data-ttu-id="2432e-129">Обязательно укажите путь к `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` для соответствующей используемой версии .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="2432e-129">Make sure to provide the path to the `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` for the respective version of .NET for Apache Spark you're using.</span></span>

<span data-ttu-id="2432e-130">**Ubuntu**</span><span class="sxs-lookup"><span data-stu-id="2432e-130">**Ubuntu**</span></span>

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

<span data-ttu-id="2432e-131">**Windows**</span><span class="sxs-lookup"><span data-stu-id="2432e-131">**Windows**</span></span>

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a><span data-ttu-id="2432e-132">Создание записной книжки</span><span class="sxs-lookup"><span data-stu-id="2432e-132">Create a notebook</span></span>

<span data-ttu-id="2432e-133">Для взаимодействия с Jupyter можно использовать различные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="2432e-133">You can use different interfaces to interact with Jupyter.</span></span> <span data-ttu-id="2432e-134">Для интерфейса на основе браузера используйте Jupyter Notebook или Jupyter Lab.</span><span class="sxs-lookup"><span data-stu-id="2432e-134">For a browser-based interface, use Jupyter Notebooks or Jupyter Lab.</span></span> <span data-ttu-id="2432e-135">Для работы с локальным редактором используйте VS Code.</span><span class="sxs-lookup"><span data-stu-id="2432e-135">For a local editor experience, use VS Code.</span></span>

### <a name="jupyter-notebooks--jupyter-lab"></a><span data-ttu-id="2432e-136">Jupyter Notebook и Jupyter Lab</span><span class="sxs-lookup"><span data-stu-id="2432e-136">Jupyter Notebooks & Jupyter Lab</span></span>

1. <span data-ttu-id="2432e-137">В другой командной строке запустите Jupyter Notebook или Jupyter Lab с помощью одной из следующих команд:</span><span class="sxs-lookup"><span data-stu-id="2432e-137">In another command prompt, start Jupyter Notebook or Jupyter Lab using one of the commands below:</span></span>

    <span data-ttu-id="2432e-138">**Записная книжка Jupyter**</span><span class="sxs-lookup"><span data-stu-id="2432e-138">**Jupyter Notebook**</span></span>

    ```bash
    jupyter notebook
    ```

    <span data-ttu-id="2432e-139">**Jupyter Lab**</span><span class="sxs-lookup"><span data-stu-id="2432e-139">**Jupyter Lab**</span></span>

    ```bash
    jupyter lab
    ```

    <span data-ttu-id="2432e-140">Эти команды запускают окно браузера с интерфейсом Jupyter Notebook или Jupyter Lab.</span><span class="sxs-lookup"><span data-stu-id="2432e-140">These commands launch a browser window with the Jupyter Notebook or Jupyter Lab interface.</span></span>

1. <span data-ttu-id="2432e-141">В браузере создайте новую записную книжку.</span><span class="sxs-lookup"><span data-stu-id="2432e-141">In the browser, create a new notebook.</span></span>

    <span data-ttu-id="2432e-142">**Записная книжка Jupyter**</span><span class="sxs-lookup"><span data-stu-id="2432e-142">**Jupyter Notebook**</span></span>

    <span data-ttu-id="2432e-143">Выберите **Создать > .NET (C#)** или **Создать > .NET (F#)**</span><span class="sxs-lookup"><span data-stu-id="2432e-143">Select **New > .NET (C#)** or **New > .NET (F#)**</span></span>

    <span data-ttu-id="2432e-144">**Jupyter Lab**</span><span class="sxs-lookup"><span data-stu-id="2432e-144">**Jupyter Lab**</span></span>

    <span data-ttu-id="2432e-145">В окне средства запуска выберите **.NET (C#)** или **.NET (F#).**</span><span class="sxs-lookup"><span data-stu-id="2432e-145">In the Launcher window, select **.NET (C#)** or **.NET (F#)**</span></span>

### <a name="visual-studio-code-preview"></a><span data-ttu-id="2432e-146">Visual Studio Code (предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="2432e-146">Visual Studio Code (preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2432e-147">Чтобы использовать Jupyter Notebook в VS Code, необходимо установить следующее:</span><span class="sxs-lookup"><span data-stu-id="2432e-147">To use Jupyter Notebooks in VS Code, you have to install:</span></span>
>
>- [<span data-ttu-id="2432e-148">VS Code Insiders</span><span class="sxs-lookup"><span data-stu-id="2432e-148">VS Code Insiders</span></span>](https://code.visualstudio.com/insiders/)
>- [<span data-ttu-id="2432e-149">Расширение Notebooks для .NET Interactive</span><span class="sxs-lookup"><span data-stu-id="2432e-149">.NET Interactive Notebooks extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. <span data-ttu-id="2432e-150">Откройте VS Code.</span><span class="sxs-lookup"><span data-stu-id="2432e-150">Open VS Code.</span></span>
1. <span data-ttu-id="2432e-151">Откройте палитру команд **Вид > Палитра команд**.</span><span class="sxs-lookup"><span data-stu-id="2432e-151">Open the command palette **View > Command Palette**.</span></span>

    <span data-ttu-id="2432e-152">Когда появится палитра команд, введите следующую команду, чтобы создать новую записную книжку .NET Interactive:</span><span class="sxs-lookup"><span data-stu-id="2432e-152">When the command palette appears, enter the following command to create a new .NET Interactive notebook:</span></span>

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    <span data-ttu-id="2432e-153">Кроме того, если вы хотите открыть существующую записную книжку .NET Interactive с расширением *IPYNB*, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2432e-153">Alternatively, if you want to open an existing .NET Interactive notebook with the *.ipynb* extension, use the following command:</span></span>

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a><span data-ttu-id="2432e-154">Инициализация сеанса Spark</span><span class="sxs-lookup"><span data-stu-id="2432e-154">Initialize a Spark Session</span></span>

1. <span data-ttu-id="2432e-155">После открытия записной книжки установите пакет NuGet `Microsoft.Spark`.</span><span class="sxs-lookup"><span data-stu-id="2432e-155">When the notebook opens, install the `Microsoft.Spark` NuGet package.</span></span> <span data-ttu-id="2432e-156">Убедитесь, что устанавливаемая версия совпадает с рабочей ролью .NET.</span><span class="sxs-lookup"><span data-stu-id="2432e-156">Make sure the version you install is the same as the .NET Worker.</span></span>

    ```text
    #r "nuget:Microsoft.Spark, 1.0.0"
    ```

1. <span data-ttu-id="2432e-157">Добавьте в файл следующую инструкцию using.</span><span class="sxs-lookup"><span data-stu-id="2432e-157">Add the following using statement to the notebook.</span></span>

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. <span data-ttu-id="2432e-158">Инициализируйте [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span><span class="sxs-lookup"><span data-stu-id="2432e-158">Initialize your [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span>

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

<span data-ttu-id="2432e-159">Записная книжка должна выглядеть примерно так, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="2432e-159">The notebook should look similar to the one in the following image.</span></span> <span data-ttu-id="2432e-160">В этом примере используется VS Code, однако Jupyter Notebook и Jupyter Lab должны выглядеть примерно так же.</span><span class="sxs-lookup"><span data-stu-id="2432e-160">This example uses VS Code, but Jupyter Notebook and Jupyter Lab should look about the same.</span></span>

> [!div class="mx-imgBorder"]
<span data-ttu-id="2432e-161">![Jupyter Notebook VS Code .NET для Apache Spark](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span><span class="sxs-lookup"><span data-stu-id="2432e-161">![.NET for Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span></span>

## <a name="next-steps"></a><span data-ttu-id="2432e-162">Next Steps</span><span class="sxs-lookup"><span data-stu-id="2432e-162">Next Steps</span></span>

- [<span data-ttu-id="2432e-163">Начало работы с .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="2432e-163">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
- [<span data-ttu-id="2432e-164">Прогнозирование тональности с помощью .NET для Apache Spark и ML.NET</span><span class="sxs-lookup"><span data-stu-id="2432e-164">Predict sentiment using .NET for Apache Spark and ML.NET</span></span>](../tutorials/ml-sentiment-analysis.md)
- <span data-ttu-id="2432e-165">Дополнительные сведения о .NET Interactive см. в [документации по .NET Interactive](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span><span class="sxs-lookup"><span data-stu-id="2432e-165">For more information on .NET Interactive, see the [.NET Interactive documentation](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span></span>
