---
title: Критическое изменение. Значение FrameworkDescription изменено с .NET Core на .NET
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где RuntimeInformation.FrameworkDescription теперь возвращает ".NET" вместо ".NET Core".
ms.date: 11/01/2020
ms.openlocfilehash: 18aa9a30a149b3c38d4bbfe4a0c99446f4372f07
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257522"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>Значение FrameworkDescription изменено с .NET Core на .NET

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> теперь возвращает ".NET" вместо ".NET Core".

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> возвращает ".NET Core" в составе строки описания, например `.NET Core 3.1.1`.

Начиная с .NET 5 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> возвращает ".NET" в составе строки описания, например `.NET 5.0.0`.

## <a name="reason-for-change"></a>Причина изменения

В .NET 5 в качестве краткого моникера целевой платформы вместо `netcoreapp` используется `net`. В целях обеспечения согласованности также было обновлено описание платформы. Это изменение носит косметический характер, так как `FrameworkName` кодируется только в свойстве <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Обновите код, в котором выполняется поиск ".NET Core" в строке, возвращаемой <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
