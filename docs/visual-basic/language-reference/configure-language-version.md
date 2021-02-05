---
title: Выберите языковую версию Visual Basic
description: Настройте компилятор для выполнения проверки синтаксиса с помощью определенной версии компилятора.
ms.date: 05/24/2018
ms.openlocfilehash: 09503db726f9d993bc986860c57aa98652b696d1
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585459"
---
# <a name="select-the-visual-basic-language-version"></a><span data-ttu-id="88500-103">Выберите языковую версию Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88500-103">Select the Visual Basic language version</span></span>

<span data-ttu-id="88500-104">Компилятор Visual Basic по умолчанию использует последнюю основную версию выпущенного языка.</span><span class="sxs-lookup"><span data-stu-id="88500-104">The Visual Basic compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="88500-105">Можно выбрать компиляцию любого проекта с помощью новой доработанной версии языка.</span><span class="sxs-lookup"><span data-stu-id="88500-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="88500-106">Выбор более новой версии языка позволяет использовать в проекте новейшие возможности языка.</span><span class="sxs-lookup"><span data-stu-id="88500-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="88500-107">В других случаях может потребоваться убедиться, что проект компилируется без ошибок при использовании более старой версии языка.</span><span class="sxs-lookup"><span data-stu-id="88500-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="88500-108">Эта возможность разделяет установку новых версий пакета SDK и средств в среде разработки и включение новых возможностей языка в проект.</span><span class="sxs-lookup"><span data-stu-id="88500-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="88500-109">Вы можете установить последнюю версию пакета SDK и средств на компьютер сборки.</span><span class="sxs-lookup"><span data-stu-id="88500-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="88500-110">В каждом проекте можно настроить использование определенной версии языка для сборки.</span><span class="sxs-lookup"><span data-stu-id="88500-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="88500-111">Существует три способа задать языковую версию:</span><span class="sxs-lookup"><span data-stu-id="88500-111">There are three ways to set the language version:</span></span>

