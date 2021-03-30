---
title: Развертывание приложения .NET для Apache Spark в Azure HDInsight
description: Узнайте, как развернуть приложение .NET для Apache Spark в HDInsight.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0c2b7522e0e6790ded418413ef0f128aae1e0884
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875347"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="647db-103">Учебник. Развертывание приложения .NET для Apache Spark в Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="647db-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="647db-104">В этом учебнике описывается развертывание приложения .NET для Apache Spark в облаке с помощью кластера Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="647db-105">HDInsight упрощает создание и настройку кластера Spark в Azure, так как кластеры Spark в HDInsight совместимы со службой хранилища Azure и Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="647db-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="647db-106">В этом руководстве вы узнаете, как:</span><span class="sxs-lookup"><span data-stu-id="647db-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="647db-107">Получить доступ к учетным записям хранения с помощью Обозревателя службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="647db-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="647db-108">Создать кластер Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="647db-109">Опубликовать приложение .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="647db-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="647db-110">Создать и запустить действие скрипта HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="647db-111">Запустить приложение .NET для Apache Spark в кластере HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="647db-112">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="647db-112">Prerequisites</span></span>

<span data-ttu-id="647db-113">Прежде чем начать, сделайте следующее.</span><span class="sxs-lookup"><span data-stu-id="647db-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="647db-114">Если у вас еще нет подписки Azure, создайте [бесплатную учетную запись Azure](https://azure.microsoft.com/free/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="647db-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="647db-115">Войдите на [портале Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="647db-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="647db-116">Установите Обозреватель службы хранилища Azure на [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409) или [компьютере MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="647db-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="647db-117">Пройдите учебник [.NET для Apache Spark — начало работы за 10 минут](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro).</span><span class="sxs-lookup"><span data-stu-id="647db-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="647db-118">Доступ к учетным записям хранения</span><span class="sxs-lookup"><span data-stu-id="647db-118">Access your storage accounts</span></span>

1. <span data-ttu-id="647db-119">Откройте обозреватель службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="647db-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="647db-120">Выберите **Добавить учетную запись** в меню слева и войдите в учетную запись Azure.</span><span class="sxs-lookup"><span data-stu-id="647db-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Вход в учетную запись Azure из Обозревателя службы хранилища](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="647db-122">После входа в систему должны отобразиться все учетные записи хранения, а также все ресурсы, отправленные в учетные записи хранения.</span><span class="sxs-lookup"><span data-stu-id="647db-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="647db-123">Создание кластера HDInsight</span><span class="sxs-lookup"><span data-stu-id="647db-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="647db-124">Счета за кластеры HDInsight выставляются пропорционально за минуту, даже если вы их не используете.</span><span class="sxs-lookup"><span data-stu-id="647db-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="647db-125">Обязательно удалите кластер, когда завершите его использование.</span><span class="sxs-lookup"><span data-stu-id="647db-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="647db-126">Дополнительные сведения см. в разделе [Очистка ресурсов](#clean-up-resources) этого учебника.</span><span class="sxs-lookup"><span data-stu-id="647db-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="647db-127">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="647db-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="647db-128">Выберите действие **Создать ресурс**.</span><span class="sxs-lookup"><span data-stu-id="647db-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="647db-129">Затем выберите **HDInsight** в категории **Аналитика**.</span><span class="sxs-lookup"><span data-stu-id="647db-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Создание ресурса HDInsight на портале Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="647db-131">В разделе **Основные сведения** укажите следующие значения.</span><span class="sxs-lookup"><span data-stu-id="647db-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="647db-132">Свойство.</span><span class="sxs-lookup"><span data-stu-id="647db-132">Property</span></span>  |<span data-ttu-id="647db-133">Описание</span><span class="sxs-lookup"><span data-stu-id="647db-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="647db-134">Подписка</span><span class="sxs-lookup"><span data-stu-id="647db-134">Subscription</span></span>  | <span data-ttu-id="647db-135">В раскрывающемся списке выберите одну из активных подписок Azure.</span><span class="sxs-lookup"><span data-stu-id="647db-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="647db-136">Группа ресурсов</span><span class="sxs-lookup"><span data-stu-id="647db-136">Resource group</span></span> | <span data-ttu-id="647db-137">Укажите, следует ли создать новую группу ресурсов или использовать имеющуюся.</span><span class="sxs-lookup"><span data-stu-id="647db-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="647db-138">Группа ресурсов — это контейнер, содержащий связанные ресурсы для решения Azure.</span><span class="sxs-lookup"><span data-stu-id="647db-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="647db-139">Имя кластера</span><span class="sxs-lookup"><span data-stu-id="647db-139">Cluster name</span></span> | <span data-ttu-id="647db-140">Введите имя кластера Spark в HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="647db-141">Местоположение</span><span class="sxs-lookup"><span data-stu-id="647db-141">Location</span></span>   | <span data-ttu-id="647db-142">Выберите расположение группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="647db-142">Select a location for the resource group.</span></span> <span data-ttu-id="647db-143">В шаблоне используется это расположение для создания кластера и его хранения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="647db-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="647db-144">Тип кластера</span><span class="sxs-lookup"><span data-stu-id="647db-144">Cluster type</span></span>| <span data-ttu-id="647db-145">Выберите **spark** в качестве типа кластера.</span><span class="sxs-lookup"><span data-stu-id="647db-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="647db-146">Cluster version</span><span class="sxs-lookup"><span data-stu-id="647db-146">Cluster version</span></span>|<span data-ttu-id="647db-147">Это поле будет автоматически заполнено версией по умолчанию после выбора типа кластера.</span><span class="sxs-lookup"><span data-stu-id="647db-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="647db-148">Выберите версию Spark 2.3 или 2.4.</span><span class="sxs-lookup"><span data-stu-id="647db-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="647db-149">Имя пользователя для входа в кластер</span><span class="sxs-lookup"><span data-stu-id="647db-149">Cluster login username</span></span>| <span data-ttu-id="647db-150">Введите имя пользователя для входа в кластер.</span><span class="sxs-lookup"><span data-stu-id="647db-150">Enter the cluster login username.</span></span>  <span data-ttu-id="647db-151">Имя по умолчанию — *admin*.</span><span class="sxs-lookup"><span data-stu-id="647db-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="647db-152">Пароль для входа в кластер</span><span class="sxs-lookup"><span data-stu-id="647db-152">Cluster login password</span></span>| <span data-ttu-id="647db-153">Введите пароль для входа.</span><span class="sxs-lookup"><span data-stu-id="647db-153">Enter any login password.</span></span> |
    |<span data-ttu-id="647db-154">Имя пользователя для Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="647db-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="647db-155">Введите имя пользователя SSH.</span><span class="sxs-lookup"><span data-stu-id="647db-155">Enter the SSH username.</span></span> <span data-ttu-id="647db-156">По умолчанию эта учетная запись использует тот же пароль, что и учетная запись *для входа в кластер*.</span><span class="sxs-lookup"><span data-stu-id="647db-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="647db-157">По завершении выберите **Next: Storage >>** (Далее: хранилище), чтобы перейти на страницу **Хранилище**.</span><span class="sxs-lookup"><span data-stu-id="647db-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="647db-158">На странице **Хранилище** укажите следующие значения.</span><span class="sxs-lookup"><span data-stu-id="647db-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="647db-159">Свойство</span><span class="sxs-lookup"><span data-stu-id="647db-159">Property</span></span>  |<span data-ttu-id="647db-160">Описание</span><span class="sxs-lookup"><span data-stu-id="647db-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="647db-161">Тип первичного хранилища</span><span class="sxs-lookup"><span data-stu-id="647db-161">Primary storage type</span></span>|<span data-ttu-id="647db-162">Используйте значение **службы хранилища Azure** по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="647db-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="647db-163">Метод выбора</span><span class="sxs-lookup"><span data-stu-id="647db-163">Selection method</span></span>|<span data-ttu-id="647db-164">Используйте значение **Выбрать в списке** по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="647db-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="647db-165">Основную учетную запись хранения</span><span class="sxs-lookup"><span data-stu-id="647db-165">Primary storage account</span></span>|<span data-ttu-id="647db-166">Выберите подписку и одну из активных учетных записей хранения в этой подписке.</span><span class="sxs-lookup"><span data-stu-id="647db-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="647db-167">Контейнер</span><span class="sxs-lookup"><span data-stu-id="647db-167">Container</span></span>|<span data-ttu-id="647db-168">Этот контейнер является конкретным контейнером больших двоичных объектов в вашей учетной записи хранения, где кластер ищет файлы для запуска приложения в облаке.</span><span class="sxs-lookup"><span data-stu-id="647db-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="647db-169">Можно присвоить ему любое доступное имя.</span><span class="sxs-lookup"><span data-stu-id="647db-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="647db-170">В разделе **Просмотр и создание** выберите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="647db-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="647db-171">Процесс создания кластеров занимает около 20 минут.</span><span class="sxs-lookup"><span data-stu-id="647db-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="647db-172">Прежде чем перейти к следующему шагу, вы должны создать кластер.</span><span class="sxs-lookup"><span data-stu-id="647db-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="647db-173">Публикация приложения</span><span class="sxs-lookup"><span data-stu-id="647db-173">Publish your app</span></span>

<span data-ttu-id="647db-174">Затем вы публикуете приложение *mySparkApp*, созданное в учебнике [.NET для Apache Spark — начало работы за 10 минут](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro), чтобы кластер Spark получил доступ ко всем файлам, которые необходимы для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="647db-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="647db-175">Для публикации *mySparkApp* выполните следующие команды:</span><span class="sxs-lookup"><span data-stu-id="647db-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="647db-176">**В Windows:**</span><span class="sxs-lookup"><span data-stu-id="647db-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r win-x64
   ```

   <span data-ttu-id="647db-177">**В Linux:**</span><span class="sxs-lookup"><span data-stu-id="647db-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="647db-178">Выполните следующие задачи и заархивируйте опубликованные файлы приложения, чтобы их можно было легко передать в кластер HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span> <span data-ttu-id="647db-179">Упакуйте содержимое папки публикации, например, в файл *publish.zip*, который был создан на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="647db-179">Zip the contents of the publish folder, *publish.zip* for example, that was created as a result of Step 1.</span></span> <span data-ttu-id="647db-180">Все сборки должны находиться на первом уровне ZIP-файла. Не должны использоваться промежуточные уровни папки.</span><span class="sxs-lookup"><span data-stu-id="647db-180">All the assemblies should be in the first layer of the ZIP file and there should be no intermediate folder layer.</span></span> <span data-ttu-id="647db-181">Это означает, что при распаковке файла *publish.zip* все сборки извлекаются в текущий рабочий каталог.</span><span class="sxs-lookup"><span data-stu-id="647db-181">This means when you unzip *publish.zip*, all assemblies are extracted into your current working directory.</span></span>

   <span data-ttu-id="647db-182">**В Windows:**</span><span class="sxs-lookup"><span data-stu-id="647db-182">**On Windows:**</span></span>

   <span data-ttu-id="647db-183">Используйте программу извлечения, например 7-Zip или WinZip, чтобы распаковать файл в каталог bin, где находятся все опубликованные двоичные файлы.</span><span class="sxs-lookup"><span data-stu-id="647db-183">Use an extraction program, like 7-Zip or WinZip, to extract the file into the bin directory with all the published binaries.</span></span>

   <span data-ttu-id="647db-184">**В Linux выполните следующую команду:**</span><span class="sxs-lookup"><span data-stu-id="647db-184">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="647db-185">Отправка файлов в Azure</span><span class="sxs-lookup"><span data-stu-id="647db-185">Upload files to Azure</span></span>

<span data-ttu-id="647db-186">Затем используйте Обозреватель службы хранилища Azure, чтобы передать следующие пять файлов в контейнер больших двоичных объектов, выбранный для системы хранения данных кластера:</span><span class="sxs-lookup"><span data-stu-id="647db-186">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="647db-187">Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="647db-187">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="647db-188">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="647db-188">install-worker.sh</span></span>
* <span data-ttu-id="647db-189">publish.zip</span><span class="sxs-lookup"><span data-stu-id="647db-189">publish.zip</span></span>
* <span data-ttu-id="647db-190">microsoft-spark-2-4_2.11-1.0.0.jar</span><span class="sxs-lookup"><span data-stu-id="647db-190">microsoft-spark-2-4_2.11-1.0.0.jar</span></span>
* <span data-ttu-id="647db-191">input.txt</span><span class="sxs-lookup"><span data-stu-id="647db-191">input.txt</span></span>

1. <span data-ttu-id="647db-192">Откройте Обозреватель службы хранилища Azure и перейдите к своей учетной записи хранения в меню слева.</span><span class="sxs-lookup"><span data-stu-id="647db-192">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="647db-193">Выполните детализацию до контейнера больших двоичных объектов для кластера в разделе **Контейнеры больших двоичных объектов** в вашей учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="647db-193">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="647db-194">*Microsoft.Spark.Worker* помогает Apache Spark запускать ваше приложение, например пользовательские функции (UDF), которые вы написали.</span><span class="sxs-lookup"><span data-stu-id="647db-194">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="647db-195">Загрузите [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="647db-195">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span> <span data-ttu-id="647db-196">Затем выберите **Отправить** в Обозревателе службы хранилища Azure, чтобы отправить рабочую роль.</span><span class="sxs-lookup"><span data-stu-id="647db-196">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Отправка файлов в Обозреватель службы хранилища Azure](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="647db-198">*install-worker.sh* — это скрипт, который позволяет копировать зависимые файлы .NET для Apache Spark в узлы кластера.</span><span class="sxs-lookup"><span data-stu-id="647db-198">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="647db-199">Создайте новый файл с именем **install-worker.sh** на локальном компьютере и вставьте [содержимое файла install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/main/deployment/install-worker.sh), расположенного на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="647db-199">Create a new file named **install-worker.sh** in your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/main/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="647db-200">Затем отправьте *install-worker.sh* в контейнер больших двоичных объектов.</span><span class="sxs-lookup"><span data-stu-id="647db-200">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="647db-201">Кластеру требуется файл *publish.zip*, содержащий опубликованные файлы приложения.</span><span class="sxs-lookup"><span data-stu-id="647db-201">Your cluster needs the *publish.zip* file that contains your app's published files.</span></span> <span data-ttu-id="647db-202">Перейдите к опубликованной папке **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64** и найдите **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="647db-202">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="647db-203">Затем отправьте файл *publish.zip* в контейнер больших двоичных объектов.</span><span class="sxs-lookup"><span data-stu-id="647db-203">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="647db-204">Кластеру требуется код приложения, упакованный в виде JAR-файла, который входит в состав пакета NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) и размещается в выходном каталоге сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="647db-204">Your cluster needs the application code that is packaged as a jar, included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) nuget and colocated in your app's build output directory.</span></span> <span data-ttu-id="647db-205">Перейдите к опубликованной папке **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64** и найдите **microsoft-spark-2-4_2.11-1.0.0.jar**.</span><span class="sxs-lookup"><span data-stu-id="647db-205">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64**, and locate **microsoft-spark-2-4_2.11-1.0.0.jar**.</span></span> <span data-ttu-id="647db-206">Затем отправьте JAR-файл в контейнер больших двоичных объектов.</span><span class="sxs-lookup"><span data-stu-id="647db-206">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="647db-207">Там может быть несколько JAR-файлов (для версий Spark 2.3.x, 2.4.x и 3.0.x).</span><span class="sxs-lookup"><span data-stu-id="647db-207">There may be multiple .jar files (for versions 2.3.x, 2.4.x and 3.0.x of Spark).</span></span> <span data-ttu-id="647db-208">Необходимо выбрать JAR-файл, соответствующий версии Spark, выбранной при создании кластера.</span><span class="sxs-lookup"><span data-stu-id="647db-208">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="647db-209">Например, выберите *microsoft-spark-2-4_2.11-1.0.0.jar*, если вы выбрали Spark 2.4 во время создания кластера.</span><span class="sxs-lookup"><span data-stu-id="647db-209">For example, choose *microsoft-spark-2-4_2.11-1.0.0.jar* if you chose Spark 2.4 during cluster creation.</span></span>

6. <span data-ttu-id="647db-210">Кластеру требуются входные данные для приложения.</span><span class="sxs-lookup"><span data-stu-id="647db-210">Your cluster needs the input to your app.</span></span> <span data-ttu-id="647db-211">Перейдите в каталог **mySparkApp** и найдите файл **input.txt**.</span><span class="sxs-lookup"><span data-stu-id="647db-211">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="647db-212">Отправьте входной файл в каталог **user/sshuser** в контейнере больших двоичных объектов.</span><span class="sxs-lookup"><span data-stu-id="647db-212">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="647db-213">Вы будете подключаться к кластеру по протоколу SSH, и в этой папке кластер будет искать входные данные.</span><span class="sxs-lookup"><span data-stu-id="647db-213">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="647db-214">Файл *input.txt* — это единственный файл, отправленный в конкретный каталог.</span><span class="sxs-lookup"><span data-stu-id="647db-214">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="647db-215">Выполнения действия скрипта HDInsight</span><span class="sxs-lookup"><span data-stu-id="647db-215">Run the HDInsight script action</span></span>

<span data-ttu-id="647db-216">После запуска кластера и отправки файлов в Azure вы запускаете скрипт **install-worker.sh** в кластере.</span><span class="sxs-lookup"><span data-stu-id="647db-216">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="647db-217">Перейдите к кластеру HDInsight Spark на портале Azure и выберите **Действия скрипта**.</span><span class="sxs-lookup"><span data-stu-id="647db-217">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="647db-218">Выберите **+ Отправить новый** и укажите следующие значения.</span><span class="sxs-lookup"><span data-stu-id="647db-218">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="647db-219">Свойство.</span><span class="sxs-lookup"><span data-stu-id="647db-219">Property</span></span>  |<span data-ttu-id="647db-220">Описание</span><span class="sxs-lookup"><span data-stu-id="647db-220">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="647db-221">Тип скрипта</span><span class="sxs-lookup"><span data-stu-id="647db-221">Script type</span></span> |<span data-ttu-id="647db-222">Другой</span><span class="sxs-lookup"><span data-stu-id="647db-222">Custom</span></span>|
   | <span data-ttu-id="647db-223">name</span><span class="sxs-lookup"><span data-stu-id="647db-223">Name</span></span> | <span data-ttu-id="647db-224">Установка рабочей роли</span><span class="sxs-lookup"><span data-stu-id="647db-224">Install Worker</span></span>|
   | <span data-ttu-id="647db-225">URI bash-скрипта</span><span class="sxs-lookup"><span data-stu-id="647db-225">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="647db-226">Чтобы подтвердить этот URI, щелкните правой кнопкой мыши install-worker.sh в Обозреватель службы хранилища Azure и выберите пункт "Свойства".</span><span class="sxs-lookup"><span data-stu-id="647db-226">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="647db-227">Типы узлов</span><span class="sxs-lookup"><span data-stu-id="647db-227">Node type(s)</span></span>| <span data-ttu-id="647db-228">Рабочий узел</span><span class="sxs-lookup"><span data-stu-id="647db-228">Worker</span></span>|
   | <span data-ttu-id="647db-229">Параметры</span><span class="sxs-lookup"><span data-stu-id="647db-229">Parameters</span></span> | <span data-ttu-id="647db-230">azure</span><span class="sxs-lookup"><span data-stu-id="647db-230">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz </br> <span data-ttu-id="647db-231">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="647db-231">/usr/local/bin</span></span>

3. <span data-ttu-id="647db-232">Выберите **Создать**, чтобы отправить скрипт.</span><span class="sxs-lookup"><span data-stu-id="647db-232">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="647db-233">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="647db-233">Run your app</span></span>

1. <span data-ttu-id="647db-234">Перейдите к кластеру HDInsight Spark на портале Azure и выберите **SSH и вход в кластер**.</span><span class="sxs-lookup"><span data-stu-id="647db-234">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="647db-235">Скопируйте данные для входа по протоколу SSH и вставьте имя для входа в терминал.</span><span class="sxs-lookup"><span data-stu-id="647db-235">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="647db-236">Войдите в кластер, используя пароль, заданный во время создания кластера.</span><span class="sxs-lookup"><span data-stu-id="647db-236">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="647db-237">Вы должны увидеть сообщение с приветствием в Ubuntu и Spark.</span><span class="sxs-lookup"><span data-stu-id="647db-237">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="647db-238">Используйте команду **spark-submit**, чтобы запустить приложение в кластере HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-238">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="647db-239">Не забудьте заменить **mycontainer** и **mystorageaccount** в примере скрипта, указав фактические имена контейнера больших двоичных объектов и учетной записи хранения.</span><span class="sxs-lookup"><span data-stu-id="647db-239">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2-4_2.11-1.0.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="647db-240">При запуске приложения отображается та же таблица подсчета слов из локального запуска начального приложения, записанная на консоль.</span><span class="sxs-lookup"><span data-stu-id="647db-240">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="647db-241">Поздравляем, вы запустили свое первое приложение .NET для Apache Spark в облаке!</span><span class="sxs-lookup"><span data-stu-id="647db-241">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="647db-242">Очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="647db-242">Clean up resources</span></span>

<span data-ttu-id="647db-243">HDInsight сохраняет ваши данные в службе хранилища Azure, что позволяет безопасно удалить неиспользуемый кластер.</span><span class="sxs-lookup"><span data-stu-id="647db-243">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="647db-244">Плата за кластеры HDInsight взимается, даже когда они не используются.</span><span class="sxs-lookup"><span data-stu-id="647db-244">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="647db-245">Поскольку стоимость кластера во много раз превышает стоимость хранилища, экономически целесообразно удалять неиспользуемые кластеры.</span><span class="sxs-lookup"><span data-stu-id="647db-245">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="647db-246">Кроме того, можно выбрать имя группы ресурсов, чтобы открыть страницу группы ресурсов, а затем щелкнуть **Удалить группу ресурсов**.</span><span class="sxs-lookup"><span data-stu-id="647db-246">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="647db-247">Вместе с группой ресурсов вы также удалите кластер Spark в HDInsight и учетную запись хранения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="647db-247">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="647db-248">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="647db-248">Next steps</span></span>

<span data-ttu-id="647db-249">В этом руководстве вы развернули приложение .NET для Apache Spark в Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-249">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="647db-250">Дополнительные сведения об HDInsight см. в документации по Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="647db-250">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="647db-251">[Удаленная отправка заданий в Azure HDInsight](../how-to-guides/hdinsight-deploy-methods.md)
> [Документации по Azure HDInsight](/azure/hdinsight/)</span><span class="sxs-lookup"><span data-stu-id="647db-251">[Submit jobs remotely on Azure HDInsight](../how-to-guides/hdinsight-deploy-methods.md)
[Azure HDInsight Documentation](/azure/hdinsight/)</span></span>
