---
title: Критическое изменение. Теперь методы WinForms вызывают исключение ArgumentException
description: Сведения о критическом изменении в .NET 5.0, где методы форм sWindows теперь вызывают исключение ArgumentException для недопустимых аргументов.
ms.date: 07/18/2020
ms.openlocfilehash: 46fe3f3b1208a5cd676e1b7546507bed36a850f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760283"
---
# <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="d9a37-103">Теперь методы WinForms вызывают исключение ArgumentException</span><span class="sxs-lookup"><span data-stu-id="d9a37-103">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="d9a37-104">Некоторые методы Windows Forms теперь вызывают <xref:System.ArgumentException> для недопустимых аргументов в ситуациях, где ранее не делали этого.</span><span class="sxs-lookup"><span data-stu-id="d9a37-104">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="d9a37-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d9a37-105">Change description</span></span>

<span data-ttu-id="d9a37-106">Ранее передача аргументов непредвиденного или неверного типа в определенные методы Windows Forms приводила к неопределенному состоянию.</span><span class="sxs-lookup"><span data-stu-id="d9a37-106">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="d9a37-107">Начиная с .NET 5.0 эти методы теперь вызывают <xref:System.ArgumentException> при передаче недопустимых аргументов.</span><span class="sxs-lookup"><span data-stu-id="d9a37-107">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="d9a37-108">Вызов <xref:System.ArgumentException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d9a37-108">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="d9a37-109">Это также улучшает процесс отладки, четко указывая, какой аргумент недопустим.</span><span class="sxs-lookup"><span data-stu-id="d9a37-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d9a37-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d9a37-110">Version introduced</span></span>

<span data-ttu-id="d9a37-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="d9a37-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d9a37-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d9a37-112">Recommended action</span></span>

- <span data-ttu-id="d9a37-113">Измените код, чтобы предотвратить передачу недопустимых аргументов.</span><span class="sxs-lookup"><span data-stu-id="d9a37-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="d9a37-114">При необходимости обработайте <xref:System.ArgumentException> при вызове метода.</span><span class="sxs-lookup"><span data-stu-id="d9a37-114">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d9a37-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d9a37-115">Affected APIs</span></span>

<span data-ttu-id="d9a37-116">В следующей таблице перечислены затронутые методы и параметры:</span><span class="sxs-lookup"><span data-stu-id="d9a37-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="d9a37-117">Метод</span><span class="sxs-lookup"><span data-stu-id="d9a37-117">Method</span></span> | <span data-ttu-id="d9a37-118">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="d9a37-118">Parameter name</span></span> | <span data-ttu-id="d9a37-119">Условие</span><span class="sxs-lookup"><span data-stu-id="d9a37-119">Condition</span></span> | <span data-ttu-id="d9a37-120">Добавлено в версии</span><span class="sxs-lookup"><span data-stu-id="d9a37-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="d9a37-121">Аргумент не является аргументом типа <xref:System.Windows.Forms.TabPage>.</span><span class="sxs-lookup"><span data-stu-id="d9a37-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="d9a37-122">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="d9a37-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="d9a37-123">Аргумент содержит `null`, <xref:System.String.Empty?displayProperty=nameWithType> или пробел.</span><span class="sxs-lookup"><span data-stu-id="d9a37-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="d9a37-124">Предварительная версия 5</span><span class="sxs-lookup"><span data-stu-id="d9a37-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="d9a37-125">Не удается извлечь `InputLanguage` для заданных языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="d9a37-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="d9a37-126">Предварительная версия 7</span><span class="sxs-lookup"><span data-stu-id="d9a37-126">Preview 7</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
