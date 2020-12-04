---
title: Критическое изменение. Изменение в поведении для Vector2.Lerp и Vector4.Lerp
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где реализация Vector2.Lerp и Vector4.Lerp изменилась, чтобы корректно учитывать ошибку округления чисел с плавающей запятой.
ms.date: 11/01/2020
ms.openlocfilehash: 8e363a559dba8b7563c40637c47f101d59951216
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759662"
---
# <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="74105-103">Изменение в поведении для Vector2.Lerp и Vector4.Lerp</span><span class="sxs-lookup"><span data-stu-id="74105-103">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="74105-104">Изменена реализация <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> и <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType>, чтобы корректно учитывать ошибку округления чисел с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="74105-104">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

## <a name="change-description"></a><span data-ttu-id="74105-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="74105-105">Change description</span></span>

<span data-ttu-id="74105-106">Ранее <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> и <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> были реализованы как `value1 + (value2 - value1) * amount`.</span><span class="sxs-lookup"><span data-stu-id="74105-106">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="74105-107">Тем не менее, из-за ошибки округления чисел с плавающей запятой этот алгоритм не всегда возвращает `value2`, когда `amount` равно `1.0f`.</span><span class="sxs-lookup"><span data-stu-id="74105-107">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="74105-108">В .NET 5.0 и более поздних версий в реализации используется тот же алгоритм, что и в <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, то есть `(value1 * (1.0f - amount)) + (value2 * amount)`.</span><span class="sxs-lookup"><span data-stu-id="74105-108">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="74105-109">В этом алгоритме корректно учитывается ошибка округления.</span><span class="sxs-lookup"><span data-stu-id="74105-109">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="74105-110">Таким образом, теперь, если `amount` равно `1.0f`, результат будет точно равен `value2`.</span><span class="sxs-lookup"><span data-stu-id="74105-110">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="74105-111">Обновленный алгоритм также может быть свободно оптимизирован с использованием <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> (если доступно).</span><span class="sxs-lookup"><span data-stu-id="74105-111">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="74105-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="74105-112">Version introduced</span></span>

<span data-ttu-id="74105-113">5.0</span><span class="sxs-lookup"><span data-stu-id="74105-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="74105-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="74105-114">Recommended action</span></span>

<span data-ttu-id="74105-115">Никаких действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="74105-115">No action is necessary.</span></span> <span data-ttu-id="74105-116">Если вы хотите сохранить старое поведение, можно реализовать собственную функцию `Lerp`, которая использует предыдущий алгоритм `value1 + (value2 - value1) * amount`.</span><span class="sxs-lookup"><span data-stu-id="74105-116">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="74105-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="74105-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
