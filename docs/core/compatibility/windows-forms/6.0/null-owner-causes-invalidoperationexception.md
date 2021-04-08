---
title: Критическое изменение в .NET 6. API, связанные с DataGridView, вызывают исключение InvalidOperationException
description: Сведения о критическом изменении в .NET 6, где некоторые API, связанные с DataGridView, вызовут исключение, если значение DataGridViewCellAccessibleObject.Owner объекта равно NULL.
ms.date: 03/29/2021
ms.openlocfilehash: 3726296bb93c88d438e45ea832bf9070ace69dd0
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106080668"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="5d707-103">API, связанные с DataGridView, теперь вызывают исключение InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="5d707-103">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="5d707-104">Некоторые API, связанные с <xref:System.Windows.Forms.DataGridView>, теперь вызывают <xref:System.InvalidOperationException>, если значение объекта <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> — `null`.</span><span class="sxs-lookup"><span data-stu-id="5d707-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="5d707-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="5d707-105">Change description</span></span>

<span data-ttu-id="5d707-106">В предыдущих версиях .NET затронутые API выдают <xref:System.NullReferenceException> при вызове, если для свойства <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> задано значение `null`.</span><span class="sxs-lookup"><span data-stu-id="5d707-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null`.</span></span> <span data-ttu-id="5d707-107">Начиная с .NET 6 эти API создают <xref:System.InvalidOperationException>, а не <xref:System.NullReferenceException>, если при их вызове свойство <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="5d707-107">Starting in .NET 6, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null` when they're invoked.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5d707-108">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="5d707-108">Reason for change</span></span>

<span data-ttu-id="5d707-109">Вызов <xref:System.InvalidOperationException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="5d707-109">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="5d707-110">Это также улучшает процесс отладки, четко указывая недопустимое свойство.</span><span class="sxs-lookup"><span data-stu-id="5d707-110">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5d707-111">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="5d707-111">Version introduced</span></span>

<span data-ttu-id="5d707-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="5d707-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5d707-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="5d707-113">Recommended action</span></span>

<span data-ttu-id="5d707-114">Проверьте код и при необходимости обновите его, чтобы не допустить создания затрагиваемых типов с помощью свойства <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> как `null`.</span><span class="sxs-lookup"><span data-stu-id="5d707-114">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5d707-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5d707-115">Affected APIs</span></span>

<span data-ttu-id="5d707-116">В следующей таблице перечислены затронутые свойства и методы.</span><span class="sxs-lookup"><span data-stu-id="5d707-116">The following table lists the affected properties and methods:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="5d707-117">Затронутый метод или свойство</span><span class="sxs-lookup"><span data-stu-id="5d707-117">Affected method or property</span></span> | <span data-ttu-id="5d707-118">Добавлено в версии</span><span class="sxs-lookup"><span data-stu-id="5d707-118">Version added</span></span> |
> |-|-|
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds?displayProperty=fullName> | <span data-ttu-id="5d707-119">Предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="5d707-119">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction?displayProperty=fullName> | <span data-ttu-id="5d707-120">Предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="5d707-120">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name?displayProperty=fullName> | <span data-ttu-id="5d707-121">Предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="5d707-121">Preview 4</span></span> |
>| <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=fullName> | <span data-ttu-id="5d707-122">Предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="5d707-122">Preview 4</span></span> |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State?displayProperty=fullName> | <span data-ttu-id="5d707-123">Предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="5d707-123">Preview 4</span></span> |

## <a name="see-also"></a><span data-ttu-id="5d707-124">См. также</span><span class="sxs-lookup"><span data-stu-id="5d707-124">See also</span></span>

- [<span data-ttu-id="5d707-125">API, связанные с DataGridView, вызывают исключение InvalidOperationException (.NET 5)</span><span class="sxs-lookup"><span data-stu-id="5d707-125">DataGridView-related APIs throw InvalidOperationException (.NET 5)</span></span>](../5.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name`
- `M:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State`

### Category

Windows Forms

-->
