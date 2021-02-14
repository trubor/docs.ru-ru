---
title: Критическое изменение. Некоторые API создают исключение ArgumentNullException
description: 'Сведения о критическом изменении в .NET 6.0: некоторые API проверяют аргументы и теперь создают исключение ArgumentNullException.'
ms.date: 01/29/2021
ms.openlocfilehash: f9d7dc8bb57ed8dc5b4ff41bda9b3bde7db7b880
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804154"
---
# <a name="some-apis-throw-argumentnullexception"></a><span data-ttu-id="7bb24-103">Некоторые API создают исключение ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="7bb24-103">Some APIs throw ArgumentNullException</span></span>

<span data-ttu-id="7bb24-104">Теперь некоторые API проверяют входные параметры и создают исключение <xref:System.ArgumentNullException>, тогда как раньше при вызове с входными аргументами `null` они создавали исключение <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="7bb24-104">Some APIs now validate input parameters and throw an <xref:System.ArgumentNullException> where previously they threw a <xref:System.NullReferenceException>, if invoked with `null` input arguments.</span></span>

## <a name="change-description"></a><span data-ttu-id="7bb24-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="7bb24-105">Change description</span></span>

<span data-ttu-id="7bb24-106">В предыдущих версиях .NET при вызове с аргументом `null` затронутые API создают исключение <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="7bb24-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> if invoked with an argument that's `null`.</span></span>

<span data-ttu-id="7bb24-107">Начиная с версии .NET 6.0, при вызове с аргументом `null` затронутые API создают исключение <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="7bb24-107">Starting in .NET 6.0, the affected APIs throw an <xref:System.ArgumentNullException> if invoked with an argument that's `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7bb24-108">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="7bb24-108">Reason for change</span></span>

<span data-ttu-id="7bb24-109">Создание исключения <xref:System.ArgumentNullException> соответствует поведению среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="7bb24-109">Throwing <xref:System.ArgumentNullException> conforms to .NET Runtime behavior.</span></span> <span data-ttu-id="7bb24-110">Оно обеспечивает улучшенную отладку за счет четкого указания аргумента, который вызвал исключение.</span><span class="sxs-lookup"><span data-stu-id="7bb24-110">It provides a better debug experience by clearly communicating which argument caused the exception.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7bb24-111">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7bb24-111">Version introduced</span></span>

<span data-ttu-id="7bb24-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="7bb24-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7bb24-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="7bb24-113">Recommended action</span></span>

- <span data-ttu-id="7bb24-114">Проверьте и при необходимости обновите код, чтобы избежать передачи входных аргументов `null` в затронутые API.</span><span class="sxs-lookup"><span data-stu-id="7bb24-114">Review and, if necessary, update your code to prevent passing `null` input arguments to the affected APIs.</span></span>
- <span data-ttu-id="7bb24-115">Если ваш код обрабатывает <xref:System.NullReferenceException>, замените или добавьте дополнительный обработчик для <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="7bb24-115">If your code handles <xref:System.NullReferenceException>, replace or add an additional handler for <xref:System.ArgumentNullException>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7bb24-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7bb24-116">Affected APIs</span></span>

<span data-ttu-id="7bb24-117">Затронутые свойства перечислены в следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="7bb24-117">The following table lists the affected properties:</span></span>

| <span data-ttu-id="7bb24-118">Свойство</span><span class="sxs-lookup"><span data-stu-id="7bb24-118">Property</span></span> | <span data-ttu-id="7bb24-119">Версия изменена</span><span class="sxs-lookup"><span data-stu-id="7bb24-119">Version changed</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | <span data-ttu-id="7bb24-120">Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="7bb24-120">Preview 1</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
