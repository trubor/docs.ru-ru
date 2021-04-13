---
title: Критическое изменение. Некоторые API создают исключение ArgumentNullException
description: 'Сведения о критическом изменении в .NET 6: некоторые API проверяют аргументы и теперь создают исключение ArgumentNullException.'
ms.date: 01/29/2021
ms.openlocfilehash: 1c7b41bf5e367dca394130da66360e660173ba14
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496856"
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

В следующей таблице перечислены затронутые API и особые параметры.

| Метод или свойство | Имя параметра | Версия изменена |
|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | `index` | Предварительная версия 1 |
| <xref:System.Windows.Forms.DrawTreeNodeEventArgs.%23ctor(System.Drawing.Graphics,System.Windows.Forms.TreeNode,System.Drawing.Rectangle,System.Windows.Forms.TreeNodeStates)> | `graphics` | Предварительная версия 3 |
| <xref:System.Windows.Forms.DataGridViewRowStateChangedEventArgs.%23ctor(System.Windows.Forms.DataGridViewRow,System.Windows.Forms.DataGridViewElementStates)> | `dataGridViewRow` | Предварительная версия 4 |

## <a name="see-also"></a>См. также

- [TreeNodeCollection.Item создает исключение, если узел назначен в другом месте](treenodecollection-item-throws-argumentexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`
- `M:System.Windows.Forms.DrawTreeNodeEventArgs.#ctor(System.Drawing.Graphics,System.Windows.Forms.TreeNode,System.Drawing.Rectangle,System.Windows.Forms.TreeNodeStates)`
- `M:System.Windows.Forms.DataGridViewRowStateChangedEventArgs.#ctor(System.Windows.Forms.DataGridViewRow,System.Windows.Forms.DataGridViewElementStates)`

### Category

Windows Forms

-->
