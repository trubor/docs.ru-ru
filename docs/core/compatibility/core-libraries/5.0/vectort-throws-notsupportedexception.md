---
title: Критическое изменение. Vector<T> создает исключение NotSupportedException
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где Vector<T> всегда вызывает исключение для неподдерживаемых параметров типа.
ms.date: 11/01/2020
ms.openlocfilehash: 63db7c6b720735b180ed11098227b31a14008f74
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759769"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="d6151-103">Vector\<T> всегда вызывает исключение NotSupportedException для неподдерживаемых типов</span><span class="sxs-lookup"><span data-stu-id="d6151-103">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="d6151-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> теперь всегда вызывает <xref:System.NotSupportedException> для неподдерживаемых параметров типа.</span><span class="sxs-lookup"><span data-stu-id="d6151-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

## <a name="change-description"></a><span data-ttu-id="d6151-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d6151-105">Change description</span></span>

<span data-ttu-id="d6151-106">Ранее члены <xref:System.Numerics.Vector%601> не всегда вызывали <xref:System.NotSupportedException>, если у `T` был [неподдерживаемый тип](#unsupported-types).</span><span class="sxs-lookup"><span data-stu-id="d6151-106">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="d6151-107">Исключение не всегда вызывалось из-за путей к коду, поддерживающих аппаратное ускорение.</span><span class="sxs-lookup"><span data-stu-id="d6151-107">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="d6151-108">Например, для `Vector<bool> + Vector<bool>` возвращалось `default` вместо вызова исключения на платформах без аппаратного ускорения, например ARM32.</span><span class="sxs-lookup"><span data-stu-id="d6151-108">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="d6151-109">Для неподдерживаемых типов члены <xref:System.Numerics.Vector%601> демонстрируют несогласованное поведение на разных платформах и с разными конфигурациями оборудования.</span><span class="sxs-lookup"><span data-stu-id="d6151-109">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="d6151-110">Начиная с .NET 5.0, члены <xref:System.Numerics.Vector%601> всегда вызывают <xref:System.NotSupportedException> во всех конфигурациях оборудования, если `T` не является поддерживаемым типом.</span><span class="sxs-lookup"><span data-stu-id="d6151-110">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

### <a name="unsupported-types"></a><span data-ttu-id="d6151-111">Неподдерживаемые типы</span><span class="sxs-lookup"><span data-stu-id="d6151-111">Unsupported types</span></span>

<span data-ttu-id="d6151-112">Поддерживаемые типы для параметра типа <xref:System.Numerics.Vector%601>:</span><span class="sxs-lookup"><span data-stu-id="d6151-112">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="d6151-113">Поддерживаемые типы не изменились, но могут измениться в будущем.</span><span class="sxs-lookup"><span data-stu-id="d6151-113">The supported types have not changed, however, they may change in the future.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d6151-114">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d6151-114">Version introduced</span></span>

<span data-ttu-id="d6151-115">5.0</span><span class="sxs-lookup"><span data-stu-id="d6151-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d6151-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d6151-116">Recommended action</span></span>

<span data-ttu-id="d6151-117">Не используйте неподдерживаемый тип для параметра типа <xref:System.Numerics.Vector%601>.</span><span class="sxs-lookup"><span data-stu-id="d6151-117">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d6151-118">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d6151-118">Affected APIs</span></span>

- <span data-ttu-id="d6151-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> и все связанные члены</span><span class="sxs-lookup"><span data-stu-id="d6151-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
