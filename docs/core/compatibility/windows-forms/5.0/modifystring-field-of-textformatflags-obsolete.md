---
title: Критическое изменение. Поле TextFormatFlags.ModifyString является устаревшим
description: Сведения о критическом изменении в .NET 5, где поле TextFormatFlags.ModifyString является устаревшим.
ms.date: 11/05/2020
ms.openlocfilehash: 9fe1e04b1ad36070b08af2affdca1e058ec74bb8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256170"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a>Флаг TextFormatFlags.ModifyString является устаревшим

Поле <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> устарело в качестве предупреждения и может быть удалено в будущей версии .NET.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET поле перечисления <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> не помечено как устаревшее. В .NET 5 и более поздних версиях оно помечено как устаревшее в качестве предупреждения. Это поле может быть удалено в будущей версии .NET.

## <a name="reason-for-change"></a>Причина изменения

В некоторых ситуациях передача строки в <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> с <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> изменяет строку. Это влечет за собой нарушение неизменности строки и может привести к неустранимому повреждению состояния среды выполнения .NET.

## <a name="version-introduced"></a>Представленная версия

.NET 5.0

## <a name="recommended-action"></a>Рекомендованное действие

Обновите весь код, который зависит от <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
