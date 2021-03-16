---
title: Критическое изменение. Алгоритмы обработки путей класса Cookie приведены в соответствие с RFC 6265
description: Узнайте о критическом изменении в .NET 5, где алгоритмы обработки путей, определенные в RFC 6265, реализованы для классов cookie и CookieContainer.
ms.date: 08/18/2020
ms.openlocfilehash: 5ee1bccc79a5ac271904dd3223b58cc168f18cfa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256469"
---
# <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>Алгоритмы обработки путей класса Cookie приведены в соответствие с RFC 6265

Алгоритмы обработки путей, определенные в [RFC 6265](https://tools.ietf.org/html/rfc6265), реализованы для классов <xref:System.Net.Cookie> и <xref:System.Net.CookieContainer>.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="change-description"></a>Описание изменений

- Свойство <xref:System.Net.Cookie.Path> больше не должно быть префиксом пути запроса.
- Вычисление значения по умолчанию для <xref:System.Net.Cookie.Path> и алгоритмов сопоставления путей реализовано в RFC 6265 в [разделе 5.1.4](https://tools.ietf.org/html/rfc6265#section-5.1.4).

## <a name="recommended-action"></a>Рекомендуемое действие

В большинстве случаев вам не нужно предпринимать никаких действий. Но если код зависел от проверки <xref:System.Net.Cookie.Path>, вам нужно реализовать необходимую проверку в коде. Если код зависел от вычисления значения по умолчанию для <xref:System.Net.Cookie.Path>, попробуйте вручную указать значение <xref:System.Net.Cookie.Path>, а не использовать значение по умолчанию.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

### Category

Networking

-->
