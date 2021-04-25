---
title: 'Критическое изменение. Razor: теперь компилятор создает одну сборку'
description: Сведения о критическом изменении в ASP.NET Core 6.0. Теперь компилятор Razor больше не использует двухэтапный процесс компиляции для создания двух отдельных сборок.
no-loc:
- Razor
ms.date: 04/08/2021
ms.openlocfilehash: 8b6817563c4670aebfe681d5f24c8e309d2500ad
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299282"
---
# <a name="razor-compiler-no-longer-produces-a-views-assembly"></a><span data-ttu-id="fd47d-103">Razor: компилятор больше не создает сборку Views</span><span class="sxs-lookup"><span data-stu-id="fd47d-103">Razor: Compiler no longer produces a Views assembly</span></span>

<span data-ttu-id="fd47d-104">Компилятор Razor больше не создает отдельный файл *Views.dll*, содержащий представления CSHTML, определенные в приложении.</span><span class="sxs-lookup"><span data-stu-id="fd47d-104">The Razor compiler no longer produces a separate *Views.dll* file that contains the CSHTML views defined in an application.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fd47d-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="fd47d-105">Version introduced</span></span>

<span data-ttu-id="fd47d-106">ASP.NET Core 6.0 (предварительная версия 3)</span><span class="sxs-lookup"><span data-stu-id="fd47d-106">ASP.NET Core 6.0 Preview 3</span></span>

## <a name="old-behavior"></a><span data-ttu-id="fd47d-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="fd47d-107">Old behavior</span></span>

<span data-ttu-id="fd47d-108">В предыдущих версиях компилятор Razor использует двухэтапный процесс компиляции, создающий два файла:</span><span class="sxs-lookup"><span data-stu-id="fd47d-108">In previous versions, the Razor compiler utilizes a two-step compilation process that produces two files:</span></span>

- <span data-ttu-id="fd47d-109">главная сборка *AppName.dll*, которая содержит типы приложений;</span><span class="sxs-lookup"><span data-stu-id="fd47d-109">A main *AppName.dll* assembly that contains application types.</span></span>
- <span data-ttu-id="fd47d-110">сборка *AppName.Views.dll*, которая содержит созданные представления, определенные в приложении.</span><span class="sxs-lookup"><span data-stu-id="fd47d-110">An *AppName.Views.dll* assembly that contains the generated views that are defined in the app.</span></span> <span data-ttu-id="fd47d-111">Созданные представления относятся к типу `public` и принадлежат пространству имен `AspNetCore`.</span><span class="sxs-lookup"><span data-stu-id="fd47d-111">Generated view types are `public` and under the `AspNetCore` namespace.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="fd47d-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="fd47d-112">New behavior</span></span>

<span data-ttu-id="fd47d-113">Типы представлений и приложений включены в одну сборку *AppName.dll*.</span><span class="sxs-lookup"><span data-stu-id="fd47d-113">Both views and application types are included in a single *AppName.dll* assembly.</span></span> <span data-ttu-id="fd47d-114">Типы представлений по умолчанию имеют модификаторы доступа `internal` и `sealed` и включены в пространство имен `AspNetCoreGeneratedDocument`.</span><span class="sxs-lookup"><span data-stu-id="fd47d-114">View types have the accessibility modifiers `internal` and `sealed`, by default, and are included under the `AspNetCoreGeneratedDocument` namespace.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="fd47d-115">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="fd47d-115">Reason for change</span></span>

<span data-ttu-id="fd47d-116">Отказ от двухэтапного процесса компиляции:</span><span class="sxs-lookup"><span data-stu-id="fd47d-116">Removing the two-step compilation process:</span></span>

* <span data-ttu-id="fd47d-117">улучшает сборку приложений, использующих представления Razor;</span><span class="sxs-lookup"><span data-stu-id="fd47d-117">Improves build performance for applications that use Razor views.</span></span>
* <span data-ttu-id="fd47d-118">позволяет использовать представления Razor в функциях горячей перезагрузки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd47d-118">Allows Razor views to participate in the "hot reload" experience for Visual Studio.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fd47d-119">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="fd47d-119">Recommended action</span></span>

<span data-ttu-id="fd47d-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fd47d-120">None.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fd47d-121">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="fd47d-121">Affected APIs</span></span>

<span data-ttu-id="fd47d-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fd47d-122">None.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
