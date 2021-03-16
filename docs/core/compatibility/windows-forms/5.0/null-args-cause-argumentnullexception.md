---
title: Критическое изменение. Теперь методы WinForms вызывают исключение ArgumentNullException
description: Сведения о критическом изменении в .NET 5, где некоторые методы Windows Forms теперь вызывают исключение ArgumentNullException для аргументов NULL.
ms.date: 09/18/2020
ms.openlocfilehash: 9d72f8e3320430396132de20c252cd5e8759dce3
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256104"
---
# <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="4ee68-103">Теперь методы WinForms вызывают исключение ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="4ee68-103">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="4ee68-104">Некоторые методы Windows Forms теперь вызывают <xref:System.ArgumentNullException> для аргументов NULL в ситуациях, где ранее вызывали <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="4ee68-104">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

## <a name="change-description"></a><span data-ttu-id="4ee68-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="4ee68-105">Change description</span></span>

<span data-ttu-id="4ee68-106">Ранее некоторые методы Windows Forms вызвали <xref:System.NullReferenceException> при передаче аргумента, который имел значение NULL.</span><span class="sxs-lookup"><span data-stu-id="4ee68-106">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="4ee68-107">Начиная с .NET 5, вместо этого такие методы вызывают <xref:System.ArgumentNullException> для аргументов NULL.</span><span class="sxs-lookup"><span data-stu-id="4ee68-107">Starting in .NET 5, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="4ee68-108">Вызов <xref:System.ArgumentNullException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="4ee68-108">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="4ee68-109">Это также улучшает процесс отладки, четко указывая, что аргумент имеет значение NULL и какой именно это аргумент.</span><span class="sxs-lookup"><span data-stu-id="4ee68-109">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4ee68-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="4ee68-110">Version introduced</span></span>

<span data-ttu-id="4ee68-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="4ee68-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4ee68-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="4ee68-112">Recommended action</span></span>

<span data-ttu-id="4ee68-113">Если вы вызываете любой из этих методов и код в данный момент перехватывает <xref:System.NullReferenceException> для аргументов NULL, вместо этого перехватите <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="4ee68-113">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="4ee68-114">Кроме того, рекомендуется обновить код, чтобы предотвратить передачу аргументов NULL в перечисленные методы.</span><span class="sxs-lookup"><span data-stu-id="4ee68-114">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4ee68-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="4ee68-115">Affected APIs</span></span>

<span data-ttu-id="4ee68-116">В следующей таблице перечислены затронутые методы и параметры:</span><span class="sxs-lookup"><span data-stu-id="4ee68-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="4ee68-117">Метод</span><span class="sxs-lookup"><span data-stu-id="4ee68-117">Method</span></span> | <span data-ttu-id="4ee68-118">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="4ee68-118">Parameter name</span></span> | <span data-ttu-id="4ee68-119">Добавлено в версии</span><span class="sxs-lookup"><span data-stu-id="4ee68-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="4ee68-120">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="4ee68-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="4ee68-121">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="4ee68-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="4ee68-122">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="4ee68-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="4ee68-123">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="4ee68-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="4ee68-124">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="4ee68-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="4ee68-125">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="4ee68-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="4ee68-126">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="4ee68-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="4ee68-127">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="4ee68-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="4ee68-128">Предварительная версия 2</span><span class="sxs-lookup"><span data-stu-id="4ee68-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="4ee68-129">Предварительная версия 2</span><span class="sxs-lookup"><span data-stu-id="4ee68-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="4ee68-130">Предварительная версия 5</span><span class="sxs-lookup"><span data-stu-id="4ee68-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="4ee68-131">Предварительная версия 5</span><span class="sxs-lookup"><span data-stu-id="4ee68-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="4ee68-132">Предварительная версия 5</span><span class="sxs-lookup"><span data-stu-id="4ee68-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="4ee68-133">Предварительная версия 5</span><span class="sxs-lookup"><span data-stu-id="4ee68-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="4ee68-134">предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="4ee68-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="4ee68-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="4ee68-135">`owner`, `value`</span></span> | <span data-ttu-id="4ee68-136">предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="4ee68-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="4ee68-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="4ee68-137">`owner`, `value`</span></span> | <span data-ttu-id="4ee68-138">предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="4ee68-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="4ee68-139">предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="4ee68-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="4ee68-140">предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="4ee68-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="4ee68-141">предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="4ee68-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="4ee68-142">предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="4ee68-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="4ee68-143">предварительная версия 7</span><span class="sxs-lookup"><span data-stu-id="4ee68-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4ee68-144">`key` имеет значение `null` или пуст</span><span class="sxs-lookup"><span data-stu-id="4ee68-144">`key` is `null` or empty</span></span> | <span data-ttu-id="4ee68-145">предварительная версия 8</span><span class="sxs-lookup"><span data-stu-id="4ee68-145">Preview 8</span></span> |
> | <xref:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4ee68-146">`key` имеет значение `null` или пуст</span><span class="sxs-lookup"><span data-stu-id="4ee68-146">`key` is `null` or empty</span></span> | <span data-ttu-id="4ee68-147">RC1</span><span class="sxs-lookup"><span data-stu-id="4ee68-147">RC1</span></span> |
> | <xref:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="4ee68-148">RC1</span><span class="sxs-lookup"><span data-stu-id="4ee68-148">RC1</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`
- `M:System.Windows.Forms.ListViewGroup.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.#ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System#Collections#ICollection#CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)`

### Category

Windows Forms

-->
