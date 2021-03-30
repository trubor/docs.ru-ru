---
title: Вызов определяемых пользователем функций Java из приложения .NET для Apache Spark
description: Узнайте, как вызвать UDF Java из приложения .NET для Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f85ed5585c8daef0ca9a21275b8de71b2eead360
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875490"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a><span data-ttu-id="a59f2-103">Вызов определяемой пользователем функции Java из приложения .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a59f2-103">Call a Java UDF from your .NET for Apache Spark application</span></span>

<span data-ttu-id="a59f2-104">Из этой статьи вы узнаете, как вызвать определяемую пользователем функцию (UDF) Java из [приложения .NET для Apache Spark](https://github.com/dotnet/spark).</span><span class="sxs-lookup"><span data-stu-id="a59f2-104">In this article, you learn how to call a Java User-Defined Function (UDF) from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

1. <span data-ttu-id="a59f2-105">Определение UDF Java и их компиляция в JAR-файл — этот шаг не требуется, если у вас уже определена UDF в файле JAR.</span><span class="sxs-lookup"><span data-stu-id="a59f2-105">How to define your Java UDFs and compile them into a jar - this step is not needed if you already have a UDF defined in a jar file.</span></span> <span data-ttu-id="a59f2-106">В этом случае все, что нужно, — это полное имя функции UDF, включая пакет.</span><span class="sxs-lookup"><span data-stu-id="a59f2-106">In which case, all you need is the full name of the UDF function including the package.</span></span>
2. <span data-ttu-id="a59f2-107">Регистрация и вызов определяемой пользователем функции Java в приложении .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="a59f2-107">Register and call your Java UDF in your .NET for Apache Spark application.</span></span>

## <a name="define-and-compile-your-java-udfs"></a><span data-ttu-id="a59f2-108">Определение и компиляция UDF Java</span><span class="sxs-lookup"><span data-stu-id="a59f2-108">Define and compile your Java UDFs</span></span>

1. <span data-ttu-id="a59f2-109">Создайте проект Maven или SBT и добавьте следующие зависимости в файл конфигурации проекта:</span><span class="sxs-lookup"><span data-stu-id="a59f2-109">Create a Maven or SBT project and add the following dependencies into the project configuration file:</span></span>
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. <span data-ttu-id="a59f2-110">Определите UDF Java, реализовав [соответствующий интерфейс](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (в соответствии с сигнатурой UDF) и импортировав соответствующий пакет, как показано ниже, в простом примере.</span><span class="sxs-lookup"><span data-stu-id="a59f2-110">Define your Java UDF by implementing the [relevant interface](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (according to your UDF's signature) and importing the relevant package as shown below in a simple example</span></span>

    ```java
    package com.ScalaUdf.app; // Name of package where UDF is defined
    import org.apache.spark.sql.api.java.UDF1; // UDF interface to implement

    public class JavaUdf implements UDF1<Integer, Integer> { // Name of the Java UDF
        private static final int serialVersionUID = 1;
        @Override
        public Integer call(Integer num) throws Exception { // Define logic of UDF
            return (num + 5);
        }
    }
    ```

3. <span data-ttu-id="a59f2-111">Скомпилируйте и упакуйте проект, чтобы создать и исполняемый файл JAR, например `UdfApp-0.0.1.jar`.</span><span class="sxs-lookup"><span data-stu-id="a59f2-111">Compile and package your project to create and executable jar say `UdfApp-0.0.1.jar`.</span></span>

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a><span data-ttu-id="a59f2-112">Регистрация и вызов определяемых пользователем функций Java в .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a59f2-112">Register and call Java UDFs in .NET for Apache Spark</span></span>

1. <span data-ttu-id="a59f2-113">Используйте API [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424), чтобы зарегистрировать определяемую пользователем функцию Java с помощью Spark SQL.</span><span class="sxs-lookup"><span data-stu-id="a59f2-113">Use the [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API to register your Java UDF with Spark SQL.</span></span>
2. <span data-ttu-id="a59f2-114">Зарегистрируйте `DataFrame`, для которой необходимо вызвать определяемую пользователем функцию в виде таблицы SQL с помощью функции [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982).</span><span class="sxs-lookup"><span data-stu-id="a59f2-114">Register the `DataFrame` on which you want to call your UDF as an SQL Table using the [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) function.</span></span>
3. <span data-ttu-id="a59f2-115">Используйте `SparkSession.Sql` для вызова определяемой пользователем функции в табличном представлении с помощью Spark SQL.</span><span class="sxs-lookup"><span data-stu-id="a59f2-115">Use `SparkSession.Sql` to call the UDF on the table view using Spark SQL.</span></span>
<span data-ttu-id="a59f2-116">Базовый пример, иллюстрирующий описанные выше шаги.</span><span class="sxs-lookup"><span data-stu-id="a59f2-116">A basic example to illustrate the above steps:</span></span>

    ```csharp
    class Program
    {
        static void Main()
        {
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Scala/Java UDFs from .NET for Apache Spark")
                .GetOrCreate();
            spark.Udf().RegisterJava<int>("udfAdd5", "com.ScalaUdf.app.JavaUdf"); // Register your Java UDF as 'udfAdd5'
            DataFrame df = spark.CreateDataFrame(new int[] { 2, 5 });
            df.CreateOrReplaceTempView("numbersData"); // Create an SQL table from the DataFrame `df`
            DataFrame dfUdf = spark.Sql("SELECT udfAdd5(_1) As Result FROM numbersData"); // Call the registered UDF on the table
            dfUdf.Show();
            spark.Stop();
        }
    }
    ```

4. <span data-ttu-id="a59f2-117">Отправьте это приложение с помощью `spark-submit`, передав ранее скомпилированный JAR-файл UDF Java с помощью параметра `--jars`:</span><span class="sxs-lookup"><span data-stu-id="a59f2-117">Submit this application using `spark-submit` by passing the previously compiled Java UDF jar through the `--jars` option:</span></span>

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-2-4_2.11-1.0.0.jar InterRuntimeUDFs.exe
    ```

    <span data-ttu-id="a59f2-118">Результирующий кадр данных `dfUdf` содержал число 5, добавленное в каждую строку входного столбца, как определено `JavaUdf`:</span><span class="sxs-lookup"><span data-stu-id="a59f2-118">The resultant `dfUdf` DataFrame had the number 5 added to each row of the input column as defined by `JavaUdf`:</span></span>

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a><span data-ttu-id="a59f2-119">Вызов UDF .NET из Scala или Python в Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a59f2-119">Call .NET UDF from Scala or Python in Apache Spark</span></span>

<span data-ttu-id="a59f2-120">Вы также можете зарегистрировать и вызвать определяемую пользователем функцию C# из приложения Apache Spark, написанного на Scala или Python, с помощью [средства sparkdotnetudf с открытым исходным кодом](https://github.com/imback82/sparkdotnetudf).</span><span class="sxs-lookup"><span data-stu-id="a59f2-120">You can also register and invoke a C# UDF from an Apache Spark application written in Scala or Python using [the sparkdotnetudf open source tool](https://github.com/imback82/sparkdotnetudf).</span></span>
