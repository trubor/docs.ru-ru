---
title: Руководство. Структурированная потоковая передача с помощью .NET для Apache Spark
description: Узнайте, как с помощью .NET для Apache Spark выполнять структурированную потоковую передачу Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 29f90c43ece1f2655a15f759b473f723e712bda8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873176"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Учебник. Структурированная потоковая передача с помощью .NET для Apache Spark

В этом руководстве показано, как запустить структурированную потоковую передачу Spark с помощью .NET для Apache Spark. Структурированная потоковая передача в Apache Spark предназначена для обработки потоков данных в режиме реального времени. Потоковая обработка означает анализ актуальных данных по мере их создания.

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
>
> * создать и выполнить приложение .NET для Apache Spark;
> * создать поток данных с помощью netcat;
> * применить пользовательские функции и SparkSQL для анализа потоковых данных.

## <a name="prerequisites"></a>Предварительные требования

Если это ваше первое приложение .NET для Apache Spark, начните с [руководства по началу работы](get-started.md), чтобы ознакомиться с основами.

## <a name="create-a-console-application"></a>Создание консольного приложение

1. В командной строке выполните следующие команды, чтобы создать новое консольное приложение:

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   Команда `dotnet` создаст для вас приложение `new` типа `console`. Параметр `-o` создаст каталог с именем *mySparkStreamingApp*, в котором хранится приложение и требуемые файлы. Команда `cd mySparkStreamingApp` изменит каталог на только что созданный каталог приложения.

1. Чтобы использовать .NET для Apache Spark в приложении, установите пакет Microsoft.Spark. В консоли выполните следующую команду:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Создание потока данных и подключение к нему

Одним из популярных методов проверки потоковой обработки является **netcat**. Средство netcat (или *nc*) позволяет считывать данные из сетевых подключений и записывать эти данные в них. Сетевое подключение в netcat устанавливается через окно терминала.

### <a name="create-a-data-stream-with-netcat"></a>Создание потока данных с помощью netcat

1. [Скачайте netcat](https://sourceforge.net/projects/nc110/files/). Затем извлеките файл из скачанного ZIP-файла и добавьте каталог, в который вы его извлекли, в переменную среды PATH.

2. Чтобы создать подключение, откройте новую консоль и выполните следующую команду, которая подключается к localhost через порт 9999.

   В Windows:

   ```console
   nc -vvv -l -p 9999
   ```

   В Linux

   ```console
   nc -lk 9999
   ```

   Программа Spark прослушивает входные данные, которые вы вводите в командную строку.

### <a name="create-a-sparksession"></a>Создание SparkSession

1. Добавьте следующие дополнительные инструкции `using` в начало файла *Program.cs* приложения *mySparkStreamingApp*:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Добавьте приведенный ниже код в метод `Main`, чтобы создать новый экземпляр `SparkSession`. Сеанс Spark является точкой входа для программирования Spark через API DataSet и DataFrame.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   Вызов созданного выше объекта *spark* позволяет получить доступ к функциям Spark и DataFrame в любом месте вашей программы.

### <a name="connect-to-a-stream-with-readstream"></a>Подключение к потоку с помощью ReadStream()

Метод `ReadStream()` возвращает `DataStreamReader` для чтения потоковых данных в виде `DataFrame`. Включите сведения об узле и порте, чтобы приложение Spark знало, где ожидать данные потоковой передачи.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Регистрация определяемой пользователем функции

Для выполнения вычислений и анализа данных в приложениях Spark можно использовать *определяемые пользователем функции*.

Добавьте следующий код в метод `Main`, чтобы зарегистрировать определяемую пользователем функцию с именем `udfArray`.

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Она обрабатывает каждую строку, полученную из терминала netcat, и создает массив, который содержит исходную строку (в *str*) и объединение исходной строки с длиной этой строки.

Например, если вы введете в терминале netcat строку *Hello World*, итоговый массив будет выглядеть так:

* array\[0] = Hello world
* array\[1] = Hello world 11

## <a name="use-sparksql"></a>Использование SparkSQL

С помощью SparkSQL можно выполнять разные функции с данными, сохраненными в DataFrame. Достаточно распространен вариант совместного применения определяемых пользователем функций и SparkSQL, чтобы эта функция обрабатывала каждую строку в DataFrame.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Следующий фрагмент кода применяет *udfArray* к каждому значению в DataFrame с представлением строк, считанных из терминала netcat. Примените метод SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A>, чтобы разместить каждую запись массива в отдельной строке. Наконец, используйте <xref:Microsoft.Spark.Sql.DataFrame.Select%2A>, чтобы разместить столбцы, созданные в новом экземпляре *arrayDF* DataFrame.

## <a name="display-your-stream"></a>Отображение потока

Используйте <xref:Microsoft.Spark.Sql.DataFrame.WriteStream>, чтобы установить характеристики выходных данных, например вывод результатов на консоль и отображение только самых свежих выходных данных.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Выполнение кода

Структурированная потоковая передача в Spark обрабатывает данные в виде нескольких небольших **пакетов**.  При выполнении программы для ввода данных можно использовать командную строку, в которой вы установили подключение netcat. После каждого нажатия клавиши ВВОД при вводе в командную строку любых данных Spark запускает определяемую пользователем функцию с пакетом данных, содержащим эти введенные данные.

### <a name="use-spark-submit-to-run-your-app"></a>Использование команды spark-submit для выполнения приложения

Запустив новый сеанс netcat, откройте новое окно терминала и выполните команду `spark-submit`, как показано ниже.

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Не забудьте указать в представленной выше команде фактический путь к JAR-файлу Microsoft Spark. Приведенная выше команда также предполагает, что сервер netcat использует порт localhost 9999.

## <a name="get-the-code"></a>Получение кода

В этом руководстве используется пример [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs), но на GitHub есть еще три полных примера обработки потока:

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs) вычисляет количество слов в потоке данных из любого источника;
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs) вычисляет количество слов в данных, используя логику управления окнами;
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs) вычисляет количество слов в данных потоковой передачи от Kafka.

## <a name="next-steps"></a>Дальнейшие действия

Переходите к следующему руководстве, чтобы научиться развертывать приложение .NET для Apache Spark в среде Databricks.
> [!div class="nextstepaction"]
> [Учебник. Развертывание приложения .NET для Apache Spark в Databricks](databricks-deployment.md)
