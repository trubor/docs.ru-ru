---
title: Критическое изменение. MulticastOption.Group не принимает значение null
description: Сведения о критическом изменении в .NET 5, где MulticastOption.Group не принимает значение NULL.
ms.date: 08/18/2020
ms.openlocfilehash: 09c6415d275361abee8285aabdda13ccd9727043
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256456"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>MulticastOption.Group не принимает значение null

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> больше не принимает значение `null`. Если задать для свойства значение `null`, вызывается исключение <xref:System.ArgumentNullException>.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET для свойства <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> можно было задать значение `null`. Если впоследствии <xref:System.Net.Sockets.MulticastOption> передается в <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, среда выполнения вызывает исключение <xref:System.NullReferenceException>.

В .NET 5 и более поздних версиях исключение <xref:System.ArgumentNullException> вызывается, если для этого свойства задано значение `null`.

## <a name="reason-for-change"></a>Причина изменения

Для соответствия рекомендациям по проектированию платформы свойство было обновлено для создания исключения <xref:System.ArgumentNullException>, если значение равно `null`.

## <a name="recommended-action"></a>Рекомендованное действие

Убедитесь, что для <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> не задается значение `null`.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
