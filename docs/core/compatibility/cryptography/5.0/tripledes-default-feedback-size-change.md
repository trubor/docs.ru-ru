---
title: Критическое изменение. Изменено значение FeedbackSize по умолчанию для экземпляров, создаваемых методом TripleDES.Create
description: Сведения о критическом изменении в .NET 5.0, где значение свойства FeedbackSize для экземпляра TripleDES, возвращаемое методом TripleDES.Create(), изменено с 64 на 8.
ms.date: 10/16/2020
ms.openlocfilehash: 4179da17bf2e5cc5fcc7d64d83ba92119f912042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759895"
---
# <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a><span data-ttu-id="5d485-103">Изменено значение FeedbackSize по умолчанию для экземпляров, создаваемых методом TripleDES.Create</span><span class="sxs-lookup"><span data-stu-id="5d485-103">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>

<span data-ttu-id="5d485-104">Значение по умолчанию для свойства <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> экземпляра <xref:System.Security.Cryptography.TripleDES>, возвращаемого <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType>, изменено с 64 на 8, чтобы упростить переход с .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d485-104">The default value for the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> property on the <xref:System.Security.Cryptography.TripleDES> instance returned from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> has changed from 64 to 8 to make migration from .NET Framework easier.</span></span> <span data-ttu-id="5d485-105">Это свойство, если оно не используется непосредственно в коде вызывающего объекта, применяется только в том случае, когда свойство <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> имеет значение <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d485-105">This property, unless used directly in caller code, is used only when the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property is <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5d485-106">Поддержка режима <xref:System.Security.Cryptography.CipherMode.CFB> появилась в выпуске .NET 5.0 RC1, поэтому это изменение должно влиять только на приложения .NET 5.0 RC1 и .NET 5.0 RC2.</span><span class="sxs-lookup"><span data-stu-id="5d485-106">Support for the <xref:System.Security.Cryptography.CipherMode.CFB> mode was first added to .NET for the 5.0 RC1 release, so only .NET 5.0 RC1 and .NET 5.0 RC2 applications should be impacted by this change.</span></span>

## <a name="change-description"></a><span data-ttu-id="5d485-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="5d485-107">Change description</span></span>

<span data-ttu-id="5d485-108">В .NET Core и предыдущих предварительных версиях .NET 5.0 `TripleDES.Create().FeedbackSize` имеет значение по умолчанию 64.</span><span class="sxs-lookup"><span data-stu-id="5d485-108">In .NET Core and previous pre-release versions of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 64.</span></span> <span data-ttu-id="5d485-109">Начиная с RTM-версии .NET 5.0 `TripleDES.Create().FeedbackSize` имеет значение по умолчанию 8.</span><span class="sxs-lookup"><span data-stu-id="5d485-109">Starting in the RTM version of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 8.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5d485-110">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="5d485-110">Reason for change</span></span>

<span data-ttu-id="5d485-111">В .NET Framework в базовом классе <xref:System.Security.Cryptography.TripleDES> свойство <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> имеет значение по умолчанию 64, но класс <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> меняет его на 8.</span><span class="sxs-lookup"><span data-stu-id="5d485-111">In .NET Framework, the <xref:System.Security.Cryptography.TripleDES> base class defaults the value of <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> to 64, but the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class overwrites the default to 8.</span></span> <span data-ttu-id="5d485-112">Когда свойство <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> было введено в .NET Core версии 2.0, это поведение сохранилось.</span><span class="sxs-lookup"><span data-stu-id="5d485-112">When the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property was introduced to .NET Core in version 2.0, this same behavior was preserved.</span></span> <span data-ttu-id="5d485-113">Однако в .NET Framework <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> возвращает экземпляр <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, поэтому значение по умолчанию, возвращаемое фабрикой алгоритмов, равно 8.</span><span class="sxs-lookup"><span data-stu-id="5d485-113">However, in .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> returns an instance of <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, so the default value from the algorithm factory is 8.</span></span> <span data-ttu-id="5d485-114">Для .NET Core и .NET 5 или более поздней версии фабрика алгоритмов возвращает закрытую реализацию, которая ранее имела значение по умолчанию 64.</span><span class="sxs-lookup"><span data-stu-id="5d485-114">For .NET Core and .NET 5+, the algorithm factory returns a non-public implementation, which, until now, had a default value of 64.</span></span>

<span data-ttu-id="5d485-115">Изменение значения <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> для реализации класса <xref:System.Security.Cryptography.TripleDES> на 8 позволяет написанным для .NET Framework приложениям, в которых задавался режим шифрования <xref:System.Security.Cryptography.CipherMode.CFB>, но свойство <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> не указывалось явным образом, продолжать работать в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="5d485-115">Changing the <xref:System.Security.Cryptography.TripleDES> implementation class' <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> value to 8 allows for applications written for .NET Framework that specified the cipher mode as <xref:System.Security.Cryptography.CipherMode.CFB> but didn't explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property, to continue to function on .NET 5.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5d485-116">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="5d485-116">Version introduced</span></span>

<span data-ttu-id="5d485-117">5.0</span><span class="sxs-lookup"><span data-stu-id="5d485-117">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5d485-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="5d485-118">Recommended action</span></span>

<span data-ttu-id="5d485-119">Приложения, которые шифруют или расшифровывают данные в версии RC1 или RC2 .NET 5.0, делают это с помощью алгоритма CFB64 при выполнении следующих условий:</span><span class="sxs-lookup"><span data-stu-id="5d485-119">Applications that encrypt or decrypt data in the RC1 or RC2 versions of .NET 5.0 do so with CFB64, when the following conditions are met:</span></span>

- <span data-ttu-id="5d485-120">экземпляр <xref:System.Security.Cryptography.TripleDES> получен от метода <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType>;</span><span class="sxs-lookup"><span data-stu-id="5d485-120">With a <xref:System.Security.Cryptography.TripleDES> instance from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="5d485-121">для <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> используется значение по умолчанию;</span><span class="sxs-lookup"><span data-stu-id="5d485-121">Using the default value for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span>
- <span data-ttu-id="5d485-122">свойству <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> присвоено значение <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d485-122">With the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property set to <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5d485-123">Чтобы сохранить это поведение, присвойте свойству <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> значение `64`.</span><span class="sxs-lookup"><span data-stu-id="5d485-123">To maintain this behavior, assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property to `64`.</span></span>

<span data-ttu-id="5d485-124">Не все реализации `TripleDES` используют такое же значение по умолчанию для <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span><span class="sxs-lookup"><span data-stu-id="5d485-124">Not all `TripleDES` implementations use the same default for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span> <span data-ttu-id="5d485-125">При использовании режима шифрования <xref:System.Security.Cryptography.CipherMode.CFB> в экземплярах <xref:System.Security.Cryptography.TripleDES> мы рекомендуем всегда явно задавать значение свойства <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span><span class="sxs-lookup"><span data-stu-id="5d485-125">We recommend that if you use the <xref:System.Security.Cryptography.CipherMode.CFB> cipher mode on <xref:System.Security.Cryptography.TripleDES> instances, you should always explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property value.</span></span>

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

## <a name="affected-apis"></a><span data-ttu-id="5d485-126">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5d485-126">Affected APIs</span></span>

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

### Category

- Cryptography

-->
