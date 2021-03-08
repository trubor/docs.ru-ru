---
title: Начало работы с .NET для Apache Spark
description: Узнайте, как запустить приложение .NET для Apache Spark, используя .NET Core на Windows, macOS и Ubuntu.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 44859d1c4819853c07454429e8a83f1fbb2e3af5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103664"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="8522c-103">Учебник. Начало работы с .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8522c-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="8522c-104">В этом руководстве описывается, как запустить приложение .NET для Apache Spark, используя .NET Core на Windows, macOS и Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="8522c-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, macOS, and Ubuntu.</span></span>

<span data-ttu-id="8522c-105">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="8522c-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="8522c-106">подготовить среду под .NET для Apache Spark;</span><span class="sxs-lookup"><span data-stu-id="8522c-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="8522c-107">написать свое первое приложение .NET для Apache Spark;</span><span class="sxs-lookup"><span data-stu-id="8522c-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="8522c-108">скомпилировать и запустить приложение .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-108">Build and run your .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="8522c-109">Подготовка среды</span><span class="sxs-lookup"><span data-stu-id="8522c-109">Prepare your environment</span></span>

<span data-ttu-id="8522c-110">Прежде чем приступить к написанию приложения, нужно настроить некоторые необходимые зависимости.</span><span class="sxs-lookup"><span data-stu-id="8522c-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="8522c-111">Если вы можете выполнить `dotnet`, `java`, `spark-shell` из среды командной строки, то ваша среда уже подготовлена, и вы можете перейти к следующему разделу.</span><span class="sxs-lookup"><span data-stu-id="8522c-111">If you can run `dotnet`, `java`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="8522c-112">Если эти команды или хотя бы одну из них выполнить не получается, сделайте следующее.</span><span class="sxs-lookup"><span data-stu-id="8522c-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="8522c-113">1. Установка .NET</span><span class="sxs-lookup"><span data-stu-id="8522c-113">1. Install .NET</span></span>

<span data-ttu-id="8522c-114">Чтобы приступить к созданию приложений .NET, необходимо загрузить и установить пакет средств разработки программного обеспечения (SDK) для .NET.</span><span class="sxs-lookup"><span data-stu-id="8522c-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="8522c-115">Скачайте и установите [пакет SDK для .NET Core](https://dotnet.microsoft.com/download/dotnet/3.1).</span><span class="sxs-lookup"><span data-stu-id="8522c-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet/3.1).</span></span> <span data-ttu-id="8522c-116">При установке пакета SDK в переменную PATH добавляется цепочка инструментов `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="8522c-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="8522c-117">Установив пакет SDK для .NET Core, откройте новое окно командной строки или терминала и выполните команду `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="8522c-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="8522c-118">Если команда выполняется и выводит сведения об использовании dotnet, можно перейти к следующему шагу.</span><span class="sxs-lookup"><span data-stu-id="8522c-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="8522c-119">Если возникает ошибка `'dotnet' is not recognized as an internal or external command`, убедитесь, что команда выполняется в **новом** окне терминала или командной строки.</span><span class="sxs-lookup"><span data-stu-id="8522c-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="8522c-120">2. Установка Java</span><span class="sxs-lookup"><span data-stu-id="8522c-120">2. Install Java</span></span>

