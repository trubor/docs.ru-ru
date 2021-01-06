---
title: Предупреждение SYSLIB0009
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0009.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 922fcc30b2b1577976e4e88e3f7631e19d4b2cce
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596360"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a><span data-ttu-id="93d7b-103">SYSLIB0009. Методы проверки подлинности и предварительной проверки подлинности AuthenticationManager не поддерживаются</span><span class="sxs-lookup"><span data-stu-id="93d7b-103">SYSLIB0009: The AuthenticationManager Authenticate and PreAuthenticate methods are not supported</span></span>

<span data-ttu-id="93d7b-104">Следующие API помечены как устаревшие, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="93d7b-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="93d7b-105">При использовании этих API во время компиляции создается предупреждение `SYSLIB0009`.</span><span class="sxs-lookup"><span data-stu-id="93d7b-105">Use of these APIs generates warning `SYSLIB0009` at compile time.</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a><span data-ttu-id="93d7b-106">Отключение предупреждения</span><span class="sxs-lookup"><span data-stu-id="93d7b-106">Suppress the warning</span></span>

<span data-ttu-id="93d7b-107">Если вы не можете изменить код, это предупреждение можно отключить с помощью директивы `#pragma` или параметра проекта `<NoWarn>`.</span><span class="sxs-lookup"><span data-stu-id="93d7b-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="93d7b-108">Примеры см. в разделе [Отключение предупреждений](../syslib-obsoletions.md#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="93d7b-108">For examples, see [Suppress warnings](../syslib-obsoletions.md#suppress-warnings).</span></span>
