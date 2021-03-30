---
title: Сборка приложения .NET для Apache Spark в Ubuntu
description: Сведения о том, как скомпилировать приложение .NET для Apache Spark в Ubuntu.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 300c858a76ba31650615bde70c951e383e9e0436
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875334"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>Сведения о том, как скомпилировать приложение .NET для Apache Spark в Ubuntu.

В этой статье представлены сведения о том, как скомпилировать приложение .NET для Apache Spark в Ubuntu.

## <a name="prerequisites"></a>Prerequisites

Если у вас уже есть все перечисленные ниже компоненты, перейдите к [сборке](#build).

1. Скачайте и установите пакет SDK для **[.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)** . После этого в путь будет добавлена цепочка инструментов `dotnet`.  Поддерживается .NET Core версий 2.1, 2.2 и 3.1.

2. Установите **[OpenJDK 8](https://openjdk.java.net/install/)** .

   - Вы можете использовать следующую команду:

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * Убедитесь в том, что можно выполнить команду `java` в командной строке.

      Пример выходных данных java-version:

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * Если вы уже установили несколько версий OpenJDK и хотите выбрать OpenJDK 8, используйте следующую команду:

      ```bash
      sudo update-alternatives --config java
      ```

3. Установите **[Apache Maven 3.6.0 или более поздней версии](https://maven.apache.org/download.cgi)** .

   * Выполните следующую команду:

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       Обратите внимание, что при закрытии терминала эти переменные среды не будут сохранены. Если вы хотите, чтобы изменения были постоянными, добавьте строки `export` в файл `~/.bashrc`.

   * Убедитесь в том, что можно выполнить команду `mvn` в командной строке.

       Пример выходных данных mvn -version:

       ```output
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. Установите **[Apache Spark 2.3 или более поздней версии](https://spark.apache.org/downloads.html)** .
Скачайте [Apache Spark 2.3 или более поздней версии](https://spark.apache.org/downloads.html) и извлеките содержимое в локальную папку (например, `~/bin/spark-3.0.1-bin-hadoop2.7`). (Поддерживаются версии Spark 2.3.*, 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 и 3.0.1)

   ```bash
   tar -xvzf /path/to/spark-3.0.1-bin-hadoop2.7.tgz -C ~/bin/spark-3.0.1-bin-hadoop2.7
   ```

   * Добавьте необходимые [переменные среды](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (например, `~/bin/spark-3.0.1-bin-hadoop2.7/`) и `PATH` (например, `$SPARK_HOME/bin:$PATH`).

      ```bash
      export SPARK_HOME=~/bin/spark-3.0.1-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      Обратите внимание, что при закрытии терминала эти переменные среды не будут сохранены. Если вы хотите, чтобы изменения были постоянными, добавьте строки `export` в файл `~/.bashrc`.

   * Убедитесь в том, что можно выполнить команду `spark-shell` в командной строке.

      Пример выходных данных в консоли.

      ```
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

Перед переходом к следующему разделу еще раз убедитесь, что можно выполнять команды `dotnet`, `java`, `mvn` и `spark-shell` из командной строки. Считаете, что есть более эффективный способ? [Сообщите о проблеме](https://github.com/dotnet/spark/issues) и поделитесь своим мнением.

## <a name="build"></a>Сборка

Для выполнения задач оставшейся части этого руководства потребуется копия репозитория .NET для Apache Spark, клонированная на локальный компьютер, например `~/dotnet.spark/`.

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>Сборка уровня расширений Scala в .NET для Spark

Когда вы отправляете приложение .NET, .NET для Apache Spark применяет соответствующую логику на языке Scala, которая информирует Apache Spark о методах обработки запросов (таких как запрос на создание нового сеанса Spark, запрос на передачу данных от .NET на виртуальную машину Java и т. п.). Эту логику можно найти в [исходном коде Scala в .NET для Apache Spark](https://github.com/dotnet/spark/tree/main/src/scala).

Следующий шаг: сборка уровня расширений Scala в .NET для Apache Spark

```bash
cd src/scala
mvn clean package
```

Здесь должны быть JAR-файлы, созданные для поддерживаемых версий Spark:

* `microsoft-spark-2-3\target\microsoft-spark-2-3_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-2-4\target\microsoft-spark-2-4_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-3-0\target\microsoft-spark-3-0_2.12-<spark-dotnet-version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>Сборка примеров приложений .NET с помощью .NET Core CLI

В этом разделе объясняется, как создать [примеры приложений](https://github.com/dotnet/spark/tree/main/examples) для .NET для Apache Spark. Эти шаги помогут составить представление об общем процессе сборки для любого приложения .NET для Spark.

1. Скомпилируйте рабочую роль:

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   ```

   Пример выходных данных в консоли.

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.1/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/
   ```

2. Скомпилируйте примеры:

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   ```

   Пример выходных данных в консоли.

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.1/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a>Запуск примеров приложений .NET для Spark

После сборки примеров вы можете отправить приложения .NET Core с помощью `spark-submit`. Убедитесь, что выполнены все [предварительные требования](#prerequisites) и установка Apache Spark.

1. Включите в переменную среды `DOTNET_WORKER_DIR` или `PATH` путь, по которому был создан двоичный файл `Microsoft.Spark.Worker` (например, `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish`).

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish
   ```

2. Откройте терминал и перейдите к каталогу, где был создан двоичный файл приложения (например, `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish`).

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish
   ```

3. Приложение запускается по единой общей схеме.

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   Вот несколько примеров, которые вы можете выполнить:

   * **[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)** .

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)** .

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)** .

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)** .

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
