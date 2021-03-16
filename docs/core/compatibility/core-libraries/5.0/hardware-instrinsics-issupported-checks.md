---
title: Критическое изменение. Встроенные проверки IsSupported, поддерживаемые оборудованием, могут отличаться для вложенных типов
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где проверка X64.IsSupported для аппаратных встроенных функций может привести к другим результатам.
ms.date: 11/01/2020
ms.openlocfilehash: 5c6049ad5881c0389870cfd5e1550f8358c67599
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257457"
---
# <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a><span data-ttu-id="d6d67-103">Встроенные проверки IsSupported, поддерживаемые оборудованием, могут отличаться для вложенных типов</span><span class="sxs-lookup"><span data-stu-id="d6d67-103">Hardware intrinsic IsSupported checks may differ for nested types</span></span>

<span data-ttu-id="d6d67-104">Проверка `<Isa>.X64.IsSupported`, где `<Isa>` ссылается на классы в пространстве имен <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType>, теперь может привести к другим результатам в предыдущих версиях .NET.</span><span class="sxs-lookup"><span data-stu-id="d6d67-104">Checking `<Isa>.X64.IsSupported`, where `<Isa>` refers to the classes in the <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, may now produce a different result to previous versions of .NET.</span></span>

> [!TIP]
> <span data-ttu-id="d6d67-105">*ISA* означает стандартную промышленную архитектуру.</span><span class="sxs-lookup"><span data-stu-id="d6d67-105">*ISA* stands for industry standard architecture.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d6d67-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d6d67-106">Version introduced</span></span>

<span data-ttu-id="d6d67-107">5.0</span><span class="sxs-lookup"><span data-stu-id="d6d67-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="d6d67-108">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d6d67-108">Change description</span></span>

<span data-ttu-id="d6d67-109">В предыдущих версиях .NET некоторые встроенные в оборудование типы <xref:System.Runtime.Intrinsics.X86>, например <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, не содержали вложенный класс `X64`.</span><span class="sxs-lookup"><span data-stu-id="d6d67-109">In previous versions of .NET, some of the <xref:System.Runtime.Intrinsics.X86> hardware-intrinsic types, for example, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, didn't expose a nested `X64` class.</span></span> <span data-ttu-id="d6d67-110">Для этих типов вызов `<Isa>.X64.IsSupported` разрешался в свойство `IsSupported` вложенного класса `X64` родительского класса `<Isa>`.</span><span class="sxs-lookup"><span data-stu-id="d6d67-110">For these types, calling `<Isa>.X64.IsSupported` resolved to an `IsSupported` property on a nested `X64` class of a parent class of `<Isa>`.</span></span> <span data-ttu-id="d6d67-111">Это означало, что свойство может возвращать `true` даже тогда, когда `<Isa>.IsSupported` возвращает `false`.</span><span class="sxs-lookup"><span data-stu-id="d6d67-111">This meant that the property could return `true` even when `<Isa>.IsSupported` returns `false`.</span></span>

<span data-ttu-id="d6d67-112">В .NET 5 и более поздних версиях все типы <xref:System.Runtime.Intrinsics.X86> предоставляют вложенный класс `X64`, который поддерживает соответствующие отчеты.</span><span class="sxs-lookup"><span data-stu-id="d6d67-112">In .NET 5 and later versions, all of the <xref:System.Runtime.Intrinsics.X86> types expose a nested `X64` class that appropriately reports support.</span></span> <span data-ttu-id="d6d67-113">Это гарантирует, что общая иерархия останется правильной и что если `<Isa>.X64.IsSupported` `true`, то `<Isa>.IsSupported` также может считаться `true`.</span><span class="sxs-lookup"><span data-stu-id="d6d67-113">This ensures that the general hierarchy remains correct, and that if `<Isa>.X64.IsSupported` is `true`, then `<Isa>.IsSupported` can also be assumed to be `true`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d6d67-114">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d6d67-114">Reason for change</span></span>

<span data-ttu-id="d6d67-115">Предполагалось, что если `<Isa>.X64.IsSupported` `true`, то `<Isa>.IsSupported` также предполагается `true`.</span><span class="sxs-lookup"><span data-stu-id="d6d67-115">It was intended that if `<Isa>.X64.IsSupported` is `true`, `<Isa>.IsSupported` is also implied to be `true`.</span></span> <span data-ttu-id="d6d67-116">Тем не менее, из-за того, как работает разрешение члена C#, классы, у которых нет вложенного класса `X64`, это было не всегда, что приводило к ошибкам в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="d6d67-116">However, due to how member resolution works in C#, classes that didn't have a nested `X64` class exposed a situation where this wasn't always the case and led to bugs in user code.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d6d67-117">Рекомендуемое действие</span><span class="sxs-lookup"><span data-stu-id="d6d67-117">Recommended action</span></span>

<span data-ttu-id="d6d67-118">При необходимости настройте код, проверяющий `IsSupported` для поиска соответствующего ISA.</span><span class="sxs-lookup"><span data-stu-id="d6d67-118">If necessary, adjust code that checks `IsSupported` to check for the appropriate ISA.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d6d67-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d6d67-119">Affected APIs</span></span>

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
