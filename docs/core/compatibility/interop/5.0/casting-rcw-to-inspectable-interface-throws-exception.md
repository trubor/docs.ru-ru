---
title: Критическое изменение. Приведение RCW к `InterfaceIsIInspectable` создает исключение
description: Узнайте о критических изменениях взаимодействия в .NET 5, где приведение RCW к интерфейсу `InterfaceIsIInspectable` создает исключение PlatformNotSupportedException.
ms.date: 09/13/2020
ms.openlocfilehash: 9f777ee9396f7822c9ff6bf5209021c07b8b618a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256638"
---
# <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a>Приведение вызываемой оболочки времени выполнения к интерфейсу `InterfaceIsIInspectable` вызывает исключение PlatformNotSupportedException

Приведение вызываемой оболочки времени выполнения (RCW) к интерфейсу, помеченному как <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, теперь вызывает исключение <xref:System.PlatformNotSupportedException>. Это изменение соответствует [удалению поддержки WinRT из .NET](built-in-support-for-winrt-removed.md).

## <a name="version-introduced"></a>Представленная версия

5.0 RC2

## <a name="change-description"></a>Описание изменений

В версиях от .NET до .NET 5 (предварительная версия 6) приведение RCW к интерфейсу, помеченному как <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, работает должным образом. В версиях .NET 5 (предварительные версии 6–8 и RC1) можно успешно привести RCW к интерфейсу <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>. Однако при выполнении методов в интерфейсе могут возникнуть нарушения прав доступа, так как базовая поддержка в среде выполнения [была удалена в .NET 5 (предварительная версия 6)](built-in-support-for-winrt-removed.md).

В .NET 5 RC2 и более поздних версиях приведение RCW к интерфейсу, помеченному как <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, вызывает исключение <xref:System.PlatformNotSupportedException> во время приведения.

## <a name="reason-for-change"></a>Причина изменения

Поддержка <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> была [удалена в предыдущей предварительной версии .NET 5](built-in-support-for-winrt-removed.md). Однако приведение к интерфейсу <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> было пропущено по ошибке. Поскольку базовая поддержка в среде выполнения больше не существует, выдача исключения <xref:System.PlatformNotSupportedException> обеспечивает корректную обработку сбоя. Создание исключения также позволяет легче обнаружить, что эта функция больше не поддерживается.

## <a name="recommended-action"></a>Рекомендованное действие

- Если вы можете определить интерфейс в файле метаданных среды выполнения Windows (WinMD), используйте вместо этого средство C#/WinRT.

- В противном случае пометьте интерфейс как <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> вместо <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> и добавьте три фиктивные записи в начало интерфейса для методов <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>. Фрагмент кода приведен ниже.

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

### Category

Interop

-->
