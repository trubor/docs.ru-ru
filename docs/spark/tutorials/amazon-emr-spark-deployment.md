---
title: Развертывание приложения .NET для Apache Spark в Amazon EMR Spark
description: Узнайте, как развернуть приложение .NET для Apache Spark в Amazon EMR Spark.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a0904b5b692e1c32ba12a685f2c3a3f7d86c2c58
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874060"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Развертывание приложения .NET для Apache Spark в Amazon EMR Spark

В этом руководстве рассматривается развертывание приложения .NET для Apache Spark в Amazon EMR Spark. [Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) — это управляемая кластерная платформа, которая упрощает выполнение систем больших данных в AWS.

Из этого руководства вы узнаете, как выполнять следующие задачи:

> [!div class="checklist"]
>
> * Подготовка Microsoft.Spark.Worker
> * Публикация приложения Spark .NET
> * Развертывание приложения в Amazon EMR Spark
> * Запустите приложение.

> [!Note]
> AWS EMR Spark работает под управлением Linux. Поэтому если вы хотите развернуть приложение в AWS EMR Spark, оно должно быть совместимо с .NET Standard, а для его компиляции необходимо использовать компилятор .NET Core.

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, сделайте следующее:

* Скачайте [интерфейс командной строки AWS](https://aws.amazon.com/cli/).
* Скачайте файл [install-worker.sh](https://github.com/dotnet/spark/blob/main/deployment/install-worker.sh) на локальный компьютер. Это вспомогательный скрипт, который будет использоваться позже для копирования зависимых файлов .NET для Apache Spark в рабочие узлы кластера Spark.

## <a name="prepare-worker-dependencies"></a>Подготовка зависимостей рабочей роли

**Microsoft.Spark.Worker** — это серверный компонент, который размещается в отдельных рабочих узлах кластера Spark. Если вам нужно выполнить определяемую пользователем функцию C#, Spark необходимо знать, как запустить среду CLR .NET для выполнения этой функции. **Microsoft.Spark.Worker** предоставляет Spark коллекцию классов, которые обеспечивают такую возможность.

1. Выберите выпуск netcoreapp компонента [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) для Linux, который будет развернут в кластере.

   Например, чтобы использовать `.NET for Apache Spark v1.0.0` с `netcoreapp3.1`, скачайте выпуск [Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).

2. Передайте файлы `Microsoft.Spark.Worker.<release>.tar.gz` и [install-worker.sh](https://github.com/dotnet/spark/blob/main/deployment/install-worker.sh) в распределенную файловую систему (например, S3), к которой есть доступ у кластера.

## <a name="prepare-your-net-for-apache-spark-app"></a>Подготовка приложения .NET для Apache Spark

1. Выполните сборку приложения согласно инструкциям из [руководства по началу работы](get-started.md).

2. Опубликуйте приложение .NET для Spark как автономное.

   Выполните приведенную ниже команду в Linux.

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

3. Создайте `<your app>.zip` для опубликованных файлов.

   Выполните приведенную ниже команду в Linux с помощью `zip`.

   ```bash
   zip -r <your app>.zip .
   ```

4. Передайте в распределенную файловую систему (например, S3), к которой есть доступ у кластера, следующие объекты:

   * `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: Этот JAR-файл входит в состав пакета NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) и размещается в выходном каталоге сборки приложения.
   * `<your app>.zip`
   * Файлы (например, файлы зависимостей или общие данные, доступные каждой рабочей роли) или сборки (например, библиотеки DLL, содержащие определяемые пользователем функции, или библиотеки, от которых зависит приложение), которые необходимо поместить в рабочий каталог каждого исполнителя.

## <a name="deploy-to-amazon-emr-spark"></a>Развертывание в Amazon EMR Spark

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) — это управляемая кластерная платформа, которая упрощает выполнение систем больших данных в AWS.

> [!NOTE]
> Amazon EMR Spark работает под управлением Linux. Поэтому если вы хотите развернуть приложение в Amazon EMR Spark, оно должно быть совместимо с .NET Standard, а для его компиляции необходимо использовать [компилятор .NET Core](https://dotnet.microsoft.com/download).

### <a name="deploy-microsoftsparkworker"></a>Развертывание Microsoft.Spark.Worker

Этот шаг необходимо выполнить только при создании кластера.

Выполните скрипт `install-worker.sh` во время создания кластера с помощью [действий начальной загрузки](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).

Выполните приведенную ниже команду в Linux с помощью интерфейса командной строки AWS.

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>Запустите приложение.

Приложение можно запускать в Amazon EMR Spark двумя способами: с помощью команды spark-submit или с помощью шагов Amazon EMR.

### <a name="use-spark-submit"></a>Использование команды spark-submit

Для отправки заданий .NET для Apache Spark в Amazon EMR Spark можно использовать команду [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html).

1. Подключитесь к одному из узлов кластера с помощью команды `ssh`.

2. Выполните `spark-submit`.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Использование шагов Amazon EMR

[Шаги Amazon EMR](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) можно использовать для отправки заданий в платформу Spark, установленную в кластере EMR.

Выполните приведенную ниже команду в Linux с помощью интерфейса командной строки AWS.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы развернули приложение .NET для Apache Spark в Amazon EMR Spark. Примеры проектов .NET для Apache Spark можно найти в GitHub.

> [!div class="nextstepaction"]
> [Примеры .NET для Apache Spark](https://github.com/dotnet/spark/tree/main/examples)
