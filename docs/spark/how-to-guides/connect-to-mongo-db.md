---
title: Подключение .NET для Apache Spark к MongoDB
description: Узнайте, как подключиться к экземпляру MongoDB из приложения .NET для Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 3889088ce32046f72a9a3392e28a5a36cda4745e
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957849"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a><span data-ttu-id="94e57-103">Подключение .NET для Apache Spark к MongoDB</span><span class="sxs-lookup"><span data-stu-id="94e57-103">Connect .NET for Apache Spark to MongoDB</span></span>

<span data-ttu-id="94e57-104">Из этой статьи вы узнаете, как подключиться к экземпляру MongoDB из приложения .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="94e57-104">In this article, you learn how to connect to a MongoDB instance from your .NET for Apache Spark application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94e57-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="94e57-105">Prerequisites</span></span>

- <span data-ttu-id="94e57-106">Настройте и запустите сервер MongoDB с базой данных [ и коллекцией ](https://docs.mongodb.com/manual/core/databases-and-collections/) (скачайте [этот сервер сообщества](https://www.mongodb.com/try/download/community) для локального сервера, либо можно попробовать использовать [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) для облачной службы MongoDB).</span><span class="sxs-lookup"><span data-stu-id="94e57-106">Have a MongoDB server up and running with a [database and some collection](https://docs.mongodb.com/manual/core/databases-and-collections/) added to it (Download [this community server](https://www.mongodb.com/try/download/community) for a local server or you can try [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) for a cloud MongoDB service.)</span></span>

## <a name="set-up-your-mongodb-instance"></a><span data-ttu-id="94e57-107">Настройка экземпляра MongoDB</span><span class="sxs-lookup"><span data-stu-id="94e57-107">Set up your MongoDB instance</span></span>

<span data-ttu-id="94e57-108">Чтобы организовать взаимодействие .NET для Apache Spark с экземпляром MongoDB, необходимо убедиться, что он правильно настроен, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="94e57-108">In order to get .NET for Apache Spark to talk to your MongoDB instance you need to make sure it is set up correctly by doing the following:</span></span>

1. <span data-ttu-id="94e57-109">Создайте имя пользователя и пароль для подключения к приложению и предоставьте пользователю необходимые разрешения или роли с помощью следующей команды через оболочку mongo:</span><span class="sxs-lookup"><span data-stu-id="94e57-109">Create a username and password for your application to connect through, and give the user the necessary permissions/roles using the following command through mongo shell:</span></span>

    ```bash
    use database
    db.createUser(
      {
        user: "mySparkUser",
        pwd: "<password>",
        roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
      }
    )
    ```

2. <span data-ttu-id="94e57-110">Убедитесь, что IP-адрес компьютера, на котором запущено приложение .NET для Apache Spark, находится в списке разрешенных, чтобы сервер MongoDB мог подключиться к нему.</span><span class="sxs-lookup"><span data-stu-id="94e57-110">Make sure the IP address of the machine your .NET for Apache Spark application is running on is allowlisted for the MongoDB server to be able to connect to.</span></span> <span data-ttu-id="94e57-111">Подробнее см. в [этом руководстве](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/).</span><span class="sxs-lookup"><span data-stu-id="94e57-111">You can refer to [this guide](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) to learn how to do that.</span></span>

## <a name="configure-your-net-for-apache-spark-application"></a><span data-ttu-id="94e57-112">Настройка приложения .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="94e57-112">Configure your .NET for Apache Spark application</span></span>

1. <span data-ttu-id="94e57-113">Задайте следующие переменные, чтобы настроить приложение для взаимодействия с экземпляром MongoDB и чтения из коллекции.</span><span class="sxs-lookup"><span data-stu-id="94e57-113">Have the following variables set to configure your application to talk to the MongoDB instance and read from a collection.</span></span>
    1. <span data-ttu-id="94e57-114">**authURI**: "Строка подключения, разрешающая приложению подключаться к требуемому экземпляру MongoDB".</span><span class="sxs-lookup"><span data-stu-id="94e57-114">**authURI**: "Connection string authorizing your application to connect to the required MongoDB instance".</span></span> <span data-ttu-id="94e57-115">Формат строки подключения:</span><span class="sxs-lookup"><span data-stu-id="94e57-115">The format for that is as follows:</span></span>

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. <span data-ttu-id="94e57-116">**username**: имя пользователя учетной записи, созданной на шаге 1 предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="94e57-116">**username**: Username of the account you created in Step 1 of the previous section</span></span>
    3. <span data-ttu-id="94e57-117">**password**: пароль учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="94e57-117">**password**: Password of the user account created</span></span>
    4. <span data-ttu-id="94e57-118">**cluster_address**: имя узла/адрес кластера MongoDB</span><span class="sxs-lookup"><span data-stu-id="94e57-118">**cluster_address**: hostname/address of your MongoDB cluster</span></span>
    5. <span data-ttu-id="94e57-119">**database**: база данных MongoDB, к которой необходимо подключиться</span><span class="sxs-lookup"><span data-stu-id="94e57-119">**database**: The MongoDB database you want to connect to</span></span>
    6. <span data-ttu-id="94e57-120">**collection**: коллекция MongoDB, которую необходимо прочитать.</span><span class="sxs-lookup"><span data-stu-id="94e57-120">**collection**: The MongoDB collection you want to read.</span></span> <span data-ttu-id="94e57-121">(Здесь используется стандартный пример файла [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json), поставляемого в комплекте каждой установки Apache Spark.)</span><span class="sxs-lookup"><span data-stu-id="94e57-121">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.)</span></span>

2. <span data-ttu-id="94e57-122">Используйте формат `com.mongodb.spark.sql.DefaultSource` (`spark.Read()`), как показано ниже в простом фрагменте кода:</span><span class="sxs-lookup"><span data-stu-id="94e57-122">Use the `com.mongodb.spark.sql.DefaultSource` format is `spark.Read()` as shown below in a simple code snippet:</span></span>

    ```csharp
    class Program
    {
        static void Main()
        {
            var authURI = "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>?retryWrites=true&w=majority";
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Connect to Mongo DB example")
                .Config("spark.mongodb.input.uri", authURI)
                .GetOrCreate();

            DataFrame df = spark.Read().Format("com.mongodb.spark.sql.DefaultSource").Load();
            df.PrintSchema();
            df.Show();
            spark.Stop();
        }
    }
    ```

## <a name="run-your-application"></a><span data-ttu-id="94e57-123">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="94e57-123">Run your application</span></span>

<span data-ttu-id="94e57-124">Чтобы запустить приложение .NET для Apache Spark, определите модуль `mongo-spark-connector` как часть определения сборки в проекте Spark, используя `libraryDependency` в `build.sbt` для проектов sbt.</span><span class="sxs-lookup"><span data-stu-id="94e57-124">In order to run your .NET for Apache Spark application, you should define the `mongo-spark-connector` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="94e57-125">Для сред Spark, таких как `spark-submit` (или `spark-shell`), используйте параметр командной строки `--packages` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="94e57-125">For Spark environments such as `spark-submit` (or `spark-shell`), use the `--packages` command-line option like so:</span></span>

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar yourApp.exe
```

> [!NOTE]
> <span data-ttu-id="94e57-126">Убедитесь, что включили версию пакета, соответствующую используемой версии Spark.</span><span class="sxs-lookup"><span data-stu-id="94e57-126">Make sure to include the package version in accordance with the version of Spark being run.</span></span>

<span data-ttu-id="94e57-127">В результате отображается кадр данных (`df`), как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="94e57-127">The result as displayed is the DataFrame (`df`) shown here:</span></span>

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
