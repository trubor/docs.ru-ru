---
title: NETSDK1004. Файл ресурсов не найден
description: Сведения об ошибке NETSDK1004 пакета SDK для .NET, которая возникает, когда не найден файл project.assets.json.
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: 8416063fe318106cbcb4dbccacef3ecaaff5bba2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216439"
---
# <a name="netsdk1004-assets-file-not-found"></a><span data-ttu-id="10323-103">NETSDK1004. Файл ресурсов не найден</span><span class="sxs-lookup"><span data-stu-id="10323-103">NETSDK1004: Assets file not found</span></span>

<span data-ttu-id="10323-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 2.1.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="10323-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="10323-105">NuGet записывает файл с именем *project.assets.json* в папку *obj*, а пакет SDK для .NET использует его для получения сведений о пакетах для передачи в компилятор.</span><span class="sxs-lookup"><span data-stu-id="10323-105">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="10323-106">Эта ошибка возникает, когда во время сборки во время сборки не найден файл ресурсов *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="10323-106">This error occurs when the assets file *project.assets.json* is not found during build.</span></span> <span data-ttu-id="10323-107">Полный текст сообщения об ошибке подобен приведенному ниже.</span><span class="sxs-lookup"><span data-stu-id="10323-107">The full error message is similar to the following example:</span></span>

<span data-ttu-id="10323-108">**NETSDK1004. Файл ресурсов "C:\путь\to\project.assets.json"не найден. Запустите восстановление пакета NuGet, чтобы создать этот файл.**</span><span class="sxs-lookup"><span data-stu-id="10323-108">**NETSDK1004: Assets file 'C:\path\to\project.assets.json' not found. Run a NuGet package restore to generate this file.**</span></span>

<span data-ttu-id="10323-109">Ниже приведены некоторые возможные причины возникновения этой ошибки.</span><span class="sxs-lookup"><span data-stu-id="10323-109">Here are some possible causes of the error:</span></span>

* <span data-ttu-id="10323-110">Команда `dotnet build` выполняется из пути к каталогу, в котором содержится символ `%`.</span><span class="sxs-lookup"><span data-stu-id="10323-110">You are running the `dotnet build` command from a directory path that contains a `%` character.</span></span> <span data-ttu-id="10323-111">Чтобы устранить эту ошибку, удалите `%` из имени папки и перезапустите `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="10323-111">To resolve the error, remove the `%` from the folder name, and rerun `dotnet build`.</span></span>
* <span data-ttu-id="10323-112">Изменение файла проекта не было автоматически обнаружено и восстановлено системой проекта.</span><span class="sxs-lookup"><span data-stu-id="10323-112">A change to the project file wasn't automatically detected and restored by the project system.</span></span> <span data-ttu-id="10323-113">Чтобы устранить эту ошибку, откройте командную строку и запустите `dotnet restore` в проекте.</span><span class="sxs-lookup"><span data-stu-id="10323-113">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="10323-114">Проект был восстановлен отдельно от более старой версии NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="10323-114">A project was restored separately by an older version of Nuget.exe.</span></span> <span data-ttu-id="10323-115">Чтобы устранить эту ошибку, откройте командную строку и запустите `dotnet restore` в проекте.</span><span class="sxs-lookup"><span data-stu-id="10323-115">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="10323-116">Более ранняя ошибка, например, NETSDK1045 (версия пакета SDK, которую вы используете, не поддерживает целевую платформу проекта), не позволила NuGet создать файл ресурсов проекта.</span><span class="sxs-lookup"><span data-stu-id="10323-116">An earlier error, such as NETSDK1045 (the version of the SDK you're using doesn't support the project's target framework), prevented NuGet from creating the project assets file.</span></span> <span data-ttu-id="10323-117">Чтобы устранить ошибку NETSDK1004, устраните предыдущую ошибку, а затем запустите `dotnet restore` в проекте.</span><span class="sxs-lookup"><span data-stu-id="10323-117">To resolve the NETSDK1004 error, resolve the earlier error, and then run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="10323-118">CI центра приложений — это создание проекта, который содержит внешнюю сборку, которой нет в NuGet.</span><span class="sxs-lookup"><span data-stu-id="10323-118">App Center CI is building a project that has an external assembly that is not in NuGet.</span></span> <span data-ttu-id="10323-119">Чтобы устранить эту ошибку, используйте пакет NuGet для сборки.</span><span class="sxs-lookup"><span data-stu-id="10323-119">To resolve the error, use a NuGet package for the assembly.</span></span>
