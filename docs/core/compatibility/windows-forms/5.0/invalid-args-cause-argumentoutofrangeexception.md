---
title: Критическое изменение. Теперь свойства WinForms вызывают исключение ArgumentOutOfRangeException
description: Сведения о критическом изменении в .NET 5, где некоторые свойства Windows Forms теперь вызывают исключение ArgumentOutOfRangeException для недопустимых аргументов.
ms.date: 06/18/2020
ms.openlocfilehash: 493669af1ed5646d93e7c7d2688afd40f3fa731c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256157"
---
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="0942b-103">Теперь свойства WinForms вызывают исключение ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="0942b-103">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="0942b-104">Некоторые свойства Windows Forms теперь вызывают <xref:System.ArgumentOutOfRangeException> для недопустимых аргументов в ситуациях, где ранее не делали этого.</span><span class="sxs-lookup"><span data-stu-id="0942b-104">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="0942b-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="0942b-105">Change description</span></span>

<span data-ttu-id="0942b-106">Ранее эти свойства вызывали различные исключения, такие как <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException> или <xref:System.ArgumentException> при передаче аргументов вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="0942b-106">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="0942b-107">Начиная с .NET 5 эти свойства вызывают <xref:System.ArgumentOutOfRangeException> при передаче аргументов, которые выходят за пределы диапазона.</span><span class="sxs-lookup"><span data-stu-id="0942b-107">Starting in .NET 5, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="0942b-108">Вызов <xref:System.ArgumentOutOfRangeException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="0942b-108">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="0942b-109">Это также улучшает процесс отладки, четко указывая, какой аргумент недопустим.</span><span class="sxs-lookup"><span data-stu-id="0942b-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0942b-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="0942b-110">Version introduced</span></span>

<span data-ttu-id="0942b-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0942b-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0942b-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="0942b-112">Recommended action</span></span>

- <span data-ttu-id="0942b-113">Измените код, чтобы предотвратить передачу недопустимых аргументов.</span><span class="sxs-lookup"><span data-stu-id="0942b-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="0942b-114">При необходимости обработайте <xref:System.ArgumentOutOfRangeException> при указании свойства.</span><span class="sxs-lookup"><span data-stu-id="0942b-114">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0942b-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="0942b-115">Affected APIs</span></span>

<span data-ttu-id="0942b-116">В следующей таблице перечислены затронутые свойства и параметры.</span><span class="sxs-lookup"><span data-stu-id="0942b-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="0942b-117">Свойство.</span><span class="sxs-lookup"><span data-stu-id="0942b-117">Property</span></span> | <span data-ttu-id="0942b-118">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="0942b-118">Parameter name</span></span> | <span data-ttu-id="0942b-119">Добавлено в версии</span><span class="sxs-lookup"><span data-stu-id="0942b-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="0942b-120">5.0, предварительная версия 5</span><span class="sxs-lookup"><span data-stu-id="0942b-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="0942b-121">5.0, предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="0942b-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="0942b-122">5.0, предварительная версия 6</span><span class="sxs-lookup"><span data-stu-id="0942b-122">5.0 Preview 6</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
