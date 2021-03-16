---
title: Критическое изменение. Файлы Directory.Packages.props импортируются по умолчанию
description: Узнайте о критическом изменении в .NET 5, где файлы PROPS NuGet автоматически импортируют файл с именем Directory.Packages.props, если он находится в папке проекта.
ms.date: 09/17/2020
ms.openlocfilehash: a031d9b2bd832be06dedb20495c24075d1239b02
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256586"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="eafe4-103">Файлы Directory.Packages.props импортируются по умолчанию</span><span class="sxs-lookup"><span data-stu-id="eafe4-103">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="eafe4-104">Файлы *.props* NuGet автоматически импортируют файл с именем *Directory.Packages.props*, если он находится в папке проекта или любом из ее предков.</span><span class="sxs-lookup"><span data-stu-id="eafe4-104">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="eafe4-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="eafe4-105">Version introduced</span></span>

<span data-ttu-id="eafe4-106">5.0</span><span class="sxs-lookup"><span data-stu-id="eafe4-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="eafe4-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="eafe4-107">Change description</span></span>

<span data-ttu-id="eafe4-108">В предыдущих версиях .NET в файле проекта у вас мог быть файл с именем *Directory.Packages.props*, который автоматически не импортировался файлом *.props* NuGet во время сборки.</span><span class="sxs-lookup"><span data-stu-id="eafe4-108">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="eafe4-109">Начиная с .NET 5 такой файл автоматически *импортируется*, если он существует в папке проекта или любом из ее предков.</span><span class="sxs-lookup"><span data-stu-id="eafe4-109">Starting in .NET 5, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="eafe4-110">Если в папке проекта есть файл с таким именем, эта операция автоматического импорта может изменить поведение сборки.</span><span class="sxs-lookup"><span data-stu-id="eafe4-110">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="eafe4-111">Например, файл будет импортирован, но не импортировался ранее, или порядок, в котором он импортируется, может измениться в случае его намеренного импорта.</span><span class="sxs-lookup"><span data-stu-id="eafe4-111">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="eafe4-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="eafe4-112">Reason for change</span></span>

<span data-ttu-id="eafe4-113">Это изменение было внесено для поддержки [централизованного управления версиями пакетов](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) для NuGet.</span><span class="sxs-lookup"><span data-stu-id="eafe4-113">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="eafe4-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="eafe4-114">Recommended action</span></span>

<span data-ttu-id="eafe4-115">Переименуйте существующий файл *Directory.Packages.props*, если он не должен импортироваться автоматически.</span><span class="sxs-lookup"><span data-stu-id="eafe4-115">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="eafe4-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="eafe4-116">Affected APIs</span></span>

<span data-ttu-id="eafe4-117">Н/Д</span><span class="sxs-lookup"><span data-stu-id="eafe4-117">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
