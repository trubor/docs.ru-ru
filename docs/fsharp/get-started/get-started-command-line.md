---
title: 'Приступая к работе с F # с помощью программ командной строки'
description: 'Узнайте, как создать простое решение с несколькими проектами на F # с помощью .NET Core CLI в любой операционной системе (Windows, macOS или Linux).'
ms.date: 08/15/2020
ms.openlocfilehash: f890e31fe8c665874dc3034aebfae32e38b9031a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739919"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="6ac5e-103">Начало работы с F # с .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="6ac5e-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="6ac5e-104">В этой статье описывается, как можно приступить к работе с F # в любой операционной системе (Windows, macOS или Linux) с .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="6ac5e-105">Он проходит через создание многопроектного решения с библиотекой классов, которая вызывается консольным приложением.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ac5e-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="6ac5e-106">Prerequisites</span></span>

<span data-ttu-id="6ac5e-107">Для начала необходимо установить последнюю [пакет SDK для .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="6ac5e-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="6ac5e-108">В этой статье предполагается, что вы умеете использовать командную строку и предпочитаемый текстовый редактор.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="6ac5e-109">Если вы еще не используете его, [Visual Studio Code](get-started-vscode.md) является отличным вариантом в качестве текстового редактора для F #.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="6ac5e-110">Создание простого решения с несколькими проектами</span><span class="sxs-lookup"><span data-stu-id="6ac5e-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="6ac5e-111">Откройте командную строку или терминал и выполните команду [DotNet New](../../core/tools/dotnet-new.md) , чтобы создать новый файл решения с именем `FSNetCore` :</span><span class="sxs-lookup"><span data-stu-id="6ac5e-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="6ac5e-112">Следующая структура каталогов создается после выполнения предыдущей команды:</span><span class="sxs-lookup"><span data-stu-id="6ac5e-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="6ac5e-113">Написание библиотеки классов</span><span class="sxs-lookup"><span data-stu-id="6ac5e-113">Write a class library</span></span>

<span data-ttu-id="6ac5e-114">Перейдите в каталог *фснеткоре*.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="6ac5e-115">Используйте `dotnet new` команду, чтобы создать проект библиотеки классов в папке **src** с именем Library.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

<span data-ttu-id="6ac5e-116">Следующая структура каталогов создается после выполнения предыдущей команды:</span><span class="sxs-lookup"><span data-stu-id="6ac5e-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="6ac5e-117">Замените содержимое `Library.fs` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="6ac5e-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    $"I used to be {value} but now I'm {json} thanks to JSON.NET!"
```

<span data-ttu-id="6ac5e-118">Добавьте Newtonsoft.Jsв пакет NuGet в проект библиотеки.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="6ac5e-119">Добавьте `Library` проект в `FSNetCore` решение с помощью команды [DotNet SLN Add](../../core/tools/dotnet-sln.md) :</span><span class="sxs-lookup"><span data-stu-id="6ac5e-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="6ac5e-120">Выполните команду `dotnet build` , чтобы выполнить сборку проекта.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="6ac5e-121">При сборке будут восстановлены неразрешенные зависимости.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="6ac5e-122">Написание консольного приложения, использующего библиотеку классов</span><span class="sxs-lookup"><span data-stu-id="6ac5e-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="6ac5e-123">Используйте `dotnet new` команду, чтобы создать консольное приложение в папке **src** с именем App.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

<span data-ttu-id="6ac5e-124">Следующая структура каталогов создается после выполнения предыдущей команды:</span><span class="sxs-lookup"><span data-stu-id="6ac5e-124">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="6ac5e-125">Замените содержимое файла `Program.fs` приведенным ниже кодом.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    for arg in argv do
        let value = getJsonNetJson arg
        printfn $"{value}"

    0 // return an integer exit code
```

<span data-ttu-id="6ac5e-126">Добавьте ссылку на `Library` проект с помощью команды [DotNet Add](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="6ac5e-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="6ac5e-127">Добавьте `App` проект в `FSNetCore` решение с помощью `dotnet sln add` команды:</span><span class="sxs-lookup"><span data-stu-id="6ac5e-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="6ac5e-128">Чтобы выполнить сборку проекта, восстановите зависимости NuGet `dotnet restore` и выполните команду `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="6ac5e-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="6ac5e-129">Перейдите в каталог `src/App` консольного проекта и запустите проект, передавая `Hello World` в качестве аргументов:</span><span class="sxs-lookup"><span data-stu-id="6ac5e-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```dotnetcli
cd src/App
dotnet run Hello World
```

<span data-ttu-id="6ac5e-130">Вы увидите следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="6ac5e-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="6ac5e-131">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="6ac5e-131">Next steps</span></span>

<span data-ttu-id="6ac5e-132">Далее ознакомьтесь с [обзором f #](../tour.md) , чтобы узнать больше о различных функциях f #.</span><span class="sxs-lookup"><span data-stu-id="6ac5e-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
