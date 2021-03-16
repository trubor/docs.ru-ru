---
title: Критическое изменение. Класс WinHttpHandler удален из среды выполнения .NET
description: Сведения о критическом изменении в .NET 5, где класс WinHttpHandler был удален из среды выполнения .NET.
ms.date: 10/18/2020
ms.openlocfilehash: 95abcfb4d7670be035bd640dbb85458406c1b0e0
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256417"
---
# <a name="winhttphandler-removed-from-net-runtime"></a>Класс WinHttpHandler удален из среды выполнения .NET

Класс `WinHttpHandler` был удален из сборки *System.Net.Http.dll*. Теперь он доступен только как внештатный (OOB) [пакет NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET класс <xref:System.Net.Http.WinHttpHandler> доступен как часть основных библиотек .NET. Начиная с .NET 5 класс <xref:System.Net.Http.WinHttpHandler> доступен только как отдельно устанавливаемый [пакет NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).

## <a name="recommended-action"></a>Рекомендованное действие

Установите пакет NuGet [System.Net.Http.WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/). Или, если не требуются специфические для WinHTTP функции, используйте вместо этого <xref:System.Net.Http.SocketsHttpHandler>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->
