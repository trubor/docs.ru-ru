---
title: Критическое изменение. API, связанные с DataGridView, вызывают исключение InvalidOperationException
description: Сведения о критическом изменении в .NET 5.0, где некоторые интерфейсы API, связанные с DataGridView, вызовут исключение, если значение DataGridViewCellAccessibleObject.Owner объекта равно NULL.
ms.date: 09/18/2020
ms.openlocfilehash: 927b1c9160700159a45aa1472b8d96f1a9ecfe25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759910"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="e31a2-103">API, связанные с DataGridView, теперь вызывают исключение InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="e31a2-103">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="e31a2-104">Некоторые API, связанные с <xref:System.Windows.Forms.DataGridView>, теперь вызывают <xref:System.InvalidOperationException>, если значение объекта <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> — `null`.</span><span class="sxs-lookup"><span data-stu-id="e31a2-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="e31a2-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="e31a2-105">Change description</span></span>

<span data-ttu-id="e31a2-106">В предыдущих версиях .NET затронутые API выдают <xref:System.NullReferenceException> при вызове, а значение <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> — `null`.</span><span class="sxs-lookup"><span data-stu-id="e31a2-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null`.</span></span> <span data-ttu-id="e31a2-107">Начиная с .NET 5.0 эти API создают <xref:System.InvalidOperationException>, а не <xref:System.NullReferenceException>, если при вызове значение <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> — `null`.</span><span class="sxs-lookup"><span data-stu-id="e31a2-107">Starting in .NET 5.0, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null` when they are invoked.</span></span>

<span data-ttu-id="e31a2-108">Вызов <xref:System.InvalidOperationException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="e31a2-108">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="e31a2-109">Это также улучшает процесс отладки, четко указывая недопустимое свойство.</span><span class="sxs-lookup"><span data-stu-id="e31a2-109">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e31a2-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="e31a2-110">Version introduced</span></span>

<span data-ttu-id="e31a2-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e31a2-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="e31a2-112">Recommended action</span></span>

<span data-ttu-id="e31a2-113">Проверьте код и при необходимости обновите его, чтобы не допустить создания затрагиваемых типов с помощью свойства <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> как `null`.</span><span class="sxs-lookup"><span data-stu-id="e31a2-113">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e31a2-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="e31a2-114">Affected APIs</span></span>

<span data-ttu-id="e31a2-115">В следующей таблице перечислены затронутые свойства и параметры.</span><span class="sxs-lookup"><span data-stu-id="e31a2-115">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="e31a2-116">Затронутый метод или свойство</span><span class="sxs-lookup"><span data-stu-id="e31a2-116">Affected method or property</span></span> | <span data-ttu-id="e31a2-117">Проверенное свойство</span><span class="sxs-lookup"><span data-stu-id="e31a2-117">Validated property</span></span> | <span data-ttu-id="e31a2-118">Добавлено в версии</span><span class="sxs-lookup"><span data-stu-id="e31a2-118">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-119">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-119">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-120">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-121">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-122">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-123">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-124">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-125">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-126">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-127">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-128">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-129">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="e31a2-130">5.0</span><span class="sxs-lookup"><span data-stu-id="e31a2-130">5.0</span></span> |

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
