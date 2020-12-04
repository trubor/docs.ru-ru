---
title: Критическое изменение. Встроенные проверки IsSupported, поддерживаемые оборудованием, могут отличаться для вложенных типов
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где проверка X64.IsSupported для аппаратных встроенных функций может привести к другим результатам.
ms.date: 11/01/2020
ms.openlocfilehash: 9acef15860de76a9743621cb4c5edba5aac3931c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759826"
---
# <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a><span data-ttu-id="5ee9b-103">Встроенные проверки IsSupported, поддерживаемые оборудованием, могут отличаться для вложенных типов</span><span class="sxs-lookup"><span data-stu-id="5ee9b-103">Hardware intrinsic IsSupported checks may differ for nested types</span></span>

<span data-ttu-id="5ee9b-104">Проверка `<Isa>.X64.IsSupported`, где `<Isa>` ссылается на классы в пространстве имен <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType>, теперь может привести к другим результатам в предыдущих версиях .NET.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-104">Checking `<Isa>.X64.IsSupported`, where `<Isa>` refers to the classes in the <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, may now produce a different result to previous versions of .NET.</span></span>

> [!TIP]
> <span data-ttu-id="5ee9b-105">*ISA* означает стандартную промышленную архитектуру.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-105">*ISA* stands for industry standard architecture.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5ee9b-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="5ee9b-106">Version introduced</span></span>

<span data-ttu-id="5ee9b-107">5.0</span><span class="sxs-lookup"><span data-stu-id="5ee9b-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="5ee9b-108">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="5ee9b-108">Change description</span></span>

<span data-ttu-id="5ee9b-109">В предыдущих версиях .NET некоторые встроенные в оборудование типы <xref:System.Runtime.Intrinsics.X86>, например <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, не содержали вложенный класс `X64`.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-109">In previous versions of .NET, some of the <xref:System.Runtime.Intrinsics.X86> hardware-intrinsic types, for example, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, didn't expose a nested `X64` class.</span></span> <span data-ttu-id="5ee9b-110">Для этих типов вызов `<Isa>.X64.IsSupported` разрешался в свойство `IsSupported` вложенного класса `X64` родительского класса `<Isa>`.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-110">For these types, calling `<Isa>.X64.IsSupported` resolved to an `IsSupported` property on a nested `X64` class of a parent class of `<Isa>`.</span></span> <span data-ttu-id="5ee9b-111">Это означало, что свойство может возвращать `true` даже тогда, когда `<Isa>.IsSupported` возвращает `false`.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-111">This meant that the property could return `true` even when `<Isa>.IsSupported` returns `false`.</span></span>

<span data-ttu-id="5ee9b-112">В .NET 5.0 и более поздних версиях все типы <xref:System.Runtime.Intrinsics.X86> предоставляют вложенный класс `X64`, который поддерживает соответствующие отчеты.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-112">In .NET 5.0 and later versions, all of the <xref:System.Runtime.Intrinsics.X86> types expose a nested `X64` class that appropriately reports support.</span></span> <span data-ttu-id="5ee9b-113">Это гарантирует, что общая иерархия останется правильной и что если `<Isa>.X64.IsSupported` `true`, то `<Isa>.IsSupported` также может считаться `true`.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-113">This ensures that the general hierarchy remains correct, and that if `<Isa>.X64.IsSupported` is `true`, then `<Isa>.IsSupported` can also be assumed to be `true`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5ee9b-114">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="5ee9b-114">Reason for change</span></span>

<span data-ttu-id="5ee9b-115">Предполагалось, что если `<Isa>.X64.IsSupported` `true`, то `<Isa>.IsSupported` также предполагается `true`.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-115">It was intended that if `<Isa>.X64.IsSupported` is `true`, `<Isa>.IsSupported` is also implied to be `true`.</span></span> <span data-ttu-id="5ee9b-116">Тем не менее, из-за того, как работает разрешение члена C#, классы, у которых нет вложенного класса `X64`, это было не всегда, что приводило к ошибкам в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-116">However, due to how member resolution works in C#, classes that didn't have a nested `X64` class exposed a situation where this wasn't always the case and led to bugs in user code.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5ee9b-117">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="5ee9b-117">Recommended action</span></span>

<span data-ttu-id="5ee9b-118">При необходимости настройте код, проверяющий `IsSupported` для поиска соответствующего ISA.</span><span class="sxs-lookup"><span data-stu-id="5ee9b-118">If necessary, adjust code that checks `IsSupported` to check for the appropriate ISA.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5ee9b-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5ee9b-119">Affected APIs</span></span>

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