- <span data-ttu-id="88500-112">Изменение [файла **. vbproj** вручную](#edit-the-vbproj-file)</span><span class="sxs-lookup"><span data-stu-id="88500-112">Manually edit your [**.vbproj** file](#edit-the-vbproj-file)</span></span>
- <span data-ttu-id="88500-113">Задание языковой версии [для нескольких проектов в подкаталоге](#configure-multiple-projects)</span><span class="sxs-lookup"><span data-stu-id="88500-113">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects)</span></span>
- <span data-ttu-id="88500-114">Настройка [ `-langversion` параметра компилятора](#set-the-langversion-compiler-option)</span><span class="sxs-lookup"><span data-stu-id="88500-114">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option)</span></span>

## <a name="edit-the-vbproj-file"></a><span data-ttu-id="88500-115">Изменение файла VBPROJ</span><span class="sxs-lookup"><span data-stu-id="88500-115">Edit the vbproj file</span></span>

<span data-ttu-id="88500-116">Языковую версию можно задать в файле **. vbproj** .</span><span class="sxs-lookup"><span data-stu-id="88500-116">You can set the language version in your **.vbproj** file.</span></span> <span data-ttu-id="88500-117">Добавьте следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="88500-117">Add the following element:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="88500-118">Это значение `latest` использует последнюю дополнительную версию языка Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="88500-118">The value `latest` uses the latest minor version of the Visual Basic language.</span></span> <span data-ttu-id="88500-119">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="88500-119">Valid values are:</span></span>

|<span data-ttu-id="88500-120">Значение</span><span class="sxs-lookup"><span data-stu-id="88500-120">Value</span></span>|<span data-ttu-id="88500-121">Значение</span><span class="sxs-lookup"><span data-stu-id="88500-121">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="88500-122">значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="88500-122">default</span></span>|<span data-ttu-id="88500-123">Компилятор допускает использование любого допустимого синтаксиса языка из последней основной версии, которую он поддерживает.</span><span class="sxs-lookup"><span data-stu-id="88500-123">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="88500-124">9</span><span class="sxs-lookup"><span data-stu-id="88500-124">9</span></span>|<span data-ttu-id="88500-125">Компилятор принимает только синтаксис, включенный в Visual Basic 9,0 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-125">The compiler accepts only syntax that is included in Visual Basic 9.0 or lower.</span></span>|
|<span data-ttu-id="88500-126">10</span><span class="sxs-lookup"><span data-stu-id="88500-126">10</span></span>|<span data-ttu-id="88500-127">Компилятор принимает только синтаксис, включенный в Visual Basic 10,0 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-127">The compiler accepts only syntax that is included in Visual Basic 10.0 or lower.</span></span>|
|<span data-ttu-id="88500-128">11</span><span class="sxs-lookup"><span data-stu-id="88500-128">11</span></span>|<span data-ttu-id="88500-129">Компилятор принимает только синтаксис, включенный в Visual Basic 11,0 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-129">The compiler accepts only syntax that is included in Visual Basic 11.0 or lower.</span></span>|
|<span data-ttu-id="88500-130">12</span><span class="sxs-lookup"><span data-stu-id="88500-130">12</span></span>|<span data-ttu-id="88500-131">Компилятор принимает только синтаксис, включенный в Visual Basic 12,0 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-131">The compiler accepts only syntax that is included in Visual Basic 12.0 or lower.</span></span>|
|<span data-ttu-id="88500-132">14</span><span class="sxs-lookup"><span data-stu-id="88500-132">14</span></span>|<span data-ttu-id="88500-133">Компилятор принимает только синтаксис, включенный в Visual Basic 14,0 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-133">The compiler accepts only syntax that is included in Visual Basic 14.0 or lower.</span></span>|
|<span data-ttu-id="88500-134">15</span><span class="sxs-lookup"><span data-stu-id="88500-134">15</span></span>|<span data-ttu-id="88500-135">Компилятор принимает только синтаксис, включенный в Visual Basic 15,0 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-135">The compiler accepts only syntax that is included in Visual Basic 15.0 or lower.</span></span>|
|<span data-ttu-id="88500-136">15,3</span><span class="sxs-lookup"><span data-stu-id="88500-136">15.3</span></span>|<span data-ttu-id="88500-137">Компилятор принимает только синтаксис, включенный в Visual Basic 15,3 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-137">The compiler accepts only syntax that is included in Visual Basic 15.3 or lower.</span></span>|
|<span data-ttu-id="88500-138">15.5</span><span class="sxs-lookup"><span data-stu-id="88500-138">15.5</span></span>|<span data-ttu-id="88500-139">Компилятор принимает только синтаксис, включенный в Visual Basic 15,5 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-139">The compiler accepts only syntax that is included in Visual Basic 15.5 or lower.</span></span>|
|<span data-ttu-id="88500-140">16</span><span class="sxs-lookup"><span data-stu-id="88500-140">16</span></span>|<span data-ttu-id="88500-141">Компилятор принимает только синтаксис, включенный в Visual Basic 16 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-141">The compiler accepts only syntax that is included in Visual Basic 16 or lower.</span></span>|
|<span data-ttu-id="88500-142">16,9</span><span class="sxs-lookup"><span data-stu-id="88500-142">16.9</span></span>|<span data-ttu-id="88500-143">Компилятор принимает только синтаксис, включенный в Visual Basic 16,9 или ниже.</span><span class="sxs-lookup"><span data-stu-id="88500-143">The compiler accepts only syntax that is included in Visual Basic 16.9 or lower.</span></span>|
|<span data-ttu-id="88500-144">последняя</span><span class="sxs-lookup"><span data-stu-id="88500-144">latest</span></span>|<span data-ttu-id="88500-145">Компилятор допускает использование любого допустимого синтаксиса языка, который он может поддерживать.</span><span class="sxs-lookup"><span data-stu-id="88500-145">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="88500-146">В специальных строках `default` и `latest` будет указана соответственно последняя основная и дополнительная версия языка, установленная на компьютере сборки.</span><span class="sxs-lookup"><span data-stu-id="88500-146">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="88500-147">Настройка нескольких проектов</span><span class="sxs-lookup"><span data-stu-id="88500-147">Configure multiple projects</span></span>

<span data-ttu-id="88500-148">Можно создать файл **Directory.build.props**, содержащий элемент `<LangVersion>`, чтобы настроить несколько каталогов.</span><span class="sxs-lookup"><span data-stu-id="88500-148">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="88500-149">Обычно это делается в каталоге решения.</span><span class="sxs-lookup"><span data-stu-id="88500-149">You typically do that in your solution directory.</span></span> <span data-ttu-id="88500-150">Добавьте следующий объект в файл **Directory. Build. props** в каталоге решения:</span><span class="sxs-lookup"><span data-stu-id="88500-150">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="88500-151">Теперь сборка в каждом подкаталоге каталога, содержащего этот файл, будет использовать синтаксис Visual Basic версии 15,5.</span><span class="sxs-lookup"><span data-stu-id="88500-151">Now, builds in every subdirectory of the directory containing that file will use Visual Basic version 15.5 syntax.</span></span> <span data-ttu-id="88500-152">Дополнительные сведения см. в статье о [настройке сборки](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="88500-152">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="88500-153">Задание параметра компилятора langversion</span><span class="sxs-lookup"><span data-stu-id="88500-153">Set the langversion compiler option</span></span>

<span data-ttu-id="88500-154">Вы можете использовать параметр командной строки `-langversion`.</span><span class="sxs-lookup"><span data-stu-id="88500-154">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="88500-155">Дополнительные сведения см. в статье, посвященной параметру компилятора [-langversion](../reference/command-line-compiler/langversion.md).</span><span class="sxs-lookup"><span data-stu-id="88500-155">For more information, see the article on the [-langversion](../reference/command-line-compiler/langversion.md) compiler option.</span></span> <span data-ttu-id="88500-156">Список допустимых значений можно получить, введя  `vbc -langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="88500-156">You can see a list of the valid values by typing  `vbc -langversion:?` .</span></span>
