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
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Сведения о том, как скомпилировать приложение .NET для Apache Spark в Windows

В этой статье представлены сведения о том, как скомпилировать приложение .NET для Apache Spark в Windows.

## <a name="prerequisites"></a>Предварительные требования

Если у вас уже есть все перечисленные ниже компоненты, перейдите к [сборке](#build).

  1. Скачайте и установите **[пакет SDK для .NET Core](https://dotnet.microsoft.com/download/dotnet/3.1)** . После этого в путь будет добавлена цепочка инструментов `dotnet`. Поддерживается .NET Core версий 2.1, 2.2 и 3.1.
  2. Установите **[Visual Studio 2019](https://www.visualstudio.com/downloads/)**  16.3 или более поздней версии. Версия Community предоставляется бесплатно. При настройке установки включите по меньшей мере следующие компоненты:
     * Разработка классических приложений .NET
       * Все необходимые компоненты.
         * Средства разработки для .NET Framework 4.6.1
     * Кроссплатформенная разработка .NET Core
       * Все необходимые компоненты.
  3. Установите **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** .
     - Выберите соответствующую версию для вашей операционной системы. Например, *jdk-8u201-windows-x64.exe* для компьютера с 64-разрядной версией Windows.
     - Запустите установщик и убедитесь, что можете выполнить команду `java` в командной строке.
  4. Установите **[Apache Maven 3.6.0 или более поздней версии](https://maven.apache.org/download.cgi)** .
     - Скачайте [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Извлеките содержимое в локальный каталог. Например, *C:\bin\apache-maven-3.6.0\*.
     - Добавьте Apache Maven в [переменную среды PATH](https://www.java.com/en/download/help/path.xml). Например, *C:\bin\apache-maven-3.6.0\bin*.
     - Убедитесь в том, что можно выполнить команду `mvn` в командной строке.
  5. Установите **[Apache Spark 2.3 или более поздней версии](https://spark.apache.org/downloads.html)** .
     - Скачайте [Apache Spark 2.3 или более поздней версии](https://spark.apache.org/downloads.html) и извлеките содержимое в локальную папку (например, *C:\bin\spark-3.0.1-bin-hadoop2.7\*) с помощью средства [7-zip](https://www.7-zip.org/). (Поддерживаются версии Spark 2.3.* , 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 и 3.0.1.)
     - Добавьте [новую переменную среды](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`. Например, *C:\bin\spark-3.0.1-bin-hadoop2.7\*.

       ```powershell
       set SPARK_HOME=C:\bin\spark-3.0.1-bin-hadoop2.7\
       ```

     - Добавьте Apache Spark в [переменную среды PATH](https://www.java.com/en/download/help/path.xml). Например, *C:\bin\spark-3.0.1-bin-hadoop2.7\bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Убедитесь в том, что можно выполнить команду `spark-shell` в командной строке.
        Пример выходных данных в консоли.

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

  6. Установите **[WinUtils](https://github.com/steveloughran/winutils)** .
     - Скачайте двоичный файл `winutils.exe` из [репозитория WinUtils](https://github.com/steveloughran/winutils). Выберите версию Hadoop, с использованием которой был скомпилирован дистрибутив Spark. Например, для Spark 3.0.1 используйте hadoop-2.7.1.
     - Сохраните двоичный файл `winutils.exe` в любом каталоге по своему выбору. Например, *C:\hadoop\bin*.
     - Включите в переменную среды `HADOOP_HOME` путь к каталогу с файлом winutils.exe (без строки bin). Например, выполните такую команду в командной строке:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Включите в переменную среды PATH значение `%HADOOP_HOME%\bin`. Например, выполните следующую команду в командной строке:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Перед переходом к следующему разделу еще раз убедитесь, что можете выполнять команды `dotnet`, `java`, `mvn` и `spark-shell` из командной строки. Считаете, что есть более эффективный способ? [Сообщите о проблеме](https://github.com/dotnet/spark/issues) и поделитесь своим мнением.

> [!NOTE]
> После обновления переменных среды, возможно, потребуется открыть новый экземпляр командной строки.

## <a name="build"></a>Построение

Для выполнения задач оставшейся части этого руководства потребуется копия репозитория .NET для Apache Spark, клонированная на локальный компьютер. Для клонированного репозитория можно выбрать любое расположение. Например, *C:\github\dotnet-spark\*.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Сборка уровня расширений Scala в .NET для Apache Spark

Когда вы отправляете приложение .NET, .NET для Apache Spark применяет соответствующую логику на языке Scala, которая информирует Apache Spark о методах обработки запросов (таких как запрос на создание нового сеанса Spark, запрос на передачу данных из .NET на виртуальную машину Java и т. п.). Эту логику можно найти в [исходном коде Scala в .NET для Spark](https://github.com/dotnet/spark/tree/main/src/scala).

Независимо от того, какую технологию вы используете (.NET Framework или .NET Core), вам нужно создать уровень расширения Scala в .NET для Apache Spark:

```powershell
cd src\scala
mvn clean package
```

Здесь должны быть JAR-файлы, созданные для поддерживаемых версий Spark:

* `microsoft-spark-2-3\target\microsoft-spark-2-3_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-2-4\target\microsoft-spark-2-4_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-3-0\target\microsoft-spark-3-0_2.12-<spark-dotnet-version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Сборка примеров приложений .NET для Spark

В этом разделе объясняется, как создать [примеры приложений](https://github.com/dotnet/spark/tree/main/examples) для .NET для Apache Spark. Эти шаги помогут составить представление об общем процессе сборки для любого приложения .NET для Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Использование Visual Studio для .NET Framework

  1. Откройте `src\csharp\Microsoft.Spark.sln` в Visual Studio и скомпилируйте проект `Microsoft.Spark.CSharp.Examples` в папке `examples` (это действие приводит к автоматической компиляции проекта привязок .NET). При желании можно добавить в проект `Microsoft.Spark.Examples` собственный код (в нашем примере файл input_file.json содержит данные в формате JSON, на основе которых вы будете создавать таблицу данных):
  
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

     После успешной сборки вы увидите двоичные файлы, созданные в выходном каталоге.
     Пример выходных данных в консоли.

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

#### <a name="using-net-core-cli-for-net-core"></a>Использование .NET Core CLI для .NET Core

> [!NOTE]
> Сейчас мы работаем над автоматизацией сборок .NET Core для Spark .NET. Пока этот компонент не готов, вам придется выполнить часть действий вручную. Благодарим за терпение.

  1. Скомпилируйте рабочую роль:

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp3.1 -r win-x64
      ```

      Пример выходных данных в консоли.

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

  2. Скомпилируйте примеры:

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp3.1 -r win-x64
      ```

      Пример выходных данных в консоли.

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

## <a name="run-the-net-for-spark-sample-applications"></a>Запуск примеров приложений .NET для Spark

После сборки примеров их можно запустить через `spark-submit`, независимо от целевой платформы (.NET Framework или .NET Core). Убедитесь, что выполнены все [предварительные требования](#prerequisites) и установка Apache Spark.

  1. Задайте переменную среды `DOTNET_WORKER_DIR` или `PATH`, чтобы включить путь, по которому был создан двоичный файл `Microsoft.Spark.Worker` (например, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* для .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish* для .NET Core):

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\x64\Debug\netcoreapp3.1\win-x64\publish
      ```
  
  2. Откройте PowerShell и перейдите в каталог, где создан двоичный файл приложения (например, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* для .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish* для .NET Core):

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\x64\Debug\netcoreapp3.1\win-x64\publish
      ```

  3. Приложение запускается по единой общей схеме.

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Вот несколько примеров, которые вы можете выполнить:

     - **[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)** .

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)** .

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)** .

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)** .

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
