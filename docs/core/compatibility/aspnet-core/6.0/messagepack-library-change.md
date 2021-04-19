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
# <a name="changed-messagepack-library-in-microsoftsignalr-protocol-msgpack"></a><span data-ttu-id="e4c46-103">Изменения в библиотеке MessagePack в @microsoft/signalr-protocol-msgpack</span><span class="sxs-lookup"><span data-stu-id="e4c46-103">Changed MessagePack library in @microsoft/signalr-protocol-msgpack</span></span>

<span data-ttu-id="e4c46-104">Теперь пакет npm [@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack) ссылается на `@msgpack/msgpack`, а не на `msgpack5`.</span><span class="sxs-lookup"><span data-stu-id="e4c46-104">The [@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack) npm package now references `@msgpack/msgpack` instead of `msgpack5`.</span></span> <span data-ttu-id="e4c46-105">Кроме того, изменились доступные параметры, которые при необходимости можно передать в `MessagePackHubProtocol`.</span><span class="sxs-lookup"><span data-stu-id="e4c46-105">Additionally, the available options that can optionally be passed into the `MessagePackHubProtocol` have changed.</span></span> <span data-ttu-id="e4c46-106">Свойства `MessagePackOptions.disableTimestampEncoding` и `MessagePackOptions.forceFloat64` были удалены, а также были добавлены новые параметры.</span><span class="sxs-lookup"><span data-stu-id="e4c46-106">The `MessagePackOptions.disableTimestampEncoding` and `MessagePackOptions.forceFloat64` properties were removed, and some new options were added.</span></span>

<span data-ttu-id="e4c46-107">Обсуждение этого вопроса см. на странице <https://github.com/dotnet/aspnetcore/issues/30471>.</span><span class="sxs-lookup"><span data-stu-id="e4c46-107">For discussion, see <https://github.com/dotnet/aspnetcore/issues/30471>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e4c46-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="e4c46-108">Version introduced</span></span>

<span data-ttu-id="e4c46-109">ASP.NET Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e4c46-109">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="e4c46-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="e4c46-110">Old behavior</span></span>

<span data-ttu-id="e4c46-111">В предыдущих версиях для того, чтобы можно было использовать [протокол MessagePack для концентратора](/aspnet/core/signalr/messagepackhubprotocol) в браузере, необходимо было добавить три ссылки на скрипты:</span><span class="sxs-lookup"><span data-stu-id="e4c46-111">In previous versions, you must include three script references to use the [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) in the browser:</span></span>

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/msgpack5/msgpack5.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

## <a name="new-behavior"></a><span data-ttu-id="e4c46-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="e4c46-112">New behavior</span></span>

<span data-ttu-id="e4c46-113">Начиная с ASP.NET Core 6, для того, чтобы можно было использовать [протокол MessagePack для концентратора](/aspnet/core/signalr/messagepackhubprotocol) в браузере, требуются только две ссылки на скрипты:</span><span class="sxs-lookup"><span data-stu-id="e4c46-113">Starting in ASP.NET Core 6, you only need two script references to use the [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) in the browser:</span></span>

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

<span data-ttu-id="e4c46-114">Вместо пакета `msgpack5` в каталог *node_modules* загружается пакет `@msgpack/msgpack`, если вы хотите использовать его непосредственно в приложении.</span><span class="sxs-lookup"><span data-stu-id="e4c46-114">Instead of the `msgpack5` package, the `@msgpack/msgpack` package is downloaded to your *node_modules* directory if you want to use it directly in your app.</span></span>

<span data-ttu-id="e4c46-115">Наконец, в `MessagePackOptions` появились новые дополнительные свойства, а свойства `disableTimestampEncoding` и `forceFloat64` были удалены.</span><span class="sxs-lookup"><span data-stu-id="e4c46-115">Finally, `MessagePackOptions` has new, additional properties, and the `disableTimestampEncoding` and `forceFloat64` properties are removed.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e4c46-116">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="e4c46-116">Reason for change</span></span>

<span data-ttu-id="e4c46-117">Это изменение было сделано для того, чтобы сократить размер ресурса, упростить использование пакета и расширить возможности настройки.</span><span class="sxs-lookup"><span data-stu-id="e4c46-117">This change was made to reduce asset size, make it simpler to consume the package, and add more customizability.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e4c46-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="e4c46-118">Recommended action</span></span>

<span data-ttu-id="e4c46-119">Если вы ранее использовали `msgpack5` в своем приложении, необходимо добавить прямую ссылку на библиотеку в файл *package.json*.</span><span class="sxs-lookup"><span data-stu-id="e4c46-119">If you were previously using `msgpack5` in your app, you'll need to add a direct reference to the library in your *package.json* file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e4c46-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="e4c46-120">Affected APIs</span></span>

<span data-ttu-id="e4c46-121">Были удалены следующие API:</span><span class="sxs-lookup"><span data-stu-id="e4c46-121">The following APIs were removed:</span></span>

- `MessagePackOptions.disableTimestampEncoding`
- `MessagePackOptions.forceFloat64`

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis.

-->
