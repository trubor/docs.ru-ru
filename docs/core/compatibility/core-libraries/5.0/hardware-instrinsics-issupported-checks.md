---
title: Критическое изменение. Встроенные проверки IsSupported, поддерживаемые оборудованием, могут отличаться для вложенных типов
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где проверка X64.IsSupported для аппаратных встроенных функций может привести к другим результатам.
ms.date: 11/01/2020
ms.openlocfilehash: 5c6049ad5881c0389870cfd5e1550f8358c67599
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257457"
---
# <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a>Встроенные проверки IsSupported, поддерживаемые оборудованием, могут отличаться для вложенных типов

Проверка `<Isa>.X64.IsSupported`, где `<Isa>` ссылается на классы в пространстве имен <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType>, теперь может привести к другим результатам в предыдущих версиях .NET.

> [!TIP]
> *ISA* означает стандартную промышленную архитектуру.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET некоторые встроенные в оборудование типы <xref:System.Runtime.Intrinsics.X86>, например <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, не содержали вложенный класс `X64`. Для этих типов вызов `<Isa>.X64.IsSupported` разрешался в свойство `IsSupported` вложенного класса `X64` родительского класса `<Isa>`. Это означало, что свойство может возвращать `true` даже тогда, когда `<Isa>.IsSupported` возвращает `false`.

В .NET 5 и более поздних версиях все типы <xref:System.Runtime.Intrinsics.X86> предоставляют вложенный класс `X64`, который поддерживает соответствующие отчеты. Это гарантирует, что общая иерархия останется правильной и что если `<Isa>.X64.IsSupported` `true`, то `<Isa>.IsSupported` также может считаться `true`.

## <a name="reason-for-change"></a>Причина изменения

Предполагалось, что если `<Isa>.X64.IsSupported` `true`, то `<Isa>.IsSupported` также предполагается `true`. Тем не менее, из-за того, как работает разрешение члена C#, классы, у которых нет вложенного класса `X64`, это было не всегда, что приводило к ошибкам в пользовательском коде.

## <a name="recommended-action"></a>Рекомендуемое действие

При необходимости настройте код, проверяющий `IsSupported` для поиска соответствующего ISA.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
