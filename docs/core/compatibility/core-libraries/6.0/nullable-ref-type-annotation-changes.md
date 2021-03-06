---
title: Критическое изменение. Изменения в заметках ссылочного типа, допускающих значения NULL
description: Ознакомьтесь с критическим изменением .NET 6.0 в основных библиотеках .NET, в которых изменились некоторые заметки ссылочного типа, допускающие значения NULL.
ms.date: 02/11/2021
ms.openlocfilehash: a0133ce49ba33d0e835b718f3f2b19180526c61b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488226"
---
# <a name="changes-to-nullable-reference-type-annotations"></a><span data-ttu-id="fe3e7-103">Изменения в заметках ссылочного типа, допускающих значения NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-103">Changes to nullable reference type annotations</span></span>

<span data-ttu-id="fe3e7-104">В .NET 6.0 некоторые заметки о допустимости значений NULL в библиотеках .NET были изменены.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-104">In .NET 6.0, some nullability annotations in the .NET libraries have changed.</span></span>

## <a name="change-description"></a><span data-ttu-id="fe3e7-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="fe3e7-105">Change description</span></span>

<span data-ttu-id="fe3e7-106">В предыдущих версиях .NET некоторые заметки ссылочного типа, допускающие значения NULL, не верны, а предупреждения сборки либо отсутствуют, либо неверны.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-106">In previous .NET versions, some nullable reference type annotations are incorrect, and build warnings are either absent or incorrect.</span></span> <span data-ttu-id="fe3e7-107">Начиная с .NET 6.0, были обновлены некоторые заметки, которые применялись ранее.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-107">Starting in .NET 6.0, some annotations that were previously applied have been updated.</span></span> <span data-ttu-id="fe3e7-108">Будут созданы новые предупреждения сборки, а неправильные предупреждения сборки для затронутых API больше не будут создаваться.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-108">New build warnings will be produced and incorrect build warnings will no longer be produced for the affected APIs.</span></span>

<span data-ttu-id="fe3e7-109">Некоторые из этих изменений считаются *критическими*, поскольку они могут привести к появлению новых предупреждений во время сборки.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-109">Some of these changes are considered to be *breaking* because they can lead to new build-time warnings.</span></span> <span data-ttu-id="fe3e7-110">При переходе на .NET 6.0 необходимо обновить код, который ссылается на такие API.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-110">When you migrate to .NET 6.0, code that references these APIs will need to be updated.</span></span>

<span data-ttu-id="fe3e7-111">Другие изменения, которые не считаются критическими, также описаны на этой странице.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-111">Other changes that aren't considered to be breaking are also documented on this page.</span></span> <span data-ttu-id="fe3e7-112">Любой код, ссылающийся на обновленные API, может стать эффективнее за счет удаления операторов или прагм, которые больше не нужны.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-112">Any code that references the updated APIs may benefit from removing operators or pragmas that are no longer unnecessary.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fe3e7-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="fe3e7-113">Version introduced</span></span>

<span data-ttu-id="fe3e7-114">6,0</span><span class="sxs-lookup"><span data-stu-id="fe3e7-114">6.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="fe3e7-115">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="fe3e7-115">Reason for change</span></span>

<span data-ttu-id="fe3e7-116">Начиная с .NET Core 3.0, к библиотекам .NET были применены заметки о допустимости значений NULL.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-116">Starting in .NET Core 3.0, nullability annotations were applied to the .NET libraries.</span></span> <span data-ttu-id="fe3e7-117">С самого начала ожидались ошибки в этих заметках.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-117">From the outset of the effort, mistakes in these annotations were anticipated.</span></span> <span data-ttu-id="fe3e7-118">Благодаря отзывам и дальнейшему тестированию заметки, допускающие значение NULL для затрагиваемых API, были определены как неточные.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-118">Through feedback and further testing, the nullable annotations for the affected APIs were determined to be inaccurate.</span></span> <span data-ttu-id="fe3e7-119">В обновленных заметках правильно представлены контракты допустимости значений NULL для API.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-119">The updated annotations correctly represent the nullability contracts for the APIs.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fe3e7-120">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="fe3e7-120">Recommended action</span></span>

<span data-ttu-id="fe3e7-121">Обновите код, в результате выполнения которого API отражают изменения в контрактах, допускающих значения NULL.</span><span class="sxs-lookup"><span data-stu-id="fe3e7-121">Update code that calls these APIs to reflect the revised nullability contracts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fe3e7-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="fe3e7-122">Affected APIs</span></span>

<span data-ttu-id="fe3e7-123">Затронутые API перечислены в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="fe3e7-123">The following table lists the affected APIs:</span></span>

