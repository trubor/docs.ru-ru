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
# <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a><span data-ttu-id="5fa16-103">Создание экземпляров реализаций по умолчанию для криптографических абстракций не поддерживается</span><span class="sxs-lookup"><span data-stu-id="5fa16-103">Instantiating default implementations of cryptographic abstractions is not supported</span></span>

<span data-ttu-id="5fa16-104">Начиная с версии .NET 5.0 перегрузки `Create()` без параметров для криптографических абстракций не рекомендуются к применению и приводят к возникновению предупреждения.</span><span class="sxs-lookup"><span data-stu-id="5fa16-104">The parameterless `Create()` overloads on cryptographic abstractions are obsolete as warning as of .NET 5.0.</span></span>

## <a name="change-description"></a><span data-ttu-id="5fa16-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="5fa16-105">Change description</span></span>

<span data-ttu-id="5fa16-106">В .NET Framework версий с 2.0 по 4.8 фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, могут быть настроены для возврата различных алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="5fa16-106">In .NET Framework 2.0 - 4.8, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> can be configured to return different algorithms.</span></span> <span data-ttu-id="5fa16-107">Например, при установке .NET Framework 4.8 по умолчанию статический метод без параметров <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> возвращает экземпляр алгоритма SHA1, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="5fa16-107">For example, on a default install of .NET Framework 4.8, the parameterless, static method <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> returns an instance of the SHA1 algorithm, as shown in the following snippet.</span></span>

<span data-ttu-id="5fa16-108">**Только .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="5fa16-108">**.NET Framework only**</span></span>

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

<span data-ttu-id="5fa16-109">Также можно использовать [конфигурации на уровне компьютера](../../../../framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) для изменения алгоритма по умолчанию без необходимости программного вызова `CryptoConfig`.</span><span class="sxs-lookup"><span data-stu-id="5fa16-109">You can also use [machine-wide configuration](../../../../framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) to change the default algorithm without needing to call into `CryptoConfig` programmatically.</span></span>

<span data-ttu-id="5fa16-110">В .NET Core версий с 2.0 по 3.1 фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, всегда создают исключение <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="5fa16-110">In .NET Core 2.0 - 3.1, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> always throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="5fa16-111">В .NET 5 и более поздних версий фабрики абстрактных примитивов шифрования, такие как <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType>, не рекомендуются для использования и во время компиляции с создают предупреждение идентификатором `SYSLIB0007`.</span><span class="sxs-lookup"><span data-stu-id="5fa16-111">In .NET 5 and later versions, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> are marked obsolete and produce a compile-time warning with ID `SYSLIB0007`.</span></span> <span data-ttu-id="5fa16-112">Во время выполнения эти методы продолжают создавать исключение <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="5fa16-112">At run time, these methods continue to throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="5fa16-113">Это изменение происходит только во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="5fa16-113">This is a compile-time only change.</span></span> <span data-ttu-id="5fa16-114">Относительно предыдущих версий .NET Core во время выполнения нет никаких изменений.</span><span class="sxs-lookup"><span data-stu-id="5fa16-114">There is no run-time change from previous versions of .NET Core.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="5fa16-115">Для применения не рекомендуются только перегрузки методов `Create()` без параметров.</span><span class="sxs-lookup"><span data-stu-id="5fa16-115">Only the parameterless overloads of the `Create()` methods are obsolete.</span></span> <span data-ttu-id="5fa16-116">Параметризованные перегрузки по-прежнему актуальны и функционируют в соответствии с ожиданиями.</span><span class="sxs-lookup"><span data-stu-id="5fa16-116">Parameterized overloads are not obsolete and still function as expected.</span></span>
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - <span data-ttu-id="5fa16-117">Перегрузки без параметров для *определенных* семейств алгоритмов (не абстракции) также сохраняют актуальность и будут продолжать работать ожидаемым образом.</span><span class="sxs-lookup"><span data-stu-id="5fa16-117">Parameterless overloads of *specific* algorithm families (not abstractions) are not obsolete, and will continue to function as expected.</span></span>
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

## <a name="reason-for-change"></a><span data-ttu-id="5fa16-118">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="5fa16-118">Reason for change</span></span>

<span data-ttu-id="5fa16-119">Система конфигурации шифрования, представленная в .NET Framework, больше не используется в .NET Core и .NET 5.0 и более поздних версий, поскольку она является устаревшей и не позволяет обеспечить необходимую гибкость шифрования.</span><span class="sxs-lookup"><span data-stu-id="5fa16-119">The cryptographic configuration system present in .NET Framework is no longer present in .NET Core and .NET 5.0+, since that legacy system doesn't allow for proper cryptographic agility.</span></span> <span data-ttu-id="5fa16-120">Требования к обратной совместимости .NET также не позволяют платформе обновлять определенные API шифрования, чтобы обеспечить поддержку улучшений технологий шифрования.</span><span class="sxs-lookup"><span data-stu-id="5fa16-120">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="5fa16-121">Например, метод <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> был представлен в .NET Framework 1.0, когда алгоритм хэширования SHA-1 соответствовал уровню развития технологий на тот момент.</span><span class="sxs-lookup"><span data-stu-id="5fa16-121">For example, the <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> method was introduced in .NET Framework 1.0, when the SHA-1 hash algorithm was state-of-the-art.</span></span> <span data-ttu-id="5fa16-122">Прошло двадцать лет, и теперь SHA-1 считается ненадежным, но мы не можем изменить <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> для возврата другого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="5fa16-122">Twenty years have passed, and now SHA-1 is considered broken, but we cannot change <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> to return a different algorithm.</span></span> <span data-ttu-id="5fa16-123">Это может привести к неприемлемым критическим изменениям в использовании приложений.</span><span class="sxs-lookup"><span data-stu-id="5fa16-123">Doing so would introduce an unacceptable breaking change in consuming applications.</span></span>

