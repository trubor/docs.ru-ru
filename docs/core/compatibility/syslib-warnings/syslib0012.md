---
title: Предупреждение SYSLIB0012
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0012.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 9b3fa94029efb2343e6dbbeb3ae36195f0956523
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596333"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="ee85b-103">SYSLIB0012. Assembly.CodeBase и Assembly.EscapedCodeBase устарели</span><span class="sxs-lookup"><span data-stu-id="ee85b-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="ee85b-104">Следующие API помечены как устаревшие, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="ee85b-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="ee85b-105">При их использовании во время компиляции создается предупреждение `SYSLIB0012`.</span><span class="sxs-lookup"><span data-stu-id="ee85b-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="ee85b-106">Обходные пути</span><span class="sxs-lookup"><span data-stu-id="ee85b-106">Workarounds</span></span>

<span data-ttu-id="ee85b-107">Взамен рекомендуется использовать <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ee85b-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]
