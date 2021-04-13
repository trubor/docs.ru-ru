---
title: Критическое изменение. Kestrel. HTTP/2 по TLS отключен в несовместимых версиях Windows
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Kestrel. HTTP/2 по TLS отключен в несовместимых версиях Windows
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b8bbe113b3357508b6af29fa9a4d1431f6a6acea
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498117"
---
# <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a>Kestrel. HTTP/2 по TLS отключен в несовместимых версиях Windows

Чтобы включить HTTP/2 по TLS в Windows, необходимо выполнить два условия:

- поддержка согласования протокола уровня приложений доступна, начиная с Windows 8.1 и Windows Server 2012 R2;
- набор шифров, совместимых с HTTP/2, доступен, начиная с Windows 10 и Windows Server 2016.

Таким образом, поведение Kestrel при настройке HTTP/2 по протоколу TLS изменилось следующим образом:

- Переход на использование более ранней версии `Http1` и регистрация сообщения в журнале на уровне `Information`, если [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) имеет значение `Http1AndHttp2`. Значение `Http1AndHttp2` является значением по умолчанию для свойства `ListenOptions.HttpProtocols`.
- Выводится `NotSupportedException`, если `ListenOptions.HttpProtocols` имеет значение `Http2`.

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 5.0 (предварительная версия 7)

## <a name="old-behavior"></a>Старое поведение

В следующей таблице показано поведение при настройке HTTP/2 по TLS.

| Протоколы | Windows 7,<br />Windows Server 2008 R2<br />или более ранней версии | Windows 8,<br />Windows Server 2012 | Windows 8.1,<br />Windows Server 2012 R2 | Windows 10,<br />Windows Server 2016<br />или более поздней версии |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | Выводится `NotSupportedException`                   | Ошибка при подтверждении соединения по TLS     | Ошибка при подтверждении соединения по TLS &ast;     | Без ошибок |
| `Http1AndHttp2` | Переход на использование более ранней версии `Http1`                    | Переход на использование более ранней версии `Http1`     | Ошибка при подтверждении соединения по TLS &ast;     | Без ошибок |

&ast; Настройте совместимые комплекты шифров, чтобы включить эти сценарии.

## <a name="new-behavior"></a>Новое поведение

В следующей таблице показано поведение при настройке HTTP/2 по TLS.

| Протоколы | Windows 7,<br />Windows Server 2008 R2<br />или более ранней версии | Windows 8,<br />Windows Server 2012 | Windows 8.1,<br />Windows Server 2012 R2 | Windows 10,<br />Windows Server 2016<br />или более поздней версии |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | Выводится `NotSupportedException`                   | Выводится `NotSupportedException`     | Выводится `NotSupportedException` &ast;&ast;     | Без ошибок |
| `Http1AndHttp2` | Переход на использование более ранней версии `Http1`                    | Переход на использование более ранней версии `Http1`     | Переход на использование более ранней версии `Http1` &ast;&ast;     | Без ошибок |

&ast;&ast; Настройте совместимые комплекты шифров и задайте для параметра контекста приложения `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` значение `true`, чтобы включить эти сценарии.

## <a name="reason-for-change"></a>Причина изменения

Это изменение гарантирует, что ошибки совместимости для HTTP/2 по TLS в более старых версиях Windows отображаются как можно раньше и точнее.

## <a name="recommended-action"></a>Рекомендованное действие

Необходимо обеспечить отключение HTTP/2 по TLS в несовместимых версиях Windows. Windows 8.1 и Windows Server 2012 R2 несовместимы, так как по умолчанию в них отсутствуют необходимые шифры. Однако можно обновить параметры конфигурации компьютера для использования шифров, совместимых с HTTP/2. Дополнительные сведения см. в разделе [Комплекты шифров TLS в Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1). После настройки необходимо включить HTTP/2 по TLS в Kestrel путем настройки параметра контекста приложения `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`. Пример:

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

Основная поддержка не изменилась. Например, HTTP/2 по TLS никогда не поддерживался в Windows 8 и Windows Server 2012. В результате этого изменения меняется представление ошибок в этих неподдерживаемых сценариях.

## <a name="affected-apis"></a>Затронутые API

Отсутствуют

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
