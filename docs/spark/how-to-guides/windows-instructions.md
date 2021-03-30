---
title: Сборка приложения .NET для Apache Spark в Windows
description: Сведения о том, как скомпилировать приложение .NET для Apache Spark в Windows.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: e3ab62ea8bc493c7e652b66f0e9c7adce7decb56
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876959"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="0b8d7-103">Сведения о том, как скомпилировать приложение .NET для Apache Spark в Windows</span><span class="sxs-lookup"><span data-stu-id="0b8d7-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="0b8d7-104">В этой статье представлены сведения о том, как скомпилировать приложение .NET для Apache Spark в Windows.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0b8d7-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="0b8d7-105">Prerequisites</span></span>

<span data-ttu-id="0b8d7-106">Если у вас уже есть все перечисленные ниже компоненты, перейдите к [сборке](#build).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="0b8d7-107">Скачайте и установите **[пакет SDK для .NET Core](https://dotnet.microsoft.com/download/dotnet/3.1)** . После этого в путь будет добавлена цепочка инструментов `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet/3.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="0b8d7-108">Поддерживается .NET Core версий 2.1, 2.2 и 3.1.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="0b8d7-109">Установите **[Visual Studio 2019](https://www.visualstudio.com/downloads/)**  16.3 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="0b8d7-110">Версия Community предоставляется бесплатно.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-110">The Community version is completely free.</span></span> <span data-ttu-id="0b8d7-111">При настройке установки включите по меньшей мере следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="0b8d7-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="0b8d7-112">Разработка классических приложений .NET</span><span class="sxs-lookup"><span data-stu-id="0b8d7-112">.NET desktop development</span></span>
       * <span data-ttu-id="0b8d7-113">Все необходимые компоненты.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-113">All Required Components</span></span>
         * <span data-ttu-id="0b8d7-114">Средства разработки для .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="0b8d7-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="0b8d7-115">Кроссплатформенная разработка .NET Core</span><span class="sxs-lookup"><span data-stu-id="0b8d7-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="0b8d7-116">Все необходимые компоненты.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-116">All Required Components</span></span>
  3. <span data-ttu-id="0b8d7-117">Установите **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span>
     - <span data-ttu-id="0b8d7-118">Выберите соответствующую версию для вашей операционной системы.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-118">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="0b8d7-119">Например, *jdk-8u201-windows-x64.exe* для компьютера с 64-разрядной версией Windows.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-119">For example, *jdk-8u201-windows-x64.exe* for Windows x64 machine.</span></span>
     - <span data-ttu-id="0b8d7-120">Запустите установщик и убедитесь, что можете выполнить команду `java` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-120">Install using the installer and verify you are able to run `java` from your command line.</span></span>
  4. <span data-ttu-id="0b8d7-121">Установите **[Apache Maven 3.6.0 или более поздней версии](https://maven.apache.org/download.cgi)** .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-121">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="0b8d7-122">Скачайте [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-122">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span></span>
     - <span data-ttu-id="0b8d7-123">Извлеките содержимое в локальный каталог.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-123">Extract to a local directory.</span></span> <span data-ttu-id="0b8d7-124">Например, \*C:\bin\apache-maven-3.6.0\*.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-124">For example, \*C:\bin\apache-maven-3.6.0\*.</span></span>
     - <span data-ttu-id="0b8d7-125">Добавьте Apache Maven в [переменную среды PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-125">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="0b8d7-126">Например, *C:\bin\apache-maven-3.6.0\bin*.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-126">For example, *C:\bin\apache-maven-3.6.0\bin*.</span></span>
     - <span data-ttu-id="0b8d7-127">Убедитесь в том, что можно выполнить команду `mvn` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-127">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="0b8d7-128">Установите **[Apache Spark 2.3 или более поздней версии](https://spark.apache.org/downloads.html)** .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-128">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="0b8d7-129">Скачайте [Apache Spark 2.3 или более поздней версии](https://spark.apache.org/downloads.html) и извлеките содержимое в локальную папку (например, *C:\bin\spark-3.0.1-bin-hadoop2.7\*) с помощью средства [7-zip](https://www.7-zip.org/). (Поддерживаются версии Spark 2.3.* , 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 и 3.0.1.)</span><span class="sxs-lookup"><span data-stu-id="0b8d7-129">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (for example, *C:\bin\spark-3.0.1-bin-hadoop2.7\*) using [7-zip](https://www.7-zip.org/). (The supported spark versions are 2.3.*, 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 and 3.0.1)</span></span>
     - <span data-ttu-id="0b8d7-130">Добавьте [новую переменную среды](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-130">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span></span> <span data-ttu-id="0b8d7-131">Например, \*C:\bin\spark-3.0.1-bin-hadoop2.7\*.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-131">For example, \*C:\bin\spark-3.0.1-bin-hadoop2.7\*.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-3.0.1-bin-hadoop2.7\
       ```

     - <span data-ttu-id="0b8d7-132">Добавьте Apache Spark в [переменную среды PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-132">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="0b8d7-133">Например, *C:\bin\spark-3.0.1-bin-hadoop2.7\bin*.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-133">For example, *C:\bin\spark-3.0.1-bin-hadoop2.7\bin*.</span></span>

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - <span data-ttu-id="0b8d7-134">Убедитесь в том, что можно выполнить команду `spark-shell` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-134">Verify you are able to run `spark-shell` from your command-line.</span></span>
        <span data-ttu-id="0b8d7-135">Пример выходных данных в консоли.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-135">Sample console output:</span></span>

        ```output
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 3.0.1
              /_/

        Using Scala version 2.12.10 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. <span data-ttu-id="0b8d7-136">Установите **[WinUtils](https://github.com/steveloughran/winutils)** .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-136">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="0b8d7-137">Скачайте двоичный файл `winutils.exe` из [репозитория WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-137">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="0b8d7-138">Выберите версию Hadoop, с использованием которой был скомпилирован дистрибутив Spark.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-138">You should select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="0b8d7-139">Например, для Spark 3.0.1 используйте hadoop-2.7.1.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-139">For exammple, use hadoop-2.7.1 for Spark 3.0.1.</span></span>
     - <span data-ttu-id="0b8d7-140">Сохраните двоичный файл `winutils.exe` в любом каталоге по своему выбору.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-140">Save `winutils.exe` binary to a directory of your choice.</span></span> <span data-ttu-id="0b8d7-141">Например, *C:\hadoop\bin*.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-141">For example, *C:\hadoop\bin*.</span></span>
     - <span data-ttu-id="0b8d7-142">Включите в переменную среды `HADOOP_HOME` путь к каталогу с файлом winutils.exe (без строки bin).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-142">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="0b8d7-143">Например, выполните такую команду в командной строке:</span><span class="sxs-lookup"><span data-stu-id="0b8d7-143">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="0b8d7-144">Включите в переменную среды PATH значение `%HADOOP_HOME%\bin`.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-144">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="0b8d7-145">Например, выполните следующую команду в командной строке:</span><span class="sxs-lookup"><span data-stu-id="0b8d7-145">For instance, using command line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="0b8d7-146">Перед переходом к следующему разделу еще раз убедитесь, что можете выполнять команды `dotnet`, `java`, `mvn` и `spark-shell` из командной строки.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-146">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span> <span data-ttu-id="0b8d7-147">Считаете, что есть более эффективный способ?</span><span class="sxs-lookup"><span data-stu-id="0b8d7-147">Feel there is a better way?</span></span> <span data-ttu-id="0b8d7-148">[Сообщите о проблеме](https://github.com/dotnet/spark/issues) и поделитесь своим мнением.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-148">[Open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="0b8d7-149">После обновления переменных среды, возможно, потребуется открыть новый экземпляр командной строки.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-149">A new instance of the command line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="0b8d7-150">Построение</span><span class="sxs-lookup"><span data-stu-id="0b8d7-150">Build</span></span>

<span data-ttu-id="0b8d7-151">Для выполнения задач оставшейся части этого руководства потребуется копия репозитория .NET для Apache Spark, клонированная на локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-151">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="0b8d7-152">Для клонированного репозитория можно выбрать любое расположение.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-152">You can choose any location for the cloned repository.</span></span> <span data-ttu-id="0b8d7-153">Например, \*C:\github\dotnet-spark\*.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-153">For example, \*C:\github\dotnet-spark\*.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="0b8d7-154">Сборка уровня расширений Scala в .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="0b8d7-154">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="0b8d7-155">Когда вы отправляете приложение .NET, .NET для Apache Spark применяет соответствующую логику на языке Scala, которая информирует Apache Spark о методах обработки запросов (таких как запрос на создание нового сеанса Spark, запрос на передачу данных из .NET на виртуальную машину Java и т. п.).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-155">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (for example, request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="0b8d7-156">Эту логику можно найти в [исходном коде Scala в .NET для Spark](https://github.com/dotnet/spark/tree/main/src/scala).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-156">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/main/src/scala).</span></span>

<span data-ttu-id="0b8d7-157">Независимо от того, какую технологию вы используете (.NET Framework или .NET Core), вам нужно создать уровень расширения Scala в .NET для Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="0b8d7-157">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package
```

<span data-ttu-id="0b8d7-158">Здесь должны быть JAR-файлы, созданные для поддерживаемых версий Spark:</span><span class="sxs-lookup"><span data-stu-id="0b8d7-158">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2-3\target\microsoft-spark-2-3_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-2-4\target\microsoft-spark-2-4_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-3-0\target\microsoft-spark-3-0_2.12-<spark-dotnet-version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="0b8d7-159">Сборка примеров приложений .NET для Spark</span><span class="sxs-lookup"><span data-stu-id="0b8d7-159">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="0b8d7-160">В этом разделе объясняется, как создать [примеры приложений](https://github.com/dotnet/spark/tree/main/examples) для .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-160">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/main/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="0b8d7-161">Эти шаги помогут составить представление об общем процессе сборки для любого приложения .NET для Spark.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-161">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="0b8d7-162">Использование Visual Studio для .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0b8d7-162">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="0b8d7-163">Откройте `src\csharp\Microsoft.Spark.sln` в Visual Studio и скомпилируйте проект `Microsoft.Spark.CSharp.Examples` в папке `examples` (это действие приводит к автоматической компиляции проекта привязок .NET).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-163">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="0b8d7-164">При желании можно добавить в проект `Microsoft.Spark.Examples` собственный код (в нашем примере файл input_file.json содержит данные в формате JSON, на основе которых вы будете создавать таблицу данных):</span><span class="sxs-lookup"><span data-stu-id="0b8d7-164">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     <span data-ttu-id="0b8d7-165">После успешной сборки вы увидите двоичные файлы, созданные в выходном каталоге.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-165">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>
     <span data-ttu-id="0b8d7-166">Пример выходных данных в консоли.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-166">Sample console output:</span></span>

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="0b8d7-167">Использование .NET Core CLI для .NET Core</span><span class="sxs-lookup"><span data-stu-id="0b8d7-167">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="0b8d7-168">Сейчас мы работаем над автоматизацией сборок .NET Core для Spark .NET.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-168">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="0b8d7-169">Пока этот компонент не готов, вам придется выполнить часть действий вручную. Благодарим за терпение.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-169">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="0b8d7-170">Скомпилируйте рабочую роль:</span><span class="sxs-lookup"><span data-stu-id="0b8d7-170">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp3.1 -r win-x64
      ```

      <span data-ttu-id="0b8d7-171">Пример выходных данных в консоли.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-171">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp3.1 -r win-x64
      Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.1\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish\
      ```

  2. <span data-ttu-id="0b8d7-172">Скомпилируйте примеры:</span><span class="sxs-lookup"><span data-stu-id="0b8d7-172">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp3.1 -r win-x64
      ```

      <span data-ttu-id="0b8d7-173">Пример выходных данных в консоли.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-173">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp3.1 -r win-x64
      Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.1\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="0b8d7-174">Запуск примеров приложений .NET для Spark</span><span class="sxs-lookup"><span data-stu-id="0b8d7-174">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="0b8d7-175">После сборки примеров их можно запустить через `spark-submit`, независимо от целевой платформы (.NET Framework или .NET Core).</span><span class="sxs-lookup"><span data-stu-id="0b8d7-175">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="0b8d7-176">Убедитесь, что выполнены все [предварительные требования](#prerequisites) и установка Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-176">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="0b8d7-177">Задайте переменную среды `DOTNET_WORKER_DIR` или `PATH`, чтобы включить путь, по которому был создан двоичный файл `Microsoft.Spark.Worker` (например, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* для .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish* для .NET Core):</span><span class="sxs-lookup"><span data-stu-id="0b8d7-177">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish* for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish
      ```
  
  2. <span data-ttu-id="0b8d7-178">Откройте PowerShell и перейдите в каталог, где создан двоичный файл приложения (например, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* для .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish* для .NET Core):</span><span class="sxs-lookup"><span data-stu-id="0b8d7-178">Open PowerShell and go to the directory where your app binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish* for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish
      ```

  3. <span data-ttu-id="0b8d7-179">Приложение запускается по единой общей схеме.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-179">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="0b8d7-180">Вот несколько примеров, которые вы можете выполнить:</span><span class="sxs-lookup"><span data-stu-id="0b8d7-180">Here are some examples you can run:</span></span>

     - <span data-ttu-id="0b8d7-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)** .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="0b8d7-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)** .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="0b8d7-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)** .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="0b8d7-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)** .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