<span data-ttu-id="8522c-121">Установите [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) для Windows и macOS или [OpenJDK 8](https://openjdk.java.net/install/) для Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="8522c-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and macOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="8522c-122">Выберите соответствующую версию для вашей операционной системы.</span><span class="sxs-lookup"><span data-stu-id="8522c-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="8522c-123">Например, выберите **jdk-8u201-windows-x64.exe** для компьютера с 64-разрядной версией Windows (как показано ниже) или **jdk-8u231-macosx-x64.dmg** для macOS.</span><span class="sxs-lookup"><span data-stu-id="8522c-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for macOS.</span></span> <span data-ttu-id="8522c-124">Затем используйте команду `java`, чтобы проверить установку.</span><span class="sxs-lookup"><span data-stu-id="8522c-124">Then, use the command `java` to verify the installation.</span></span>

![Скачать Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="8522c-126">3. Установка ПО для сжатия</span><span class="sxs-lookup"><span data-stu-id="8522c-126">3. Install compression software</span></span>

<span data-ttu-id="8522c-127">Apache Spark загружается как сжатый файл TGZ.</span><span class="sxs-lookup"><span data-stu-id="8522c-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="8522c-128">Чтобы извлечь файл, используйте программу-архиватор, например [7-Zip](https://www.7-zip.org/) или [WinZip](https://www.winzip.com/).</span><span class="sxs-lookup"><span data-stu-id="8522c-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="8522c-129">4. Установка Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8522c-129">4. Install Apache Spark</span></span>

<span data-ttu-id="8522c-130">[Скачайте и установите Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="8522c-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="8522c-131">Вам потребуется выбрать одну из следующих версий: 2.3.\* либо 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 или 3.0.1 (.NET для Apache Spark несовместима с другими версиями Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="8522c-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0, or 3.0.1 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="8522c-132">Команды, используемые на следующих этапах, подразумевают, что [скачана и установлена версия Apache Spark 3.0.1](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="8522c-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 3.0.1](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="8522c-133">Если вы хотите использовать другую версию, замените **3.0.1** на соответствующий номер версии.</span><span class="sxs-lookup"><span data-stu-id="8522c-133">If you wish to use a different version, replace **3.0.1** with the appropriate version number.</span></span> <span data-ttu-id="8522c-134">Затем извлеките файл **TAR** и файлы Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="8522c-135">Чтобы извлечь вложенный файл **TAR**:</span><span class="sxs-lookup"><span data-stu-id="8522c-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="8522c-136">Найдите скачанный файл **spark-3.0.1-bin-hadoop2.7.tgz**.</span><span class="sxs-lookup"><span data-stu-id="8522c-136">Locate the **spark-3.0.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="8522c-137">Щелкните файл правой кнопкой мыши и выберите **7-Zip -> Извлечь сюда**.</span><span class="sxs-lookup"><span data-stu-id="8522c-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="8522c-138">**spark-3.0.1-bin-hadoop2.7.tar** будет создан рядом со скачанным файлом **TGZ**.</span><span class="sxs-lookup"><span data-stu-id="8522c-138">**spark-3.0.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="8522c-139">Чтобы извлечь файлы Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="8522c-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="8522c-140">Щелкните правой кнопкой мыши **spark-3.0.1-bin-hadoop2.7.tar** и выберите **7-Zip -> Извлечь файлы...**</span><span class="sxs-lookup"><span data-stu-id="8522c-140">Right-click on **spark-3.0.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="8522c-141">Введите **C:\bin** в поле **Извлечь в**.</span><span class="sxs-lookup"><span data-stu-id="8522c-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="8522c-142">Снимите флажок под полем **Извлечь в**.</span><span class="sxs-lookup"><span data-stu-id="8522c-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="8522c-143">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="8522c-143">Select **OK**.</span></span>
* <span data-ttu-id="8522c-144">Файлы Apache Spark будут извлечены в папку C:\bin\spark-3.0.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="8522c-144">The Apache Spark files are extracted to C:\bin\spark-3.0.1-bin-hadoop2.7</span></span>\

![Установка Spark](./media/spark-extract-with-7-zip.png)

<span data-ttu-id="8522c-146">Выполните следующие команды, чтобы задать переменные среды, используемые для размещения Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-146">Run the following commands to set the environment variables used to locate Apache Spark.</span></span> <span data-ttu-id="8522c-147">В Windows обязательно запускайте командную строку от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="8522c-147">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="8522c-148">Windows</span><span class="sxs-lookup"><span data-stu-id="8522c-148">Windows</span></span>](#tab/windows)

```console
setx /M HADOOP_HOME C:\bin\spark-3.0.1-bin-hadoop2.7\
setx /M SPARK_HOME C:\bin\spark-3.0.1-bin-hadoop2.7\
setx /M PATH "%PATH%;%HADOOP_HOME%;%SPARK_HOME%\bin" # Warning: Don't run this if your path is already long as it will truncate your path to 1024 characters and potentially remove entries!
```

#### <a name="maclinux"></a>[<span data-ttu-id="8522c-149">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="8522c-149">Mac/Linux</span></span>](#tab/linux)

```bash
export SPARK_HOME=~/bin/spark-3.0.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

---

<span data-ttu-id="8522c-150">Установив все необходимое и задав переменные сред, откройте **новое** окно командной строки или терминала и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8522c-150">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

```text
spark-submit --version
```

<span data-ttu-id="8522c-151">Если команда выполняется и выводит сведения о версии, можно перейти к следующему шагу.</span><span class="sxs-lookup"><span data-stu-id="8522c-151">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="8522c-152">При возникновении ошибки `'spark-submit' is not recognized as an internal or external command` убедитесь, что вы открыли **новую** командную строку.</span><span class="sxs-lookup"><span data-stu-id="8522c-152">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="8522c-153">5. Установка .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8522c-153">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="8522c-154">Загрузите выпуск [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) со страницы выпусков .NET для Apache Spark в GitHub.</span><span class="sxs-lookup"><span data-stu-id="8522c-154">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="8522c-155">Например, если вы планируете использовать .NET Core на компьютере под управлением Windows, [скачайте выпуск netcoreapp3.1 для Windows x64](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="8522c-155">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases).</span></span>

<span data-ttu-id="8522c-156">Для извлечения Microsoft.Spark.Worker:</span><span class="sxs-lookup"><span data-stu-id="8522c-156">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="8522c-157">Найдите скачанный файл **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-1.0.0.zip**.</span><span class="sxs-lookup"><span data-stu-id="8522c-157">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-1.0.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="8522c-158">Щелкните правой кнопкой мыши и выберите **7-Zip -> Извлечь файлы**.</span><span class="sxs-lookup"><span data-stu-id="8522c-158">Right-click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="8522c-159">Введите **C:\bin** в поле **Извлечь в**.</span><span class="sxs-lookup"><span data-stu-id="8522c-159">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="8522c-160">Снимите флажок под полем **Извлечь в**.</span><span class="sxs-lookup"><span data-stu-id="8522c-160">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="8522c-161">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="8522c-161">Select **OK**.</span></span>

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="8522c-162">6.  Установка WinUtils (только для Windows)</span><span class="sxs-lookup"><span data-stu-id="8522c-162">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="8522c-163">.NET для Apache Spark требует установки WinUtils вместе с Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-163">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="8522c-164">[Скачайте winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="8522c-164">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="8522c-165">Затем скопируйте WinUtils в папку **C:\bin\spark-3.0.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="8522c-165">Then, copy WinUtils into **C:\bin\spark-3.0.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="8522c-166">Если вы используете другую версию Hadoop, которая указывается в конце имени папки установки Spark, [выберите версию WinUtils](https://github.com/steveloughran/winutils), совместимую с вашей версией Hadoop.</span><span class="sxs-lookup"><span data-stu-id="8522c-166">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="8522c-167">7. Установка DOTNET_WORKER_DIR и проверка зависимостей</span><span class="sxs-lookup"><span data-stu-id="8522c-167">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="8522c-168">Выполните одну из следующих команд, чтобы задать переменную среды `DOTNET_WORKER_DIR`, которая используется приложениями .NET для обнаружения .NET для двоичных файлов рабочих ролей Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-168">Run one of the following commands to set the `DOTNET_WORKER_DIR` environment variable, which is used by .NET apps to locate .NET for Apache Spark worker binaries.</span></span> <span data-ttu-id="8522c-169">Обязательно замените `<PATH-DOTNET_WORKER_DIR>` каталогом, который вы использовали для скачивания и распаковки `Microsoft.Spark.Worker`.</span><span class="sxs-lookup"><span data-stu-id="8522c-169">Make sure to replace `<PATH-DOTNET_WORKER_DIR>` with the directory where you downloaded and extracted the `Microsoft.Spark.Worker`.</span></span> <span data-ttu-id="8522c-170">В Windows обязательно запускайте командную строку от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="8522c-170">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="8522c-171">Windows</span><span class="sxs-lookup"><span data-stu-id="8522c-171">Windows</span></span>](#tab/windows)

```console
setx /M DOTNET_WORKER_DIR <PATH-DOTNET-WORKER-DIR>
```

#### <a name="maclinux"></a>[<span data-ttu-id="8522c-172">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="8522c-172">Mac/Linux</span></span>](#tab/linux)

```bash
export DOTNET_WORKER_DIR=<PATH-DOTNET-WORKER-DIR>
```

---

<span data-ttu-id="8522c-173">Наконец, перед переходом к следующему разделу еще раз проверьте, можно ли выполнить команды `dotnet`, `java`, `spark-shell` из командной строки.</span><span class="sxs-lookup"><span data-stu-id="8522c-173">Finally, double-check that you can run `dotnet`, `java`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="8522c-174">Написание приложения .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8522c-174">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="8522c-175">1. Создание консольного приложения</span><span class="sxs-lookup"><span data-stu-id="8522c-175">1. Create a console app</span></span>

<span data-ttu-id="8522c-176">В командной строке или терминале выполните следующие команды, чтобы создать новое консольное приложение:</span><span class="sxs-lookup"><span data-stu-id="8522c-176">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o MySparkApp
cd MySparkApp
```

<span data-ttu-id="8522c-177">Команда `dotnet` создаст для вас приложение `new` типа `console`.</span><span class="sxs-lookup"><span data-stu-id="8522c-177">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="8522c-178">Параметр `-o` создаст каталог с именем *MySparkApp*, в котором хранится приложение и используемые им файлы.</span><span class="sxs-lookup"><span data-stu-id="8522c-178">The `-o` parameter creates a directory named *MySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="8522c-179">Команда `cd MySparkApp` изменит каталог на созданный каталог приложения.</span><span class="sxs-lookup"><span data-stu-id="8522c-179">The `cd MySparkApp` command changes the directory to the app directory you created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="8522c-180">2. Установка пакета NuGet</span><span class="sxs-lookup"><span data-stu-id="8522c-180">2. Install NuGet package</span></span>

<span data-ttu-id="8522c-181">Чтобы использовать .NET для Apache Spark в приложении, установите пакет Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-181">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="8522c-182">В командной строке или терминале выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8522c-182">In your command prompt or terminal, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.Spark
```

> [!NOTE]
> <span data-ttu-id="8522c-183">Для работы с этим руководством используйте последнюю версию пакета NuGet `Microsoft.Spark` (если не указано иное).</span><span class="sxs-lookup"><span data-stu-id="8522c-183">This tutorial uses the latest version of the `Microsoft.Spark` NuGet package unless otherwise specified.</span></span>

### <a name="3-write-your-app"></a><span data-ttu-id="8522c-184">3. Написание приложения</span><span class="sxs-lookup"><span data-stu-id="8522c-184">3. Write your app</span></span>

<span data-ttu-id="8522c-185">Откройте *Program.cs* в Visual Studio Code или любом текстовом редакторе и замените весь код следующим:</span><span class="sxs-lookup"><span data-stu-id="8522c-185">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;
using static Microsoft.Spark.Sql.Functions;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create Spark session
            SparkSession spark =
                SparkSession
                    .Builder()
                    .AppName("word_count_sample")
                    .GetOrCreate();

            // Create initial DataFrame
            string filePath = args[0];
            DataFrame dataFrame = spark.Read().Text(filePath);

            //Count words
            DataFrame words =
                dataFrame
                    .Select(Split(Col("value")," ").Alias("words"))
                    .Select(Explode(Col("words")).Alias("word"))
                    .GroupBy("word")
                    .Count()
                    .OrderBy(Col("count").Desc());

            // Display results
            words.Show();

            // Stop Spark session
            spark.Stop();
        }
    }
}
```

<span data-ttu-id="8522c-186">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) — это точка входа приложений Apache Spark, которая управляет контекстом и сведениями о приложении.</span><span class="sxs-lookup"><span data-stu-id="8522c-186">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) is the entrypoint of Apache Spark applications, which manages the context and information of your application.</span></span> <span data-ttu-id="8522c-187">С помощью метода [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) текстовые данные из файла, указанного с помощью параметра `filePath`, считываются в [DataFrame](xref:Microsoft.Spark.Sql.DataFrame).</span><span class="sxs-lookup"><span data-stu-id="8522c-187">Using the [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) method, the text data from the file specified by the `filePath` is read into a [DataFrame](xref:Microsoft.Spark.Sql.DataFrame).</span></span> <span data-ttu-id="8522c-188">DataFrame представляет способ упорядочивания данных в набор именованных столбцов.</span><span class="sxs-lookup"><span data-stu-id="8522c-188">A DataFrame is a way of organizing data into a set of named columns.</span></span> <span data-ttu-id="8522c-189">Над ними затем выполняется серия преобразований для разделения предложений в файле, определения каждого слова в группу, подсчета слов и упорядочивания их в порядке убывания.</span><span class="sxs-lookup"><span data-stu-id="8522c-189">Then, a series of transformations is applied to split the sentences in the file, group each of the words, count them and order them in descending order.</span></span> <span data-ttu-id="8522c-190">Результат этих операций хранится в другом DataFrame.</span><span class="sxs-lookup"><span data-stu-id="8522c-190">The result of these operations is stored in another DataFrame.</span></span> <span data-ttu-id="8522c-191">Обратите внимание, что на этом этапе операции не выполнялись, так как .NET для Apache Spark оценивает данные в отложенном режиме.</span><span class="sxs-lookup"><span data-stu-id="8522c-191">Note that at this point, no operations have taken place because .NET for Apache Spark lazily evaluates the data.</span></span> <span data-ttu-id="8522c-192">Операции, определенные в строках выше, начнут выполняться только после того, как будет вызван метод [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) для отображения содержимого записи `words` преобразованного DataFrame в консоли.</span><span class="sxs-lookup"><span data-stu-id="8522c-192">It's not until the [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) method is called to display the contents of the `words` transformed DataFrame to the console that the operations defined in the lines above execute.</span></span> <span data-ttu-id="8522c-193">Если вы не будете продолжать работу с сеансом Spark, завершите его с помощью метода [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A).</span><span class="sxs-lookup"><span data-stu-id="8522c-193">Once you no longer need the Spark session, use the [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) method to stop your session.</span></span>

### <a name="4-create-data-file"></a><span data-ttu-id="8522c-194">4. Создание файла данных</span><span class="sxs-lookup"><span data-stu-id="8522c-194">4. Create data file</span></span>

<span data-ttu-id="8522c-195">Ваше приложение обрабатывает файл, содержащий строки текста.</span><span class="sxs-lookup"><span data-stu-id="8522c-195">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="8522c-196">В каталоге *MySparkApp* создайте файл *input.txt*, содержащий следующий текст:</span><span class="sxs-lookup"><span data-stu-id="8522c-196">Create a file called *input.txt* file in your *MySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

<span data-ttu-id="8522c-197">Сохраните изменения и закройте файл.</span><span class="sxs-lookup"><span data-stu-id="8522c-197">Save the changes and close the file.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="8522c-198">Запуск приложения .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8522c-198">Run your .NET for Apache Spark app</span></span>

<span data-ttu-id="8522c-199">Запустите сборку приложения с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="8522c-199">Run the following command to build your application:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="8522c-200">Перейдите к каталогу выходных данных сборки и с помощью команды `spark-submit` отправьте приложение для выполнения в Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-200">Navigate to your build output directory and use the `spark-submit` command to submit your application to run on Apache Spark.</span></span> <span data-ttu-id="8522c-201">Обязательно замените `<version>` версией своей рабочей роли .NET, а `<path-of-input.txt>` — путем к вашему сохраненному файлу *input.txt*.</span><span class="sxs-lookup"><span data-stu-id="8522c-201">Make sure to replace  `<version>` with the version of your .NET worker and `<path-of-input.txt>` with the path of your *input.txt* file is stored.</span></span>

### <a name="windows"></a>[<span data-ttu-id="8522c-202">Windows</span><span class="sxs-lookup"><span data-stu-id="8522c-202">Windows</span></span>](#tab/windows)

```console
spark-submit ^
--class org.apache.spark.deploy.dotnet.DotnetRunner ^
--master local ^
microsoft-spark-3-0_2.12-<version>.jar ^
dotnet MySparkApp.dll <path-of-input.txt>
```

### <a name="maclinux"></a>[<span data-ttu-id="8522c-203">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="8522c-203">Mac/Linux</span></span>](#tab/linux)

```bash
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master local \
microsoft-spark-3-0_2.12-<version>.jar \
dotnet MySparkApp.dll <path-of-input.txt>
```

---

> [!NOTE]
> <span data-ttu-id="8522c-204">При выполнении этой команды предполагается, что вы скачали Apache Spark и добавили это решение в переменную среды PATH, чтобы использовать `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="8522c-204">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="8522c-205">В противном случае потребуется использовать полный путь (например, *C:\bin\apache-spark\bin\spark-submit* или *~/spark/bin/spark-submit*).</span><span class="sxs-lookup"><span data-stu-id="8522c-205">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

<span data-ttu-id="8522c-206">При запуске приложения данные подсчета слов из файла *input.txt* записываются в консоль.</span><span class="sxs-lookup"><span data-stu-id="8522c-206">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

```console
+------+-----+
|  word|count|
+------+-----+
|  .NET|    3|
|Apache|    2|
|   app|    2|
|  This|    2|
| Spark|    2|
| World|    1|
|counts|    1|
|   for|    1|
| words|    1|
|  with|    1|
| Hello|    1|
|  uses|    1|
+------+-----+
```

<span data-ttu-id="8522c-207">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="8522c-207">Congratulations!</span></span> <span data-ttu-id="8522c-208">Вы успешно создали и запустили приложение .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-208">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8522c-209">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="8522c-209">Next steps</span></span>

<span data-ttu-id="8522c-210">В этом руководстве вы узнали, как выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="8522c-210">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="8522c-211">подготовить среду под .NET для Apache Spark;</span><span class="sxs-lookup"><span data-stu-id="8522c-211">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="8522c-212">написать свое первое приложение .NET для Apache Spark;</span><span class="sxs-lookup"><span data-stu-id="8522c-212">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="8522c-213">скомпилировать и запустить приложение .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="8522c-213">Build and run your .NET for Apache Spark application</span></span>

<span data-ttu-id="8522c-214">Видео, в котором подробнее объясняются приведенные выше шаги, можно найти в серии видео с [общими сведениями о .NET для Apache Spark](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="8522c-214">To see a video explaining the steps above, check out the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="8522c-215">Дополнительные сведения см. на странице ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8522c-215">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8522c-216">Ресурсы по .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8522c-216">.NET for Apache Spark Resources</span></span>](../resources/index.md)
