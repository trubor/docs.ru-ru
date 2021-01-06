---
title: Предупреждение SYSLIB0008
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0008.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2b573f4b28cdf79107395f5cb38a4226d0ccc11e
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596334"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a><span data-ttu-id="800b2-103">SYSLIB0008. CreatePdbGenerator не поддерживается</span><span class="sxs-lookup"><span data-stu-id="800b2-103">SYSLIB0008: CreatePdbGenerator is not supported</span></span>

<span data-ttu-id="800b2-104">API <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> помечен как устаревший, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="800b2-104">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API is marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="800b2-105">При его использовании во время компиляции создается предупреждение `SYSLIB0008`.</span><span class="sxs-lookup"><span data-stu-id="800b2-105">Using this API generates warning `SYSLIB0008` at compile time.</span></span>

## <a name="suppress-the-warning"></a><span data-ttu-id="800b2-106">Отключение предупреждения</span><span class="sxs-lookup"><span data-stu-id="800b2-106">Suppress the warning</span></span>

<span data-ttu-id="800b2-107">Если вы не можете изменить код, это предупреждение можно отключить с помощью директивы `#pragma` или параметра проекта `<NoWarn>`.</span><span class="sxs-lookup"><span data-stu-id="800b2-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="800b2-108">Примеры см. в разделе [Отключение предупреждений](../syslib-obsoletions.md#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="800b2-108">For examples, see [Suppress warnings](../syslib-obsoletions.md#suppress-warnings).</span></span>