<span data-ttu-id="5fa16-124">Рекомендации предписывают, что библиотеки, использующие примитивы шифрования (такие как AES, SHA-\* и RSA), должны полностью контролировать использование этих примитивов.</span><span class="sxs-lookup"><span data-stu-id="5fa16-124">Best practice dictates that libraries that consume cryptographic primitives (such as AES, SHA-\*, and RSA) should be in full control over how they consume these primitives.</span></span> <span data-ttu-id="5fa16-125">Приложения, для которых требуется обеспечить гарантированную актуальность в будущем, должны использовать библиотеки более высокого уровня, которые заключают эти примитивы в оболочку, а затем добавляют возможности управления ключами и гибкого шифрования.</span><span class="sxs-lookup"><span data-stu-id="5fa16-125">Applications that require future-proofing should utilize higher-level libraries that wrap these primitives and add key management and cryptographic agility capabilities.</span></span> <span data-ttu-id="5fa16-126">Такие библиотеки часто предоставляются средой размещения.</span><span class="sxs-lookup"><span data-stu-id="5fa16-126">These libraries are often provided by the hosting environment.</span></span> <span data-ttu-id="5fa16-127">В качестве примера можно привести [библиотеку защиты данных ASP.NET](/aspnet/core/security/data-protection/), которая обеспечивает решение этих задач от имени вызывающего приложения.</span><span class="sxs-lookup"><span data-stu-id="5fa16-127">One example is [ASP.NET's Data Protection library](/aspnet/core/security/data-protection/), which handles these concerns on behalf of the calling application.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5fa16-128">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="5fa16-128">Version introduced</span></span>

<span data-ttu-id="5fa16-129">5.0</span><span class="sxs-lookup"><span data-stu-id="5fa16-129">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5fa16-130">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="5fa16-130">Recommended action</span></span>

- <span data-ttu-id="5fa16-131">Рекомендуется заменить вызовы к устаревшим API вызовами методов фабрики для конкретных алгоритмов, например <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5fa16-131">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5fa16-132">Таким образом, вы будете полностью контролировать алгоритмы, для которых создаются экземпляры.</span><span class="sxs-lookup"><span data-stu-id="5fa16-132">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="5fa16-133">Если необходимо обеспечить совместимость с существующими полезными данными, создаваемыми приложениями .NET Framework, которые используют устаревшие API, используйте предложенные в следующей таблице альтернативные варианты.</span><span class="sxs-lookup"><span data-stu-id="5fa16-133">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="5fa16-134">В этой таблице приводится сопоставление алгоритмов .NET Framework по умолчанию с их эквивалентами в .NET 5 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="5fa16-134">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="5fa16-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5fa16-135">.NET Framework</span></span> | <span data-ttu-id="5fa16-136">Совместимый эквивалент в .NET Core или .NET 5.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="5fa16-136">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="5fa16-137">Remarks</span><span class="sxs-lookup"><span data-stu-id="5fa16-137">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="5fa16-138">Алгоритм SHA-1 считается ненадежным.</span><span class="sxs-lookup"><span data-stu-id="5fa16-138">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="5fa16-139">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="5fa16-139">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="5fa16-140">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="5fa16-140">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="5fa16-141">Алгоритм HMACSHA1 не рекомендуется к применению для большинства современных приложений.</span><span class="sxs-lookup"><span data-stu-id="5fa16-141">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="5fa16-142">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="5fa16-142">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="5fa16-143">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="5fa16-143">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="5fa16-144">Алгоритм HMACSHA1 не рекомендуется к применению для большинства современных приложений.</span><span class="sxs-lookup"><span data-stu-id="5fa16-144">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="5fa16-145">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="5fa16-145">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="5fa16-146">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="5fa16-146">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- <span data-ttu-id="5fa16-147">Если вам по-прежнему требуется вызывать устаревшие перегрузки `Create()` без параметров, вы можете отключить предупреждение `SYSLIB0007` в коде.</span><span class="sxs-lookup"><span data-stu-id="5fa16-147">If you must continue to call the obsolete parameterless `Create()` overloads, you can suppress the `SYSLIB0007` warning in code.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  <span data-ttu-id="5fa16-148">Это предупреждение также можно отключить в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="5fa16-148">You can also suppress the warning in your project file.</span></span> <span data-ttu-id="5fa16-149">В таком случае предупреждение также будет отключено для всех исходных файлов в проекте.</span><span class="sxs-lookup"><span data-stu-id="5fa16-149">Doing so disables the warning for all source files within the project.</span></span>

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
  > <span data-ttu-id="5fa16-150">Если отключить `SYSLIB0007`, для указанных здесь API шифрования будут отключены только предупреждения об устаревании.</span><span class="sxs-lookup"><span data-stu-id="5fa16-150">Suppressing `SYSLIB0007` disables only the obsoletion warnings for the cryptography APIs listed here.</span></span> <span data-ttu-id="5fa16-151">Другие предупреждения не отключаются.</span><span class="sxs-lookup"><span data-stu-id="5fa16-151">It does not disable any other warnings.</span></span> <span data-ttu-id="5fa16-152">Кроме того, даже если отключить предупреждение, эти устаревшие API все равно будут создавать исключение <xref:System.PlatformNotSupportedException> во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5fa16-152">Additionally, even if you suppress the warning, these obsoleted APIs will still throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5fa16-153">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5fa16-153">Affected APIs</span></span>

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
