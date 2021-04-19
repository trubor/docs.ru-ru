---
title: 'Критическое изменение: изменение в библиотеке MessagePack в пакете signalr-protocol-msgpack'
description: Сведения о критическом изменении в ASP.NET Core 6.0, где была изменена библиотека MessagePack и из пакета @microsoft/signalr-protocol-msgpack были удалены два параметра.
ms.date: 04/07/2021
ms.openlocfilehash: 62f853cbed0904e278e25f231528845baac9f71d
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107260033"
---
# <a name="changed-messagepack-library-in-microsoftsignalr-protocol-msgpack"></a>Изменения в библиотеке MessagePack в @microsoft/signalr-protocol-msgpack

Теперь пакет npm [@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack) ссылается на `@msgpack/msgpack`, а не на `msgpack5`. Кроме того, изменились доступные параметры, которые при необходимости можно передать в `MessagePackHubProtocol`. Свойства `MessagePackOptions.disableTimestampEncoding` и `MessagePackOptions.forceFloat64` были удалены, а также были добавлены новые параметры.

Обсуждение этого вопроса см. на странице <https://github.com/dotnet/aspnetcore/issues/30471>.

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 6.0

## <a name="old-behavior"></a>Старое поведение

В предыдущих версиях для того, чтобы можно было использовать [протокол MessagePack для концентратора](/aspnet/core/signalr/messagepackhubprotocol) в браузере, необходимо было добавить три ссылки на скрипты:

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/msgpack5/msgpack5.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

## <a name="new-behavior"></a>Новое поведение

Начиная с ASP.NET Core 6, для того, чтобы можно было использовать [протокол MessagePack для концентратора](/aspnet/core/signalr/messagepackhubprotocol) в браузере, требуются только две ссылки на скрипты:

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

Вместо пакета `msgpack5` в каталог *node_modules* загружается пакет `@msgpack/msgpack`, если вы хотите использовать его непосредственно в приложении.

Наконец, в `MessagePackOptions` появились новые дополнительные свойства, а свойства `disableTimestampEncoding` и `forceFloat64` были удалены.

## <a name="reason-for-change"></a>Причина изменения

Это изменение было сделано для того, чтобы сократить размер ресурса, упростить использование пакета и расширить возможности настройки.

## <a name="recommended-action"></a>Рекомендованное действие

Если вы ранее использовали `msgpack5` в своем приложении, необходимо добавить прямую ссылку на библиотеку в файл *package.json*.

## <a name="affected-apis"></a>Затронутые API

Были удалены следующие API:

- `MessagePackOptions.disableTimestampEncoding`
- `MessagePackOptions.forceFloat64`

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis.

-->
