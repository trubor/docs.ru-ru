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
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>Теперь CounterSet.CreateCounterSetInstance создает исключение InvalidOperationException, если экземпляр уже существует.

Начиная с .NET 5 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> создает исключение <xref:System.InvalidOperationException> вместо <xref:System.ArgumentException>, если набор счетчиков уже существует.

## <a name="change-description"></a>Описание изменений

В .NET Framework и .NET Core 1.0–3.1 экземпляр набора счетчиков можно создать, вызвав <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>. Однако если набор счетчиков уже существует, метод вызывает исключение <xref:System.ArgumentException>.

В .NET 5 и более поздних версиях при вызове <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> и наличии набора счетчиков возникает исключение <xref:System.InvalidOperationException>.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Если при вызове <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> возникают исключения <xref:System.ArgumentException>, также следует рассмотреть перехват исключений <xref:System.InvalidOperationException>.

> [!NOTE]
> Перехват исключений <xref:System.ArgumentException> не рекомендуется.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
