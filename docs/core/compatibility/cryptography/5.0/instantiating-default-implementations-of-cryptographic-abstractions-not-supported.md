---
title: Критическое изменение. Создание экземпляров реализаций по умолчанию для криптографических абстракций не поддерживается
description: Сведения о критическом изменении в .NET 5, в котором перегрузки Create() для криптографических абстракций устарели.
ms.date: 10/16/2020
ms.openlocfilehash: b75f3568317d1db8ae1bb629f760aaec7e69776a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256794"
---
# <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a>Создание экземпляров реализаций по умолчанию для криптографических абстракций не поддерживается

Начиная с версии .NET 5.0 перегрузки `Create()` без параметров для криптографических абстракций не рекомендуются к применению и приводят к возникновению предупреждения.

## <a name="change-description"></a>Описание изменений

В .NET Framework версий с 2.0 по 4.8 фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, могут быть настроены для возврата различных алгоритмов. Например, при установке .NET Framework 4.8 по умолчанию статический метод без параметров <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> возвращает экземпляр алгоритма SHA1, как показано в следующем фрагменте кода.

**Только .NET Framework**

```csharp
// Return an instance of the default hash algorithm (SHA1).
HashAlgorithm alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA1CryptoServiceProvider'.
Console.WriteLine(alg.GetType());

// Change the default algorithm to be SHA256, not SHA1.
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), typeof(HashAlgorithm).FullName);
alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA256CryptoServiceProvider'.
Console.WriteLine(alg.GetType());
```

Также можно использовать [конфигурации на уровне компьютера](../../../../framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) для изменения алгоритма по умолчанию без необходимости программного вызова `CryptoConfig`.

В .NET Core версий с 2.0 по 3.1 фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, всегда создают исключение <xref:System.PlatformNotSupportedException>.

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

В .NET 5 и более поздних версий фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, не рекомендуются для использования и во время компиляции с создают предупреждение идентификатором `SYSLIB0007`. Во время выполнения эти методы продолжают создавать исключение <xref:System.PlatformNotSupportedException>.

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

Это изменение происходит только во время компиляции. Относительно предыдущих версий .NET Core во время выполнения нет никаких изменений.

> [!NOTE]
>
> - Для применения не рекомендуются только перегрузки методов `Create()` без параметров. Параметризованные перегрузки по-прежнему актуальны и функционируют в соответствии с ожиданиями.
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - Перегрузки без параметров для *определенных* семейств алгоритмов (не абстракции) также сохраняют актуальность и будут продолжать работать ожидаемым образом.
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

## <a name="reason-for-change"></a>Причина изменения

Система конфигурации шифрования, представленная в .NET Framework, больше не используется в .NET Core и .NET 5.0 и более поздних версий, поскольку она является устаревшей и не позволяет обеспечить необходимую гибкость шифрования. Требования к обратной совместимости .NET также не позволяют платформе обновлять определенные API шифрования, чтобы обеспечить поддержку улучшений технологий шифрования. Например, метод <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> был представлен в .NET Framework 1.0, когда алгоритм хэширования SHA-1 соответствовал уровню развития технологий на тот момент. Прошло двадцать лет, и теперь SHA-1 считается ненадежным, но мы не можем изменить <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> для возврата другого алгоритма. Это может привести к неприемлемым критическим изменениям в использовании приложений.

Рекомендации предписывают, что библиотеки, использующие примитивы шифрования (такие как AES, SHA-* и RSA), должны полностью контролировать использование этих примитивов. Приложения, для которых требуется обеспечить гарантированную актуальность в будущем, должны использовать библиотеки более высокого уровня, которые заключают эти примитивы в оболочку, а затем добавляют возможности управления ключами и гибкого шифрования. Такие библиотеки часто предоставляются средой размещения. В качестве примера можно привести [библиотеку защиты данных ASP.NET](/aspnet/core/security/data-protection/), которая обеспечивает решение этих задач от имени вызывающего приложения.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Рекомендуется заменить вызовы к устаревшим API вызовами методов фабрики для конкретных алгоритмов, например <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>. Таким образом, вы будете полностью контролировать алгоритмы, для которых создаются экземпляры.

- Если необходимо обеспечить совместимость с существующими полезными данными, создаваемыми приложениями .NET Framework, которые используют устаревшие API, используйте предложенные в следующей таблице альтернативные варианты. В этой таблице приводится сопоставление алгоритмов .NET Framework по умолчанию с их эквивалентами в .NET 5 и более поздних версий.

  | .NET Framework | Совместимый эквивалент в .NET Core или .NET 5.0 и более поздних версий | Remarks |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | Алгоритм SHA-1 считается ненадежным. По возможности рекомендуется использовать более надежный алгоритм. Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности. |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | Алгоритм HMACSHA1 не рекомендуется к применению для большинства современных приложений. По возможности рекомендуется использовать более надежный алгоритм. Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности. |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | Алгоритм HMACSHA1 не рекомендуется к применению для большинства современных приложений. По возможности рекомендуется использовать более надежный алгоритм. Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности. |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- Если вам по-прежнему требуется вызывать устаревшие перегрузки `Create()` без параметров, вы можете отключить предупреждение `SYSLIB0007` в коде.

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  Это предупреждение также можно отключить в файле проекта. В таком случае предупреждение также будет отключено для всех исходных файлов в проекте.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0007 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0007</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > Если отключить `SYSLIB0007`, для указанных здесь API шифрования будут отключены только предупреждения об устаревании. Другие предупреждения не отключаются. Кроме того, даже если отключить предупреждение, эти устаревшие API все равно будут создавать исключение <xref:System.PlatformNotSupportedException> во время выполнения.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

### Category

- Cryptography

-->
