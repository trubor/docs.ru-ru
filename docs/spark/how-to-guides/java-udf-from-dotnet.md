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
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a>Вызов определяемой пользователем функции Java из приложения .NET для Apache Spark

Из этой статьи вы узнаете, как вызвать определяемую пользователем функцию (UDF) Java из [приложения .NET для Apache Spark](https://github.com/dotnet/spark).

1. Определение UDF Java и их компиляция в JAR-файл — этот шаг не требуется, если у вас уже определена UDF в файле JAR. В этом случае все, что нужно, — это полное имя функции UDF, включая пакет.
2. Регистрация и вызов определяемой пользователем функции Java в приложении .NET для Apache Spark.

## <a name="define-and-compile-your-java-udfs"></a>Определение и компиляция UDF Java

1. Создайте проект Maven или SBT и добавьте следующие зависимости в файл конфигурации проекта:
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. Определите UDF Java, реализовав [соответствующий интерфейс](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (в соответствии с сигнатурой UDF) и импортировав соответствующий пакет, как показано ниже, в простом примере.

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

3. Скомпилируйте и упакуйте проект, чтобы создать и исполняемый файл JAR, например `UdfApp-0.0.1.jar`.

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a>Регистрация и вызов определяемых пользователем функций Java в .NET для Apache Spark

1. Используйте API [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424), чтобы зарегистрировать определяемую пользователем функцию Java с помощью Spark SQL.
2. Зарегистрируйте `DataFrame`, для которой необходимо вызвать определяемую пользователем функцию в виде таблицы SQL с помощью функции [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982).
3. Используйте `SparkSession.Sql` для вызова определяемой пользователем функции в табличном представлении с помощью Spark SQL.
Базовый пример, иллюстрирующий описанные выше шаги.

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

4. Отправьте это приложение с помощью `spark-submit`, передав ранее скомпилированный JAR-файл UDF Java с помощью параметра `--jars`:

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-2-4_2.11-1.0.0.jar InterRuntimeUDFs.exe
    ```

    Результирующий кадр данных `dfUdf` содержал число 5, добавленное в каждую строку входного столбца, как определено `JavaUdf`:

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a>Вызов UDF .NET из Scala или Python в Apache Spark

Вы также можете зарегистрировать и вызвать определяемую пользователем функцию C# из приложения Apache Spark, написанного на Scala или Python, с помощью [средства sparkdotnetudf с открытым исходным кодом](https://github.com/imback82/sparkdotnetudf).
