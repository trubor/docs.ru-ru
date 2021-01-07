---
title: Предупреждение SYSLIB0007
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0007.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: c011340665a0c53172bf5b23e032d78301b3cd72
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596366"
---
# <a name="syslib0007-default-implementations-of-cryptography-algorithms-not-supported"></a><span data-ttu-id="a59cb-103">SYSLIB0007. Реализации алгоритмов шифрования по умолчанию не поддерживаются</span><span class="sxs-lookup"><span data-stu-id="a59cb-103">SYSLIB0007: Default implementations of cryptography algorithms not supported</span></span>

<span data-ttu-id="a59cb-104">Система конфигурации шифрования, представленная в .NET Framework, больше не используется в .NET Core и .NET 5 и более поздних версий, поскольку она не позволяет обеспечить необходимую гибкость шифрования.</span><span class="sxs-lookup"><span data-stu-id="a59cb-104">The cryptographic configuration system in .NET Framework doesn't allow for proper cryptographic agility and isn't present in .NET Core and .NET 5+.</span></span> <span data-ttu-id="a59cb-105">Требования к обратной совместимости .NET также не позволяют платформе обновлять определенные API шифрования, чтобы обеспечить поддержку улучшений технологий шифрования.</span><span class="sxs-lookup"><span data-stu-id="a59cb-105">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="a59cb-106">В связи с этим следующие API помечены как устаревшие, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="a59cb-106">As a result, the following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="a59cb-107">При использовании этих API во время компиляции создается предупреждение `SYSLIB0007`.</span><span class="sxs-lookup"><span data-stu-id="a59cb-107">Use of these APIs generates warning `SYSLIB0007` at compile time.</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

## <a name="workarounds"></a><span data-ttu-id="a59cb-108">Обходные пути</span><span class="sxs-lookup"><span data-stu-id="a59cb-108">Workarounds</span></span>

- <span data-ttu-id="a59cb-109">Рекомендуется заменить вызовы к устаревшим API вызовами методов фабрики для конкретных алгоритмов, например <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a59cb-109">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a59cb-110">Таким образом, вы будете полностью контролировать алгоритмы, для которых создаются экземпляры.</span><span class="sxs-lookup"><span data-stu-id="a59cb-110">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="a59cb-111">Если необходимо обеспечить совместимость с существующими полезными данными, создаваемыми приложениями .NET Framework, которые используют устаревшие API, используйте предложенные в следующей таблице альтернативные варианты.</span><span class="sxs-lookup"><span data-stu-id="a59cb-111">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="a59cb-112">В этой таблице приводится сопоставление алгоритмов .NET Framework по умолчанию с их эквивалентами в .NET 5 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="a59cb-112">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="a59cb-113">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a59cb-113">.NET Framework</span></span> | <span data-ttu-id="a59cb-114">Совместимый эквивалент в .NET Core или .NET 5.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="a59cb-114">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="a59cb-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="a59cb-115">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="a59cb-116">Алгоритм SHA-1 считается ненадежным.</span><span class="sxs-lookup"><span data-stu-id="a59cb-116">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="a59cb-117">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="a59cb-117">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="a59cb-118">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="a59cb-118">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="a59cb-119">Алгоритм HMACSHA1 не рекомендуется к применению для большинства современных приложений.</span><span class="sxs-lookup"><span data-stu-id="a59cb-119">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="a59cb-120">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="a59cb-120">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="a59cb-121">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="a59cb-121">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="a59cb-122">Алгоритм HMACSHA1 не рекомендуется к применению для большинства современных приложений.</span><span class="sxs-lookup"><span data-stu-id="a59cb-122">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="a59cb-123">По возможности рекомендуется использовать более надежный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="a59cb-123">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="a59cb-124">Дополнительные сведения вы можете получить у своего консультанта по вопросам безопасности.</span><span class="sxs-lookup"><span data-stu-id="a59cb-124">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="a59cb-125">См. также</span><span class="sxs-lookup"><span data-stu-id="a59cb-125">See also</span></span>

- [<span data-ttu-id="a59cb-126">Создание экземпляров реализаций по умолчанию для криптографических абстракций не поддерживается</span><span class="sxs-lookup"><span data-stu-id="a59cb-126">Instantiating default implementations of cryptographic abstractions is not supported</span></span>](../cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)