| <span data-ttu-id="fe3e7-124">API</span><span class="sxs-lookup"><span data-stu-id="fe3e7-124">API</span></span> | <span data-ttu-id="fe3e7-125">Изменения</span><span class="sxs-lookup"><span data-stu-id="fe3e7-125">What changed</span></span> | <span data-ttu-id="fe3e7-126">Критическое или некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-126">Breaking or nonbreaking</span></span> | <span data-ttu-id="fe3e7-127">Добавлено в версии</span><span class="sxs-lookup"><span data-stu-id="fe3e7-127">Version added</span></span> |
| - | - | - |
| <xref:System.ComponentModel.ISite.Container?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-128">Тип свойства допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-128">Property type is nullable</span></span> | <span data-ttu-id="fe3e7-129">Критическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-129">Breaking</span></span> | <span data-ttu-id="fe3e7-130">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-130">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.Add(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-131">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-131">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-132">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-132">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-133">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-133">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.AddFirst(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-134">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-134">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-135">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-135">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-136">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-136">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-137">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-137">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-138">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-138">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-139">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-139">Preview 1</span></span> |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Object[])> | <span data-ttu-id="fe3e7-140">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-140">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-141">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-141">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-142">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-142">Preview 1</span></span> |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Xml.Linq.XDeclaration,System.Object[])> | <span data-ttu-id="fe3e7-143">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-143">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-144">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-144">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-145">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-145">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | <span data-ttu-id="fe3e7-146">Тип второго параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-146">Second parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-147">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-147">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-148">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-148">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.ReplaceAll(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-149">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-149">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-150">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-150">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-151">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-151">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-152">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-152">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-153">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-153">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-154">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-154">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-155">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-155">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-156">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-156">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-157">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-157">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-158">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-158">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-159">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-159">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-160">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-160">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.ReplaceWith(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-161">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-161">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-162">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-162">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-163">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-163">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object)> | <span data-ttu-id="fe3e7-164">Тип второго параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-164">Second parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-165">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-165">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-166">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-166">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | <span data-ttu-id="fe3e7-167">Тип второго параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-167">Second parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-168">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-168">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-169">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-169">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.Add(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-170">Тип параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-170">Parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-171">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-171">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-172">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-172">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PatchAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-173">Тип параметра `content` допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-173">`content` parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-174">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-174">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-175">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-175">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PostAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-176">Тип параметра `content` допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-176">`content` parameter type is nullable</span></span>  | <span data-ttu-id="fe3e7-177">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-177">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-178">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-178">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PutAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-179">Тип параметра `content` допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-179">`content` parameter type is nullable</span></span>  | <span data-ttu-id="fe3e7-180">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-180">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-181">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-181">Preview 1</span></span> |
| <xref:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-182">Тип первого параметра допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-182">First parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-183">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-183">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-184">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-184">Preview 1</span></span> |
| <xref:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-185">Тип возвращаемого значения не допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-185">Return type is not nullable</span></span> | <span data-ttu-id="fe3e7-186">Некритическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-186">Nonbreaking</span></span> | <span data-ttu-id="fe3e7-187">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-187">Preview 1</span></span> |
| <xref:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-188">Тип параметра `buffer` допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-188">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-189">Критическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-189">Breaking</span></span> | <span data-ttu-id="fe3e7-190">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-190">Preview 1</span></span> |
| <xref:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-191">Тип параметра `buffer` допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-191">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-192">Критическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-192">Breaking</span></span> | <span data-ttu-id="fe3e7-193">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-193">Preview 1</span></span> |
| <xref:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-194">Тип параметра `buffer` допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-194">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-195">Критическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-195">Breaking</span></span> | <span data-ttu-id="fe3e7-196">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-196">Preview 1</span></span> |
| <xref:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="fe3e7-197">Тип параметра `buffer` допускает значение NULL</span><span class="sxs-lookup"><span data-stu-id="fe3e7-197">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="fe3e7-198">Критическое</span><span class="sxs-lookup"><span data-stu-id="fe3e7-198">Breaking</span></span> | <span data-ttu-id="fe3e7-199">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="fe3e7-199">Preview 1</span></span> |

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.ComponentModel.ISite.Container`
- `M:System.Xml.Linq.XContainer.Add(System.Object[])`
- `M:System.Xml.Linq.XContainer.AddFirst(System.Object[])`
- `M:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Xml.Linq.XDeclaration,System.Object[])`
- `M:System.Xml.Linq.XElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAll(System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])`
- `M:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.ReplaceWith(System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object)`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.Add(System.Object[])`
- `O:System.Net.Http.HttpClient.PatchAsync`
- `O:System.Net.Http.HttpClient.PostAsync`
- `O:System.Net.Http.HttpClient.PutAsync`
- `M:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})`
- `M:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})`
- `M:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`

-->