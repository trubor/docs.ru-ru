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
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a>Теперь свойства WinForms вызывают исключение ArgumentOutOfRangeException

Некоторые свойства Windows Forms теперь вызывают <xref:System.ArgumentOutOfRangeException> для недопустимых аргументов в ситуациях, где ранее не делали этого.

## <a name="change-description"></a>Описание изменений

Ранее эти свойства вызывали различные исключения, такие как <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException> или <xref:System.ArgumentException> при передаче аргументов вне диапазона. Начиная с .NET 5 эти свойства вызывают <xref:System.ArgumentOutOfRangeException> при передаче аргументов, которые выходят за пределы диапазона.

Вызов <xref:System.ArgumentOutOfRangeException> соответствует поведению среды выполнения .NET. Это также улучшает процесс отладки, четко указывая, какой аргумент недопустим.

## <a name="version-introduced"></a>Представленная версия

.NET 5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Измените код, чтобы предотвратить передачу недопустимых аргументов.
- При необходимости обработайте <xref:System.ArgumentOutOfRangeException> при указании свойства.

## <a name="affected-apis"></a>Затронутые API

В следующей таблице перечислены затронутые свойства и параметры.

> [!div class="mx-tdBreakAll"]
> | Свойство. | Имя параметра | Добавлено в версии |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | 5.0, предварительная версия 5 |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | 5.0, предварительная версия 6 |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | 5.0, предварительная версия 6 |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
