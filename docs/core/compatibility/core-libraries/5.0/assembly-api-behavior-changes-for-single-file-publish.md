---
title: Критическое изменение. Изменения в поведении API, связанные со сборкой, для формата публикации с одним файлом
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где изменилось поведение нескольких интерфейсов API, связанных с расположением файла сборки, когда они вызываются в формате публикации с одним файлом.
ms.date: 11/01/2020
ms.openlocfilehash: 3810a71fac481a42ccf2c8e64149d171f31c6821
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257691"
---
# <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="83ece-103">Изменения в поведении API, связанные со сборкой, для формата публикации с одним файлом</span><span class="sxs-lookup"><span data-stu-id="83ece-103">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="83ece-104">Изменилось поведение нескольких интерфейсов API, связанных с расположением файла сборки, когда они вызываются в формате публикации с одним файлом.</span><span class="sxs-lookup"><span data-stu-id="83ece-104">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

## <a name="change-description"></a><span data-ttu-id="83ece-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="83ece-105">Change description</span></span>

<span data-ttu-id="83ece-106">В публикации с одним файлом для .NET 5 и более поздних версий упакованные сборки загружаются из памяти, а не извлекаются на диск.</span><span class="sxs-lookup"><span data-stu-id="83ece-106">In single-file publishing for .NET 5 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="83ece-107">Для приложений, опубликованных в одном файле, это означает, что определенные интерфейсы API, связанные с расположением, возвращают в .NET 5 и более поздних версиях другие значения по сравнению с предыдущими версиями .NET.</span><span class="sxs-lookup"><span data-stu-id="83ece-107">For single-file published apps, this means that certain location-related APIs return different values on .NET 5 and later than on previous versions of .NET.</span></span> <span data-ttu-id="83ece-108">Изменения заключается в следующем.</span><span class="sxs-lookup"><span data-stu-id="83ece-108">The changes are as follows:</span></span>

| <span data-ttu-id="83ece-109">API</span><span class="sxs-lookup"><span data-stu-id="83ece-109">API</span></span> | <span data-ttu-id="83ece-110">предыдущих версий</span><span class="sxs-lookup"><span data-stu-id="83ece-110">Previous versions</span></span> | <span data-ttu-id="83ece-111">.NET 5 и более поздней версии</span><span class="sxs-lookup"><span data-stu-id="83ece-111">.NET 5 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="83ece-112">Возвращает путь к извлеченному файлу DLL</span><span class="sxs-lookup"><span data-stu-id="83ece-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="83ece-113">Возвращает пустую строку для упакованных сборок</span><span class="sxs-lookup"><span data-stu-id="83ece-113">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="83ece-114">Возвращает путь к извлеченному файлу DLL</span><span class="sxs-lookup"><span data-stu-id="83ece-114">Returns extracted DLL file path</span></span> | <span data-ttu-id="83ece-115">Вызывает исключение для упакованных сборок</span><span class="sxs-lookup"><span data-stu-id="83ece-115">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="83ece-116">Возвращает `null` для упакованных сборок</span><span class="sxs-lookup"><span data-stu-id="83ece-116">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="83ece-117">Вызывает исключение для упакованных сборок</span><span class="sxs-lookup"><span data-stu-id="83ece-117">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="83ece-118">Значением является имя точки входа библиотеки DLL</span><span class="sxs-lookup"><span data-stu-id="83ece-118">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="83ece-119">Значением является имя исполняемого файла узла</span><span class="sxs-lookup"><span data-stu-id="83ece-119">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="83ece-120">Значением является временный каталог извлечения</span><span class="sxs-lookup"><span data-stu-id="83ece-120">Value is the temporary extraction directory</span></span> | <span data-ttu-id="83ece-121">Значением является каталог, содержащий исполняемый файл узла</span><span class="sxs-lookup"><span data-stu-id="83ece-121">Value is the containing directory of the host executable</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="83ece-122">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="83ece-122">Version introduced</span></span>

<span data-ttu-id="83ece-123">5.0</span><span class="sxs-lookup"><span data-stu-id="83ece-123">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="83ece-124">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="83ece-124">Recommended action</span></span>

<span data-ttu-id="83ece-125">Избегайте зависимостей от расположения файлов сборок при публикации в виде одного файла.</span><span class="sxs-lookup"><span data-stu-id="83ece-125">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="83ece-126">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="83ece-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
