---
title: Критическое изменение. Некоторые API создают исключение ArgumentNullException
description: 'Сведения о критическом изменении в .NET 6: некоторые API проверяют аргументы и теперь создают исключение ArgumentNullException.'
ms.date: 01/29/2021
ms.openlocfilehash: dd0ee33ca7335bfd6e4ddfefca0e56ab719178eb
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079574"
---
# <a name="some-apis-throw-argumentnullexception"></a><span data-ttu-id="32913-103">Некоторые API создают исключение ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="32913-103">Some APIs throw ArgumentNullException</span></span>

<span data-ttu-id="32913-104">Теперь некоторые API проверяют входные параметры и создают исключение <xref:System.ArgumentNullException>, тогда как раньше при вызове с входными аргументами `null` они создавали исключение <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="32913-104">Some APIs now validate input parameters and throw an <xref:System.ArgumentNullException> where previously they threw a <xref:System.NullReferenceException>, if invoked with `null` input arguments.</span></span>

## <a name="change-description"></a><span data-ttu-id="32913-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="32913-105">Change description</span></span>

<span data-ttu-id="32913-106">В предыдущих версиях .NET при вызове с аргументом `null` затронутые API создают исключение <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="32913-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> if invoked with an argument that's `null`.</span></span>

<span data-ttu-id="32913-107">Начиная с версии .NET 6, при вызове с аргументом `null` затронутые API создают исключение <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="32913-107">Starting in .NET 6, the affected APIs throw an <xref:System.ArgumentNullException> if invoked with an argument that's `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="32913-108">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="32913-108">Reason for change</span></span>

<span data-ttu-id="32913-109">Создание исключения <xref:System.ArgumentNullException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="32913-109">Throwing <xref:System.ArgumentNullException> conforms to .NET Runtime behavior.</span></span> <span data-ttu-id="32913-110">Оно обеспечивает улучшенную отладку за счет четкого указания аргумента, который вызвал исключение.</span><span class="sxs-lookup"><span data-stu-id="32913-110">It provides a better debug experience by clearly communicating which argument caused the exception.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="32913-111">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="32913-111">Version introduced</span></span>

<span data-ttu-id="32913-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="32913-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="32913-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="32913-113">Recommended action</span></span>

- <span data-ttu-id="32913-114">Проверьте и при необходимости обновите код, чтобы избежать передачи входных аргументов `null` в затронутые API.</span><span class="sxs-lookup"><span data-stu-id="32913-114">Review and, if necessary, update your code to prevent passing `null` input arguments to the affected APIs.</span></span>
- <span data-ttu-id="32913-115">Если ваш код обрабатывает <xref:System.NullReferenceException>, замените или добавьте дополнительный обработчик для <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="32913-115">If your code handles <xref:System.NullReferenceException>, replace or add an additional handler for <xref:System.ArgumentNullException>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="32913-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="32913-116">Affected APIs</span></span>

<span data-ttu-id="32913-117">В следующей таблице перечислены затронутые API и особые параметры.</span><span class="sxs-lookup"><span data-stu-id="32913-117">The following table lists the affected APIs and specific parameters:</span></span>

| <span data-ttu-id="32913-118">Метод или свойство</span><span class="sxs-lookup"><span data-stu-id="32913-118">Method/property</span></span> | <span data-ttu-id="32913-119">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="32913-119">Parameter name</span></span> | <span data-ttu-id="32913-120">Версия изменена</span><span class="sxs-lookup"><span data-stu-id="32913-120">Version changed</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | `index` | <span data-ttu-id="32913-121">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="32913-121">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataGridViewRowStateChangedEventArgs.%23ctor(System.Windows.Forms.DataGridViewRow,System.Windows.Forms.DataGridViewElementStates)> | `dataGridViewRow` | <span data-ttu-id="32913-122">Предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="32913-122">Preview 4</span></span> |

## <a name="see-also"></a><span data-ttu-id="32913-123">См. также</span><span class="sxs-lookup"><span data-stu-id="32913-123">See also</span></span>

- [<span data-ttu-id="32913-124">TreeNodeCollection.Item создает исключение, если узел назначен в другом месте</span><span class="sxs-lookup"><span data-stu-id="32913-124">TreeNodeCollection.Item throws exception if node is assigned elsewhere</span></span>](treenodecollection-item-throws-argumentexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`
- `M:System.Windows.Forms.DataGridViewRowStateChangedEventArgs.#ctor(System.Windows.Forms.DataGridViewRow,System.Windows.Forms.DataGridViewElementStates)`

### Category

Windows Forms

-->
