---
title: Критическое изменение в .NET 5. API, связанные с DataGridView, вызывают исключение InvalidOperationException
description: Сведения о критическом изменении в .NET 5, где некоторые интерфейсы API, связанные с DataGridView, вызовут исключение, если значение DataGridViewCellAccessibleObject.Owner объекта равно NULL.
ms.date: 09/18/2020
ms.openlocfilehash: 57ff50d7bdc83286d4d452746e8f64bace187edb
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079600"
---
# <a name="datagridview-related-apis-throw-invalidoperationexception"></a><span data-ttu-id="f1beb-103">API, связанные с DataGridView, вызывают исключение InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="f1beb-103">DataGridView-related APIs throw InvalidOperationException</span></span>

<span data-ttu-id="f1beb-104">Некоторые API, связанные с <xref:System.Windows.Forms.DataGridView>, теперь вызывают <xref:System.InvalidOperationException>, если значение объекта <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> — `null`.</span><span class="sxs-lookup"><span data-stu-id="f1beb-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="f1beb-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="f1beb-105">Change description</span></span>

<span data-ttu-id="f1beb-106">В предыдущих версиях .NET затронутые API выдают <xref:System.NullReferenceException> при вызове, если для свойства <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> задано значение `null`.</span><span class="sxs-lookup"><span data-stu-id="f1beb-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null`.</span></span> <span data-ttu-id="f1beb-107">Начиная с .NET 5 эти API создают <xref:System.InvalidOperationException>, а не <xref:System.NullReferenceException>, если при их вызове свойство <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="f1beb-107">Starting in .NET 5, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property value is `null` when they're invoked.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f1beb-108">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="f1beb-108">Reason for change</span></span>

<span data-ttu-id="f1beb-109">Вызов <xref:System.InvalidOperationException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="f1beb-109">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="f1beb-110">Это также улучшает процесс отладки, четко указывая недопустимое свойство.</span><span class="sxs-lookup"><span data-stu-id="f1beb-110">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f1beb-111">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="f1beb-111">Version introduced</span></span>

<span data-ttu-id="f1beb-112">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-112">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f1beb-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="f1beb-113">Recommended action</span></span>

<span data-ttu-id="f1beb-114">Проверьте код и при необходимости обновите его, чтобы не допустить создания затрагиваемых типов с помощью свойства <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> как `null`.</span><span class="sxs-lookup"><span data-stu-id="f1beb-114">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f1beb-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="f1beb-115">Affected APIs</span></span>

<span data-ttu-id="f1beb-116">Затронутые API перечислены в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="f1beb-116">The following table lists the affected APIs:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="f1beb-117">Затронутый метод или свойство</span><span class="sxs-lookup"><span data-stu-id="f1beb-117">Affected method or property</span></span> | <span data-ttu-id="f1beb-118">Проверенное свойство</span><span class="sxs-lookup"><span data-stu-id="f1beb-118">Validated property</span></span> | <span data-ttu-id="f1beb-119">Добавлено в версии</span><span class="sxs-lookup"><span data-stu-id="f1beb-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-120">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-121">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-122">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-123">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-124">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-125">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-126">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-127">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-128">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-129">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-130">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-130">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="f1beb-131">5.0</span><span class="sxs-lookup"><span data-stu-id="f1beb-131">5.0</span></span> |

## <a name="see-also"></a><span data-ttu-id="f1beb-132">См. также</span><span class="sxs-lookup"><span data-stu-id="f1beb-132">See also</span></span>

- [<span data-ttu-id="f1beb-133">API, связанные с DataGridView, вызывают исключение InvalidOperationException (.NET 6)</span><span class="sxs-lookup"><span data-stu-id="f1beb-133">DataGridView-related APIs throw InvalidOperationException (.NET 6)</span></span>](../6.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `M:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State`
- `M:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `M:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction`

### Category

Windows Forms

-->
