---
title: Критическое изменение. MulticastOption.Group не принимает значение null
description: Сведения о критическом изменении в .NET 5.0, где MulticastOption.Group не принимает значение NULL.
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759690"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="b49ac-103">MulticastOption.Group не принимает значение null</span><span class="sxs-lookup"><span data-stu-id="b49ac-103">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="b49ac-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> больше не принимает значение `null`.</span><span class="sxs-lookup"><span data-stu-id="b49ac-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="b49ac-105">Если задать для свойства значение `null`, вызывается исключение <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="b49ac-105">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b49ac-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="b49ac-106">Version introduced</span></span>

<span data-ttu-id="b49ac-107">5.0</span><span class="sxs-lookup"><span data-stu-id="b49ac-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="b49ac-108">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="b49ac-108">Change description</span></span>

<span data-ttu-id="b49ac-109">В предыдущих версиях .NET для свойства <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> можно было задать значение `null`.</span><span class="sxs-lookup"><span data-stu-id="b49ac-109">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="b49ac-110">Если впоследствии <xref:System.Net.Sockets.MulticastOption> передается в <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, среда выполнения вызывает исключение <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="b49ac-110">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="b49ac-111">В .NET 5.0 и более поздних версиях исключение <xref:System.ArgumentNullException> вызывается, если для этого свойства задано значение `null`.</span><span class="sxs-lookup"><span data-stu-id="b49ac-111">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b49ac-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="b49ac-112">Reason for change</span></span>

<span data-ttu-id="b49ac-113">Для соответствия рекомендациям по проектированию платформы свойство было обновлено для создания исключения <xref:System.ArgumentNullException>, если значение равно `null`.</span><span class="sxs-lookup"><span data-stu-id="b49ac-113">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b49ac-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="b49ac-114">Recommended action</span></span>

<span data-ttu-id="b49ac-115">Убедитесь, что для <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> не задается значение `null`.</span><span class="sxs-lookup"><span data-stu-id="b49ac-115">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b49ac-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="b49ac-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
