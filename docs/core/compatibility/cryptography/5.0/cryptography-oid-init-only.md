---
title: Критическое изменение. Класс Cryptography.Oid функционально доступен только для инициализации
description: Сведения о критическом изменении в .NET 5, где методы задания свойств в классе Cryptography.Oid теперь вызывают исключение при попытке изменить значение.
ms.date: 08/16/2020
ms.openlocfilehash: aa1e72adcda61f2292574729e36cdc578bf907d2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256872"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a>Класс System.Security.Cryptography.Oid функционально доступен только для инициализации

Класс <xref:System.Security.Cryptography.Oid?displayProperty=fullName>, используемый для представления значений идентификаторов объектов ASN.1 и их понятных имен, был ранее полностью изменяемым. Эта изменяемость часто игнорировалась или становилась неожиданностью. Теперь методы задания свойств вызывают <xref:System.PlatformNotSupportedException> при попытке изменить значение после того, как оно уже было назначено.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях методы задания свойств в <xref:System.Security.Cryptography.Oid> можно было использовать для изменения значений свойств <xref:System.Security.Cryptography.Oid.FriendlyName> и <xref:System.Security.Cryptography.Oid.Value>.

В .NET 5 и более поздних версиях методы задания свойств можно использовать только для инициализации значения. После того как свойство получило значение из конструктора или предыдущего вызова метода задания свойств, метод задания свойств всегда будет вызывать <xref:System.PlatformNotSupportedException>.

## <a name="reason-for-change"></a>Причина изменения

Это изменение позволяет повторно использовать объекты <xref:System.Security.Cryptography.Oid> как часть возвращаемых значений в общедоступных API для уменьшения количества профилей выделения объектов. Это позволяет избежать необходимости создавать временные "защитные" копии, когда значения <xref:System.Security.Cryptography.Oid> используются в качестве входных данных.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

Избегайте использования методов задания свойств <xref:System.Security.Cryptography.Oid>, отличных от инициализации объектов. Чтобы представить новое значение, используйте новый экземпляр вместо изменения значения существующего объекта.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

### Category

Cryptography

-->
