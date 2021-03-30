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
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="cfaf0-103">Учебник. Структурированная потоковая передача с помощью .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="cfaf0-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="cfaf0-104">В этом руководстве показано, как запустить структурированную потоковую передачу Spark с помощью .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="cfaf0-105">Структурированная потоковая передача в Apache Spark предназначена для обработки потоков данных в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="cfaf0-106">Потоковая обработка означает анализ актуальных данных по мере их создания.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="cfaf0-107">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="cfaf0-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="cfaf0-108">создать и выполнить приложение .NET для Apache Spark;</span><span class="sxs-lookup"><span data-stu-id="cfaf0-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="cfaf0-109">создать поток данных с помощью netcat;</span><span class="sxs-lookup"><span data-stu-id="cfaf0-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="cfaf0-110">применить пользовательские функции и SparkSQL для анализа потоковых данных.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cfaf0-111">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="cfaf0-111">Prerequisites</span></span>

<span data-ttu-id="cfaf0-112">Если это ваше первое приложение .NET для Apache Spark, начните с [руководства по началу работы](get-started.md), чтобы ознакомиться с основами.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="cfaf0-113">Создание консольного приложение</span><span class="sxs-lookup"><span data-stu-id="cfaf0-113">Create a console application</span></span>

1. <span data-ttu-id="cfaf0-114">В командной строке выполните следующие команды, чтобы создать новое консольное приложение:</span><span class="sxs-lookup"><span data-stu-id="cfaf0-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="cfaf0-115">Команда `dotnet` создаст для вас приложение `new` типа `console`.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="cfaf0-116">Параметр `-o` создаст каталог с именем *mySparkStreamingApp*, в котором хранится приложение и требуемые файлы.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="cfaf0-117">Команда `cd mySparkStreamingApp` изменит каталог на только что созданный каталог приложения.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="cfaf0-118">Чтобы использовать .NET для Apache Spark в приложении, установите пакет Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="cfaf0-119">В консоли выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="cfaf0-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="cfaf0-120">Создание потока данных и подключение к нему</span><span class="sxs-lookup"><span data-stu-id="cfaf0-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="cfaf0-121">Одним из популярных методов проверки потоковой обработки является **netcat**.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="cfaf0-122">Средство netcat (или *nc*) позволяет считывать данные из сетевых подключений и записывать эти данные в них.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="cfaf0-123">Сетевое подключение в netcat устанавливается через окно терминала.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="cfaf0-124">Создание потока данных с помощью netcat</span><span class="sxs-lookup"><span data-stu-id="cfaf0-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="cfaf0-125">[Скачайте netcat](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="cfaf0-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="cfaf0-126">Затем извлеките файл из скачанного ZIP-файла и добавьте каталог, в который вы его извлекли, в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="cfaf0-127">Чтобы создать подключение, откройте новую консоль и выполните следующую команду, которая подключается к localhost через порт 9999.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="cfaf0-128">В Windows:</span><span class="sxs-lookup"><span data-stu-id="cfaf0-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="cfaf0-129">В Linux</span><span class="sxs-lookup"><span data-stu-id="cfaf0-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="cfaf0-130">Программа Spark прослушивает входные данные, которые вы вводите в командную строку.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="cfaf0-131">Создание SparkSession</span><span class="sxs-lookup"><span data-stu-id="cfaf0-131">Create a SparkSession</span></span>

1. <span data-ttu-id="cfaf0-132">Добавьте следующие дополнительные инструкции `using` в начало файла *Program.cs* приложения *mySparkStreamingApp*:</span><span class="sxs-lookup"><span data-stu-id="cfaf0-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="cfaf0-133">Добавьте приведенный ниже код в метод `Main`, чтобы создать новый экземпляр `SparkSession`.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="cfaf0-134">Сеанс Spark является точкой входа для программирования Spark через API DataSet и DataFrame.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="cfaf0-135">Вызов созданного выше объекта *spark* позволяет получить доступ к функциям Spark и DataFrame в любом месте вашей программы.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="cfaf0-136">Подключение к потоку с помощью ReadStream()</span><span class="sxs-lookup"><span data-stu-id="cfaf0-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="cfaf0-137">Метод `ReadStream()` возвращает `DataStreamReader` для чтения потоковых данных в виде `DataFrame`.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="cfaf0-138">Включите сведения об узле и порте, чтобы приложение Spark знало, где ожидать данные потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="cfaf0-139">Регистрация определяемой пользователем функции</span><span class="sxs-lookup"><span data-stu-id="cfaf0-139">Register a user-defined function</span></span>

<span data-ttu-id="cfaf0-140">Для выполнения вычислений и анализа данных в приложениях Spark можно использовать *определяемые пользователем функции*.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="cfaf0-141">Добавьте следующий код в метод `Main`, чтобы зарегистрировать определяемую пользователем функцию с именем `udfArray`.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="cfaf0-142">Она обрабатывает каждую строку, полученную из терминала netcat, и создает массив, который содержит исходную строку (в *str*) и объединение исходной строки с длиной этой строки.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="cfaf0-143">Например, если вы введете в терминале netcat строку *Hello World*, итоговый массив будет выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="cfaf0-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="cfaf0-144">array\[0] = Hello world</span><span class="sxs-lookup"><span data-stu-id="cfaf0-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="cfaf0-145">array\[1] = Hello world 11</span><span class="sxs-lookup"><span data-stu-id="cfaf0-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="cfaf0-146">Использование SparkSQL</span><span class="sxs-lookup"><span data-stu-id="cfaf0-146">Use SparkSQL</span></span>

<span data-ttu-id="cfaf0-147">С помощью SparkSQL можно выполнять разные функции с данными, сохраненными в DataFrame.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="cfaf0-148">Достаточно распространен вариант совместного применения определяемых пользователем функций и SparkSQL, чтобы эта функция обрабатывала каждую строку в DataFrame.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="cfaf0-149">Следующий фрагмент кода применяет *udfArray* к каждому значению в DataFrame с представлением строк, считанных из терминала netcat.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="cfaf0-150">Примените метод SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A>, чтобы разместить каждую запись массива в отдельной строке.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="cfaf0-151">Наконец, используйте <xref:Microsoft.Spark.Sql.DataFrame.Select%2A>, чтобы разместить столбцы, созданные в новом экземпляре *arrayDF* DataFrame.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="cfaf0-152">Отображение потока</span><span class="sxs-lookup"><span data-stu-id="cfaf0-152">Display your stream</span></span>

<span data-ttu-id="cfaf0-153">Используйте <xref:Microsoft.Spark.Sql.DataFrame.WriteStream>, чтобы установить характеристики выходных данных, например вывод результатов на консоль и отображение только самых свежих выходных данных.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="cfaf0-154">Выполнение кода</span><span class="sxs-lookup"><span data-stu-id="cfaf0-154">Run your code</span></span>

<span data-ttu-id="cfaf0-155">Структурированная потоковая передача в Spark обрабатывает данные в виде нескольких небольших **пакетов**.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="cfaf0-156">При выполнении программы для ввода данных можно использовать командную строку, в которой вы установили подключение netcat.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="cfaf0-157">После каждого нажатия клавиши ВВОД при вводе в командную строку любых данных Spark запускает определяемую пользователем функцию с пакетом данных, содержащим эти введенные данные.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="cfaf0-158">Использование команды spark-submit для выполнения приложения</span><span class="sxs-lookup"><span data-stu-id="cfaf0-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="cfaf0-159">Запустив новый сеанс netcat, откройте новое окно терминала и выполните команду `spark-submit`, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="cfaf0-160">Не забудьте указать в представленной выше команде фактический путь к JAR-файлу Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="cfaf0-161">Приведенная выше команда также предполагает, что сервер netcat использует порт localhost 9999.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="cfaf0-162">Получение кода</span><span class="sxs-lookup"><span data-stu-id="cfaf0-162">Get the code</span></span>

<span data-ttu-id="cfaf0-163">В этом руководстве используется пример [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs), но на GitHub есть еще три полных примера обработки потока:</span><span class="sxs-lookup"><span data-stu-id="cfaf0-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="cfaf0-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs) вычисляет количество слов в потоке данных из любого источника;</span><span class="sxs-lookup"><span data-stu-id="cfaf0-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="cfaf0-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs) вычисляет количество слов в данных, используя логику управления окнами;</span><span class="sxs-lookup"><span data-stu-id="cfaf0-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="cfaf0-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs) вычисляет количество слов в данных потоковой передачи от Kafka.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="cfaf0-167">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="cfaf0-167">Next steps</span></span>

<span data-ttu-id="cfaf0-168">Переходите к следующему руководстве, чтобы научиться развертывать приложение .NET для Apache Spark в среде Databricks.</span><span class="sxs-lookup"><span data-stu-id="cfaf0-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="cfaf0-169">Учебник. Развертывание приложения .NET для Apache Spark в Databricks</span><span class="sxs-lookup"><span data-stu-id="cfaf0-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
