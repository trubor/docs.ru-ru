---
title: Критическое изменение. Максимальная длина текста NotifyIcon.Text увеличена
description: Сведения о критическом изменении в .NET 6, в результате которого увеличена максимальная длина текста для свойства NotifyIcon.Text.
ms.date: 01/19/2021
ms.openlocfilehash: f87b98dd852ce202689ae9360bee9b6cfbf01794
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255780"
---
# <a name="notifyicontext-maximum-text-length-increased"></a>Максимальная длина текста NotifyIcon.Text увеличена

Максимальная допустимая длина текста для свойства <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> увеличилась с 63 до 127 символов.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET максимальная допустимая длина для свойства <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> составляет 63 символа. Начиная с .NET 6, максимальная допустимая длина текста составляет 127 символов. В любой версии при попытке задать значение, длина которого превышает ограничение, выдается <xref:System.ArgumentException>.

## <a name="reason-for-change"></a>Причина изменения

Максимальная допустимая длина текста была увеличена в соответствии с [базовым API Windows](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080). API Windows был обновлен в Windows 2000, но по соображениям совместимости максимальный размер этого свойства не был обновлен на платформе .NET Framework.

## <a name="version-introduced"></a>Представленная версия

.NET 6, предварительная версия 1

## <a name="recommended-action"></a>Рекомендованное действие

Проверьте код и при необходимости ослабьте любые имеющиеся защитные проверки.

## <a name="affected-apis"></a>Затронутые API

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
