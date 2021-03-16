---
title: Критическое изменение. Распознавание URI UNC-путей в UNIX
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где класс URI теперь распознает строки, начинающиеся с двух косых черт, как пути в формате UNC в операционных системах UNIX.
ms.date: 11/01/2020
ms.openlocfilehash: 65baaad5e1be7a8f61e3e62c976fd7e28f48730f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257028"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a>Распознавание URI UNC-путей в UNIX

Класс <xref:System.Uri> теперь распознает строки, начинающиеся с двух косых черт (`//`) как пути в формате UNC в операционных системах UNIX. Это изменение делает поведение для таких строк согласованным на всех платформах.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET класс <xref:System.Uri> распознавал строки, начинающиеся с двух косых черт, например `//contoso`, как абсолютные пути к файлам в операционных системах UNIX. Однако в Windows такие строки распознаются как UNC-пути.

Начиная с .NET 5 класс <xref:System.Uri> распознает строки, начинающиеся с двух косых черт, как UNC-пути на всех платформах, включая UNIX. Кроме того, свойства ведут себя в соответствии с семантикой UNC:

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> возвращает `true`.
- Символы обратной косой черты в пути заменяются прямой косой чертой. Например, `//first\second` преобразуется в `//first/second`.
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> не кодирует символы процентами. Например, `//first/\uFFF0` *не* преобразуется в `//first/%EF%BF%B0`.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

От разработчика не требуется никаких действий.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
