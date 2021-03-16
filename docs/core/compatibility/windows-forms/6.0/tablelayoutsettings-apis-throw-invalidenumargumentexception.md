---
title: Критическое изменение. Некоторые свойства TableLayoutSettings выдают исключение InvalidEnumArgumentException
description: Сведения о критическом изменении в .NET 6, в результате которого ряд API TableLayoutSettings теперь выдает исключение InvalidEnumArgumentException для недопустимых аргументов.
ms.date: 01/18/2021
ms.openlocfilehash: 2da097122b935ec3a60c2bb009cc8ebbcff6468e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255728"
---
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a>Выбранные свойства TableLayoutSettings выдают исключение InvalidEnumArgumentException

Теперь выбранные свойства <xref:System.Windows.Forms.TableLayoutSettings> выдают <xref:System.ComponentModel.InvalidEnumArgumentException> при попытке присвоить неверное значение.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET эти свойства выдают <xref:System.ArgumentOutOfRangeException> при попытке присвоить неверное значение. Начиная с .NET 6 эти свойства в таких случаях выдают <xref:System.ComponentModel.InvalidEnumArgumentException>.

## <a name="reason-for-change"></a>Причина изменения

Выдача <xref:System.ComponentModel.InvalidEnumArgumentException> соответствует поведению текущего API Windows Forms в аналогичных ситуациях. Выдача этого исключения также позволяет сделать более удобным процесс отладки для разработчиков.

## <a name="version-introduced"></a>Представленная версия

.NET 6.0

## <a name="recommended-action"></a>Рекомендованное действие

- Обновите код, чтобы предотвратить присвоение неверных значений.
- При необходимости обработайте <xref:System.ComponentModel.InvalidEnumArgumentException> при доступе к этим API.

## <a name="affected-apis"></a>Затронутые API

Затронутые свойства перечислены в следующей таблице:

| Свойство | Версия изменена |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | Предварительная версия 1 |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | Предварительная версия 1 |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
