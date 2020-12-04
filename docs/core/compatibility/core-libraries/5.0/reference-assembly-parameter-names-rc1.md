---
title: Критическое изменение. В RC2 изменились имена параметров
description: Ознакомьтесь с критическим изменением .NET 5.0 в основных библиотеках .NET, где некоторые имена параметров ссылочных сборок изменились с версий .NET 5.0, выпущенных в виде предварительной версии и версии-кандидата.
ms.date: 11/01/2020
ms.openlocfilehash: 554a4fa9e08fdb504f380465496d7e7e9df85814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759754"
---
# <a name="parameter-names-changed-in-rc2"></a><span data-ttu-id="d9b91-103">В RC2 изменились имена параметров</span><span class="sxs-lookup"><span data-stu-id="d9b91-103">Parameter names changed in RC2</span></span>

<span data-ttu-id="d9b91-104">Некоторые имена параметров ссылочных сборок изменились для соответствия с именами параметров в сборках реализации.</span><span class="sxs-lookup"><span data-stu-id="d9b91-104">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

## <a name="change-description"></a><span data-ttu-id="d9b91-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d9b91-105">Change description</span></span>

<span data-ttu-id="d9b91-106">В предыдущей предварительной версии и версии RC .NET 5.0 некоторые имена параметров [ссылочных сборок](../../../../standard/assembly/reference-assemblies.md) отличаются от соответствующих им параметров в сборке реализации.</span><span class="sxs-lookup"><span data-stu-id="d9b91-106">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="d9b91-107">Это может вызвать проблемы при использовании именованных аргументов и отражения.</span><span class="sxs-lookup"><span data-stu-id="d9b91-107">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="d9b91-108">В .NET 5.0 RC2 несоответствующие имена параметров были изменены в ссылочных сборках, чтобы точно соответствовать именам параметров в сборках реализации.</span><span class="sxs-lookup"><span data-stu-id="d9b91-108">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="d9b91-109">В следующей таблице приведены измененные API-интерфейсы и имена параметров.</span><span class="sxs-lookup"><span data-stu-id="d9b91-109">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="d9b91-110">API</span><span class="sxs-lookup"><span data-stu-id="d9b91-110">API</span></span> | <span data-ttu-id="d9b91-111">Старое имя параметра</span><span class="sxs-lookup"><span data-stu-id="d9b91-111">Old parameter name</span></span> | <span data-ttu-id="d9b91-112">Новое имя параметра</span><span class="sxs-lookup"><span data-stu-id="d9b91-112">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

## <a name="reason-for-change"></a><span data-ttu-id="d9b91-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d9b91-113">Reason for change</span></span>

<span data-ttu-id="d9b91-114">Имена параметров были изменены для согласованности и предотвращения сбоев при использовании именованных аргументов и отражения.</span><span class="sxs-lookup"><span data-stu-id="d9b91-114">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d9b91-115">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d9b91-115">Version introduced</span></span>

<span data-ttu-id="d9b91-116">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="d9b91-116">5.0 RC2</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d9b91-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d9b91-117">Recommended action</span></span>

<span data-ttu-id="d9b91-118">Если возникла ошибка компилятора из-за изменения имени параметра, измените имя параметра соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="d9b91-118">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d9b91-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d9b91-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
