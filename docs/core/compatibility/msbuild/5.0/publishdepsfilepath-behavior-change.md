---
title: Критическое изменение. Изменение поведения PublishDepsFilePath
description: Сведения о критическом изменении в .NET 5, где свойство MSBuild PublishDepsFilePath пусто для однофайловых приложений.
ms.date: 09/17/2020
ms.openlocfilehash: 845073e73ec6bdf820f28ace487d9ae4d04d0790
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872929"
---
# <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="5fb99-103">Изменение поведения PublishDepsFilePath</span><span class="sxs-lookup"><span data-stu-id="5fb99-103">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="5fb99-104">Свойство MSBuild `PublishDepsFilePath` пусто для однофайловых приложений.</span><span class="sxs-lookup"><span data-stu-id="5fb99-104">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="5fb99-105">Кроме того, для приложений с несколькими файлами файл *deps.json* может быть скопирован в выходной каталог только на более поздних этапах сборки.</span><span class="sxs-lookup"><span data-stu-id="5fb99-105">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5fb99-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="5fb99-106">Version introduced</span></span>

<span data-ttu-id="5fb99-107">5.0</span><span class="sxs-lookup"><span data-stu-id="5fb99-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="5fb99-108">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="5fb99-108">Change description</span></span>

<span data-ttu-id="5fb99-109">В предыдущих версиях .NET свойство MSBuild `PublishDepsFilePath` является путем к файлу *deps.json* приложения в выходном каталоге для приложений с несколькими файлами и путем в промежуточном каталоге для однофайловых приложений.</span><span class="sxs-lookup"><span data-stu-id="5fb99-109">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="5fb99-110">Начиная с .NET 5 свойство `PublishDepsFilePath` пусто для однофайловых приложений, а новое свойство `IntermediateDepsFilePath` указывает расположение файла *deps.json* в промежуточном каталоге.</span><span class="sxs-lookup"><span data-stu-id="5fb99-110">Starting in .NET 5, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="5fb99-111">Кроме того, для приложений с несколькими файлами файл *deps.json* может быть скопирован в выходной каталог (т. е. по пути, указанному в `PublishDepsFilePath`) только на более поздних этапах сборки.</span><span class="sxs-lookup"><span data-stu-id="5fb99-111">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5fb99-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="5fb99-112">Reason for change</span></span>

<span data-ttu-id="5fb99-113">Это изменение было внесено по нескольким причинам.</span><span class="sxs-lookup"><span data-stu-id="5fb99-113">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="5fb99-114">Из-за рефакторинга логики публикации для поддержки [улучшенных однофайловых приложений](https://github.com/dotnet/designs/blob/main/accepted/2020/single-file/design.md) в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="5fb99-114">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/main/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="5fb99-115">Для защиты однофайловых приложений от целевых объектов, которые пытаются перезаписать файл *deps.json* уже после его объединения в пакет, без влияния на приложение.</span><span class="sxs-lookup"><span data-stu-id="5fb99-115">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="5fb99-116">Поэтому свойство MSBuild `PublishDepsFilePath` пусто для однофайловых приложений.</span><span class="sxs-lookup"><span data-stu-id="5fb99-116">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5fb99-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="5fb99-117">Recommended action</span></span>

<span data-ttu-id="5fb99-118">Целевые объекты, которые перезаписывают файл *deps.json*, обычно используют для этого свойство `IntermediateDepsFilePath`.</span><span class="sxs-lookup"><span data-stu-id="5fb99-118">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5fb99-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5fb99-119">Affected APIs</span></span>

<span data-ttu-id="5fb99-120">Н/Д</span><span class="sxs-lookup"><span data-stu-id="5fb99-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
