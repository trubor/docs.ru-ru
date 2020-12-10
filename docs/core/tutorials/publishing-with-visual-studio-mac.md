---
title: Публикация консольного приложения .NET с помощью Visual Studio для Mac
description: Узнайте, как использовать Visual Studio для Mac для создания набора файлов, необходимых для запуска приложения .NET.
ms.date: 11/30/2020
ms.openlocfilehash: 88f143011b19ca8eda6610803c894e619d06a635
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599194"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="b1668-103">Учебник. Публикация консольного приложения .NET с помощью Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="b1668-103">Tutorial: Publish a .NET console application using Visual Studio for Mac</span></span>

<span data-ttu-id="b1668-104">В этом руководстве показано, как опубликовать консольное приложение, чтобы его могли запускать другие пользователи.</span><span class="sxs-lookup"><span data-stu-id="b1668-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="b1668-105">При публикации создается набор файлов, которые необходимы для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b1668-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="b1668-106">Чтобы развернуть файлы, скопируйте их на целевой компьютер.</span><span class="sxs-lookup"><span data-stu-id="b1668-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1668-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b1668-107">Prerequisites</span></span>

- <span data-ttu-id="b1668-108">В этом руководстве используется консольное приложение, созданное по инструкциям из статьи [Создание консольного приложения .NET с помощью Visual Studio для Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="b1668-108">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="b1668-109">Публикация приложения</span><span class="sxs-lookup"><span data-stu-id="b1668-109">Publish the app</span></span>

1. <span data-ttu-id="b1668-110">Запустите Visual Studio для Mac.</span><span class="sxs-lookup"><span data-stu-id="b1668-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="b1668-111">Откройте проект HelloWorld, созданный по инструкциям из статьи [Создание консольного приложения .NET с помощью Visual Studio для Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="b1668-111">Open the HelloWorld project that you created in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="b1668-112">Убедитесь, что в Visual Studio настроен режим сборки для версии выпуска.</span><span class="sxs-lookup"><span data-stu-id="b1668-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="b1668-113">При необходимости измените конфигурацию сборки на панели инструментов, указав конфигурацию **Выпуск** вместо конфигурации **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="b1668-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Панель инструментов Visual Studio с выбранной сборкой выпуска":::

1. <span data-ttu-id="b1668-115">В главном меню выберите **Сборка** > **Опубликовать в папке…**</span><span class="sxs-lookup"><span data-stu-id="b1668-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Контекстное меню Опубликовать в Visual Studio":::

1. <span data-ttu-id="b1668-117">В диалоговом окне **Опубликовать в папке** выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="b1668-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Диалоговое окно Опубликовать в папке в Visual Studio":::

   <span data-ttu-id="b1668-119">Откроется папка публикации с созданными файлами.</span><span class="sxs-lookup"><span data-stu-id="b1668-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="папка публикации":::

1. <span data-ttu-id="b1668-121">Щелкните значок шестеренки, а затем в контекстном меню выберите **Copy "publish" as Pathname** (Копировать publish как путь к папке).</span><span class="sxs-lookup"><span data-stu-id="b1668-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Копирование пути к папке публикации":::

## <a name="inspect-the-files"></a><span data-ttu-id="b1668-123">Проверка файлов</span><span class="sxs-lookup"><span data-stu-id="b1668-123">Inspect the files</span></span>

<span data-ttu-id="b1668-124">В ходе публикации создается платформенно-зависимое развертывание. При таком развертывании опубликованное приложение выполняется на компьютере с установленной средой выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="b1668-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET runtime installed.</span></span> <span data-ttu-id="b1668-125">Пользователи могут запустить опубликованное приложение, выполнив команду `dotnet HelloWorld.dll` из командной строки.</span><span class="sxs-lookup"><span data-stu-id="b1668-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="b1668-126">Как показано на предыдущем рисунке, опубликованные выходные данные включают следующие файлы:</span><span class="sxs-lookup"><span data-stu-id="b1668-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="b1668-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="b1668-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="b1668-128">Это файл зависимостей среды выполнения приложения.</span><span class="sxs-lookup"><span data-stu-id="b1668-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="b1668-129">Он определяет библиотеки и компоненты .NET (включая библиотеку DLL, содержащую приложение), необходимые для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b1668-129">It defines the .NET components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="b1668-130">Дополнительные сведения см. в разделе [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md) (Файлы конфигурации среды выполнения).</span><span class="sxs-lookup"><span data-stu-id="b1668-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="b1668-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="b1668-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="b1668-132">Это версия [зависимого от платформы развертывания](../deploying/deploy-with-cli.md#framework-dependent-deployment) приложения.</span><span class="sxs-lookup"><span data-stu-id="b1668-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="b1668-133">Чтобы выполнить эту библиотеку динамической компоновки, введите `dotnet HelloWorld.dll` в командной строке.</span><span class="sxs-lookup"><span data-stu-id="b1668-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="b1668-134">Этот метод запуска приложения работает на любой платформе, где установлена среда выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="b1668-134">This method of running the app works on any platform that has the .NET runtime installed.</span></span>

* <span data-ttu-id="b1668-135">*HelloWorld.pdb* (необязателен для развертывания)</span><span class="sxs-lookup"><span data-stu-id="b1668-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="b1668-136">Это файл отладочных символов.</span><span class="sxs-lookup"><span data-stu-id="b1668-136">This is the debug symbols file.</span></span> <span data-ttu-id="b1668-137">Этот файл не нужно распространять вместе с приложением, но желательно сохранить его на случай, если придется выполнять отладку опубликованной версии приложения.</span><span class="sxs-lookup"><span data-stu-id="b1668-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="b1668-138">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="b1668-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="b1668-139">Это файл конфигурации среды выполнения для приложения.</span><span class="sxs-lookup"><span data-stu-id="b1668-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="b1668-140">Он определяет версию платформы .NET, для которой предназначено приложение.</span><span class="sxs-lookup"><span data-stu-id="b1668-140">It identifies the version of .NET that your application was built to run on.</span></span> <span data-ttu-id="b1668-141">Кроме того, в него можно добавить параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b1668-141">You can also add configuration options to it.</span></span> <span data-ttu-id="b1668-142">Дополнительные сведения см. в статье [Параметры конфигурации среды выполнения .NET](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="b1668-142">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="b1668-143">Запуск опубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="b1668-143">Run the published app</span></span>

1. <span data-ttu-id="b1668-144">Откройте терминал и перейдите в папку *publish*.</span><span class="sxs-lookup"><span data-stu-id="b1668-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="b1668-145">Для этого введите `cd` и вставьте скопированный ранее путь.</span><span class="sxs-lookup"><span data-stu-id="b1668-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="b1668-146">Пример:</span><span class="sxs-lookup"><span data-stu-id="b1668-146">For example:</span></span>

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/net5.0/publish/
   ```

1. <span data-ttu-id="b1668-147">Запустите приложение с помощью команды `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="b1668-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="b1668-148">Введите `dotnet HelloWorld.dll` и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b1668-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="b1668-149">В ответ на запрос введите имя и нажмите любую клавишу, чтобы выйти.</span><span class="sxs-lookup"><span data-stu-id="b1668-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b1668-150">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="b1668-150">Additional resources</span></span>

- [<span data-ttu-id="b1668-151">развертывание приложений .NET</span><span class="sxs-lookup"><span data-stu-id="b1668-151">.NET application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="b1668-152">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="b1668-152">Next steps</span></span>

<span data-ttu-id="b1668-153">В этом руководстве вы опубликовали консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="b1668-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="b1668-154">Далее вы создадите библиотеку классов.</span><span class="sxs-lookup"><span data-stu-id="b1668-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b1668-155">Создание библиотеки классов .NET с помощью Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="b1668-155">Create a .NET library using Visual Studio for Mac</span></span>](library-with-visual-studio-mac.md)
