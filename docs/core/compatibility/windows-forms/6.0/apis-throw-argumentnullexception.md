---
title: Критическое изменение. Некоторые API создают исключение ArgumentNullException
description: 'Сведения о критическом изменении в .NET 6: некоторые API проверяют аргументы и теперь создают исключение ArgumentNullException.'
ms.date: 01/29/2021
ms.openlocfilehash: ca7f32739237715657350f52d2523b0ce378364d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255741"
---
# <a name="some-apis-throw-argumentnullexception"></a>Некоторые API создают исключение ArgumentNullException

Теперь некоторые API проверяют входные параметры и создают исключение <xref:System.ArgumentNullException>, тогда как раньше при вызове с входными аргументами `null` они создавали исключение <xref:System.NullReferenceException>.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET при вызове с аргументом `null` затронутые API создают исключение <xref:System.NullReferenceException>.

Начиная с версии .NET 6, при вызове с аргументом `null` затронутые API создают исключение <xref:System.ArgumentNullException>.

## <a name="reason-for-change"></a>Причина изменения

Создание исключения <xref:System.ArgumentNullException> соответствует поведению среды выполнения .NET. Оно обеспечивает улучшенную отладку за счет четкого указания аргумента, который вызвал исключение.

## <a name="version-introduced"></a>Представленная версия

.NET 6.0

## <a name="recommended-action"></a>Рекомендованное действие

- Проверьте и при необходимости обновите код, чтобы избежать передачи входных аргументов `null` в затронутые API.
- Если ваш код обрабатывает <xref:System.NullReferenceException>, замените или добавьте дополнительный обработчик для <xref:System.ArgumentNullException>.

## <a name="affected-apis"></a>Затронутые API

Затронутые свойства перечислены в следующей таблице:

| Свойство | Версия изменена |
|-|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | Предварительная версия 1 |

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
