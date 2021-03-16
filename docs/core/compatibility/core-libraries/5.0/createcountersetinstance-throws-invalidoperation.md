---
title: Критическое изменение. CreateCounterSetInstance создает исключение InvalidOperationException, если экземпляр уже существует
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где CounterSet.CreateCounterSetInstance создает исключение, если счетчик уже существует.
ms.date: 11/01/2020
ms.openlocfilehash: bf59677a85538bc4992c589f8642ab4a0fce54ac
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257574"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="c2dc3-103">Теперь CounterSet.CreateCounterSetInstance создает исключение InvalidOperationException, если экземпляр уже существует.</span><span class="sxs-lookup"><span data-stu-id="c2dc3-103">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="c2dc3-104">Начиная с .NET 5 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> создает исключение <xref:System.InvalidOperationException> вместо <xref:System.ArgumentException>, если набор счетчиков уже существует.</span><span class="sxs-lookup"><span data-stu-id="c2dc3-104">Starting in .NET 5, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

## <a name="change-description"></a><span data-ttu-id="c2dc3-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="c2dc3-105">Change description</span></span>

<span data-ttu-id="c2dc3-106">В .NET Framework и .NET Core 1.0–3.1 экземпляр набора счетчиков можно создать, вызвав <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2dc3-106">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="c2dc3-107">Однако если набор счетчиков уже существует, метод вызывает исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c2dc3-107">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="c2dc3-108">В .NET 5 и более поздних версиях при вызове <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> и наличии набора счетчиков возникает исключение <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="c2dc3-108">In .NET 5 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c2dc3-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c2dc3-109">Version introduced</span></span>

<span data-ttu-id="c2dc3-110">5.0</span><span class="sxs-lookup"><span data-stu-id="c2dc3-110">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c2dc3-111">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c2dc3-111">Recommended action</span></span>

<span data-ttu-id="c2dc3-112">Если при вызове <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> возникают исключения <xref:System.ArgumentException>, также следует рассмотреть перехват исключений <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="c2dc3-112">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="c2dc3-113">Перехват исключений <xref:System.ArgumentException> не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c2dc3-113">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c2dc3-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c2dc3-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
