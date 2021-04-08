---
title: Критическое изменение в .NET 6. API, связанные с DataGridView, вызывают исключение InvalidOperationException
description: Сведения о критическом изменении в .NET 6, где некоторые API, связанные с DataGridView, вызовут исключение, если значение DataGridViewCellAccessibleObject.Owner объекта равно NULL.
ms.date: 03/29/2021
ms.openlocfilehash: 3726296bb93c88d438e45ea832bf9070ace69dd0
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106080668"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a>API, связанные с DataGridView, теперь вызывают исключение InvalidOperationException

Некоторые API, связанные с <xref:System.Windows.Forms.DataGridView>, теперь вызывают <xref:System.InvalidOperationException>, если значение объекта <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> — `null`.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET затронутые API выдают <xref:System.NullReferenceException> при вызове, если для свойства <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> задано значение `null`. Начиная с .NET 6 эти API создают <xref:System.InvalidOperationException>, а не <xref:System.NullReferenceException>, если при их вызове свойство <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> имеет значение `null`.

## <a name="reason-for-change"></a>Причина изменения

Вызов <xref:System.InvalidOperationException> соответствует поведению среды выполнения .NET. Это также улучшает процесс отладки, четко указывая недопустимое свойство.

## <a name="version-introduced"></a>Представленная версия

.NET 6.0

## <a name="recommended-action"></a>Рекомендованное действие

Проверьте код и при необходимости обновите его, чтобы не допустить создания затрагиваемых типов с помощью свойства <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> как `null`.

## <a name="affected-apis"></a>Затронутые API

В следующей таблице перечислены затронутые свойства и методы.

> [!div class="mx-tdBreakAll"]
> | Затронутый метод или свойство | Добавлено в версии |
> |-|-|
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds?displayProperty=fullName> | Предварительная версия 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction?displayProperty=fullName> | Предварительная версия 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name?displayProperty=fullName> | Предварительная версия 4 |
>| <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=fullName> | Предварительная версия 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State?displayProperty=fullName> | Предварительная версия 4 |

## <a name="see-also"></a>См. также

- [API, связанные с DataGridView, вызывают исключение InvalidOperationException (.NET 5)](../5.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name`
- `M:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State`

### Category

Windows Forms

-->
